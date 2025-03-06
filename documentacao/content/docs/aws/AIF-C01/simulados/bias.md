Claro! Aqui está um simulado de múltipla escolha sobre **viés (bias)** em IA, alinhado aos domínios de certificações AWS como **AWS Certified Machine Learning – Specialty** e **AWS Certified AI Practitioner**. As respostas e explicações estão no final.  

---

### **Simulado: Viés (Bias) em IA**  
**1. Qual serviço da AWS é usado para detectar e relatar viés em dados e modelos de Machine Learning?**  
a) Amazon Rekognition  
b) Amazon SageMaker Clarify  
c) AWS Lambda  
d) Amazon Forecast  

**2. Um modelo de IA para aprovação de empréstimos está negando mais solicitações de pessoas de um grupo étnico específico. Qual tipo de viés provavelmente está ocorrendo?**  
a) Viés de Implantação  
b) Viés Histórico  
c) Viés de Medição  
d) Viés de Agregação  

**3. Qual métrica é usada pelo SageMaker Clarify para avaliar disparidades entre grupos em um modelo?**  
a) RMSE (Root Mean Square Error)  
b) Disparate Impact Ratio  
c) Precisão (Accuracy)  
d) F1-Score  

**4. Um dataset de treinamento contém 80% de dados de homens e 20% de mulheres. Qual tipo de viés está presente?**  
a) Viés de Confirmação  
b) Viés de Seleção  
c) Viés Algorítmico  
d) Viés de Preconceito Histórico  

**5. Como mitigar viés em um modelo de reconhecimento facial que apresenta baixa precisão para pessoas de pele escura?**  
a) Usar um dataset mais diversificado e balanceado.  
b) Aumentar a quantidade de dados do grupo majoritário.  
c) Ignorar métricas de viés para acelerar o treinamento.  
d) Reduzir a complexidade do modelo.  

**6. Qual prática ajuda a garantir transparência em decisões de IA afetadas por viés?**  
a) Não documentar o processo de treinamento.  
b) Usar o Amazon SageMaker Clarify para gerar relatórios de explicabilidade.  
c) Ocultar as métricas de desempenho do modelo.  
d) Treinar o modelo sem dados históricos.  

**7. Um modelo de recrutamento prioriza currículos de homens para cargos técnicos devido a dados históricos. Qual tipo de viés está envolvido?**  
a) Viés de Medição  
b) Viés de Confirmação  
c) Viés Histórico  
d) Viés de Implantação  

**8. Qual recurso da AWS permite integrar revisão humana em workflows automatizados para reduzir viés?**  
a) Amazon Comprehend  
b) Amazon Augmented AI (A2I)  
c) Amazon Kendra  
d) AWS Glue  

---

### **Respostas e Explicações**  
1. **b) Amazon SageMaker Clarify**  
   - O **SageMaker Clarify** identifica viés em dados e modelos, além de gerar relatórios detalhados.  

2. **b) Viés Histórico**  
   - O viés histórico reflete desigualdades passadas nos dados, como discriminação sistêmica em decisões de crédito.  

3. **b) Disparate Impact Ratio**  
   - Essa métrica compara resultados entre grupos (ex: taxa de aprovação por etnia) para detectar disparidades.  

4. **b) Viés de Seleção**  
   - O dataset desbalanceado sub-representa mulheres, caracterizando viés de seleção.  

5. **a) Usar um dataset mais diversificado e balanceado**  
   - Dados balanceados melhoram a representatividade e reduzem viés em modelos de reconhecimento.  

6. **b) Usar o Amazon SageMaker Clarify para gerar relatórios de explicabilidade**  
   - Relatórios de explicabilidade tornam as decisões do modelo compreensíveis e auditáveis.  

7. **c) Viés Histórico**  
   - O modelo reflete preconceitos históricos presentes nos dados de treinamento (ex: preferência por homens em cargos técnicos).  

8. **b) Amazon Augmented AI (A2I)**  
   - O **A2I** permite que humanos revisem previsões automatizadas, reduzindo erros e viés.  

---

### **Dicas para Certificações**  
- **SageMaker Clarify:** Domine seu uso para detectar viés e gerar relatórios.  
- **Casos de Uso:** Estude exemplos como sistemas de crédito, recrutamento e reconhecimento facial.  
- **Métricas:** Entenda **Disparate Impact Ratio**, **Class Imbalance** e outras métricas de justiça.  
- **Mitigação:** Saiba como balancear dados, usar A2I e ajustar hiperparâmetros.  

Esse simulado abrange cenários comuns de viés em IA e soluções AWS. Pratique com o [SageMaker Clarify](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-detect-bias.html) e revise as [Diretrizes de IA Responsável da AWS](https://aws.amazon.com/machine-learning/responsible-ai/)! 🛡️📊