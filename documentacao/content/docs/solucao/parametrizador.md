Normalização parametrizador

Para criação de areas novas e manutenção das antigas
Deleção é fisica:

Situações:
Ativo - Situação de ativação area está sendo usada.
Rascunho - Situação de rascunho area não está ativa para o ambiente.

Controle de acesso via funcional:

Perfil:
Editor
Criador
Administrador
Consultor

Parametrizador:
Editor: Pode editar dados não criticos das areas do produto.
Criador: Pode criar novas areas para o produto.
Consultor: Pode visualizar dados das areas do produto.
Administrador: Pode editar, criar, consultar e adicionar novos integrantes as areas do produtos.

Portal de Documentos:
Editor: Pode editar dados não criticos das das ordens ja em andamento e editar dados de ordens rascunho do produto.
Criador: Pode criar novas ordens e executar ordens em rascunho para areas para o produto.
Consultor: Pode visualizar dados das ordens para areas do produto. (pode reenviar email, links, telefones via botoes disponiveis)
Administrador: Pode editar, criar e consultar ordens para as areas do produtos.

O que tem no parametrizador:
Todos os dados do parametrizador são baseados nos dominios existentes, sendo assim o parametrizador nada mais é que um gerador de possibilidade para os produtos criar suas ordens de maneira que determine os limites juridicos de cada produto nao podendo por exemplo criar ordens com assinaturas simples.

Dominios:
Area
    id da area
    sigla
    centro de custo
    plataforma
    notificacao
    participante
    retorno
    poder
Plataforma
    meio de assinatura
    funcionalidade
Meio de assinatura
    tipo
Funcionalidade
    tipo
Notificacao
    sigla
    layout
    meio de assinatura
    plataforma
    tipo
    variaveis
    participante
Poder
    agrupamento
    servico
    papel
    meio de assinatura
    plataforma
Retorno (callback)
    sigla
    tipo
Participante
    sigla
    tipo
    codigo pessoa
    papel
    plataforma
    meio de assinatura
    certificado
Ambiente
    Area
Usuario
    Ambiente
    Area
    Plataforma

Script de deploy de ambiente
    Para cada adição de nova area por um produto em ambiente de sandbox é gerado um script de deploy de ambiente que deve ser armazenado em uma fila fifo que será executado quando o produto selecionar o ambiente de migração podemos realizar via automatização ou vpc peering

Sandbox
    Espaço para criar pequenos padrões de simulação para testes nos ambientes

Uma plataforma tem um ou muitos meios de assinatura
Um meio de assinatura tem uma ou muitas plataformas
Um meio de assinatura tem nenhum ou muitas funcionalidades
Uma funcionalidade tem nenhum ou muitos meios de assinatura
Uma plataforma tem nenhum ou muitas funcionalidades
Uma funcionalidade tem nhum ou muitas plataformas
Uma area tem um ou muitas plataformas
uma plataforma esta nenhum ou muitas areas
Uma area tem nenhum ou muitos poderes
Um poder esta uma ou muitas areas
Um poder e consultado em um ou muitos meios de assinatura
Um meio de assinatura tem nenhum ou muitos poderes
Um poder e consultado em um ou muitas funcionalidades
Uma funcionalidade tem nenhum ou muitos poderes
Uma area tem nenhum ou muitos participantes
Um participante esta uma ou muitas areas
Um participante assina com um ou muitos meio de assinatura
Um meio de assinatura tem nenhum ou muitos participantes
Um participante participa de uma ou muitas plataformas
Uma plataforma tem nenhum ou muitos participantes
Uma area tem nenhum ou muitos retornos
Um retorno esta em nenhuma ou muitas areas
Uma area tem nenhuma ou muitas notificações
Uma notificação está em uma ou muitas areas
Uma notificação tem um ou nenhum participante
Um participante tem nenhum ou uma notificação
Uma notificação tem uma ou muitas plataformas
Uma platafroma tem nenhum ou muitas notificação
Uma notificação tem um ou muitos meios de assinatura
Um meio de assinatura tem nenhum ou muitas notificacoes
Uma area esta em um ou muitos ambientes
Um ambiente tem nenhum ou muitas areas
Um usuario pode um ou muitas areas
Uma area poder ter um e muitos usuarios
Um usuario tem um ou muitos perfis
Um perfil tem nenhum ou muitos usuarios
Um usuário um ou muitas plataformas(param/portal)
Uma plataforma(interna) tem nenhum ou muitos usuários
Um ambiente tem nenhum ou muitos usuarios
Um usuário pode acessar um ou muitos ambientes

UX:
Tela de pedido de criação de usário (caso nao tenha usuário com acesso)
Tela de lista de areas (vazio ainda nao tem area e caso tem acesso com usuario) botao de criar so ficara presente para adm e criador - situação criada não deve aparecer para consultor
Tela de criação de area (todas as etapas)
    Consumir api de comunidades, rts, squads e siglas (area pode ser a nivel de comunidade ate nivel de sigla(squad))
    Consumir lista de centro de custos para preenchimento
    Notificação email oferecer um botão para testar o disparo do layuot para um email digitado para teste.
    Notificação SMS oferecer um botão para testar o disparo do layuot para um telefone digitado para teste.
    Notificação Whats oferecer um botão para testar o disparo do layuot para um telefone digitado para teste.
    Poderes oferecer um botão para uma consulta de poder para um cnpj para teste
    Callback oferecer um botão para testes de notificação para a area webhook/kafka
    Participante oferecer sandbox de ordem simples com o participante e mais um caso ele seja vistador/observador
    Adicionar (i) infos para cada categoria e dados dos dominios.
    Adicionar pequenos slides/videos em modais para visualização do uso do dominio.
    Promoção de ambientes deve ser 1 a 1 se estou em sandbox posso levar para hom (via somente adm) e de hom para produção.
    Gestão de usuarios só ficara presente para adm
    Somente adm e criador podem criar e ativar uma area
    Participante buscar quando digitar cpf e verificar se o mesmo ja nao esta cadastrador para outra area do mesmo produto.
Tela de Consulta e sandbox (ambientes sandox e hom) sandbox em produção somente para adm
Tela de edição (so nao parece para consultor)
