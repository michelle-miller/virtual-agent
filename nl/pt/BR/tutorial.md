---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-10"

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

# Tutorial: Incluindo recursos customizados 
{: #tutorial}

Este tutorial ajuda a entender como aumentar os recursos de seu agente virtual incluindo os seus próprios recursos.
{: shortdesc}

Neste tutorial, você usará a área de trabalho que alimenta a demo simples do {{site.data.keyword.conversationshort}} para incluir todos os novos
recursos em seu agente. A área de trabalho simula a função de um copiloto para alguém dirigindo um carro. É possível conferir a demo [aqui ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://conversation-simple.mybluemix.net/ "Ícone de link externo"){: new_window}. Após importar a área de trabalho em sua
instância de serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}, você vinculará a área de trabalho ao seu agente. Em
seguida, você incluirá as intenções de área de trabalho como recursos customizados e finalmente direcionará qualquer conflito que surgir entre os recursos principais
e os recursos que você incluir.

## Aprendendo objetivos

Após concluir este tutorial, você saberá como executar as tarefas a seguir:

- Vincular uma área de trabalho ao seu agente
- Usar uma área de trabalho vinculada para incluir recursos customizados em seu agente
- Direcionar potenciais conflitos entre recursos existentes e novos

Esse tutorial levará aproximadamente 30 minutos para ser concluído. Se você explorar outros conceitos relacionados a este tutorial, ele poderá demorar mais tempo para ser concluído.

### Pré-Requisitos

Deve-se ter uma conta do {{site.data.keyword.Bluemix_notm}} e estar inscrito para usar o
serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Consulte o [tutorial de Introdução ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "External link icon"){: new_window} para obter detalhes.

### Resultados

Após concluir este tutorial, além de responder perguntas típicas do usuário sobre a sua empresa, o seu agente será capaz de direcionar perguntas e solicitações que alguém dirigindo um carro pode perguntar ao seu copiloto, como *Quando você acha que chegaremos?* ou *Ligue o rádio.*

### Lições neste tutorial

[Lição 1: Importando uma área de trabalho para o {{site.data.keyword.conversationshort}}](tutorial.html#tutless1)

[Lição 2: Vinculando uma área de trabalho](tutorial.html#tutless2)

[Lição 3: Incluindo recursos customizados](tutorial.html#tutless3)

[Lição 4: Testando recursos customizados](tutorial.html#tutless4)

[Lição 5: Resolvendo conflitos entre recursos](tutorial.html#tutless5)

## Lição 1: Importando uma área de trabalho para a Conversa 
{: #tutless1}

Nesta lição, você aprenderá como importar uma área de trabalho para o serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.

### Antes de começar

Deve-se ter uma conta do {{site.data.keyword.Bluemix_notm}} e estar inscrito para o serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.

### Sobre essa Tarefa

Para simplificar o processo de criação de uma área de trabalho do {{site.data.keyword.conversationshort}}, você importará o arquivo `car_demo_workspace.json` que contém artefatos pré-construídos da demo simples do {{site.data.keyword.conversationshort}}.

### Procedimento

1.  Faça download do arquivo [car_demo_workspace.json ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json "Ícone de link externo"){: new_window} para seu computador.
1.  [Efetue login no ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/dashboard/watson "Ícone de link externo"){: new_window} para a instância de serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.
1.  Clique em **Launch tool (ferramenta Ativar)**.
1.  Para importar uma área de trabalho de um arquivo JSON, clique no ícone ![Seta virada para cima acima de uma caixa de para indicar uma ação de importação](images/workspace_import.png).
1.  Clique em **Choose a file (Escolha um arquivo)** para procurar o arquivo `car_demo_workspace.json` que você transferiu por download anteriormente.
1.  Selecione **Tudo (Intenções, Entidades, e {{site.data.keyword.dialogshort}})**, em seguida, clique em  **Importar**.

### Resultados

A área de trabalho **Car Dashboard Tutorial (Tutorial de Painel de Carro)** é incluída em sua instância de serviço do {{site.data.keyword.conversationshort}}.

## Lição 2: Vinculando uma área de trabalho 
{: #tutless2}

Nesta lição, você aprenderá como vincular uma área de trabalho de serviço do {{site.data.keyword.conversationshort}} ao seu agente.

### Procedimento

1.  No menu do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selecione **Linked Workspaces (Áreas de Trabalho Vinculadas)**.
1.  Clique em **Link Workspace (Vincular Área de Trabalho)**.
1.  Selecione a instância do serviço do {{site.data.keyword.conversationshort}} para a qual você importou a área de trabalho na lição anterior.
1.  Selecione a área de trabalho do **Car Dashboard Tutorial (Tutorial do Painel do Carro)**.
1.  Clique em **Link workspaces (Vincular áreas de trabalho)**.

## Lição 3: Incluindo recursos customizados 
{: #tutless3}

Nesta lição, você aprenderá como incluir recursos customizados em seu agente.

### Procedimento

1.  No {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} menu, selecione **Capabilities (Recursos)**.
1.  Clique na guia **Custom Capabilities (Recursos Customizados)**.
1.  Clique em **Add Capabilities (Incluir Recursos)**.
1.  Clique na área de trabalho **Car Dashboard Tutorial (Tutorial de Painel de Carro)** e, em seguida, clique em **Select Workspace (Selecionar Área de Trabalho)**.

    A página Custom Capabilities (Recursos Customizados) agora exibe uma lista de recursos.

## Lição 4: Testando recursos customizados 
{: #tutless4}

Nesta lição, você aprenderá mais sobre os recursos customizados que você incluiu.

### Sobre essa Tarefa

Agora que você incluiu recursos no agente, descubra o que eles podem fazer.

### Procedimento

1.  No cabeçalho do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, clique em **Preview (Visualizar)**.
1.  Faça uma pergunta que acionará um recurso customizado. Insira o texto *Podemos ouvir música?*

    O agente avalia essa solicitação e a mapeia para o recurso customizado **#turn_on**. Na área de trabalho vinculada, o nó de diálogo com uma condição que corresponde à intenção #turn_on é usado. Como resultado, o agente pergunta qual gênero de música reproduzir.

    > **Nota:** é possível ver o recurso para o qual a entrada do usuário é mapeada porque o nome do recurso é exibido como um link abaixo da resposta.

1.  Insira um gênero musical, como *Clássico* ou *Rock* para concluir o diálogo.
1.  Clique em **Edit** ao lado do recurso identificado (#turn_on) a partir do histórico de visualização para abrir a página de recursos customizados.
1.  Agora, faça uma pergunta que acionará um recurso principal. Insira o texto *Fale-me sobre você*.

    Clique em **Edit (Editar)** ao lado do link *System information (Informações do sistema)* para abrir a página de detalhes de recurso. Os recursos principais têm, cada um, a sua própria página de detalhes do recurso na qual é possível customizar a resposta.

1.  Agora, tente confundir o agente inserindo o texto *Podemos ouvir alguma música?*

    O agente reconhece que você já pediu para tocar música e o informa.

## Lição 5: Resolvendo conflitos entre recursos 
{: #tutless5}

Nesta lição, você aprenderá como resolver conflitos entre recursos principais e customizados.

### Sobre essa Tarefa

Depois de vincular a área de trabalho customizada, você é notificado de que existem conflitos entre recursos principais e alguns dos recursos incluídos.

| Recurso principal    | Recurso customizado |
|--------------------|-------------------|
| Finalizando             | #goodbyes         |
| Localizar a loja mais próxima | #locate_amenity   |
| Saudações          | #greetings        |
| Garantia de segurança | #system_reliance  |

### Procedimento

1.  Desative qualquer recurso customizado que você escolher não usar.

    - O propósito do recurso `Ending` e `#goodbyes` se sobrepõe inteiramente. Para assegurar que os usuários tenham uma experiência consistente quando concluírem uma conversa com o seu agente, deve-se escolher usar um ou outro, mas não ambos.

        É comum construir lógica que é acionada no término de uma conversa. Para garantir que o controle sobre qualquer comportamento desse tipo será mantido pelo agente virtual, você usará o recurso principal `Ending` em vez de o customizado.

    - Os recursos `Find nearest store` e `#locate_amenity` se sobrepõem. Insira as elocuções de amostra a seguir na área de janela de Visualização para ver por si mesmo:

        - *Localizar a loja mais próxima* é roteado para `#locate_amenity`.
        - *Localizar a minha loja* é roteado para `Find nearest store`.

        O recurso `#locate_amenity` customizado fornece informações sobre uma ampla gama de serviços, além de apenas uma loja, mas o recurso principal tem uma agradável conversa integrada associada a ele que coleta um CEP do usuário e retorna o endereço da loja mais próxima dele. Para aproveitar o comportamento integrado, use o recurso principal `Find nearest store`.

    - Os recursos relacionados à segurança também se sobrepõem. Para obter uma noção melhor de que tipos de entrada do usuário são manipulados por cada um, insira essas elocuções de amostra na área de janela de Visualização.

        - *Os meus dados estão protegidos?* é roteado para `Security assurance`.
        - *Posso confiar em você com as minhas informações?* é roteado para `#system_reliance`.

        O recurso `#system_reliance` tem dados de treinamento limitados em comparação com o recurso `Security assurance`; portanto, você usará o recurso principal em vez do customizado.

    Para desativar um recurso customizado, deve-se excluí-lo da área de trabalho do {{site.data.keyword.conversationshort}}.
    1.  Na ferramenta {{site.data.keyword.conversationshort}}, expanda a intenção `#goodbyes` na página Intenções e, em seguida, clique no ícone **Delete intent (Excluir intenção)** para excluí-la da área de trabalho.
    1.  Expanda a intenção `#locate_amenity` e, em seguida, clique no ícone **Delete intent (Excluir intenção)** para excluí-la da área de trabalho.
    1.  Expanda a intenção `#system_reliance` e, em seguida, clique no ícone **Delete intent (Excluir intenção)** para excluí-la da área de trabalho.

1.  Quando você faz mudanças na área de trabalho customizada, ela é automaticamente treinada com os novos dados. Após o treinamento de área de trabalho estar concluído, retorne para o {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.

    Na página Recursos, abra a guia **Custom Capabilities (Recursos Customizados)** para confirmar se os recursos removidos (`#goodbyes`, `#locate_amenity` e `#system_reliance`) não estão mais listados.

1.  Os recursos `Greetings` e `#greetings` se sobrepõem completamente um ao outro. Queremos que o agente exiba um comportamento consistente e tenha alguma personalidade. O recurso customizado `#greetings` é projetado para mostrar a emoção de um tipo de personalidade específico que reflete a marca da empresa; portanto, você usará o recurso customizado em vez de o principal.

    Para desativar um recurso principal, deve-se desligá-lo.
    1.  Na guia **Core Capabilities (Recursos principais)** da página Recursos do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, localize o recurso `Greetings`.
    1.  Clique no azulejo para abri-lo, e, em seguida, alterne o comutador Ligado para **Off (Desligado)**. Clique na seta voltar para retornar para a página Configuração principal.

1.  Execute mais testes inserindo consultas de usuário de teste na área de janela de Visualização para confirmar que o recurso apropriado está manipulando a entrada do usuário conforme esperado. Por exemplo, é possível testar novamente as elocuções a seguir:

    - *Posso confiar em você com as minhas informações?* deve ser manipulado pelo recurso `Security assurance`.
    - *Localizar a loja mais próxima* deve ser manipulado pelo recurso `Find nearest store`.

## Resumo de tutorial 
{: #tutless_sum}

Ao aprender sobre o {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, você aumentou o seu agente com recursos customizados.

### Lições aprendidas

Concluindo este tutorial, você aprendeu sobre os conceitos a seguir:

- Áreas de trabalho vinculadas
- Recursos
- Recursos conflitantes
