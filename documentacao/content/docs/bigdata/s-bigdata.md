---
title: "Simulado de Big Data"
---

## **Simulado de Big Data**

### **1. Teoria e Conceitos**
1. **O que são os 5 Vs do Big Data e como eles impactam o processamento e análise de dados?**
2. **Explique a diferença entre dados estruturados, semiestruturados e não estruturados. Dê exemplos de cada tipo.**
3. **Qual é a diferença entre ETL e ELT? Em quais cenários cada abordagem é mais adequada?**
4. **O que é a camada "Source of Truth" (SOT) em um pipeline de dados? Por que ela é importante?**
5. **Quais são os principais desafios relacionados à qualidade de dados em projetos de Big Data?**

---

### **2. Ferramentas e Tecnologias**
6. **Descreva a arquitetura do Hadoop e explique o papel de cada um de seus principais componentes (HDFS, MapReduce, YARN).**
7. **Qual é a principal vantagem do Apache Spark em relação ao Hadoop MapReduce? Dê um exemplo de uso prático do Spark.**
8. **O que é um Data Lake e como ele se diferencia de um Data Warehouse?**
9. **Explique o conceito de "stream processing" e cite duas ferramentas utilizadas para esse fim.**
10. **Quais são os formatos de arquivo mais comuns em Big Data (ex: Parquet, Avro, ORC) e quais são suas vantagens?**

---

### **3. Aplicações Práticas**
11. **Como o Big Data pode ser aplicado na área de saúde para melhorar diagnósticos e tratamentos?**
12. **Descreva um caso de uso real onde o processamento em tempo real (stream processing) é essencial.**
13. **Qual é o papel do Big Data no marketing digital? Como ele pode ser usado para personalizar campanhas?**
14. **Explique como o Big Data e a IoT (Internet das Coisas) estão interligados. Dê um exemplo prático.**
15. **Quais são os riscos associados ao uso de Big Data em termos de privacidade e segurança? Como mitigá-los?**

---

### **4. Análise e Resolução de Problemas**
16. **Você está projetando um pipeline de dados para uma empresa de e-commerce. Quais ferramentas e estratégias você usaria para garantir a qualidade dos dados?**
17. **Uma empresa está enfrentando lentidão no processamento de grandes volumes de dados. Quais soluções você recomendaria para melhorar o desempenho?**
18. **Explique como a arquitetura Medallion (Bronze, Silver, Gold) pode ser aplicada em um projeto de Big Data.**
19. **Quais métricas de qualidade de dados você monitoraria em um pipeline de dados e por quê?**
20. **Como você justificaria a migração de uma infraestrutura on-premises para a nuvem em um projeto de Big Data?**

---

## **Respostas e Explicações**

### **1. Teoria e Conceitos**
1. **5 Vs do Big Data**:
   - **Volume**: Quantidade massiva de dados.
   - **Velocidade**: Rapidez com que os dados são gerados e processados.
   - **Variedade**: Diferentes tipos de dados (estruturados, semiestruturados, não estruturados).
   - **Veracidade**: Confiabilidade e qualidade dos dados.
   - **Valor**: Capacidade de extrair insights úteis.
   - **Impacto**: Esses aspectos exigem ferramentas e técnicas específicas para armazenamento, processamento e análise.

2. **Tipos de Dados**:
   - **Estruturados**: Dados organizados em tabelas (ex: bancos de dados SQL).
   - **Semiestruturados**: Dados com alguma estrutura, mas não rígida (ex: JSON, XML).
   - **Não estruturados**: Dados sem formato definido (ex: vídeos, imagens, textos).

3. **ETL vs ELT**:
   - **ETL**: Dados são transformados antes de serem carregados no destino. Ideal para cenários com transformações complexas.
   - **ELT**: Dados são carregados primeiro e transformados no destino. Mais escalável e rápido para grandes volumes.

4. **Source of Truth (SOT)**:
   - É a camada onde os dados são consolidados e validados, servindo como referência confiável para análises. Importante para garantir consistência e precisão.

5. **Desafios de Qualidade de Dados**:
   - Precisão, completude, consistência, duplicidade e validade. Dados de baixa qualidade podem levar a decisões erradas.

---

### **2. Ferramentas e Tecnologias**
6. **Arquitetura do Hadoop**:
   - **HDFS**: Armazenamento distribuído.
   - **MapReduce**: Processamento paralelo.
   - **YARN**: Gerenciamento de recursos.

7. **Vantagem do Spark**:
   - Processamento em memória, o que o torna mais rápido que o MapReduce. Exemplo: Análise de logs em tempo real.

8. **Data Lake vs Data Warehouse**:
   - **Data Lake**: Armazena dados brutos em seu formato original.
   - **Data Warehouse**: Armazena dados processados e estruturados.

9. **Stream Processing**:
   - Processamento contínuo de dados em tempo real. Ferramentas: Apache Kafka, Apache Flink.

10. **Formatos de Arquivo**:
    - **Parquet**: Eficiente para consultas.
    - **Avro**: Ideal para serialização.
    - **ORC**: Boa compressão.

---

### **3. Aplicações Práticas**
11. **Saúde**:
    - Previsão de surtos, personalização de tratamentos, análise de imagens médicas.

12. **Stream Processing**:
    - Detecção de fraudes em transações financeiras.

13. **Marketing Digital**:
    - Segmentação de público, análise de sentimentos em redes sociais.

14. **Big Data e IoT**:
    - Sensores IoT geram grandes volumes de dados, que são processados para monitoramento e análise.

15. **Riscos de Privacidade e Segurança**:
    - Vazamento de dados, uso indevido. Mitigação: Criptografia, governança de dados.

---

### **4. Análise e Resolução de Problemas**
16. **Pipeline de Dados**:
    - Ferramentas: Apache Airflow, Apache NiFi. Estratégias: Validação de dados, monitoramento de qualidade.

17. **Melhoria de Desempenho**:
    - Uso de Spark, particionamento de dados, migração para a nuvem.

18. **Arquitetura Medallion**:
    - **Bronze**: Dados brutos.
    - **Silver**: Dados limpos e integrados.
    - **Gold**: Dados prontos para análise.

19. **Métricas de Qualidade**:
    - Precisão, completude, consistência. Importantes para garantir confiabilidade.

20. **Migração para a Nuvem**:
    - Justificativa: Escalabilidade, redução de custos, flexibilidade.
