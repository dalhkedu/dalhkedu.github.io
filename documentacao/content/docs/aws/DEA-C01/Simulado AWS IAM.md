---
title: "Simulado: AWS IAM"
---

### **Simulado: AWS IAM**

#### **1. Qual componente do AWS IAM é usado para definir um conjunto de permissões para assumir temporariamente?**
A) Usuário  
B) Grupo  
C) Função  
D) Política  

**Resposta:** C) Função  
**Explicação:** As funções (Roles) no IAM são usadas para definir um conjunto de permissões que podem ser assumidas temporariamente por usuários, serviços ou aplicações.

---

#### **2. Qual serviço da AWS pode ser usado para registrar todas as chamadas de API para auditoria e conformidade?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor  

**Resposta:** A) AWS CloudTrail  
**Explicação:** O AWS CloudTrail registra todas as chamadas de API feitas na conta da AWS, permitindo auditoria e conformidade.

---

#### **3. Qual das seguintes opções é uma prática recomendada para otimizar a segurança no AWS IAM?**
A) Conceder permissões amplas a todos os usuários.  
B) Usar MFA para usuários com acesso privilegiado.  
C) Desabilitar a rotação de credenciais.  
D) Manter políticas inline para todas as permissões.  

**Resposta:** B) Usar MFA para usuários com acesso privilegiado.  
**Explicação:** O uso de MFA (Multi-Factor Authentication) adiciona uma camada extra de segurança, especialmente para usuários com acesso privilegiado.

---

#### **4. Qual serviço da AWS pode ser usado para identificar recursos compartilhados externamente?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) IAM Access Analyzer  
D) AWS Trusted Advisor  

**Resposta:** C) IAM Access Analyzer  
**Explicação:** O IAM Access Analyzer ajuda a identificar recursos compartilhados externamente, permitindo a correção de permissões excessivas.

---

#### **5. Qual das seguintes opções é verdadeira sobre o AWS IAM?**
A) Ele não suporta a criação de políticas personalizadas.  
B) Ele permite a integração com provedores de identidade externos usando SAML.  
C) Ele não suporta o uso de MFA.  
D) Ele não permite a criação de grupos de usuários.  

**Resposta:** B) Ele permite a integração com provedores de identidade externos usando SAML.  
**Explicação:** O AWS IAM suporta a integração com provedores de identidade externos usando SAML (Security Assertion Markup Language) para federated access.

---

#### **6. Qual das seguintes opções é uma vantagem do uso de políticas gerenciadas no AWS IAM?**
A) Elas são mais difíceis de gerenciar do que políticas inline.  
B) Elas são pré-definidas pela AWS e não podem ser personalizadas.  
C) Elas podem ser reutilizadas em múltiplos usuários, grupos e funções.  
D) Elas não suportam permissões granulares.  

**Resposta:** C) Elas podem ser reutilizadas em múltiplos usuários, grupos e funções.  
**Explicação:** Políticas gerenciadas podem ser reutilizadas, o que facilita o gerenciamento e a consistência das permissões.

---

#### **7. Qual das seguintes opções é uma prática recomendada para reduzir riscos de segurança no AWS IAM?**
A) Conceder permissões amplas a todos os usuários.  
B) Rotacionar chaves de acesso regularmente.  
C) Desabilitar o uso de MFA.  
D) Manter políticas inline para todas as permissões.  

**Resposta:** B) Rotacionar chaves de acesso regularmente.  
**Explicação:** A rotação regular de chaves de acesso reduz o risco de credenciais comprometidas.

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no AWS IAM?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O AWS IAM é usado para controlar o acesso a recursos e dados na AWS, integrando-se ao KMS para cifragem.

---

#### **9. Qual das seguintes opções é uma limitação do AWS IAM?**
A) Ele não suporta a criação de políticas personalizadas.  
B) Ele tem um limite de 1000 políticas por conta da AWS.  
C) Ele não suporta a integração com provedores de identidade externos.  
D) Ele não permite a criação de grupos de usuários.  

**Resposta:** B) Ele tem um limite de 1000 políticas por conta da AWS.  
**Explicação:** O AWS IAM tem um limite de 1000 políticas gerenciadas por conta da AWS, o que pode ser uma limitação para contas com muitas políticas personalizadas.

---

#### **10. Qual das seguintes opções é uma vantagem do uso do AWS IAM com o AWS Organizations?**
A) Ele permite o gerenciamento centralizado de permissões em múltiplas contas da AWS.  
B) Ele aumenta o custo de gerenciamento de permissões.  
C) Ele não suporta a criação de políticas personalizadas.  
D) Ele não permite a integração com provedores de identidade externos.  

**Resposta:** A) Ele permite o gerenciamento centralizado de permissões em múltiplas contas da AWS.  
**Explicação:** A integração com o AWS Organizations permite o gerenciamento centralizado de permissões em múltiplas contas da AWS, facilitando a administração e a conformidade.

---

### **Resumo das Respostas**
1. C) Função  
2. A) AWS CloudTrail  
3. B) Usar MFA para usuários com acesso privilegiado.  
4. C) IAM Access Analyzer  
5. B) Ele permite a integração com provedores de identidade externos usando SAML.  
6. C) Elas podem ser reutilizadas em múltiplos usuários, grupos e funções.  
7. B) Rotacionar chaves de acesso regularmente.  
8. B) Ele usa IAM para controlar o acesso a recursos e dados.  
9. B) Ele tem um limite de 1000 políticas por conta da AWS.  
10. A) Ele permite o gerenciamento centralizado de permissões em múltiplas contas da AWS.  

---
