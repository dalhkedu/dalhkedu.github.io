---
title: "Armazenamento"
---

### **1. Amazon S3 (Simple Storage Service)**
**O que é**:  
- **Armazenamento de objetos** altamente durável, escalável e disponível globalmente.  
- Projetado para armazenar e recuperar **qualquer quantidade de dados**, em qualquer lugar (via HTTP/HTTPS).  

**Principais Recursos**:  
- **Classes de Armazenamento**:  
  - **S3 Standard**: Acesso frequente (baixa latência).  
  - **S3 Intelligent-Tiering**: Otimiza custos automaticamente entre tiers (frequente, infrequente, arquivamento).  
  - **S3 Standard-IA/One Zone-IA**: Para dados acessados com menos frequência.  
  - **S3 Glacier/Glacier Deep Archive**: Arquivamento de longo prazo (retrieval de minutos a horas).  
- **Durabilidade**: 99.999999999% (11 noves) e disponibilidade de 99.99%.  
- **Recursos Adicionais**: Versionamento, políticas de lifecycle, logs de acesso, criptografia (SSE-S3, SSE-KMS), ACLs.  

**Casos de Uso**:  
- Hospedagem de sites estáticos.  
- Backup e recuperação de desastres (DR).  
- Data lakes (integração com serviços como Athena e Redshift).  
- Armazenamento de logs, mídia (imagens, vídeos) e distribuição de conteúdo via CloudFront.  

**Quando Usar**:  
- Dados não estruturados (ex: arquivos de mídia).  
- Cenários que exigem acesso global via HTTP/HTTPS.  
- Arquiteturas serverless (ex: integração com Lambda).  

---

### **2. Amazon EBS (Elastic Block Store)**
**O que é**:  
- **Armazenamento em bloco** persistente e de baixa latência, anexado a instâncias EC2.  
- Funciona como um disco rígido virtual (volumes são provisionados em uma única AZ).  

**Principais Tipos de Volume**:  
- **gp3/SSD**: Uso geral (balanceamento entre custo e desempenho).  
- **io1/SSD**: Alta performance (IOPS provisionados para bancos de dados).  
- **st1/HDD**: Throughput otimizado (big data, data warehouses).  
- **sc1/HDD**: Custo mais baixo (dados acessados raramente).  

**Casos de Uso**:  
- Sistemas de arquivos para EC2 (ex: discos de boot).  
- Bancos de dados (RDBMS como MySQL, PostgreSQL).  
- Aplicações que exigem baixa latência (ex: transações em tempo real).  

**Quando Usar**:  
- Workloads que requerem armazenamento persistente e acoplado a uma instância EC2.  
- Necessidade de snapshots incrementais (backup via EBS Snapshots para S3).  

---

### **3. Amazon EFS (Elastic File System)**
**O que é**:  
- **Armazenamento de arquivos** totalmente gerenciado, escalável e compartilhado (NFS).  
- Compatível com múltiplas instâncias EC2 e serviços serverless (Lambda, ECS).  

**Principais Recursos**:  
- **Escalabilidade Automática**: Cresce ou diminui conforme o uso.  
- **Modos de Desempenho**:  
  - **General Purpose**: Para maioria dos casos (ex: CMS, home directories).  
  - **Max I/O**: Alta paralelização (ex: big data analytics).  
- **Disponibilidade**: Multi-AZ (padrão) ou One Zone (custo reduzido).  

**Casos de Uso**:  
- Sistemas de arquivos compartilhados entre instâncias EC2 (ex: CMS como WordPress).  
- CI/CD pipelines (compartilhamento de artefatos).  
- Aplicações de machine learning com acesso paralelo a dados.  

**Quando Usar**:  
- Dados que precisam ser acessados por múltiplas instâncias ou serviços simultaneamente.  
- Workloads que exigem baixa latência e alta throughput (ex: processamento de mídia).  

---

