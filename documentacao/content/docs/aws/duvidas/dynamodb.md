---
title: "Quando usar DynamoDB"
---

### **1. Visão Geral do Amazon DynamoDB**
- **O que é:** Um banco de dados NoSQL que oferece desempenho consistente de milissegundos em qualquer escala.
- **Casos de Uso Comuns:**
  - Aplicações web e móveis.
  - Jogos online.
  - Sistemas de recomendação.
  - Armazenamento de sessões e carrinhos de compras.

---

### **2. Componentes do Amazon DynamoDB**
#### **Tabelas**
- **Definição:** Coleções de itens (registros) que contêm atributos (campos).
- **Chaves:**
  - **Chave Primária:** Composta por uma chave de partição (Partition Key) ou uma combinação de chave de partição e chave de ordenação (Sort Key).

#### **Itens**
- **Definição:** Unidades de dados armazenados em uma tabela.
- **Atributos:** Pares de chave-valor que representam os dados.

#### **Índices**
- **Índices Globais Secundários (GSI):**
  - Permitem consultas flexíveis em diferentes atributos.
  - Podem ter uma chave primária diferente da tabela base.
- **Índices Locais Secundários (LSI):**
  - Permitem consultas em atributos adicionais dentro da mesma partição.
  - Compartilham a chave de partição da tabela base.

---

### **3. Funcionalidades Principais**
#### **Desempenho**
- **Escalabilidade Automática:** Ajusta automaticamente a capacidade de leitura/escrita com base na demanda.
- **Baixa Latência:** Oferece desempenho consistente de milissegundos.

#### **Disponibilidade e Durabilidade**
- **Multi-AZ (Multi-Availability Zone):** Replicação automática em múltiplas zonas de disponibilidade.
- **Backups Automáticos:** Backups contínuos e restauração pontual (Point-in-Time Recovery).

#### **Segurança**
- **IAM:** Controle de acesso usando políticas do IAM.
- **Cifragem:** Dados podem ser cifrados em repouso e em trânsito usando AWS KMS.
- **VPC:** Execução em VPCs para isolamento de rede.

#### **Integrações**
- **AWS Lambda:** Para processamento de dados em tempo real.
- **Amazon S3:** Para armazenamento de grandes volumes de dados.
- **Amazon Redshift:** Para análise de dados em um data warehouse.

---

### **4. Melhores Práticas**
#### **Desempenho**
- **Escolha de Chaves:** Use chaves de partição que distribuam os dados uniformemente para evitar hotspots.
- **Índices:** Use GSI e LSI para consultas flexíveis e eficientes.
- **Throughput Provisionado:** Ajuste a capacidade de leitura/escrita com base na demanda.

#### **Segurança**
- **IAM:** Use políticas granulares para controlar o acesso ao DynamoDB e aos dados.
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.
- **VPC:** Execute tabelas em uma VPC para isolamento de rede.

#### **Custos**
- **Escalabilidade Automática:** Use a escalabilidade automática para ajustar a capacidade com base na demanda.
- **Backups Automáticos:** Use backups automáticos para reduzir custos de armazenamento manual.

---

### **5. Tópicos Relevantes para o Exame**
- **Tabelas e Itens:** Entenda como criar e gerenciar tabelas e itens.
- **Índices:** Conheça os diferentes tipos de índices e quando usá-los.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Aplicações web, jogos online e sistemas de recomendação.

---

### **6. Exemplos de Perguntas do Exame**
1. **Qual tipo de índice no Amazon DynamoDB permite consultas flexíveis em diferentes atributos?**
   - A) Índice Local Secundário (LSI)  
   - B) Índice Global Secundário (GSI)  
   - C) Índice Primário  
   - D) Índice de Partição  
   **Resposta:** B) Índice Global Secundário (GSI).

2. **Qual serviço da AWS pode ser usado para processar dados em tempo real no Amazon DynamoDB?**
   - A) Amazon S3  
   - B) AWS Lambda  
   - C) Amazon Redshift  
   - D) AWS Glue  
   **Resposta:** B) AWS Lambda.

3. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon DynamoDB?**
   - A) Usar índices globais secundários (GSI) para consultas flexíveis.  
   - B) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   - C) Manter tabelas em execução 24/7, mesmo quando não estiverem em uso.  
   - D) Usar apenas a chave de partição para todas as consultas.  
   **Resposta:** A) Usar índices globais secundários (GSI) para consultas flexíveis.

4. **Qual serviço da AWS pode ser usado para monitorar métricas como uso de capacidade e latência no Amazon DynamoDB?**
   - A) AWS CloudTrail  
   - B) Amazon CloudWatch  
   - C) AWS Config  
   - D) AWS Trusted Advisor  
   **Resposta:** B) Amazon CloudWatch.

---

### **7. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie uma tabela DynamoDB e insira itens.
  - Configure índices globais secundários (GSI) para consultas flexíveis.
  - Integre o DynamoDB com o AWS Lambda para processamento de dados em tempo real.
