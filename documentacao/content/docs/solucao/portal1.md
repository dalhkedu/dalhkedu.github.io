## 1. Introdução

O Portal de Documentos é uma solução AWS que visa oferecer uma interface gráfica (GUI) para a criação, consulta e gerenciamento de ordens de assinatura digital. Destinado a usuários que preferem interagir via interface em vez de APIs, o portal integra-se ao Assistente de Montagem de Envelope (AME) e aos serviços de domínios, possibilitando a criação de ordens para áreas cadastradas no Parametrizador. A solução permite a manipulação de contratos (documentos) armazenados no S3 e mantém o histórico de envelopes no RDS Aurora.

---

## 2. Objetivos e Escopo

- **Facilitar a Criação de Ordens:**  
  Permitir que os usuários criem ordens de assinatura digital sem necessidade de interação direta com APIs, utilizando uma interface intuitiva.
  
- **Integração com Serviços Existentes:**  
  Consumir os serviços do AME para armazenar rascunhos e atualizar ordens, além de utilizar o serviço de domínios para recuperar nomes e chaves de funcionalidades.

- **Gestão Completa das Ordens:**  
  Oferecer funcionalidades para consulta (ordens em andamento, rascunhos), edição e clonagem de ordens, além de ações específicas como reenvio de notificações e cancelamento de ordens.

- **Suporte a Débitos Técnicos:**  
  Exibir erros provenientes do Step Functions, permitindo que o usuário retome ordens salvas como rascunho e realize ajustes para efetivação ou cancelamento.

---

## 3. Arquitetura Técnica

### 3.1. Componentes e Tecnologias

- **Backend:**  
  - **ECS Fargate com Java Spring Boot:** Responsável pela lógica de negócio e integração com serviços externos (AME, domínios, poderes, registro de pessoas).

- **Frontend:**  
  - **Angular hospedado no S3 e distribuído via CloudFront:** Interface responsiva e moderna para interação dos usuários.

- **Armazenamento de Documentos:**  
  - **S3:** Armazenamento dos contratos e documentos enviados via presigned URL (upload multipart).

- **Banco de Dados:**  
  - **RDS Aurora:** Armazena as informações dos envelopes de assinatura, mantendo o histórico e os estados das ordens.

- **Integração com Serviços Externos:**  
  - **Consumo do AME:** Para criação, edição e atualização dos rascunhos de ordens.  
  - **Serviço de Domínios:** Para recuperar nomes e chaves que padronizam as funcionalidades e regras do sistema.

---

### 3.2. Fluxo de Operação

#### Criação de Ordens (Etapa 1)

1. **Dados Iniciais:**  
   - O usuário preenche os dados do requisitante (ex.: CNPJ), acionando uma consulta via BFF para obter o nome da empresa a partir do serviço de registro de pessoas.

2. **Seleção de Área:**  
   - O sistema consulta o Parametrizador para recuperar os dados padrão da área (incluindo funcionalidades e regras pré-definidas).  
   - Dados não preenchidos automaticamente deverão ser informados manualmente (ex.: conta, agência, DAC, valor da ordem, nome do contato, código do contrato).

3. **Upload de Contrato:**  
   - Utilizando a funcionalidade de "presigned URL", o usuário realiza o upload do arquivo (contrato) para o S3.

4. **Consulta a Poderes e Criação do Rascunho:**  
   - Após o upload, o sistema consulta o serviço de poderes para obter representantes e regras do requisitante.  
   - Em seguida, o AME é chamado para armazenar os dados como rascunho, gerando um ID e chave de ordem.  
   - Caso o processo seja interrompido, o rascunho fica disponível para continuidade.

#### Complementação e Finalização (Etapa 2)

1. **Adição de Participantes:**  
   - O usuário pode incluir garantidores e outras pessoas além dos representantes já recuperados.  
   - São apresentadas informações como nome, email, telefone e ressalvas (que, embora não impeçam a continuidade, devem ser analisadas pela área responsável).

2. **Validação e Atualização:**  
   - Caso seja necessário, o sistema realiza nova consulta em serviços (registro de pessoas e base própria do portal) para atualizar os dados de participantes.  
   - Participantes podem ser ativados ou desativados para seguir na ordem.

3. **Inclusão de Aprovadores e Observadores:**  
   - É possível vincular aprovadores e observadores (pessoas físicas ou jurídicas) à ordem, com a possibilidade de edição dos dados.

4. **Definição de Regras e Agrupamentos:**  
   - O sistema exibe as regras provenientes do serviço de poderes, mostrando agrupamentos e definições de assinatura (quem assina com quem e condições para assinaturas individuais ou em conjunto).

#### Funcionalidades Adicionais

