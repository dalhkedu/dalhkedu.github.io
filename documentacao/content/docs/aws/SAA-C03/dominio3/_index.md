---
title: "Domínio 3: Projetar arquiteturas de alta performance"
---

# Domínio 3: Projetar arquiteturas de alta performance

### **1. Otimização de Armazenamento**
#### **Amazon EBS (Elastic Block Store)**  
**O que é**: Armazenamento em bloco para instâncias EC2.  
**Otimizações**:  
- **Escolha do Tipo de Volume**:  
  - **gp3**: Uso geral (balanceamento entre custo e desempenho).  
  - **io2 Block Express**: Alta IOPS (até 256.000 IOPS) para bancos de dados críticos.  
- **RAID 0**: Combinar múltiplos volumes para aumentar throughput (ex: 4 volumes io2 de 16K IOPS cada = 64K IOPS total).  
- **Provisioned IOPS (io2)**: Garantir desempenho consistente para cargas de trabalho intensivas.  

**Exemplo Prático**:  
- **Cenário**: Um banco de dados Oracle exige 50.000 IOPS.  
  - **Solução**: Use um volume **io2 Block Express** com 50.000 IOPS provisionados.  

**Possível Pergunta no Exame**:  
*"Qual tipo de volume EBS é mais adequado para um banco de dados OLTP com requisitos de latência ultrabaixa?"*  
**Resposta**: **io2 Block Express**.  

---

#### **Amazon S3**  
**Otimizações**:  
- **Multi-Part Upload**: Para arquivos grandes (>5 GB), reduzindo tempo de transferência.  
- **Transfer Acceleration**: Acelera uploads via CloudFront Edge Locations.  
- **S3 Intelligent-Tiering**: Move dados automaticamente entre tiers (frequente, infrequente, arquivamento) para otimizar custo e acesso.  

**Exemplo Prático**:  
- **Cenário**: Upload de arquivos de vídeo de 10 GB para processamento.  
  - **Solução**: Usar **Multi-Part Upload** e **Transfer Acceleration**.  

**Possível Pergunta no Exame**:  
*"Como melhorar o upload de arquivos grandes para o S3 em regiões distantes?"*  
**Resposta**: **S3 Transfer Acceleration**.  

---

### **2. Otimização de Computação**  
#### **Amazon EC2**  
**Otimizações**:  
- **Escolha de Instâncias**:  
  - **Computação (C5, C6g)**: Para cargas de CPU intensiva.  
  - **Memória (R5, X2gd)**: Para bancos de dados em memória (ex: Redis).  
- **Elastic Network Adapter (ENA)**: Melhora throughput de rede (até 100 Gbps).  
- **Placement Groups**: Agrupar instâncias para latência ultrabaixa (ex: aplicações HPC).  

**Exemplo Prático**:  
- **Cenário**: Aplicação de machine learning com alto uso de CPU.  
  - **Solução**: Usar instâncias **C6g** (Graviton2) com Placement Group **Cluster**.  

---

#### **AWS Lambda**  
**Otimizações**:  
- **Concorrência Reservada (Provisioned Concurrency)**: Reduz cold starts para funções críticas.  
- **Tamanho do Pacote**: Minimizar dependências para reduzir tempo de inicialização.  
- **Escolha de Memória**: Ajustar memória alocada (afecta CPU e custo).  

**Exemplo Prático**:  
- **Cenário**: API serverless com picos de tráfego imprevisíveis.  
  - **Solução**: Usar **Provisioned Concurrency** para funções essenciais.  

**Possível Pergunta no Exame**:  
*"Como garantir baixa latência para uma função Lambda crítica durante picos de tráfego?"*  
**Resposta**: **Provisioned Concurrency**.  

---

### **3. Otimização de Redes**  
#### **Amazon CloudFront**  
**O que é**: CDN para distribuir conteúdo estático/dinâmico com baixa latência.  
**Otimizações**:  
- **Cache Policies**: Configurar TTLs para conteúdo estático.  
- **Lambda@Edge**: Personalizar conteúdo na borda (ex: redirecionamentos).  

**Exemplo Prático**:  
- **Cenário**: Site global com imagens pesadas.  
  - **Solução**: Usar CloudFront com **Cache Policies** e compressão de imagens (ex: WebP).  

---

#### **AWS Global Accelerator**  
**O que é**: Melhora performance de aplicações TCP/UDP via rede backbone da AWS.  
**Casos de Uso**:  
- Aplicações sensíveis a latência (ex: jogos online).  
- Failover entre regiões usando endpoints estáticos (anycast IPs).  

**Exemplo Prático**:  
- **Cenário**: Aplicação VoIP com usuários globais.  
  - **Solução**: Usar Global Accelerator para rotear tráfego via AWS backbone.  

**Possível Pergunta no Exame**:  
*"Qual serviço reduz a latência de uma aplicação global usando IPs anycast?"*  
**Resposta**: **AWS Global Accelerator**.  

---

### **4. Cache (Amazon ElastiCache)**  
**O que é**: Serviço gerenciado para Redis (ElastiCache for Redis) e Memcached.  
**Otimizações**:  
- **Padrão Cache-Aside**: Aplicação consulta o cache antes do banco de dados.  
- **Redis Cluster Mode**: Escalabilidade horizontal para grandes cargas.  

