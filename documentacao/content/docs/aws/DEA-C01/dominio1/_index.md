---
title: "Domínio 1: Coleta de Dados"
---
## **1. Identificar Fontes de Dados**
A coleta de dados começa com a identificação das fontes de dados, que podem ser de diferentes tipos e formatos. Essas fontes podem ser categorizadas em:

### **Tipos de Fontes de Dados**
1. **Streaming (Dados em Tempo Real):**
   - Dados gerados continuamente, como logs de aplicações, métricas de IoT, cliques em websites ou transações financeiras.
   - Exemplos de fontes:
     - **Amazon Kinesis Data Streams**: Para ingestão de dados em tempo real. [Leitura](../kinesis)
     - **Amazon Managed Streaming for Apache Kafka (MSK)**: Para processamento de streams com Kafka.
     - **AWS IoT Core**: Para coleta de dados de dispositivos IoT.

2. **Batch (Dados em Lote):**
   - Dados coletados em intervalos regulares, como arquivos CSV, logs diários ou backups.
   - Exemplos de fontes:
     - **Amazon S3**: Para armazenamento de arquivos em lote.
     - **Amazon RDS**: Para exportação de dados de bancos relacionais.
     - **AWS Glue**: Para ETL de dados em lote. [Leitura](../glue)

3. **Dados Semi-Estruturados e Não Estruturados:**
   - Dados que não seguem um esquema rígido, como JSON, XML, logs ou imagens.
   - Exemplos de fontes:
     - **Amazon S3**: Para armazenamento de dados semi-estruturados.
     - **Amazon DynamoDB**: Para dados NoSQL semi-estruturados.

4. **Dados de Terceiros:**
   - Dados provenientes de APIs externas, feeds de redes sociais ou parceiros comerciais.
   - Exemplos de ferramentas:
     - **Amazon AppFlow**: Para integração com SaaS (Salesforce, Slack, etc.).

---

## **2. Configurar Métodos de Ingestão de Dados**
Após identificar as fontes de dados, é necessário configurar métodos eficientes para ingerir esses dados na AWS. A escolha do método depende do tipo de dados (streaming ou batch) e dos requisitos de desempenho e custo.

### **Métodos de Ingestão**
1. **Para Dados em Streaming:**
   - **Amazon Kinesis Data Streams:**
     - Ingestão de dados em tempo real.
     - Escalável e durável.
     - Integração com Lambda, S3, Redshift e Elasticsearch.
   - **Amazon Kinesis Data Firehose:**
     - Entrega automática de dados para destinos como S3, Redshift e Elasticsearch.
     - Totalmente gerenciado, sem necessidade de provisionar shards.
   - **Amazon MSK:**
     - Para cenários que exigem compatibilidade com Apache Kafka.
     - Ideal para pipelines de streaming complexos.

2. **Para Dados em Lote:**
   - **Amazon S3:**
     - Armazenamento de arquivos em lote (CSV, JSON, Parquet, etc.).
     - Integração com AWS Glue para ETL.
   - **AWS Glue:**
     - Extração, transformação e carregamento (ETL) de dados em lote.
     - Catalogação de metadados no Glue Data Catalog.
   - **AWS Data Pipeline:**
     - Orquestração de workflows de ingestão de dados em lote.
     - Integração com S3, RDS, DynamoDB e Redshift.

3. **Para Dados de APIs e Terceiros:**
   - **Amazon AppFlow:**
     - Integração com serviços SaaS como Salesforce, Slack e Zendesk.
     - Transferência segura de dados para S3 ou Redshift.
   - **AWS Lambda:**
     - Execução de código para ingestão de dados de APIs personalizadas.
     - Integração com S3, DynamoDB e Kinesis.

---

## **3. Validar e Limpar Dados Durante a Ingestão**
A validação e limpeza de dados são etapas críticas para garantir a qualidade dos dados ingeridos. Isso envolve a detecção e correção de problemas como dados incompletos, duplicados ou inconsistentes.

