https://docs.aws.amazon.com/pt_br/quicksight/latest/user/welcome.html
---

### **1. Visão Geral do Amazon QuickSight**
- **O que é:** Um serviço de BI que permite criar visualizações interativas, painéis e relatórios.
- **Casos de Uso Comuns:**
  - Análise de dados em tempo real.
  - Criação de painéis interativos para tomada de decisões.
  - Compartilhamento de insights com equipes e stakeholders.
  - Integração com data lakes e data warehouses.

---

### **2. Funcionalidades Principais**
#### **Visualizações Interativas**
- **Tipos de Gráficos:** Barras, linhas, pizza, dispersão, mapas, tabelas pivotantes, etc.
- **Interatividade:** Filtros, drill-downs e highlights para explorar dados.

#### **Integrações**
- **Amazon S3:** Para análise de dados armazenados em data lakes.
- **Amazon Redshift:** Para análise de dados em data warehouses.
- **Amazon RDS:** Para análise de dados em bancos de dados relacionais.
- **Amazon Athena:** Para consulta de dados diretamente no S3.
- **AWS Glue:** Para catalogação e preparação de dados.

#### **SPICE (Super-fast, Parallel, In-memory Calculation Engine)**
- **O que é:** Um mecanismo de cálculo em memória que acelera a análise de dados.
- **Benefícios:** Desempenho rápido e escalável para grandes volumes de dados.

#### **Segurança**
- **IAM:** Controle de acesso usando políticas do IAM.
- **Cifragem:** Dados podem ser cifrados em repouso e em trânsito usando AWS KMS.
- **VPC:** Execução em VPCs para isolamento de rede.

#### **Colaboração**
- **Compartilhamento:** Compartilhe painéis e relatórios com usuários e grupos.
- **Embedding:** Incorpore visualizações em aplicações web e móveis.

---

### **3. Melhores Práticas**
#### **Desempenho**
- **Uso de SPICE:** Use o SPICE para acelerar a análise de grandes volumes de dados.
- **Otimização de Consultas:** Otimize consultas para reduzir o tempo de carregamento de dados.

#### **Segurança**
- **IAM:** Use políticas granulares para controlar o acesso ao QuickSight e aos dados.
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.
- **VPC:** Execute análises em uma VPC para isolamento de rede.

#### **Custos**
- **Escalabilidade:** O QuickSight escala automaticamente com base na demanda, reduzindo custos.
- **Uso de SPICE:** Use o SPICE para reduzir o custo de consultas repetitivas.

---

### **4. Tópicos Relevantes para o Exame**
- **Visualizações:** Conheça os tipos de gráficos e interatividades disponíveis.
- **Integrações:** Como o QuickSight se integra a S3, Redshift, RDS, Athena e Glue.
- **SPICE:** Entenda o mecanismo de cálculo em memória e seus benefícios.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Análise de dados em tempo real, criação de painéis e compartilhamento de insights.

---

### **5. Exemplos de Perguntas do Exame**
1. **Qual mecanismo de cálculo em memória é usado pelo Amazon QuickSight para acelerar a análise de dados?**
   - A) Amazon Redshift  
   - B) SPICE  
   - C) Amazon Athena  
   - D) AWS Glue  
   **Resposta:** B) SPICE.

2. **Qual serviço da AWS pode ser usado para consultar dados diretamente no S3 e visualizá-los no Amazon QuickSight?**
   - A) Amazon Redshift  
   - B) Amazon Athena  
   - C) Amazon RDS  
   - D) AWS Glue  
   **Resposta:** B) Amazon Athena.

3. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de análises no Amazon QuickSight?**
   - A) Usar o SPICE para acelerar a análise de grandes volumes de dados.  
   - B) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   - C) Manter painéis em execução 24/7, mesmo quando não estiverem em uso.  
   - D) Usar formatos de dados não comprimidos.  
   **Resposta:** A) Usar o SPICE para acelerar a análise de grandes volumes de dados.

4. **Qual serviço da AWS pode ser usado para catalogar metadados e preparar dados para análise no Amazon QuickSight?**
   - A) Amazon S3  
   - B) Amazon Redshift  
   - C) AWS Glue  
   - D) Amazon Athena  
   **Resposta:** C) AWS Glue.

---

### **6. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um painel no QuickSight usando dados do Amazon S3.
  - Configure o SPICE para acelerar a análise de dados.
  - Compartilhe um painel com outros usuários e teste a interatividade.

---
