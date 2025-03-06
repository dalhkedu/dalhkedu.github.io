Claro! Aqui está um simulado de múltipla escolha focado no **Amazon Rekognition** e sua aplicação aos domínios das certificações AWS, como **AWS Certified Machine Learning – Specialty** e **AWS Certified Security – Specialty**. As respostas e explicações estão no final.

---

### **Simulado: Amazon Rekognition**  
**1. Uma empresa deseja identificar defeitos em produtos usando visão computacional, mas os objetos específicos não são cobertos pelos modelos pré-treinados do Rekognition. Qual funcionalidade deve ser usada?**  
a) Detecção de Celebridades  
b) Custom Labels  
c) Moderação de Conteúdo  
d) Reconhecimento Facial  

**2. Qual caso de uso do Rekognition está mais alinhado à conformidade com políticas de segurança em redes sociais?**  
a) Detecção de texto em imagens  
b) Análise de emoções em rostos  
c) Moderação de conteúdo explícito  
d) Rastreamento de pessoas em vídeos  

**3. Para implementar um sistema de controle de acesso baseado em reconhecimento facial, qual combinação de serviços AWS é mais adequada?**  
a) Rekognition + Amazon S3  
b) Rekognition + AWS Lambda + API Gateway  
c) Rekognition + Amazon Redshift  
d) Rekognition + Amazon EC2  

**4. Como o Amazon Rekognition é cobrado?**  
a) Por hora de uso de instâncias EC2  
b) Por quantidade de dados armazenados no S3  
c) Por imagem analisada e minuto de vídeo processado  
d) Por número de modelos treinados  

**5. Um arquiteto precisa garantir que as imagens processadas pelo Rekognition sejam criptografadas em repouso. Qual serviço AWS deve ser configurado?**  
a) AWS KMS  
b) Amazon CloudFront  
c) AWS Direct Connect  
d) Amazon RDS  

**6. Qual funcionalidade do Rekognition é usada para detectar atividades suspeitas em vídeos de vigilância?**  
a) Custom Labels  
b) Rastreamento de Pessoas  
c) Detecção de Celebridades  
d) OCR (Detecção de Texto)  

**7. Para filtrar automaticamente imagens inadequadas em um aplicativo de compartilhamento de fotos, qual recurso do Rekognition é mais indicado?**  
a) Reconhecimento Facial  
b) Moderação de Conteúdo  
c) Detecção de Objetos  
d) Análise de Emoções  

**8. Qual serviço do Rekognition permite extrair texto manuscrito de imagens para digitalização de documentos?**  
a) Custom Labels  
b) Detecção de Texto (OCR)  
c) Detecção de Cenas  
d) Face Liveness  

**9. Um varejista quer analisar o fluxo de clientes em lojas físicas usando câmeras. Qual funcionalidade do Rekognition deve ser utilizada?**  
a) Detecção de Celebridades  
b) Rastreamento de Pessoas  
c) Moderação de Conteúdo  
d) Reconhecimento Facial  

**10. Qual recurso do Rekognition ajuda a prevenir fraudes em verificações de identidade online?**  
a) Face Liveness  
b) Custom Labels  
c) Detecção de Objetos  
d) Análise de Emoções  

---

### **Respostas e Explicações**  
1. **b) Custom Labels**  
   - O **Custom Labels** permite treinar modelos personalizados para reconhecer objetos específicos (ex: defeitos), essencial para casos não cobertos por modelos pré-treinados (**Machine Learning – Specialty**).  

2. **c) Moderação de conteúdo explícito**  
   - A moderação de conteúdo ajuda a bloquear material inadequado, garantindo conformidade com políticas de segurança (**Security – Specialty**).  

3. **b) Rekognition + AWS Lambda + API Gateway**  
   - A combinação permite criar uma API escalável para processar imagens em tempo real e acionar lógica de acesso (**Solutions Architect – Associate**).  

4. **c) Por imagem analisada e minuto de vídeo processado**  
   - O Rekognition segue modelo "pay-as-you-go", cobrado por uso de recursos, não por instâncias ou armazenamento (**Cloud Practitioner**).  

5. **a) AWS KMS**  
   - O AWS Key Management Service (KMS) gerencia criptografia de dados em repouso, requisito crítico para segurança (**Security – Specialty**).  

6. **b) Rastreamento de Pessoas**  
   - O rastreamento analisa movimentos e poses em vídeos, útil para vigilância (**Machine Learning – Specialty**).  

7. **b) Moderação de Conteúdo**  
   - A moderação identifica conteúdo explícito (ex: nudez, violência), alinhado a políticas de segurança (**Security – Specialty**).  

8. **b) Detecção de Texto (OCR)**  
   - O OCR extrai texto impresso ou manuscrito de imagens, aplicável a digitalização de documentos (**Machine Learning – Specialty**).  

9. **b) Rastreamento de Pessoas**  
   - O rastreamento monitora trajetórias e densidade de clientes em vídeos, útil para análise de fluxo (**Solutions Architect – Associate**).  

10. **a) Face Liveness**  
    - O **Face Liveness** detecta se a imagem facial é de uma pessoa real (e não uma foto), prevenindo fraudes (**Security – Specialty**).  

---

### **Dicas para Certificações**  
- **Machine Learning – Specialty:** Foque em **Custom Labels**, métricas de avaliação e integração com SageMaker.  
- **Security – Specialty:** Estude moderação de conteúdo, criptografia com KMS e **Face Liveness**.  
- **Solutions Architect – Associate:** Entenda arquiteturas escaláveis com Lambda, S3 e API Gateway.  

O Amazon Rekognition é uma ferramenta versátil para aplicações de visão computacional, e seu domínio é crucial para certificações AWS focadas em **ML** e **segurança**. 📸🔒