- **Consulta de Ordens:**  
  - Visualização de todas as ordens (concluídas, canceladas, pendentes, expiradas e recusadas) e rascunhos.

- **Ações no Detalhe da Ordem:**  
  - Possibilidade de reenvio de email, notificação via SMS, cópia de link e visualização dos eventos de cada participante (aceitação de termos, download do contrato etc.).

- **Edição e Clonagem:**  
  - Acesso para editar ordens rascunho ou para clonar ordens já finalizadas, com atualização automática dos dados (em razão de possíveis alterações nos registros de pessoas e poderes).

- **Cancelamento de Ordens:**  
  - Usuários autorizados podem cancelar ordens em andamento, justificando o cancelamento (ex.: liberação via contrato manual), o que remove a ordem da visão do cliente.

---

## 4. Débitos Técnicos e Propostas de Melhoria

### 4.1. Débitos Técnicos Identificados

- **Tratamento de Erros do Step Functions:**  
  - Exibir os erros retornados para ordens criadas via API do AME, permitindo ao usuário retomar e corrigir o rascunho.

- **Cancelamento de Ordens:**  
  - Falta de funcionalidade nativa para cancelamento, exigindo a implementação de rotina para atualização de status e notificação dos participantes.

- **Criação de Regras Sem Consulta de Poderes:**  
  - Necessidade de permitir que áreas definam regras e agrupamentos manualmente, sem depender exclusivamente da consulta ao serviço de poderes.

- **Padronização de Logs e Auditoria:**  
  - Falta de padronização dos logs das ações realizadas na interface, dificultando a rastreabilidade das operações.

### 4.2. Propostas de Melhoria

- **Exibição Detalhada de Erros:**  
  - Implementar mecanismos para exibir os detalhes dos erros do Step Functions diretamente na interface, com opções de edição para retomar o processo.

- **Funcionalidade de Cancelamento:**  
  - Permitir que usuários autorizados possam cancelar ordens em andamento, com justificativas, atualização de status no banco de dados e envio de notificações.

- **Interface para Regras e Agrupamentos:**  
  - Criar uma funcionalidade que permita a criação e ajuste de regras e agrupamentos diretamente pelo Portal, com validações de conformidade.

- **Otimização e Validação em Tempo Real:**  
  - Implementar validação dos dados enquanto o usuário preenche os formulários, reduzindo erros e aumentando a eficiência.

- **Logs Padronizados e Auditoria:**  
  - Adicionar campos de log em todas as ações realizadas no portal, facilitando a auditoria e o monitoramento do uso.

---

## 5. Melhoria na Arquitetura do Portal (Pilares do AWS Well-Architected Framework)

### 5.1. Segurança (Secure Architectures)

- **Controle de Acesso ao S3:**  
  - Políticas de bucket para restringir o acesso aos documentos com base em funções.
  
- **Auditoria e Monitoramento:**  
  - Integração com AWS CloudTrail, além de um sistema de logs de auditoria no banco de dados.

- **Proteção Adicional:**  
  - Uso do AWS WAF para mitigar ataques comuns na web.

### 5.2. Resiliência (Resilient Architectures)

- **Alta Disponibilidade:**  
  - Multi-AZ no ECS Fargate e backups automatizados do RDS Aurora e S3.
  
- **Recuperação de Desastres:**  
  - Plano DR multi-região com failover automatizado e replicação de buckets S3.

- **Mensageria:**  
  - Implementação de Dead Letter Queues (DLQs) para tratar mensagens com falha no SQS.

### 5.3. Desempenho (High-Performing Architectures)

- **Cache e Otimização de Consultas:**  
  - Utilização de Elasticache (Redis) e índices otimizados no RDS.
  
- **Distribuição de Conteúdo:**  
  - Uso do CloudFront para cache e distribuição rápida dos conteúdos do frontend.

- **Monitoramento Contínuo:**  
  - Uso do CloudWatch para monitorar métricas de performance e identificar gargalos.

### 5.4. Otimização de Custos (Cost-Optimized Architectures)

- **Autoscaling e Dimensionamento:**  
  - Ajuste automático do ECS Fargate conforme a demanda e uso de instâncias reservadas/spot no RDS.
  
- **Políticas de Ciclo de Vida:**  
  - Implementação de políticas no S3 para mover documentos antigos para classes de armazenamento mais econômicas.

---

## 6. Monitoramento, Alertas e Plano de Recuperação de Desastres (DR)

### 6.1. Monitoramento e Alertas

- **Infraestrutura:**  
  - Monitoramento via CloudWatch, Prometheus/Grafana e ELK Stack para métricas (CPU, memória, latência) do ECS Fargate, RDS, S3/CloudFront e SQS.
  
