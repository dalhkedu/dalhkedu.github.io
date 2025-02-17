---
title: "AWS Lambda"
---

https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html


### **1. Visão Geral do AWS Lambda**
- **O que é:** Um serviço de computação sem servidor que executa código em resposta a eventos.
- **Casos de Uso Comuns:**
  - Processamento de dados em tempo real.
  - Automação de tarefas de backend.
  - Integração com serviços AWS para criar aplicações serverless.
  - Execução de funções em resposta a eventos como uploads no S3, atualizações no DynamoDB ou mensagens no Kinesis.

---

### **2. Funcionamento do AWS Lambda**
#### **Funções**
- **Definição:** Código (função) que é executado em resposta a eventos.
- **Linguagens Suportadas:** Node.js, Python, Java, C#, Go, Ruby e PowerShell.
- **Tempo de Execução:** Até 15 minutos por execução (configurável).

#### **Eventos e Gatilhos**
- **Gatilhos Comuns:**
  - **Amazon S3:** Executa uma função quando um objeto é criado ou excluído.
  - **Amazon DynamoDB:** Executa uma função quando uma tabela é atualizada.
  - **Amazon Kinesis:** Executa uma função quando novos dados chegam em um stream.
  - **API Gateway:** Executa uma função em resposta a chamadas HTTP.
  - **CloudWatch Events:** Executa uma função em resposta a eventos agendados ou de sistema.

#### **Concorrência e Escalabilidade**
- **Concorrência:** O número de execuções simultâneas de uma função.
- **Escalabilidade:** O AWS Lambda escala automaticamente com base na demanda.

---

### **3. Funcionalidades Principais**
#### **Camadas (Layers)**
- **O que é:** Permite compartilhar código e bibliotecas entre múltiplas funções.
- **Benefícios:** Reduz a duplicação de código e facilita a manutenção.

#### **Ambiente de Execução**
- **Tempo de Execução:** Até 15 minutos por execução (configurável).
- **Memória:** De 128 MB a 10 GB (configurável).
- **Armazenamento Temporário:** Até 512 MB no diretório `/tmp`.

#### **Integrações**
- **Amazon S3:** Para processamento de objetos.
- **Amazon DynamoDB:** Para processamento de atualizações em tabelas.
- **Amazon Kinesis:** Para processamento de dados em tempo real.
- **API Gateway:** Para criar APIs serverless.
- **CloudWatch:** Para monitoramento e logs.

---

### **4. Melhores Práticas**
#### **Desempenho**
- **Tamanho do Pacote:** Mantenha o pacote de implantação pequeno para reduzir o tempo de inicialização.
- **Concorrência:** Ajuste a concorrência para evitar gargalos.
- **Tempo de Execução:** Otimize o código para reduzir o tempo de execução.

#### **Segurança**
- **IAM:** Use políticas do IAM para controlar o acesso a recursos.
- **VPC:** Execute funções em uma VPC para isolamento de rede.
- **Cifragem:** Use AWS KMS para cifrar dados sensíveis.

#### **Custos**
- **Execuções:** O AWS Lambda cobra com base no número de execuções e no tempo de execução.
- **Memória:** Ajuste a memória alocada para otimizar custos e desempenho.

---

### **5. Tópicos Relevantes para o Exame**
- **Gatilhos:** Entenda como configurar e usar gatilhos com S3, DynamoDB, Kinesis e API Gateway.
- **Concorrência:** Saiba como ajustar a concorrência e entender o impacto no desempenho e custos.
- **Segurança:** Controle de acesso com IAM, execução em VPC e cifragem de dados.
- **Integrações:** Como o Lambda se integra a outros serviços AWS.
- **Casos de Uso:** Processamento de dados em tempo real, automação de tarefas e APIs serverless.

---

### **6. Exemplos de Perguntas do Exame**
1. **Qual serviço da AWS pode ser usado para executar código em resposta a eventos como uploads no S3 ou atualizações no DynamoDB?**
   - A) Amazon EC2  
   - B) AWS Lambda  
   - C) Amazon ECS  
   - D) AWS Fargate  
   **Resposta:** B) AWS Lambda.

2. **Qual das seguintes opções é uma vantagem do uso do AWS Lambda?**
   - A) Ele requer o gerenciamento manual de servidores.  
   - B) Ele escala automaticamente com base na demanda.  
   - C) Ele não suporta a execução de código em resposta a eventos.  
   - D) Ele não se integra a outros serviços AWS.  
   **Resposta:** B) Ele escala automaticamente com base na demanda.

3. **Qual das seguintes opções é uma prática recomendada para otimizar o desempenho do AWS Lambda?**
   - A) Aumentar o tempo de execução máximo para 30 minutos.  
   - B) Manter o pacote de implantação pequeno para reduzir o tempo de inicialização.  
   - C) Usar um único gatilho para todas as funções.  
   - D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  
   **Resposta:** B) Manter o pacote de implantação pequeno para reduzir o tempo de inicialização.

4. **Qual serviço da AWS pode ser usado para monitorar métricas e logs do AWS Lambda?**
   - A) AWS CloudTrail  
   - B) Amazon CloudWatch  
   - C) AWS Config  
   - D) AWS Trusted Advisor  
   **Resposta:** B) Amazon CloudWatch.

---

### **7. Prática Recomendada**
- **Laboratórios Práticos:**
  - Crie uma função Lambda que seja acionada por um upload no S3.
  - Configure uma função Lambda para processar dados de um stream do Kinesis.
  - Use o API Gateway para criar uma API serverless com Lambda.

---
