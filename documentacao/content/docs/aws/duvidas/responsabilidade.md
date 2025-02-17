---
title: "Modelo de Responsabilidade Compartilhada AWS"
---

### **Modelo de Responsabilidade Compartilhada AWS**  
Define quem é responsável por quais aspectos da segurança na nuvem:  

#### **Responsabilidade da AWS** (Segurança **DA** Nuvem):  
1. **Infraestrutura Física**:  
   - Data centers, hardware, rede global, energia, resfriamento.  
   - Proteção contra desastres físicos, acesso não autorizado.  
2. **Infraestrutura Global**:  
   - Regiões, Availability Zones (AZs), Edge Locations.  
3. **Serviços Gerenciados**:  
   - Segurança da camada de virtualização (ex: hipervisor EC2).  
   - Atualizações de firmware, patches de hardware.  
   - Serviços como **RDS, Lambda, DynamoDB**: AWS gerencia o sistema operacional, aplicação e escalabilidade.  
4. **Conformidade da Infraestrutura**:  
   - Certificações como ISO, SOC, PCI DSS para a infraestrutura subjacente.  

---

#### **Responsabilidade do Cliente** (Segurança **NA** Nuvem):  
1. **Dados**:  
   - Criptografia de dados em trânsito e repouso.  
   - Classificação, backup e gestão do ciclo de vida (ex: políticas no S3).  
2. **Controle de Acesso**:  
   - Gerenciamento de usuários, grupos e permissões via **IAM**.  
   - Políticas de segurança (ex: MFA, roles, políticas de bucket S3).  
3. **Configuração de Serviços**:  
   - Sistemas operacionais em instâncias EC2 (patches, firewalls).  
   - Configuração de Security Groups e NACLs em VPCs.  
   - Gerenciamento de aplicações instaladas.  
4. **Conformidade do Conteúdo**:  
   - Garantir que dados e aplicações atendam a regulamentações (ex: GDPR, HIPAA).  

---

### **Diagrama de Responsabilidades**  
```
AWS: [Hardware] | [Regiões/AZs] | [Hipervisor] | [Serviços Gerenciados (RDS, Lambda)]  
Cliente: [Dados] | [IAM] | [Sistema Operacional] | [Aplicações] | [Firewall/ACLs]  
```

---

### **Casos de Uso para Entender as Divisões**  
1. **EC2**:  
   - **AWS**: Hardware, rede, hipervisor.  
   - **Cliente**: OS, patches, Security Groups, dados na instância.  
2. **S3**:  
   - **AWS**: Durabilidade, disponibilidade do storage.  
   - **Cliente**: Políticas de bucket, cripteração, controle de acesso.  
3. **Lambda**:  
   - **AWS**: Infraestrutura de execução, escalabilidade.  
   - **Cliente**: Código, permissões da função IAM, segurança da aplicação.  

---

### **Principais Perguntas no Exame**  
1. **"Quem é responsável pela criptografia de dados em uma instância EC2?"**  
   - **Resposta**: Cliente (configuração do sistema de arquivos/volume EBS).  
2. **"Quem gerencia patches do sistema operacional em um RDS?"**  
   - **Resposta**: AWS (RDS é um serviço gerenciado).  
3. **"Qual serviço ajuda o cliente a cumprir sua parte no modelo de responsabilidade?"**  
   - **Resposta**: AWS Config (auditoria de configurações), IAM (controle de acesso), KMS (criptografia).  

---

### **Ferramentas AWS para Apoiar o Cliente**  
- **IAM**: Controle de acesso granular.  
- **KMS**: Gerenciamento de chaves de criptografia.  
- **AWS CloudTrail**: Auditoria de atividades na conta.  
- **AWS Config**: Monitoramento de conformidade de recursos.  
- **AWS Shield**: Proteção contra DDoS.  

---

### **Resumo para Memorização**  
| **AWS Cuida**               | **Cliente Cuida**            |  
|-----------------------------|-------------------------------|  
| Infraestrutura física       | Dados e criptografia          |  
| Hipervisor e zonas de disponibilidade | Sistemas operacionais e aplicações |  
| Conformidade da infraestrutura | Controle de acesso (IAM)      |  
| Serviços gerenciados (RDS, Lambda) | Configuração de Security Groups |  

---

### **Dica Final para o Exame**  
- **Foco em "Security IN the Cloud vs. OF the Cloud"**:  
  - Se o serviço é **gerenciado pela AWS** (ex: Lambda, RDS), o cliente tem menos responsabilidades.  
  - Se o serviço é **não gerenciado** (ex: EC2, EBS), o cliente precisa configurar segurança adicional.  
