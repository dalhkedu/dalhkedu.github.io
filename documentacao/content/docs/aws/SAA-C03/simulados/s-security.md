---
title: "Simulado: Design Secure Architectures"
---

### **Simulado: Design Secure Architectures**

---

#### **1. Você precisa garantir que uma IAM Role só possa ser assumida por usuários que estejam acessando a partir de um IP específico (192.0.2.0/24) e que tenham MFA habilitado. Qual política IAM atende a esses requisitos?**

a)  
```json
{
  "Effect": "Allow",
  "Principal": "*",
  "Action": "sts:AssumeRole",
  "Condition": {
    "IpAddress": {"aws:SourceIp": "192.0.2.0/24"}
  }
}
```  
b)  
```json
{
  "Effect": "Allow",
  "Principal": "*",
  "Action": "sts:AssumeRole",
  "Condition": {
    "Bool": {"aws:MultiFactorAuthPresent": "true"}
  }
}
```  
c)  
```json
{
  "Effect": "Allow",
  "Principal": "*",
  "Action": "sts:AssumeRole",
  "Condition": {
    "IpAddress": {"aws:SourceIp": "192.0.2.0/24"},
    "Bool": {"aws:MultiFactorAuthPresent": "true"}
  }
}
```  
d)  
```json
{
  "Effect": "Allow",
  "Principal": "*",
  "Action": "sts:AssumeRole",
  "Condition": {
    "IpAddressIfExists": {"aws:SourceIp": "192.0.2.0/24"},
    "BoolIfExists": {"aws:MultiFactorAuthPresent": "true"}
}
```

---

#### **2. Você deseja permitir que uma conta AWS (ID: 123456789012) use uma CMK (Customer Master Key) da sua conta para descriptografar dados. Qual configuração é necessária no KMS?**

a) Adicionar a conta 123456789012 à política de chave com a ação `kms:Decrypt`.  
b) Criar um alias compartilhado para a chave e conceder acesso à conta externa.  
c) Usar uma política de bucket S3 para permitir acesso à conta 123456789012.  
d) Habilitar o compartilhamento de chaves via AWS Resource Access Manager (RAM).  

---

#### **3. Uma instância EC2 em uma subnet privada precisa acessar atualizações de software na internet. Qual configuração de VPC é necessária?**

a) Associar um Elastic IP diretamente à instância EC2.  
b) Configurar um NAT Gateway em uma subnet pública e atualizar a tabela de rotas da subnet privada.  
c) Usar um Internet Gateway na subnet privada.  
d) Adicionar uma regra de Security Group permitindo tráfego de saída para 0.0.0.0/0.  

---

#### **4. Você precisa bloquear todo o tráfego HTTP (porta 80) de uma subnet pública, mas permitir HTTPS (porta 443). Qual é a abordagem mais segura?**

a) Usar um Security Group para bloquear a porta 80.  
b) Configurar uma NACL (Network ACL) para negar entrada na porta 80.  
c) Usar o AWS WAF para filtrar tráfego HTTP.  
d) Habilitar o AWS Shield Advanced.  

---

#### **5. Qual serviço AWS permite bloquear IPs que excedam um limite de requisições por minuto em uma API REST?**

a) AWS Shield Advanced  
b) AWS WAF com regras rate-based  
c) AWS Config  
d) Amazon GuardDuty  

---

#### **6. Qual recurso do AWS Shield Advanced NÃO está disponível no Shield Standard?**

a) Mitigação de ataques de camada 3/4 (ex: SYN floods).  
b) Acesso a uma equipe de resposta a DDoS 24/7.  
c) Proteção integrada para recursos como ALB e CloudFront.  
d) Defesa contra ataques de camada 7 (ex: HTTP floods).  

---

#### **7. Você precisa integrar um diretório Active Directory (AD) on-premises ao Amazon Cognito para autenticação em uma aplicação web. Qual abordagem deve ser usada?**

a) Configurar o Cognito como um provedor SAML e o AD como um IdP.  
b) Usar o AWS Directory Service para replicar o AD na AWS.  
c) Criar um User Pool no Cognito e sincronizar manualmente os usuários.  
d) Habilitar o OpenID Connect (OIDC) no Cognito.  

---

#### **8. Qual política de bucket S2 garante que todos os objetos sejam criptografados com SSE-KMS?**

a)  
```json
{
  "Effect": "Deny",
  "Principal": "*",
  "Action": "s3:PutObject",
  "Resource": "arn:aws:s3:::meu-bucket/*",
  "Condition": {
    "Null": {"s3:x-amz-server-side-encryption": "true"}
  }
}
```  
b)  
```json
{
  "Effect": "Allow",
  "Principal": "*",
  "Action": "s3:PutObject",
  "Resource": "arn:aws:s3:::meu-bucket/*",
  "Condition": {
    "StringEquals": {"s3:x-amz-server-side-encryption": "aws:kms"}
  }
}
```  
c) Usar ACLs (Access Control Lists) para habilitar a criptografia padrão.  
d) Habilitar a criptografia padrão no bucket via Console AWS.  

---

#### **9. Qual serviço AWS centraliza achados de segurança de ferramentas como GuardDuty, Inspector e Macie?**

