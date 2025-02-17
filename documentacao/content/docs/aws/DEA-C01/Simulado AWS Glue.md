---
title: "Simulado: AWS Glue"
---

### **Simulado: AWS Glue**

#### **1. Qual das seguintes opções é verdadeira sobre os crawlers do AWS Glue?**
A) Eles só podem ser usados com dados armazenados no Amazon S3.  
B) Eles criam tabelas no Data Catalog automaticamente com base nos dados descobertos.  
C) Eles exigem que o usuário defina manualmente o esquema dos dados.  
D) Eles não suportam a descoberta de dados em bancos de dados relacionais.  

**Resposta:** B) Eles criam tabelas no Data Catalog automaticamente com base nos dados descobertos.  
**Explicação:** Os crawlers automatizam a descoberta de esquemas e a criação de tabelas no Data Catalog, suportando várias fontes de dados, incluindo S3, RDS e DynamoDB.

---

#### **2. Você está configurando um job do AWS Glue para processar dados em um bucket S3. Qual das seguintes opções é a melhor prática para garantir que apenas novos dados sejam processados em execuções subsequentes?**
A) Usar Dynamic Frames.  
B) Habilitar Job Bookmarks.  
C) Configurar um workflow no AWS Glue Studio.  
D) Usar um crawler para atualizar o Data Catalog.  

**Resposta:** B) Habilitar Job Bookmarks.  
**Explicação:** Job Bookmarks rastreiam os dados já processados, evitando reprocessamento em execuções subsequentes.

---

#### **3. Qual das seguintes opções é uma vantagem do uso de Dynamic Frames no AWS Glue em comparação com DataFrames do Spark?**
A) Dynamic Frames são mais rápidos para processamento de grandes volumes de dados.  
B) Dynamic Frames podem inferir esquemas automaticamente e lidar com dados semi-estruturados.  
C) Dynamic Frames suportam apenas Python, enquanto DataFrames suportam Scala e Java.  
D) Dynamic Frames são mais adequados para consultas SQL.  

**Resposta:** B) Dynamic Frames podem inferir esquemas automaticamente e lidar com dados semi-estruturados.  
**Explicação:** Dynamic Frames são flexíveis e tolerantes a erros, ideais para dados com esquemas desconhecidos ou dinâmicos.

---

#### **4. Você precisa orquestrar múltiplos jobs e crawlers do AWS Glue em uma sequência específica. Qual recurso você deve usar?**
A) AWS Step Functions  
B) AWS Glue Workflows  
C) Amazon EventBridge  
D) AWS Lambda  

**Resposta:** B) AWS Glue Workflows  
**Explicação:** AWS Glue Workflows permite orquestrar jobs e crawlers em uma sequência definida, automatizando pipelines complexos de ETL.

---

#### **5. Qual das seguintes opções é verdadeira sobre o AWS Glue DataBrew?**
A) Ele é usado para criar e gerenciar clusters do Amazon EMR.  
B) Ele fornece uma interface visual para limpeza e transformação de dados.  
C) Ele só suporta dados armazenados no Amazon Redshift.  
D) Ele não se integra ao AWS Glue Data Catalog.  

**Resposta:** B) Ele fornece uma interface visual para limpeza e transformação de dados.  
**Explicação:** O AWS Glue DataBrew é uma ferramenta visual que facilita a preparação de dados para usuários não técnicos, integrando-se ao Data Catalog.

---

#### **6. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de jobs do AWS Glue?**
A) Usar Python Shell jobs para processamento de grandes volumes de dados.  
B) Particionar dados no S3 e usar a opção de particionamento no AWS Glue.  
C) Executar todos os jobs em um único worker para reduzir custos.  
D) Desabilitar Job Bookmarks para evitar sobrecarga.  

**Resposta:** B) Particionar dados no S3 e usar a opção de particionamento no AWS Glue.  
**Explicação:** Particionar dados melhora o desempenho ao permitir que o AWS Glue processe apenas os dados relevantes, reduzindo o tempo de execução.

---

#### **7. Qual serviço da AWS pode ser usado para monitorar a execução de jobs e crawlers do AWS Glue?**
A) Amazon CloudWatch  
B) AWS X-Ray  
C) AWS Config  
D) AWS Trusted Advisor  

**Resposta:** A) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar a execução de jobs e crawlers do AWS Glue.

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no AWS Glue?**
A) O AWS Glue não suporta a cifragem de dados em repouso.  
B) O AWS Glue usa IAM para controlar o acesso a recursos e dados.  
C) O AWS Glue não se integra ao AWS Key Management Service (KMS).  
D) O AWS Glue não permite a execução de jobs em VPCs.  

**Resposta:** B) O AWS Glue usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O AWS Glue integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

#### **9. Qual das seguintes opções é uma limitação dos Python Shell jobs no AWS Glue?**
A) Eles não suportam a transformação de dados.  
B) Eles só podem ser usados com dados armazenados no Amazon S3.  
C) Eles não suportam processamento distribuído.  
D) Eles não se integram ao AWS Glue Data Catalog.  

**Resposta:** C) Eles não suportam processamento distribuído.  
**Explicação:** Python Shell jobs são adequados para tarefas simples e não distribuídas, ao contrário dos Spark jobs, que suportam processamento distribuído.

---

#### **10. Qual das seguintes opções é verdadeira sobre a integração do AWS Glue com o Amazon Athena?**
A) O AWS Glue não pode catalogar dados para uso no Amazon Athena.  
B) O Amazon Athena pode consultar tabelas catalogadas no AWS Glue Data Catalog.  
C) O AWS Glue só suporta a integração com o Amazon Redshift.  
D) O Amazon Athena não suporta a consulta de dados no Amazon S3.  

**Resposta:** B) O Amazon Athena pode consultar tabelas catalogadas no AWS Glue Data Catalog.  
**Explicação:** O Amazon Athena usa o AWS Glue Data Catalog para consultar dados armazenados no S3 e outras fontes.

---

### **Resumo das Respostas**
1. B) Eles criam tabelas no Data Catalog automaticamente com base nos dados descobertos.  
2. B) Habilitar Job Bookmarks.  
3. B) Dynamic Frames podem inferir esquemas automaticamente e lidar com dados semi-estruturados.  
4. B) AWS Glue Workflows  
5. B) Ele fornece uma interface visual para limpeza e transformação de dados.  
6. B) Particionar dados no S3 e usar a opção de particionamento no AWS Glue.  
7. A) Amazon CloudWatch  
8. B) O AWS Glue usa IAM para controlar o acesso a recursos e dados.  
9. C) Eles não suportam processamento distribuído.  
10. B) O Amazon Athena pode consultar tabelas catalogadas no AWS Glue Data Catalog.  

---