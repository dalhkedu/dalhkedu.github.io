---
title: "Elastic Beanstalk"
---

### **Elastic Beanstalk: Visão Geral**
**O que é**:  
O Elastic Beanstalk é uma plataforma como serviço (**PaaS**) da AWS que simplifica o deploy, o gerenciamento e o escalonamento de aplicações. Ele abstrai a infraestrutura subjacente (EC2, RDS, Load Balancers, etc.) e automatiza tarefas operacionais, permitindo que os desenvolvedores se concentrem no código.

**Principais Características**:
- **Multiplataforma**: Suporta aplicações em Node.js, Java, .NET, PHP, Python, Ruby, Go, Docker e mais.
- **Escalonamento Automático**: Configura automaticamente Auto Scaling Groups e Elastic Load Balancers.
- **Gerenciamento Simplificado**: Atualizações de SO, patches e monitoramento são tratados pela AWS.
- **Integração com Serviços AWS**: RDS, S3, CloudWatch, SNS, VPC, IAM, etc.
- **Modelo de Custo**: Você paga apenas pelos recursos subjacentes (EC2, RDS, etc.), sem custo adicional pelo EB.

---

### **Componentes da Arquitetura do Elastic Beanstalk**
1. **Application**:  
   - Contêiner lógico que agrupa ambientes, versões e configurações de uma aplicação.

2. **Environment**:  
   - Instância da aplicação em execução (ex: ambiente de produção *vs.* staging).  
   - Dois tipos principais:  
     - **Web Server Environment**: Para aplicações web (ex: API REST, frontend).  
     - **Worker Environment**: Para processamento assíncrono (ex: filas SQS).

3. **Application Version**:  
   - Versão específica do código da aplicação (ex: `v1.0.0`), armazenada no S3.

4. **Configuration**:  
   - Define configurações de infraestrutura (tipo de instância EC2, scaling policies, variáveis de ambiente).

---

### **Funcionamento e Fluxo de Deploy**
1. O desenvolvedor faz upload do código (ZIP, WAR, ou Dockerfile).  
2. O EB provisiona automaticamente:  
   - Instâncias EC2 (com AMI pré-configurada para a linguagem escolhida).  
   - Load Balancer (CLB, ALB ou NLB).  
   - Auto Scaling Group (se escalonamento automático estiver habilitado).  
3. O código é implantado nos recursos, e o EB monitora a saúde da aplicação via **Health Dashboard**.

---

### **Comparação com Outros Serviços**

#### **Elastic Beanstalk vs. EC2**
| **Critério**            | **Elastic Beanstalk**                      | **EC2**                                      |
|-------------------------|--------------------------------------------|----------------------------------------------|
| **Gerenciamento**        | AWS gerencia infraestrutura (PaaS).        | Você gerencia tudo (IaaS).                   |
| **Velocidade de Deploy** | Minutos (automatizado).                    | Horas/dias (configuração manual).            |
| **Flexibilidade**        | Limitada (foco em simplicidade).           | Total (personalização completa).             |
| **Casos de Uso**         | MVP rápido, aplicações web tradicionais.   | Workloads complexos com requisitos específicos. |

**Melhor Escolha**:  
- **EB**: Equipes pequenas ou projetos que priorizam velocidade.  
- **EC2**: Workloads que exigem controle total sobre a infraestrutura.

---

#### **Elastic Beanstalk vs. ECS**
| **Critério**            | **Elastic Beanstalk**                      | **ECS**                                      |
|-------------------------|--------------------------------------------|----------------------------------------------|
| **Modelo**              | Foco em aplicações monolíticas ou simples. | Projetado para containers e microserviços.   |
| **Orquestração**         | Não requer conhecimento de containers.     | Baseado em Docker e Kubernetes (EKS).        |
| **Escalonamento**        | Automático, mas menos granular.            | Escalonamento por container/task.            |

**Melhor Escolha**:  
- **EB**: Aplicações tradicionais em PHP, Java, etc.  
- **ECS**: Arquiteturas baseadas em containers ou microserviços.

---

#### **Elastic Beanstalk vs. Lambda**
| **Critério**            | **Elastic Beanstalk**                      | **Lambda**                                   |
|-------------------------|--------------------------------------------|----------------------------------------------|
| **Modelo de Execução**   | Aplicações contínuas (servidores sempre ativos). | Funções serverless de curta duração (event-driven). |
| **Custo**                | Cobrança por recursos alocados (EC2, RDS). | Cobrança por solicitação e tempo de execução.|
| **Complexidade**         | Mais alto nível que EC2, mas menos que Lambda. | Total abstração da infraestrutura.           |

