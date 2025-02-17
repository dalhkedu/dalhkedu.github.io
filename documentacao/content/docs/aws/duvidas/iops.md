---
title: "O que é IOPS"
---

### **O que é IOPS (Input/Output Operations Per Second)?**  
IOPS (Operações de Entrada/Saída por Segundo) é uma métrica que mede a quantidade de operações de leitura e escrita que um sistema de armazenamento consegue processar por segundo. Quanto maior o IOPS, maior a capacidade de processamento de dados do armazenamento.

---

## **Onde o IOPS é aplicado na AWS?**  
O IOPS é usado principalmente nos serviços de armazenamento e bancos de dados da AWS para otimizar a performance de leitura e escrita. Os principais serviços onde o IOPS é relevante são:

### **Amazon EBS (Elastic Block Store) - Discos para EC2**
O **Amazon EBS** fornece volumes de armazenamento que suportam diferentes níveis de IOPS:
- **gp3 (General Purpose SSD)** → Permite ajustar IOPS separadamente da capacidade do disco.
- **io1/io2 (Provisioned IOPS SSD)** → Discos otimizados para alto desempenho, podendo provisionar até 256.000 IOPS.
- **st1 (Throughput Optimized HDD) e sc1 (Cold HDD)** → Discos de baixo custo sem otimização para IOPS.

➡ **Exemplo de uso:** Se você tem um banco de dados de alta performance rodando em um **EC2**, um volume **io2** pode fornecer IOPS altos para evitar gargalos.

---

### **Amazon RDS (Relational Database Service)**
Os bancos de dados do **Amazon RDS** também permitem escolher volumes com diferentes níveis de IOPS:
- **GP3/GP2** (SSD Padrão) → Indicado para cargas de trabalho normais.
- **IO1/IO2 (Provisioned IOPS SSD)** → Indicado para bancos que exigem alta taxa de leitura e escrita, como PostgreSQL e MySQL de alto desempenho.

➡ **Exemplo de uso:** Um banco de dados **Oracle ou SQL Server** em RDS precisa de IOPS provisionado para garantir resposta rápida a queries pesadas.

---

### **Amazon Aurora**
O **Aurora** usa armazenamento distribuído e otimiza automaticamente o IOPS com base no workload. Ele pode escalar automaticamente os IOPS conforme necessário.

➡ **Exemplo de uso:** Um banco de dados Aurora MySQL escalável para uma aplicação web de alta demanda.

---

### **Amazon DynamoDB**
O **DynamoDB**, banco NoSQL da AWS, utiliza **Throughput Read/Write Capacity**, que é similar ao IOPS para bancos de chave-valor.

➡ **Exemplo de uso:** Um aplicativo de alta performance que precisa de leituras e escritas rápidas, como um sistema de recomendação.

---

### **Amazon FSx for Windows/Lustre**
O **Amazon FSx**, serviço de sistema de arquivos gerenciado, permite ajustar IOPS para cargas intensivas de leitura/escrita, como processamento de Big Data.

➡ **Exemplo de uso:** Empresas que rodam aplicações CAD/CAM ou análises financeiras podem usar FSx for Windows/Lustre.

---

## **Conclusão**
O IOPS é um fator crítico para o desempenho de discos e bancos de dados na AWS. Se você precisa de alto desempenho em **EBS, RDS, Aurora, DynamoDB ou FSx**, ajustar o IOPS corretamente pode evitar gargalos e garantir um sistema rápido e eficiente.
