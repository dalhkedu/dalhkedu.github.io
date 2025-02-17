---
title: "Simulado: AWS Step Functions"
---

### **Simulado: AWS Step Functions**

#### **1. Qual tipo de estado no AWS Step Functions é usado para executar uma função Lambda?**
A) Choice State  
B) Task State  
C) Parallel State  
D) Wait State  

**Resposta:** B) Task State  
**Explicação:** O Task State é usado para executar tarefas, como invocar uma função Lambda.

---

#### **2. Qual serviço da AWS pode ser usado para monitorar métricas como tempo de execução e status de workflows no AWS Step Functions?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor  

**Resposta:** B) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar o desempenho e a saúde do AWS Step Functions.

---

#### **3. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho de workflows no AWS Step Functions?**
A) Usar Choice State para todas as tarefas.  
B) Usar expressões JSONPath para manipulação eficiente de dados.  
C) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
D) Manter workflows em execução 24/7, mesmo quando não estiverem em uso.  

**Resposta:** B) Usar expressões JSONPath para manipulação eficiente de dados.  
**Explicação:** O uso de expressões JSONPath permite a manipulação eficiente de dados, melhorando o desempenho dos workflows.

---

#### **4. Qual serviço da AWS pode ser usado para notificações em workflows no AWS Step Functions?**
A) Amazon SNS  
B) Amazon SQS  
C) AWS Lambda  
D) Amazon ECS  

**Resposta:** A) Amazon SNS  
**Explicação:** O Amazon SNS pode ser usado para enviar notificações em workflows no AWS Step Functions.

---

#### **5. Qual das seguintes opções é verdadeira sobre o AWS Step Functions?**
A) Ele não suporta a execução de tarefas em paralelo.  
B) Ele permite a orquestração de workflows usando state machines.  
C) Ele não se integra ao AWS Lambda.  
D) Ele não suporta a cifragem de dados em trânsito.  

**Resposta:** B) Ele permite a orquestração de workflows usando state machines.  
**Explicação:** O AWS Step Functions permite a orquestração de workflows usando state machines, que podem incluir tarefas, decisões, paralelismos e mais.

---

#### **6. Qual das seguintes opções é uma vantagem do uso do AWS Step Functions com o AWS Lambda?**
A) Ele permite a execução de código em resposta a eventos.  
B) Ele aumenta o custo de execução de workflows.  
C) Ele não suporta a execução de tarefas em paralelo.  
D) Ele não se integra ao Amazon SNS.  

**Resposta:** A) Ele permite a execução de código em resposta a eventos.  
**Explicação:** A integração com o AWS Lambda permite a execução de código em resposta a eventos, facilitando a automação de tarefas.

---

#### **7. Qual das seguintes opções é uma prática recomendada para reduzir custos no AWS Step Functions?**
A) Usar Step Functions Express para workflows de alta velocidade e curta duração.  
B) Manter workflows em execução 24/7, mesmo quando não estiverem em uso.  
C) Usar Choice State para todas as tarefas.  
D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  

**Resposta:** A) Usar Step Functions Express para workflows de alta velocidade e curta duração.  
**Explicação:** O Step Functions Express é otimizado para workflows de alta velocidade e curta duração, reduzindo custos.

---

#### **8. Qual das seguintes opções é verdadeira sobre a segurança no AWS Step Functions?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O AWS Step Functions integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

#### **9. Qual das seguintes opções é uma limitação do AWS Step Functions?**
A) Ele não suporta a execução de tarefas em paralelo.  
B) Ele tem um tempo de execução máximo de 15 minutos por workflow.  
C) Ele não suporta a integração com o AWS Lambda.  
D) Ele não se integra ao Amazon SNS.  

**Resposta:** B) Ele tem um tempo de execução máximo de 15 minutos por workflow.  
**Explicação:** O AWS Step Functions tem um tempo de execução máximo de 15 minutos por workflow, o que pode ser uma limitação para workflows de longa duração.

---

#### **10. Qual das seguintes opções é uma vantagem do uso do AWS Step Functions com o AWS Glue?**
A) Ele permite a catalogação automática de metadados.  
B) Ele aumenta o custo de execução de workflows.  
C) Ele não suporta a execução de tarefas em paralelo.  
D) Ele não se integra ao Amazon SNS.  

**Resposta:** A) Ele permite a catalogação automática de metadados.  
**Explicação:** A integração com o AWS Glue permite a catalogação automática de metadados, facilitando a descoberta e organização de dados.

---

### **Resumo das Respostas**
1. B) Task State  
2. B) Amazon CloudWatch  
3. B) Usar expressões JSONPath para manipulação eficiente de dados.  
4. A) Amazon SNS  
5. B) Ele permite a orquestração de workflows usando state machines.  
6. A) Ele permite a execução de código em resposta a eventos.  
7. A) Usar Step Functions Express para workflows de alta velocidade e curta duração.  
8. B) Ele usa IAM para controlar o acesso a recursos e dados.  
9. B) Ele tem um tempo de execução máximo de 15 minutos por workflow.  
10. A) Ele permite a catalogação automática de metadados.  

---
