---
title: "Banco de dados"
---

### **1. Amazon RDS (Relational Database Service)**
**O que é**:  
Serviço gerenciado para bancos de dados relacionais (SQL), como MySQL, PostgreSQL, MariaDB, Oracle e SQL Server. Oferece alta disponibilidade, backups automatizados e escalabilidade vertical.

**Quando usar**:  
- Aplicações que exigem **modelo relacional** (transações ACID, joins complexos).  
- Casos de uso tradicionais: sistemas ERP, CRMs, aplicações web com estrutura fixa.  
- Requisitos de conformidade (ex: bancos de dados compatíveis com HIPAA).

**Benefícios**:  
- **Gerenciamento simplificado**: Patches, backups e failover automatizados.  
- **Alta disponibilidade**: Configuração Multi-AZ (réplica em outra Availability Zone).  
- **Escalabilidade vertical**: Aumento do tamanho da instância sob demanda.  
- **Segurança**: Criptografia em repouso (KMS) e em trânsito (SSL).  

**Exemplo de Arquitetura**:  
**Aplicação de E-commerce**:  
- **Camada Web**: EC2 ou Elastic Beanstalk.  
- **Banco de Dados**: RDS PostgreSQL em Multi-AZ para alta disponibilidade.  
- **Backup**: Snapshots automáticos diários e retenção de 7 dias.  
- **Escalabilidade**: Read Replicas para balanceamento de carga de leitura.  

---

### **2. Amazon DynamoDB**  
**O que é**:  
Banco de dados NoSQL totalmente gerenciado, **serverless** e de alta performance, com modelo de dados chave-valor e documento. Projetado para escalabilidade horizontal ilimitada.

**Quando usar**:  
- Workloads **OLTP** (transações rápidas e alta concorrência).  
- Aplicações com tráfego imprevisível (ex: jogos online, APIs de alta escala).  
- Dados não estruturados ou semi-estruturados (ex: carrinhos de compras, perfis de usuário).  

**Benefícios**:  
- **Escalabilidade automática**: Ajusta capacidade (RCU/WCU) conforme a demanda.  
- **Baixa latência**: Respostas em milissegundos, mesmo com milhões de solicitações.  
- **Serverless**: Sem provisionamento de servidores ou clusters.  
- **Global Tables**: Replicação multi-região para aplicações globais.  

**Exemplo de Arquitetura**:  
**Plataforma de Jogos Online**:  
- **API Backend**: Lambda + API Gateway.  
- **Banco de Dados**: DynamoDB com tabelas para perfis de jogadores e inventários.  
- **Escalabilidade**: Auto Scaling de WCU/RCU durante picos de acesso.  
- **Cache**: DAX (DynamoDB Accelerator) para consultas frequentes.  

---

### **3. Amazon Aurora**  
**O que é**:  
Banco de dados relacional compatível com MySQL e PostgreSQL, mas com desempenho até 5x superior. Combina a simplicidade do RDS com a escalabilidade de soluções empresariais.

**Quando usar**:  
- Aplicações que exigem **alta performance e escalabilidade horizontal**.  
- Sistemas críticos com requisitos de disponibilidade (ex: SaaS, fintechs).  
- Workloads híbridas (OLTP + analytics leves).  

**Benefícios**:  
- **Escalabilidade automática**: Armazenamento cresce de 10 GB até 128 TB.  
- **Multi-AZ nativo**: Tolerância a falhas com replicação em 6 cópias dos dados.  
- **Aurora Serverless**: Modo serverless para workloads imprevisíveis.  
- **Global Database**: Replicação cross-região com latência <1 segundo.  

**Exemplo de Arquitetura**:  
**Sistema Bancário**:  
- **Camada de Aplicação**: ECS Fargate com microsserviços.  
- **Banco de Dados**: Aurora PostgreSQL com Global Database para failover entre regiões.  
- **Backup**: Backup contínuo e snapshots manuais.  
- **Performance**: Instâncias otimizadas para IOPS (ex: db.r5.24xlarge).  

---

### **4. Amazon Redshift**  
**O que é**:  
Data warehouse gerenciado para **análises em grande escala (OLAP)**. Armazena dados em formato colunar e é otimizado para queries complexas em petabytes de dados.

