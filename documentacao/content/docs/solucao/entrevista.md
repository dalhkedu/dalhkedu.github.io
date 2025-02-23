# Proposta

Voce foi contratado para uma area de engenharia de dados em uma startup de crédito, que acabou de iniciar suas operações. A empresa oferece credito por meio de uma plataforma digital, e todas as decisões de concessão de credito são feitas com base em regras de negocio e analise de dados transacionais dos cliente.
Atualmente, os dados da empresa estão fragmentados entre diferentes sistemas operacionais (bd do app, log de eventos, apis de terceiros e dados bancários). Sua missão será estruturar um produto de dados que permita análises, geração de relatórios e otimização do modelo de crédito.

## Objetivo

Unificar e integrar dados fragmentados (banco de dados do app, logs de eventos, APIs de terceiros, dados bancários) em uma plataforma centralizada que permita análises detalhadas, geração de relatórios e melhoria contínua dos modelos de crédito.

## Características Principais

* Escalabilidade: Aproveitar serviços gerenciados e serverless para suportar picos e crescimento contínuo dos dados.
* Custo-Efetividade: Utilizar modelos de consumo sob demanda e armazenamento de baixo custo (ex.: S3 com classes de armazenamento adequadas) e instâncias spot ou escaláveis para processamento.
* Governança e Segurança: Adotar políticas rígidas com criptografia, controle de acesso granular e monitoramento intensivo, dada a sensibilidade dos dados financeiros.
* Monitoramento e Observabilidade: Integrar o DataDog para coleta de métricas, logs e monitoramento de performance e segurança em toda a arquitetura.

### Etapa 1

O time de produto precisa de um dashboard em tempo real que exiba os pedidos de credito feito pelos clientes e seus status de aprovação. A empresa usa um banco de dados relacional (postgresql) para armazenar os pedidos e um sistema externo que avalia o risco de credito via api.

### Seu desafio é projetar uma pipeline de dados transacional que

1. Capture e processe em tempo real os novos pedidos de credito.
2. integre a resposta da api externa de avaliação de risco ao pedido do cliente.
3. garanta a consistencia dos dados ao salvar o status final no banco.
4. Otimize a performance para evitar sobrecarga no banco operacional.

### Perguntas

* Qual tecnologia voce uitlizaria para processar esse fluxo em tempo real?
* Como garantiria a idempotencia das operações no ETL transacional?
* Como organizaria o modelo de dados para armazenar esses pedidos?
* Como garantiria escalabilidade caso o volume de pedidos aumentasse?

## Etapa 2

Agora, a equipe de credito quer fazer uma analise histórica dos pedidos aprovados e rejeitados para ajustar os creditos de concessão de crédito. Esses dados precisam ser armazenados em um data lake e integrados com outras fontes, como scores de crédito de terceiros.

### Seu desafio é criar um pipeline ETL Batch que

1. Extraia os pedidos de credito e suas respectivas avaliações do banco de dados transacional.
2. Enriqueça os dados com informações de fontes externas.
3. Transforme e normalize os dados para que fiquem disponiveis para analise no data lake.
4. Processe os dados diariamente sem impactar o banco de produção.

### Perguntas

* Como organizaria a arquitetura do ETL BAtch e quis ferramentas usaria?
* Como garantiria a qualidade e rastreabilidade dos dados?
* Como lidaria com dados faltantes ou inconsistentes?
* Como definiria um modelo de particionamento eficiente no data lake?

## Etapa 3

A diretoria quer criar um produto de dados interno para oferecer insights sobre o comportamento dos clientes. Hoje, os dados estão dispersos e não há um modelo estruturado para analise.

### Sua missão

1. Definir um modelo de dados para centralizar as informações dos clientes, pedidos e comportamento de uso da plataforma.
2. Escolher a stack tecnologica para construir esse produto de dados.
3. Criar uma arquitetura que permita consultas rápidas e flexiveis.
4. Implementar um fluxo de atualização de dados, garantindo integridade e eficiencia.

### Perguntas

* Como estruturaria esse produto de dados?
* Como garantiria governança e controle de acesso as informações sensiveis?
* Como disponibilizaria esses dados para diferentes times (exemplo: financeiro, marketing e credito)?
* Como projetaria um modelo de dados escalavel para futuros produtos analiticos?

E por fim com as melhores praticas recomendadas e garantindo uma economia financeira que possibilitaria um planejmanento de evolução de escala e custos.
