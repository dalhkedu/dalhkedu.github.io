### **Simulado: Design High-Performing Architectures**  
**Instruções**: Escolha a melhor resposta com base nas práticas recomendadas da AWS. Justifique sua escolha.

---

#### **1. Uma aplicação OLTP (Online Transaction Processing) com alto volume de transações está enfrentando lentidão em consultas de leitura. Qual estratégia melhora o desempenho sem afetar a consistência dos dados?**  
a) Habilitar o RDS Multi-AZ.  
b) Adicionar Read Replicas do Amazon Aurora.  
c) Migrar para Amazon DynamoDB Global Tables.  
d) Usar Amazon ElastiCache for Memcached.  

**Resposta Correta**: **b**  
**Explicação**:  
- **Read Replicas do Aurora** permitem descarregar consultas de leitura, melhorando desempenho sem impactar a instância primária.  
- **Multi-AZ** (opção a) é para HA, não performance.  
- **DynamoDB** (opção c) é NoSQL e pode não ser compatível com esquemas relacionais existentes.  
- **Memcached** (opção d) é stateless e menos adequado para transações ACID.  

---

#### **2. Qual tipo de instância EC2 é mais adequado para uma carga de trabalho de processamento de dados com alto uso de CPU e custo otimizado?**  
a) C5  
b) R5  
c) M5  
d) T3  

**Resposta Correta**: **a**  
**Explicação**:  
- **C5** é otimizado para cargas de CPU intensivas.  
- **R5** (opção b) é para memória, **M5** (opção c) para uso geral, e **T3** (opção d) para cargas burstáveis.  

---

#### **3. Como reduzir a latência de consultas a um banco de dados RDS PostgreSQL frequentemente acessado pelo mesmo conjunto de dados?**  
a) Habilitar o RDS Proxy.  
b) Usar Amazon ElastiCache for Redis no padrão Cache-Aside.  
c) Migrar para Amazon Redshift.  
d) Habilitar o Auto Scaling do RDS.  

**Resposta Correta**: **b**  
**Explicação**:  
- **ElastiCache for Redis** (padrão Cache-Aside) armazena resultados de queries frequentes, reduzindo latência.  
- **RDS Proxy** (opção a) gerencia conexões, mas não cache.  
- **Redshift** (opção c) é para analytics, não OLTP.  
- **Auto Scaling do RDS** (opção d) não existe; escalabilidade vertical é manual.  

---

#### **4. Qual configuração melhora o desempenho de upload de arquivos de 20 GB para o Amazon S3 em uma região distante?**  
a) Usar S3 Intelligent-Tiering.  
b) Habilitar S3 Transfer Acceleration e Multi-Part Upload.  
c) Usar S3 Standard-IA para reduzir custos.  
d) Configurar uma política de lifecycle para arquivamento.  

**Resposta Correta**: **b**  
**Explicação**:  
- **Transfer Acceleration** usa CloudFront Edge Locations para uploads rápidos.  
- **Multi-Part Upload** divide arquivos grandes em partes paralelas.  
- **Intelligent-Tiering** (opção a) e **Standard-IA** (opção c) otimizam custo, não performance.  

---

#### **5. Uma função AWS Lambda crítica sofre com cold starts durante picos de tráfego. Como resolver?**  
a) Aumentar a memória alocada.  
b) Usar Provisioned Concurrency.  
c) Migrar para EC2 Spot Instances.  
d) Habilitar Lambda@Edge.  

**Resposta Correta**: **b**  
**Explicação**:  
- **Provisioned Concurrency** mantém instâncias "quentes" para evitar cold starts.  
- **Aumentar memória** (opção a) pode reduzir duração da execução, mas não cold starts.  
- **EC2** (opção c) não é serverless.  
- **Lambda@Edge** (opção d) é para processamento em borda, não performance geral.  

---

#### **6. Qual serviço AWS é mais eficiente para reduzir latência em uma aplicação global que serve conteúdo estático?**  
a) AWS Global Accelerator  
b) Amazon CloudFront  
c) Amazon Route 53  
d) AWS Direct Connect  

**Resposta Correta**: **b**  
**Explicação**:  
- **CloudFront** é uma CDN projetada para conteúdo estático/dinâmico com cache em Edge Locations.  
- **Global Accelerator** (opção a) é melhor para TCP/UDP com baixa latência (ex: APIs).  
- **Route 53** (opção c) é DNS, não otimiza latência diretamente.  

---

#### **7. Uma empresa precisa acelerar queries analíticas complexas em um data warehouse de 50 TB. Qual recurso do Amazon Redshift é mais adequado?**  
a) RA3 Nodes  
b) Materialized Views  
c) Elastic Resize  
d) Concurrency Scaling  

**Resposta Correta**: **b**  
**Explicação**:  
- **Materialized Views** pré-computam resultados de queries complexas.  
- **RA3 Nodes** (opção a) separam storage/compute, mas não otimizam queries.  
- **Concurrency Scaling** (opção d) lida com picos de usuários, não performance de queries.  

---

#### **8. Qual tipo de volume EBS oferece o maior throughput para workloads de Big Data?**  
a) gp3  
b) st1  
c) sc1  
d) io2 Block Express  

**Resposta Correta**: **b**  
**Explicação**:  
- **st1** (Throughput Optimized HDD) é projetado para Big Data (alta throughput, baixo custo).  
- **io2** (opção d) é para alta IOPS, não throughput.  
- **gp3** (opção a) é uso geral.  

---

#### **9. Como reduzir a carga em um banco de dados RDS MySQL durante picos de tráfego?**  
a) Habilitar o RDS Multi-AZ.  
b) Usar Amazon ElastiCache for Redis para cache de queries frequentes.  
c) Migrar para Aurora Serverless.  
d) Habilitar o RDS Read Replicas em outra região.  

**Resposta Correta**: **b**  
**Explicação**:  
- **ElastiCache** descarrega o banco de dados armazenando resultados de queries repetitivas.  
- **Multi-AZ** (opção a) é para HA, não performance.  
- **Aurora** (opção c) pode ajudar, mas exige migração.  

---

#### **10. Qual serviço AWS é ideal para reduzir a latência de uma aplicação global baseada em TCP com endpoints em múltiplas regiões?**  
a) Amazon CloudFront  
b) AWS Global Accelerator  
c) Amazon API Gateway  
d) AWS Transit Gateway  

**Resposta Correta**: **b**  
**Explicação**:  
- **Global Accelerator** usa IPs anycast e a rede backbone da AWS para rotear tráfego de forma eficiente.  
- **CloudFront** (opção a) é para HTTP/HTTPS.  
- **Transit Gateway** (opção d) conecta VPCs, mas não otimiza latência global.  

---

### **Dicas para o Exame**  
1. **Trade-offs de Armazenamento**:  
   - **EBS gp3**: Custo-benefício para workloads gerais.  
   - **EBS io2**: Alta IOPS para bancos de dados críticos.  
2. **Escolha de Instâncias EC2**:  
   - **C5/C6g**: CPU intensiva.  
   - **R5/X2gd**: Memória intensiva.  
3. **Redes**:  
   - **CloudFront**: Conteúdo estático/dinâmico com cache.  
   - **Global Accelerator**: Aplicações TCP/UDP sensíveis a latência.  

---

### **Conclusão**  
Este simulado abrange cenários complexos de otimização de desempenho na AWS. Pratique no **AWS Free Tier** e revise os **whitepapers** de serviços como Aurora, Redshift e ElastiCache para consolidar seu conhecimento! 🚀