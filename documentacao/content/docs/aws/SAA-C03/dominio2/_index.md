---
title: "Domínio 2: Projetar arquiteturas resilientes"
---
# Domínio 2: Projetar arquiteturas resilientes

### **1. Alta Disponibilidade (HA) e Escalabilidade**
#### **Conceitos-Chave**:
- **Alta Disponibilidade (HA)**: Garantir que um sistema permaneça operacional com tempo de inatividade mínimo, geralmente usando redundância em múltiplas zonas de disponibilidade (AZs).
- **Escalabilidade**: Capacidade de ajustar recursos sob demanda (escalabilidade horizontal ou vertical).
- **Redundância**: Duplicação de componentes críticos para evitar pontos únicos de falha (SPOFs).

#### **Serviços e Exemplos Práticos**:
- **Amazon EC2 Auto Scaling**:  
  - **Caso de Uso**: Uma aplicação web com tráfego variável.  
  - **Implementação**:  
    - Configure um Auto Scaling Group (ASG) para adicionar/remover instâncias EC2 com base na utilização de CPU.  
    - Use um **Application Load Balancer (ALB)** para distribuir tráfego entre instâncias.  
    - **Benefício**: Escalabilidade automática e tolerância a falhas em múltiplas AZs.  

- **Amazon RDS Multi-AZ**:  
  - **Caso de Uso**: Banco de dados crítico que não pode ter downtime.  
  - **Implementação**:  
    - Habilite o Multi-AZ no RDS (uma réplica síncrona é mantida em outra AZ).  
    - Em caso de falha na AZ primária, o RDS faz failover automático para a réplica.  
    - **Benefício**: HA sem intervenção manual.  

#### **Exemplo de Questão no Exame**:
- *"Como garantir que um banco de dados MySQL na AWS permaneça disponível durante uma falha de zona de disponibilidade?"*  
  **Resposta**: Habilitar o **RDS Multi-AZ**, que cria uma réplica síncrona em outra AZ e faz failover automático.  

---

### **2. Recuperação de Desastres (DR)**  
#### **Conceitos-Chave**:
- **Recuperação de Desastres (DR)**: Estratégia para restaurar sistemas após falhas catastróficas (ex: falha de região inteira).  
- **RTO (Recovery Time Objective)**: Tempo máximo aceitável para restaurar operações.  
- **RPO (Recovery Point Objective)**: Perda máxima de dados aceitável (ex: backups a cada 15 minutos).  

#### **Serviços e Exemplos Práticos**:
- **Amazon S3 Cross-Region Replication (CRR)**:  
  - **Caso de Uso**: Backup de dados críticos em outra região.  
  - **Implementação**:  
    - Habilite a CRR em um bucket S3 para replicar objetos automaticamente em outra região.  
    - Use **Versionamento do S3** para proteger contra exclusões acidentais.  
    - **Benefício**: Recuperação rápida de dados em caso de falha regional.  

- **DynamoDB Global Tables**:  
  - **Caso de Uso**: Aplicação global que exige acesso de baixa latência e HA em múltiplas regiões.  
  - **Implementação**:  
    - Crie uma tabela global com réplicas em pelo menos duas regiões (ex: us-east-1 e eu-west-1).  
    - Escrita em qualquer região é replicada em milissegundos.  
    - **Benefício**: HA multi-região e DR integrado.  

#### **Exemplo de Questão no Exame**:
- *"Qual serviço AWS permite replicar dados do S3 automaticamente em outra região para DR?"*  
  **Resposta**: **Amazon S3 Cross-Region Replication (CRR)**.  

---

### **3. Redundância e Balanceamento de Carga**  
#### **Serviços e Exemplos Práticos**:
- **Elastic Load Balancing (ELB)**:  
  - **Tipos**:  
    - **Application Load Balancer (ALB)**: Para HTTP/HTTPS, roteamento baseado em caminho/host.  
    - **Network Load Balancer (NLB)**: Para tráfego TCP/UDP de alta performance.  
  - **Caso de Uso**: Distribuir tráfego entre instâncias EC2 em múltiplas AZs.  
  - **Benefício**: Redundância e HA para aplicações web.  

- **Route 53 (DNS Failover)**:  
  - **Caso de Uso**: Direcionar usuários para uma região secundária se a primária falhar.  
  - **Implementação**:  
    - Configure **health checks** no Route 53 para monitorar endpoints.  
    - Use **Failover Routing Policy** para alternar entre registros primário e secundário.  
    - **Benefício**: DR automatizado baseado em saúde do endpoint.  

#### **Exemplo de Questão no Exame**:
- *"Como garantir que os usuários sejam redirecionados para uma região secundária se a primária ficar inativa?"*  
  **Resposta**: Usar **Route 53 com Failover Routing Policy e health checks**.  

---

### **4. Arquiteturas Híbridas e Multi-Região**  
#### **Exemplo Prático**:  
**Plataforma de Streaming Global**:  
- **Alta Disponibilidade**:  
  - **EC2 Auto Scaling + ALB**: Instâncias em múltiplas AZs com balanceamento de carga.  
  - **DynamoDB Global Tables**: Dados de usuários replicados em us-east-1 e eu-west-1.  
