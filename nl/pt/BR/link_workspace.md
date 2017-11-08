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

# Vinculando as áreas de trabalho 
{: #link_workspace}

Antes de poder usar um recurso customizado ou um diálogo customizado com um recurso principal, deve-se estabelecer uma conexão entre o agente virtual e a área
de trabalho de serviço do {{site.data.keyword.conversationshort}} que contém os artefatos que você deseja usar.
{: shortdesc}

## Sobre Áreas

Uma área de trabalho é um contêiner de serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} que
retém intenções, entidades e um diálogo, que são artefatos que são usados para definir e treinar um fluxo de conversa. O seu agente pode usar artefatos da área de
trabalho, incluindo as intenções treinadas e um diálogo, conforme ele interage com os seus clientes para customizar e estender o escopo das coisas que podemos
discutir.

É possível vincular as áreas de trabalho para alcançar os objetivos a seguir:

- Defina os seus recursos recursos: a área de trabalho deve incluir intenções, elocuções de amostra e um diálogo com condições de nó que correspondam a cada
intenção definida.
- Defina um diálogo customizado para um recurso principal: a área de trabalho deve incluir um diálogo com uma condição de nó que corresponda ao nome da
intenção para um recurso principal.

É *possível* usar a mesma área de trabalho para incluir recursos customizados e diálogos customizados para recursos principais. No entanto, é mais simples gerenciar as coisas se você criar uma única área de trabalho dedicada para definir os recursos customizados que deseja usar e uma ou mais áreas de trabalho separadas para definir os diálogos que deseja usar como respostas para recursos principais. Se você optar por usar a mesma área de trabalho para ambos, certifique-se de incluir todos os nós que contêm diálogos customizados para recursos principais específicos na parte superior da árvore de diálogo para evitar que elocuções sejam roteadas incorretamente para recursos customizados.

### Procedimento

1.  Abra a página **Linked Workspaces (Áreas de Trabalho Vinculadas)** para o agente atual. 
1.  Clique em **Link Workspace (Vincular Área de Trabalho)**.

    Forneça as suas credenciais de conta do {{site.data.keyword.Bluemix_notm}} para
dar permissão ao {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para acessar a sua
instância de serviço do {{site.data.keyword.conversationshort}} e recuperar informações da área de trabalho.

1.  Selecione a instância do serviço do {{site.data.keyword.conversationshort}} que contém as áreas de trabalho que você deseja usar.
1.  Selecione uma ou mais áreas de trabalho que você deseja vincular ao seu agente.
1.  Clique em **Link workspaces (Vincular áreas de trabalho)**.

[Construindo um diálogo customizado](add-custom-dialog.html)

[Incluindo os seus próprios recursos](add-custom-capabilities.html)

## Desvinculando as áreas de trabalho 
{: #unlink_workspace}

Se você decidir que não deseja manter uma conexão entre o seu agente virtual e uma área de trabalho específica do
{{site.data.keyword.conversationshort}}, será possível desvincular a área de trabalho.

### Antes de começar

Certifique-se de que a área de trabalho que deseja desvincular não esteja sendo ativamente usada por um recurso que a requer. Lembre-se de que uma área de
trabalho que você vincula ao agente virtual estará disponível para uso por qualquer recurso que estiver associado a
esse agente, seja um recurso customizado ou um recurso principal.

### Sobre essa Tarefa

Quando você desvincula uma área de trabalho de um recurso, o recurso é automaticamente desligado. Desativar o recurso assegura que os usuários ativos não sejam
expostos a um comportamento inesperado enquanto você estiver fazendo mudanças. Essa abordagem é verdadeira para todos, exceto o recurso **None of the above (Nenhuma das opções acima)**, que não pode ser desativado. Deve-se mudar o tipo de resposta de **Use your own conversation (Usar sua própria conversa)** para uma das outras opções de
tipo de resposta para este recurso antes de você poder desvincular uma área de trabalho que esteja associada a ele.

### Procedimento

1.  Abra a página **Linked Workspaces (Áreas de Trabalho Vinculadas)** para o agente atual. 
1.  Clique para abrir a área de trabalho que você deseja desassociar com o agente.
1.  Clique em **Unlink this Workspace (Desvincular esta Área de Trabalho)** ![ícone de lixeira que representa o relacionamento de links de exclusão](images/trash.png) .

[Vinculando as áreas de trabalho](link_workspace.html)