a) AWS Security Hub  
b) AWS Config  
c) Amazon CloudWatch  
d) AWS Trusted Advisor  

---

#### **10. Uma instância EC2 na conta A precisa acessar um bucket S3 na conta B, que está criptografado com uma CMK da conta B. O que é necessário?**

a) Compartilhar a CMK com a conta A via política de chave e conceder acesso ao bucket S3.  
b) Usar uma Role na conta A com acesso ao S3 e replicar a CMK na conta A.  
c) Criptografar o bucket com uma CMK gerenciada pela AWS (SSE-S3).  
d) Configurar um bucket policy na conta B permitindo acesso da conta A e habilitar criptografia SSE-KMS.  

---

**Resposta Correta**: **c**  
**Explicação**:  
- A opção **c** usa condições combinadas (`IpAddress` e `Bool`) para exigir que o usuário esteja no IP especificado **e** tenha MFA habilitado.  
- As opções **a** e **b** aplicam apenas uma condição individual.  
- A opção **d** usa `IfExists`, o que permite a ação mesmo se a chave de condição não estiver presente, violando o requisito de segurança.  

---

**Resposta Correta**: **a**  
**Explicação**:  
- O KMS exige que a política da chave (key policy) conceda explicitamente permissões à conta externa. A opção **a** está correta, pois adiciona a conta à política com `kms:Decrypt`.  
- A opção **b** é incorreta, pois aliases não concedem permissões.  
- A opção **c** refere-se ao S3, não ao KMS.  
- A opção **d** é inválida, pois o RAM não gerencia compartilhamento de chaves KMS.  

---

**Resposta Correta**: **b**  
**Explicação**:  
- O NAT Gateway permite que instâncias em subnets privadas acessem a internet enquanto permanecem isoladas. A opção **b** está correta.  
- A opção **a** exporia a instância à internet, comprometendo a segurança.  
- A opção **c** é impossível, pois Internet Gateways são associados à VPC, não a subnets.  
- A opção **d** é necessária, mas insuficiente sem o NAT Gateway.  

---

**Resposta Correta**: **b**  
**Explicação**:  
- NACLs operam no nível da subnet e podem bloquear tráfego específico (como porta 80). A opção **b** está correta.  
- A opção **a** não é eficaz, pois Security Groups são stateful e não bloqueiam tráfego de entrada se a saída for permitida.  
- A opção **c** aplica-se a aplicações web em ALB/CloudFront, não a subnets.  
- A opção **d** protege contra DDoS, mas não bloqueia portas específicas.  

---

**Resposta Correta**: **b**  
**Explicação**:  
- O AWS WAF suporta regras rate-based para limitar requisições por IP. A opção **b** está correta.  
- A opção **a** protege contra DDoS, mas não gerencia rate limiting granular.  
- A opção **c** audita configurações, não bloqueia tráfego.  
- A opção **d** detecta ameaças, mas não aplica rate limiting.  

---

**Resposta Correta**: **b**  
**Explicação**:  
- O Shield Advanced inclui suporte 24/7 da equipe de resposta a DDoS, enquanto o Shield Standard (gratuito) não. A opção **b** está correta.  
- As opções **a**, **c** e **d** são recursos do Shield Standard.  

---

**Resposta Correta**: **a**  
**Explicação**:  
- O SAML é o protocolo adequado para integração com AD. A opção **a** está correta.  
- A opção **b** não integra diretamente o AD ao Cognito.  
- A opção **c** exigiria sincronização manual, não automatizada.  
- A opção **d** é usada para provedores como Google/Facebook, não AD.  

---

**Resposta Correta**: **a**  
**Explicação**:  
- A opção **a** nega uploads de objetos sem criptografia, garantindo compliance.  
- A opção **b** permite uploads apenas com criptografia, mas não bloqueia os demais.  
- A opção **c** é incorreta, pois ACLs não controlam criptografia.  
- A opção **d** é válida, mas não é uma política de bucket (a questão pede uma política explícita).  

---

**Resposta Correta**: **a**  
**Explicação**:  
- O Security Hub agrega dados de múltiplas ferramentas de segurança. A opção **a** está correta.  
- A opção **b** foca em conformidade de configuração.  
- A opção **c** monitora métricas e logs.  
- A opção **d** fornece recomendações de otimização, não de segurança.  

---

**Resposta Correta**: **a**  
**Explicação**:  
- A conta B deve compartilhar a CMK com a conta A (via key policy) e o bucket deve permitir acesso via bucket policy. A opção **a** está correta.  
- A opção **d** está incompleta, pois sem acesso à CMK, a conta A não pode descriptografar os dados.  
- As opções **b** e **c** não resolvem a necessidade de descriptografia com a CMK da conta B.  

---

### **Dicas para o Exame**  
- **IAM Policies**: Domine condições como `aws:SourceIp`, `aws:MultiFactorAuthPresent` e operadores lógicos (`Bool`, `IpAddress`).  
- **KMS Cross-Account**: Sempre atualize a política da chave para incluir contas externas.  
- **NACL vs Security Group**: Lembre-se de que NACLs são stateless e aplicadas à subnet, enquanto SGs são stateful e aplicadas à instância.  
- **WAF Rate-Based Rules**: Úteis para mitigar ataques de força bruta e scraping.  
