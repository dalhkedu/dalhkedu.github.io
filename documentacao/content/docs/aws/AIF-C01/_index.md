---
bookCollapseSection: true
weight: 20
title: "AIF-C01"
---

### **Resumo do Guia do Exame AWS Certified AI Practitioner (AIF-C01)**

#### **Visão Geral do Exame**

- **Objetivo:** Validar conhecimentos em IA/ML, IA generativa e serviços AWS relacionados, com foco em aplicações práticas e responsáveis.
- **Público-Alvo:** Profissionais com até 6 meses de experiência em IA/ML na AWS, que utilizam (mas não necessariamente desenvolvem) soluções de IA.
- **Formato:** 50 questões (múltipla escolha, múltipla resposta, estudo de caso, etc.), pontuação de 100 a 1000, nota mínima 700.

---

### **Domínios do Exame e Ponderações**

| **Domínio** | **Peso** | **Tópicos Principais** |
|-------------|----------|------------------------|
| **1. Fundamentos de IA e ML** | 20% | [Conceitos básicos de IA/ML](https://docs.aws.amazon.com/pt_br/whitepapers/latest/aws-overview/machine-learning.html), tipos de dados, [ciclo de vida de ML](https://unite.ai/pt/an%C3%A1lise-completa-do-ciclo-de-vida-de-desenvolvimento-de-IA-em-2023/), serviços AWS (SageMaker, Transcribe, Lex, etc.). |
| **2. Fundamentos de IA Generativa** | 24% | Conceitos de IA generativa ([LLMs](https://blog.dsacademy.com.br/o-que-sao-large-language-models-llms/), [tokens](https://digitra.com/pt/article/tokens-IA-que-sao-como-funcionam/), [RAG](https://www.alura.com.br/artigos/o-que-e-rag)), casos de uso, serviços AWS (Bedrock, SageMaker JumpStart, Amazon Q). |
| **3. Aplicações de Modelos de Base** | 28% | Seleção de modelos, [engenharia de prompts]((https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/what-is-prompt-engineering.html), [ajuste fino](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/jumpstart-fine-tune.html#:~:text=O%20ajuste%20fino%20treina%20um%20modelo%20pr%C3%A9-treinado%20em,de%20dados%20menores%20e%20menos%20tempo%20de%20treinamento.), avaliação de desempenho. |
| **4. Diretrizes de IA Responsável** | 14% | Viés, transparência, ferramentas de mitigação (SageMaker Clarify, A2I), conformidade ética. |
| **5. Segurança, Conformidade e Governança** | 14% | Proteção de dados, criptografia (KMS), conformidade regulatória (GDPR, ISO), serviços AWS (IAM, CloudTrail). |

---

### **Serviços AWS Dentro do Escopo**

| **Categoria** | **Serviços Relevantes** |
|---------------|-------------------------|
| **Machine Learning** | [Amazon SageMaker](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/whatis.html), [Bedrock](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/what-is-bedrock.html), [Comprehend](https://docs.aws.amazon.com/pt_br/comprehend/latest/dg/what-is.html), [Lex](https://docs.aws.amazon.com/pt_br/lex/latest/dg/what-is.html), [Polly](https://docs.aws.amazon.com/pt_br/polly/?id=docs_gateway), [Transcribe](https://aws.amazon.com/pt/transcribe/), [Textract](https://docs.aws.amazon.com/pt_br/textract/latest/dg/what-is.html), [Rekognition](https://docs.aws.amazon.com/pt_br/rekognition/latest/dg/what-is.html), [Q](https://aws.amazon.com/pt/q/business/), [Personalize](https://docs.aws.amazon.com/pt_br/personalize/latest/dg/what-is-personalize.html), [Kendra](https://docs.aws.amazon.com/pt_br/kendra/latest/dg/what-is-kendra.html), [Mechanical Turk](https://docs.aws.amazon.com/pt_br/AWSMechTurk/latest/AWSMechanicalTurkRequester/WhatIs.html), [Augmented AI](https://docs.aws.amazon.com/pt_br/augmented-ai/), [DeepRacer](https://docs.aws.amazon.com/pt_br/deepracer/latest/developerguide/what-is-deepracer.html), [Forecast](https://docs.aws.amazon.com/pt_br/forecast/latest/dg/what-is-forecast.html), [Translate](https://docs.aws.amazon.com/pt_br/translate/latest/dg/what-is.html) |
| **Segurança** | IAM, KMS, [Macie](https://docs.aws.amazon.com/pt_br/macie/latest/user/what-is-macie.html), [CloudTrail](https://docs.aws.amazon.com/pt_br/awscloudtrail/latest/userguide/cloudtrail-user-guide.html), [Audit Manager](https://docs.aws.amazon.com/pt_br/audit-manager/latest/userguide/what-is.html). |
| **Armazenamento** | Amazon S3, Glacier. |
| **Analytics** | [QuickSight](https://docs.aws.amazon.com/pt_br/quicksight/latest/user/welcome.html), [Glue](https://docs.aws.amazon.com/pt_br/glue/latest/dg/what-is-glue.html), [Redshift](https://docs.aws.amazon.com/pt_br/redshift/latest/mgmt/welcome.html). |
| **Banco de Dados** | Amazon RDS, DynamoDB, [OpenSearch](https://docs.aws.amazon.com/pt_br/opensearch-service/latest/developerguide/what-is.html). |

---

### **Pontos Importantes:**

[Impedir conteúdo prejudicial em modelos usando o Amazon Bedrock Guardrails](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/guardrails.html) \
[Data collection](https://docs.aws.amazon.com/pt_br/wellarchitected/latest/machine-learning-lens/data-collection.html) \
[ML lifecycle phase – Monitoring](https://docs.aws.amazon.com/pt_br/wellarchitected/latest/machine-learning-lens/ml-lifecycle-phase-monitoring.html) \
[Feature engineering](https://docs.aws.amazon.com/pt_br/wellarchitected/latest/machine-learning-lens/feature-engineering.html) \
[Model evaluation](https://docs.aws.amazon.com/pt_br/wellarchitected/latest/machine-learning-lens/model-evaluation.html) \
[Model training and tuning](https://docs.aws.amazon.com/pt_br/wellarchitected/latest/machine-learning-lens/model-training-and-tuning.html) \
[Vocabulários personalizados](https://docs.aws.amazon.com/pt_br/transcribe/latest/dg/custom-vocabulary.html) \
[Identificação de idioma com trabalhos de transcrição em lote](https://docs.aws.amazon.com/pt_br/transcribe/latest/dg/lang-id-batch.html) \
[Classificar imagens](https://docs.aws.amazon.com/pt_br/rekognition/latest/customlabels-dg/tutorial-classification.html) \
[Foundational AI capabilities](https://docs.aws.amazon.com/pt_br/whitepapers/latest/aws-caf-for-ai/foundational-ai-capabilities.html) \
[Engenharia rápida para modelos de base](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/jumpstart-foundation-models-customize-prompt-engineering.html) \
[Terminologia básica](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/key-definitions.html) \
[Modelos da Amazon SageMaker JumpStart Foundation](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/jumpstart-foundation-models.html) \
[O que é RAG (Retrieval-Augmented Generation)?](https://aws.amazon.com/pt/what-is/retrieval-augmented-generation/) \
[O que é um prompt?](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/what-is-a-prompt.html) \
[Conceitos de engenharia de prompts](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/prompt-engineering-guidelines.html) \
[Personalizar o modelo para melhorar a performance para o caso de uso](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/custom-models.html) \
[Implantar modelos para inferência](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/deploy-model.html) \
[O que é overfitting?](https://aws.amazon.com/pt/what-is/overfitting/) \
[Best practices to build generative AI applications on AWS](https://aws.amazon.com/pt/blogs/machine-learning/best-practices-to-build-generative-ai-applications-on-aws/) \
[Métricas para ajustar modelos de linguagem grandes no Autopilot](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/autopilot-llms-finetuning-metrics.html) \
[Modelos de base e hiperparâmetros para ajuste](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/jumpstart-foundation-models-fine-tuning.html) \
[Ajustar um grande modelo de linguagem (LLM) usando prompts rápidos](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/jumpstart-foundation-models-fine-tuning-instruction-based.html) \
[O que é aprendizado por reforço?](https://aws.amazon.com/pt/what-is/reinforcement-learning/) \
[Métricas e validação](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/autopilot-metrics-validation.html) \
[Monitore API chamadas do Amazon Bedrock usando CloudTrail](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/logging-using-cloudtrail.html) \
[Implantar modelos para inferência](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/deploy-model.html#deploy-model-options) /
[Cartões SageMaker modelo da Amazon](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/model-cards.html) \
[Gerente de SageMaker funções da Amazon](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/role-manager.html) \
[Painel de SageMaker modelos da Amazon](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/model-dashboard.html) \
[Monitoramento da qualidade de dados e modelos com o Amazon SageMaker Model Monitor](https://docs.aws.amazon.com/pt_br/sagemaker/latest/dg/model-monitor.html)

#### Outros
[Amazon Inspector](https://docs.aws.amazon.com/pt_br/inspector/latest/user/what-is-inspector.html) \
[AWS Trusted Advisor](https://docs.aws.amazon.com/pt_br/awssupport/latest/user/trusted-advisor.html) \
[AWS Artifact](https://docs.aws.amazon.com/pt_br/artifact/latest/ug/what-is-aws-artifact.html)


---

### **Principais Tópicos por Domínio**

#### **Domínio 1: Fundamentos de IA e ML**

- **Conceitos:** IA vs. ML vs. Deep Learning, tipos de aprendizado (supervisionado, não supervisionado, reforço).
- **Serviços-Chave:** SageMaker (Data Wrangler, Model Monitor), Transcribe (transcrição), Lex (chatbots), Polly (text-to-speech).
- **Casos de Uso:** Visão computacional, [NLP](https://aws.amazon.com/pt/what-is/nlp/), sistemas de recomendação.

#### **Domínio 2: IA Generativa**

- **Conceitos:** Modelos de base (LLMs), engenharia de prompts, RAG (Retrieval-Augmented Generation).
- **Serviços-Chave:** Bedrock (acesso a modelos como Claude, Titan), SageMaker JumpStart (modelos pré-treinados).
- **Aplicações:** Geração de conteúdo, chatbots, tradução, código.

#### **Domínio 3: Aplicações de Modelos de Base**

- **Seleção de Modelos:** Critérios (custo, latência, modalidade).
- **Engenharia de Prompts:** [Técnicas](https://aws.amazon.com/pt/blogs/machine-learning/zero-shot-and-few-shot-prompting-for-the-bloomz-176b-foundation-model-with-the-simplified-amazon-sagemaker-jumpstart-sdk/) (zero-shot, few-shot), [riscos](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/prompt-injection.html) (injeção de prompt).
- **Ajuste Fino:** Métodos (transfer learning, RLHF) e preparação de dados.

#### **Domínio 4: IA Responsável**

- **Mitigação de Viés:** SageMaker Clarify (análise de viés), A2I (revisão humana).
- **Transparência:** Model Cards (documentação de modelos), explicações de decisões.

#### **Domínio 5: Segurança e Conformidade**

- **Proteção de Dados:** Criptografia (KMS), IAM (controle de acesso).
- **Conformidade:** AWS Audit Manager, CloudTrail (logs), GDPR, ISO.

---

### **Dicas de Preparação**

1. **Domine os Serviços-Chave:**
   - **SageMaker:** Entenda o ciclo de vida de ML (treinamento, implantação, monitoramento).
   - **Bedrock:** Saiba usar RAG e modelos generativos.
   - **Transcribe/Textract:** Aplique em casos de processamento de áudio e documentos.

2. **IA Generativa:**
   - Estude técnicas de engenharia de prompts e ajuste fino.
   - Pratique com o **Bedrock Playground** para experimentar modelos.

3. **IA Responsável:**
   - Use **SageMaker Clarify** para detectar viés.
   - Entenda políticas de privacidade e conformidade (ex: GDPR).

4. **Segurança:**
   - Configure políticas de IAM e criptografia com **KMS**.
   - Revise logs com **CloudTrail**.

5. **Simulados e Laboratórios:**
   - Utilize o **AWS Skill Builder** para treinar com laboratórios práticos.
   - Resolva questões de múltipla escolha focadas em casos de uso reais.

---

### **Exemplo de Questão**

**Domínio 3 (Aplicações de Modelos de Base):**  
*"Qual técnica permite enriquecer respostas de IA generativa com dados específicos de uma base de conhecimento?"*  
**a)** Aprendizado por reforço  
**b)** RAG (Retrieval-Augmented Generation)  
**c)** Ajuste fino  
**d)** Zero-shot learning  

**Resposta Correta:** **b) RAG**.  
**Explicação:** O RAG combina recuperação de dados (ex: Amazon Kendra) com geração de respostas para contextualizar prompts.

---

### **Recursos Recomendados**

- **Documentação AWS:** [Amazon Bedrock](https://aws.amazon.com/bedrock/), [SageMaker](https://aws.amazon.com/sagemaker/).
- **Treinamentos:** Cursos no AWS Skill Builder (ex: "Generative AI with Large Language Models").
- **Laboratórios Práticos:** Experimente o **Bedrock Playground** e o **SageMaker Studio**.

Bons estudos! 🚀🔍