### **4. Amazon S3 Glacier**
**O que é**:  
- Serviço de **armazenamento de arquivamento** de baixo custo, para dados raramente acessados.  
- **Recursos**:  
  - **Glacier Instant Retrieval**: Recuperação em milissegundos (para dados acessados 1-2 vezes/ano).  
  - **Glacier Flexible Retrieval**: Recuperação em minutos (3-5 horas) ou horas (5-12 horas).  
  - **Glacier Deep Archive**: Custo mais baixo, recuperação em até 48 horas.  

**Casos de Uso**:  
- Arquivos de compliance (ex: registros financeiros por 7 anos).  
- Backups de longo prazo (ex: snapshots EBS antigos).  
- Dados científicos ou históricos.  

**Quando Usar**:  
- Dados que não exigem acesso rápido, mas precisam ser mantidos por anos.  
- Cumprimento de regulamentações (ex: LGPD, GDPR).  

---

### **Comparação entre os Serviços**

| **Critério**              | **S3**                          | **EBS**                          | **EFS**                          | **Glacier**                      |
|---------------------------|----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|
| **Tipo de Armazenamento**  | Objetos (HTTP/HTTPS).           | Bloco (disco virtual).            | Arquivos (NFS).                   | Arquivos/Objetos (arquivamento).  |
| **Acesso**                | Global (via internet).           | Apenas pela instância EC2 anexada. | Multi-AZ, múltiplas instâncias.   | Via API ou console (retrieval lento). |
| **Durabilidade**          | 99.999999999% (11 noves).        | 99.8%-99.9% (depende do tipo).    | 99.999999999% (11 noves).         | 99.999999999% (11 noves).         |
| **Custo**                 | Pago por GB/mês e transferência. | Pago por GB provisionado.         | Pago por GB usado.                | Mais barato que S3 (custos de retrieval). |
| **Latência**              | Milissegundos (exceto Glacier).  | Sub-milissegundos (baixa).        | Milissegundos.                    | Minutos a horas (depende do tier). |
| **Escalabilidade**        | Ilimitada.                       | Até 16 TB por volume.             | Automática e ilimitada.           | Ilimitada.                        |

---

### **Quando Usar Cada Serviço?**
#### **Cenário 1: Site Estático com Alto Tráfego**  
- **Serviço**: **S3** + CloudFront.  
- **Por quê?** Baixo custo, alta disponibilidade e integração com CDN.  

#### **Cenário 2: Banco de Dados em EC2**  
- **Serviço**: **EBS (io1/gp3)**.  
- **Por quê?** Baixa latência e IOPS altos para transações rápidas.  

#### **Cenário 3: Sistema de Arquivos Compartilhado**  
- **Serviço**: **EFS**.  
- **Por quê?** Acesso simultâneo de múltiplas instâncias (ex: CMS).  

#### **Cenário 4: Backup de Longo Prazo**  
- **Serviço**: **S3 Glacier Deep Archive**.  
- **Por quê?** Custo mínimo para dados raramente acessados.  

---

### **Melhores Práticas para o Exame SAA-C03**
1. **S3**:  
   - Use **versionamento** para proteger contra exclusões acidentais.  
   - Configure **lifecycle policies** para mover dados para Glacier após um período.  
2. **EBS**:  
   - Use **snapshots** para backups incrementais (armazenados no S3).  
   - Escolha **gp3** para uso geral e **io1** para workloads de alta performance.  
3. **EFS**:  
   - Use **Throughput Mode** para workloads que exigem alta velocidade (ex: vídeo editing).  
4. **Glacier**:  
   - Priorize **Flexible Retrieval** para balancear custo e tempo de acesso.  

---

### **Exemplo de Pergunta no Exame**
**Cenário**: Uma empresa precisa armazenar logs de aplicação por 1 ano, com acesso esporádico para auditoria.  
**Resposta Correta**: **S3 Standard-IA** ou **S3 Glacier Flexible Retrieval**.  
**Por quê?** Custo reduzido para dados acessados raramente, mantendo a durabilidade.  

---

### **Conclusão**
- **S3**: Objetos, global, uso geral.  
- **EBS**: Bloco, acoplado a EC2, baixa latência.  
- **EFS**: Arquivos compartilhados, multi-instância.  
- **Glacier**: Arquivos/objetos, arquivamento de baixo custo.  
