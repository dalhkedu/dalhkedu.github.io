---
title: "Simulado: Amazon Athena"
---

### **Simulado: Amazon Athena**

#### **1. Qual das seguintes opções é verdadeira sobre o Amazon Athena?**
A) Ele requer o provisionamento de servidores para executar consultas.  
B) Ele permite consultar dados diretamente no Amazon S3 usando SQL.  
C) Ele não suporta a consulta de dados em formatos como Parquet ou ORC.  
D) Ele só pode ser usado com dados armazenados no Amazon Redshift.  

---

#### **2. Qual formato de dados é recomendado para melhorar o desempenho e reduzir custos no Amazon Athena?**
A) CSV  
B) JSON  
C) Parquet  
D) TXT  

---

#### **3. Qual serviço da AWS pode ser usado para catalogar metadados no Amazon Athena?**
A) Amazon S3  
B) AWS Glue  
C) Amazon Redshift  
D) Amazon QuickSight  

---

#### **4. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de consultas no Amazon Athena?**
A) Usar particionamento para reduzir a quantidade de dados escaneados.  
B) Armazenar todos os dados em um único arquivo grande.  
C) Desabilitar a compressão de dados.  
D) Usar formatos de dados não estruturados.  

---

#### **5. Qual das seguintes opções é verdadeira sobre a segurança no Amazon Athena?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS). 

---

#### **6. Qual das seguintes opções é uma limitação do Amazon Athena?**
A) Ele não suporta a consulta de dados no Amazon S3.  
B) Ele tem um tempo de execução máximo de 15 minutos por consulta.  
C) Ele não suporta a integração com o AWS Glue.  
D) Ele não suporta a consulta de dados em formatos colunares.  

---

#### **7. Qual serviço da AWS pode ser usado para visualizar dados consultados no Amazon Athena?**
A) Amazon S3  
B) AWS Glue  
C) Amazon Redshift  
D) Amazon QuickSight  

---

#### **8. Qual das seguintes opções é uma vantagem do uso do Amazon Athena com o AWS Glue?**
A) Ele permite a catalogação automática de metadados.  
B) Ele aumenta o custo de consultas no Athena.  
C) Ele não suporta a consulta de dados no S3.  
D) Ele não se integra ao Amazon QuickSight.  

---

#### **9. Qual das seguintes opções é uma prática recomendada para reduzir custos no Amazon Athena?**
A) Usar formatos de dados não comprimidos.  
B) Executar consultas complexas que escaneiam grandes volumes de dados.  
C) Usar formatos colunares e compressão para reduzir a quantidade de dados escaneados.  
D) Armazenar todos os dados em um único arquivo grande.  

---

#### **10. Qual das seguintes opções é verdadeira sobre a execução do Amazon Athena em uma VPC?**
A) Ele não suporta a execução em VPCs.  
B) Ele requer a configuração manual de sub-redes e grupos de segurança.  
C) Ele não se integra ao IAM.  
D) Ele não suporta a cifragem de dados.  

---

**Resposta:** B) Ele permite consultar dados diretamente no Amazon S3 usando SQL.  
**Explicação:** O Amazon Athena permite consultar dados diretamente no S3 usando SQL padrão, sem a necessidade de provisionar servidores.

---

**Resposta:** C) Parquet  
**Explicação:** Formatos colunares como Parquet e ORC são recomendados para melhorar o desempenho e reduzir custos, pois reduzem a quantidade de dados escaneados.

---

**Resposta:** B) AWS Glue  
**Explicação:** O AWS Glue Data Catalog pode ser usado para gerenciar metadados no Amazon Athena, facilitando a descoberta e organização de dados.

---

**Resposta:** A) Usar particionamento para reduzir a quantidade de dados escaneados.  
**Explicação:** O particionamento permite que o Athena escaneie apenas os dados relevantes, melhorando o desempenho e reduzindo custos.

---

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O Amazon Athena integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

**Resposta:** B) Ele tem um tempo de execução máximo de 15 minutos por consulta.  
**Explicação:** O Amazon Athena tem um tempo de execução máximo de 15 minutos por consulta, o que pode ser uma limitação para consultas complexas.

---

**Resposta:** D) Amazon QuickSight  
**Explicação:** O Amazon QuickSight pode ser usado para visualizar dados consultados no Amazon Athena, criando dashboards e relatórios interativos.

---

**Resposta:** A) Ele permite a catalogação automática de metadados.  
**Explicação:** A integração com o AWS Glue permite a catalogação automática de metadados, facilitando a descoberta e organização de dados.

---

**Resposta:** C) Usar formatos colunares e compressão para reduzir a quantidade de dados escaneados.  
**Explicação:** Usar formatos colunares e compressão reduz a quantidade de dados escaneados, otimizando custos e desempenho.

---

**Resposta:** B) Ele requer a configuração manual de sub-redes e grupos de segurança.  
**Explicação:** A execução do Amazon Athena em uma VPC requer a configuração manual de sub-redes e grupos de segurança para garantir o isolamento de rede.

---

### **Resumo das Respostas**
1. B) Ele permite consultar dados diretamente no Amazon S3 usando SQL.  
2. C) Parquet  
3. B) AWS Glue  
4. A) Usar particionamento para reduzir a quantidade de dados escaneados.  
5. B) Ele usa IAM para controlar o acesso a recursos e dados.  
6. B) Ele tem um tempo de execução máximo de 15 minutos por consulta.  
7. D) Amazon QuickSight  
8. A) Ele permite a catalogação automática de metadados.  
9. C) Usar formatos colunares e compressão para reduzir a quantidade de dados escaneados.  
10. B) Ele requer a configuração manual de sub-redes e grupos de segurança.  

---
