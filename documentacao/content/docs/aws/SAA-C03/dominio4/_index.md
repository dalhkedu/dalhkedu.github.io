---
title: "Domínio 4: Projetar arquiteturas econômicas"
---

# Domínio 4: Projetar arquiteturas econômicas

### **1. Estratégias de Redução de Custos**  
#### **Reserved Instances (RIs)**  
**O que é**:  
- Compromisso de uso de recursos (ex: EC2, RDS) por 1 ou 3 anos, com descontos de até 72% comparado ao modelo **On-Demand**.  
- **Tipos de Pagamento**:  
  - **All Upfront**: Desconto máximo (pagamento total antecipado).  
  - **Partial Upfront**: Pagamento parcial antecipado + mensal.  
  - **No Upfront**: Pagamento mensal (menor desconto).  

**Quando usar**:  
- Workloads previsíveis e de longo prazo (ex: servidores de banco de dados, aplicações 24/7).  

**Exemplo Prático**:  
- **Cenário**: Uma empresa usa 10 instâncias EC2 **m5.large** 24/7.  
  - **Economia**: Comprar 10 RIs de 3 anos (All Upfront) reduz custos em ~60%.  

**Possível Pergunta no Exame**:  
*"Qual opção oferece o maior desconto para instâncias EC2 com uso contínuo?"*  
**Resposta**: **Reserved Instances (All Upfront)**.  

---

#### **Spot Instances**  
**O que é**:  
- Instâncias EC2 com custo até 90% menor que On-Demand, mas podem ser interrompidas com aviso de 2 minutos.  

**Quando usar**:  
- Workloads tolerantes a falhas: batch processing, CI/CD, renderização.  
- **Estratégias**:  
  - Usar múltiplas AZs e tipos de instâncias para reduzir risco de interrupção.  

**Exemplo Prático**:  
- **Cenário**: Processamento de dados noturno (6 horas/dia).  
  - **Economia**: Usar Spot Instances reduz custos em 70% comparado a On-Demand.  

**Possível Pergunta no Exame**:  
*"Qual serviço é ideal para workloads de processamento em lote que podem ser interrompidos?"*  
**Resposta**: **Spot Instances**.  

---

#### **AWS Cost Explorer**  
**O que é**:  
- Ferramenta para analisar custos e uso de recursos, identificar tendências e otimizar gastos.  

**Funcionalidades**:  
- Visualizar custos por serviço, região, tags.  
- Prever custos futuros com base no uso histórico.  
- Identificar recursos subutilizados (ex: instâncias EC2 ociosas).  

**Exemplo Prático**:  
- **Cenário**: Custos altos de EC2.  
  - **Ação**: Usar o Cost Explorer para identificar instâncias com <10% de uso de CPU e redimensioná-las.  

---

### **2. Seleção de Serviços Econômicos**  
#### **Amazon S3 Intelligent-Tiering**  
**O que é**:  
- Classe de armazenamento que move objetos automaticamente entre tiers (frequente, infrequente, arquivamento) com base no acesso.  
- **Custo**:  
  - US$ 0,023/GB (frequente) → US$ 0,0125/GB (arquivamento instantâneo).  

**Quando usar**:  
- Dados com padrões de acesso imprevisíveis (ex: logs, backups).  

**Exemplo Prático**:  
- **Cenário**: Armazenar logs de aplicação acessados apenas nos primeiros 30 dias.  
  - **Economia**: Intelligent-Tiering move dados para tiers mais baratos automaticamente.  

**Possível Pergunta no Exame**:  
*"Qual classe do S3 é mais econômica para dados com acesso imprevisível?"*  
**Resposta**: **S3 Intelligent-Tiering**.  

---

#### **AWS Lambda vs. EC2**  
**Comparação**:  
| **Critério**         | **Lambda**                                  | **EC2**                                      |  
|-----------------------|---------------------------------------------|----------------------------------------------|  
| **Custo**             | Pago por execução (milissegundos).          | Pago por hora, mesmo ocioso.                 |  
| **Uso Ideal**         | Workloads esporádicas (ex: APIs, eventos).  | Workloads contínuas (ex: servidores web 24/7). |  

**Exemplo Prático**:  
- **Cenário**: Processar uploads de arquivos no S3 (1.000 execuções/dia, 1s cada).  
  - **Economia**: Lambda custa ~US$ 0,20/mês vs. EC2 t4g.nano (US$ 3,50/mês).  

**Possível Pergunta no Exame**:  
*"Qual serviço é mais econômico para uma função executada 10 vezes ao dia?"*  
**Resposta**: **Lambda**.  

