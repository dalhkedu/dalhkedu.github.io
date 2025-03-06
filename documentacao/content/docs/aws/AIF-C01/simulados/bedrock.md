Claro! Aqui está um simulado de múltipla escolha focado no **Amazon Bedrock** e seus domínios de aplicação. As respostas e explicações estão no final.  

---

### **Simulado: Amazon Bedrock**  
**1. Qual é o principal objetivo do Amazon Bedrock?**  
a) Treinar modelos de IA a partir do zero.  
b) Fornecer acesso a modelos de IA generativa pré-treinados e customizáveis.  
c) Substituir totalmente o Amazon SageMaker em projetos de ML.  
d) Armazenar dados estruturados para análise em tempo real.  

**2. Um desenvolvedor precisa criar um chatbot para suporte técnico que utilize documentos internos da empresa para responder perguntas. Qual abordagem no Bedrock é mais adequada?**  
a) Fine-tuning do modelo Titan Text com dados públicos.  
b) Usar RAG (Retrieval-Augmented Generation) integrado ao Amazon Kendra.  
c) Implantar o Stable Diffusion para gerar imagens explicativas.  
d) Utilizar o Claude 3 apenas com prompts estáticos.  

**3. Qual serviço da AWS é integrado ao Bedrock para monitorar o desempenho de modelos em tempo real?**  
a) AWS CloudTrail  
b) Amazon CloudWatch  
c) AWS Config  
d) Amazon QuickSight  

**4. Uma empresa de saúde deseja usar o Bedrock para resumir prontuários médicos, garantindo conformidade com HIPAA. Qual ação é essencial?**  
a) Usar o modelo Stable Diffusion para visualizar dados.  
b) Habilitar criptografia em repouso e configurar políticas de IAM restritivas.  
c) Treinar um novo modelo do zero com dados anônimos.  
d) Utilizar o Amazon Redshift para armazenar os prontuários.  

**5. Qual modelo do Bedrock é mais indicado para geração de imagens realistas a partir de prompts textuais?**  
a) Claude 3  
b) Titan Embeddings  
c) Stable Diffusion  
d) Llama 3  

**6. Para reduzir custos ao usar o Bedrock, qual prática é recomendada?**  
a) Executar modelos 24/7 sem interrupção.  
b) Usar o AWS Budgets para monitorar gastos e definir alertas.  
c) Ignorar a criptografia de dados para reduzir latência.  
d) Utilizar apenas modelos multimodais para todas as tarefas.  

**7. Qual técnica permite adaptar um modelo do Bedrock a termos técnicos específicos de um domínio (ex: jurídico)?**  
a) Usar apenas prompts genéricos.  
b) Aplicar fine-tuning com dados especializados.  
c) Aumentar a quantidade de instâncias EC2.  
d) Desativar o registro em log no CloudWatch.  

**8. Um modelo multimodal como o Claude 3 é capaz de:**  
a) Gerar apenas texto em um único idioma.  
b) Processar entradas de texto e imagem simultaneamente.  
c) Operar sem integração com outros serviços AWS.  
d) Substituir completamente o Amazon Rekognition.  

---

### **Respostas e Explicações**  
1. **b) Fornecer acesso a modelos de IA generativa pré-treinados e customizáveis**  
   - O Bedrock oferece modelos prontos (como Claude e Titan) que podem ser ajustados com fine-tuning ou RAG, sem necessidade de treinar do zero.  

2. **b) Usar RAG (Retrieval-Augmented Generation) integrado ao Amazon Kendra**  
   - O RAG combina a geração de respostas com busca em bases de dados específicas (ex: documentos internos via Kendra), aumentando a precisão do chatbot.  

3. **b) Amazon CloudWatch**  
   - O CloudWatch monitora métricas como latência e uso de recursos em tempo real, essencial para otimizar modelos no Bedrock.  

4. **b) Habilitar criptografia em repouso e configurar políticas de IAM restritivas**  
   - Setores regulamentados (como saúde) exigem criptografia e controle de acesso rigoroso, recursos nativos do Bedrock.  

5. **c) Stable Diffusion**  
   - O Stable Diffusion, da Stability AI, é especializado em gerar imagens a partir de prompts textuais.  

6. **b) Usar o AWS Budgets para monitorar gastos e definir alertas**  
   - O Bedrock segue o modelo "pay-as-you-go", e o AWS Budgets ajuda a evitar custos inesperados.  

7. **b) Aplicar fine-tuning com dados especializados**  
   - O fine-tuning ajusta modelos pré-treinados com dados específicos (ex: jargões jurídicos), melhorando a relevância das respostas.  

8. **b) Processar entradas de texto e imagem simultaneamente**  
   - Modelos multimodais como o Claude 3 aceitam entradas combinadas (ex: imagem + texto) para tarefas como análise de gráficos ou fotos.  

---

Esse simulado abrange desde conceitos básicos até aplicações práticas do Bedrock, alinhado aos domínios de segurança, customização, integração e custos. Para aprofundar, consulte a [documentação oficial](https://aws.amazon.com/bedrock/) e faça laboratórios no AWS Skill Builder! 🧠🔧