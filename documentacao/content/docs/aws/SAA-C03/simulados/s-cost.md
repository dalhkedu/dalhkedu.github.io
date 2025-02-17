---
title: "Simulado: Design Cost-Optimized Architectures"
---

### **Simulado: Design Cost-Optimized Architectures**  
**Instruções**: Escolha a melhor resposta com base nas práticas recomendadas da AWS. Justifique sua escolha.

---

#### **1. Uma empresa executa uma carga de trabalho batch de processamento de dados todas as noites por 4 horas. Qual estratégia de custo é mais eficiente?**  
a) Usar Reserved Instances (RIs) de 3 anos.  
b) Usar Spot Instances com Auto Scaling.  
c) Usar On-Demand Instances.  
d) Usar Savings Plans para EC2.  

---

#### **2. Qual serviço AWS é mais econômico para armazenar dados acessados uma vez por mês após os primeiros 30 dias?**  
a) S3 Standard  
b) S3 Intelligent-Tiering  
c) S3 Glacier Deep Archive  
d) S3 One Zone-IA  

---

#### **3. Uma aplicação serverless precisa executar uma função por 1 segundo, 500 vezes ao dia. Qual opção é mais econômica?**  
a) AWS Lambda  
b) EC2 t4g.nano (On-Demand)  
c) EC2 Spot Instances  
d) AWS Fargate  

---

#### **4. Qual estratégia reduz custos de um banco de dados RDS MySQL usado apenas em horário comercial (8h/dia)?**  
a) Habilitar Multi-AZ  
b) Usar Reserved Instances com pagamento All Upfront  
c) Parar manualmente a instância fora do horário comercial  
d) Usar RDS Proxy  

---

#### **5. Qual serviço AWS ajuda a identificar instâncias EC2 subutilizadas para redução de custos?**  
a) AWS Cost Explorer  
b) AWS Trusted Advisor  
c) Amazon CloudWatch  
d) AWS Budgets  

---

#### **6. Uma empresa usa 10 instâncias EC2 m5.large 24/7 há 6 meses. Qual estratégia de custo é mais eficiente?**  
a) Migrar para Spot Instances  
b) Comprar Reserved Instances (All Upfront)  
c) Usar Savings Plans para EC2  
d) Continuar com On-Demand  

---

#### **7. Qual classe de armazenamento do S3 é mais econômica para backups retidos por 7 anos com acesso quase inexistente?**  
a) S3 Intelligent-Tiering  
b) S3 Glacier Deep Archive  
c) S3 Standard-IA  
d) S3 One Zone-IA  

---

#### **8. Qual estratégia reduz custos de uma aplicação web com picos de tráfego imprevisíveis?**  
a) Usar Reserved Instances para baseline e On-Demand para picos  
b) Usar EC2 Auto Scaling com Spot Instances e On-Demand  
c) Migrar toda a aplicação para AWS Lambda  
d) Usar Savings Plans para cobrir 100% do uso  

---

#### **9. Qual serviço permite comprar capacidade de computação com desconto em troca de flexibilidade na família de instâncias?**  
a) Reserved Instances  
b) Spot Instances  
c) Savings Plans  
d) Dedicated Hosts  

---

#### **10. Como reduzir custos de um banco de dados Aurora usado apenas para relatórios mensais?**  
a) Habilitar o Aurora Serverless  
b) Usar Multi-AZ  
c) Habilitar o Auto Scaling  
d) Usar Reserved Instances  

---

**Resposta Correta**: **b**  
**Explicação**:  
- **Spot Instances** oferecem até 90% de desconto e são ideais para workloads tolerantes a interrupções, como processamento em lote.  
- **RIs** (opção a) e **Savings Plans** (opção d) são mais adequados para cargas contínuas.  
- **On-Demand** (opção c) é mais caro para uso intermitente. 
 
---

**Resposta Correta**: **b**  
**Explicação**:  
- **S3 Intelligent-Tiering** move automaticamente dados para tiers mais baratos (infrequente/arquivamento) após 30 dias de inatividade.  
- **Glacier Deep Archive** (opção c) é mais barato, mas tem retrieval lento (48 horas), inviável para acesso mensal.  
- **One Zone-IA** (opção d) não é recomendado para dados críticos (armazenamento em apenas uma AZ).  

---

**Resposta Correta**: **a**  
**Explicação**:  
- **Lambda** cobra por execução (US$ 0,20 por 1 milhão de requisições + US$ 0,0000166667/GB-segundo). Custo estimado: ~US$ 0,10/mês.  
- **EC2 t4g.nano** custa ~US$ 3,50/mês, mesmo ocioso.  
- **Fargate** (opção d) tem custo mínimo por tarefa, maior que Lambda.  

---

**Resposta Correta**: **c**  
**Explicação**:  
- Parar a instância fora do horário comercial elimina custos de computação (armazenamento ainda é cobrado).  
- **RIs** (opção b) são menos eficientes se o recurso não estiver em uso 24/7.  
- **Multi-AZ** (opção a) aumenta custos (réplica em outra AZ).  

---

**Resposta Correta**: **b**  
**Explicação**:  
- **Trusted Advisor** fornece recomendações específicas sobre instâncias ociosas ou subutilizadas.  
- **Cost Explorer** (opção a) analisa custos, mas não identifica subutilização diretamente.  
- **CloudWatch** (opção c) monitora métricas, mas não dá recomendações.  

---

**Resposta Correta**: **c**  
**Explicação**:  
- **Savings Plans** oferecem flexibilidade (aplicam-se a qualquer tipo de instância/família) e desconto de até 72%, sem compromisso com RIs específicas.  
- **RIs** (opção b) também são válidas, mas menos flexíveis.  
- **Spot Instances** (opção a) não são ideais para workloads 24/7.  

---

**Resposta Correta**: **b**  
**Explicação**:  
- **Glacier Deep Archive** custa US$ 0,00099/GB/mês, ideal para arquivamento de longo prazo.  
- **Intelligent-Tiering** (opção a) custa mais para dados nunca acessados.  

---

**Resposta Correta**: **b**  
**Explicação**:  
- **Auto Scaling com Spot Instances** reduz custos durante picos, usando On-Demand como fallback.  
- **Lambda** (opção c) pode ser viável, mas depende da arquitetura (nem toda app é serverless).  
- **Savings Plans** (opção d) não são ideais para picos imprevisíveis.  

---

**Resposta Correta**: **c**  
**Explicação**:  
- **Savings Plans** oferecem descontos em troca de compromisso de gasto, com flexibilidade de tipos de instância.  
- **RIs** (opção a) exigem compromisso com instâncias específicas.  

---

**Resposta Correta**: **a**  
**Explicação**:  
- **Aurora Serverless** escala automaticamente para zero quando ocioso, cobrando apenas pelo uso.  
- **RIs** (opção d) são menos eficientes para uso esporádico.  

---

### **Dicas para o Exame**  
1. **Serverless First**: Priorize Lambda, Fargate e Aurora Serverless para cargas variáveis.  
2. **Combine Estratégias**: Use Savings Plans para baseline e Spot Instances para picos.  
3. **Lifecycle Policies**: Automatize a transição de dados para classes de armazenamento mais baratas.  
4. **Trusted Advisor**: Use para identificar recursos subutilizados.  

---
 
