Claro! Aqui está um simulado de múltipla escolha focado em **Segurança, Conformidade e Governança** para o **AWS Certified AI Practitioner (AIF-C01)**, com respostas e explicações detalhadas:

---

### **Simulado: Segurança, Conformidade e Governança em IA na AWS**  
**1. Qual serviço AWS é usado para gerenciar permissões de acesso a recursos como modelos do SageMaker e buckets S3?**  
a) AWS KMS  
b) AWS IAM  
c) Amazon Macie  
d) AWS Shield  

**Resposta Correta:** b) AWS IAM  
**Explicação:** O AWS Identity and Access Management (IAM) controla acesso a recursos da AWS por meio de políticas e roles, garantindo o princípio do menor privilégio.  

---

**2. Para criptografar dados em repouso em um bucket S3 que armazena dados de treinamento de ML, qual serviço deve ser utilizado?**  
a) AWS Shield  
b) Amazon Macie  
c) AWS KMS  
d) AWS WAF  

**Resposta Correta:** c) AWS KMS  
**Explicação:** O AWS Key Management Service (KMS) gerencia chaves de criptografia para proteger dados em repouso, como datasets em S3 ou modelos no SageMaker.  

---

**3. Qual serviço AWS registra atividades da conta para auditoria, como acesso a modelos no Bedrock ou alterações em políticas de IAM?**  
a) AWS CloudTrail  
b) AWS Config  
c) AWS Audit Manager  
d) AWS Trusted Advisor  

**Resposta Correta:** a) AWS CloudTrail  
**Explicação:** O AWS CloudTrail monitora e registra todas as atividades da conta AWS, permitindo auditoria de ações como acesso a recursos de IA.  

---

**4. Qual serviço detecta automaticamente dados sensíveis (como PII) em um bucket S3 usado para treinar modelos de ML?**  
a) AWS KMS  
b) Amazon Macie  
c) AWS WAF  
d) AWS Shield  

**Resposta Correta:** b) Amazon Macie  
**Explicação:** O Amazon Macie usa machine learning para identificar dados confidenciais (ex: CPF, números de cartão de crédito) em armazenamentos como S3.  

---

**5. Qual serviço AWS ajuda a gerar relatórios de conformidade com padrões como ISO e SOC2 para auditorias externas?**  
a) AWS Artifact  
b) AWS Config  
c) AWS Audit Manager  
d) AWS Organizations  

**Resposta Correta:** a) AWS Artifact  
**Explicação:** O AWS Artifact fornece relatórios de conformidade prontos para download, essenciais para validar práticas regulatórias (ex: GDPR, HIPAA).  

---

**6. Qual serviço AWS é usado para proteger APIs de modelos generativos contra ataques de injeção de prompts maliciosos?**  
a) AWS Shield  
b) AWS WAF  
c) AWS KMS  
d) Amazon Macie  

**Resposta Correta:** b) AWS WAF  
**Explicação:** O AWS Web Application Firewall (WAF) filtra tráfego malicioso em APIs, bloqueando ataques como SQL injection ou injeção de prompts.  

---

**7. Qual recurso do SageMaker documenta métricas de desempenho, limitações e contexto de uso de um modelo de ML?**  
a) SageMaker Model Monitor  
b) SageMaker Model Cards  
c) SageMaker Clarify  
d) SageMaker Pipelines  

**Resposta Correta:** b) SageMaker Model Cards  
**Explicação:** As Model Cards são documentos que detalham características de modelos, promovendo transparência e governança em IA.  

---

**8. Para garantir que configurações de recursos AWS estejam alinhadas a políticas internas, qual serviço deve ser usado?**  
a) AWS Config  
b) AWS CloudTrail  
c) AWS Trusted Advisor  
d) AWS Control Tower  

**Resposta Correta:** a) AWS Config  
**Explicação:** O AWS Config avalia configurações de recursos (ex: permissões de S3) contra regras pré-definidas, garantindo conformidade contínua.  

---

**9. Qual serviço AWS protege endpoints de inferência de modelos contra ataques DDoS?**  
a) AWS Shield  
b) AWS WAF  
c) AWS KMS  
d) Amazon Macie  

**Resposta Correta:** a) AWS Shield  
**Explicação:** O AWS Shield oferece proteção contra ataques de negação de serviço (DDoS), garantindo disponibilidade de serviços como SageMaker endpoints.  

---

**10. Qual serviço permite gerenciar múltiplas contas AWS com políticas centralizadas de segurança e uso de recursos?**  
a) AWS Organizations  
b) AWS Control Tower  
c) AWS Audit Manager  
d) AWS Artifact  

**Resposta Correta:** a) AWS Organizations  
**Explicação:** O AWS Organizations centraliza a governança de contas, aplicando políticas como restrições de regiões ou serviços permitidos.  

---

### **Dicas para o Exame**  
- **IAM e KMS:** Domine políticas de acesso mínimo e criptografia de dados.  
- **Conformidade:** Entenda GDPR, HIPAA e o papel do AWS Artifact/Audit Manager.  
- **Governança:** Saiba usar Model Cards e AWS Organizations para transparência e controle.  
- **Segurança:** Foque em WAF, Shield e Macie para proteção contra ameaças.  

Este simulado abrange os principais tópicos do Domínio 5. Revise a documentação oficial e pratique no AWS Skill Builder! 🛡️📚