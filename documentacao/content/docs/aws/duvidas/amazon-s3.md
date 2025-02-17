---
title: "Amazon S3"
---

### **1. Visão Geral do Amazon S3**
- **O que é:** Serviço de armazenamento de objetos escalável, durável e altamente disponível.
- **Casos de Uso Comuns:**
  - Data lakes e big data analytics.
  - Backup e recuperação de desastres.
  - Armazenamento de arquivos estáticos para websites.
  - Repositório para pipelines de ETL.

---

### **2. Conceitos Fundamentais**
#### **Buckets**
- **Definição:** Contêineres lógicos para armazenar objetos.
- **Regiões:** Buckets são criados em uma região específica da AWS.
- **Nomes:** Devem ser globalmente únicos e seguir convenções de nomenclatura.

#### **Objetos**
- **Definição:** Arquivos armazenados em buckets.
- **Estrutura:** Compostos por dados (o arquivo em si) e metadados (informações sobre o arquivo).
- **Chave:** Identificador único do objeto dentro de um bucket (semelhante a um caminho de arquivo).

#### **Classes de Armazenamento**
- **S3 Standard:** Para acesso frequente.
- **S3 Intelligent-Tiering:** Otimiza custos automaticamente com base no padrão de acesso.
- **S3 Standard-IA (Infrequent Access):** Para dados acessados com menos frequência.
- **S3 One Zone-IA:** Armazenamento em uma única zona de disponibilidade, com custo reduzido.
- **S3 Glacier:** Para arquivamento de longo prazo (acesso em minutos a horas).
- **S3 Glacier Deep Archive:** Para arquivamento raramente acessado (acesso em horas).

---

### **3. Recursos e Funcionalidades**
#### **Gerenciamento do Ciclo de Vida**
- **O que é:** Regras para automatizar a transição de objetos entre classes de armazenamento ou excluí-los após um período.
- **Casos de Uso:** Reduzir custos movendo dados para classes de armazenamento mais econômicas ou excluindo dados desnecessários.

#### **Versionamento**
- **O que é:** Mantém múltiplas versões de um objeto no mesmo bucket.
- **Benefícios:** Recuperação de dados após exclusões acidentais ou sobrescritas.

#### **Cifragem**
- **Tipos:**
  - **SSE-S3:** Cifragem gerenciada pela AWS usando chaves da S3.
  - **SSE-KMS:** Cifragem usando AWS Key Management Service (KMS).
  - **SSE-C:** Cifragem usando chaves fornecidas pelo cliente.
  - **Cifragem no Cliente:** Dados cifrados antes de serem enviados para o S3.
- **Importância:** Garante a segurança dos dados em repouso.

#### **ACLs e Políticas de Bucket**
- **ACLs (Access Control Lists):** Controle de acesso básico em nível de objeto ou bucket.
- **Políticas de Bucket:** Permissões granulares usando políticas baseadas em JSON.
- **IAM:** Integração com AWS Identity and Access Management para controle de acesso.

#### **Transferência de Dados**
- **Multipart Upload:** Para uploads de grandes arquivos de forma eficiente.
- **Transfer Acceleration:** Acelera transferências usando a rede global da AWS (CloudFront).

#### **Eventos do S3**
- **O que é:** Notificações em tempo real quando objetos são criados, excluídos ou modificados.
- **Integrações:** Pode acionar AWS Lambda, SQS, SNS ou Step Functions para automatizar workflows.

#### **S3 Select e Glacier Select**
- **O que é:** Recupera apenas partes específicas de objetos usando consultas SQL.
- **Benefícios:** Reduz custos e tempo de processamento ao trabalhar com grandes volumes de dados.

---

### **4. Melhores Práticas**
- **Organização de Dados:**
  - Use prefixos (pastas lógicas) para organizar objetos.
  - Estruture buckets para otimizar consultas (ex.: particionamento por data).
- **Segurança:**
  - Habilite a cifragem para todos os objetos.
  - Use políticas de bucket e IAM para restringir acesso.
  - Ative o versionamento para proteger contra exclusões acidentais.
- **Custos:**
  - Use classes de armazenamento adequadas para cada tipo de dado.
  - Configure regras de ciclo de vida para reduzir custos.
- **Desempenho:**
  - Use Multipart Upload para grandes arquivos.
  - Habilite Transfer Acceleration para transferências globais.

---

### **5. Integrações com Outros Serviços AWS**
- **AWS Glue:** Para ETL e catalogação de dados no S3.
- **Amazon Athena:** Para consultar dados diretamente no S3 usando SQL.
- **Amazon Redshift:** Para carregar dados do S3 em um data warehouse.
- **Amazon Kinesis:** Para ingestão de dados de streaming no S3.
- **AWS Lambda:** Para processar eventos do S3 em tempo real.
- **Amazon CloudFront:** Para distribuir conteúdo armazenado no S3 com baixa latência.

---

### **6. Tópicos Relevantes para o Exame**
- **Escolha de Classes de Armazenamento:** Saber quando usar cada classe de armazenamento com base no padrão de acesso e custo.
- **Segurança:** Entender cifragem, políticas de bucket e integração com IAM.
- **Ciclo de Vida:** Configurar regras de transição e expiração.
- **Integrações:** Como o S3 se integra a serviços como Glue, Athena, Redshift e Lambda.
- **Casos de Uso:** Data lakes, pipelines de ETL e armazenamento de logs.

---

### **7. Exemplos de Perguntas do Exame**
1. **Qual classe de armazenamento é mais adequada para dados acessados uma vez por mês?**
   - A) S3 Standard
   - B) S3 Intelligent-Tiering
   - C) S3 Glacier
   - D) S3 Standard-IA
   **Resposta:** D) S3 Standard-IA.

2. **Como garantir que dados no S3 sejam cifrados em repouso?**
   - A) Usar SSE-S3.
   - B) Habilitar o versionamento.
   - C) Configurar uma política de bucket.
   - D) Usar Transfer Acceleration.
   **Resposta:** A) Usar SSE-S3.

---

### **8. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie um bucket e configure regras de ciclo de vida.
  - Habilite versionamento e cifragem.
  - Integre o S3 com AWS Glue e Athena para consultar dados.
