---
title: "Domínio 1: Projetar arquiteturas seguras"
---
# Domínio 1: Projetar arquiteturas seguras

### **1. IAM (Identity and Access Management)**  
**O que é**:  
Serviço para gerenciar acesso a recursos AWS com políticas baseadas em permissões granulares.  

**Exemplos Práticos**:  
- **Política de Mínimo Privilégio**:  
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [{
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::meu-bucket-dados/*"
    }]
  }
  ```
  - **Caso de Uso**: Um desenvolvedor precisa apenas ler arquivos de um bucket S3 específico.  

- **Roles para EC2**:  
  - Crie uma IAM Role com permissão para acessar o DynamoDB e associe-a a uma instância EC2.  
  - **Benefício**: Elimina o uso de chaves de acesso fixas.  

**Perguntas Típicas no Exame**:  
- *"Como garantir que uma instância EC2 acesse o S3 sem chaves de acesso?"*  
  **Resposta**: Usar uma IAM Role associada à instância.  

- *"Qual política nega acesso a um bucket S3 para um usuário específico?"*  
  **Resposta**: Use uma política IAM com `"Effect": "Deny"` e `"NotResource"`.  

---

### **2. Criptografia (AWS KMS)**  
**O que é**:  
Serviço para criar e gerenciar chaves de criptografia (CMKs) para proteger dados em repouso e em trânsito.  

**Exemplos Práticos**:  
- **Criptografia em Repouso no S3**:  
  - Habilite **SSE-KMS** no bucket S3 para criptografar objetos com uma CMK.  
  - **Caso de Uso**: Dados sensíveis de clientes em um bucket de relatórios.  

- **Envelope Encryption**:  
  - Use uma CMK para criptografar uma chave de dados (DEK) que, por sua vez, criptografa os dados.  
  - **Benefício**: Segurança em camadas e rotação de chaves simplificada.  

**Perguntas Típicas**:  
- *"Como garantir que todos os buckets S3 sejam criptografados?"*  
  **Resposta**: Use uma **Config Rule** do AWS Config com a regra `s3-bucket-server-side-encryption-enabled`.  

- *"Qual serviço permite rotação automática de chaves de criptografia?"*  
  **Resposta**: AWS KMS (habilite a rotação automática na CMK).  

---

### **3. Segurança de Rede (VPC, Security Groups, NACLs)**  
**Conceitos-Chave**:  
- **VPC**: Rede virtual isolada com subnets públicas/privadas.  
- **Security Groups (SGs)**: Firewall **stateful** (rastreia conexões) no nível da instância.  
- **NACLs (Network ACLs)**: Firewall **stateless** (não rastreia conexões) no nível da subnet.  

**Exemplos Práticos**:  
- **Arquitetura de 3 Camadas**:  
  - **Subnet Pública**: ALB (Security Group permite HTTP/HTTPS de qualquer IP).  
  - **Subnet Privada**: Instâncias EC2 (SG permite tráfego apenas do ALB na porta 80).  
  - **Subnet de Dados**: RDS (SG permite tráfego apenas das EC2 na porta 5432).  

- **NACLs para Bloqueio de IPs Maliciosos**:  
  - Crie uma NACL na subnet pública para bloquear o IP `123.45.67.89/32`.  

**Perguntas Típicas**:  
- *"Qual a diferença entre Security Groups e NACLs?"*  
  **Resposta**: SGs são stateful (regras de entrada/saída são automaticamente permitidas), NACLs são stateless (regras de entrada/saída devem ser explícitas).  

- *"Como restringir acesso a uma instância EC2 apenas de um IP específico?"*  
  **Resposta**: Configure o Security Group da instância para permitir tráfego apenas desse IP.  

---

### **4. AWS WAF (Web Application Firewall)**  
**O que é**:  
Firewall para proteger aplicações web contra ataques como SQL injection, XSS e bots maliciosos.  

**Exemplo Prático**:  
- **Proteção de uma API REST**:  
  - Associe o WAF a um API Gateway.  
  - Adicione regras:  
    1. Bloquear tráfego de países não autorizados.  
    2. Rate limiting de 100 requisições/min por IP.  
    3. Usar **AWS Managed Rules** para SQL injection.  

**Perguntas Típicas**:  
- *"Como proteger uma aplicação web hospedada no S3 e CloudFront?"*  
  **Resposta**: Associe o WAF ao CloudFront e configure regras de segurança.  

- *"Qual regra do WAF bloqueia requisições com o padrão 'SELECT * FROM'?"*  
  **Resposta**: Uma regra personalizada baseada em **SQL injection**.  

---

### **5. AWS Shield e AWS Cognito**  
**AWS Shield**:  
- **Standard**: Proteção contra DDoS básica (gratuita).  
- **Advanced**: Proteção contra ataques complexos (pago).  

**Exemplo Prático**:  
- **Proteção de um ALB**:  
  - Habilite o **Shield Advanced** no ALB para mitigação automática de DDoS.  

**AWS Cognito**:  
- Gerencia autenticação de usuários (login social, SAML, OIDC).  

**Exemplo Prático**:  
- **Login em uma Aplicação Web**:  
  - Use Cognito para autenticar usuários via Google/Facebook.  
  - Autorize acesso a uma API Gateway usando tokens JWT.  

**Perguntas Típicas**:  
- *"Qual serviço AWS protege contra ataques DDoS em aplicações hospedadas no EC2?"*  
  **Resposta**: AWS Shield Advanced.  

- *"Como integrar autenticação social (Google) em uma aplicação React?"*  
  **Resposta**: Use o Amazon Cognito User Pools com Identity Providers.  

---

### **6. Proteção de Dados**  
**Serviços-Chave**:  
- **AWS Backup**: Backup centralizado de recursos (EBS, RDS, DynamoDB).  
- **Amazon Macie**: Identifica dados sensíveis (ex: PII) no S3.  

**Exemplo Prático**:  
- **Backup Automático de RDS**:  
  - Configure uma política no AWS Backup para backups diários do RDS com retenção de 30 dias.  

**Perguntas Típicas**:  
- *"Como garantir que dados no S3 sejam automaticamente classificados como sensíveis?"*  
  **Resposta**: Use o Amazon Macie para análise automatizada.  

---

### **Estudos Práticos Recomendados**  
1. **Cenário 1**:  
   - **Problema**: Uma aplicação web está sofrendo ataques de força bruta.  
   - **Solução**:  
     - Use o WAF com rate limiting e regras para bloquear IPs após 5 tentativas de login.  
     - Habilite o AWS Shield Advanced.  

2. **Cenário 2**:  
   - **Problema**: Dados de clientes em um bucket S3 não estão criptografados.  
   - **Solução**:  
     - Habilite a criptografia SSE-KMS no bucket.  
     - Crie uma Config Rule para auditar compliance.  

3. **Cenário 3**:  
   - **Problema**: Uma instância EC2 foi comprometida devido a uma política IAM excessivamente permissiva.  
   - **Solução**:  
     - Revise a política IAM usando o **IAM Access Analyzer**.  
     - Aplique o princípio do menor privilégio.  

---

### **Dicas para o Exame**  
- **IAM Policies**: Entenda a estrutura JSON (Effect, Action, Resource, Conditions).  
- **KMS vs. CloudHSM**: KMS é gerenciado pela AWS; CloudHSM oferece controle total sobre HSMs físicos.  
- **VPC Flow Logs**: Use para auditoria de tráfego de rede (útil para troubleshooting e segurança).  

---

### **Exemplo de Questão Completa no Exame**  
**Cenário**:  
*"Uma empresa precisa garantir que todas as instâncias EC2 em sua VPC só aceitem tráfego SSH de um IP específico (203.0.113.0/24). Como implementar isso de forma segura e escalável?"*  

**Opções**:  
a) Usar Security Groups para permitir SSH apenas de 203.0.113.0/24.  
b) Usar NACLs para bloquear todo o tráfego SSH exceto de 203.0.113.0/24.  
c) Configurar uma VPN para a VPC.  

**Resposta Correta**: **a** (Security Groups são stateful e aplicam regras no nível da instância).  

---

### **Conclusão**  
Para dominar **Design Secure Architectures**, foque em:  
1. **Controle de Acesso Granular** (IAM, políticas de segurança).  
2. **Criptografia de Dados** (KMS, SSE, TLS).  
3. **Proteção de Rede** (VPC, SGs, NACLs, WAF).  
4. **Ferramentas de Conformidade** (AWS Config, CloudTrail).  



https://docs.aws.amazon.com/accounts/latest/reference/managing-accounts.html
https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html
https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
https://docs.aws.amazon.com/vpc/latest/userguide/security.html
https://docs.aws.amazon.com/whitepapers/latest/aws-overview/security-services.html
https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/data-encryption.html
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.html
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.BackupRestore.html
https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_CreateSnapshotCluster.html
https://docs.aws.amazon.com/efs/latest/ug/awsbackup.html
https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html
https://docs.aws.amazon.com/neptune/latest/userguide/backup-restore-overview.html
https://docs.aws.amazon.com/documentdb/latest/developerguide/backup_restore.html
http://aws.amazon.com/s3/features/replication/
http://aws.amazon.com/backup
http://aws.amazon.com/ebs/
http://aws.amazon.com/ec2/
http://aws.amazon.com/rds/
http://aws.amazon.com/rds/aurora/
http://aws.amazon.com/dynamodb/
http://aws.amazon.com/efs/
http://aws.amazon.com/storagegateway/
http://aws.amazon.com/fsx/windows/