---

### **3. Outras Estratégias de Otimização**  
#### **Right-Sizing**  
- Redimensionar recursos para evitar superprovisionamento:  
  - **EC2**: Usar tipos de instância adequados (ex: trocar **m5.xlarge** por **m5.large**).  
  - **EBS**: Escolher volume **gp3** em vez de **io2** para workloads não críticos.  

**Exemplo**:  
- **Cenário**: Instância EC2 com 10% de uso de CPU e 20% de memória.  
  - **Ação**: Migrar para uma instância menor (ex: **t3.micro**).  

---

#### **Lifecycle Policies**  
- Automatizar transição e expiração de dados:  
  - **S3**: Mover dados para S3 Glacier após 90 dias.  
  - **EBS Snapshots**: Excluir snapshots antigos automaticamente.  

**Exemplo Prático**:  
- **Cenário**: Backups diários de RDS retidos por 30 dias.  
  - **Ação**: Configurar uma política para excluir snapshots com mais de 30 dias.  

---

#### **AWS Trusted Advisor**  
**O que é**:  
- Ferramenta que analisa sua conta e fornece recomendações de segurança, performance e custo.  

**Recomendações de Custo**:  
- Identificar instâncias EC2 ociosas.  
- Alertar sobre RIs não utilizadas.  
- Sugerir a exclusão de volumes EBS não anexados.  

**Exemplo Prático**:  
- **Cenário**: Trusted Advisor identifica 5 volumes EBS não utilizados (US$ 50/mês).  
  - **Economia**: Excluir volumes → economia de US$ 600/ano.  

---

### **Exemplos de Arquiteturas Otimizadas**  
#### **Aplicação Web de Baixo Custo**  
- **Computação**: EC2 Spot Instances para backend + Auto Scaling.  
- **Armazenamento**: S3 Intelligent-Tiering para uploads de usuários.  
- **Banco de Dados**: Aurora Serverless (pago por uso).  
- **Monitoramento**: AWS Cost Explorer para análise mensal.  

---

### **Questões Típicas no Exame**  
1. **Questão**:  
   *"Qual estratégia reduz custos para uma aplicação com uso esporádico de processamento de imagens?"*  
   **Opções**:  
   a) Usar EC2 Reserved Instances.  
   b) Usar AWS Lambda.  
   c) Usar EC2 On-Demand.  
   **Resposta**: **b** (Lambda cobra apenas pelo tempo de execução).  

2. **Questão**:  
   *"Como reduzir custos de armazenamento para dados raramente acessados após 6 meses?"*  
   **Opções**:  
   a) S3 Standard.  
   b) S3 Intelligent-Tiering.  
   c) S3 Glacier Deep Archive.  
   **Resposta**: **c** (custo mais baixo para arquivamento de longo prazo).  

---

### **Melhores Práticas para o Exame**  
- **Priorize Serverless**: Lambda, Aurora Serverless e Fargate são econômicos para cargas variáveis.  
- **Combine RIs e Spot Instances**: Use RIs para baseline e Spot para cargas variáveis.  
- **Monitore Custos**: Use Cost Explorer e Trusted Advisor para auditorias regulares.  

---

### **Conclusão**  
Para dominar **Design Cost-Optimized Architectures**:  
- Entenda o trade-off entre **custos fixos vs. variáveis** (RIs vs. Spot/Lambda).  
- Automatize otimizações com **Lifecycle Policies** e **Cost Explorer**.  
- Pratique cenários reais no **AWS Free Tier** (ex: comparar custos de EC2 vs. Lambda).  


[Práticas recomendadas de arquitetura para otimização de custos](https://aws.amazon.com/architecture/cost-optimization/?cards-all.sort-by=item.additionalFields.sortDate&cards-all.sort-order=desc&awsf.content-type=*all&awsf.methodology=*all) \
[Cost Optimization](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.pillar.costOptimization.en.html) \
[Otimização de custos da AWS](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/aws-cost-optimization.html) \
[Ferramentas da AWS para relatórios e otimização de custos](https://docs.aws.amazon.com/whitepapers/latest/cost-optimization-laying-the-foundation/reporting-cost-optimization-tools.html) \
[Automatizar backups com o Amazon Data Lifecycle Manager](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/snapshot-lifecycle.html) \
[Definição de preço do Amazon EC2](https://aws.amazon.com/ec2/pricing/) \
[Recursos economicamente eficientes](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/cost-effective-resources.html)