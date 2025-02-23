# Documentação: Assistente de Montagem de Envelope (AME)

## 1. Introdução

O Assistente de Montagem de Envelope (AME) é um serviço crítico na cadeia de criação de ordens de assinatura digital. Ele atua como a porta de entrada para validar a elegibilidade (ou “coro”) de requisitantes e garantidores, assegurando a conformidade com as regras de negócio e os requisitos jurídicos antes da efetiva criação da ordem de assinatura. O AME é exposto via API para produtos internos e parceiros e, adicionalmente, alimenta um portal de documentos para áreas que não utilizam a API diretamente.

---

## 2. Objetivos

- **Garantir Conformidade:** Validar que somente requisitantes e garantidores com “coro” possam criar e concluir ordens de assinatura.
- **Automatizar Processos:** Integrar diversas verificações (padrões, limites jurídicos, consulta a serviços de poderes, pessoas e cadastro único) de forma automatizada.
- **Oferecer Integração:** Disponibilizar uma API robusta para consumo por produtos parceiros e uma interface de usuário para áreas internas.
- **Assegurar Resiliência:** Utilizar padrões como filas (SQS), retries, fallback e circuit breaker para garantir robustez na orquestração dos fluxos.
- **Democratizar Dados:** Unificar informações para análise e geração de insights que auxiliem na tomada de decisões estratégicas e na otimização dos modelos de crédito.

---

## 3. Arquitetura e Componentes

### 3.1. Tecnologias Utilizadas

- **Banco de Dados:**  
  - AWS RDS Aurora (MySQL) para armazenamento de dados relacionais e rascunhos de intenções de ordem.
  
- **Computação e Containers:**  
  - AWS ECS com Fargate para execução de microsserviços Java (Spring Boot).

- **Orquestração de Fluxos:**  
  - AWS Step Functions para gerenciar os fluxos de criação de envelope, implementando lógicas de retry, fallback e divisão de cenários.

- **Filas e Mensageria:**  
  - AWS SQS para desacoplamento dos serviços, garantindo resiliência e comunicação assíncrona (incluindo DLQs para tratamento de erros).

- **Funções Serverless:**  
  - AWS Lambda para consumo de mensagens da SQS e disparo do fluxo via Step Functions.

- **Exposição de API:**  
  - API Gateway para disponibilizar o serviço AME tanto para parceiros quanto para consumo interno.

---

### 3.2. Fluxo de Criação de Ordens e Envelopes

#### Criação de Ordem (via API)

1. **Recepção da Requisição:**  
   - O serviço AME recebe um POST com os dados da ordem.
2. **Validações Iniciais:**  
   - Consulta ao serviço de Parametrizador para verificação de padrões e limites jurídicos.
   - Consulta ao serviço de Domínios para obtenção de nomes e chaves.
3. **Armazenamento e Resposta:**  
   - Armazena um rascunho de intenção de ordem no RDS Aurora.
   - Retorna uma chave de ordem para posterior consulta.
4. **Disparo Assíncrono:**  
   - Postagem de mensagem na fila SQS para criação do envelope.

#### Criação do Envelope (via Step Functions)

1. **Inicialização pelo Lambda:**  
   - Consumo da mensagem SQS e disparo do Step Functions.
2. **Verificações Detalhadas:**  
   - **Consulta de Poderes:** Verifica se o requisitante (pessoa jurídica) possui representantes cadastrados e os agrupamentos necessários.
     - Se não houver representantes, a execução falha e é postada uma mensagem indicando ausência de “coro”.
   - **Validação de Representantes:**  
     - Verifica ressalvas e a elegibilidade dos representantes.
     - Armazena dados dos representantes com ressalvas (desabilitados para assinatura, mas presentes para registro).
   - **Consulta de Dados de Participantes:**  
     - Integra com serviço de Pessoas para capturar dados (email, telefone, nome) dos representantes.
   - **Verificação de Operadores e Acesso:**  
     - Consulta ao parceiro de Cadastro Único para confirmar se os representantes possuem operador válido e acesso à conta (bankline).
     - Se nenhum representante estiver apto, o fluxo falha e é notificado.
3. **Validação Final:**  
   - Análise dos agrupamentos de poderes para determinar se a ordem pode ser efetivada.
   - Se as condições não forem atendidas (por exemplo, apenas um representante sem possibilidade de assinatura isolada), o fluxo falha.
4. **Sucesso e Notificação:**  
   - Se as verificações forem satisfatórias, o envelope é considerado “com coro”.
   - Mensagem na SQS é enviada com o status de sucesso para que o próximo serviço (criação efetiva) seja acionado.

---

### 3.3. Integrações com Serviços Externos

