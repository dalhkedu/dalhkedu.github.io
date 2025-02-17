### **Simulado: AWS Well-Architected Framework, Sustentabilidade e Machine Learning (Nível Difícil)**  
**Instruções**: Escolha a melhor resposta com base nas práticas recomendadas da AWS. Justifique sua escolha.

---

#### **1. Uma empresa deseja reduzir custos operacionais e impacto ambiental de uma aplicação que processa dados em lote apenas 3 horas por dia. Qual estratégia atende aos pilares de "Otimização de Custos" e "Sustentabilidade"?**  
a) Usar instâncias EC2 On-Demand e desligá-las manualmente após o processamento.  
b) Usar instâncias EC2 Spot com Auto Scaling para escalar a zero quando ocioso.  
c) Migrar para AWS Lambda com triggers agendados pelo EventBridge.  
d) Usar Amazon ECS Fargate com tarefas agendadas.  

**Resposta Correta**: **c**  
**Explicação**:  
- **Lambda** é serverless, cobra apenas pelo tempo de execução (reduz custos) e não requer provisionamento contínuo (menos energia).  
- **EventBridge** agenda a execução sem intervenção manual.  
- As opções **b** e **d** envolvem recursos provisionados (EC2 Spot/Fargate), que consomem energia mesmo quando ociosos.  
- A opção **a** é ineficiente e propensa a erros humanos.  

---

#### **2. Qual prática do pilar "Excelência Operacional" é crítica para garantir a recuperação de backups de um banco de dados RDS em caso de falha humana?**  
a) Habilitar o Multi-AZ para alta disponibilidade.  
b) Automatizar a rotação de chaves do KMS.  
c) Definir políticas de lifecycle para snapshots no AWS Backup.  
d) Usar IAM para restringir acesso ao console AWS.  

**Resposta Correta**: **c**  
**Explicação**:  
- **Lifecycle policies** automatizam a retenção e exclusão de backups, garantindo recuperação confiável.  
- A opção **a** é do pilar "Confiabilidade".  
- A opção **b** relaciona-se à segurança.  
- A opção **d** é do pilar "Segurança".  

---

#### **3. Um cientista de dados precisa criar um modelo de ML para classificação de texto sem escrever código. Qual serviço AWS é mais adequado?**  
a) Amazon SageMaker Autopilot  
b) Amazon Comprehend  
c) AWS Lambda  
d) Amazon Rekognition  

**Resposta Correta**: **a**  
**Explicação**:  
- **SageMaker Autopilot** automatiza a criação de modelos de ML (incluindo pré-processamento e treinamento) sem código.  
- **Comprehend** (opção b) é um serviço de NLP pré-treinado, não personalizável.  
- **Rekognition** (opção d) é para visão computacional.  
- **Lambda** (opção c) não é focado em ML.  

---

#### **4. Qual prática do pilar "Segurança" é essencial ao usar SageMaker para treinar modelos com dados sensíveis?**  
a) Habilitar o endpoint do SageMaker em uma VPC privada.  
b) Usar instâncias Spot para reduzir custos de treinamento.  
c) Habilitar o Auto Scaling no endpoint de inferência.  
d) Armazenar dados de treinamento no S3 Standard-IA.  

**Resposta Correta**: **a**  
**Explicação**:  
- Isolar o ambiente de treinamento em uma **VPC privada** protege dados sensíveis de acesso não autorizado.  
- As opções **b** e **c** são relacionadas a custos e performance.  
- A opção **d** não garante segurança (apenas custo de armazenamento).  

---

#### **5. Qual serviço AWS ajuda a reduzir a pegada de carbono de uma aplicação que roda 24/7 em instâncias EC2?**  
a) AWS Compute Optimizer  
b) AWS Trusted Advisor  
c) Amazon SageMaker  
d) AWS Snowball  

**Resposta Correta**: **a**  
**Explicação**:  
- **AWS Compute Optimizer** recomenda tipos de instância EC2 mais eficientes (ex: instâncias Graviton), reduzindo consumo energético.  
- **Trusted Advisor** (opção b) sugere otimizações gerais, não focadas em sustentabilidade.  
- **SageMaker** (opção c) é para ML.  
- **Snowball** (opção d) é para transferência de dados offline.  

---

#### **6. Qual estratégia do pilar "Confiabilidade" é recomendada para garantir que uma aplicação baseada em Lambda continue operando durante falhas regionais?**  
a) Habilitar o versionamento de funções Lambda.  
b) Implantar funções Lambda em múltiplas regiões e usar Route 53 Failover.  
c) Aumentar a memória alocada para cada função Lambda.  
d) Usar provisioned concurrency para reduzir cold starts.  

**Resposta Correta**: **b**  
**Explicação**:  
- **Multi-region deployment + Route 53 Failover** garante HA/DR.  
- A opção **d** melhora performance, não confiabilidade regional.  
- As opções **a** e **c** não tratam de resiliência geográfica.  

---

#### **7. Uma empresa quer substituir um modelo de ML pré-treinado por um personalizado, mantendo baixo custo e escalabilidade. Qual serviço AWS é mais adequado?**  
a) Amazon Rekognition  
b) Amazon SageMaker JumpStart  
c) AWS DeepRacer  
d) Amazon Transcribe  

**Resposta Correta**: **b**  
**Explicação**:  
- **SageMaker JumpStart** oferece modelos pré-treinados personalizáveis com infraestrutura gerenciada.  
- **Rekognition** e **Transcribe** (opções a/d) são serviços de ML pré-treinados sem personalização.  
- **DeepRacer** (opção c) é para reinforcement learning.  

---

#### **8. Qual prática do pilar "Performance Efficiency" é recomendada para uma aplicação que processa grandes volumes de dados em tempo real?**  
a) Usar instâncias EC2 de propósito geral (t3).  
b) Armazenar dados em S3 Intelligent-Tiering.  
c) Processar streams com Amazon Kinesis Data Analytics.  
d) Habilitar o AWS Shield Advanced.  

**Resposta Correta**: **c**  
**Explicação**:  
- **Kinesis Data Analytics** é otimizado para processamento de streams em tempo real.  
- As opções **a** e **b** não são específicas para cargas de tempo real.  
- A opção **d** é para segurança contra DDoS.  

---

### **Dicas para o Exame**  
1. **Well-Architected Framework**:  
   - Associe práticas como **Multi-AZ** → Confiabilidade, **Lifecycle Policies** → Excelência Operacional.  
2. **Sustentabilidade**:  
   - Priorize **serverless (Lambda)**, **instâncias eficientes (Graviton)**, e **regiões com energia renovável**.  
3. **SageMaker**:  
   - Diferencie **Autopilot** (AutoML), **Data Wrangler** (preparação de dados), e **Endpoints** (deploy de modelos).  

---

### **Conclusão**  
Este simulado reflete a complexidade do exame SAA-C03, combinando múltiplos conceitos em cenários realistas. Pratique no **AWS Free Tier** e revise os **Whitepapers AWS** para consolidar seu conhecimento! 🚀