**Melhor Escolha**:  
- **EB**: Aplicações web com execução contínua.  
- **Lambda**: Tarefas event-driven ou backend de APIs serverless.

---

### **Casos de Uso do Elastic Beanstalk**
1. **MVP (Minimum Viable Product)**:  
   - Implante rapidamente uma aplicação web para validar uma ideia, sem gastar tempo configurando infraestrutura.

2. **Aplicações Web Tradicionais**:  
   - Blogs, sites corporativos ou APIs em Node.js/Python com tráfego previsível.

3. **Ambientes de Teste/Staging**:  
   - Crie ambientes isolados para testes usando o mesmo código da produção.

4. **Integração com CI/CD**:  
   - Use o EB com **AWS CodePipeline** e **CodeBuild** para pipelines de deploy automatizados.

---

### **Estratégias de Deploy no Elastic Beanstalk**
1. **All at Once**:  
   - Atualiza todas as instâncias simultaneamente (rápido, mas causa downtime).  
   - **Uso**: Ambientes de desenvolvimento/teste.

2. **Rolling**:  
   - Atualiza instâncias em grupos (minimiza downtime parcial).  
   - **Uso**: Produção com tolerância a downtime curto.

3. **Immutable**:  
   - Cria novas instâncias em paralelo e substitui as antigas após teste.  
   - **Uso**: Produção crítica (zero downtime).

4. **Blue/Green**:  
   - Cria um novo ambiente e roteia o tráfego após validação (usando Route 53 ou ALB).  
   - **Uso**: Atualizações complexas com risco mínimo.

---

### **Vantagens do Elastic Beanstalk**
- **Produtividade**: Foco no código, sem gerenciar servidores.  
- **Escalabilidade Automática**: Ajusta capacidade conforme carga (configurável via políticas).  
- **Monitoramento Integrado**: Health Dashboard, métricas do CloudWatch e logs centralizados.  
- **Customização via `.ebextensions`**: Arquivos YAML para configurar recursos AWS (ex: Security Groups, environment variables).

---

### **Limitações do Elastic Beanstalk**
- **Controle Limitado**: Não é ideal para configurações de infraestrutura altamente personalizadas.  
- **Lock-in AWS**: Configurações específicas do EB podem dificultar migrações para outras clouds.  
- **Custos Subjacentes**: Recursos como RDS ou ALB podem aumentar o custo total.

---

### **Melhores Práticas para o Exame SAA-C03**
1. **Separação de Ambientes**:  
   - Use ambientes separados para produção, staging e teste.  
   - Evite compartilhar recursos como RDS entre ambientes.

2. **Configuração de Segurança**:  
   - Aplique o **princípio do menor privilégio** às roles do IAM.  
   - Use HTTPS via Load Balancer e certificados ACM.

3. **Gerenciamento de Configurações**:  
   - Armazene segredos (senhas, API keys) no **AWS Systems Manager Parameter Store**.  
   - Use **Saved Configurations** para reutilizar configurações entre ambientes.

4. **Monitoramento**:  
   - Habilite **Enhanced Health Reporting** para detalhes sobre falhas.  
   - Configure alarmes no CloudWatch para métricas como `CPUUtilization`.

---

### **Quando NÃO Usar Elastic Beanstalk**
- **Arquiteturas Baseadas em Containers**: Prefira ECS ou EKS.  
- **Workloads de Machine Learning ou Big Data**: Opte por SageMaker ou EMR.  
- **Aplicações Serverless**: Lambda + API Gateway é mais eficiente.

---

### **Exemplo de Cenário para o Exame**
**Cenário**: Uma startup precisa lançar uma aplicação web em Python com alta disponibilidade e escalabilidade, mas a equipe não tem expertise em AWS.  
**Solução**:  
1. Use **Elastic Beanstalk** para implantar o código em um ambiente web server.  
2. Configure **Auto Scaling** baseado em CPU para lidar com picos de tráfego.  
3. Use **RDS Multi-AZ** para alta disponibilidade do banco de dados.  
4. Habilite **CloudWatch Logs** para monitorar erros.  

**Por que não Lambda?** A aplicação requer execução contínua e estado persistente (sessões de usuário).

---

### **Resumo para a Prova SAA-C03**
- **Elastic Beanstalk** é ideal para aplicações web tradicionais, MVPs e equipes que priorizam velocidade.  
- **Diferencie-o de ECS/Lambda**: EB é PaaS para código monolítico; ECS é para containers; Lambda é serverless.  
- **Estratégias de Deploy**: Saiba quando usar Blue/Green vs. Immutable para minimizar downtime.  

Pratique a criação de ambientes EB e explore `.ebextensions` para personalizações avançadas. Compreender esses tópicos garantirá confiança nas questões de arquitetura do exame! 🚀