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

# Tutorial: Incluindo recursos customizados
{: #tutorial}

Este tutorial ajuda a entender como aumentar os recursos de seu agente virtual incluindo os seus próprios recursos.
{: shortdesc}

Neste tutorial, você usará a área de trabalho que alimenta a demo simples do {{site.data.keyword.conversationshort}} para incluir todos os novos
recursos em seu agente. A área de trabalho simula a função de um copiloto para alguém dirigindo um carro. É possível verificar a demo
[aqui ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://conversation-simple.mybluemix.net/){: new_window}. Após importar a área de trabalho em sua
instância de serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}, você vinculará a área de trabalho ao seu agente. Em
seguida, você incluirá as intenções de área de trabalho como recursos customizados e finalmente direcionará qualquer conflito que surgir entre os recursos principais
e os recursos que você incluir.

## Aprendendo objetivos

Após concluir este tutorial, você saberá como executar as tarefas a seguir:

- Vincular uma área de trabalho ao seu agente
- Usar uma área de trabalho vinculada para incluir recursos customizados em seu agente
- Direcionar potenciais conflitos entre recursos existentes e novos

Esse tutorial levará aproximadamente 30 minutos para ser concluído. Se você explorar outros conceitos relacionados a este tutorial, ele poderá demorar mais tempo para ser concluído.

## Pré-Requisitos

Deve-se ter uma conta do {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} e estar inscrito para usar o
serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Consulte
[https://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window} para obter detalhes.

## Resultados

Após concluir este tutorial, além de responder perguntas típicas do usuário sobre a sua empresa, o seu agente será capaz de direcionar perguntas e solicitações
que alguém dirigindo um carro pode perguntar ao seu copiloto, como *Quando você acha que chegaremos?* ou *Ligue o rádio.*

### Lições neste tutorial

[Lição 1: Importando uma área de trabalho para o {{site.data.keyword.conversationshort}}](/docs/services/virtual-agent/tutorial.html#tutless1)

[Lição 2: Vinculando uma área de trabalho](/docs/services/virtual-agent/tutorial.html#tutless2)

[Lição 3: Incluindo recursos customizados](/docs/services/virtual-agent/tutorial.html#tutless3)

[Lição 4: Testando recursos customizados](/docs/services/virtual-agent/tutorial.html#tutless4)

[Lição 5: Resolvendo conflitos entre recursos](/docs/services/virtual-agent/tutorial.html#tutless5)

## Lição 1: Importando uma área de trabalho para a Conversa
{: #tutless1}

Nesta lição, você aprenderá como importar uma área de trabalho para o serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}}.

### Antes de começar

Deve-se ter uma conta do {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} e estar inscrito para o
serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.

### Sobre essa Tarefa

Para simplificar o processo de criação de uma área de trabalho do {{site.data.keyword.conversationshort}}, você importará o
arquivo `car_demo_workspace.json` que contém artefatos pré-construídos da demo simples do {{site.data.keyword.conversationshort}}.

### Procedimento

1. Faça download do arquivo
<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json" download>car_demo_workspace.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> em seu computador.
1. [Efetue login ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/dashboard/watson){: new_window} em sua
instância de serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.
1. Clique na **ferramenta Ativar**.
1. Para importar uma área de trabalho de um arquivo JSON, clique no ícone ![Seta virada para cima acima de uma caixa de
entrada para indicar uma ação de importação](images/workspace_import.png).
1. Clique em **Escolher um arquivo** para procurar o arquivo `car_demo_workspace.json` que você transferiu por download
anteriormente.
1. Selecione **Tudo (Intenções, Entidades e {{site.data.keyword.dialogshort}})** e, em seguida, clique em
**Importar**.

### Resultados

A área de trabalho **Tutorial de painel de carro** é incluída em sua instância de serviço do {{site.data.keyword.conversationshort}}.

## Lição 2: Vinculando uma área de trabalho
{: #tutless2}

Nesta lição, você aprenderá como vincular uma área de trabalho de serviço do {{site.data.keyword.conversationshort}} ao seu agente.

### Procedimento

1. No menu do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selecione **Áreas de trabalho
vinculadas**.
1. Clique em **Vincular a área de trabalho**.
1. Selecione a instância do serviço do {{site.data.keyword.conversationshort}} para a qual você importou a área de trabalho na lição anterior.
1. Selecione a área de trabalho do **Tutorial de painel de carro**.
1. Clique em **Vincular as áreas de trabalho**.

## Lição 3: Incluindo recursos customizados
{: #tutless3}

Nesta lição, você aprenderá como incluir recursos customizados em seu agente.

### Procedimento

1. No menu do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selecione **Configurar**.
1. Clique na guia **Recursos customizados**.
1. Clique em **Incluir recursos**.
1. Clique na área de trabalho **Tutorial de painel de carro** e, em seguida, clique em **Selecionar área de trabalho**.

    A página Recursos customizados agora exibe uma lista de recursos.

## Lição 4: Testando recursos customizados
{: #tutless4}

Nesta lição, você aprenderá mais sobre os recursos customizados que você incluiu.

### Sobre essa Tarefa

Agora que você incluiu recursos no agente, descubra o que eles podem fazer.

### Procedimento

1. No cabeçalho do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, clique em **Visualização**.
1. Faça uma pergunta que acionará um recurso customizado. Insira o texto *Podemos ouvir música?*

    O agente avalia essa solicitação e a mapeia para o recurso customizado **#turn_on**. Na área de trabalho vinculada, o nó de diálogo com
uma condição que corresponde à intenção #turn_on é usado. Como resultado, o agente pergunta qual gênero de música reproduzir.

    > **Nota:** é possível ver o recurso para o qual a entrada do usuário é mapeada porque o nome do recurso é exibido como um link abaixo da
resposta.
1. Insira um gênero musical, como *Clássico* ou *Rock* para concluir o diálogo.
1. Clique no link **#turn_on** no histórico de visualização para abrir a página de recursos customizados.
1. Agora, faça uma pergunta que acionará um recurso principal. Insira o texto *Fale-me sobre você*.

    Clique no link **Informações do sistema** para abrir a página de detalhes do recurso. Os recursos principais têm, cada um, a sua
própria página de detalhes do recurso na qual é possível customizar a resposta.

1. Agora, tente confundir o agente inserindo o texto *Podemos ouvir alguma música?*

    O agente reconhece que você já pediu para tocar música e o informa.

## Lição 5: Resolvendo conflitos entre recursos
{: #tutless5}

Nesta lição, você aprenderá como antecipar e resolver conflitos entre recursos principais e customizados.

### Sobre essa Tarefa

Você deseja que o usuário tenha uma experiência consistente ao interagir com o agente. Se as respostas para determinadas consultas variam entre ser fornecida
por um recurso principal e um recurso customizado, isto poderá causar confusão para o usuário. Identifique onde tais conflitos podem surgir e aja para assegurar que
apenas um recurso seja acionado para cada tipo de consulta.

### Procedimento

1. Compare os recursos que são definidos no aplicativo principal com aqueles definidos na área de trabalho customizada.

    - Para revisar os recursos que são fornecidos com o aplicativo, veja [Recursos principais](/docs/services/virtual-agent/intent_list.html) para obter uma descrição
de cada recurso principal.
    - Para revisar as intenções que estão definidas na área de trabalho do {{site.data.keyword.conversationshort}}, abra a área de trabalho na
ferramenta do {{site.data.keyword.conversationshort}} e, em seguida, abra a página **Intenções**. Expanda cada intenção de ver os tipos de
elocuções para os quais ela é treinada para responder.

1. Com base na descrição e função de cada um, faça uma lista de todos os recursos que você suspeita que possam competir uns com os outros para manipular uma
elocução de usuário.

    Por exemplo, os recursos a seguir podem ambos tentar direcionar a mesma entrada do usuário:

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d6710e463" class="stentry thleft thbot">Recurso principal</th>
    <th valign="bottom" align="left" id="d6710e465" class="stentry thleft thbot">Recurso customizado</th>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Finalizando</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#goodbyes</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Localizar a loja mais próxima</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#locate_amenity</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Saudações</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#greetings</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Garantia de segurança</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#system_reliance</p></td>
    </tr>
    </table>

1. Desative qualquer recurso customizado que você escolher não usar.

    - O propósito do recurso `Ending` e `#goodbyes` se sobrepõe inteiramente. Para assegurar que os usuários tenham uma
experiência consistente quando concluírem uma conversa com o seu agente, deve-se escolher usar um ou outro, mas não ambos.

        É comum construir lógica que é acionada no término de uma conversa. Para garantir que o controle sobre qualquer comportamento desse tipo será mantido
pelo agente virtual, você usará o recurso principal `Ending` em vez de o customizado.

    - Os recursos `Find nearest store` e `#locate_amenity` se sobrepõem. Insira as elocuções de amostra a
seguir na área de janela de Visualização para ver por si mesmo:

        - *Localizar a loja mais próxima* é roteado para `#locate_amenity`.
        - *Localizar a minha loja* é roteado para `Find nearest store`.

        O recurso `#locate_amenity` customizado fornece informações sobre uma ampla gama de serviços, além de apenas uma loja, mas o recurso
principal tem uma agradável conversa integrada associada a ele que coleta um CEP do usuário e retorna o endereço da loja mais próxima dele. Para aproveitar o
comportamento integrado, use o recurso principal `Find nearest store`.

    - Os recursos relacionados à segurança também se sobrepõem. Para obter uma noção melhor de que tipos de entrada do usuário são manipulados por cada um,
insira essas elocuções de amostra na área de janela de Visualização.

        - *Os meus dados estão protegidos?* é roteado para `Security assurance`.
        - *Posso confiar em você com as minhas informações?* é roteado para `#system_reliance`.

        O recurso `#system_reliance` tem dados de treinamento limitados em comparação com o recurso `Security
assurance`; portanto, você usará o recurso principal em vez do customizado.

    Para desativar um recurso customizado, deve-se excluí-lo da área de trabalho do {{site.data.keyword.conversationshort}}.
    1. Na ferramenta do {{site.data.keyword.conversationshort}}, expanda a intenção `#goodbyes` na página Intenções
e, em seguida, clique no ícone **Excluir intenção** para excluí-la da área de trabalho.
    1. Expanda a intenção `#locate_amenity` e, em seguida, clique no ícone **Excluir intenção** para excluí-la da área de
trabalho.
    1. Expanda a intenção `#system_reliance` e, em seguida, clique no ícone **Excluir intenção** para excluí-la da área de trabalho.

1. Quando você faz mudanças na área de trabalho customizada, ela é automaticamente treinada com os novos dados. Após o treinamento de área de trabalho
estar concluído, retorne para o {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.

    Na página Configurar, abra a guia **Recursos customizados** para confirmar que os recursos que você removeu
(`#goodbyes`, `#locate_amenity` e `#system_reliance`) não são mais listados.

1. Os recursos `Greetings` e `#greetings` se sobrepõem completamente um ao outro. Queremos que o agente exiba um
comportamento consistente e tenha alguma personalidade. O recurso customizado `#greetings` é projetado para mostrar a emoção de um tipo de
personalidade específico que reflete a marca da empresa; portanto, você usará o recurso customizado em vez de o principal.

    Para desativar um recurso principal, deve-se desligá-lo.
    1. Na guia **Recursos principais** da página Configurar do {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, localize o recurso `Greetings`.
    1. Clique no azulejo para abri-lo, e, em seguida, alterne o comutador Ligado para **Desligado**. Clique na seta voltar para retornar
para a página Configuração principal.

1. Execute mais testes inserindo consultas de usuário de teste na área de janela de Visualização para confirmar que o recurso apropriado está manipulando a
entrada do usuário conforme esperado. Por exemplo, é possível testar novamente as elocuções a seguir:

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
