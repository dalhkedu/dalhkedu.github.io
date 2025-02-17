---
title: "Famílias de Instâncias EC2"
---

Na AWS, as instâncias EC2 são divididas em famílias – cada uma projetada para tipos específicos de cargas de trabalho – e em tamanhos (nano, micro, small, medium, large, etc.) que determinam a quantidade de CPU, memória, armazenamento e rede disponíveis. Aqui está uma explicação simples e recomendações para dois cenários comuns:

---

### Famílias de Instâncias EC2

1. **Família T (Burstable Performance):**  
   - **Características:** Possuem desempenho base com a capacidade de "estourar" (burst) para cargas de trabalho de curta duração.  
   - **Tamanhos Comuns:** t2.micro, t3.small, t3a.medium.  
   - **Recomendação:** Indicadas para ambientes de desenvolvimento, sites de baixo tráfego ou tarefas que não exigem desempenho constante.  
   - **Uso para VMs:** Ideal para pequenos servidores web, testes e ambientes de desenvolvimento.

2. **Família M (General Purpose):**  
   - **Características:** Equilíbrio entre CPU, memória e rede.  
   - **Tamanhos Comuns:** m5.large, m5.xlarge, m6g.2xlarge.  
   - **Recomendação:** Uma escolha versátil para a maioria das aplicações, desde servidores web até bancos de dados de pequeno e médio porte.
   - **Uso para VMs:** Ótima para aplicações empresariais, servidores de aplicação e workloads que precisam de equilíbrio de recursos.

3. **Família C (Compute Optimized):**  
   - **Características:** Otimizadas para cargas de trabalho que exigem alto poder de processamento (CPU intensiva).  
   - **Tamanhos Comuns:** c5.large, c5.xlarge, c6g.2xlarge.  
   - **Recomendação:** Recomendadas para processamento em lote, aplicações de machine learning e servidores web que processam cálculos pesados.

4. **Família R (Memory Optimized):**  
   - **Características:** Oferecem mais memória por vCPU, ideal para aplicações que dependem de alta capacidade de memória.  
   - **Tamanhos Comuns:** r5.large, r5.xlarge, r6g.2xlarge.  
   - **Recomendação:** Indicadas para bancos de dados, caches em memória (como Redis ou Memcached) e análises em tempo real que exigem grande quantidade de memória.
   - **Uso para Bancos de Dados:** A família R é geralmente preferida para bancos de dados e aplicações que precisam processar grandes volumes de dados em memória.

5. **Outras Famílias (I, P, G, etc.):**  
   - **I (Storage Optimized):** Projetadas para workloads que exigem alta performance de I/O, como bancos de dados NoSQL ou sistemas de processamento de transações com alta demanda de armazenamento.
   - **P/G (GPU Instances):** Para aplicações de machine learning, renderização 3D, e processamento gráfico intensivo.

---

### Recomendações de Abordagem

- **Para Criar Máquinas Virtuais (Servidores Web, Aplicações):**  
  - **Ambientes de Desenvolvimento ou Teste:** Famílias T (por exemplo, t3.micro ou t3.small) são econômicas e permitem testes sem custos altos.  
  - **Ambientes de Produção:** Famílias M ou C são mais adequadas – a escolha dependerá se sua aplicação é mais equilibrada ou se é intensiva em processamento.  
  - **Dimensionamento:** Comece com um tamanho menor (por exemplo, medium) e ajuste conforme a demanda aumenta, utilizando Auto Scaling para gerenciar picos de tráfego.

- **Para Criar Bancos de Dados:**  
  - **Bancos Relacionais ou NoSQL:** Instâncias das famílias M e, especialmente, R (Memory Optimized) são recomendadas para oferecer maior capacidade de memória e desempenho consistente.  
  - **Cenários de Alto Desempenho:** Se o banco de dados exigir processamento intensivo (como para cargas analíticas), considere também as instâncias com alto desempenho de I/O ou compute (algumas vezes combinando R com I para armazenamento rápido).

---

### Resumo Final

- **Famílias T:** Para workloads leves e de teste, com possibilidade de burst de desempenho.  
- **Famílias M:** Equilibradas para a maioria das aplicações e servidores web.  
- **Famílias C:** Quando o foco é processamento intenso (CPU).  
- **Famílias R:** Para bancos de dados e aplicações que demandam muita memória.