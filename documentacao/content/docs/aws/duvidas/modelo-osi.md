---
title: "OSI"
---

O modelo **OSI (Open Systems Interconnection)** é um modelo de referência que define uma arquitetura de comunicação em redes de computadores, dividindo o processo de comunicação em sete camadas distintas. Cada camada tem funções específicas e interage com as camadas adjacentes, permitindo uma implementação modular e independente do hardware. Confira um resumo das sete camadas:

1. **Camada Física**  
   - Responsável pela transmissão dos bits através de meios físicos (cabos, fibras ópticas, rádio, etc.).  
   - Define os aspectos elétricos, mecânicos e funcionais para a transmissão dos sinais.

2. **Camada de Enlace de Dados**  
   - Garante a transferência confiável de dados entre dispositivos conectados fisicamente.  
   - Lida com a detecção e correção de erros na transmissão, além de gerenciar o acesso ao meio.

3. **Camada de Rede**  
   - Responsável pelo roteamento e encaminhamento dos pacotes entre diferentes redes.  
   - Define endereçamento lógico (como o IP) e escolhe o melhor caminho para a transmissão dos dados.

4. **Camada de Transporte**  
   - Assegura a entrega correta e ordenada dos dados entre os sistemas finais.  
   - Gerencia a segmentação, reagrupamento, controle de fluxo e a detecção de erros (ex.: TCP e UDP).

5. **Camada de Sessão**  
   - Gerencia as sessões de comunicação entre aplicações, estabelecendo, mantendo e finalizando conexões.  
   - Coordena a troca de dados, garantindo que a comunicação seja organizada e sincronizada.

6. **Camada de Apresentação**  
   - Responsável pela tradução, criptografia, compressão e formatação dos dados, garantindo que a informação seja compreendida pela aplicação receptora.  
   - Atua como um tradutor entre diferentes formatos de dados.

7. **Camada de Aplicação**  
   - Fornece serviços de rede diretamente aos usuários e aplicações (ex.: e-mail, FTP, HTTP).  
   - É a interface com a qual os programas de aplicação interagem para enviar e receber dados.

Essa divisão em camadas facilita o desenvolvimento, a manutenção e a interoperabilidade entre sistemas heterogêneos, permitindo que cada camada evolua ou seja substituída independentemente, sem afetar as demais.  
