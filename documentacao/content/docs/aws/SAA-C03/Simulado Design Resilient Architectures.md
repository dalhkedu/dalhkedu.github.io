### **Simulado: Design Resilient Architectures**  
**Instruções**: Escolha a melhor resposta e justifique-a com base nas práticas recomendadas da AWS.  

---

#### **1. Uma empresa precisa garantir que uma falha na região us-east-1 não afete sua aplicação global, que exige latência ultrabaixa para usuários na Europa e Ásia. Qual arquitetura atende a HA e DR com RPO próximo a zero?**  
a) Usar DynamoDB Global Tables em us-east-1, eu-central-1 e ap-northeast-1, com Route 53 Geolocation Routing.  
b) Configurar RDS Multi-AZ em us-east-1 e uma Read Replica em eu-central-1.  
c) Usar S3 Cross-Region Replication entre us-east-1 e eu-west-1, com CloudFront.  
d) Implantar EC2 Auto Scaling em us-east-1 e usar AWS Backup para snapshots diários.  

**Resposta Correta**: **a**  
**Explicação**:  
- **DynamoDB Global Tables** replicam dados em tempo real (RPO ≈ 0) em múltiplas regiões, garantindo HA e latência baixa para usuários globais.  
- **Route 53 Geolocation Routing** direciona tráfego para a região mais próxima.  
- A opção **b** não oferece replicação multi-região síncrona (Read Replicas são assíncronas).  
- A opção **c** é focada em armazenamento, não em banco de dados.  
- A opção **d** não resolve latência ou RPO próximo a zero.  

---

#### **2. Qual estratégia de recuperação de desastres (DR) tem o menor RTO para uma aplicação crítica baseada em EC2 e RDS?**  
a) Backup diário do RDS e AMIs do EC2 armazenados no S3, com restauração manual em outra região.  
b) Configurar RDS Multi-AZ e EC2 Auto Scaling em múltiplas zonas de disponibilidade.  
c) Usar RDS Cross-Region Read Replicas e EC2 AMIs pré-configuradas em outra região, com Route 53 Failover.  
d) Habilitar S3 Cross-Region Replication e AWS Lambda para restaurar recursos automaticamente.  

**Resposta Correta**: **c**  
**Explicação**:  
- **RDS Cross-Region Read Replicas** podem ser promovidas a primárias em minutos (RTO baixo).  
- **AMIs pré-configuradas** em outra região permitem implantação rápida de EC2 via Auto Scaling.  
- **Route 53 Failover** automatiza o redirecionamento de tráfego.  
- A opção **a** tem RTO alto devido à restauração manual.  
- A opção **b** é para HA em uma única região, não DR multi-região.  
- A opção **d** depende de scripts Lambda, que podem introduzir atrasos.  

---

#### **3. Como garantir que um bucket S3 com dados críticos seja recuperável após uma exclusão acidental em uma região?**  
a) Habilitar versionamento e S3 Cross-Region Replication (CRR) para outro bucket em uma região diferente.  
b) Usar uma política de bucket para bloquear exclusões.  
c) Configurar o S3 Intelligent-Tiering para mover dados automaticamente para outra região.  
d) Habilitar o S3 Transfer Acceleration para backups rápidos.  

**Resposta Correta**: **a**  
**Explicação**:  
- O **versionamento** preserva versões anteriores de objetos, mesmo após exclusão.  
- A **CRR** replica objetos em outra região, garantindo redundância geográfica.  
- A opção **b** não previne exclusões acidentais por usuários autorizados.  
- A opção **c** não replica dados entre regiões.  
- A opção **d** acelera transferências, mas não é uma solução de DR.  

---

#### **4. Qual serviço AWS é mais adequado para balancear tráfego entre instâncias EC2 em múltiplas regiões com base na latência?**  
a) Application Load Balancer (ALB)  
b) Network Load Balancer (NLB)  
c) AWS Global Accelerator  
d) Route 53 Latency-Based Routing  

**Resposta Correta**: **d**  
**Explicação**:  
- **Route 53 Latency-Based Routing** direciona o tráfego para a região com menor latência para o usuário.  
- **Global Accelerator** (opção c) melhora performance via rede backbone da AWS, mas não é baseado em latência.  
- **ALB/NLB** (opções a e b) operam dentro de uma região.  

