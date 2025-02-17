---
title: "Simulado de Big Data"
---

## **Simulado de Big Data**

### **1. Teoria e Conceitos**
1. **Qual dos seguintes NÃO é um dos 5 Vs do Big Data?**
   - a) Volume
   - b) Velocidade
   - c) Veracidade
   - d) Virtualização

2. **Qual é a principal diferença entre dados estruturados e não estruturados?**
   - a) Dados estruturados são sempre armazenados em bancos de dados relacionais, enquanto dados não estruturados não podem ser armazenados.
   - b) Dados estruturados têm um formato definido, enquanto dados não estruturados não têm um formato específico.
   - c) Dados estruturados são gerados apenas por humanos, enquanto dados não estruturados são gerados por máquinas.
   - d) Dados estruturados são sempre menores em volume que dados não estruturados.

3. **Qual das seguintes afirmações sobre ETL e ELT está correta?**
   - a) ETL é mais adequado para cenários onde a transformação ocorre após o carregamento.
   - b) ELT é mais eficiente para grandes volumes de dados, pois a transformação ocorre no destino.
   - c) ETL é sempre mais rápido que ELT.
   - d) ELT não é compatível com Data Warehouses.

---

### **2. Ferramentas e Tecnologias**
4. **Qual componente do Hadoop é responsável pelo armazenamento distribuído de dados?**
   - a) MapReduce
   - b) YARN
   - c) HDFS
   - d) Spark

5. **Qual é a principal vantagem do Apache Spark em relação ao Hadoop MapReduce?**
   - a) Spark é mais adequado para processamento em lote.
   - b) Spark processa dados em memória, o que o torna mais rápido.
   - c) Spark não suporta processamento em tempo real.
   - d) Spark é mais complexo de configurar que o Hadoop.

6. **Qual formato de arquivo é otimizado para consultas rápidas em grandes volumes de dados?**
   - a) CSV
   - b) JSON
   - c) Parquet
   - d) XML

---

### **3. Aplicações Práticas**
7. **Qual das seguintes aplicações é um exemplo de uso de Big Data na área de saúde?**
   - a) Detecção de fraudes em transações financeiras.
   - b) Previsão de surtos de doenças com base em dados históricos.
   - c) Personalização de campanhas de marketing.
   - d) Monitoramento de tráfego em tempo real.

8. **Qual ferramenta é comumente usada para processamento de dados em tempo real (stream processing)?**
   - a) Hadoop MapReduce
   - b) Apache Kafka
   - c) Apache Hive
   - d) Apache Pig

9. **Qual é o principal benefício de um Data Lake em comparação com um Data Warehouse?**
   - a) Armazena apenas dados estruturados.
   - b) Permite armazenar dados brutos em seu formato original.
   - c) É mais rápido para consultas SQL.
   - d) Não requer infraestrutura de nuvem.

---

### **4. Análise e Resolução de Problemas**
10. **Qual das seguintes métricas NÃO é usada para avaliar a qualidade de dados?**
    - a) Precisão
    - b) Completude
    - c) Velocidade
    - d) Consistência

11. **Qual é o principal desafio ao migrar uma infraestrutura de Big Data para a nuvem?**
    - a) Aumento do custo de armazenamento.
    - b) Dificuldade em garantir a segurança e privacidade dos dados.
    - c) Incompatibilidade com ferramentas de Big Data.
    - d) Limitação na capacidade de processamento.

12. **Qual das seguintes ferramentas é usada para orquestração de pipelines de dados?**
    - a) Apache Kafka
    - b) Apache Airflow
    - c) Apache Spark
    - d) Apache HBase

---

### **5. Casos de Uso e Cenários**
13. **Qual é o principal benefício do uso de Big Data no marketing digital?**
    - a) Redução do custo de infraestrutura.
    - b) Personalização de campanhas com base no comportamento do consumidor.
    - c) Aumento da velocidade de processamento de dados.
    - d) Eliminação da necessidade de Data Warehouses.

14. **Qual é o papel do Big Data na Internet das Coisas (IoT)?**
    - a) Reduzir o volume de dados gerados por dispositivos IoT.
    - b) Processar e analisar grandes volumes de dados gerados por dispositivos IoT.
    - c) Substituir dispositivos IoT por soluções baseadas em nuvem.
    - d) Limitar o uso de dados não estruturados.

15. **Qual das seguintes práticas ajuda a mitigar riscos de privacidade em projetos de Big Data?**
    - a) Armazenar todos os dados em formato não criptografado.
    - b) Implementar políticas de governança de dados e criptografia.
    - c) Ignorar regulamentações como GDPR e LGPD.
    - d) Limitar o uso de dados estruturados.

---

## **Respostas e Explicações**

1. **d) Virtualização**  
   - Os 5 Vs do Big Data são Volume, Velocidade, Variedade, Veracidade e Valor. Virtualização não faz parte deles.

2. **b) Dados estruturados têm um formato definido, enquanto dados não estruturados não têm um formato específico.**  
   - Dados estruturados são organizados (ex: tabelas), enquanto dados não estruturados não seguem um formato rígido (ex: vídeos, textos).

3. **b) ELT é mais eficiente para grandes volumes de dados, pois a transformação ocorre no destino.**  
   - ELT é mais escalável e eficiente para grandes volumes, pois a transformação é feita no destino (ex: Data Warehouse).

4. **c) HDFS**  
   - O HDFS (Hadoop Distributed File System) é responsável pelo armazenamento distribuído de dados no Hadoop.

5. **b) Spark processa dados em memória, o que o torna mais rápido.**  
   - O Spark é mais rápido que o MapReduce porque processa dados em memória, em vez de depender de operações em disco.

6. **c) Parquet**  
   - O formato Parquet é otimizado para consultas rápidas e eficientes em grandes volumes de dados.

7. **b) Previsão de surtos de doenças com base em dados históricos.**  
   - Big Data é usado na saúde para prever surtos, melhorar diagnósticos e personalizar tratamentos.

8. **b) Apache Kafka**  
   - O Apache Kafka é uma ferramenta popular para processamento de dados em tempo real (stream processing).

9. **b) Permite armazenar dados brutos em seu formato original.**  
   - Um Data Lake armazena dados brutos em seu formato original, enquanto um Data Warehouse armazena dados processados.

10. **c) Velocidade**  
    - Velocidade não é uma métrica de qualidade de dados. As métricas comuns são precisão, completude e consistência.

11. **b) Dificuldade em garantir a segurança e privacidade dos dados.**  
    - A segurança e privacidade dos dados são os principais desafios ao migrar para a nuvem.

12. **b) Apache Airflow**  
    - O Apache Airflow é uma ferramenta de orquestração de pipelines de dados.

13. **b) Personalização de campanhas com base no comportamento do consumidor.**  
    - Big Data permite segmentar o público e personalizar campanhas de marketing.

14. **b) Processar e analisar grandes volumes de dados gerados por dispositivos IoT.**  
    - Big Data é usado para processar e analisar os dados gerados por dispositivos IoT.

15. **b) Implementar políticas de governança de dados e criptografia.**  
    - Políticas de governança e criptografia ajudam a mitigar riscos de privacidade.
