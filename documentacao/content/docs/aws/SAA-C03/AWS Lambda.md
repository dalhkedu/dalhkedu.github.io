---
title: "AWS Lambda"
---

### **AWS Lambda: Visão Geral**
**O que é**:  
O Lambda é um serviço de computação **serverless** que executa código em resposta a eventos sem exigir provisionamento ou gerenciamento de servidores. Você paga apenas pelo tempo de execução e pelo número de solicitações, tornando-o ideal para workloads event-driven e de curta duração.

#### **Características Principais**:
- **Serverless**: Sem gerenciamento de infraestrutura (patches, escalonamento, disponibilidade).
- **Escalonamento Automático**: Processa milhares de solicitações em paralelo instantaneamente.
- **Modelo de Preço**: Cobrança por solicitação (US$ 0,20 por 1 milhão de solicitações) e por tempo de execução (US$ 0,0000166667 por GB-segundo).
- **Tempo Máximo de Execução**: 15 minutos por função (limite atual).
- **Integrações Nativa**: Conecta-se facilmente a serviços como S3, DynamoDB, API Gateway, SNS, SQS, etc.
- **Runtimes Suportados**: Python, Node.js, Java, Go, .NET, Ruby, e custom runtimes via containers.

---

### **Casos de Uso do Lambda**
1. **Processamento de Eventos**:
   - Executar código em resposta a uploads no S3 (ex: redimensionar imagens).
   - Processar streams de dados em tempo real (Kinesis, DynamoDB Streams).
   - Disparar ações após mudanças em bancos de dados (ex: DynamoDB Triggers).

2. **Backend para APIs**:
   - Criar APIs RESTful ou GraphQL com **API Gateway** (arquitetura serverless).
   - Servir conteúdo dinâmico para aplicações web/mobile.

3. **Automação de Tarefas**:
   - Executar scripts periódicos (via CloudWatch Events/EventBridge).
   - Processar filas de mensagens (SQS/SNS).

4. **ETL (Extract, Transform, Load)**:
   - Transformar dados antes de armazená-los em data lakes (ex: S3 → Lambda → Redshift).

---

### **Vantagens do Lambda**
- **Custo-Efetivo**: Ideal para workloads esporádicos (não paga por ociosidade).
- **Escalabilidade Automática**: Lida com picos de tráfego sem intervenção manual.
- **Integração com Ecossistema AWS**: Facilmente acionado por mais de 200 serviços.
- **Foco no Código**: Equipes concentram-se na lógica de negócio, não em infraestrutura.

---

### **Limitações do Lambda**
- **Cold Starts**: Latência inicial quando uma função é executada após período de inatividade (pode afetar aplicações sensíveis a tempo real).
- **Limites de Recursos**:
  - Memória: 128 MB a 10 GB.
  - Armazenamento Temporário (Ephemeral Storage): 512 MB a 10 GB (configurável).
  - Tamanho do Pacote de Implantação: 250 MB (50 MB via console).
- **Tempo de Execução Fixo**: Máximo de 15 minutos (não adequado para processos longos).
- **Depuração Complexa**: Requer ferramentas como CloudWatch Logs e X-Ray.

---

### **Comparação com Outros Serviços**

#### **Lambda vs. EC2**
| **Critério**            | **Lambda**                                  | **EC2**                                      |
|-------------------------|---------------------------------------------|----------------------------------------------|
| **Gerenciamento**        | AWS gerencia tudo.                          | Você gerencia OS, patches, escalonamento.    |
| **Escalonamento**        | Automático e instantâneo.                   | Requer Auto Scaling Groups (minutos).        |
| **Custo**                | Pague por uso (milissegundos).              | Pague por hora/segundo (instância ativa).    |
| **Casos de Uso**         | Eventos esporádicos, funções de curta duração. | Workloads contínuos, aplicações stateful.    |

**Melhor Escolha**:  
- Use **Lambda** para tarefas event-driven (ex: processar uploads no S3).  
- Use **EC2** para workloads estáveis (ex: servidor web 24/7).

---

#### **Lambda vs. ECS/Fargate**
| **Critério**            | **Lambda**                                  | **ECS/Fargate**                              |
|-------------------------|---------------------------------------------|----------------------------------------------|
| **Abstração**            | Funções serverless (sem containers).        | Containers Docker gerenciados.               |
| **Tempo de Execução**    | Até 15 minutos.                             | Sem limite (depende da configuração).        |
| **Escalonamento**        | Automático por solicitação.                 | Escalonamento baseado em métricas (CPU/RAM). |
| **Casos de Uso**         | Microserviços leves, funções stateless.     | Aplicações containerizadas de longa duração. |

