---
title: "Simulado: Amazon S3"
---

### **Simulado: Amazon S3**

#### **1. Qual das seguintes opções é a mais eficiente para reduzir custos ao armazenar dados raramente acessados, mas que precisam estar disponíveis em milissegundos quando solicitados?**
A) S3 Glacier  
B) S3 Intelligent-Tiering  
C) S3 Standard-IA  
D) S3 One Zone-IA  

**Resposta:** B) S3 Intelligent-Tiering  
**Explicação:** O S3 Intelligent-Tiering move automaticamente os dados entre camadas de acesso frequente e infrequente com base no padrão de acesso, garantindo disponibilidade imediata e otimização de custos.

---

#### **2. Você está configurando um bucket S3 para armazenar logs de aplicações. Os logs devem ser armazenados por 90 dias e depois excluídos automaticamente. Qual é a melhor maneira de implementar isso?**
A) Usar uma política de bucket para excluir objetos após 90 dias.  
B) Configurar uma regra de ciclo de vida para expirar objetos após 90 dias.  
C) Usar o S3 Glacier para arquivar os logs após 90 dias.  
D) Habilitar o versionamento e excluir manualmente os logs após 90 dias.  

**Resposta:** B) Configurar uma regra de ciclo de vida para expirar objetos após 90 dias.  
**Explicação:** As regras de ciclo de vida permitem automatizar a exclusão de objetos após um período especificado, o que é ideal para gerenciar logs.

---

#### **3. Você precisa garantir que todos os objetos carregados em um bucket S3 sejam cifrados. Qual das seguintes opções é a mais segura e escalável?**
A) Cifrar os objetos manualmente antes do upload.  
B) Usar SSE-S3 (Server-Side Encryption com chaves gerenciadas pela S3).  
C) Usar uma política de bucket para rejeitar objetos não cifrados.  
D) Habilitar o versionamento para garantir a cifragem.  

**Resposta:** C) Usar uma política de bucket para rejeitar objetos não cifrados.  
**Explicação:** Uma política de bucket pode ser configurada para negar operações de upload que não incluam cabeçalhos de cifragem, garantindo que todos os objetos sejam cifrados.

---

#### **4. Qual das seguintes opções é verdadeira sobre o S3 Select?**
A) Ele permite consultar dados diretamente no S3 usando SQL, sem a necessidade de carregá-los em outro serviço.  
B) Ele só funciona com objetos armazenados no S3 Glacier.  
C) Ele requer a configuração de um cluster do Amazon Redshift.  
D) Ele não suporta a consulta de arquivos CSV ou JSON.  

**Resposta:** A) Ele permite consultar dados diretamente no S3 usando SQL, sem a necessidade de carregá-los em outro serviço.  
**Explicação:** O S3 Select permite consultar dados em formatos como CSV, JSON e Parquet diretamente no S3, sem a necessidade de mover ou processar os dados em outro serviço.

---

#### **5. Você está projetando uma arquitetura para armazenar dados de sensores IoT em tempo real. Os dados devem ser armazenados no S3 e processados em tempo real. Qual serviço da AWS você usaria para ingerir os dados no S3?**
A) Amazon Kinesis Data Firehose  
B) AWS Glue  
C) Amazon Athena  
D) Amazon EMR  

**Resposta:** A) Amazon Kinesis Data Firehose  
**Explicação:** O Kinesis Data Firehose é projetado para ingestão de dados em tempo real e pode entregar os dados diretamente no S3, além de integrar-se com outros serviços para processamento.

---

#### **6. Qual das seguintes opções é uma prática recomendada para otimizar o desempenho ao carregar grandes volumes de dados no S3?**
A) Usar Transfer Acceleration para todos os uploads.  
B) Dividir os dados em partes menores e usar Multipart Upload.  
C) Armazenar os dados em um único arquivo grande.  
D) Usar o S3 Glacier para uploads grandes.  

**Resposta:** B) Dividir os dados em partes menores e usar Multipart Upload.  
**Explicação:** O Multipart Upload melhora o desempenho e a confiabilidade ao carregar grandes volumes de dados, permitindo que partes do arquivo sejam carregadas em paralelo.

---

#### **7. Você precisa garantir que um bucket S3 seja acessível apenas a partir de uma VPC específica. Como você pode implementar isso?**
A) Usar uma política de bucket com uma condição que restrinja o acesso à VPC.  
B) Configurar um endpoint de gateway da VPC para o S3.  
C) Usar uma ACL para restringir o acesso à VPC.  
D) Habilitar o versionamento no bucket.  

**Resposta:** A) Usar uma política de bucket com uma condição que restrinja o acesso à VPC.  
**Explicação:** As políticas de bucket podem incluir condições para restringir o acesso com base no endpoint da VPC, garantindo que apenas recursos dentro da VPC possam acessar o bucket.

---

#### **8. Qual das seguintes opções é verdadeira sobre o S3 Glacier Deep Archive?**
A) Ele é projetado para dados que precisam ser acessados em milissegundos.  
B) Ele tem um tempo de recuperação de 12 horas ou mais.  
C) Ele não suporta a integração com regras de ciclo de vida do S3.  
D) Ele é mais caro que o S3 Standard.  

**Resposta:** B) Ele tem um tempo de recuperação de 12 horas ou mais.  
**Explicação:** O S3 Glacier Deep Archive é a classe de armazenamento mais econômica da AWS, projetada para dados raramente acessados, com tempos de recuperação de 12 horas ou mais.

---

#### **9. Você precisa garantir que todos os objetos em um bucket S3 sejam armazenados em uma única zona de disponibilidade para reduzir custos. Qual classe de armazenamento você deve usar?**
A) S3 Standard  
B) S3 Intelligent-Tiering  
C) S3 One Zone-IA  
D) S3 Glacier  

**Resposta:** C) S3 One Zone-IA  
**Explicação:** O S3 One Zone-IA armazena dados em uma única zona de disponibilidade, o que reduz custos em comparação com outras classes que replicam dados em várias zonas.

---

#### **10. Qual das seguintes opções é uma vantagem do versionamento do S3?**
A) Reduzir o custo de armazenamento.  
B) Permitir a recuperação de objetos excluídos ou sobrescritos.  
C) Automatizar a transição de objetos para o S3 Glacier.  
D) Melhorar o desempenho de leitura dos objetos.  

**Resposta:** B) Permitir a recuperação de objetos excluídos ou sobrescritos.  
**Explicação:** O versionamento do S3 mantém múltiplas versões de um objeto, permitindo a recuperação de versões anteriores em caso de exclusão acidental ou sobrescrita.

---

### **Resumo das Respostas**
1. B) S3 Intelligent-Tiering  
2. B) Configurar uma regra de ciclo de vida para expirar objetos após 90 dias.  
3. C) Usar uma política de bucket para rejeitar objetos não cifrados.  
4. A) Ele permite consultar dados diretamente no S3 usando SQL.  
5. A) Amazon Kinesis Data Firehose  
6. B) Dividir os dados em partes menores e usar Multipart Upload.  
7. A) Usar uma política de bucket com uma condição que restrinja o acesso à VPC.  
8. B) Ele tem um tempo de recuperação de 12 horas ou mais.  
9. C) S3 One Zone-IA  
10. B) Permitir a recuperação de objetos excluídos ou sobrescritos.  

---
