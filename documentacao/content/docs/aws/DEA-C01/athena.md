---
title: "Amazon Athena"
---

https://docs.aws.amazon.com/pt_br/athena/latest/ug/what-is.html

### **1. Visão Geral do Amazon Athena**
- **O que é:** Um serviço de consulta interativa que permite analisar dados no S3 usando SQL.
- **Casos de Uso Comuns:**
  - Consultas ad-hoc em grandes volumes de dados armazenados no S3.
  - Análise de logs e métricas.
  - Integração com data lakes.
  - Criação de relatórios e dashboards.

---

### **2. Funcionamento do Amazon Athena**
#### **Consultas SQL**
- **Linguagem:** SQL padrão (ANSI SQL).
- **Formatos Suportados:** CSV, JSON, Parquet, ORC, Avro e outros.
- **Desempenho:** Otimizado para consultas em grandes volumes de dados.

#### **Integração com o Amazon S3**
- **Armazenamento:** Dados são armazenados no S3, sem necessidade de carregá-los no Athena.
- **Custos:** Cobrança baseada na quantidade de dados escaneados (pay-per-query).

#### **Data Catalog**
- **O que é:** Repositório de metadados que descreve a estrutura dos dados.
- **Integração com o AWS Glue:** O Glue Data Catalog pode ser usado para gerenciar metadados no Athena.

---

### **3. Funcionalidades Principais**
#### **Desempenho**
- **Particionamento:** Melhora o desempenho ao reduzir a quantidade de dados escaneados.
- **Compressão:** Formatos como Parquet e ORC reduzem o espaço de armazenamento e melhoram o desempenho.

#### **Segurança**
- **Cifragem:** Dados podem ser cifrados em repouso e em trânsito.
- **IAM:** Controle de acesso usando políticas do IAM.
- **VPC:** Suporta execução em VPCs para isolamento de rede.

#### **Integrações**
- **AWS Glue:** Para catalogação e preparação de dados.
- **Amazon Redshift:** Para análise de dados em um data warehouse.
- **Amazon QuickSight:** Para visualização de dados.
- **AWS Lambda:** Para automação de tarefas.

---

### **4. Melhores Práticas**
#### **Desempenho**
- **Particionamento:** Use particionamento para reduzir a quantidade de dados escaneados.
- **Formato de Dados:** Use formatos colunares como Parquet ou ORC para melhorar o desempenho e reduzir custos.
- **Compressão:** Habilite a compressão para reduzir o espaço de armazenamento e melhorar o desempenho.

#### **Segurança**
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.
- **IAM:** Use políticas granulares para controlar o acesso ao Athena e aos dados no S3.
- **VPC:** Execute consultas em uma VPC para isolamento de rede.

#### **Custos**
- **Escaneamento de Dados:** Otimize consultas para reduzir a quantidade de dados escaneados.
- **Formato de Dados:** Use formatos colunares e compressão para reduzir custos.

---

### **5. Tópicos Relevantes para o Exame**
- **Consultas SQL:** Entenda como escrever consultas SQL eficientes no Athena.
- **Particionamento:** Saiba como particionar dados para melhorar o desempenho.
- **Integrações:** Como o Athena se integra a S3, Glue, Redshift e QuickSight.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Análise de logs, consultas ad-hoc e integração com data lakes.

---

### **6. Exemplos de Perguntas do Exame**
1. **Qual formato de dados é recomendado para melhorar o desempenho e reduzir custos no Amazon Athena?**
   - A) CSV  
   - B) JSON  
   - C) Parquet  
   - D) TXT  
   **Resposta:** C) Parquet.

2. **Qual serviço da AWS pode ser usado para catalogar metadados no Amazon Athena?**
   - A) Amazon S3  
   - B) AWS Glue  
   - C) Amazon Redshift  
   - D) Amazon QuickSight  
   **Resposta:** B) AWS Glue.

3. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon Athena?**
   - A) Usar particionamento para reduzir a quantidade de dados escaneados.  
   - B) Armazenar todos os dados em um único arquivo grande.  
   - C) Desabilitar a compressão de dados.  
   - D) Usar formatos de dados não estruturados.  
   **Resposta:** A) Usar particionamento para reduzir a quantidade de dados escaneados.

4. **Qual serviço da AWS pode ser usado para visualizar dados consultados no Amazon Athena?**
   - A) Amazon S3  
   - B) AWS Glue  
   - C) Amazon Redshift  
   - D) Amazon QuickSight  
   **Resposta:** D) Amazon QuickSight.

---

### **7. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie tabelas no Athena a partir de dados no S3.
  - Execute consultas SQL no Athena e analise os resultados.
  - Integre o Athena com o AWS Glue para catalogação de dados.

---