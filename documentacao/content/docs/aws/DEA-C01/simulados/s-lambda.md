---
title: "Simulado: AWS Lambda"
---

### **Simulado: AWS Lambda**

#### **1. Qual das seguintes opções é verdadeira sobre o tempo de execução máximo de uma função AWS Lambda?**
A) O tempo de execução máximo é de 5 minutos.  
B) O tempo de execução máximo é de 15 minutos.  
C) O tempo de execução máximo é de 30 minutos.  
D) O tempo de execução máximo é de 1 hora.  

---

#### **2. Qual das seguintes opções é uma vantagem do uso do AWS Lambda em comparação com o Amazon EC2?**
A) O AWS Lambda requer o gerenciamento manual de servidores.  
B) O AWS Lambda escala automaticamente com base na demanda.  
C) O AWS Lambda não suporta a execução de código em resposta a eventos.  
D) O AWS Lambda não se integra a outros serviços AWS.  

---

#### **3. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho do AWS Lambda?**
A) Aumentar o tempo de execução máximo para 30 minutos.  
B) Manter o pacote de implantação pequeno para reduzir o tempo de inicialização.  
C) Usar um único gatilho para todas as funções.  
D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  

---

#### **4. Qual serviço da AWS pode ser usado para monitorar métricas e logs do AWS Lambda?**
A) AWS CloudTrail  
B) Amazon CloudWatch  
C) AWS Config  
D) AWS Trusted Advisor  

---

#### **5. Qual das seguintes opções é verdadeira sobre a segurança no AWS Lambda?**
A) Ele não suporta a cifragem de dados em trânsito.  
B) Ele usa IAM para controlar o acesso a recursos e dados.  
C) Ele não permite a execução em VPCs.  
D) Ele não se integra ao AWS Key Management Service (KMS).  

---

#### **6. Qual das seguintes opções é uma limitação do AWS Lambda?**
A) Ele não suporta a execução de código em resposta a eventos.  
B) Ele tem um tempo de execução máximo de 15 minutos.  
C) Ele não se integra a outros serviços AWS.  
D) Ele requer o gerenciamento manual de servidores.  

---

#### **7. Qual das seguintes opções é uma vantagem do uso de camadas (Layers) no AWS Lambda?**
A) Elas permitem compartilhar código e bibliotecas entre múltiplas funções.  
B) Elas aumentam o tempo de execução máximo para 30 minutos.  
C) Elas reduzem o custo de execução das funções.  
D) Elas não suportam a execução em VPCs.  

---

#### **8. Qual das seguintes opções é uma prática recomendada para reduzir custos no AWS Lambda?**
A) Aumentar a memória alocada para todas as funções.  
B) Ajustar a memória alocada com base nas necessidades da função.  
C) Usar um único gatilho para todas as funções.  
D) Desabilitar a cifragem para reduzir a sobrecarga de processamento.  

---

#### **9. Qual das seguintes opções é verdadeira sobre a execução do AWS Lambda em uma VPC?**
A) Ele não suporta a execução em VPCs.  
B) Ele requer a configuração manual de sub-redes e grupos de segurança.  
C) Ele não se integra ao IAM.  
D) Ele não suporta a cifragem de dados.  

---

#### **10. Qual das seguintes opções é uma vantagem do uso do AWS Lambda com o API Gateway?**
A) Ele permite a criação de APIs serverless.  
B) Ele não suporta a execução de código em resposta a eventos HTTP.  
C) Ele requer o gerenciamento manual de servidores.  
D) Ele não se integra a outros serviços AWS.  

---

**Resposta:** B) O tempo de execução máximo é de 15 minutos.  
**Explicação:** O tempo de execução máximo de uma função Lambda é de 15 minutos, configurável até esse limite.

---

**Resposta:** B) O AWS Lambda escala automaticamente com base na demanda.  
**Explicação:** O AWS Lambda é um serviço sem servidor que escala automaticamente, ao contrário do EC2, que requer gerenciamento manual de servidores.

---

**Resposta:** B) Manter o pacote de implantação pequeno para reduzir o tempo de inicialização.  
**Explicação:** Manter o pacote de implantação pequeno ajuda a reduzir o tempo de inicialização, melhorando o desempenho.

---

**Resposta:** B) Amazon CloudWatch  
**Explicação:** O Amazon CloudWatch fornece métricas e logs para monitorar o desempenho e a saúde do AWS Lambda.

---

**Resposta:** B) Ele usa IAM para controlar o acesso a recursos e dados.  
**Explicação:** O AWS Lambda integra-se ao IAM para gerenciar permissões e ao KMS para cifragem de dados.

---

**Resposta:** B) Ele tem um tempo de execução máximo de 15 minutos.  
**Explicação:** O tempo de execução máximo de uma função Lambda é de 15 minutos, o que pode ser uma limitação para tarefas de longa duração.

---

**Resposta:** A) Elas permitem compartilhar código e bibliotecas entre múltiplas funções.  
**Explicação:** As camadas (Layers) permitem compartilhar código e bibliotecas entre múltiplas funções, facilitando a manutenção e reduzindo a duplicação de código.

---

**Resposta:** B) Ajustar a memória alocada com base nas necessidades da função.  
**Explicação:** Ajustar a memória alocada com base nas necessidades da função ajuda a otimizar custos e desempenho.

---

**Resposta:** B) Ele requer a configuração manual de sub-redes e grupos de segurança.  
**Explicação:** A execução do AWS Lambda em uma VPC requer a configuração manual de sub-redes e grupos de segurança para garantir o isolamento de rede.

---

**Resposta:** A) Ele permite a criação de APIs serverless.  
**Explicação:** A integração do AWS Lambda com o API Gateway permite a criação de APIs serverless, que escalam automaticamente com base na demanda.

---

### **Resumo das Respostas**
1. B) O tempo de execução máximo é de 15 minutos.  
2. B) O AWS Lambda escala automaticamente com base na demanda.  
3. B) Manter o pacote de implantação pequeno para reduzir o tempo de inicialização.  
4. B) Amazon CloudWatch  
5. B) Ele usa IAM para controlar o acesso a recursos e dados.  
6. B) Ele tem um tempo de execução máximo de 15 minutos.  
7. A) Elas permitem compartilhar código e bibliotecas entre múltiplas funções.  
8. B) Ajustar a memória alocada com base nas necessidades da função.  
9. B) Ele requer a configuração manual de sub-redes e grupos de segurança.  
10. A) Ele permite a criação de APIs serverless.  

---
