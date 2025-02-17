---
title: "Simulado: Amazon EMR"
---

### **Simulado: Amazon EMR**

#### **1. Qual framework é recomendado para processamento em memória e análise de dados em tempo real no Amazon EMR?**
A) Apache Hadoop  
B) Apache Spark  
C) Apache HBase  
D) Presto  

---

#### **2. Qual tipo de nó no Amazon EMR é responsável por armazenar dados no HDFS?**
A) Master Node  
B) Core Node  
C) Task Node  
D) Edge Node  

---

#### **3. Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon EMR?**
A) Usar instâncias spot para tarefas tolerantes a falhas.  
B) Manter clusters em execução 24/7, mesmo quando não estiverem em uso.  
C) Usar instâncias com alto desempenho para todas as tarefas.  
D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  

---

#### **4. Qual serviço da AWS pode ser usado para monitorar métricas como uso de CPU e memória no Amazon EMR?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor  

---

#### **5. Qual das seguintes opções é verdadeira sobre o Amazon EMR?**
A) Ele não suporta a execução de clusters em uma VPC.  
B) Ele permite a execução de frameworks como Hadoop, Spark e HBase.  
C) Ele não se integra ao Amazon S3.  
D) Ele não suporta a cifragem de dados em repouso.  

---

#### **6. Qual das seguintes opções é uma vantagem do uso do Amazon EMR com o Amazon S3?**
A) Ele permite o armazenamento de dados diretamente no HDFS, sem a necessidade de usar o S3.  
B) Ele permite o armazenamento de dados no S3, reduzindo a necessidade de usar o HDFS.  
C) Ele não suporta a leitura de dados diretamente do S3.  
D) Ele aumenta o custo de armazenamento de dados. 

---

#### **7. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de clusters no Amazon EMR?**
A) Usar instâncias com baixo desempenho para todas as tarefas.  
B) Particionar dados no S3 para melhorar o desempenho de consultas.  
C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
D) Manter clusters em execução 24/7, mesmo quando não estiverem em uso.  

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no Amazon EMR?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

---

#### **9. Qual das seguintes opções é uma limitação do Amazon EMR?**
A) Ele não suporta a execução de frameworks de código aberto.  
B) Ele tem um tempo de execução máximo de 15 minutos por job.  
C) Ele não suporta a integração com o Amazon S3.  
D) Ele requer o gerenciamento manual de servidores.  

---

#### **10. Qual das seguintes opções é uma vantagem do uso do Amazon EMR com o AWS Glue?**
A) Ele permite a catalogação automática de metadados.  
B) Ele aumenta o custo de processamento de dados.  
C) Ele não suporta a consulta de dados no S3.  
D) Ele não se integra ao Amazon Redshift.  

---

**Resposta:** B) Apache Spark  
**Explicação:** O Apache Spark é otimizado para processamento em memória e análise de dados em tempo real, sendo uma escolha comum para esses casos de uso no Amazon EMR.

---

**Resposta:** B) Core Node  
**Explicação:** O Core Node é responsável por armazenar dados no HDFS (Hadoop Distributed File System) e executar tarefas de processamento.

---

**Resposta:** A) Usar instâncias spot para tarefas tolerantes a falhas.  
**Explicação:** As instâncias spot são uma opção econômica para tarefas tolerantes a falhas, pois custam menos que as instâncias sob demanda.

---

**Resposta:** B) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar o desempenho e a saúde do Amazon EMR, incluindo uso de CPU e memória.

---

**Resposta:** B) Ele permite a execução de frameworks como Hadoop, Spark e HBase.  
**Explicação:** O Amazon EMR suporta vários frameworks de big data, incluindo Hadoop, Spark, HBase, Flink e Presto.

---

**Resposta:** B) Ele permite o armazenamento de dados no S3, reduzindo a necessidade de usar o HDFS.  
**Explicação:** O Amazon EMR pode usar o S3 como armazenamento principal, reduzindo a necessidade de usar o HDFS e facilitando a integração com outros serviços AWS.

---

**Resposta:** B) Particionar dados no S3 para melhorar o desempenho de consultas.  
**Explicação:** O particionamento de dados no S3 permite que o Amazon EMR acesse apenas os dados relevantes, melhorando o desempenho e reduzindo custos.

---

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O Amazon EMR integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

**Resposta:** B) Ele tem um tempo de execução máximo de 15 minutos por job.  
**Explicação:** O Amazon EMR não tem um tempo de execução máximo por job, mas jobs de longa duração podem aumentar custos e exigir otimização.

---

**Resposta:** A) Ele permite a catalogação automática de metadados.  
**Explicação:** A integração com o AWS Glue permite a catalogação automática de metadados, facilitando a descoberta e organização de dados.

---

### **Resumo das Respostas**
1. B) Apache Spark  
2. B) Core Node  
3. A) Usar instâncias spot para tarefas tolerantes a falhas.  
4. B) Amazon CloudWatch  
5. B) Ele permite a execução de frameworks como Hadoop, Spark e HBase.  
6. B) Ele permite o armazenamento de dados no S3, reduzindo a necessidade de usar o HDFS.  
7. B) Particionar dados no S3 para melhorar o desempenho de consultas.  
8. B) Ele usa IAM para controlar o acesso a recursos e dados.  
9. B) Ele tem um tempo de execução máximo de 15 minutos por job.  
10. A) Ele permite a catalogação automática de metadados.  

---
