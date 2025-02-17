---
title: "Modelo Warehouse AWS"
---

## ** Arquitetura do Data Warehouse na AWS**  

🔹 **Armazenamento e Processamento**: Amazon Redshift  
🔹 **Ingestão de Dados**: AWS Glue, AWS DMS, AWS Kinesis Data Firehose  
🔹 **Governança e Segurança**: AWS IAM, AWS KMS, AWS Lake Formation  
🔹 **Consultas e BI**: Amazon QuickSight, Amazon Redshift Spectrum  
🔹 **Escalabilidade**: Amazon Redshift RA3 + Redshift Spectrum  

---

## ** Estrutura do Data Warehouse no Redshift**  

**Banco de Dados no Redshift**: `data_warehouse`  
&nbsp;&nbsp;&nbsp;&nbsp; `staging` → (dados brutos carregados)  
&nbsp;&nbsp;&nbsp;&nbsp; `ods` → (Operational Data Store - dados tratados)  
&nbsp;&nbsp;&nbsp;&nbsp; `dw` → (dados modelados para analytics)  
&nbsp;&nbsp;&nbsp;&nbsp; `marts` → (dados agregados para BI)  

**Modelagem**: Usamos **Star Schema** ou **Snowflake Schema** para otimizar performance.  

---

## ** Como garantir Segurança?**  

**IAM Policies** – Controla permissões de acesso ao Redshift.  
**Redshift Security Groups** – Restringe acessos externos.  
**AWS KMS** – Criptografa os dados no Redshift.  
**AWS Lake Formation** – Gerencia permissões refinadas nos dados.  
**CloudTrail + GuardDuty** – Monitora acessos e ameaças.  

---

## ** Fluxo de Processamento de Dados**  

**Ingestão de Dados**  
Dados chegam via **AWS Glue, AWS DMS, Kinesis Firehose ou S3 COPY**.  

**Armazenamento e Processamento**  
Dados brutos são carregados na tabela `staging` usando **COPY do S3 para Redshift**.  
**ETL no AWS Glue** ou **Stored Procedures no Redshift** transformam e movem dados para `dw`.  

**Consulta e Análise**  
**Amazon Redshift Spectrum** permite consultas em dados externos no S3.  
**Amazon QuickSight** gera dashboards interativos.  

---

## ** Benefícios dessa Arquitetura**  

**Alta Performance** → Processamento distribuído massivo no Redshift.  
**Econômico** → Armazena dados raramente acessados no S3 via Redshift Spectrum.  
**Seguro** → IAM, KMS e Lake Formation garantem controle.  
**Escalável** → RA3 Nodes permitem desacoplar armazenamento e computação.  