- **Serviço de Parametrização:** Validação dos padrões e limites jurídicos.
- **Serviço de Domínios:** Consulta de nomes e chaves de domínios.
- **Serviço de Poderes:** Verificação dos poderes e representantes do requisitante.
- **Serviço de Pessoas:** Coleta de dados detalhados dos representantes.
- **Serviço de Cadastro Único:** Validação de operadores e acesso bancário.
- **Serviço de Notificação:** Envio de alertas aos participantes quanto ao status do envelope.

---

## 4. Detalhes Técnicos

### API e Exposição de Serviços

- **Exposição:**  
  - API Gateway fornece acesso ao serviço AME.
- **Documentação:**  
  - OpenAPI/Swagger para facilitar a integração com parceiros e equipes internas.
- **Segurança:**  
  - Autenticação, autorização e uso de padrões de segurança (IAM, criptografia).

### Orquestração com Step Functions

- **Função:**  
  - Gerenciar fluxos complexos de criação de envelopes, integrando chamadas a serviços externos.
- **Técnicas Utilizadas:**  
  - Retry e fallback para tolerância a falhas.
  - Uso de S3 para armazenamento e passagem de payloads grandes.
- **Logs e Monitoramento:**  
  - Logs detalhados para rastreabilidade e análise de performance.

### Mensageria e Resiliência com SQS

- **Desacoplamento:**  
  - Uso de filas para comunicação assíncrona entre serviços.
- **Tratamento de Erros:**  
  - Implementação de Dead Letter Queues (DLQs) para mensagens não processadas.

### Banco de Dados e Armazenamento

- **RDS Aurora:**  
  - Armazenamento de dados relacionais, com índices otimizados e rotinas de limpeza.
- **Armazenamento Temporário:**  
  - Uso de buckets S3 para payloads grandes e backups.

---

## 5. Melhoria e Otimização da Arquitetura

### 5.1. Cache para Serviços Externos

- **Proposta:**  
  - Implementação de Elasticache (Redis) para armazenar resultados de consultas aos serviços de Poderes, Pessoas e Cadastro Único, reduzindo latência e carga.

### 5.2. Otimização do Step Functions

- **Melhorias:**  
  - Revisão do fluxo para eliminar gargalos.
  - Implementação de lógica de retry, fallback e circuit breaker.
  - Inclusão de logs detalhados e métricas personalizadas para melhor monitoramento.

### 5.3. Monitoramento e Alertas Proativos

- **Ferramentas:**  
  - AWS CloudWatch, Prometheus, Grafana para monitoramento.
- **Alertas:**  
  - Configuração de notificações (email, SMS, Slack) para falhas, lentidão e anomalias.

### 5.4. Desacoplamento de Serviços

- **Estratégia:**  
  - Utilização de filas e armazenamento local de dados essenciais para minimizar dependências diretas de parceiros.

### 5.5. Validação de Coro e Agrupamentos

- **Solução:**  
  - Criação de um serviço dedicado para centralizar e tornar configuráveis as regras de validação de coro e agrupamentos.

### 5.6. Melhoria na API e Banco de Dados

- **API:**  
  - Padronização de logs e retornos, com documentação atualizada (Swagger/OpenAPI).
- **Banco de Dados:**  
  - Criação de índices adicionais, rotinas de limpeza e campos de auditoria.

---

## 6. Democratização de Dados e Modelagem

### 6.1. Modelagem de Dados

#### Tabela Principal (Envelopes/Ordens)

- **Campos Principais:**  
  - envelope_id (PK)
  - area_id (FK)
  - data_criacao
  - status_envelope (e.g., rascunho, em_processamento, concluido, falha)
  - plataforma_id (FK)
  - meio_assinatura_id (FK)
  - requisitante_id
  - tipo_requisitante (pessoa física, pessoa jurídica)
  - numero_participantes
  - coro_completo (boolean)
  - motivo_falha (caso aplicável)

#### Tabelas de Dimensão

- **Área:**  
  - area_id, sigla_area, centro_custo.
- **Plataforma:**  
  - plataforma_id, nome_plataforma, tipo_plataforma.
- **Meio de Assinatura:**  
  - meio_assinatura_id, tipo_assinatura.
- **Status do Envelope:**  
  - status_envelope, descricao_status.

### 6.2. Benefícios da Democratização dos Dados

- **Otimização do Produto:**  
  - Identificação de gargalos e análise de taxas de sucesso/falha por área, plataforma e meio de assinatura.
- **Melhoria da Experiência do Cliente:**  
  - Fornecimento de insights e relatórios para suporte e treinamento das áreas.
- **Tomada de Decisões Estratégicas:**  
  - Avaliação da adoção do AME e identificação de oportunidades de expansão e melhoria.
- **Geração de Valor:**  
  - Criação de novos relatórios e funcionalidades com base na análise dos dados.
- **Otimização de Custos:**  
  - Análise de fluxos de validação e identificação de parceiros com maior ou menor custo operacional.

### 6.3. Ferramentas para Análise

- **Amazon Athena:** Consultas SQL diretamente no S3.
- **Amazon QuickSight:** Dashboards interativos e visualizações.
- **AWS Glue:** ETL e catálogo de dados para preparação e governança.

