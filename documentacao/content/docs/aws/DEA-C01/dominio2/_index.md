---
title: "Domínio 2: Armazenamento e Gerenciamento de Dados"
---

## **1. Escolher o Armazenamento Adequado para Diferentes Casos de Uso**
A escolha do armazenamento depende do tipo de dados, do padrão de acesso e dos requisitos de desempenho e custo. Aqui estão os principais serviços de armazenamento da AWS e seus casos de uso:

### **Serviços de Armazenamento e Casos de Uso**
1. **Amazon S3 (Simple Storage Service):**
   - **Casos de Uso:**
     - Armazenamento de objetos para data lakes.
     - Backup e recuperação de desastres.
     - Hospedagem de arquivos estáticos para websites.
   - **Características:**
     - Escalável, durável e altamente disponível.
     - Suporta classes de armazenamento (S3 Standard, S3 Intelligent-Tiering, S3 Glacier).

2. **Amazon RDS (Relational Database Service):**
   - **Casos de Uso:**
     - Bancos de dados relacionais para aplicações web e móveis.
     - Armazenamento de dados transacionais.
   - **Características:**
     - Suporta motores como MySQL, PostgreSQL, Oracle e SQL Server.
     - Escalável e gerenciado.

3. **Amazon DynamoDB:**
   - **Casos de Uso:**
     - Bancos de dados NoSQL para aplicações de alta performance.
     - Armazenamento de dados semi-estruturados.
   - **Características:**
     - Escalável, sem servidor e de baixa latência.
     - Ideal para cargas de trabalho com alta taxa de leitura/escrita.

4. **Amazon Redshift:**
   - **Casos de Uso:**
     - Data warehouses para análise de grandes volumes de dados.
     - Business intelligence e relatórios.
   - **Características:**
     - Otimizado para consultas SQL em larga escala.
     - Integração com S3 e Glue.

5. **Amazon Glacier:**
   - **Casos de Uso:**
     - Armazenamento de arquivamento de longo prazo.
     - Dados raramente acessados.
   - **Características:**
     - Baixo custo, com tempos de recuperação variáveis (minutos a horas).

---

## **2. Gerenciar o Ciclo de Vida dos Dados**
O gerenciamento do ciclo de vida dos dados envolve a movimentação de dados entre diferentes classes de armazenamento e a exclusão de dados desnecessários para otimizar custos.

### **Amazon S3 Lifecycle**
- **O que é:** Regras para automatizar a transição de objetos entre classes de armazenamento ou excluí-los após um período.
- **Casos de Uso:**
  - Transição de dados para S3 Glacier após 30 dias.
  - Exclusão de dados após 1 ano.
- **Exemplo de Configuração:**
  - Transição para S3 Glacier após 30 dias.
  - Exclusão permanente após 365 dias.

### **Amazon Glacier Vault Lock**
- **O que é:** Políticas imutáveis para garantir que dados não sejam excluídos ou modificados por um período definido.
- **Casos de Uso:**
  - Conformidade com regulamentações (ex.: GDPR, HIPAA).

---

## **3. Implementar Estratégias de Particionamento e Indexação**
O particionamento e a indexação são técnicas essenciais para melhorar o desempenho de consultas e reduzir custos.

### **Particionamento**
1. **Amazon S3:**
   - **Estratégias:**
     - Particionamento por data (ex.: `s3://bucket/year=2023/month=10/day=01/`).
     - Particionamento por categoria ou região.
   - **Benefícios:**
     - Reduz a quantidade de dados escaneados em consultas.
     - Melhora o desempenho de ferramentas como Amazon Athena e AWS Glue.

2. **Amazon Redshift:**
   - **Estratégias:**
     - Particionamento por colunas de data ou chaves de distribuição.
   - **Benefícios:**
     - Melhora o desempenho de consultas SQL.

3. **Amazon DynamoDB:**
   - **Estratégias:**
     - Escolha de chaves de partição e ordenação para distribuição uniforme de dados.
   - **Benefícios:**
     - Evita hotspots e melhora a escalabilidade.

### **Indexação**
1. **Amazon RDS:**
   - **Estratégias:**
     - Criação de índices em colunas frequentemente consultadas.
   - **Benefícios:**
     - Acelera consultas SQL.

