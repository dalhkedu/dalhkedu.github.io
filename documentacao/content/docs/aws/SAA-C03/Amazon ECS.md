---
title: "Amazon ECS"
---

### **Amazon ECS: Visão Geral**
**O que é**:  
O ECS é um serviço de orquestração de containers totalmente gerenciado pela AWS, projetado para executar, escalar e gerenciar aplicações em containers Docker. Ele se integra nativamente com outros serviços AWS, como Elastic Load Balancing, IAM e CloudWatch, sendo ideal para ambientes de microserviços e CI/CD.

#### **Características Principais**:
- **Suporte a Containers Docker**: Execute containers sem precisar gerenciar servidores subjacentes (com **Fargate**) ou usando instâncias EC2.
- **Escalabilidade Automática**: Ajuste o número de containers com base em métricas como CPU e memória.
- **Integração com Ecossistema AWS**: Trabalha com serviços como ALB (Application Load Balancer), CloudMap, e AWS Copilot para CLI simplificada.
- **Modelos de Execução**:
  - **Fargate**: Serverless (AWS gerencia a infraestrutura).
  - **EC2 Launch Type**: Controle total sobre as instâncias EC2 subjacentes.

---

### **Componentes Principais do ECS**
1. **Cluster ECS**:  
   - Grupo lógico de recursos (instâncias EC2 ou recursos Fargate) onde os containers são executados.  
   - Pode conter múltiplos **serviços** e **tasks**.

2. **Task Definition**:  
   - "Receita" que define como um container deve ser executado:  
     - Imagem Docker, portas, variáveis de ambiente, requisitos de CPU/memória.  
     - Configurações de rede (AWS VPC, subnets).  
     - **Task Role**: Permissões IAM para a task acessar outros serviços AWS.

3. **Service**:  
   - Mantém um número especificado de instâncias de uma **task** em execução contínua.  
   - Gerencia escalabilidade (auto scaling) e integração com load balancers.

4. **Task**:  
   - Instância de uma **task definition** em execução no cluster.  
   - Em modo **Fargate**, cada task tem sua própria isolamento de rede (ENI dedicada).

---

### **Fargate vs. EC2 Launch Type**
| **Critério**            | **Fargate**                                  | **EC2 Launch Type**                          |
|-------------------------|----------------------------------------------|-----------------------------------------------|
| **Gerenciamento**        | Serverless (AWS gerencia servidores).        | Você gerencia instâncias EC2 (patches, scaling). |
| **Custo**                | Cobrança por vCPU e memória usada na task.   | Cobrança por instância EC2 (independente do uso). |
| **Escalonamento**        | Escalonamento no nível da task.              | Escalonamento no nível da instância EC2 + tasks. |
| **Casos de Uso**         | Equipes que não querem gerenciar servidores. | Workloads que exigem controle total sobre a infra. |
| **Performance**          | Isolamento por task (nenhuma interferência). | Compartilhamento de recursos entre tasks.     |

---

### **Casos de Uso do ECS**
1. **Microserviços**:  
   - Execute cada serviço como um container separado, com escalabilidade independente.  
   - Exemplo: Backend de e-commerce com serviços de catálogo, carrinho e pagamento.

2. **CI/CD Pipelines**:  
   - Use ECS com AWS CodePipeline e CodeBuild para deploy contínuo de containers.  
   - Atualizações sem downtime com **blue/green deployments** (via AWS CodeDeploy).

3. **Aplicações Híbridas**:  
   - Integre containers no ECS com workloads on-premises via **AWS Outposts**.

4. **Batch Processing**:  
   - Execute tarefas em lote de curta duração usando **ECS Tasks** (ex: processamento de dados noturno).

---

### **Comparação com Outros Serviços**

#### **ECS vs. EC2**
| **Critério**            | **ECS**                                      | **EC2**                                      |
|-------------------------|----------------------------------------------|----------------------------------------------|
| **Abstração**            | Foco em containers (Docker).                 | Máquinas virtuais tradicionais.              |
| **Escalonamento**        | Escalonamento granular (por container/task). | Escalonamento no nível da instância.         |
| **Gerenciamento**        | Mais alto nível (menos configuração).        | Controle total (mais complexidade).          |

**Melhor Escolha**:  
- Use **ECS** para aplicações containerizadas.  
- Use **EC2** para workloads não containerizados ou que exigem acesso direto à VM.

---

