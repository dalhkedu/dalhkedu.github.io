---
title: "Amazon EMR"
---

https://docs.aws.amazon.com/pt_br/emr/latest/ManagementGuide/emr-gs.html

### **1. Visão Geral do Amazon EMR**
- **O que é:** Um serviço gerenciado para processamento de big data usando frameworks de código aberto.
- **Casos de Uso Comuns:**
  - Processamento de grandes volumes de dados (ETL).
  - Análise de dados em tempo real.
  - Machine learning e análise preditiva.
  - Processamento de logs e dados de sensores.

---

### **2. Componentes do Amazon EMR**
#### **Clusters**
- **Definição:** Um conjunto de instâncias EC2 que executam frameworks de big data.
- **Tipos de Nós:**
  - **Master Node:** Gerencia o cluster e coordena tarefas.
  - **Core Node:** Executa tarefas e armazena dados no HDFS (Hadoop Distributed File System).
  - **Task Node:** Executa tarefas, mas não armazena dados (opcional).

#### **Frameworks Suportados**
- **Apache Hadoop:** Para processamento distribuído de grandes volumes de dados.
- **Apache Spark:** Para processamento em memória e análise de dados em tempo real.
- **Apache HBase:** Para banco de dados NoSQL distribuído.
- **Apache Flink:** Para processamento de streams em tempo real.
- **Presto:** Para consultas SQL interativas em grandes volumes de dados.

#### **Integrações**
- **Amazon S3:** Armazenamento de dados brutos e processados.
- **AWS Glue:** Catalogação e preparação de dados.
- **Amazon Redshift:** Análise de dados em um data warehouse.
- **Amazon Athena:** Consulta de dados diretamente no S3.

---

### **3. Funcionalidades Principais**
#### **Escalabilidade**
- **Auto Scaling:** Ajusta automaticamente o número de instâncias com base na carga.
- **Spot Instances:** Reduz custos usando instâncias EC2 spot.

#### **Desempenho**
- **HDFS:** Armazenamento distribuído para dados processados no cluster.
- **EBS (Elastic Block Store):** Armazenamento persistente para dados temporários.
- **Optimized Instances:** Instâncias EC2 otimizadas para big data.

#### **Segurança**
- **IAM:** Controle de acesso usando políticas do IAM.
- **VPC:** Execução em VPCs para isolamento de rede.
- **Cifragem:** Dados podem ser cifrados em repouso e em trânsito usando AWS KMS.

#### **Monitoramento**
- **CloudWatch:** Monitora métricas como uso de CPU, memória e armazenamento.
- **Logs:** Armazena logs de execução no S3 ou CloudWatch Logs.

---

### **4. Melhores Práticas**
#### **Desempenho**
- **Escolha de Instâncias:** Use instâncias otimizadas para big data (ex.: instâncias com alto desempenho de rede e armazenamento).
- **Particionamento de Dados:** Particione dados no S3 para melhorar o desempenho de consultas.
- **Uso de Spot Instances:** Reduza custos usando instâncias spot para tarefas tolerantes a falhas.

#### **Segurança**
- **IAM:** Use políticas granulares para controlar o acesso ao EMR e aos dados.
- **VPC:** Execute clusters em uma VPC para isolamento de rede.
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.

#### **Custos**
- **Auto Scaling:** Ajuste o tamanho do cluster com base na demanda para otimizar custos.
- **Spot Instances:** Use instâncias spot para tarefas tolerantes a falhas.
- **Terminação de Clusters:** Configure clusters para terminar automaticamente após a conclusão das tarefas.

---

### **5. Tópicos Relevantes para o Exame**
- **Arquitetura:** Entenda a diferença entre Master Node, Core Node e Task Node.
- **Frameworks:** Conheça os frameworks suportados (Hadoop, Spark, HBase, Flink, Presto).
- **Integrações:** Como o EMR se integra a S3, Glue, Redshift e Athena.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Processamento de grandes volumes de dados, análise em tempo real e machine learning.

---

### **6. Exemplos de Perguntas do Exame**
1. **Qual framework é recomendado para processamento em memória e análise de dados em tempo real no Amazon EMR?**
   - A) Apache Hadoop  
   - B) Apache Spark  
   - C) Apache HBase  
   - D) Presto  
   **Resposta:** B) Apache Spark.

2. **Qual tipo de nó no Amazon EMR é responsável por armazenar dados no HDFS?**
   - A) Master Node  
   - B) Core Node  
   - C) Task Node  
   - D) Edge Node  
   **Resposta:** B) Core Node.

3. **Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon EMR?**
   - A) Usar instâncias spot para tarefas tolerantes a falhas.  
   - B) Manter clusters em execução 24/7, mesmo quando não estiverem em uso.  
   - C) Usar instâncias com alto desempenho para todas as tarefas.  
   - D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   **Resposta:** A) Usar instâncias spot para tarefas tolerantes a falhas.

4. **Qual serviço da AWS pode ser usado para monitorar métricas como uso de CPU e memória no Amazon EMR?**
   - A) AWS CloudTrail  
   - B) Amazon CloudWatch  
   - C) AWS Config  
   - D) AWS Trusted Advisor  
   **Resposta:** B) Amazon CloudWatch.

---

### **7. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um cluster EMR e execute um job de processamento de dados usando Apache Spark.
  - Configure o EMR para usar instâncias spot e auto scaling.
  - Integre o EMR com o Amazon S3 e AWS Glue para processamento de dados.

---
