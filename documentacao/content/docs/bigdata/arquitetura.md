---
title: Arquitetura de Big Data
---
Exemplos práticos de arquiteturas de **big data** e **processamento de streaming** dentro da AWS, com explicações sobre as decisões de uso e os problemas que essas arquiteturas resolvem.

---

## **1. Arquitetura de Big Data para Análise de Logs**
### **Cenário:**
Uma empresa precisa analisar logs de servidores para monitorar o desempenho, detectar anomalias e gerar relatórios diários.

### **Arquitetura:**
1. **Coleta de Dados:**
   - **Amazon Kinesis Data Firehose:** Coleta logs em tempo real e os entrega ao Amazon S3.
   - **Amazon S3:** Armazena os logs brutos em um data lake.

2. **Transformação de Dados:**
   - **AWS Glue:** Executa jobs de ETL para limpar, transformar e particionar os logs.
   - **Amazon Athena:** Consulta os logs transformados diretamente no S3 usando SQL.

3. **Análise e Visualização:**
   - **Amazon Redshift:** Armazena dados processados para análise mais complexa.
   - **Amazon QuickSight:** Cria painéis interativos para visualização de métricas de desempenho.

### **Decisões e Benefícios:**
- **Kinesis Data Firehose:** Escalável e totalmente gerenciado, ideal para ingestão de logs em tempo real.
- **S3:** Armazenamento durável e de baixo custo para dados brutos.
- **Glue:** Facilita a transformação de dados sem a necessidade de infraestrutura gerenciada.
- **Athena:** Permite consultas SQL em dados no S3, sem a necessidade de carregá-los em um banco de dados.
- **Redshift:** Otimizado para consultas complexas e análise de grandes volumes de dados.
- **QuickSight:** Facilita a criação de painéis interativos para tomada de decisões.

### **Problemas Resolvidos:**
- **Escalabilidade:** A arquitetura escala automaticamente com o volume de logs.
- **Custo:** Uso de serviços gerenciados e armazenamento de baixo custo no S3.
- **Flexibilidade:** Permite análise de logs em tempo real e em lote.

---

## **2. Arquitetura de Processamento de Streaming para IoT**
### **Cenário:**
Uma empresa de IoT precisa processar dados de sensores em tempo real para monitorar o status dos dispositivos e detectar falhas.

### **Arquitetura:**
1. **Coleta de Dados:**
   - **AWS IoT Core:** Coleta dados de sensores e os envia para um tópico no Amazon Kinesis Data Streams.

2. **Processamento em Tempo Real:**
   - **Amazon Kinesis Data Streams:** Armazena os dados de sensores em tempo real.
   - **AWS Lambda:** Processa os dados em tempo real para detectar anomalias e acionar alertas.

3. **Armazenamento e Análise:**
   - **Amazon S3:** Armazena dados históricos para análise futura.
   - **Amazon DynamoDB:** Armazena status atual dos dispositivos para consultas rápidas.
   - **Amazon QuickSight:** Visualiza métricas em tempo real e históricas.

### **Decisões e Benefícios:**
- **IoT Core:** Gerencia a conexão de dispositivos IoT de forma segura e escalável.
- **Kinesis Data Streams:** Processa dados em tempo real com baixa latência.
- **Lambda:** Executa funções sem servidor para processamento em tempo real, reduzindo custos.
- **S3:** Armazenamento durável e de baixo custo para dados históricos.
- **DynamoDB:** Banco de dados NoSQL de alta performance para consultas rápidas.
- **QuickSight:** Visualização de dados em tempo real para monitoramento contínuo.

### **Problemas Resolvidos:**
- **Baixa Latência:** Processamento em tempo real para detecção imediata de falhas.
- **Escalabilidade:** A arquitetura escala automaticamente com o número de dispositivos.
- **Custo:** Uso de serviços sem servidor (Lambda) e armazenamento de baixo custo (S3).

---

## **3. Arquitetura de Big Data para Análise de Vendas**
### **Cenário:**
Uma empresa de varejo precisa analisar dados de vendas de várias lojas para identificar tendências e otimizar estoques.

### **Arquitetura:**
1. **Coleta de Dados:**
   - **Amazon S3:** Armazena dados de vendas em lote (CSV, JSON) enviados pelas lojas.

2. **Transformação de Dados:**
   - **AWS Glue:** Executa jobs de ETL para limpar, transformar e particionar os dados.
   - **Amazon Redshift:** Armazena dados processados para análise.

3. **Análise e Visualização:**
   - **Amazon Athena:** Consulta dados no S3 para análises ad-hoc.
   - **Amazon QuickSight:** Cria painéis interativos para visualização de tendências de vendas.

### **Decisões e Benefícios:**
- **S3:** Armazenamento centralizado para dados brutos e processados.
- **Glue:** Facilita a transformação de dados sem a necessidade de infraestrutura gerenciada.
- **Redshift:** Otimizado para consultas complexas e análise de grandes volumes de dados.
- **Athena:** Permite consultas SQL em dados no S3, sem a necessidade de carregá-los em um banco de dados.
- **QuickSight:** Facilita a criação de painéis interativos para tomada de decisões.

### **Problemas Resolvidos:**
- **Integração de Dados:** Consolida dados de várias lojas em um único repositório.
- **Desempenho:** Consultas rápidas e eficientes no Redshift e Athena.
- **Custo:** Uso de serviços gerenciados e armazenamento de baixo custo no S3.

---

## **4. Arquitetura de Processamento de Streaming para Análise de Cliques**
### **Cenário:**
Uma empresa de e-commerce precisa analisar cliques em tempo real para personalizar recomendações de produtos.

### **Arquitetura:**
1. **Coleta de Dados:**
   - **Amazon Kinesis Data Streams:** Coleta cliques em tempo real.

2. **Processamento em Tempo Real:**
   - **AWS Lambda:** Processa cliques para gerar recomendações personalizadas.
   - **Amazon DynamoDB:** Armazena recomendações para consultas rápidas.

3. **Armazenamento e Análise:**
   - **Amazon S3:** Armazena dados históricos de cliques para análise futura.
   - **Amazon Redshift:** Armazena dados processados para análise mais complexa.
   - **Amazon QuickSight:** Visualiza métricas em tempo real e históricas.

### **Decisões e Benefícios:**
- **Kinesis Data Streams:** Processa cliques em tempo real com baixa latência.
- **Lambda:** Executa funções sem servidor para processamento em tempo real, reduzindo custos.
- **DynamoDB:** Banco de dados NoSQL de alta performance para consultas rápidas.
- **S3:** Armazenamento durável e de baixo custo para dados históricos.
- **Redshift:** Otimizado para consultas complexas e análise de grandes volumes de dados.
- **QuickSight:** Visualização de dados em tempo real para monitoramento contínuo.

### **Problemas Resolvidos:**
- **Personalização em Tempo Real:** Recomendações personalizadas com base em cliques recentes.
- **Escalabilidade:** A arquitetura escala automaticamente com o volume de cliques.
- **Custo:** Uso de serviços sem servidor (Lambda) e armazenamento de baixo custo (S3).

---

## **5. Tópicos Relevantes para a Avaliação**
- Escolher serviços AWS com base em cenários de big data e streaming.
- Entender as vantagens e desvantagens de cada serviço.
- Configurar pipelines de dados usando serviços como Kinesis, Glue, Lambda e Redshift.
- Visualizar dados usando QuickSight.

---
