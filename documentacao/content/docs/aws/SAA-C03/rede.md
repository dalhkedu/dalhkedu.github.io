---
title: "Redes"
---

### **1. Amazon VPC (Virtual Private Cloud)**  
**O que é**:  
Uma rede virtual isolada e personalizável na AWS, onde você implanta recursos (EC2, RDS, etc.) em subnets públicas/privadas.  

**Quando usar**:  
- Para isolar ambientes (ex: produção, desenvolvimento).  
- Hospedar aplicações multi-camadas (web, app, banco de dados).  
- Conectar redes on-premises à AWS via VPN ou Direct Connect.  

**Vantagens**:  
- Controle total sobre IPs, subnets, tabelas de roteamento e Security Groups.  
- Segurança avançada com NACLs (Network ACLs) e Security Groups.  
- Integração com serviços AWS (ex: S3 Gateway Endpoint).  

**Desvantagens**:  
- Complexidade na configuração inicial (ex: NAT Gateways, VPN).  
- Custos adicionais por NAT Gateway, VPC Peering e tráfego entre regiões.  

**Exemplo Arquitetural**:  
- **Aplicação Web de 3 Camadas**:  
  - **Subnet Pública**: EC2 com servidor web (acessível via Internet).  
  - **Subnet Privada**: EC2 com servidor de aplicação e RDS (sem acesso direto à Internet).  
  - **NAT Gateway**: Permite atualizações de software em instâncias privadas.  

---

### **2. Amazon CloudFront**  
**O que é**:  
Uma CDN (Content Delivery Network) que distribui conteúdo estático/dinâmico globalmente com baixa latência.  

**Quando usar**:  
- Acelerar sites estáticos (ex: imagens, CSS, JS).  
- Streaming de vídeo (ex: HLS, DASH).  
- Proteção contra DDoS (integração com AWS Shield).  

**Vantagens**:  
- Cache em borda (Edge Locations) para conteúdo frequente.  
- Suporte a SSL/TLS personalizado e integração com WAF.  
- Funcionalidades avançadas como Lambda@Edge (customização de conteúdo).  

**Desvantagens**:  
- Custos podem ser altos para tráfego muito elevado.  
- Configuração complexa para comportamentos de cache personalizados.  

**Exemplo Arquitetural**:  
- **Site Estático Global**:  
  - **Origem**: Bucket S3.  
  - **CloudFront**: Distribui conteúdo para Edge Locations.  
  - **WAF**: Protege contra SQL injection e bots.  

---

### **3. Amazon Route 53**  
**O que é**:  
Serviço de DNS gerenciado que roteia tráfego para recursos AWS ou externos.  

**Quando usar**:  
- Registrar domínios e gerenciar zonas DNS.  
- Balanceamento de carga com políticas de roteamento (ex: geolocalização, weighted).  
- Health Checks para failover automático (ex: entre regiões AWS).  

**Vantagens**:  
- Alta disponibilidade (100% SLA).  
- Integração com ALB, CloudFront e serviços externos.  
- Roteamento inteligente (ex: latency-based para melhor performance).  

**Desvantagens**:  
- Custos por zona hospedada e consultas DNS.  
- Configuração complexa para cenários multi-região.  

**Exemplo Arquitetural**:  
- **Aplicação Multi-Região**:  
  - **Região Leste dos EUA**: EC2 + RDS (produção).  
  - **Região Europa**: EC2 + RDS (backup).  
  - **Route 53**: Usa latency-based routing para direcionar usuários ao site mais próximo.  

---

### **4. Amazon API Gateway**  
**O que é**:  
Serviço para criar, publicar e gerenciar APIs REST, HTTP e WebSocket.  

**Quando usar**:  
- Expor microsserviços (ex: Lambda, ECS).  
- Criar APIs serverless com autenticação (Cognito, IAM).  
- Transformar requests/responses (ex: XML para JSON).  

**Vantagens**:  
- Escalabilidade automática e cobrança por uso.  
- Cache de API para reduzir latência.  
- Suporte a CORS e throttling para segurança.  

**Desvantagens**:  
- Custos podem subir com alto volume de requests (ex: milhões/mês).  
- Limite de 29 segundos para timeout de integrações (ex: Lambda).  

**Exemplo Arquitetural**:  
- **Backend Serverless**:  
  - **API Gateway**: Expõe endpoints REST.  
  - **Lambda**: Processa solicitações (ex: CRUD em DynamoDB).  
  - **Cognito**: Gerencia autenticação de usuários.  

---

### **Conceitos Adicionais**  

#### **Full Mesh Networking**  
**O que é**:  
Uma topologia de rede onde todos os nós (ex: VPCs, redes on-premises) estão interconectados diretamente.  
**Quando usar**:  
- Arquiteturas híbridas que exigem comunicação direta entre todas as redes.  
- Cenários de alta redundância (ex: sistemas financeiros).  
**Exemplo**:  
- **Transit Gateway**: Conecta múltiplas VPCs e VPNs em uma arquitetura hub-and-spoke ou full mesh.  

#### **Conexões entre VPCs**  
1. **VPC Peering**:  
   - Comunicação direta entre duas VPCs (sem sobreposição de CIDR).  
   - **Uso**: Compartilhar recursos entre ambientes (ex: produção e análise).  
2. **Transit Gateway**:  
   - Hub central para conectar múltiplas VPCs, VPNs e redes on-premises.  
   - **Uso**: Empresas com dezenas de VPCs.  
3. **VPN ou Direct Connect**:  
   - Conexão segura entre VPC e data centers on-premises.  

#### **Blue/Green Deployment**  
**O que é**:  
Estratégia de implantação que cria um ambiente idêntico (**green**) ao atual (**blue**) e direciona o tráfego gradualmente para o novo ambiente.  
**Quando usar**:  
- Atualizações de aplicações sem downtime.  
- Rollback rápido em caso de falhas.  
**Exemplo com AWS**:  
- **Elastic Beanstalk**: Cria um novo ambiente (green) e troca o CNAME após testes.  
- **Route 53**: Usa weighted routing para dividir tráfego entre blue/green.  
- **Lambda**: Atualiza aliases para direcionar tráfego entre versões.  

---

### **Exemplo de Arquitetura Integrada**  
**Plataforma de E-commerce Global**:  
1. **Rede**:  
   - **VPC** com subnets públicas (ALB) e privadas (ECS + Aurora).  
2. **Conteúdo**:  
   - **CloudFront** distribui imagens e JS a partir do S3.  
3. **DNS**:  
   - **Route 53** gerencia o domínio e faz failover entre regiões.  
4. **APIs**:  
   - **API Gateway** expõe endpoints para checkout e autenticação (Cognito).  
5. **Conexões**:  
   - **Transit Gateway** interliga VPCs de produção e backup.  
6. **Deploy**:  
   - **Blue/Green** no ECS para atualizar containers sem downtime.  

---

### **Resumo para o Exame SAA-C03**  
- **VPC**: Base para redes seguras e isoladas.  
- **CloudFront**: CDN para performance global.  
- **Route 53**: DNS inteligente e failover.  
- **API Gateway**: Gerenciamento de APIs serverless.  
- **Full Mesh/Transit Gateway**: Conectividade escalável entre VPCs.  
- **Blue/Green**: Estratégia de implantação de baixo risco.  

