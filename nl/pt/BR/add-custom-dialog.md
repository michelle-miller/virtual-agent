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

# Incluindo diálogos customizados para recursos principais 
{: #use_custom}

Para qualquer recurso principal, é possível escolher usar a sua própria conversa para interagir com o usuário para satisfazer o objetivo do usuário.
{: shortdesc}

## Construindo um diálogo customizado 
{: #custom_dialog}

Se um recurso principal que você ativar requerer manipulação por um diálogo customizado, será possível usar o serviço do {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} para construir o diálogo e, em seguida, vinculá-lo ao seu agente virtual.

### Sobre essa Tarefa

O serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} é um conjunto de ferramentas e APIs que é possível usar para
construir aplicativos que usam interfaces de língua natural para automatizar interações com clientes. O {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} usa o serviço do {{site.data.keyword.conversationshort}} para definir os recursos treinados e o fluxo de
diálogo que são usados pelo robô. Se o diálogo não fornecer a flexibilidade de que você precisa, será possível construir o seu próprio diálogo usando as
ferramentas de serviço do {{site.data.keyword.conversationshort}}.

Para compatibilidade com o agente virtual, qualquer diálogo criado deve estar em conformidade com as diretrizes de design definidas no [contrato de diálogo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Ícone de link externo"){: new_window}. Estas diretrizes especificam como o diálogo interage com a interface de bate-papo do agente virtual, incluindo como
exibir prompts para usuários e onde armazenar informações fornecidas pelos usuários para que ele possa ser acessado pela interface de janela de bate-papo.

O repositório do {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} também fornece exemplos que ilustram como as interações de diálogo funcionam. É possível usar a amostra como um modelo para o seu próprio diálogo. Consulte o [arquivo JSON de fluxos de diálogo de amostra ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/michelle-miller-patch-1/sample_dialog_flows.json "Ícone de link externo"){: new_window}.

#### Procedimento

Para construir um diálogo customizado:

1.  Se você não fez isso ainda, inscreva-se para o serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Para obter informações adicionais, consulte a documentação do [{{site.data.keyword.conversationshort}} serviço Introdução ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "Ícone de link externo"){: new_window}.
1.  Crie uma área de trabalho para conter o seu diálogo.

    Para obter informações sobre áreas de trabalho, consulte a documentação do [{{site.data.keyword.conversationshort}} serviço Criando uma área de trabalho ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace "Ícone de link externo"){: new_window}.

1.  Navegue diretamente para a guia do **{{site.data.keyword.dialogshort}}**. (Não crie nenhuma intenção ou entidade.)
1.  Crie um nó de diálogo para cada recurso que você deseja customizar.

    Um nó de diálogo deve ter uma condição que é avaliada para o nome de intenção para o recurso que a usará.

    Use a sintaxe a seguir:

    ```java
    $wva.intents.get (0) .intent.equals ('intent-name')
    ```
    {: screen}

    Por exemplo, para o recurso **Contact us (Contacte-nos)**, o *intent-name* é `Information-Contact_Us`. O seu diálogo seria testado para `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Se você tiver um robô mais antigo, e suas configurações indicarem que você deseja reverter para transmitir a intenção somente para sua área de trabalho, use então a seguinte sintaxe:

    ```java
    #intent-name
    ```
    {: screen}

    Por exemplo, `#Information-Contact_Us`

    Para descobrir o nome de intenção que está associado com um recurso, veja [Nomes de intenção](intent_codenames.html).

1.  Inclua os nós conforme necessário para criar o fluxo de diálogo necessário.

    Para ser compatível com o {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, o seu diálogo deve estar em conformidade com determinadas diretrizes de design ao armazenar informações coletadas ou ao usar eventos para se comunicar com a interface de widget de bate-papo. Crie um diálogo que esteja em conformidade com as diretrizes de design de diálogo do {{site.data.keyword.virtualagentshort}} em [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Ícone de link externo"){: new_window}.

1.  Vincule as áreas de trabalho com diálogos que você criou para o seu agente.

    Consulte [Vinculando as áreas de trabalho](link_workspace.html) para obter detalhes.

1.  Na guia **Core Capabilities (Recursos Principais)** da página Configure (Configurar), mude o tipo de resposta de cada recurso para o qual você deseja usar um diálogo customizado para o tipo de resposta **Use your own conversation (Usar sua própria conversa)**.
1.  Selecione a área de trabalho que contém o diálogo que você deseja usar na lista de áreas de trabalho vinculadas e, em seguida, clique em **Save (Salvar)** para concluir o estabelecimento da vinculação.

    Se você ainda não vinculou a área de trabalho, é possível clicar em **Link a workspace (Vincular uma área de trabalho)** daqui para vincular uma área de trabalho criada anteriormente ao seu agente.