### **Validação de Dados**
1. **Verificação de Esquema:**
   - Garantir que os dados estejam no formato esperado (ex.: colunas obrigatórias, tipos de dados corretos).
   - Ferramentas:
     - **AWS Glue**: Validação de esquemas durante o ETL.
     - **Amazon Athena**: Consulta de dados no S3 para validação.

2. **Verificação de Integridade:**
   - Garantir que os dados estejam completos e sem corrupção.
   - Exemplos:
     - Verificar checksums de arquivos.
     - Validar chaves primárias em bancos de dados.

3. **Validação de Regras de Negócio:**
   - Aplicar regras específicas do domínio (ex.: faixas de valores aceitáveis, formatos de datas).
   - Ferramentas:
     - **AWS Lambda**: Execução de funções personalizadas para validação.

### **Limpeza de Dados**
1. **Remoção de Duplicatas:**
   - Identificar e remover registros duplicados.
   - Ferramentas:
     - **AWS Glue**: Transformações para remoção de duplicatas.
     - **Amazon Redshift**: Consultas SQL para identificar duplicatas.

2. **Preenchimento de Dados Faltantes:**
   - Preencher valores ausentes com padrões ou valores derivados.
   - Ferramentas:
     - **AWS Glue**: Transformações para preenchimento de dados.
     - **Amazon Athena**: Consultas SQL para manipulação de dados.

3. **Padronização de Dados:**
   - Garantir consistência nos formatos (ex.: datas, moedas, unidades de medida).
   - Ferramentas:
     - **AWS Glue**: Transformações para padronização.
     - **AWS Lambda**: Funções personalizadas para formatação.

---

## **4. Tópicos que Podem Aparecer na Avaliação**
Aqui estão alguns tópicos específicos que podem ser cobrados no exame relacionados ao Domínio 1:

### **Identificação de Fontes de Dados**
- Diferenciar entre fontes de dados em streaming e batch.
- Escolher a ferramenta adequada para ingestão com base no tipo de dados (ex.: Kinesis para streaming, S3 para batch).

### **Configuração de Métodos de Ingestão**
- Configurar um Kinesis Data Stream para ingestão de dados em tempo real.
- Usar o AWS Glue para ETL de dados em lote.
- Configurar o Amazon AppFlow para integração com serviços SaaS.

### **Validação e Limpeza de Dados**
- Configurar validações de esquema no AWS Glue.
- Escrever funções Lambda para validação de dados durante a ingestão.
- Usar o Amazon Athena para consultar e validar dados no S3.

---

## **5. Exemplos de Perguntas do Exame**
1. **Qual serviço da AWS é mais adequado para ingestão de dados em tempo real de dispositivos IoT?**
   - A) Amazon S3  
   - B) Amazon Kinesis Data Streams  
   - C) AWS Glue  
   - D) Amazon Redshift  
   **Resposta:** B) Amazon Kinesis Data Streams.

2. **Qual ferramenta da AWS pode ser usada para validar o esquema de dados durante a ingestão?**
   - A) Amazon Athena  
   - B) AWS Glue  
   - C) Amazon Kinesis Data Firehose  
   - D) Amazon S3  
   **Resposta:** B) AWS Glue.

3. **Qual prática é recomendada para garantir a qualidade dos dados durante a ingestão?**
   - A) Ignorar dados incompletos.  
   - B) Validar o esquema e aplicar regras de negócio.  
   - C) Armazenar todos os dados sem validação.  
   - D) Usar apenas dados em lote.  
   **Resposta:** B) Validar o esquema e aplicar regras de negócio.

---

## **6. Melhores Práticas para o Domínio 1**
- **Escolha a Ferramenta Certa:** Use Kinesis para streaming e Glue/S3 para batch.
- **Valide Dados na Fonte:** Aplique validações durante a ingestão para evitar problemas downstream.
- **Documente os Processos:** Mantenha documentação clara sobre fontes de dados, métodos de ingestão e regras de validação.
- **Monitore a Ingestão:** Use CloudWatch para monitorar métricas de ingestão e detectar anomalias.