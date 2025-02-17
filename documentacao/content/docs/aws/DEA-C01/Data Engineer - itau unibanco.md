

## **Big Data (Peso: 30%)**

### **O que é Big Data?**
Big Data refere-se ao grande volume de dados (estruturados, semiestruturados e não estruturados) que são gerados em alta velocidade e variedade, exigindo ferramentas e técnicas específicas para armazenamento, processamento e análise.

### **Princípios do Big Data (3 Vs):**
1. **Volume**: Quantidade massiva de dados.
2. **Velocidade**: Rapidez com que os dados são gerados e processados.
3. **Variedade**: Diferentes tipos de dados (texto, vídeo, áudio, logs, etc.).

### **Desafios do Big Data:**
- **Armazenamento**: Escalabilidade e custo para armazenar grandes volumes de dados.
- **Integração**: Combinação de dados de diferentes fontes e formatos.
- **Análise**: Processamento eficiente para extrair insights.
- **Fast Data**: Processamento em tempo real para decisões rápidas.

### **Tipos de Processamento de Dados:**
- **Batch Processing**: Processamento em lotes (ex: Hadoop MapReduce).
- **Stream Processing**: Processamento contínuo em tempo real (ex: Apache Kafka, Apache Flink).

### **ETL vs ELT:**
- **ETL (Extract, Transform, Load)**: Dados são transformados antes de serem carregados no destino.
- **ELT (Extract, Load, Transform)**: Dados são carregados primeiro e transformados no destino (ex: Data Warehouses modernos).

### **Camadas de Dados:**
1. **Source of Record**: Fonte original dos dados.
2. **Source of Truth**: Fonte confiável e consolidada.
3. **Specialized**: Dados específicos para casos de uso.

### **Tipos de Dados e Formatos:**
- **Estruturados**: Tabelas (ex: CSV, SQL).
- **Semiestruturados**: JSON, XML.
- **Não estruturados**: Vídeos, imagens, logs.
- **Formatos comuns**: Parquet, ORC, Avro (otimizados para Big Data).

### **Qualidade de Dados:**
- **Métricas**: Precisão, completude, consistência, duplicidade, validade.
- **Importância**: Garantir confiabilidade e tomada de decisão assertiva.

### **Infraestrutura de Sistemas Distribuídos:**
- **Hadoop**: Framework para processamento distribuído.
  - **Componentes**: HDFS (armazenamento), MapReduce (processamento), YARN (gerenciamento de recursos).
  - **Vantagens**: Escalabilidade, tolerância a falhas.
  - **Desvantagens**: Complexidade e latência.

### **Apache Spark:**
- **Características**: Processamento em memória, suporte a batch e streaming.
- **Conceitos**: RDDs (Resilient Distributed Datasets), DataFrames, APIs.
- **Vantagens**: Velocidade, facilidade de uso.
- **Desvantagens**: Consumo de memória.

---

## **AWS (Peso: 28%)**

### **Serviços Gerais da AWS:**
- **Computação**:
  - **EC2**: Máquinas virtuais escaláveis.
  - **Lambda**: Computação sem servidor (serverless).
- **Integração**:
  - **SQS**: Filas de mensagens.
  - **SNS**: Notificações e pub/sub.
  - **API Gateway**: Gerenciamento de APIs.
  - **Route 53**: DNS.
  - **CodePipeline**: CI/CD.
- **Segurança**:
  - **IAM**: Gerenciamento de acesso.
  - **KMS**: Gerenciamento de chaves de criptografia.
- **Armazenamento**:
  - **S3**: Armazenamento de objetos.
  - **RDS**: Bancos de dados relacionais.
  - **DynamoDB**: Banco de dados NoSQL.
  - **ECS**: Contêineres.
  - **Storage Gateway**: Integração de armazenamento local com a nuvem.

### **Data Tools:**
- **Glue**: ETL gerenciado.
- **Redshift**: Data Warehouse.
- **Athena**: Consultas SQL em dados no S3.

### **FinOps:**
- **Acompanhamento de Custos**: AWS Cost Explorer, Budgets.
- **Otimização**: Uso de instâncias reservadas, spot instances, e arquitetura eficiente.

---

## **Banco de Dados (Peso: 15%)**

### **O que são Bancos de Dados?**
Sistemas para armazenar, organizar e recuperar dados de forma eficiente.

### **Tipos de Bancos de Dados:**
- **Relacionais**: SQL (ex: MySQL, PostgreSQL).
- **NoSQL**: Documentos (MongoDB), Chave-Valor (DynamoDB), Grafos (Neo4j).

### **Modelagem de Dados:**
- **Conceitual**: Visão geral dos dados.
- **Lógica**: Estrutura detalhada.
- **Física**: Implementação no banco.

### **Chaves:**
- **Primária**: Identificador único.
- **Secundária**: Indexação para consultas rápidas.
- **Composta**: Combinação de colunas.

### **SQL:**
- **Sintaxe**: SELECT, JOIN, GROUP BY, ORDER BY.
- **Resultados**: Tabelas, agregações, filtros.

### **Data Warehouse:**
- **Definição**: Repositório centralizado para análise.
- **Componentes**: ETL, OLAP, Data Marts.
- **Arquitetura**: Inmon vs Kimball.

---

## **Programação (Peso: 12,5%)**

### **Fundamentos:**
- **Algoritmos**: Lógica de programação.
- **Operadores**: Condicionais (if-else), lógicos (AND, OR).
- **Programação Distribuída**: Paralelismo e concorrência.

---

## **DevOps (Peso: 10%)**

### **O que é DevOps?**
Cultura e práticas para integração entre desenvolvimento e operações.

### **Ferramentas:**
- **Shell Script**: Automação de tarefas.
- **Git**: Versionamento de código.
- **Observability**: Monitoramento, logs, métricas.

---

## **DataMesh (Peso: 4,5%)**

### **O que é DataMesh?**
Paradigma que descentraliza a gestão de dados, tratando-os como produtos.

### **Vantagens:**
- Escalabilidade.
- Autonomia das equipes.

### **Desvantagens:**
- Complexidade de governança.
- Comparado a **Data Lake**: Menos centralizado, mas mais organizado.

---
