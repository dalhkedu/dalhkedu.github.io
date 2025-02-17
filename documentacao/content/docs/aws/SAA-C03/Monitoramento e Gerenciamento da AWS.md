---
title: "Monitoramento"
---

### **1. Amazon CloudWatch**
**O que é**:  
Serviço de monitoramento para coletar métricas, logs e eventos em tempo real de recursos AWS (EC2, S3, Lambda, etc.) e aplicações personalizadas.  

**Uso Padrão**:  
- **Métricas**: Monitorar CPU de EC2, latência de ALB, invocações de Lambda, etc.  
- **Logs**: Coletar logs de aplicações (ex: logs do Apache, NGINX ou containers).  
- **Alertas (Alarms)**: Notificar via SNS quando métricas ultrapassarem limites (ex: CPU > 80%).  
- **Dashboards**: Visualizar métricas em painéis personalizados.  

**Integrações**:  
- **AWS Services**: EC2, Lambda, RDS, ECS, API Gateway.  
- **APIs Customizadas**: Enviar métricas de aplicações via SDK (ex: `PutMetricData`).  
- **Ferramentas Externas**: Grafana (via CloudWatch Data Source), Datadog, Splunk.  

**Ativação Necessária?**  
- **Métricas Básicas**: EC2, EBS, RDS enviam métricas básicas para CloudWatch automaticamente (ex: CPUUtilization).  
- **Métricas Detalhadas**: Requer ativação (ex: métricas de memória de EC2 via *CloudWatch Agent*).  
- **Logs**: É preciso configurar o *CloudWatch Logs Agent* ou usar integrações nativas (ex: Lambda envia logs automaticamente).  

---

### **2. AWS CloudTrail**  
**O que é**:  
Serviço de auditoria que registra todas as **chamadas de API** na conta AWS, incluindo quem fez, o que fez e quando.  

**Uso Padrão**:  
- **Registros de Atividade**: Rastrear criação/exclusão de recursos (ex: quem excluiu um bucket S3).  
- **Conformidade**: Atender a regulamentações como GDPR, PCI DSS.  
- **Detecção de Ameaças**: Identificar atividades suspeitas (ex: login de IPs desconhecidos).  

**Integrações**:  
- **CloudWatch Logs**: Enviar logs do CloudTrail para análise em tempo real.  
- **Amazon S3**: Armazenar logs para auditoria de longo prazo.  
- **AWS Lambda**: Acionar funções para respostas automatizadas (ex: bloquear usuário após falha de autenticação).  

**Ativação Necessária?**  
- **Trail de Eventos de Gerenciamento**: Ativado por padrão nos últimos 90 dias (apenas na região selecionada).  
- **Trail de Eventos de Dados** (ex: operações em objetos S3): Requer configuração manual.  

---

### **3. AWS Config**  
**O que é**:  
Serviço para avaliar, auditar e registrar **configurações de recursos AWS** (ex: regras de Security Groups, criptografia de S3).  

**Uso Padrão**:  
- **Histórico de Configurações**: Verificar como um recurso foi alterado ao longo do tempo.  
- **Regras de Conformidade**: Validar recursos contra políticas (ex: "Todos os buckets S3 devem estar criptografados").  
- **Detecção de Desvios**: Alertar quando um recurso violar regras (ex: Security Group aberto para 0.0.0.0/0).  

**Integrações**:  
- **CloudWatch Events**: Notificar sobre mudanças não autorizadas.  
- **AWS Systems Manager Automation**: Corrigir automaticamente recursos não conformes.  
- **Security Hub**: Centralizar achados de conformidade.  

**Ativação Necessária?**  
- **Não é ativado por padrão**. É necessário habilitar o AWS Config e definir quais recursos serão monitorados.  

---

### **Melhores Práticas e Recomendações AWS**  
1. **Habilite o CloudTrail em Todas as Regiões**:  
   - Crie um *trail* que envie logs para um bucket S3 centralizado.  
   - Use *CloudTrail Insights* para detectar atividades anômalas.  

2. **Monitore Recursos Críticos com CloudWatch**:  
   - Configure métricas detalhadas (ex: memória de EC2, conexões ativas do RDS).  
   - Use *Composite Alarms* para combinar múltiplas métricas em um único alerta.  

3. **Automatize a Conformidade com AWS Config**:  
   - Crie *Config Rules* para políticas como:  
     - `s3-bucket-server-side-encryption-enabled` (S3 criptografado).  
     - `restricted-ssh` (Security Groups não permitem SSH público).  
   - Use *Auto-Remediation* para corrigir automaticamente recursos não conformes.  

4. **Centralize Logs e Métricas**:  
   - Use uma conta central para agregar logs de múltiplas contas AWS (via *Organizations*).  
   - Envie logs do CloudTrail e CloudWatch para um SIEM como **Splunk** ou **Elasticsearch**.  

5. **Custos**:  
   - CloudWatch: Evite métricas personalizadas em alta frequência para reduzir custos.  
   - CloudTrail: Armazene logs no S3 Glacier após um período para economia.  

---

### **Exemplo Prático: Empresa de E-commerce**  
**Cenário**: Uma empresa usa EC2, RDS, S3 e Lambda. Seus requisitos são:  
- Monitorar desempenho em tempo real.  
- Auditoria de acesso a recursos.  
- Garantir que todos os buckets S3 estejam criptografados.  

**Implementação**:  
1. **CloudWatch**:  
   - Métricas: CPU do EC2, latência do ALB, invocações de Lambda.  
   - Logs: Coletar logs da aplicação (ex: erros de pagamento).  
   - Alarmes: Notificar equipe se o uso de CPU do RDS > 90%.  

2. **CloudTrail**:  
   - Trail habilitado em todas as regiões, com logs enviados para um bucket S3 central.  
   - Integração com CloudWatch Logs para alertas em tempo real (ex: alterações em IAM Roles).  

3. **AWS Config**:  
   - Regra `s3-bucket-server-side-encryption-enabled` para verificar criptografia de S3.  
   - Auto-remediação: Se um bucket não criptografado for criado, uma Lambda function o criptografa via KMS.  

4. **Resposta a Incidentes**:  
   - **Cenário**: Um bucket S3 é configurado sem criptografia.  
   - **Fluxo**:  
     - AWS Config detecta a não conformidade.  
     - CloudWatch Events aciona uma Lambda function para aplicar criptografia.  
     - CloudTrail registra a alteração e o reparo.  

---

### **Quando os Serviços São Ativados por Padrão?**  
| **Serviço**       | **Ativação Padrão**                              |  
|--------------------|--------------------------------------------------|  
| **CloudWatch**     | Métricas básicas de EC2, EBS, RDS. Logs requerem configuração. |  
| **CloudTrail**     | Trail de eventos de gerenciamento (90 dias) em uma região. |  
| **AWS Config**     | Não ativado. Requer configuração manual.         |  

---

### **Conclusão**  
CloudWatch, CloudTrail e AWS Config são pilares para monitoramento, auditoria e governança na AWS. Enquanto CloudWatch foca em desempenho operacional, CloudTrail rastreia atividades de API e AWS Config garante conformidade contínua. Para ambientes críticos:  
- **Ative todos os serviços** e integre-os a ferramentas de resposta automatizada.  
- Siga as melhores práticas da AWS para evitar custos inesperados e gaps de segurança.  
