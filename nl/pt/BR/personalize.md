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

# Personalizando o agente
{: #personalize}

Certifique-se de que o agente virtual responda às questões que importem aos seus clientes. E que as suas respostas transmitam com precisão as informações
sobre os serviços que a sua empresa oferece ou ajudem os clientes a concluírem transações de negócios.
{: shortdesc}

## Sobre essa Tarefa

É possível personalizar o agente executando as ações a seguir:

[Incluindo diálogos customizados para recursos principais](/docs/services/virtual-agent/personalize.html#use_custom)

[Incluindo os seus próprios recursos](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Incluindo diálogos customizados para recursos principais
{: #use_custom}

Para qualquer recurso principal, é possível escolher usar a sua própria conversa para interagir com o usuário para satisfazer o objetivo do usuário.

### Construindo um diálogo customizado
{: #custom_dialog}

Se um recurso principal que você ativar requerer manipulação por um diálogo customizado, será possível usar o serviço do {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} para construir o diálogo e, em seguida, vinculá-lo ao seu agente virtual.

#### Sobre essa Tarefa

O serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} é um conjunto de ferramentas e APIs que é possível usar para
construir aplicativos que usam interfaces de língua natural para automatizar interações com clientes. O {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} usa o serviço do {{site.data.keyword.conversationshort}} para definir os recursos treinados e o fluxo de
diálogo que são usados pelo robô. Se o diálogo não fornecer a flexibilidade de que você precisa, será possível construir o seu próprio diálogo usando as
ferramentas de serviço do {{site.data.keyword.conversationshort}}.

Para compatibilidade com o agente virtual, qualquer diálogo que você construir deve estar em conformidade com as diretrizes de design em
[https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}. Estas diretrizes especificam como o diálogo interage com a interface de bate-papo do agente virtual, incluindo como
exibir prompts para usuários e onde armazenar informações fornecidas pelos usuários para que ele possa ser acessado pela interface de janela de bate-papo.

O repositório do {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} também fornece exemplos que ilustram como as
interações de diálogo funcionam. É possível usar a amostra como um modelo para o seu próprio diálogo. Consulte o
[arquivo do JSON de fluxos de diálogo de amostra ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/sample_dialog_flows.json){: new_window}.

#### Procedimento

Para construir um diálogo customizado:

1. Se você não fez isso ainda, inscreva-se para o serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Para
obter mais informações, veja a documentação do serviço do
[{{site.data.keyword.conversationshort}}
Introdução ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.
1. Crie uma área de trabalho para conter o seu diálogo. 

    Para obter informações sobre áreas de trabalho, veja a documentação do serviço do
[{{site.data.keyword.conversationshort}} Criando uma área de
trabalho ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/create-workspace.html){: new_window}.

1. Navegue diretamente para a guia do **{{site.data.keyword.dialogshort}}**. (Não crie nenhuma intenção ou entidade.)
1. Crie um nó de diálogo para cada recurso que você deseja customizar.

    Um nó de diálogo deve ter uma condição que é avaliada para o nome de intenção para o recurso que a usará.

    Use a sintaxe a seguir:

    ```
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Por exemplo, para o recurso **Contate-nos**, o *nome da intenção* é `Information-Contact_Us`. O seu
diálogo seria testado para `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Se você tem um robô mais velho e as suas preferências estão configuradas para reverter para a passagem da intenção apenas para a sua área de
trabalho, então, use a sintaxe a seguir, como alternativa:

    ```
    #intent-name
    ```
    {: screen}

    Por exemplo, `#Information-Contact_Us`

    Para descobrir o nome de intenção que está associado com um recurso, veja [Nomes de intenção](/docs/services/virtual-agent/intent_codenames.html).

1. Inclua os nós conforme necessário para criar o fluxo de diálogo necessário. 

    Para ser compatível com o {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, o seu diálogo deve estar em conformidade
com determinadas diretrizes de design ao armazenar informações coletadas ou ao usar eventos para se comunicar com a interface de widget de bate-papo. Crie um
diálogo que esteja em conformidade com as diretrizes de design de diálogo do {{site.data.keyword.virtualagentshort}} em
[https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}.

1. Vincule as áreas de trabalho com diálogos que você criou para o seu agente.

    Consulte [Vinculando as áreas de trabalho](/docs/services/virtual-agent/link_workspace.html) para obter detalhes.

1. Na guia **Recursos principais** da página Configurar, mude o tipo de resposta de cada recurso para o qual você deseja usar um diálogo
customizado para o tipo de resposta **Usar a sua própria conversa**.
1. Selecione a área de trabalho que contém o diálogo que você deseja usar na lista de áreas de trabalho vinculadas e, em seguida, clique em
**Salvar** para concluir o estabelecimento da vinculação.

    Uma área de trabalho que já estiver sendo usada para incluir recursos customizados não será exibida como uma opção. Não é possível usar a mesma área de
trabalho para incluir recursos customizados conforme você usa para incluir um diálogo para um recurso principal. 

    Se você não vinculou a área de trabalho ainda, então, será possível clicar em **Vincular uma área de trabalho** daqui
para vincular a área de trabalho que você criou anteriormente para o seu agente.

## Incluindo os seus próprios recursos
{: #add_custom_capabilities}

Para expandir sobre o que o agente virtual pode discutir com os seus clientes, inclua os seus próprios recursos.

### Antes de começar

Quando você usa uma área de trabalho para fornecer um diálogo customizado para um recurso principal, apenas é necessário fornecer um diálogo na área de
trabalho. O agente já foi treinado para reconhecer elocuções que mapeiam para os recursos principais; portanto, não é necessário fornecer as intenções, as
entidades e os dados de treinamento. Quando você fornece uma área de trabalho que define os seus próprios recursos, deve-se fornecer as intenções e as entidades, além
do diálogo. Deve-se também fornecer um grande número de elocuções de amostra que o serviço pode usar para treinar as intenções que você deseja suportar. Use a
documentação, as demos e as ferramentas que são fornecidas com o serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}} para construir uma área de trabalho com recursos customizados. Consulte a documentação do [{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/index.html){: new_window} para obter mais informações.

### Sobre essa Tarefa

É possível criar apenas uma área de trabalho para definir recursos customizados. Cada intenção que você incluir na área de trabalho será disponibilizada como um
recurso customizado quando você vincular a área de trabalho para o agente. A área de trabalho deve conter todos os recursos que você deseja incluir em seu agente. Não
inclua intenções na área de trabalho que você não deseja que o seu agente possa manipular.

### Procedimento

1. Na sua instância de serviço do {{site.data.keyword.conversationshort}}, crie uma área de trabalho que defina os seus recursos customizados. Consulte a
documentação de serviço do
[{{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

    Siga estas diretrizes:
    - Inclua uma ramificação para cada recurso que você deseja suportar como um nó base (que é referido como uma *conversa alternativa*
na interface com o usuário de ferramenta do {{site.data.keyword.conversationshort}}) no diálogo. Por exemplo, não defina um nó base na sua caixa de diálogo
que reconhece e responde às saudações do usuário e, em seguida, inclua os nós-filhos que correspondem a outras intenções de recurso customizado abaixo dela.
    - Evite manipular incompatibilidades de entrada do usuário com loops recursivos. Crie apenas mudanças de diálogo que tenham um término definitivo.
    - Não crie uma intenção customizada com o mesmo nome que uma intenção que é usada por um recurso principal. Consulte
[Nomes de intenção](/docs/services/virtual-agent/intent_codenames.html) para obter uma lista de nomes a serem evitados.

1. Vincule a área de trabalho ao agente. Consulte [Vinculando as áreas de trabalho](/docs/services/virtual-agent/link_workspace.html)
1. Na página **Configurar**, abra a guia **Recursos customizados**.
1. Clique em **Incluir recursos**.
1. Selecione a área de trabalho que você vinculou ao agente na Etapa 2 e, em seguida, clique em **Selecionar a área de trabalho**.

    As intenções que são definidas na área de trabalho vinculada agora são listadas como recursos ativados.

    > **Nota:** Não é possível desativar recursos individuais. Se você desejar remover um recurso customizado, será possível excluir a intenção da
área de trabalho na ferramenta de serviço do {{site.data.keyword.conversationshort}}.
    É possível remover todos os recursos de uma só vez clicando em **Remover recursos privados**. Remover os recursos não exclui a
associação entre o agente e a área de trabalho na qual os recursos estão definidos.

### Resultados

Após você incluir recursos customizados, cada elocução de usuário que é avaliada pelo {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} é transmitida para ambos, a área de trabalho principal e a sua área de trabalho de recursos customizados, para
avaliação. O recurso que melhor corresponde à intenção de entrada do usuário é acionado e o diálogo associado a ela é usado.

![Mostra a passagem de usuário de uma elocução para o Watson Virtual Agent. Ele transmite-a para ambas, a
Área de trabalho integrada e a Área de trabalho de recursos vinculados, para avaliação. A Área de trabalho integrada tem uma confiança de 0,85 em comparação com a
confiança de 0,55 da Área de trabalho de recursos vinculados. A Área de trabalho integrada transmite uma resposta de volta para o Watson Virtual Agent passar
para o usuário.](images/workspace-confidences.png)

### Testando recursos customizados
{: #test_custom_capabilities}

Após incluir os seus próprios recursos, execute alguns testes para certificar-se de que eles se comportam conforme esperado.

#### Sobre essa Tarefa

Ao incluir os seus próprios recursos, é possível facilmente definir um que seja semelhante em comportamento a um recurso principal existente. Se for assim,
certifique-se de que os dois não competem um com o outro para responder a determinadas consultas do usuário.

#### Procedimento

1. Use a área de janela de Visualização para fazer perguntas ou fazer os tipos de solicitações que você espera que os seus clientes façam.

    Abaixo da resposta, o recurso que foi acionado para direcionar a solicitação é exibido. Se o recurso que é exibido não for o que você espera, será
possível fazer mudanças para corrigir como a elocução está sendo roteada para os recursos.

1. Compare os recursos que são definidos no aplicativo principal com aqueles definidos na área de trabalho customizada.

    - Para revisar os recursos que são fornecidos com o aplicativo, veja [Recursos principais](/docs/services/virtual-agent/intent_list.html) para obter uma descrição de
cada recurso principal.
    - Para revisar as intenções que estão definidas na área de trabalho do {{site.data.keyword.conversationshort}}, abra a área de trabalho na
ferramenta do {{site.data.keyword.conversationshort}} e, em seguida, abra a página **Intenções**. Expanda cada intenção de ver os tipos de
elocuções para os quais ela é treinada para responder.

1. Use a área de janela de Visualização para testar elocuções que você suspeita que possam causar um conflito.

    Com base nas respostas, verifique se os recursos de sobreposição manipulam as consultas do usuário que são distintas o suficiente entre si de maneira que
os recursos de sobreposição possam coexistir sem resultar em uma experiência desarticulada para o usuário. Se os dois recursos competirem pelos mesmos tipos de
elocuções, então, um deverá ser desativado. É possível lidar com recursos de sobreposição das seguintes maneiras:
    - **Desative o recurso customizado**

        1. Na ferramenta do {{site.data.keyword.conversationshort}}, localize a intenção na página **Intenções**, expanda-a
e, em seguida, clique no ícone **Excluir intenção** para excluí-la da área de trabalho.
        1. Após você fazer mudanças na área de trabalho, ela será automaticamente treinada. Após o treinamento ser concluído, retorne para o
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.
        1. Na página Configurar, abra a guia **Recursos customizados** para confirmar que o recurso não é mais listado.

    - **Desative o recurso principal**

        1. Na guia **Recursos principais** da página Configurar do {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, localize o recurso que você deseja desativar.
        1. Clique no azulejo para abrir o recurso e, em seguida, alterne o comutador Ligado para Desligado.

    - **Edite os dados de treinamento para o recurso customizado**

        Se o recurso customizado direcionar um objetivo de cliente semelhante, mas com um escopo mais amplo, será possível remover elocuções de amostra dos
dados de treinamento para o recurso customizado para excluir exemplos que se sobrepõem com os tipos de elocuções que forem direcionados pelo recurso customizado. Não
é possível acessar a área de trabalho para o recurso principal; só é possível editar a área de trabalho para o recurso customizado para efetuar mudanças. Para
determinar quais elocuções são roteadas para o recurso principal, use a área de janela de Visualização para testar várias elocuções e ver quais acionam o recurso
principal.

        > **Atenção:** Se você escolher essa abordagem, esteja preparado para executar muitos testes e revisão. É difícil prever como o aprendizado de
máquina reagirá às mudanças de dados de treinamento. Será necessário executar muitos testes para confirmar que as suas mudanças têm um impacto planejado.
        Edite a área de trabalho para o recurso customizado seguindo estas etapas:
        1. Na ferramenta do {{site.data.keyword.conversationshort}}, localize a intenção na página **Intenções** e, em seguida,
expanda a intenção de ver a lista de elocuções de amostra.
        1. Selecione a caixa próxima às elocuções que se sobrepõem com elocuções que são manipuladas por recursos principais e, em seguida, clique em
**Remover exemplos**.
        1. Após você fazer mudanças na área de trabalho, ela será automaticamente treinada. 

    - **Mantenha ambos os recursos**

        Em alguns casos, embora os recursos sejam semelhantes, eles direcionam casos de uso distintos o suficiente para que seja possível mantê-los ambos
ativados.

1. Insira as elocuções de teste na área de janela de Visualização novamente para confirmar que as suas mudanças resultem no comportamento esperado. Caso
contrário, faça mudanças adicionais.

## Como nenhum dos acima é usado
{: #none_of_the_above}

Entenda como o recurso **Nenhum dos acima** é usado pelo agente virtual.

Diferente de todos os outros recursos principais, o recurso **Nenhum dos acima** não pode ser desativado. A razão pela qual ele não pode ser
desativado é que ele serve como um tipo de depósito para elocuções que não mapeiam para qualquer um dos recursos configurados. Essa funcionalidade é útil porque é
possível fornecer uma resposta padrão, como *Não posso ajudá-lo com isso*, para solicitações de usuários para recursos que o seu agente ainda
não tem. Ela também responde a perguntas absurdas que os clientes às vezes fazem por diversão quando eles começam a interagir com o agente, como
*O que devo comer no almoço?*

Por causa de seu papel único no funcionamento do agente virtual, como você configura o seu comportamento importa. O recurso **Nenhum dos
acima** é acionado com frequência e de maneiras que nem sempre são óbvias, incluindo:

- Quando você desativa qualquer outro recurso principal, as elocuções que acionam o recurso desativado são roteadas novamente para o
recurso **Nenhum dos acima** para uma resposta.
- Quando uma elocução não corresponde a qualquer dos recursos principais ativados, ela é transmitida para o recurso **Nenhum dos acima**
para uma resposta.  Se você fornece uma área de trabalho vinculada com recursos customizados, a área de trabalho principal e a área de trabalho customizada
avaliam a elocução para localizarem uma correspondência. Se nenhuma correspondência for localizada, então, a resposta que é associada com o recurso principal
**Nenhum dos acima** será usada.
- É possível configurar o recurso **Nenhum dos acima** para ter um tipo de resposta **Usar a sua própria conversa** e
vinculá-lo a uma área de trabalho com um diálogo customizado. Quando nenhuma correspondência de intenção para uma elocução é localizada na área de trabalho principal,
a elocução é transmitida para o recurso **Nenhum dos acima**, que a transmite para a área de trabalho customizada para uma resposta.
- Quando você desvincula uma área de trabalho, se a área de trabalho vinculada está associada com o recurso **Nenhum dos acima**, então
deve-se agir antes de poder continuar a desvincular a área de trabalho. Qualquer outro recurso que estiver associado com a área de trabalho que você deseja
desvincular será automaticamente desativado. Mas, como o recurso **Nenhum dos acima** não pode ser desativado, deve-se decidir sobre um
comportamento de resposta alternativo. Por exemplo, é possível mudar o tipo de resposta para **Exibir uma resposta de texto** e incluir uma
mensagem de texto para usar na resposta.

