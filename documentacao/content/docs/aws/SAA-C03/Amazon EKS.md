---
title: "Amazon EKS"
---

### **Amazon EKS: Visão Geral**
**O que é**:  
O EKS é um serviço gerenciado pela AWS que simplifica a execução de Kubernetes na nuvem. Ele elimina a necessidade de configurar e manter manualmente o **control plane** do Kubernetes, oferecendo alta disponibilidade, segurança integrada e compatibilidade com ferramentas do ecossistema Kubernetes.

#### **Características Principais**:
- **Kubernetes Gerenciado**: AWS gerencia o control plane (etcd, API server, scheduler, etc.).
- **Integração Nativa com AWS**: Load balancers (ALB/NLB), IAM, VPC, e serviços de armazenamento (EBS, EFS).
- **Escalabilidade**: Auto Scaling de nós worker (EC2) ou pods (via Kubernetes Horizontal Pod Autoscaler).
- **Multiplataforma**: Execute clusters Kubernetes on-premises (**EKS Anywhere**) ou em outras nuvens.
- **Segurança**: Integração com IAM para RBAC (Role-Based Access Control) e criptografia de dados.

---

### **Componentes Principais do EKS**
1. **Cluster EKS**:  
   - **Control Plane**: Gerenciado pela AWS em múltiplas AZs (alta disponibilidade).  
   - **Worker Nodes**: Instâncias EC2 (auto scaling groups) ou pods serverless (**EKS Fargate**) que executam containers.  

2. **Node Groups**:  
   - Grupos de instâncias EC2 com configurações específicas (ex: GPU, memória otimizada).  

3. **Pods e Deployments**:  
   - **Pods**: Menor unidade executável no Kubernetes (1 ou mais containers compartilhando recursos).  
   - **Deployments**: Define como os pods são implantados e atualizados (rolling updates, rollbacks).  

4. **Add-ons**:  
   - **AWS Load Balancer Controller**: Integra ALB/NLB com Kubernetes Ingress.  
   - **EBS CSI Driver**: Provisiona volumes persistentes (EBS) para pods.  
   - **CoreDNS**: Resolução de DNS dentro do cluster.  

5. **VPC Networking**:  
   - Cada pod recebe um IP único na VPC (**CNI da AWS**).  
   - Security Groups e Network Policies (Calico) para isolamento de tráfego.  

---

### **EKS vs. ECS**
| **Critério**            | **EKS**                                      | **ECS**                                      |
|-------------------------|----------------------------------------------|----------------------------------------------|
| **Orquestrador**         | Kubernetes (open-source).                    | Proprietário (AWS).                          |
| **Flexibilidade**        | Portabilidade multi-cloud e híbrida.         | Foco em integração AWS.                      |
| **Complexidade**         | Alta (requer conhecimento de Kubernetes).    | Baixa (abstração AWS).                       |
| **Casos de Uso**         | Equipes com expertise em Kubernetes.         | Equipes que preferem simplicidade AWS.       |
| **Custo**                | Custo do control plane (US$ 0,10/hora/cluster). | Sem custo adicional para o control plane.   |

---

### **Casos de Uso do EKS**
1. **Microserviços Complexos**:  
   - Orquestrar centenas de serviços com dependências complexas (ex: plataforma de streaming).  
   - Usar **Helm Charts** para gerenciamento de pacotes Kubernetes.  

2. **Ambientes Híbridos/Multi-Cloud**:  
   - Gerenciar clusters Kubernetes em AWS, on-premises (**EKS Anywhere**) e outras nuvens.  

3. **Machine Learning (ML)**:  
   - Escalonar treinamento de modelos em containers com GPU (ex: TensorFlow em pods).  

4. **CI/CD Enterprise**:  
   - Integração com **ArgoCD** ou **Flux** para GitOps e deploy contínuo.  

---

### **Arquitetura Típica do EKS**
1. **Control Plane**:  
   - Gerido pela AWS em 3 AZs (para alta disponibilidade).  
   - Comunica-se com os worker nodes via API Kubernetes.  

2. **Worker Nodes**:  
   - Instâncias EC2 em um auto scaling group (ex: `t3.medium`).  
   - Executam o **kubelet** para comunicação com o control plane.  

3. **Networking**:  
   - **Amazon VPC CNI**: Atribui IPs da VPC aos pods.  
   - **Network Policies**: Restringe comunicação entre pods (ex: usando Calico).  

4. **Storage**:  
   - **Persistent Volumes (PV)**: Provisionados via EBS, EFS ou FSx for Lustre.  

---

### **Comparação com Outros Serviços**

