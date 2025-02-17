---
title: "AWS Step Functions"
---

https://docs.aws.amazon.com/pt_br/step-functions/latest/dg/welcome.html


### **1. Visão Geral do AWS Step Functions**
- **O que é:** Um serviço de orquestração que permite coordenar tarefas distribuídas em workflows.
- **Casos de Uso Comuns:**
  - Automação de pipelines de ETL.
  - Orquestração de microserviços.
  - Gerenciamento de workflows de machine learning.
  - Automação de processos de negócios.

---

### **2. Componentes do AWS Step Functions**
#### **State Machines**
- **Definição:** Representação visual de um workflow, composto por estados (tasks, escolhas, paralelismos, etc.).
- **Estados:**
  - **Task State:** Executa uma tarefa (ex.: invocar uma função Lambda).
  - **Choice State:** Toma decisões com base em condições.
  - **Parallel State:** Executa múltiplas tarefas em paralelo.
  - **Wait State:** Pausa a execução por um tempo definido ou até uma condição ser atendida.
  - **Pass State:** Passa a entrada para a saída sem realizar nenhuma ação.
  - **Fail/Succeed State:** Finaliza o workflow com falha ou sucesso.

#### **Integrações**
- **AWS Lambda:** Para execução de código.
- **Amazon ECS:** Para execução de contêineres.
- **Amazon SNS:** Para notificações.
- **Amazon SQS:** Para filas de mensagens.
- **AWS Glue:** Para tarefas de ETL.

#### **Expressões**
- **Input/Output Processing:** Manipulação de dados de entrada e saída usando expressões JSONPath.
- **Retry/Catch:** Configuração de políticas de repetição e tratamento de erros.

---

### **3. Funcionalidades Principais**
#### **Desempenho**
- **Execuções Rápidas:** Step Functions Express é otimizado para workflows de alta velocidade e curta duração.
- **Escalabilidade:** Escalona automaticamente com base na demanda.

#### **Segurança**
- **IAM:** Controle de acesso usando políticas do IAM.
- **Cifragem:** Dados podem ser cifrados em repouso e em trânsito usando AWS KMS.

#### **Monitoramento**
- **CloudWatch:** Monitora métricas como tempo de execução e status de workflows.
- **Logs:** Armazena logs de execução no CloudWatch Logs.

---

### **4. Melhores Práticas**
#### **Desempenho**
- **Uso de Expressões:** Use expressões JSONPath para manipulação eficiente de dados.
- **Escolha de Estados:** Escolha os estados apropriados para cada tarefa (ex.: Task State para execução de código, Choice State para decisões).

#### **Segurança**
- **IAM:** Use políticas granulares para controlar o acesso ao Step Functions e aos recursos.
- **Cifragem:** Habilite a cifragem para proteger dados sensíveis.

#### **Custos**
- **Execuções:** O Step Functions cobra com base no número de transições de estado.
- **Step Functions Express:** Use para workflows de alta velocidade e curta duração para reduzir custos.

---

### **5. Tópicos Relevantes para o Exame**
- **State Machines:** Entenda como criar e gerenciar state machines.
- **Estados:** Conheça os diferentes tipos de estados e quando usá-los.
- **Integrações:** Como o Step Functions se integra a Lambda, ECS, SNS, SQS e Glue.
- **Segurança:** Cifragem, IAM e monitoramento.
- **Casos de Uso:** Automação de pipelines de ETL, orquestração de microserviços e workflows de machine learning.

---

### **6. Exemplos de Perguntas do Exame**
1. **Qual tipo de estado no AWS Step Functions é usado para executar uma função Lambda?**
   - A) Choice State  
   - B) Task State  
   - C) Parallel State  
   - D) Wait State  
   **Resposta:** B) Task State.

2. **Qual serviço da AWS pode ser usado para monitorar métricas como tempo de execução e status de workflows no AWS Step Functions?**
   - A) AWS CloudTrail  
   - B) Amazon CloudWatch  
   - C) AWS Config  
   - D) AWS Trusted Advisor  
   **Resposta:** B) Amazon CloudWatch.

3. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de workflows no AWS Step Functions?**
   - A) Usar Choice State para todas as tarefas.  
   - B) Usar expressões JSONPath para manipulação eficiente de dados.  
   - C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   - D) Manter workflows em execução 24/7, mesmo quando não estiverem em uso.  
   **Resposta:** B) Usar expressões JSONPath para manipulação eficiente de dados.

4. **Qual serviço da AWS pode ser usado para notificações em workflows no AWS Step Functions?**
   - A) Amazon SNS  
   - B) Amazon SQS  
   - C) AWS Lambda  
   - D) Amazon ECS  
   **Resposta:** A) Amazon SNS.

---

### **7. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie uma state machine que orquestre uma função Lambda e uma tarefa do ECS.
  - Configure um workflow com Choice State para tomar decisões com base em condições.
  - Use Step Functions Express para um workflow de alta velocidade.

---