---

#### **5. Uma aplicação stateless precisa escalar horizontalmente durante picos de tráfego e reduzir custos durante períodos ociosos. Qual combinação de serviços é ideal?**  
a) EC2 Reserved Instances + ALB  
b) EC2 Spot Instances + Auto Scaling Group  
c) AWS Lambda + API Gateway  
d) EC2 On-Demand Instances + NLB  

**Resposta Correta**: **c**  
**Explicação**:  
- **Lambda** escala automaticamente e cobra apenas por uso (sem custo ocioso).  
- **API Gateway** gerencia o tráfego de entrada.  
- As opções **a** e **d** envolvem custos fixos.  
- A opção **b** é viável, mas Spot Instances podem ser interrompidas, não sendo ideais para cargas críticas.  

---

#### **6. Qual configuração garante que um banco de dados RDS PostgreSQL tenha HA dentro de uma região?**  
a) Habilitar Multi-AZ e uma Read Replica em outra zona de disponibilidade.  
b) Habilitar Multi-AZ e backups automáticos no S3.  
c) Usar um RDS Read Replica em outra região.  
d) Configurar o RDS Multi-AZ e um Auto Scaling Group para instâncias RDS.  

**Resposta Correta**: **b**  
**Explicação**:  
- **Multi-AZ** cria uma réplica síncrona em outra AZ para failover automático (HA).  
- Backups no S3 são para DR, não HA.  
- A opção **a** é redundante (Multi-AZ já inclui HA).  
- A opção **c** é para DR multi-região.  
- RDS não suporta Auto Scaling (opção d é inválida).  

---

#### **7. Como projetar uma arquitetura serverless altamente disponível para uma API global?**  
a) Lambda@Edge + CloudFront + DynamoDB Global Tables.  
b) Lambda em uma região + API Gateway + RDS Multi-AZ.  
c) EC2 Auto Scaling + ALB + S3 Cross-Region Replication.  
d) ECS Fargate + NLB + Route 53.  

**Resposta Correta**: **a**  
**Explicação**:  
- **Lambda@Edge** processa requisições em Edge Locations (latência ultrabaixa).  
- **DynamoDB Global Tables** replicam dados em tempo real.  
- A opção **b** não é multi-região.  
- As opções **c** e **d** não são serverless.  

---

#### **8. Qual estratégia reduz o RTO de uma aplicação que usa EC2 e EBS?**  
a) Snapshots diários do EBS armazenados no S3 Standard.  
b) EC2 Auto Scaling com AMIs pré-configuradas e snapshots do EBS replicados em outra região.  
c) Usar EC2 Spot Instances para reduzir custos.  
d) Habilitar o EBS Multi-AZ.  

**Resposta Correta**: **b**  
**Explicação**:  
- **AMIs pré-configuradas** permitem implantação rápida em outra região.  
- **Snapshots do EBS replicados** garantem dados atualizados.  
- A opção **a** não replica snapshots automaticamente.  
- A opção **d** é inválida (EBS não suporta Multi-AZ).  

---

### **Dicas para o Exame**  
1. **Multi-AZ vs. Multi-Region**:  
   - **Multi-AZ**: Para HA em uma região (ex: RDS, ElastiCache).  
   - **Multi-Region**: Para DR (ex: S3 CRR, DynamoDB Global Tables).  
2. **Escalabilidade Serverless**:  
   - Lambda + API Gateway + DynamoDB são ideais para cargas imprevisíveis.  
3. **RTO/RPO**:  
   - RTO baixo exige automação (ex: Route 53 Failover, Read Replicas promovidas).  
   - RPO baixo requer replicação síncrona (ex: DynamoDB Global Tables).  

---

### **Conclusão**  
Este simulado aborda cenários complexos de HA, DR e escalabilidade. Para aprofundar:  
- Pratique no **AWS Free Tier** (ex: configure Global Tables, Route 53 Failover).  
- Estude os **Whitepapers AWS** (*Disaster Recovery*, *Well-Architected Framework*).  
- Revise as **documentações** de RDS Multi-AZ, S3 CRR e DynamoDB Global Tables.  
