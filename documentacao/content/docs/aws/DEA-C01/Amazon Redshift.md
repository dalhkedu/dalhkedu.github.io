---
title: "Amazon Redshift"
---

https://docs.aws.amazon.com/pt_br/redshift/latest/mgmt/welcome.html


### **1. Visão Geral do Amazon Redshift**
- **O que é:** Um data warehouse baseado em colunas, otimizado para análise de grandes volumes de dados.
- **Casos de Uso Comuns:**
  - Análise de dados em tempo real.
  - Business intelligence (BI) e relatórios.
  - Integração com data lakes (S3) para consultas híbridas.
  - Armazenamento e análise de dados históricos.

---

### **2. Arquitetura do Amazon Redshift**
#### **Clusters**
- **Definição:** Um conjunto de nós (servidores) que armazenam e processam dados.
- **Tipos de Nós:**
  - **Leader Node:** Gerencia consultas e coordena a execução.
  - **Compute Nodes:** Armazenam dados e executam consultas.
- **Tipos de Clusters:**
  - **Dense Storage (DS):** Para grandes volumes de dados.
  - **Dense Compute (DC):** Para alta performance em consultas complexas.

#### **Colunas e Linhas**
- **Armazenamento Colunar:** Dados são armazenados por coluna, o que melhora a eficiência em consultas analíticas.
- **Compressão:** Reduz o espaço de armazenamento e melhora o desempenho.

#### **Distribuição de Dados**
- **Estilos de Distribuição:**
  - **EVEN:** Dados distribuídos uniformemente entre os nós.
  - **KEY:** Dados distribuídos com base em uma coluna específica.
  - **ALL:** Uma cópia completa dos dados em cada nó (útil para tabelas pequenas).

#### **Ordenação de Dados**
- **Sort Keys:** Define a ordem física dos dados para otimizar consultas.
  - **Compound Sort Key:** Combinação de múltiplas colunas.
  - **Interleaved Sort Key:** Distribui a prioridade igualmente entre as colunas.

---

### **3. Funcionalidades Principais**
#### **Redshift Spectrum**
- **O que é:** Permite consultar dados diretamente no Amazon S3 sem carregá-los no Redshift.
- **Benefícios:** Reduz custos de armazenamento e permite análises em data lakes.

#### **Concurrency Scaling**
- **O que é:** Escalona automaticamente a capacidade de processamento para lidar com picos de carga.
- **Benefícios:** Mantém o desempenho durante consultas simultâneas.

#### **Materialized Views**
- **O que é:** Visualizações pré-computadas que melhoram o desempenho de consultas repetitivas.
- **Benefícios:** Reduz o tempo de execução de consultas complexas.

#### **RA3 Nodes**
- **O que é:** Nós que separam armazenamento e computação, permitindo escalabilidade independente.
- **Benefícios:** Reduz custos e melhora a flexibilidade.

---

### **4. Integrações com Outros Serviços AWS**
- **Amazon S3:** Carregamento e descarregamento de dados (COPY e UNLOAD).
- **AWS Glue:** Catalogação e preparação de dados para o Redshift.
- **Amazon Athena:** Consulta de dados no Redshift usando SQL.
- **Amazon QuickSight:** Visualização de dados armazenados no Redshift.
- **AWS Lambda:** Execução de funções personalizadas durante o processamento de dados.

---

### **5. Melhores Práticas**
#### **Desempenho**
- **Escolha de Sort Keys e Distribution Keys:** Otimize consultas com base nos padrões de acesso.
- **Compressão de Dados:** Use compressão para reduzir o espaço e melhorar o desempenho.
- **Concurrency Scaling:** Habilite para lidar com picos de carga.

#### **Segurança**
- **Cifragem:** Habilite a cifragem em repouso e em trânsito.
- **IAM e VPC:** Use IAM para controle de acesso e VPC para isolamento de rede.
- **Auditoria:** Use o AWS CloudTrail para monitorar atividades no Redshift.

#### **Custos**
- **RA3 Nodes:** Separe armazenamento e computação para reduzir custos.
- **Pause e Resume:** Pause clusters quando não estiverem em uso para economizar.
- **Redshift Spectrum:** Use para consultar dados diretamente no S3, evitando custos de armazenamento no Redshift.

---

### **6. Tópicos Relevantes para o Exame**
- **Arquitetura:** Entenda a diferença entre Leader Node e Compute Nodes.
- **Distribuição e Ordenação:** Saiba como escolher Distribution Keys e Sort Keys.
- **Integrações:** Como o Redshift se integra a S3, Glue, Athena e QuickSight.
- **Segurança:** Cifragem, IAM e VPC.
- **Casos de Uso:** Análise de dados em tempo real, BI e data lakes.

---

### **7. Exemplos de Perguntas do Exame**
1. **Qual das seguintes opções é verdadeira sobre o Redshift Spectrum?**
   - A) Ele permite consultar dados diretamente no Amazon S3.  
   - B) Ele só funciona com dados armazenados no Redshift.  
   - C) Ele não suporta consultas SQL.  
   - D) Ele aumenta os custos de armazenamento no Redshift.  
   **Resposta:** A) Ele permite consultar dados diretamente no Amazon S3.

2. **Qual estilo de distribuição é recomendado para tabelas pequenas no Amazon Redshift?**
   - A) EVEN  
   - B) KEY  
   - C) ALL  
   - D) INTERLEAVED  
   **Resposta:** C) ALL.

3. **Qual recurso do Amazon Redshift permite escalar automaticamente a capacidade de processamento durante picos de carga?**
   - A) Redshift Spectrum  
   - B) Concurrency Scaling  
   - C) Materialized Views  
   - D) RA3 Nodes  
   **Resposta:** B) Concurrency Scaling.

4. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon Redshift?**
   - A) Usar Distribution Keys aleatórias.  
   - B) Desabilitar a compressão de dados.  
   - C) Escolher Sort Keys com base nos padrões de consulta.  
   - D) Armazenar todos os dados no Leader Node.  
   **Resposta:** C) Escolher Sort Keys com base nos padrões de consulta.

---

### **8. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um cluster Redshift e carregue dados do S3.
  - Configure Distribution Keys e Sort Keys.
  - Use o Redshift Spectrum para consultar dados no S3.

---