---
title: "Instâncias EC2"
---

### **Amazon EC2 (Elastic Compute Cloud)**
**O que é**:  
O EC2 é um serviço de computação em nuvem que fornece máquinas virtuais (instâncias) escaláveis, com controle total sobre o sistema operacional, rede, armazenamento e configurações de segurança. É ideal para aplicações que exigem controle granular e personalização.

#### **Características Principais**:
- **Flexibilidade**: Escolha de tipos de instância (CPU, RAM, GPU), sistemas operacionais (Linux, Windows) e configurações de rede.
- **Escalabilidade**: Auto Scaling Groups para ajustar a capacidade conforme a demanda.
- **Modelo de Preço**: Sob demanda (On-Demand), Reserved Instances (economia de longo prazo), Spot Instances (custos reduzidos para workloads tolerantes a interrupções).
- **Casos de Uso**:
  - Aplicações monolíticas tradicionais (ex: ERP, sistemas legados).
  - Servidores web personalizados (ex: Apache, Nginx).
  - Workloads de longa duração (ex: bancos de dados, servidores de aplicação).
  - Ambientes que exigem acesso root ou configurações específicas (ex: kernels customizados).

---

### **Comparação EC2 vs. Outros Serviços**

#### **1. EC2 vs. AWS Lambda**
| **Critério**            | **EC2**                                      | **AWS Lambda**                                  |
|-------------------------|----------------------------------------------|-------------------------------------------------|
| **Modelo de Execução**   | Servidores persistentes (sempre ativos).     | Serverless (execução sob demanda, sem servidores gerenciados). |
| **Escalonamento**        | Manual ou via Auto Scaling (minutos).        | Automático e instantâneo (milissegundos).       |
| **Custo**                | Cobrança por hora/segundo (instância ativa). | Cobrança por solicitação e tempo de execução (milissegundos). |
| **Tempo de Execução**    | Adequado para workloads contínuos.           | Limitado a 15 minutos por execução (15 GB de memória máxima). |
| **Controle**             | Total controle sobre o ambiente.             | Abstração completa da infraestrutura.           |

**Melhor Escolha**:  
- **EC2**: Workloads estáveis, longos processos (ex: servidores web, bancos de dados).  
- **Lambda**: Funções event-driven (ex: processamento de arquivos S3, APIs backend), tarefas de curta duração (ex: transformação de dados).  

---

#### **2. EC2 vs. Amazon ECS (Elastic Container Service)**
| **Critério**            | **EC2**                                      | **Amazon ECS**                                  |
|-------------------------|----------------------------------------------|-------------------------------------------------|
| **Abstração**            | Máquinas virtuais (gerenciamento manual).    | Orquestração de containers Docker (gerenciamento simplificado). |
| **Escalonamento**        | Escalonamento de instâncias EC2.             | Escalonamento de containers (tasks/services).   |
| **Casos de Uso**         | Aplicações não containerizadas.              | Microserviços, CI/CD pipelines, ambientes Kubernetes (EKS). |
| **Custo**                | Cobrança por instância EC2.                  | Cobrança por instância EC2 (modo EC2) ou por vCPU/memória (Fargate). |

**Melhor Escolha**:  
- **EC2**: Aplicações não containerizadas ou que exigem acesso direto à VM.  
- **ECS**: Ambientes baseados em containers (Docker), arquiteturas de microserviços.  

---

#### **3. EC2 vs. Elastic Beanstalk**
| **Critério**            | **EC2**                                      | **Elastic Beanstalk**                          |
|-------------------------|----------------------------------------------|------------------------------------------------|
| **Gerenciamento**        | Controle total da infraestrutura.            | Plataforma como serviço (PaaS) – AWS gerencia a infraestrutura. |
| **Flexibilidade**        | Alto (customização de rede, segurança, etc.).| Limitada (foco na entrega rápida de aplicações).|
| **Implantação**          | Manual (scripts, AMIs, etc.).                | Automatizada (upload do código, AWS cuida do resto). |
| **Casos de Uso**         | Ambientes altamente personalizados.          | Aplicações web simples (ex: Node.js, Python), MVP rápido. |

**Melhor Escolha**:  
- **EC2**: Projetos complexos com requisitos específicos de infraestrutura.  
- **Elastic Beanstalk**: Equipes que priorizam velocidade de implantação sem gerenciar servidores.  

---

### **Cenários e Recomendações**

#### **Cenário 1: Aplicação Web Monolítica com Tráfego Variável**
- **EC2**: Use Auto Scaling Groups para escalar instâncias EC2 horizontalmente.  
- **Elastic Beanstalk**: Ideal se a equipe prefere focar no código e não na infraestrutura.  
- **Por que não Lambda**: A aplicação é stateful e requer execução contínua.  

#### **Cenário 2: Processamento de Dados de IoT (Eventos Esporádicos)**
- **Lambda**: Executa funções em resposta a eventos (ex: mensagens do IoT Core).  
- **Por que não EC2**: O custo de manter instâncias ativas seria alto para workloads intermitentes.  

#### **Cenário 3: Microserviços em Containers com Alta Disponibilidade**
- **ECS (Fargate)**: Orquestração de containers sem gerenciar servidores.  
- **Por que não EC2**: O ECS simplifica o deploy, scaling e gerenciamento de containers.  

#### **Cenário 4: Startup com MVP para Validação de Mercado**
- **Elastic Beanstalk**: Implante rapidamente sem preocupações com infraestrutura.  
- **Por que não EC2**: A equipe tem recursos limitados para configurar servidores.  

---

### **Considerações para o Exame SAA-C03**
1. **Trade-offs entre Controle e Simplicidade**:  
   - EC2 oferece máximo controle, mas exige mais esforço de gerenciamento.  
   - Lambda/Beanstalk são "managed services" e reduzem overhead operacional.  

2. **Custos**:  
   - EC2: Custo fixo para instâncias reservadas ou contínuas.  
   - Lambda: Custo variável (pague apenas pelo uso).  

3. **Resiliência**:  
   - EC2 exige configuração manual de Multi-AZ.  
   - ECS/Lambda têm resiliência nativa integrada.  

4. **Desempenho**:  
   - EC2 é ideal para workloads de alto desempenho (ex: GPU, computação intensiva).  
   - Lambda tem latência de cold start (evite para tarefas críticas de tempo real).  

---

### **Resumo das Melhores Escolhas**
| **Serviço**          | **Quando Escolher**                                  | **Exemplo de Caso de Uso**                     |
|-----------------------|------------------------------------------------------|------------------------------------------------|
| **EC2**               | Controle total, workloads estáveis, aplicações legacy. | Servidor web personalizado, banco de dados.    |
| **Lambda**            | Eventos esporádicos, backend serverless.             | Processamento de imagens, APIs REST.           |
| **ECS**               | Microserviços em containers, CI/CD pipelines.        | Aplicação Docker com escalabilidade automática.|
| **Elastic Beanstalk** | Implantação rápida, foco no código (PaaS).           | MVP de uma aplicação web em Python.            |

---