**Exemplo Prático**:  
- **Cenário**: Aplicação de e-commerce com picos de tráfego durante promoções.  
  - **Solução**: Usar **ElastiCache for Redis** para armazenar sessões de usuário e resultados de queries frequentes.  

**Possível Pergunta no Exame**:  
*"Como reduzir a carga em um banco de dados RDS durante picos de tráfego?"*  
**Resposta**: **Usar ElastiCache para cache de queries frequentes**.  

---

### **5. Otimização de Bancos de Dados**  
#### **Amazon Aurora**  
**O que é**: Banco de dados relacional compatível com MySQL/PostgreSQL, 5x mais rápido que RDS.  
**Otimizações**:  
- **Aurora Serverless v2**: Escalabilidade automática baseada em carga.  
- **Read Replicas**: Balanceamento de carga de leituras.  

**Exemplo Prático**:  
- **Cenário**: Aplicação SaaS com carga variável de leitura/escrita.  
  - **Solução**: Usar **Aurora Serverless v2** e 3 Read Replicas.  

---

#### **Amazon Redshift**  
**O que é**: Data warehouse para análises em larga escala.  
**Otimizações**:  
- **RA3 Nodes**: Separa storage e compute (escalabilidade independente).  
- **Materialized Views**: Pré-calcular resultados complexos.  

**Exemplo Prático**:  
- **Cenário**: Relatórios lentos em um data warehouse de 100 TB.  
  - **Solução**: Migrar para **Redshift RA3** e usar **Materialized Views**.  

**Possível Pergunta no Exame**:  
*"Qual recurso do Redshift melhora performance de queries complexas?"*  
**Resposta**: **Materialized Views**.  

---

### **Exemplo de Arquitetura Integrada**  
**Aplicação de Streaming de Vídeo**:  
- **Armazenamento**: S3 com Transfer Acceleration e Intelligent-Tiering.  
- **Computação**: EC2 C6g (Graviton2) para encoding de vídeo.  
- **Redes**: CloudFront para distribuição global + Global Accelerator para uploads.  
- **Cache**: ElastiCache Redis para metadados de vídeo.  
- **Banco de Dados**: Aurora Serverless para catálogo de conteúdo.  

---

### **Questões Típicas no Exame**  
1. **Questão**:  
   *"Uma aplicação de comércio eletrônico está enfrentando lentidão durante o Black Friday. Como melhorar o desempenho sem redesenhar toda a arquitetura?"*  
   **Opções**:  
   a) Aumentar o tamanho das instâncias EC2.  
   b) Adicionar ElastiCache para armazenar resultados de queries frequentes.  
   c) Migrar para S3 Standard-IA.  
   **Resposta**: **b**.  

2. **Questão**:  
   *"Qual serviço AWS é mais adequado para reduzir a latência de uma API global baseada em REST?"*  
   **Opções**:  
   a) Amazon API Gateway  
   b) AWS Global Accelerator  
   c) Amazon CloudFront  
   **Resposta**: **c** (se a API servir conteúdo cacheável) ou **b** (se a API for dinâmica).  

---

### **Melhores Práticas para o Exame**  
- **Entenda Trade-offs**:  
  - **EBS gp3 vs. io2**: Custo vs. desempenho garantido.  
  - **Lambda vs. EC2**: Escalabilidade automática vs. controle total.  
- **Foco em Casos de Uso**:  
  - Alta IOPS → io2 Block Express.  
  - Baixa latência global → Global Accelerator + CloudFront.  
- **SaaS e Serverless**:  
  - Aurora Serverless e Lambda são frequentemente citados em questões de otimização.  

---

### **Conclusão**  
Para dominar **Design High-Performing Architectures** no exame SAA-C03:  
- Pratique cenários com **EBS, S3, Lambda, CloudFront e ElastiCache**.  
- Entenda como escolher instâncias EC2 e configurar Redshift/Aurora.  
- Revise casos de uso de **Global Accelerator** vs. **CloudFront**.  


[Armazenamento](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/storage-services.html) \
[Armazenamento na nuvem na AWS](https://aws.amazon.com/products/storage/) \
[Gerenciar o ciclo de vida dos objetos](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html) \
[Computar](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/compute-services.html) \
[bancos de dados](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/database.html) \
[Redes no Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-networking.html) \
[Como planejar a VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-getting-started.html) \
[Conectar VPCs usando emparelhamento da VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-peering.html) \
[Conectar sua VPC a outro serviços usando o AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/userguide/endpoint-services-overview.html) \
[Filtrar o tráfego de DNS usando o Route 53 Resolver DNS Firewall](https://docs.aws.amazon.com/vpc/latest/userguide/resolver-dns-firewall.html) \
[Filtrar o tráfego de rede usando o AWS Network Firewall](https://docs.aws.amazon.com/vpc/latest/userguide/network-firewall.html) \
[Exemplos de VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-scenarios-intro.html) \
[O que é o AWS Global Accelerator?](https://docs.aws.amazon.com/global-accelerator/latest/dg/what-is-global-accelerator.html) \
[O que é o Amazon CloudFront?](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) \
[Data ingestion methods](https://docs.aws.amazon.com/whitepapers/latest/building-data-lakes/data-ingestion-methods.html) \
[Data processing](https://docs.aws.amazon.com/whitepapers/latest/data-warehousing-on-aws/data-processing.html) \
[O que AWS Lake Formation](https://docs.aws.amazon.com/lake-formation/latest/dg/what-is-lake-formation.html)