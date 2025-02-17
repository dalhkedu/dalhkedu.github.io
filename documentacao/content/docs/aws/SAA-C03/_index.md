---
bookCollapseSection: true
weight: 20
title: "SAA-C03"
---

### **Visão Geral do Exame SAA-C03**
- **Objetivo**: Avaliar a capacidade de projetar sistemas distribuídos seguindo as melhores práticas da AWS, considerando requisitos de custo, desempenho, resiliência e segurança.
- **Público-alvo**: Profissionais como arquitetos de soluções, desenvolvedores e administradores de sistemas com experiência prática na AWS (recomendado 1+ ano).
- **Validade**: 3 anos (recertificação necessária após esse período).

---

### **Domínios do Exame (Conteúdo)**
O exame é dividido em 4 domínios principais, com a seguinte distribuição de peso:
1. **Design Secure Architectures** (30%):  
   - IAM, políticas de segurança, criptografia, proteção de dados, segurança de rede (VPC, Security Groups, NACLs).  
   - Serviços como AWS KMS, AWS Shield, WAF, Cognito.

2. **Design Resilient Architectures** (26%):  
   - Alta disponibilidade (HA), recuperação de desastres (DR), escalabilidade (Auto Scaling, ELB), redundância.  
   - Serviços como RDS Multi-AZ, S3 Cross-Region Replication, Route 53, DynamoDB Global Tables.

3. **Design High-Performing Architectures** (24%):  
   - Otimização de desempenho para armazenamento (EBS, S3), computação (EC2, Lambda), redes (CloudFront, Global Accelerator).  
   - Cache (ElastiCache), otimização de bancos de dados (Aurora, Redshift).

4. **Design Cost-Optimized Architectures** (20%):  
   - Estratégias de redução de custos (reservas de instâncias, Spot Instances, análise de custos com AWS Cost Explorer).  
   - Seleção de serviços econômicos (ex: S3 Intelligent-Tiering, Lambda vs. EC2).

---

### **Detalhes do Exame**
- **Formato**: 65 questões de múltipla escolha (escolha única ou múltipla respostas).
- **Duração**: 130 minutos.
- **Custo**: US$ 150 (varia por região).
- **Nota de aprovação**: 720/1000 pontos.
- **Local**: Online (proctored) ou em centros de teste autorizados (Pearson VUE).

---

### **Principais Serviços AWS Cobrados**
- **Computação**: EC2, Lambda, ECS, Elastic Beanstalk.  
- **Armazenamento**: S3, EBS, EFS, Glacier.  
- **Bancos de Dados**: RDS, DynamoDB, Aurora, Redshift.  
- **Rede e Conteúdo**: VPC, CloudFront, Route 53, API Gateway.  
- **Segurança**: IAM, KMS, WAF, AWS Organizations.  
- **Monitoramento e Gerenciamento**: CloudWatch, CloudTrail, AWS Config.

---

### **Diferenças Entre SAA-C02 e SAA-C03**
A versão SAA-C03 trouxe atualizações para refletir as novas tendências e serviços da AWS:
- Maior ênfase em **serverless** (Lambda, Fargate), **containers** (ECS, EKS) e **arquiteturas híbridas** (AWS Outposts).
- Inclusão de tópicos como **AWS Well-Architected Framework**, **sustentabilidade** e **Machine Learning básico** (ex: SageMaker).
- Questões mais focadas em **casos práticos** e análise de trade-offs (custo vs. desempenho vs. segurança).

---

### **Como Estudar para o SAA-C03**
1. **Treinamentos Oficiais**:  
   - Curso "[Architecting on AWS](https://aws.amazon.com/training/)" da AWS.  
   - AWS Skill Builder (recursos gratuitos e laboratórios).

2. **Prática Hands-on**:  
   - Use a AWS Free Tier para criar projetos reais (ex: deploy de uma aplicação web com EC2, RDS e CloudFront).  
   - Experimente serviços como Lambda, S3 e VPC.

3. **Materiais de Estudo**:  
   - Livros: *AWS Certified Solutions Architect Study Guide* (Ben Piper) ou *Tutorials Dojo Cheat Sheets*.  
   - Whitepapers: **[AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)** e **Security Best Practices**.

4. **Testes Práticos**:  
   - Simulados da Tutorials Dojo, Whizlabs ou A Cloud Guru.  
   - Foco em entender **por que uma resposta está correta** (lógica de arquitetura).

---

### **Dicas para o Exame**
- Entenda **cenários de multi-AZ e multi-region** para resiliência.  
- Domine **estratégias de otimização de custos** (ex: escolher entre Spot vs. On-Demand Instances).  
- Pratique a leitura rápida de diagramas de arquitetura.  
- Revise **casos de uso de serviços-chave** (ex: quando usar S3 vs. EFS).

---

### **Recertificação**
Após 3 anos, você pode renovar fazendo:  
- O exame atualizado.  
- O exame de recertificação (online, 50 questões, 80 minutos).