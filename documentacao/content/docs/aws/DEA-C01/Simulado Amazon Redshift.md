---
title: "Simulado: Amazon Redshift"
---

### **Simulado: Amazon Redshift**

#### **1. Qual das seguintes opções é verdadeira sobre o armazenamento colunar no Amazon Redshift?**
A) Ele é mais eficiente para operações OLTP (Online Transaction Processing).  
B) Ele melhora o desempenho de consultas analíticas ao reduzir a quantidade de dados lidos.  
C) Ele não suporta compressão de dados.  
D) Ele armazena dados em linhas, semelhante a bancos de dados relacionais tradicionais.  

**Resposta:** B) Ele melhora o desempenho de consultas analíticas ao reduzir a quantidade de dados lidos.  
**Explicação:** O armazenamento colunar é otimizado para consultas analíticas, pois permite ler apenas as colunas relevantes, reduzindo a E/S de dados.

---

#### **2. Você está projetando um esquema de distribuição para uma tabela de fatos grande no Amazon Redshift. Qual estilo de distribuição é mais adequado para garantir que dados relacionados sejam armazenados no mesmo nó?**
A) EVEN  
B) KEY  
C) ALL  
D) INTERLEAVED  

**Resposta:** B) KEY  
**Explicação:** A distribuição KEY garante que dados relacionados (com base em uma coluna específica) sejam armazenados no mesmo nó, melhorando o desempenho de junções.

---

#### **3. Qual das seguintes opções é uma vantagem do uso de Materialized Views no Amazon Redshift?**
A) Elas são atualizadas automaticamente sempre que os dados subjacentes mudam.  
B) Elas melhoram o desempenho de consultas repetitivas ao armazenar resultados pré-computados.  
C) Elas não ocupam espaço de armazenamento no cluster.  
D) Elas só podem ser usadas com dados armazenados no Amazon S3.  

**Resposta:** B) Elas melhoram o desempenho de consultas repetitivas ao armazenar resultados pré-computados.  
**Explicação:** Materialized Views armazenam resultados de consultas complexas, reduzindo o tempo de execução para consultas subsequentes.

---

#### **4. Qual recurso do Amazon Redshift permite consultar dados diretamente no Amazon S3 sem carregá-los no cluster?**
A) Concurrency Scaling  
B) Redshift Spectrum  
C) Materialized Views  
D) RA3 Nodes  

**Resposta:** B) Redshift Spectrum  
**Explicação:** O Redshift Spectrum permite consultar dados diretamente no S3, integrando-se ao data lake sem a necessidade de carregar dados no cluster.

---

#### **5. Qual das seguintes opções é verdadeira sobre o Concurrency Scaling no Amazon Redshift?**
A) Ele aumenta o custo de armazenamento no cluster.  
B) Ele escala automaticamente a capacidade de processamento para lidar com picos de carga.  
C) Ele só pode ser usado com clusters do tipo Dense Storage (DS).  
D) Ele não suporta consultas SQL.  

**Resposta:** B) Ele escala automaticamente a capacidade de processamento para lidar com picos de carga.  
**Explicação:** O Concurrency Scaling adiciona capacidade de processamento temporária para lidar com consultas simultâneas, mantendo o desempenho.

---

#### **6. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon Redshift?**
A) Usar Distribution Keys aleatórias.  
B) Desabilitar a compressão de dados.  
C) Escolher Sort Keys com base nos padrões de consulta.  
D) Armazenar todos os dados no Leader Node.  

**Resposta:** C) Escolher Sort Keys com base nos padrões de consulta.  
**Explicação:** Sort Keys ordenam os dados fisicamente, melhorando o desempenho de consultas que filtram ou ordenam por essas colunas.

---

#### **7. Qual das seguintes opções é verdadeira sobre os nós RA3 no Amazon Redshift?**
A) Eles não suportam a separação de armazenamento e computação.  
B) Eles permitem escalar armazenamento e computação de forma independente.  
C) Eles são mais caros que os nós Dense Storage (DS).  
D) Eles não suportam o uso do Redshift Spectrum.  

**Resposta:** B) Eles permitem escalar armazenamento e computação de forma independente.  
**Explicação:** Os nós RA3 separam armazenamento e computação, permitindo escalabilidade independente e redução de custos.

---

#### **8. Qual das seguintes opções é uma limitação do Redshift Spectrum?**
A) Ele não suporta consultas SQL.  
B) Ele só pode ser usado com dados armazenados no Amazon Redshift.  
C) Ele pode aumentar os custos de consulta ao acessar grandes volumes de dados no S3.  
D) Ele não se integra ao AWS Glue Data Catalog.  

**Resposta:** C) Ele pode aumentar os custos de consulta ao acessar grandes volumes de dados no S3.  
**Explicação:** O Redshift Spectrum cobra com base na quantidade de dados escaneados no S3, o que pode aumentar os custos para grandes volumes.

---

#### **9. Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon Redshift?**
A) Manter o cluster em execução 24/7, mesmo quando não estiver em uso.  
B) Usar o Redshift Spectrum para consultar dados diretamente no S3.  
C) Desabilitar a cifragem de dados para reduzir a sobrecarga de processamento.  
D) Armazenar todos os dados no Leader Node.  

**Resposta:** B) Usar o Redshift Spectrum para consultar dados diretamente no S3.  
**Explicação:** O Redshift Spectrum permite consultar dados no S3 sem carregá-los no cluster, reduzindo custos de armazenamento.

---

#### **10. Qual das seguintes opções é verdadeira sobre a segurança no Amazon Redshift?**
A) Ele não suporta a cifragem de dados em repouso.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução de consultas em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O Amazon Redshift integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

### **Resumo das Respostas**
1. B) Ele melhora o desempenho de consultas analíticas ao reduzir a quantidade de dados lidos.  
2. B) KEY  
3. B) Elas melhoram o desempenho de consultas repetitivas ao armazenar resultados pré-computados.  
4. B) Redshift Spectrum  
5. B) Ele escala automaticamente a capacidade de processamento para lidar com picos de carga.  
6. C) Escolher Sort Keys com base nos padrões de consulta.  
7. B) Eles permitem escalar armazenamento e computação de forma independente.  
8. C) Ele pode aumentar os custos de consulta ao acessar grandes volumes de dados no S3.  
9. B) Usar o Redshift Spectrum para consultar dados diretamente no S3.  
10. B) Ele usa IAM para controlar o acesso a recursos e dados.  

---
