---
title: "Amazon RDS"
---

### **1. Visão Geral do Amazon RDS**
- **O que é:** Um serviço gerenciado para bancos de dados relacionais.
- **Casos de Uso Comuns:**
  - Aplicações web e móveis.
  - Armazenamento de dados transacionais.
  - Data warehouses e análise de dados.
  - Migração de bancos de dados para a nuvem.

---

### **2. Motores de Banco de Dados Suportados**
- **MySQL:** Banco de dados relacional de código aberto.
- **PostgreSQL:** Banco de dados relacional avançado de código aberto.
- **Oracle:** Banco de dados relacional empresarial.
- **SQL Server:** Banco de dados relacional da Microsoft.
- **MariaDB:** Banco de dados relacional de código aberto, fork do MySQL.

---

### **3. Funcionalidades Principais**
#### **Escalabilidade**
- **Escalamento Vertical:** Aumento ou redução da capacidade de computação e armazenamento.
- **Escalamento Horizontal:** Uso de réplicas de leitura para distribuir a carga de trabalho.

#### **Disponibilidade e Durabilidade**
- **Multi-AZ (Multi-Availability Zone):** Replicação síncrona para alta disponibilidade e recuperação de desastres.
- **Backups Automáticos:** Backups diários e snapshots manuais.
- **Recuperação Pontual (Point-in-Time Recovery):** Restauração do banco de dados para qualquer momento dentro do período de retenção.

#### **Segurança**
- **Cifragem:** Dados podem ser cifrados em repouso e em trânsito usando AWS KMS.
- **IAM:** Controle de acesso usando políticas do IAM.
- **VPC:** Execução em VPCs para isolamento de rede.
- **Autenticação:** Integração com IAM e autenticação nativa do banco de dados.

#### **Monitoramento**
- **CloudWatch:** Monitora métricas como uso de CPU, memória e armazenamento.
- **Logs:** Armazena logs de execução no CloudWatch Logs.

---

### **4. Melhores Práticas**
#### **Desempenho**
- **Escolha de Instâncias:** Use instâncias otimizadas para banco de dados (ex.: instâncias com alto desempenho de armazenamento e rede).
- **Indexação:** Crie índices para melhorar o desempenho de consultas.
- **Particionamento:** Use particionamento para melhorar o desempenho de consultas em grandes volumes de dados.

#### **Segurança**
- **IAM:** Use políticas granulares para controlar o acesso ao RDS e aos dados.
- **VPC:** Execute bancos de dados em uma VPC para isolamento de rede.
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.

#### **Custos**
- **Escalamento Vertical:** Ajuste a capacidade de computação e armazenamento com base na demanda para otimizar custos.
- **Backups Automáticos:** Use backups automáticos para reduzir custos de armazenamento manual.
- **Recuperação Pontual:** Configure a recuperação pontual para reduzir o tempo de inatividade.

---

### **5. Tópicos Relevantes para o Exame**
- **Motores de Banco de Dados:** Conheça os motores suportados (MySQL, PostgreSQL, Oracle, SQL Server, MariaDB).
- **Escalabilidade:** Entenda a diferença entre escalamento vertical e horizontal.
- **Disponibilidade:** Saiba como configurar e usar Multi-AZ e réplicas de leitura.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Aplicações web, armazenamento de dados transacionais e migração para a nuvem.

---

### **6. Exemplos de Perguntas do Exame**
1. **Qual motor de banco de dados é recomendado para aplicações web de código aberto no Amazon RDS?**
   - A) MySQL  
   - B) Oracle  
   - C) SQL Server  
   - D) Amazon DynamoDB  
   **Resposta:** A) MySQL.

2. **Qual funcionalidade do Amazon RDS permite a replicação síncrona para alta disponibilidade e recuperação de desastres?**
   - A) Multi-AZ  
   - B) Réplicas de Leitura  
   - C) Backups Automáticos  
   - D) Recuperação Pontual  
   **Resposta:** A) Multi-AZ.

3. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon RDS?**
   - A) Usar instâncias com baixo desempenho para todas as tarefas.  
   - B) Criar índices para melhorar o desempenho de consultas.  
   - C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   - D) Manter bancos de dados em execução 24/7, mesmo quando não estiverem em uso.  
   **Resposta:** B) Criar índices para melhorar o desempenho de consultas.

4. **Qual serviço da AWS pode ser usado para monitorar métricas como uso de CPU e memória no Amazon RDS?**
   - A) AWS CloudTrail  
   - B) Amazon CloudWatch  
   - C) AWS Config  
   - D) AWS Trusted Advisor  
   **Resposta:** B) Amazon CloudWatch.

---

### **7. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um banco de dados RDS com MySQL e configure Multi-AZ.
  - Execute consultas SQL no banco de dados e analise o desempenho.
  - Configure backups automáticos e recuperação pontual.

---