---

## 7. Monitoramento e Alertas Proativos

### 7.1. Monitoramento Técnico

- **Infraestrutura:**  
  - Monitoramento de CPU, memória, latência e conexões (RDS, DynamoDB).
- **Processamento:**  
  - Monitoramento do tempo de execução e taxa de falhas (EMR, Glue, Lambda, SageMaker).
- **Mensageria e Armazenamento:**  
  - Taxas de transferência e ingestão (S3, Kinesis).
- **Aplicação:**  
  - Tempo de resposta, logs de erros, exceções e métricas de desempenho.
- **Segurança:**  
  - Detecção de tentativas de acesso não autorizado e vulnerabilidades.

### 7.2. Monitoramento de Negócios

- **Desempenho dos Modelos de Crédito:**  
  - Taxas de aprovação, inadimplência, precisão (AUC, recall, precisão).
- **Qualidade dos Dados:**  
  - Monitoramento de dados faltantes e anomalias.
- **Indicadores de Negócio:**  
  - Volume de crédito, lucratividade, conversão de clientes.

### 7.3. Canais e Níveis de Alerta

- **Canais:**  
  - Email, SMS, Slack/Microsoft Teams e, para incidentes críticos, chamadas telefônicas.
- **Níveis de Severidade:**  
  - Informativo, aviso e crítico.

---

## 8. Plano de Recuperação de Desastres (DR)

### 8.1. Estratégias de DR

- **Backup e Restauração:**  
  - Backups regulares do RDS Aurora para S3, snapshots dos containers no ECS Fargate e backup das configurações dos Step Functions e Lambdas.
- **Multi-Região Ativo-Passivo:**  
  - Replicação do RDS Aurora para uma região secundária e implantação de uma cópia do AME com roteamento dinâmico (via Route 53) em caso de falha.
- **Multi-Região Ativo-Ativo:**  
  - Distribuição do serviço em múltiplas regiões com balanceamento global (Global Accelerator) para reduzir RTO e RPO.

### 8.2. Componentes Essenciais no DR

- **RDS Aurora:**  
  - Replicação multi-AZ, backups automatizados e snapshots.
- **ECS Fargate:**  
  - Implantação em múltiplas zonas de disponibilidade com autoscaling.
- **Step Functions e Lambda:**  
  - Replicação das configurações e código, além de monitoramento contínuo.
- **SQS:**  
  - Filas replicadas com DLQs para tratamento de mensagens não processadas.
- **S3:**  
  - Replicação de buckets e versionamento de objetos.
- **Route 53/Global Accelerator:**  
  - Roteamento e balanceamento de tráfego em cenários de failover.
- **CloudWatch:**  
  - Monitoramento de métricas e logs em todas as regiões.
- **IAM:**  
  - Políticas e permissões replicadas para garantir segurança.

### 8.3. Plano de Implementação do DR

- **Definição de RTO/RPO:**  
  - Determinar o tempo máximo de inatividade e a perda máxima de dados toleráveis.
- **Seleção e Implementação da Estratégia:**  
  - Escolher a estratégia (ativo-passivo ou ativo-ativo) com base nos requisitos e orçamento.
- **Testes e Validação:**  
  - Realizar testes periódicos de failover para validar o plano e identificar melhorias.
- **Documentação e Automação:**  
  - Documentar detalhadamente os procedimentos e automatizar processos de failover e failback.
- **Comunicação:**  
  - Estabelecer um plano de comunicação para notificar as partes interessadas em caso de desastre.

---

## 9. Conclusão

O Assistente de Montagem de Envelope (AME) representa uma solução robusta e escalável para a criação de ordens de assinatura digital. Com uma arquitetura orientada a microsserviços, uso de tecnologias modernas (como RDS Aurora, ECS Fargate, Step Functions, SQS e Lambda) e integração com diversos serviços externos, o AME garante que somente ordens válidas e em conformidade sejam processadas.  

As melhorias propostas – que vão desde a implementação de caches e otimização do fluxo no Step Functions até a criação de um sistema abrangente de monitoramento e alertas – visam reduzir a latência, aumentar a resiliência e simplificar a manutenção. Além disso, a democratização dos dados, por meio de uma modelagem bem definida e do uso de ferramentas analíticas (Athena, QuickSight, Glue), permite gerar insights valiosos para decisões estratégicas e otimização dos modelos de crédito.

Por fim, a implementação de um plano de Recuperação de Desastres (DR) robusto assegura a continuidade do negócio e a proteção dos dados críticos, mesmo em cenários adversos, garantindo alta disponibilidade e confiabilidade do serviço.

Essa abordagem integrada não só otimiza os processos internos, mas também potencializa a experiência dos usuários finais e das áreas parceiras, consolidando o AME como um pilar essencial na estratégia de assinatura digital e na transformação digital da organização.

---
