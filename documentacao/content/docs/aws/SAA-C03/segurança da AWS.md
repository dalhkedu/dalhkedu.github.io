---
title: "AWS IAM"
---

### **1. AWS IAM (Identity and Access Management)**  
**O que é**:  
Serviço centralizado para gerenciar **acesso a recursos da AWS**. Permite definir **quem** pode fazer **o que** em quais recursos.  

**Finalidade**:  
- Autenticação (usuários, grupos, roles).  
- Autorização (políticas baseadas em JSON).  
- Integração com provedores de identidade (SAML, OIDC, Microsoft AD).  

**Como usar**:  
- **Usuários/Grupos**: Crie usuários para pessoas e grupos para aplicar políticas a múltiplos usuários.  
- **Roles**: Permissões temporárias para serviços (ex: EC2 acessar S3) ou usuários externos (SSO).  
- **Políticas**: Defina regras como:  
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [{
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::meu-bucket/*"
    }]
  }
  ```

**Exemplo em uma Grande Empresa**:  
- **Cenário**: Uma empresa com departamentos (TI, RH, Financeiro) precisa de acesso granular.  
  - **Solução**:  
    - Crie grupos como `TI-Admins`, `RH-ReadOnly`, `Financeiro-Billing`.  
    - Atribua políticas:  
      - `TI-Admins`: Acesso total a EC2, VPC.  
      - `RH-ReadOnly`: Apenas leitura em DynamoDB de dados de funcionários.  
    - Use **IAM Roles** para aplicações EC2 acessarem o S3 sem credenciais fixas.  

**Melhores Práticas**:  
- **Princípio do menor privilégio**.  
- Habilite **MFA** para usuários administrativos.  
- Use **Roles** em vez de chaves de acesso de longo prazo.  

---

### **2. AWS KMS (Key Management Service)**  
**O que é**:  
Serviço gerenciado para criar e controlar **chaves de criptografia** (CMKs – Customer Master Keys).  

**Finalidade**:  
- Criptografar dados em repouso (S3, RDS, EBS) e em trânsito.  
- Gerenciar ciclo de vida de chaves (rotação automática, revogação).  

**Como usar**:  
- **Chaves Simétricas (AES-256)**: Para criptografia de dados.  
- **Envelope Encryption**: Criptografe chaves de dados com uma CMK.  
- **Integração**: Ative criptografia em serviços como S3, EBS, Lambda.  

**Exemplo em uma Grande Empresa**:  
- **Cenário**: Um banco precisa criptografar dados sensíveis de clientes.  
  - **Solução**:  
    - Crie uma CMK no KMS com política restrita ao departamento de segurança.  
    - Criptografe dados no S3 (SSE-KMS) e bancos de dados RDS (usando CMK).  
    - Use **AWS CloudHSM** para chaves sob controle de hardware dedicado (HSM).  

**Melhores Práticas**:  
- Use **CMKs diferentes** por departamento ou aplicação.  
- Habilite **rotação automática** de chaves (a cada 1 ano).  
- Revogue acesso via políticas de chave se um funcionário sair.  

---

### **3. AWS WAF (Web Application Firewall)**  
**O que é**:  
Firewall de aplicação web para proteger contra ataques como SQL injection, XSS e bots maliciosos.  

**Finalidade**:  
- Filtrar tráfego HTTP/HTTPS em aplicações (CloudFront, ALB, API Gateway).  
- Criar regras personalizadas ou usar **AWS Managed Rules**.  

**Como usar**:  
- **Web ACLs**: Conjunto de regras aplicadas a recursos.  
- **Regras**:  
  - Bloquear IPs de países específicos.  
  - Limitar taxa de requisições (rate limiting).  
  - Detectar padrões maliciosos (ex: `SELECT * FROM`).  

**Exemplo em uma Grande Empresa**:  
- **Cenário**: Uma loja online sofre ataques de bots e SQL injection.  
  - **Solução**:  
    - Associe o WAF a um Application Load Balancer (ALB).  
    - Adicione regras:  
      - Bloquear tráfego de fora do país de operação.  
      - Usar **AWS Managed Rules** para SQL injection e XSS.  
      - Rate limiting de 100 requisições/min por IP.  

**Melhores Práticas**:  
- Monitore métricas como `BlockedRequests` no CloudWatch.  
- Use **WAF Security Automations** para respostas automatizadas a ameaças.  

---

### **4. AWS Organizations**  
**O que é**:  
Serviço para gerenciar **múltiplas contas AWS** centralizadamente, com políticas de governança.  

**Finalidade**:  
- **Consolidar billing** de todas as contas.  
- Aplicar **SCPs (Service Control Policies)** para restringir acesso.  
- Criar hierarquia de **OUs (Organizational Units)**.  

**Como usar**:  
- **Conta Master**: Gerencia todas as contas vinculadas.  
- **SCPs**: Políticas JSON que limitam permissões (ex: bloquear regiões não autorizadas).  
- **OUs**: Agrupe contas por departamento (ex: TI, Marketing, Produção).  

**Exemplo em uma Grande Empresa**:  
- **Cenário**: Uma multinacional com 50 contas AWS precisa de governança centralizada.  
  - **Solução**:  
    - Crie OUs como `Prod-Brasil`, `Dev-EUA`, `Financeiro`.  
    - Aplique SCPs:  
      - Bloquear criação de recursos fora das regiões `us-east-1` e `sa-east-1`.  
      - Impedir a exclusão de buckets S3 em contas de produção.  
    - Use **AWS Control Tower** para automatizar a configuração de governança.  

**Melhores Práticas**:  
- Use **Service Control Policies (SCPs)** para garantir compliance.  
- Habilite **AWS CloudTrail** em todas as contas para auditoria.  

---

### **Exemplo de Arquitetura Integrada em uma Grande Empresa**  
**Empresa**: Banco internacional com requisitos de segurança rigorosos (PCI DSS, GDPR).  

1. **IAM**:  
   - **SSO Corporativo**: Integração com Microsoft Active Directory via AWS IAM Identity Center.  
   - **Roles para EC2**: Permissão mínima para acessar dados criptografados no S3.  

2. **KMS**:  
   - **CMKs por Departamento**: Chaves separadas para dados de clientes, transações e logs.  
   - **Criptografia em Trânsito**: TLS 1.3 para APIs usando Certificate Manager.  

3. **WAF**:  
   - **Proteção de APIs**: WAF associado ao API Gateway para bloquear ataques a APIs de pagamento.  
   - **Bot Control**: Regras para bloquear scrapers de preços.  

4. **AWS Organizations**:  
   - **SCPs Globais**: Bloquear criação de instâncias EC2 sem criptografia EBS.  
   - **OU "PCI"**: Contas dedicadas a sistemas de pagamento, com políticas restritivas.  

5. **Monitoramento**:  
   - **AWS Security Hub**: Visão unificada de vulnerabilidades.  
   - **Amazon GuardDuty**: Detecção de atividades anômalas (ex: acesso suspeito ao KMS).  

---

### **Quando Usar Cada Serviço?**  
| **Serviço**         | **Cenário de Uso**                                  |  
|----------------------|----------------------------------------------------|  
| **IAM**              | Controle de acesso granular a usuários e serviços. |  
| **KMS**              | Criptografia de dados sensíveis em repouso/trânsito.|  
| **WAF**              | Proteção de aplicações web contra ataques OWASP Top 10. |  
| **AWS Organizations**| Governança multi-conta e políticas centralizadas.   |  

---

### **Vantagens e Desvantagens**  
| **Serviço**         | **Vantagens**                                      | **Desvantagens**                              |  
|----------------------|---------------------------------------------------|-----------------------------------------------|  
| **IAM**              | Flexível, integra com SAML/AD, custo zero.        | Complexidade em ambientes muito grandes.      |  
| **KMS**              | Chaves gerenciadas, integração nativa.            | Custo por requisição de API (alto volume).    |  
| **WAF**              | Proteção em tempo real, regras personalizáveis.   | Custo pode escalar com milhões de requisições.|  
| **AWS Organizations**| Controle centralizado, SCPs poderosos.            | Configuração inicial complexa para OUs/SCPs.  |  

---

### **Conclusão**  
Em uma grande empresa, a combinação de **IAM** (controle de acesso), **KMS** (criptografia), **WAF** (proteção de aplicações) e **AWS Organizations** (governança multi-conta) forma a base de uma arquitetura segura e compliance. A integração desses serviços permite mitigar riscos, auditar atividades e garantir conformidade com regulamentações como GDPR e PCI DSS.