**Melhor Escolha**:  
- Use **Lambda** para funções simples e stateless.  
- Use **ECS/Fargate** para aplicações containerizadas complexas ou long-running tasks.

---

#### **Lambda vs. Elastic Beanstalk**
| **Critério**            | **Lambda**                                  | **Elastic Beanstalk**                        |
|-------------------------|---------------------------------------------|-----------------------------------------------|
| **Modelo**              | Serverless (funções individuais).           | PaaS (gerencia instâncias EC2, balanceadores).|
| **Escopo**              | Ideal para microsserviços event-driven.     | Adequado para aplicações web monolíticas.     |
| **Controle**            | Nenhum controle sobre infraestrutura.       | Controle limitado (foco no deploy de apps).   |

**Melhor Escolha**:  
- Use **Lambda** para APIs serverless ou automação.  
- Use **Elastic Beanstalk** para deploy rápido de apps web tradicionais.

---

### **Cenários Específicos e Recomendações**

#### **Cenário 1: Processamento de Imagens no S3**
- **Problema**: Redimensionar imagens automaticamente após upload no S3.  
- **Solução**: Lambda é acionado pelo evento `S3:ObjectCreated`, executa código para redimensionar e salvar a imagem em outro bucket.  
- **Por que Lambda**: Baixo custo (só executa quando há uploads), escalabilidade automática.

#### **Cenário 2: API Backend para Aplicação Mobile**
- **Problema**: Criar uma API REST para uma aplicação com tráfego imprevisível.  
- **Solução**: API Gateway + Lambda (serverless).  
- **Vantagem**: Escalabilidade automática durante picos de acesso.

#### **Cenário 3: Processamento de Dados em Tempo Real (Kinesis)**
- **Problema**: Analisar dados de sensores IoT em tempo real.  
- **Solução**: Lambda consome streams do Kinesis e processa registros individualmente.  
- **Por que Lambda**: Integração nativa com Kinesis, processamento paralelo.

---

### **Considerações para o Exame SAA-C03**
1. **Cold Starts**:  
   - Ocorrem quando uma função é executada após um período de inatividade.  
   - Mitigue com **Provisioned Concurrency** (mantém instâncias "quentes").

2. **Segurança**:  
   - Funções Lambda precisam de **IAM Roles** para acessar outros serviços (ex: S3, DynamoDB).  
   - Evite permissões excessivas (princípio do menor privilégio).

3. **VPC vs. Sem VPC**:  
   - Funções fora de VPC têm menor latência (ideal para serviços públicos).  
   - Funções em VPC acessam recursos privados (ex: RDS), mas podem ter cold starts mais longos.

4. **Monitoramento**:  
   - Use **CloudWatch Logs** para rastrear execuções.  
   - **AWS X-Ray** ajuda a depurar latência e gargalos.

5. **Limites e Cotas**:  
   - Conheça os limites de concorrência (1.000 execuções simultâneas por padrão).  
   - Solicite aumento de cotas se necessário.

---

### **Padrões Arquiteturais com Lambda**
1. **Serverless APIs**:  
   - API Gateway + Lambda + DynamoDB (arquitetura comum para aplicações web/mobile).

2. **Fan-Out/Fan-In**:  
   - Use **SNS** ou **EventBridge** para disparar múltiplas funções Lambda em paralelo.

3. **Step Functions**:  
   - Orquestre funções Lambda em workflows complexos com retry e error handling.

---

### **Resumo das Melhores Práticas**
- **Stateless**: Nunca armazene estado localmente (use S3, DynamoDB ou ElastiCache).  
- **Funções Pequenas**: Mantenha o código conciso para reduzir tempo de execução.  
- **Versões e Aliases**: Use versionamento para implantar atualizações sem downtime.  
- **Layers**: Compartilhe bibliotecas entre funções usando **Lambda Layers**.

---

### **Quando NÃO Usar Lambda**
- Processos que exigem execução contínua (>15 minutos).  
- Aplicações que dependem de estado local (ex: sessões de usuário).  
- Workloads de alto desempenho com uso intensivo de CPU/GPU (prefira EC2 ou ECS).

---
