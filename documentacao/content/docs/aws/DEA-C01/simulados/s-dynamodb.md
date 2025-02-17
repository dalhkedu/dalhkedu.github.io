---
title: "Simulado: Amazon DynamoDB"
---

### **Simulado: Amazon DynamoDB**

#### **1. Qual tipo de índice no Amazon DynamoDB permite consultas flexíveis em diferentes atributos?**
A) Índice Local Secundário (LSI)  
B) Índice Global Secundário (GSI)  
C) Índice Primário  
D) Índice de Partição  

---

#### **2. Qual serviço da AWS pode ser usado para processar dados em tempo real no Amazon DynamoDB?**
A) Amazon S3  
B) AWS Lambda  
C) Amazon Redshift  
D) AWS Glue  

---

#### **3. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon DynamoDB?**
A) Usar índices globais secundários (GSI) para consultas flexíveis.  
B) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
C) Manter tabelas em execução 24/7, mesmo quando não estiverem em uso.  
D) Usar apenas a chave de partição para todas as consultas.  

---

#### **4. Qual serviço da AWS pode ser usado para monitorar métricas como uso de capacidade e latência no Amazon DynamoDB?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor 

---

#### **5. Qual das seguintes opções é verdadeira sobre o Amazon DynamoDB?**
A) Ele não suporta a criação de índices secundários.  
B) Ele permite a execução de consultas SQL complexas.  
C) Ele oferece desempenho consistente de milissegundos em qualquer escala.  
D) Ele não suporta a cifragem de dados em repouso.  

---

#### **6. Qual das seguintes opções é uma vantagem do uso do Amazon DynamoDB com o AWS Lambda?**
A) Ele permite o processamento de dados em tempo real.  
B) Ele aumenta o custo de processamento de dados.  
C) Ele não suporta a execução de consultas em tempo real.  
D) Ele não se integra ao Amazon S3.  

---

#### **7. Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon DynamoDB?**
A) Usar a escalabilidade automática para ajustar a capacidade com base na demanda.  
B) Manter tabelas em execução 24/7, mesmo quando não estiverem em uso.  
C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
D) Usar apenas índices locais secundários (LSI).  

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no Amazon DynamoDB?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

---

#### **9. Qual das seguintes opções é uma limitação do Amazon DynamoDB?**
A) Ele não suporta a criação de índices secundários.  
B) Ele tem um limite de 1000 tabelas por conta da AWS.  
C) Ele não suporta a integração com o AWS Lambda.  
D) Ele não permite a criação de chaves de partição. 

---

#### **10. Qual das seguintes opções é uma vantagem do uso do Amazon DynamoDB com o Amazon S3?**
A) Ele permite o armazenamento de grandes volumes de dados.  
B) Ele aumenta o custo de armazenamento de dados.  
C) Ele não suporta a criação de índices secundários.  
D) Ele não permite a integração com o AWS Lambda.  

---

**Resposta:** B) Índice Global Secundário (GSI)  
**Explicação:** O Índice Global Secundário (GSI) permite consultas flexíveis em diferentes atributos, com uma chave primária diferente da tabela base.

---

**Resposta:** B) AWS Lambda  
**Explicação:** O AWS Lambda pode ser usado para processar dados em tempo real no Amazon DynamoDB, acionado por eventos como inserções ou atualizações.

---

**Resposta:** A) Usar índices globais secundários (GSI) para consultas flexíveis.  
**Explicação:** O uso de índices globais secundários (GSI) permite consultas flexíveis e eficientes em diferentes atributos.

---

**Resposta:** B) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar o desempenho e a saúde do Amazon DynamoDB.

---

**Resposta:** C) Ele oferece desempenho consistente de milissegundos em qualquer escala.  
**Explicação:** O Amazon DynamoDB é projetado para oferecer desempenho consistente de milissegundos, independentemente da escala.

---

**Resposta:** A) Ele permite o processamento de dados em tempo real.  
**Explicação:** A integração com o AWS Lambda permite o processamento de dados em tempo real no Amazon DynamoDB.

---

**Resposta:** A) Usar a escalabilidade automática para ajustar a capacidade com base na demanda.  
**Explicação:** A escalabilidade automática ajusta a capacidade de leitura/escrita com base na demanda, otimizando custos.

---

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O Amazon DynamoDB integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

**Resposta:** B) Ele tem um limite de 1000 tabelas por conta da AWS.  
**Explicação:** O Amazon DynamoDB tem um limite de 1000 tabelas por conta da AWS, o que pode ser uma limitação para contas com muitas tabelas.

---

**Resposta:** A) Ele permite o armazenamento de grandes volumes de dados.  
**Explicação:** A integração com o Amazon S3 permite o armazenamento de grandes volumes de dados, complementando o DynamoDB para cenários de big data.

---

### **Resumo das Respostas**
1. B) Índice Global Secundário (GSI)  
2. B) AWS Lambda  
3. A) Usar índices globais secundários (GSI) para consultas flexíveis.  
4. B) Amazon CloudWatch  
5. C) Ele oferece desempenho consistente de milissegundos em qualquer escala.  
6. A) Ele permite o processamento de dados em tempo real.  
7. A) Usar a escalabilidade automática para ajustar a capacidade com base na demanda.  
8. B) Ele usa IAM para controlar o acesso a recursos e dados.  
9. B) Ele tem um limite de 1000 tabelas por conta da AWS.  
10. A) Ele permite o armazenamento de grandes volumes de dados.  

---