2. **Amazon DynamoDB:**
   - **Estratégias:**
     - Uso de índices globais secundários (GSI) e índices locais secundários (LSI).
   - **Benefícios:**
     - Permite consultas flexíveis em diferentes atributos.

---

## **4. Garantir a Segurança dos Dados**
A segurança dos dados é um aspecto crítico no gerenciamento de armazenamento. A AWS oferece várias ferramentas e práticas para proteger dados.

### **Ferramentas e Práticas de Segurança**
1. **IAM (Identity and Access Management):**
   - **O que é:** Controle de acesso granular para usuários, grupos e funções.
   - **Casos de Uso:**
     - Restringir acesso a buckets S3 ou tabelas DynamoDB.
     - Conceder permissões mínimas necessárias.

2. **KMS (Key Management Service):**
   - **O que é:** Gerenciamento de chaves de criptografia para proteger dados em repouso e em trânsito.
   - **Casos de Uso:**
     - Criptografia de dados no S3, RDS, DynamoDB e Redshift.
     - Uso de chaves gerenciadas pela AWS ou chaves personalizadas (CMKs).

3. **Cifragem:**
   - **Tipos:**
     - **Cifragem em Repouso:** Protege dados armazenados (ex.: S3, RDS, DynamoDB).
     - **Cifragem em Trânsito:** Protege dados durante a transferência (ex.: SSL/TLS).
   - **Ferramentas:**
     - AWS KMS, SSL/TLS, AWS Certificate Manager.

4. **VPC (Virtual Private Cloud):**
   - **O que é:** Isolamento de recursos em uma rede privada.
   - **Casos de Uso:**
     - Execução de bancos de dados RDS ou Redshift em uma VPC.
     - Restrição de acesso à internet pública.

---

## **5. Tópicos que Podem Aparecer na Avaliação**
Aqui estão alguns tópicos específicos que podem ser cobrados no exame relacionados ao Domínio 2:

### **Escolha de Armazenamento**
- Escolher o serviço de armazenamento adequado com base em cenários (ex.: S3 para data lakes, DynamoDB para NoSQL).
- Diferenciar entre classes de armazenamento do S3 (Standard, Intelligent-Tiering, Glacier).

### **Gerenciamento do Ciclo de Vida**
- Configurar regras de ciclo de vida no S3 para transição e expiração de objetos.
- Entender o uso do Amazon Glacier para arquivamento de longo prazo.

### **Particionamento e Indexação**
- Implementar estratégias de particionamento no S3, Redshift e DynamoDB.
- Criar índices em RDS e DynamoDB para otimizar consultas.

### **Segurança dos Dados**
- Configurar políticas do IAM para controle de acesso.
- Habilitar criptografia usando KMS.
- Isolar recursos em uma VPC.

---

## **6. Exemplos de Perguntas do Exame**
1. **Qual serviço da AWS é mais adequado para armazenar dados semi-estruturados com alta taxa de leitura/escrita?**
   - A) Amazon S3  
   - B) Amazon RDS  
   - C) Amazon DynamoDB  
   - D) Amazon Redshift  
   **Resposta:** C) Amazon DynamoDB.

2. **Qual estratégia de particionamento é recomendada para melhorar o desempenho de consultas no Amazon S3?**
   - A) Particionamento por data.  
   - B) Armazenamento em um único arquivo grande.  
   - C) Desabilitar a compressão de dados.  
   - D) Usar apenas a classe S3 Standard.  
   **Resposta:** A) Particionamento por data.

3. **Qual prática é recomendada para garantir a segurança dos dados no Amazon S3?**
   - A) Desabilitar a criptografia para reduzir a sobrecarga de processamento.  
   - B) Usar políticas do IAM para restringir o acesso.  
   - C) Armazenar todos os dados publicamente acessíveis.  
   - D) Ignorar a configuração de VPC.  
   **Resposta:** B) Usar políticas do IAM para restringir o acesso.

---

## **7. Melhores Práticas para o Domínio 2**
- **Escolha o Serviço Certo:** Use S3 para objetos, RDS para relacionais, DynamoDB para NoSQL e Redshift para análise.
- **Otimize Custos:** Use regras de ciclo de vida no S3 e classes de armazenamento adequadas.
- **Melhore o Desempenho:** Implemente particionamento e indexação para consultas eficientes.
- **Proteja os Dados:** Use IAM, KMS e VPC para garantir a segurança.
