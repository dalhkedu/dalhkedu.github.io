---
title: "Cloud AWS"
---

### **1. Definições e Diferenças**

| **Modelo** | **Definição**                                                                 | **Controle do Usuário**                                                                 | **Responsabilidade da AWS**                                                                 |
|------------|-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| **IaaS**   | Infraestrutura como Serviço: Fornece recursos computacionais virtualizados.   | Controle total sobre SO, middleware, aplicações e dados.                              | AWS gerencia a infraestrutura física (hardware, rede, virtualização).                      |
| **PaaS**   | Plataforma como Serviço: Oferece ambiente para desenvolvimento e deploy.      | Controle sobre aplicações e dados; AWS gerencia SO, middleware e infraestrutura.      | AWS cuida de atualizações, patches e escalabilidade da plataforma.                        |
| **SaaS**   | Software como Serviço: Software completo gerenciado pelo provedor.            | Apenas controle sobre configurações e dados do software.                              | AWS gerencia tudo: infraestrutura, aplicação, atualizações e segurança.                    |

---

### **2. Serviços AWS por Categoria (Relevantes para SAA-C03)**

#### **IaaS (Infrastructure as a Service)**
- **Amazon EC2**: Máquinas virtuais sob demanda.
- **Amazon S3**: Armazenamento de objetos escalável.
- **Amazon VPC**: Rede virtual isolada na nuvem.
- **Amazon EBS**: Armazenamento em bloco para instâncias EC2.

#### **PaaS (Platform as a Service)**
- **AWS Elastic Beanstalk**: Plataforma para deploy automatizado de aplicações (PHP, Java, Node.js, etc.).
- **AWS Lambda**: Execução de código serverless (sem gerenciar servidores).
- **Amazon RDS**: Banco de dados gerenciado (MySQL, PostgreSQL, etc.).
- **Amazon ECS/EKS**: Orquestração de containers (Docker/Kubernetes gerenciado).

#### **SaaS (Software as a Service)**
- **Amazon WorkMail**: Serviço de e-mail corporativo.
- **Amazon Chime**: Ferramenta de comunicação (vídeo, voz, chat).
- **AWS QuickSight**: Business Intelligence como serviço.
- **Amazon Connect**: Central de atendimento virtual.

---

### **3. Comparação de Custos e Cenários**

#### **Cenário 1: Aplicação Web com Tráfego Variável**
- **IaaS (EC2 + RDS)**:  
  - **Custo**: Alto para workloads imprevisíveis (pagar por instâncias ociosas).  
  - **Melhor Quando**: Controle total é necessário (ex: aplicações legadas).  
- **PaaS (Elastic Beanstalk + Lambda)**:  
  - **Custo**: Reduzido para tráfego variável (escalabilidade automática, pagamento por uso).  
  - **Melhor Quando**: Equipe pequena prioriza velocidade de deploy.  
- **SaaS (QuickSight para Analytics)**:  
  - **Custo**: Previsível (assinatura por usuário).  
  - **Melhor Quando**: Não há necessidade de personalização complexa.

**Por que PaaS é melhor aqui?**  
Escalabilidade automática reduz custos em picos esporádicos, e não há custo por ociosidade.

---

#### **Cenário 2: Banco de Dados Corporativo**
- **IaaS (EC2 + Instalação Manual de MySQL)**:  
  - **Custo**: Baixo inicialmente, mas alto em manutenção (patches, backups, HA).  
  - **Melhor Quando**: Requer configurações customizadas não suportadas por RDS.  
- **PaaS (Amazon Aurora/RDS)**:  
  - **Custo**: Moderado (pagar pelo banco gerenciado, sem custo de administração).  
  - **Melhor Quando**: Alta disponibilidade e backups automatizados são críticos.  
- **SaaS (N/A para bancos de dados)**: Não se aplica.

**Por que PaaS (RDS) é melhor aqui?**  
Custo total de propriedade (TCO) é menor devido à automação de backups, patches e Multi-AZ.

---

#### **Cenário 3: Processamento de Dados em Batch**
- **IaaS (EC2 Spot Instances)**:  
  - **Custo**: Muito baixo (Spot Instances), mas risco de interrupção.  
  - **Melhor Quando**: Workloads tolerantes a falhas e flexíveis no tempo.  
- **PaaS (AWS Batch ou Lambda)**:  
  - **Custo**: Lambda paga por execução; Batch é mais econômico para jobs longos.  
  - **Melhor Quando**: Processamento rápido e sem gerenciamento de servidores.  
- **SaaS (N/A)**: Não se aplica.

**Por que PaaS (Lambda) é melhor aqui?**  
Para jobs curtos e event-driven, o custo por milissegundo é mais eficiente que EC2.

---

### **4. Regras Gerais para Escolha de Modelo**

#### **Escolha IaaS Quando**:
- Requer controle total sobre SO, redes e segurança.
- Workloads são previsíveis e estáveis (ex: servidores legados).
- Equipe tem expertise em gerenciar infraestrutura.

#### **Escolha PaaS Quando**:
- Foco é desenvolver aplicações, não gerenciar infraestrutura.
- Workloads são variáveis ou event-driven (ex: APIs, microsserviços).
- Deseja reduzir custos operacionais (ex: RDS vs. MySQL auto-gerido).

#### **Escolha SaaS Quando**:
- Necessita de software pronto para uso (ex: e-mail, BI).
- Não há recursos para desenvolvimento ou manutenção de software.
- Padronização é mais importante que personalização.

---

### **5. Tabela de Comparação de Custos**

| **Fator**               | **IaaS**                     | **PaaS**                     | **SaaS**                     |
|-------------------------|------------------------------|------------------------------|------------------------------|
| **Custo Inicial**        | Alto (configuração manual).  | Moderado (configuração rápida). | Baixo (assinatura).           |
| **Custo de Manutenção**  | Alto (patches, upgrades).    | Baixo (gerenciado pela AWS).  | Nulo (gerenciado pelo provedor). |
| **Escalabilidade**       | Manual (Auto Scaling Groups).| Automática (Elastic Beanstalk/Lambda). | Automática (depende do SaaS). |
| **Flexibilidade**        | Máxima.                      | Limitada à plataforma.        | Mínima (padronizado).         |

---

### **6. Exemplos de Perguntas no Exame SAA-C03**
1. **Cenário**: Uma empresa quer migrar uma aplicação .NET para a AWS com mínimo esforço de gerenciamento.  
   - **Resposta Correta**: **Elastic Beanstalk (PaaS)**.  
   - **Por quê?** O EB gerencia automaticamente o deploy, escalabilidade e infraestrutura.

2. **Cenário**: Uma startup precisa de um data warehouse altamente escalável sem administração.  
   - **Resposta Correta**: **Amazon Redshift (PaaS)**.  
   - **Por quê?** Redshift é um serviço gerenciado (PaaS) para analytics.

3. **Cenário**: Uma empresa deseja total controle sobre o sistema operacional para compliance.  
   - **Resposta Correta**: **EC2 (IaaS)**.  
   - **Por quê?** IaaS permite personalização total do SO.

---

### **Conclusão**
A escolha entre **IaaS, PaaS e SaaS** depende do trade-off entre **controle**, **custo** e **complexidade**. Para a certificação **SAA-C03**, foque em:
- **IaaS**: EC2, VPC, EBS.  
- **PaaS**: Elastic Beanstalk, Lambda, RDS, ECS.  
- **SaaS**: Serviços como QuickSight (menos comum no exame).  

Priorize **PaaS** para otimizar custos em workloads variáveis e **IaaS** para controle total em ambientes estáticos.