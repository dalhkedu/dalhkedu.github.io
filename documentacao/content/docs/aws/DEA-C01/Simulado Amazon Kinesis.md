---
title: "Simulado: Amazon Kinesis"
---

### **Simulado: Amazon Kinesis**

#### **1. Qual das seguintes opções é verdadeira sobre os shards no Amazon Kinesis Data Streams?**
A) Cada shard suporta até 5 MB/s de entrada e 10 MB/s de saída.  
B) O número de shards em um stream não pode ser alterado após a criação.  
C) Cada shard suporta até 1 MB/s de entrada e 2 MB/s de saída.  
D) Shards são usados apenas no Kinesis Data Firehose.  

**Resposta:** C) Cada shard suporta até 1 MB/s de entrada e 2 MB/s de saída.  
**Explicação:** Shards são unidades de capacidade no Kinesis Data Streams, com limites de throughput definidos.

---

#### **2. Qual componente do Amazon Kinesis é usado para entrega de dados em tempo real a destinos como S3, Redshift e Elasticsearch sem a necessidade de gerenciar shards?**
A) Kinesis Data Streams  
B) Kinesis Data Firehose  
C) Kinesis Data Analytics  
D) Kinesis Video Streams  

**Resposta:** B) Kinesis Data Firehose  
**Explicação:** O Kinesis Data Firehose é totalmente gerenciado e não requer provisionamento de shards.

---

#### **3. Qual das seguintes opções é uma vantagem do uso do Kinesis Data Analytics?**
A) Ele permite a análise de dados em tempo real usando SQL.  
B) Ele só suporta a análise de dados armazenados no Amazon S3.  
C) Ele não suporta a integração com Kinesis Data Streams.  
D) Ele requer o gerenciamento manual de shards.  

**Resposta:** A) Ele permite a análise de dados em tempo real usando SQL.  
**Explicação:** O Kinesis Data Analytics permite análise de dados em tempo real usando SQL, integrando-se a Kinesis Data Streams e Kinesis Data Firehose.

---

#### **4. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho do Kinesis Data Streams?**
A) Usar partition keys que distribuam os dados uniformemente entre os shards.  
B) Enviar records individualmente para reduzir a latência.  
C) Usar um único shard para todos os dados.  
D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  

**Resposta:** A) Usar partition keys que distribuam os dados uniformemente entre os shards.  
**Explicação:** A escolha de partition keys que distribuam os dados uniformemente entre os shards melhora o desempenho e a escalabilidade.

---

#### **5. Qual das seguintes opções é verdadeira sobre o Kinesis Data Firehose?**
A) Ele suporta transformações de dados em tempo real usando AWS Lambda.  
B) Ele requer o gerenciamento manual de shards.  
C) Ele só pode entregar dados ao Amazon S3.  
D) Ele não suporta a entrega de dados ao Amazon Redshift.  

**Resposta:** A) Ele suporta transformações de dados em tempo real usando AWS Lambda.  
**Explicação:** O Kinesis Data Firehose suporta transformações de dados em tempo real usando AWS Lambda e pode entregar dados a vários destinos, incluindo S3, Redshift e Elasticsearch.

---

#### **6. Qual das seguintes opções é uma limitação do Kinesis Data Streams em comparação com o Kinesis Data Firehose?**
A) Ele não suporta a entrega de dados ao Amazon S3.  
B) Ele requer o gerenciamento manual de shards.  
C) Ele não suporta transformações de dados em tempo real.  
D) Ele não suporta a análise de dados em tempo real.  

**Resposta:** B) Ele requer o gerenciamento manual de shards.  
**Explicação:** O Kinesis Data Streams requer o gerenciamento manual de shards, enquanto o Kinesis Data Firehose é totalmente gerenciado.

---

#### **7. Qual serviço da AWS pode ser usado para monitorar métricas como latência e throughput no Amazon Kinesis?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor  

**Resposta:** B) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar o desempenho e a saúde do Amazon Kinesis.

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no Amazon Kinesis?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O Amazon Kinesis integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

#### **9. Qual das seguintes opções é uma vantagem do uso do Kinesis Video Streams?**
A) Ele permite a ingestão e processamento de streams de vídeo em tempo real.  
B) Ele só suporta a análise de dados armazenados no Amazon S3.  
C) Ele não suporta a integração com AWS Lambda.  
D) Ele não suporta a cifragem de dados.  

**Resposta:** A) Ele permite a ingestão e processamento de streams de vídeo em tempo real.  
**Explicação:** O Kinesis Video Streams é projetado para ingestão e processamento de streams de vídeo em tempo real, com suporte para análise e integração com outros serviços AWS.

---

#### **10. Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon Kinesis?**
A) Usar um único shard para todos os dados.  
B) Ajustar o número de shards com base na carga para otimizar custos.  
C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
D) Usar Kinesis Data Streams para todos os casos de uso.  

**Resposta:** B) Ajustar o número de shards com base na carga para otimizar custos.  
**Explicação:** Ajustar o número de shards com base na carga ajuda a otimizar custos, evitando provisionamento excessivo.

---

### **Resumo das Respostas**
1. C) Cada shard suporta até 1 MB/s de entrada e 2 MB/s de saída.  
2. B) Kinesis Data Firehose  
3. A) Ele permite a análise de dados em tempo real usando SQL.  
4. A) Usar partition keys que distribuam os dados uniformemente entre os shards.  
5. A) Ele suporta transformações de dados em tempo real usando AWS Lambda.  
6. B) Ele requer o gerenciamento manual de shards.  
7. B) Amazon CloudWatch  
8. B) Ele usa IAM para controlar o acesso a recursos e dados.  
9. A) Ele permite a ingestão e processamento de streams de vídeo em tempo real.  
10. B) Ajustar o número de shards com base na carga para otimizar custos.  

---