#### **EKS vs. EC2**
| **Critério**            | **EKS**                                      | **EC2**                                      |
|-------------------------|----------------------------------------------|----------------------------------------------|
| **Abstração**            | Orquestração de containers (Kubernetes).     | Máquinas virtuais tradicionais.              |
| **Escalonamento**        | Escalonamento de pods e nós.                 | Escalonamento de instâncias.                 |
| **Casos de Uso**         | Aplicações containerizadas complexas.       | Workloads não containerizados.               |

**Melhor Escolha**:  
- **EKS**: Ambientes Kubernetes com múltiplos microserviços.  
- **EC2**: Aplicações monolíticas ou que exigem acesso direto à VM.  

---

#### **EKS vs. Lambda**
| **Critério**            | **EKS**                                      | **Lambda**                                   |
|-------------------------|----------------------------------------------|----------------------------------------------|
| **Modelo**              | Containers de longa duração.                 | Funções serverless de curta duração.         |
| **Custo**               | Custo contínuo (EC2 + control plane).        | Cobrança por execução.                       |
| **Flexibilidade**       | Alta (personalização total do ambiente).     | Limitada (tempo de execução e recursos).     |

**Melhor Escolha**:  
- **EKS**: Processos longos ou aplicações stateful.  
- **Lambda**: Eventos pontuais ou funções stateless.  

---

### **Cenários Específicos e Recomendações**

#### **Cenário 1: Plataforma de E-commerce Global**
- **Requisitos**: Escalabilidade global, atualizações sem downtime, multi-região.  
- **Solução**:  
  - Clusters EKS em múltiplas regiões com **Global Accelerator**.  
  - Usar **Kubernetes Deployments** para rolling updates.  

#### **Cenário 2: Treinamento de Modelos de ML**
- **Requisitos**: Escalonar treinamento com GPU e armazenamento de alto desempenho.  
- **Solução**:  
  - Worker nodes com instâncias **p3.2xlarge** (GPU).  
  - Volumes persistentes via **EFS** para datasets compartilhados.  

#### **Cenário 3: Migração de On-Premises para Cloud**
- **Requisitos**: Aplicação Kubernetes on-premises migrando para AWS.  
- **Solução**:  
  - Usar **EKS Anywhere** para compatibilidade total.  
  - Integrar com **AWS Backup** para disaster recovery.  

---

### **Considerações para o Exame SAA-C03**
1. **Custos**:  
   - **Control Plane**: US$ 0,10 por hora por cluster.  
   - **Worker Nodes**: Custo das instâncias EC2 ou Fargate.  

2. **Segurança**:  
   - **IAM Roles for Service Accounts (IRSA)**: Atribua permissões IAM a pods específicos.  
   - **Encriptação**: Dados em trânsito (TLS) e em repouso (EBS/EFS com KMS).  

3. **Escalabilidade**:  
   - **Cluster Autoscaler**: Ajusta o número de worker nodes com base na demanda.  
   - **Horizontal Pod Autoscaler (HPA)**: Escalona pods baseado em CPU/memória.  

4. **Integrações Chave**:  
   - **ALB Ingress Controller**: Roteamento HTTP/HTTPS para serviços.  
   - **Prometheus/Grafana**: Monitoramento via **Amazon Managed Service for Prometheus**.  

---

### **Padrões Arquiteturais com EKS**
1. **Serverless com EKS Fargate**:  
   - Execute pods sem gerenciar worker nodes (ideal para workloads esporádicos).  
   - Exemplo: Jobs batch de processamento de dados.  

2. **Multi-Tenancy**:  
   - Isolar times/projetos usando **Namespaces** e **Resource Quotas**.  

3. **Disaster Recovery**:  
   - Replique clusters EKS entre regiões usando **Velero** para backup de recursos Kubernetes.  

---

### **Melhores Práticas**
- **Infraestrutura como Código (IaC)**: Use **Terraform** ou **AWS CloudFormation** para criar clusters.  
- **Least Privilege**: Restrinja acesso ao cluster com **RBAC** e políticas IAM.  
- **Upgrades**: Mantenha a versão do Kubernetes atualizada para segurança e novas features.  

---

### **Quando NÃO Usar EKS**
- Equipes sem expertise em Kubernetes (prefira ECS ou Elastic Beanstalk).  
- Workloads simples ou estáticos (Lambda pode ser mais econômico).  
- Projetos com orçamento limitado (custos do control plane + worker nodes).  

---

### **Resumo para o Exame SAA-C03**
- **EKS vs. ECS**: Escolha EKS para portabilidade e Kubernetes; ECS para simplicidade AWS.  
- **EKS Fargate**: Ideal para evitar gerenciamento de nodes, mas custo mais alto que EC2.  
- **Segurança**: IRSA, Network Policies e encriptação são tópicos-chave.  
