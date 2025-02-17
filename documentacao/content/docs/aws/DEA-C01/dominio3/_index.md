---
title: "Domínio 3: Processamento de Dados"
---

## **1. Transformar Dados Usando Serviços AWS**
A transformação de dados envolve a conversão, limpeza e enriquecimento de dados brutos para torná-los úteis para análise e tomada de decisões. A AWS oferece vários serviços para essa finalidade:

### **Serviços de Transformação de Dados**
1. **AWS Glue:** [Leitura](../glue)
   - **O que é:** Um serviço de ETL (Extract, Transform, Load) totalmente gerenciado.
   - **Casos de Uso:**
     - Preparação de dados para análise.
     - Catalogação de metadados no Glue Data Catalog.
     - Integração com S3, Redshift, RDS e DynamoDB.
   - **Funcionalidades:**
     - **Glue Jobs:** Execução de scripts Python ou Scala para transformação de dados.
     - **Glue Crawlers:** Descoberta automática de esquemas de dados.
     - **Glue DataBrew:** Ferramenta visual para limpeza e transformação de dados.

2. **AWS Lambda:** [Leitura](../lambda)
   - **O que é:** Um serviço de computação sem servidor que executa código em resposta a eventos.
   - **Casos de Uso:**
     - Transformação de dados em tempo real.
     - Integração com Kinesis, S3, DynamoDB e API Gateway.
   - **Funcionalidades:**
     - Execução de funções Python, Node.js, Java, etc.
     - Escalabilidade automática com base na demanda.

3. **Amazon EMR (Elastic MapReduce):** [Leitura](../emr)
   - **O que é:** Um serviço gerenciado para processamento de big data usando frameworks como Hadoop, Spark e Hive.
   - **Casos de Uso:**
     - Processamento de grandes volumes de dados.
     - Análise de logs e dados de sensores.
   - **Funcionalidades:**
     - Escalabilidade automática.
     - Integração com S3, Redshift e Glue.

4. **AWS Step Functions:** [Leitura](../stepfunctions)
   - **O que é:** Um serviço de orquestração de workflows para coordenar tarefas distribuídas.
   - **Casos de Uso:**
     - Automação de pipelines de ETL.
     - Orquestração de microserviços.
   - **Funcionalidades:**
     - Integração com Lambda, Glue, EMR e outros serviços.

---

## **2. Processar Dados em Tempo Real**
O processamento de dados em tempo real é essencial para aplicações que exigem insights imediatos, como monitoramento de sistemas, análise de cliques e IoT.

### **Serviços de Processamento em Tempo Real**
1. **Amazon Kinesis:** [Leitura](../kinesis)
   - **Kinesis Data Streams:**
     - Ingestão de dados em tempo real.
     - Escalável e durável.
     - Integração com Lambda, S3, Redshift e Elasticsearch.
   - **Kinesis Data Firehose:**
     - Entrega automática de dados para destinos como S3, Redshift e Elasticsearch.
     - Totalmente gerenciado, sem necessidade de provisionar shards.
   - **Kinesis Data Analytics:**
     - Análise de dados em tempo real usando SQL.
     - Detecção de padrões e agregações.

2. **Amazon MSK (Managed Streaming for Apache Kafka):**
   - **O que é:** Um serviço gerenciado para processamento de streams com Apache Kafka.
   - **Casos de Uso:**
     - Pipelines de streaming complexos.
     - Integração com aplicações Kafka existentes.
   - **Funcionalidades:**
     - Escalabilidade automática.
     - Integração com Lambda, Glue e S3.

---

## **3. Otimizar o Desempenho de Processamento**
A otimização do desempenho de processamento envolve a melhoria da eficiência, escalabilidade e redução de custos.

### **Estratégias de Otimização**
1. **Escalabilidade:**
   - **Auto Scaling:** Ajuste automático da capacidade de processamento com base na demanda.
   - **Spot Instances:** Uso de instâncias EC2 spot para reduzir custos em tarefas tolerantes a falhas.

2. **Particionamento e Indexação:**
   - **Particionamento:** Dividir dados em partes menores para melhorar o desempenho de consultas (ex.: particionamento por data no S3).
   - **Indexação:** Criar índices em bancos de dados (ex.: DynamoDB, RDS) para acelerar consultas.

3. **Formato de Dados:**
   - **Formatos Colunares:** Usar formatos como Parquet ou ORC para melhorar o desempenho e reduzir custos.
   - **Compressão:** Comprimir dados para reduzir o espaço de armazenamento e melhorar a velocidade de transferência.

4. **Custos:**
   - **Escolha de Serviços:** Usar serviços como Lambda para tarefas de curta duração e EMR para processamento de grandes volumes.
   - **Uso de SPICE:** No Amazon QuickSight, usar o SPICE para acelerar consultas repetitivas.

---

## **4. Tópicos que Podem Aparecer na Avaliação**
Aqui estão alguns tópicos específicos que podem ser cobrados no exame relacionados ao Domínio 3:

### **Transformação de Dados**
- Configurar um job no AWS Glue para transformar dados no S3.
- Usar o AWS Lambda para processar dados em tempo real a partir de um Kinesis Data Stream.
- Orquestrar um pipeline de ETL usando o AWS Step Functions.

### **Processamento em Tempo Real**
- Configurar um Kinesis Data Stream para ingestão de dados em tempo real.
- Usar o Kinesis Data Firehose para entregar dados ao S3 ou Redshift.
- Analisar dados em tempo real com o Kinesis Data Analytics.

### **Otimização de Desempenho**
- Implementar particionamento de dados no S3 para melhorar o desempenho de consultas.
- Configurar índices globais secundários (GSI) no DynamoDB para consultas flexíveis.
- Usar o SPICE no Amazon QuickSight para acelerar análises.

---

## **5. Exemplos de Perguntas do Exame**
1. **Qual serviço da AWS é mais adequado para transformar dados em tempo real a partir de um Kinesis Data Stream?**
   - A) AWS Glue  
   - B) AWS Lambda  
   - C) Amazon EMR  
   - D) AWS Step Functions  
   **Resposta:** B) AWS Lambda.

2. **Qual estratégia é recomendada para melhorar o desempenho de consultas no Amazon S3?**
   - A) Usar particionamento por data.  
   - B) Armazenar todos os dados em um único arquivo grande.  
   - C) Desabilitar a compressão de dados.  
   - D) Usar apenas a classe S3 Standard.  
   **Resposta:** A) Usar particionamento por data.

3. **Qual serviço da AWS pode ser usado para orquestrar um pipeline de ETL envolvendo Lambda, Glue e EMR?**
   - A) Amazon Kinesis  
   - B) AWS Step Functions  
   - C) Amazon S3  
   - D) AWS Glue  
   **Resposta:** B) AWS Step Functions.

4. **Qual prática é recomendada para reduzir custos no processamento de grandes volumes de dados?**
   - A) Usar instâncias spot no Amazon EMR.  
   - B) Manter clusters em execução 24/7, mesmo quando não estiverem em uso.  
   - C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   - D) Usar apenas instâncias sob demanda.  
   **Resposta:** A) Usar instâncias spot no Amazon EMR.

---

## **6. Melhores Práticas para o Domínio 3**
- **Escolha a Ferramenta Certa:** Use Lambda para processamento em tempo real, Glue para ETL e EMR para big data.
- **Otimize o Desempenho:** Implemente particionamento, indexação e compressão de dados.
- **Reduza Custos:** Use instâncias spot, auto scaling e SPICE para otimizar custos.
- **Monitore e Ajuste:** Use CloudWatch para monitorar métricas e ajustar a capacidade conforme necessário.