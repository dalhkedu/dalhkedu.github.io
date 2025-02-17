---
title: "Modelo Lake AWS"
---

## ** Arquitetura do Data Lake na AWS**  

**Armazenamento**: Amazon S3 (Data Lake principal)  
**Segurança**: AWS IAM, AWS KMS, AWS Lake Formation  
**Organização dos Dados**: S3 Data Particionada + Catalogação com AWS Glue  
**Processamento**: AWS Glue, Amazon Athena e Amazon EMR  
**Governança**: AWS Lake Formation + AWS CloudTrail  
**Visualização**: Amazon QuickSight  

---

## ** Estrutura do Data Lake no S3**  

 `s3://meu-datalake/`  
&nbsp;&nbsp;&nbsp;&nbsp; `raw/` (dados brutos)  
&nbsp;&nbsp;&nbsp;&nbsp; `processed/` (dados transformados)  
&nbsp;&nbsp;&nbsp;&nbsp; `curated/` (dados prontos para análise)  

**Organização:** Usamos partições por **ano/mês/dia** para eficiência nas consultas.  

---

## ** Como garantir Segurança?**  

**IAM Policies** – Controla permissões de acesso.  
**S3 Bucket Policies** – Bloqueia acessos não autorizados.  
**AWS KMS** – Criptografa os dados no S3.  
**AWS Lake Formation** – Gerencia permissões refinadas nos dados.  
**CloudTrail + GuardDuty** – Monitora acessos e ameaças.  

---

## **📌 Fluxo de Processamento de Dados**  

**Ingestão de Dados** 🔄  
Dados chegam via **AWS Kinesis, AWS DMS, AWS Glue ETL, ou AWS Transfer**.  

**Armazenamento e Catalogação**
Dados brutos vão para `s3://meu-datalake/raw/`  
O **AWS Glue Crawler** cria um **Catálogo de Dados**.  

**Transformação e Enriquecimento** 
O **AWS Glue ETL** processa os dados, transformando para formatos otimizados (Parquet, ORC).  
Dados transformados vão para `s3://meu-datalake/processed/`  

**Consulta e Análise**
**Amazon Athena** permite consultas SQL diretas no S3.  
**Amazon EMR** roda jobs Spark para análises avançadas.  
**Amazon QuickSight** visualiza insights em dashboards.  

---

## ** Benefícios dessa Arquitetura**  

**Escalável** → S3 suporta petabytes sem precisar de servidores.  
**Econômico** → Sem necessidade de manter servidores 24/7.  
**Seguro** → IAM, KMS e Lake Formation garantem controle.  
**Rápido** → Partições no S3 + Parquet aceleram consultas.  