**Quando usar**:  
- Business Intelligence (BI) e relatórios analíticos.  
- Processamento de dados históricos (ex: vendas, logs).  
- Integração com ferramentas ETL (ex: AWS Glue, dbt).  

**Benefícios**:  
- **Desempenho**: Consultas rápidas graças ao armazenamento colunar e compressão.  
- **Escalabilidade**: Aumento de nós sob demanda (clusters multi-node).  
- **Integração**: Conecta-se a S3 (Redshift Spectrum) para queries em data lakes.  
- **Custo-efetivo**: Preço por TB analisado, ideal para grandes volumes.  

**Exemplo de Arquitetura**:  
**Plataforma de Analytics**:  
- **Data Lake**: Dados brutos armazenados em S3 (formato Parquet).  
- **ETL**: AWS Glue para transformação e carga no Redshift.  
- **BI**: Amazon QuickSight conectado ao Redshift para dashboards.  
- **Escalabilidade**: Cluster RA3 com separação de storage e computação.  

---

### **Comparação entre os Serviços**

| **Critério**          | **RDS**                     | **DynamoDB**                | **Aurora**                   | **Redshift**                 |
|-----------------------|-----------------------------|-----------------------------|------------------------------|------------------------------|
| **Modelo**            | Relacional (SQL)            | NoSQL (chave-valor)         | Relacional otimizado (SQL)   | Data Warehouse (OLAP)        |
| **Escalabilidade**    | Vertical                    | Horizontal                  | Horizontal e vertical        | Horizontal (clusters)        |
| **Caso de Uso**       | OLTP tradicional            | Alta escala, baixa latência | OLTP de alta performance     | OLAP e análises complexas    |
| **Custo**             | Baseado em instância        | Baseado em RCU/WCU          | Similar ao RDS, mais eficiência | Baseado em nós de cluster    |
| **Disponibilidade**   | Multi-AZ                    | Multi-região (Global Tables)| Multi-AZ + Global Database   | Multi-AZ                     |
| **Exemplo Prático**   | Sistema ERP                 | Carrinho de compras         | Plataforma SaaS              | Relatório de vendas anual    |

---

### **Quando Escolher Cada Serviço?**
1. **RDS**:  
   - Migração de bancos SQL on-premises para a nuvem.  
   - Aplicações que exigem transações ACID e esquema rígido.  

2. **DynamoDB**:  
   - Workloads com picos imprevisíveis (ex: Black Friday).  
   - Dados semi-estruturados e alta velocidade de escrita/leitura.  

3. **Aurora**:  
   - Necessidade de compatibilidade com MySQL/PostgreSQL, mas com maior performance.  
   - Sistemas que exigem replicação global e failover automático.  

4. **Redshift**:  
   - Análises de grandes volumes históricos (ex: tendências de vendas).  
   - Integração com ferramentas de BI (ex: Tableau, QuickSight).  

---

### **Arquiteturas Híbridas**
#### **Exemplo: Plataforma de Varejo**  
- **Transações em Tempo Real (OLTP)**: Aurora PostgreSQL para pedidos e estoque.  
- **Perfil de Usuário**: DynamoDB para dados de login e preferências.  
- **Analytics**: Redshift para análise de vendas e estoque.  
- **Backup/Arquivamento**: S3 Glacier para logs antigos.  

---

### **Dicas para o Exame SAA-C03**
1. **RDS vs. Aurora**:  
   - Aurora é mais caro, mas oferece melhor performance e escalabilidade.  
   - Use RDS para compatibilidade com engines específicas (ex: Oracle).  

2. **DynamoDB vs. RDS**:  
   - DynamoDB não suporta joins ou transações complexas (use RDS/Aurora para isso).  

3. **Redshift vs. Athena**:  
   - Redshift é para queries repetitivas em dados estruturados.  
   - Athena (baseado em S3) é para queries ad-hoc em data lakes.  

4. **Global Tables (DynamoDB) vs. Global Database (Aurora)**:  
   - DynamoDB replica dados em milissegundos; Aurora replica em <1 segundo.  

---

### **Conclusão**
Cada serviço de banco de dados da AWS atende a necessidades específicas:  
- **RDS** e **Aurora** para workloads relacionais.  
- **DynamoDB** para NoSQL de alta escala.  
- **Redshift** para análise de dados em larga escala.  