#### **ECS vs. EKS (Elastic Kubernetes Service)**
| **Critério**            | **ECS**                                      | **EKS**                                      |
|-------------------------|----------------------------------------------|----------------------------------------------|
| **Orquestrador**         | Proprietário (AWS).                          | Kubernetes (open-source).                    |
| **Flexibilidade**        | Integração nativa com AWS.                   | Portabilidade multi-cloud (Kubernetes).      |
| **Complexidade**         | Mais simples para usuários AWS.              | Requer conhecimento de Kubernetes.           |

**Melhor Escolha**:  
- **ECS**: Equipes que preferem uma solução AWS nativa.  
- **EKS**: Equipes com expertise em Kubernetes ou que precisam de portabilidade.

---

#### **ECS vs. Lambda**
| **Critério**            | **ECS**                                      | **Lambda**                                   |
|-------------------------|----------------------------------------------|----------------------------------------------|
| **Modelo**              | Containers de longa duração.                 | Funções serverless de curta duração.         |
| **Tempo de Execução**   | Sem limites (depende da configuração).       | Máximo de 15 minutos.                        |
| **Custo**               | Cobrança contínua (EC2/Fargate).             | Cobrança por execução.                       |

**Melhor Escolha**:  
- **ECS**: Aplicações com containers complexos ou long-running.  
- **Lambda**: Eventos esporádicos ou funções stateless.

---

### **Cenários Específicos e Recomendações**

#### **Cenário 1: Aplicação Web com Alta Disponibilidade**
- **Requisitos**: Escalabilidade automática, balanceamento de carga, tolerância a falhas.  
- **Solução**:  
  - Cluster ECS com **Fargate**.  
  - Service configurado com Auto Scaling baseado em CPU.  
  - Integração com **Application Load Balancer (ALB)** para distribuição de tráfego.  

#### **Cenário 2: Processamento em Lote com Containers**
- **Requisitos**: Executar tarefas noturnas para gerar relatórios.  
- **Solução**:  
  - Tasks ECS com **EC2 Launch Type** (custo menor para uso contínuo).  
  - Uso de **Spot Instances** para reduzir custos.  

#### **Cenário 3: Migração de Aplicação Monolítica para Microserviços**
- **Requisitos**: Decompor uma aplicação legada em containers.  
- **Solução**:  
  - Cluster ECS com **Fargate** para simplificar o gerenciamento.  
  - Service Discovery via **AWS CloudMap** para comunicação entre serviços.  

---

### **Considerações para o Exame SAA-C03**
1. **Segurança**:  
   - **Task Roles**: Sempre atribua permissões mínimas via IAM roles para tasks.  
   - **Segurança de Rede**: Use Security Groups e NACLs para restringir tráfego entre containers.

2. **Monitoramento**:  
   - Use **CloudWatch Metrics** para monitorar CPU/memória de tasks.  
   - **AWS X-Ray** para rastrear requisições entre microserviços.

3. **Escalabilidade**:  
   - **Service Auto Scaling**: Ajuste o número de tasks com base em métricas personalizadas.  
   - **Cluster Auto Scaling** (EC2 Launch Type): Adicione/remova instâncias EC2 conforme a demanda.

4. **Integrações Chave**:  
   - **ALB**: Roteamento avançado (ex: path-based routing para microserviços).  
   - **EFS**: Armazenamento persistente compartilhado entre containers.  

---

### **Padrões Arquiteturais com ECS**
1. **Serverless Containers com Fargate**:  
   - Implante containers sem gerenciar servidores, ideal para startups ou equipes pequenas.  
   - Exemplo: API backend + React frontend em containers Fargate.

2. **Híbrido (EC2 + Fargate)**:  
   - Use **EC2 Launch Type** para workloads críticos e **Fargate** para tarefas esporádicas.  

3. **Multi-Region Deployment**:  
   - Distribua clusters ECS em múltiplas regiões com **Route 53** para failover.  

---

### **Melhores Práticas**
- **Immutable Infrastructure**: Sempre atualize tasks com novas versões de imagens Docker (evite modificar containers em execução).  
- **Log Centralizado**: Envie logs de containers para **CloudWatch Logs** ou **Amazon OpenSearch**.  
- **Task Placement Strategies**: Controle onde as tasks são executadas no cluster (ex: distribuir tarefas entre AZs).  

---

### **Quando NÃO Usar ECS**
- Workloads não containerizados (prefira EC2 ou Lambda).  
- Equipes sem experiência em Docker (comece com Elastic Beanstalk).  
- Aplicações que exigem portabilidade multi-cloud (considere EKS ou Kubernetes).  

---

