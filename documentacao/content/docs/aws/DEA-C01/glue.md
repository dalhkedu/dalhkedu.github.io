---
title: "AWS Glue"
---

https://docs.aws.amazon.com/pt_br/glue/latest/dg/what-is-glue.html


### **1. Visão Geral do AWS Glue**
- **O que é:** Serviço totalmente gerenciado para ETL, que automatiza a descoberta, transformação e movimentação de dados.
- **Casos de Uso Comuns:**
  - Preparação de dados para análise.
  - Criação de data lakes.
  - Integração de dados de múltiplas fontes.
  - Catalogação de metadados (Data Catalog).

---

### **2. Componentes Principais do AWS Glue**
#### **Data Catalog**
- **O que é:** Repositório centralizado de metadados que descreve os dados armazenados na AWS.
- **Tabelas:** Representam a estrutura dos dados (ex.: colunas, tipos de dados).
- **Crawlers:** Ferramentas que automatizam a descoberta de esquemas e a criação de tabelas no Data Catalog.

#### **ETL Jobs**
- **O que é:** Tarefas que extraem, transformam e carregam dados.
- **Tipos de Jobs:**
  - **Spark:** Usa Apache Spark para processamento distribuído.
  - **Python Shell:** Para scripts Python simples.
- **Scripts:** Gerados automaticamente pelo AWS Glue ou personalizados pelo usuário.

#### **Desenvolvimento e Execução**
- **Desenvolvimento:** Usa o AWS Glue Studio (interface visual) ou scripts Python/Scala.
- **Execução:** Pode ser acionado manualmente, por agendamento ou por eventos (ex.: novo arquivo no S3).

#### **Conexões e Conexores**
- **Conexões:** Configurações para acessar fontes de dados (ex.: JDBC para bancos de dados).
- **Conexores:** Integrações pré-construídas com serviços como S3, Redshift, RDS, DynamoDB e Kafka.

---

### **3. Funcionalidades Avançadas**
#### **Dynamic Frames**
- **O que é:** Estrutura de dados flexível usada no AWS Glue para lidar com esquemas dinâmicos ou desconhecidos.
- **Vantagens:** Tolerante a erros e capaz de inferir esquemas automaticamente.

#### **Job Bookmarks**
- **O que é:** Rastreia os dados já processados por um job, evitando reprocessamento.
- **Casos de Uso:** Útil para pipelines incrementais.

#### **Workflows**
- **O que é:** Orquestra múltiplos jobs e crawlers em uma sequência definida.
- **Benefícios:** Automatiza pipelines complexos de ETL.

#### **DataBrew**
- **O que é:** Ferramenta visual para limpeza e transformação de dados, integrada ao AWS Glue.
- **Vantagens:** Facilita a preparação de dados para usuários não técnicos.

---

### **4. Integrações com Outros Serviços AWS**
- **Amazon S3:** Fonte e destino comum para dados brutos e processados.
- **Amazon Redshift:** Carregamento de dados transformados em um data warehouse.
- **Amazon Athena:** Consulta de dados catalogados no Data Catalog.
- **Amazon RDS e DynamoDB:** Fontes de dados para ETL.
- **AWS Lambda:** Execução de funções personalizadas durante o processo de ETL.
- **Amazon CloudWatch:** Monitoramento de jobs e crawlers.

---

### **5. Melhores Práticas**
- **Organização de Dados:**
  - Use prefixos no S3 para organizar dados brutos e processados.
  - Particione tabelas no Data Catalog para otimizar consultas.
- **Desempenho:**
  - Escolha o tipo de job adequado (Spark para grandes volumes, Python Shell para tarefas simples).
  - Use Dynamic Frames para lidar com esquemas complexos.
- **Segurança:**
  - Use IAM para controlar o acesso ao AWS Glue e aos dados.
  - Cifre dados em trânsito e em repouso.
- **Custos:**
  - Agende jobs e crawlers para executar apenas quando necessário.
  - Use Job Bookmarks para evitar reprocessamento.

---

### **6. Tópicos Relevantes para o Exame**
- **Data Catalog:** Entenda como os crawlers funcionam e como as tabelas são criadas.
- **ETL Jobs:** Saiba configurar e executar jobs, incluindo o uso de scripts e Dynamic Frames.
- **Integrações:** Como o AWS Glue se integra a S3, Redshift, Athena e outros serviços.
- **Segurança:** Controle de acesso com IAM e cifragem de dados.
- **Casos de Uso:** Preparação de dados para análise, criação de data lakes e pipelines de ETL.

---

### **7. Exemplos de Perguntas do Exame**
1. **Qual componente do AWS Glue é responsável por descobrir esquemas de dados e criar tabelas no Data Catalog?**
   - A) ETL Jobs  
   - B) Crawlers  
   - C) Dynamic Frames  
   - D) Workflows  
   **Resposta:** B) Crawlers.

2. **Qual das seguintes opções é uma vantagem do uso de Dynamic Frames no AWS Glue?**
   - A) Eles são mais rápidos que os DataFrames do Spark.  
   - B) Eles podem inferir esquemas automaticamente.  
   - C) Eles não requerem scripts para transformação.  
   - D) Eles são usados apenas para consultas SQL.  
   **Resposta:** B) Eles podem inferir esquemas automaticamente.

3. **Você precisa garantir que um job do AWS Glue processe apenas novos dados adicionados a um bucket S3. Qual recurso você deve usar?**
   - A) Data Catalog  
   - B) Job Bookmarks  
   - C) Dynamic Frames  
   - D) Workflows  
   **Resposta:** B) Job Bookmarks.

4. **Qual serviço da AWS pode ser usado para consultar dados catalogados no AWS Glue Data Catalog?**
   - A) Amazon Redshift  
   - B) Amazon Athena  
   - C) Amazon EMR  
   - D) AWS Lambda  
   **Resposta:** B) Amazon Athena.

---

### **8. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um crawler para catalogar dados no S3.
  - Configure e execute um job de ETL para transformar dados.
  - Use o AWS Glue Studio para criar um workflow visual.

---