- **Aplicação e Negócios:**  
  - Acompanhamento do tempo de resposta das APIs, taxa de erros, número de ordens criadas/alteradas e status dos participantes.
  
- **Alertas e Ações Proativas:**  
  - Configuração de alertas via email, SMS, Slack ou Teams para diferentes níveis de severidade (informativo, aviso, crítico).

### 6.2. Plano de Recuperação de Desastres (DR)

- **Objetivos (RTO/RPO):**  
  - Definir tempo máximo para recuperação e perda de dados aceitável.
  
- **Estratégias de Backup e Replicação:**  
  - Backups diários do RDS Aurora e S3 com versionamento, snapshots semanais do ECS e replicação multi-região.
  
- **Procedimentos de Failover e Failback:**  
  - Uso do Route 53 para direcionamento de tráfego e testes periódicos para validação do plano DR.

---

## 7. Experiência do Usuário (UX) e Funcionalidades Adicionais

### 7.1. Fluxo de Criação e Edição de Ordens

- **Etapa 1 – Preenchimento Inicial:**  
  - Formulário dividido em etapas, com validação de CNPJ, seleção da área (com dados padronizados do Parametrizador) e upload do contrato.
  
- **Etapa 2 – Complementação e Adição de Participantes:**  
  - Inclusão de garantidores, atualização dos dados dos participantes e visualização das ressalvas.  
  - Consulta aos serviços de poderes e atualização automática dos registros de pessoas.

- **Etapa 3 – Visualização de Regras e Confirmação:**  
  - Exibição das regras, agrupamentos e fluxos de assinatura, com possibilidade de edição final antes do envio da ordem.

### 7.2. Funcionalidades Complementares

- **Consulta e Histórico de Ordens:**  
  - Listagem de ordens por status (rascunho, pendente, concluída, cancelada, etc.) e visualização detalhada dos eventos de cada participante.
  
- **Clonagem e Edição de Rascunhos:**  
  - Reaproveitamento de dados de ordens anteriores, com atualização dinâmica dos registros de pessoas e poderes para agilizar o processo.

- **Ação de Cancelamento:**  
  - Permitir o cancelamento de ordens em andamento, com justificativas e atualização dos status nos registros.

---

## 8. Democratização de Dados e Geração de Insights

### 8.1. Arquitetura de Dados para Análise

- **Coleta e Armazenamento:**  
  - Integração de dados do Portal (RDS, logs, APIs, S3) em um Data Lake centralizado no Amazon S3.
  
- **Processamento e Catalogação:**  
  - Uso do AWS Glue e do Data Catalog para transformação e organização dos dados.
  
- **Ferramentas de Análise:**  
  - Amazon Athena para consultas SQL e Amazon QuickSight para dashboards e relatórios que suportem decisões estratégicas.

### 8.2. Benefícios da Democratização

- **Otimização dos Processos:**  
  - Identificação de gargalos na criação e gestão das ordens, além da análise de performance das funcionalidades.
  
- **Eficiência Operacional:**  
  - Automatização de relatórios e dashboards para monitoramento em tempo real, possibilitando ações corretivas imediatas.
  
- **Tomada de Decisões:**  
  - Insights detalhados sobre a adoção do Portal, taxa de conversão de rascunhos e eficiência dos fluxos de assinatura, apoiando decisões estratégicas e de investimento.

---

## 9. Conclusão

O Portal de Documentos representa uma solução moderna e escalável para a gestão de ordens de assinatura digital, integrando tecnologias como ECS Fargate, CloudFront, Angular, S3 e RDS Aurora. A interface gráfica possibilita que usuários criem, editem, consultem e monitorem ordens com facilidade, sem a necessidade de interagir diretamente com APIs.

A arquitetura atual, embora robusta, apresenta desafios que podem ser mitigados com melhorias no tratamento de erros do Step Functions, na padronização dos logs, na criação de regras manuais e na implementação de mecanismos de cancelamento e auditoria. As propostas de melhoria, aliadas aos pilares do AWS Well-Architected Framework (segurança, resiliência, desempenho e otimização de custos), garantem uma solução mais segura, performática e de fácil manutenção.

Além disso, a democratização dos dados do portal, por meio de uma arquitetura de dados integrada, possibilita a geração de insights estratégicos, contribuindo para a melhoria contínua do produto e a tomada de decisões mais informadas.

Em suma, com a implementação das melhorias sugeridas, o Portal de Documentos se consolidará como uma ferramenta essencial para a gestão de ordens de assinatura digital, oferecendo uma experiência de usuário aprimorada e garantindo eficiência operacional e segurança em todos os níveis do processo.

---
