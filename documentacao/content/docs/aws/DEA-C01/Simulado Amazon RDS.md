---
title: "Simulado: Amazon RDS"
---

### **Simulado: Amazon RDS**

#### **1. Qual motor de banco de dados é recomendado para aplicações web de código aberto no Amazon RDS?**
A) MySQL  
B) Oracle  
C) SQL Server  
D) Amazon DynamoDB  

**Resposta:** A) MySQL  
**Explicação:** O MySQL é um banco de dados relacional de código aberto amplamente utilizado para aplicações web.

---

#### **2. Qual funcionalidade do Amazon RDS permite a replicação síncrona para alta disponibilidade e recuperação de desastres?**
A) Multi-AZ  
B) Réplicas de Leitura  
C) Backups Automáticos  
D) Recuperação Pontual  

**Resposta:** A) Multi-AZ  
**Explicação:** O Multi-AZ (Multi-Availability Zone) permite a replicação síncrona para alta disponibilidade e recuperação de desastres.

---

#### **3. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon RDS?**
A) Usar instâncias com baixo desempenho para todas as tarefas.  
B) Criar índices para melhorar o desempenho de consultas.  
C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
D) Manter bancos de dados em execução 24/7, mesmo quando não estiverem em uso.  

**Resposta:** B) Criar índices para melhorar o desempenho de consultas.  
**Explicação:** A criação de índices melhora o desempenho de consultas ao reduzir o tempo de busca por dados.

---

#### **4. Qual serviço da AWS pode ser usado para monitorar métricas como uso de CPU e memória no Amazon RDS?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor  

**Resposta:** B) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar o desempenho e a saúde do Amazon RDS.

---

#### **5. Qual das seguintes opções é verdadeira sobre o Amazon RDS?**
A) Ele não suporta a execução de bancos de dados em uma VPC.  
B) Ele permite a execução de motores como MySQL, PostgreSQL e Oracle.  
C) Ele não se integra ao Amazon S3.  
D) Ele não suporta a cifragem de dados em repouso.  

**Resposta:** B) Ele permite a execução de motores como MySQL, PostgreSQL e Oracle.  
**Explicação:** O Amazon RDS suporta vários motores de banco de dados, incluindo MySQL, PostgreSQL, Oracle, SQL Server e MariaDB.

---

#### **6. Qual das seguintes opções é uma vantagem do uso do Amazon RDS com o Amazon S3?**
A) Ele permite o armazenamento de dados diretamente no S3, sem a necessidade de usar o RDS.  
B) Ele permite o armazenamento de backups e snapshots no S3.  
C) Ele não suporta a leitura de dados diretamente do S3.  
D) Ele aumenta o custo de armazenamento de dados.  

**Resposta:** B) Ele permite o armazenamento de backups e snapshots no S3.  
**Explicação:** O Amazon RDS pode armazenar backups e snapshots no S3, facilitando a recuperação de dados e reduzindo custos.

---

#### **7. Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon RDS?**
A) Usar instâncias com alto desempenho para todas as tarefas.  
B) Ajustar a capacidade de computação e armazenamento com base na demanda.  
C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
D) Manter bancos de dados em execução 24/7, mesmo quando não estiverem em uso.  

**Resposta:** B) Ajustar a capacidade de computação e armazenamento com base na demanda.  
**Explicação:** Ajustar a capacidade de computação e armazenamento com base na demanda ajuda a otimizar custos e desempenho.

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no Amazon RDS?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O Amazon RDS integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

#### **9. Qual das seguintes opções é uma limitação do Amazon RDS?**
A) Ele não suporta a execução de motores de banco de dados de código aberto.  
B) Ele tem um tempo de execução máximo de 15 minutos por consulta.  
C) Ele não suporta a integração com o Amazon S3.  
D) Ele requer o gerenciamento manual de servidores.  

**Resposta:** B) Ele tem um tempo de execução máximo de 15 minutos por consulta.  
**Explicação:** O Amazon RDS não tem um tempo de execução máximo por consulta, mas consultas de longa duração podem aumentar custos e exigir otimização.

---

#### **10. Qual das seguintes opções é uma vantagem do uso do Amazon RDS com o AWS Glue?**
A) Ele permite a catalogação automática de metadados.  
B) Ele aumenta o custo de processamento de dados.  
C) Ele não suporta a consulta de dados no S3.  
D) Ele não se integra ao Amazon Redshift.  

**Resposta:** A) Ele permite a catalogação automática de metadados.  
**Explicação:** A integração com o AWS Glue permite a catalogação automática de metadados, facilitando a descoberta e organização de dados.

---

### **Resumo das Respostas**
1. A) MySQL  
2. A) Multi-AZ  
3. B) Criar índices para melhorar o desempenho de consultas.  
4. B) Amazon CloudWatch  
5. B) Ele permite a execução de motores como MySQL, PostgreSQL e Oracle.  
6. B) Ele permite o armazenamento de backups e snapshots no S3.  
7. B) Ajustar a capacidade de computação e armazenamento com base na demanda.  
8. B) Ele usa IAM para controlar o acesso a recursos e dados.  
9. B) Ele tem um tempo de execução máximo de 15 minutos por consulta.  
10. A) Ele permite a catalogação automática de metadados.  

---
