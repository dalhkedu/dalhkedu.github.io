---
title: "Formato de dados"
---

### Formatos de Dados: JSON, XML, Parquet, Avro, ORC

#### JSON (JavaScript Object Notation)
- **Uso**: Muito utilizado em APIs e configurações de aplicativos.
- **Exemplo**: Armazenamento de dados em configurações de aplicativos, troca de dados entre servidores e clientes.
- **Vantagens**: Leitura e escrita humanamente legível, fácil de ser manipulado por linguagens de programação modernas.
- **Desvantagens**: Pode ser ineficiente para grandes volumes de dados.

#### XML (eXtensible Markup Language)
- **Uso**: Utilizado em documentos de configuração, troca de dados entre diferentes sistemas.
- **Exemplo**: Documentos de configuração de software, troca de dados em sistemas de mensagens.
- **Vantagens**: Estrutura hierárquica, amplamente suportado por diferentes plataformas e linguagens.
- **Desvantagens**: Verboso, pode ser ineficiente em termos de tamanho e processamento.

#### Parquet
- **Uso**: Armazenamento de grandes volumes de dados em data warehouses e data lakes.
- **Exemplo**: Armazenamento de dados de análise em Hadoop ou Spark.
- **Vantagens**: Alta compressão, eficiente para leitura e escrita de grandes volumes de dados.
- **Desvantagens**: Menos legível para humanos, requer ferramentas específicas para manipulação.

#### Avro
- **Uso**: Serialização de dados em sistemas distribuídos, especialmente em ambientes de big data.
- **Exemplo**: Armazenamento de dados em Hadoop, Kafka.
- **Vantagens**: Eficiente em termos de tamanho e velocidade, suporte a schema evolution.
- **Desvantagens**: Menos legível para humanos, requer ferramentas específicas para manipulação.

#### ORC (Optimized Row Columnar)
- **Uso**: Armazenamento de grandes volumes de dados em data warehouses e data lakes.
- **Exemplo**: Armazenamento de dados de análise em Hadoop ou Spark.
- **Vantagens**: Alta compressão, eficiente para leitura e escrita de grandes volumes de dados.
- **Desvantagens**: Menos legível para humanos, requer ferramentas específicas para manipulação.

### Diferença entre Dados Estruturados, Semi-Estruturados e Não Estruturados

#### Dados Estruturados
- **Definição**: Dados organizados em uma estrutura fixa, como tabelas de banco de dados.
- **Exemplo**: Bancos de dados relacionais, planilhas de Excel.
- **Características**: Fácil de analisar e processar, alta precisão.

#### Dados Semi-Estruturados
- **Definição**: Dados que possuem alguma estrutura, mas não são totalmente padronizados.
- **Exemplo**: Arquivos JSON, XML, Avro.
- **Características**: Flexível, pode ser analisado com ferramentas específicas, menos eficiente que dados estruturados.

#### Dados Não Estruturados
- **Definição**: Dados que não possuem uma estrutura definida, como texto, imagens e vídeos.
- **Exemplo**: E-mails, mensagens de chat, imagens.
- **Características**: Difícil de analisar e processar, requer técnicas avançadas de processamento de linguagem natural (NLP) e aprendizado de máquina.
