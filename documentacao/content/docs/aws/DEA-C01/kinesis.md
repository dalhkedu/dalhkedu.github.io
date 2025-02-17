---
title: "Amazon Kinesis"
---

https://docs.aws.amazon.com/pt_br/streams/latest/dev/introduction.html

### **1. Visão Geral do Amazon Kinesis**
- **O que é:** Um conjunto de serviços para processamento de dados em tempo real.
- **Casos de Uso Comuns:**
  - Análise de logs e métricas em tempo real.
  - Processamento de dados de IoT (Internet of Things).
  - Análise de cliques e comportamento do usuário.
  - Detecção de anomalias e alertas em tempo real.

---

### **2. Componentes do Amazon Kinesis**
#### **Amazon Kinesis Data Streams**
- **O que é:** Serviço para ingestão e processamento de dados em tempo real.
- **Conceitos Chave:**
  - **Shards:** Unidades de capacidade dentro de um stream. Cada shard suporta até 1 MB/s de entrada e 2 MB/s de saída.
  - **Records:** Unidades de dados (até 1 MB) enviadas para um stream.
  - **Partition Key:** Define qual shard será usado para armazenar um record.
- **Integrações:** Pode ser usado com AWS Lambda, Amazon S3, Amazon Redshift e outros serviços.

#### **Amazon Kinesis Data Firehose**
- **O que é:** Serviço para entrega de dados em tempo real a destinos como S3, Redshift, Elasticsearch e Splunk.
- **Benefícios:** Totalmente gerenciado, sem necessidade de provisionar ou gerenciar shards.
- **Transformações:** Suporta transformações de dados em tempo real usando AWS Lambda.

#### **Amazon Kinesis Data Analytics**
- **O que é:** Serviço para análise de dados em tempo real usando SQL.
- **Casos de Uso:** Detecção de padrões, agregações e análises em tempo real.
- **Integrações:** Pode ser usado com Kinesis Data Streams e Kinesis Data Firehose.

#### **Amazon Kinesis Video Streams**
- **O que é:** Serviço para ingestão e processamento de streams de vídeo em tempo real.
- **Casos de Uso:** Análise de vídeo, reconhecimento facial e detecção de objetos.

---

### **3. Funcionalidades Avançadas**
#### **Escalabilidade**
- **Ajuste de Shards:** A capacidade de um stream pode ser ajustada adicionando ou removendo shards.
- **Concurrency Scaling:** Escalona automaticamente a capacidade de processamento com base na carga.

#### **Segurança**
- **Cifragem:** Dados podem ser cifrados em trânsito e em repouso usando AWS KMS.
- **IAM:** Controle de acesso usando políticas do IAM.
- **VPC:** Suporta execução em VPCs para isolamento de rede.

#### **Monitoramento**
- **Amazon CloudWatch:** Monitora métricas como latência, throughput e erros.
- **Logs de Auditoria:** Usa o AWS CloudTrail para registrar atividades no Kinesis.

---

### **4. Integrações com Outros Serviços AWS**
- **AWS Lambda:** Para processamento de dados em tempo real.
- **Amazon S3:** Para armazenamento de dados processados.
- **Amazon Redshift:** Para análise de dados em um data warehouse.
- **Amazon Elasticsearch:** Para análise e visualização de dados em tempo real.
- **Amazon DynamoDB:** Para armazenamento de dados processados.

---

### **5. Melhores Práticas**
#### **Desempenho**
- **Escolha de Partition Key:** Use partition keys que distribuam os dados uniformemente entre os shards.
- **Batch de Records:** Envie records em lotes para reduzir o número de chamadas de API.

#### **Segurança**
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.
- **IAM:** Use políticas granulares para controlar o acesso ao Kinesis.

#### **Custos**
- **Ajuste de Shards:** Ajuste o número de shards com base na carga para otimizar custos.
- **Uso de Kinesis Data Firehose:** Para casos de uso que não exigem processamento em tempo real, o Firehose é mais econômico.

---

### **6. Tópicos Relevantes para o Exame**
- **Kinesis Data Streams:** Entenda como os shards funcionam e como escolher partition keys.
- **Kinesis Data Firehose:** Saiba configurar e usar para entrega de dados em tempo real.
- **Kinesis Data Analytics:** Entenda como usar SQL para análise de dados em tempo real.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Análise de logs, IoT, detecção de anomalias.

---

### **7. Exemplos de Perguntas do Exame**
1. **Qual componente do Amazon Kinesis é usado para ingestão e processamento de dados em tempo real com capacidade ajustável?**
   - A) Kinesis Data Firehose  
   - B) Kinesis Data Streams  
   - C) Kinesis Data Analytics  
   - D) Kinesis Video Streams  
   **Resposta:** B) Kinesis Data Streams.

2. **Qual das seguintes opções é uma vantagem do uso do Kinesis Data Firehose?**
   - A) Ele requer o gerenciamento manual de shards.  
   - B) Ele é totalmente gerenciado e não requer provisionamento de shards.  
   - C) Ele só suporta a entrega de dados ao Amazon S3.  
   - D) Ele não suporta transformações de dados em tempo real.  
   **Resposta:** B) Ele é totalmente gerenciado e não requer provisionamento de shards.

3. **Qual serviço da AWS pode ser usado para análise de dados em tempo real usando SQL no Amazon Kinesis?**
   - A) Kinesis Data Streams  
   - B) Kinesis Data Firehose  
   - C) Kinesis Data Analytics  
   - D) Kinesis Video Streams  
   **Resposta:** C) Kinesis Data Analytics.

4. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho do Kinesis Data Streams?**
   - A) Usar partition keys que distribuam os dados uniformemente entre os shards.  
   - B) Enviar records individualmente para reduzir a latência.  
   - C) Usar um único shard para todos os dados.  
   - D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   **Resposta:** A) Usar partition keys que distribuam os dados uniformemente entre os shards.

---

### **8. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um Kinesis Data Stream e envie dados usando a AWS CLI ou SDK.
  - Configure um Kinesis Data Firehose para entregar dados ao S3.
  - Use Kinesis Data Analytics para analisar dados em tempo real.

---