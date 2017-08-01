---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Analisando a atividade do usuário
{: #dashboard}

A página Métricas de participação contém um painel com visualizações que o ajudam a ganhar insights de dados que são coletados pelo agente virtual.
{: shortdesc}

## Antes de começar

A sua instância do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}
deve ser implementada e os usuários devem participar de conversas com o seu agente virtual por pelo menos 30 minutos antes do painel ter qualquer dado para
compartilhar.

## Sobre essa Tarefa

As métricas na página são atualizadas a cada 30 minutos com dados de conversas que ocorrem entre o agente virtual e os seus usuários. Elas fornecem insights sobre coisas como:

- Quantas conversas estão acontecendo
- Quantos usuários, novos e que retornam, estão participando de conversas com o agente virtual
- O que os clientes querem fazer ou aprender sobre mais e menos (com base em quais intenções são mais e menos frequentemente acionadas)

As métricas podem ajudá-lo a localizar áreas nas quais algum trabalho adicional pode melhorar significativamente o desempenho do agente virtual:

- Compare os tópicos populares para as intenções e entidades que o serviço é treinado para reconhecer. Quaisquer diferenças podem ajudá-lo a descobrir novas
intenções ou terminologia sobre as quais é possível ensinar o agente virtual.
- Revise as intenções que são identificadas na maioria das vezes logo antes de os usuários solicitarem falar com um agente humano. Investigar as causas de
escaladas pode ajudá-lo a priorizar onde concentrar esforços de treinamento futuro. É possível determinar se as consultas do usuário estão sendo mal interpretadas, se
o seu serviço tem uma intenção comum completamente ausente, se as respostas que são associadas com uma intenção precisam melhorar e assim por diante.

As métricas também podem ajudá-lo a planejar as designações de recurso de agente humano com base em dados sobre os locais geográficos nos quais o uso do agente
virtual é mais e menos comum, bem como os horários de pico de conversa.

As métricas analisam os dados de conversas em um baixo nível, concentrando-se nos artefatos que compõem os recursos, incluindo:

- **Entidades**

    Uma *entidade* representa um termo ou objeto que é relevante para uma intenção e que fornece um contexto específico para uma
intenção. Por exemplo, uma entidade pode representar uma cidade na qual o usuário deseja localizar um local de negócios ou a quantia de um pagamento de fatura. Na
interface com o usuário, o nome de uma entidade é sempre prefixado com o caractere `@`.

- **Intenções**

    Uma *intenção* representa o propósito de uma entrada do usuário. Cada recurso usa um classificador de língua natural que pode
avaliar uma elocução do usuário e localizar uma intenção predefinida se ela estiver presente. Na interface com o usuário, o nome de uma intenção é sempre prefixado
com o caractere `#`.

## Procedimento

1. Abra a página **Métricas de participação**.

    A parte superior da página tem um resumo de pontos de dados-chave e lhe dá uma percepção rápida de como está o andamento do agente virtual. Para cada ponto de
dados, a porcentagem de mudança que ocorreu durante o período que é selecionado é mostrada entre parênteses. (N/D) para *não disponível* é
exibido até o período de tempo transcorrer e uma mudança pode ser medida e exibida.

    Os números mostrados no resumo podem, às vezes, diferir dos números mostrados em outras páginas. Por exemplo, o número total de interações mostradas aqui
pode diferir do total mostrado na guia **Interações**. A diferença pode ocorrer porque as informações de resumo são agregadas e atualizadas em um
intervalo de 30 minutos enquanto a guia **Interações** é atualizada em tempo real.

    Realizar drill down nos dados em cada guia para saber mais.
    - **<b>Visão Geral**</b>

        Descubra sobre o que seus usuários desejam aprender ou o que desejam fazer quando eles se envolvem com o agente virtual, bem como quais os objetivos
do usuário o agente virtual não pôde satisfazer.
        - O diagrama interativo **Intenções e Entidades** fornece insight sobre como o serviço do
{{site.data.keyword.conversationshort}} está interpretando a entrada do usuário. Ele mostra quais as entidades foram usadas pelo serviço para ajudá-lo a
identificar a intenção do usuário.

            A sintaxe a seguir é usada para ajudá-lo a interpretar mais rapidamente as informações no diagrama:
            - `#<intent-name>`
            - `@<entity-name>`

            Clique em uma intenção para ver quais entidades ajudaram o serviço a entender a entrada do usuário como foi feita. Ou clique em uma entidade para
ver quais intenções ela ajudou o serviço a identificar.

        - O gráfico **Tópicos** captura palavras ou frases que são proferidas com mais frequência por usuários em uma conversa. Revise o
gráfico para entender sobre o que os usuários estão mais interessados em falar. As palavras neste gráfico são distintas das entidades que são capturadas no diagrama
Intenções e Entidades. Entidades são palavras que o serviço do {{site.data.keyword.conversationshort}} foi treinado para entender e associar com intenções
específicas. As palavras que são capturadas no gráfico Tópicos são apenas palavras que são mais frequentemente encontradas em conversas do usuário. Os dois podem ou
não podem se sobrepor. Fique de olho nas palavras no gráfico Tópicos para ficar em sintonia com os seus usuários e descubra coisas novas que eles podem querer fazer
ou aprender a respeito. Os tópicos populares que permanecem populares podem ser bons candidatos para novas entidades que podem ajudar o
{{site.data.keyword.watson}} a reconhecer as intenções existentes ou podem sugerir novas intenções para você ensinar o {{site.data.keyword.watson}}
a respeito.

    - **<b>Usuários
**</b>

        Obtenha informações sobre onde seus usuários estão localizados e o volume de conversas.

    - **<b>Interações**</b>

        Consulte as transcrições de conversas individuais.

        As transcrições não contêm informações pessoalmente identificáveis. Até o nome do usuário que participou da conversa é mantido privado; o termo
*Não fornecido* é usado em seu lugar. Quaisquer outras informações pessoalmente identificáveis que os usuários fornecem durante a conversa,
como números de telefone ou códigos de endereçamento postal, são substituídas por variáveis que indicam os tipos de dados que foram fornecidos, mas não os próprios dados.

        > **Nota:** O termo *interação* representa uma conversa que acontece entre o usuário e o agente virtual. Ela inicia quando o
usuário inicia um bate-papo com o agente virtual e é finalizada quando a sessão de janela de bate-papo é finalizada (que ocorre quando o usuário efetuou logout,
efetua logout, fecha a janela de bate-papo ou atualiza a janela de bate-papo). Uma interação geralmente inclui mais do que apenas uma troca de palavras; os usuários
podem clicar em botões, visualizar gráficos como mapas e executar outras transações. E, diferentemente de um telefonema para o suporte ao cliente, a interação com a
sessão de bate-papo do agente virtual não termina assim que o usuário para de se envolver com ela. O agente virtual não tem nenhum outro lugar para estar; ela é
interrompida em caso do usuário querer fazer ou perguntar sobre outra coisa. Por exemplo, se o usuário perguntar sobre algo, então, 20 minutos depois perguntar sobre
alguma outra coisa (e fizer isso dentro da mesma sessão de janela de bate-papo), então, ambas as trocas serão tratadas como uma única interação com uma duração de
cerca de 25 minutos.
1. Se você descobrir dados significativos que deseja compartilhar com outros, será possível exportá-los em formato CSV.