- **Recuperação de Desastres**:  
  - **S3 Cross-Region Replication**: Vídeos replicados em duas regiões.  
  - **RDS Read Replicas em outra região**: Backup de banco de dados para RPO baixo.  
- **Redundância**:  
  - **Route 53 Geolocation Routing**: Direcionar usuários para a região mais próxima.  

---

### **Melhores Práticas para o Exame**  
1. **Multi-AZ vs. Multi-Region**:  
   - **Multi-AZ**: Para HA dentro de uma região (ex: RDS Multi-AZ).  
   - **Multi-Region**: Para DR e HA global (ex: DynamoDB Global Tables).  

2. **Escolha de Serviços para DR**:  
   - **Backup/Restore (RTO alto)**: S3 + AWS Backup.  
   - **Pilot Light (RTO médio)**: RDS Snapshots + EC2 AMIs em outra região.  
   - **Active/Active (RTO baixo)**: DynamoDB Global Tables ou Active/Active ELB.  

3. **Auto Scaling Strategies**:  
   - **Horizontal**: Adicionar mais instâncias (ex: EC2 Auto Scaling).  
   - **Vertical**: Aumentar capacidade da instância (ex: mudar de t3.medium para t3.large).  

---

### **Exemplos de Questões Complexas no Exame**  
#### **Questão 1**:
*"Uma empresa precisa garantir que uma falha em uma região AWS não afete sua aplicação global. Qual combinação de serviços atende a HA e DR com RTO próximo a zero?"*  
**Opções**:  
a) RDS Multi-AZ + EC2 Auto Scaling em uma região.  
b) DynamoDB Global Tables + ALB em múltiplas regiões + Route 53 Failover.  
c) S3 Cross-Region Replication + RDS Read Replicas.  

**Resposta Correta**: **b**  
**Explicação**:  
- DynamoDB Global Tables oferece replicação multi-região síncrona.  
- ALB em múltiplas regiões com Route 53 Failover garante HA ativo/ativo.  

#### **Questão 2**:
*"Qual serviço AWS permite replicar automaticamente dados de um bucket S3 em outra região para fins de DR?"*  
**Opções**:  
a) S3 Transfer Acceleration  
b) S3 Cross-Region Replication  
c) S3 Intelligent-Tiering  

**Resposta Correta**: **b**  

---

### **Estudos Práticos Recomendados**  
1. **Lab 1**:  
   - Crie um ambiente com EC2 Auto Scaling, ALB e RDS Multi-AZ.  
   - Simule uma falha de AZ e observe o failover automático do RDS.  

2. **Lab 2**:  
   - Configure S3 Cross-Region Replication entre duas regiões.  
   - Delete um objeto no bucket de origem e verifique a replicação no destino.  

3. **Lab 3**:  
   - Use o Route 53 para configurar um failover entre duas instâncias EC2 em regiões diferentes.  
   - Desligue a instância primária e teste o redirecionamento automático.  

---

### **Conclusão**  
Para dominar **Design Resilient Architectures** no exame SAA-C03:  
- Entenda a diferença entre **HA (Multi-AZ)** e **DR (Multi-Region)**.  
- Saiba quando usar **Auto Scaling**, **ELB**, **RDS Multi-AZ**, **S3 CRR** e **DynamoDB Global Tables**.  
- Pratique cenários de failover e recuperação de desastres no **AWS Free Tier**.  


[HCP - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/high-performance-computing-lens/scenarios.html) \
[AWS Auto Scaling](https://aws.amazon.com/autoscaling/) \
[O que é o Amazon EC2 Auto Scaling?](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) \
[Redes de borda com a AWS](https://aws.amazon.com/products/networking/edge-networking/) \
[What is AWS Transfer Family?](https://docs.aws.amazon.com/transfer/latest/userguide/what-is-aws-transfer-family.html) \
[Sem servidor na AWS](https://aws.amazon.com/serverless/) \
[O que é o Amazon API Gateway?](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html) \
[O que é o Amazon SNS?](https://docs.aws.amazon.com/sns/latest/dg/welcome.html) \
[O que é o Amazon Simple Queue Service?](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html) \
[Alta disponibilidade e escalabilidade na AWS](https://docs.aws.amazon.com/whitepapers/latest/real-time-communication-on-aws/high-availability-and-scalability-on-aws.html) \
[Alta disponibilidade e escalabilidade na AWS](https://docs.aws.amazon.com/whitepapers/latest/availability-and-beyond-improving-resilience/fault-tolerance-and-fault-isolation.html) \
[What is Elastic Disaster Recovery?](https://docs.aws.amazon.com/drs/latest/userguide/what-is-drs.html) \
[Conectar sua VPC a outras redes](https://docs.aws.amazon.com/vpc/latest/userguide/extend-intro.html) \
[O que é o Amazon Route 53?](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html) \
[Amazon RDS Proxy para o Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/rds-proxy.html)