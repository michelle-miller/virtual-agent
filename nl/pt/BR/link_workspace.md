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

# Vinculando as áreas de trabalho
{: #link_workspace}

Antes de poder usar um recurso customizado ou um diálogo customizado com um recurso principal, deve-se estabelecer uma conexão entre o agente virtual e a área
de trabalho de serviço do {{site.data.keyword.conversationshort}} que contém os artefatos que você deseja usar.
{: shortdesc}

## Sobre essa Tarefa

Uma área de trabalho é um contêiner de serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} que
retém intenções, entidades e um diálogo, que são artefatos que são usados para definir e treinar um fluxo de conversa. O seu agente pode usar artefatos da área de
trabalho, incluindo as intenções treinadas e um diálogo, conforme ele interage com os seus clientes para customizar e estender o escopo das coisas que podemos
discutir.

É possível vincular as áreas de trabalho para alcançar os objetivos a seguir:

 - Defina os seus recursos recursos: a área de trabalho deve incluir intenções, elocuções de amostra e um diálogo com condições de nó que correspondam a cada
intenção definida. 
 - Defina um diálogo customizado para um recurso principal: a área de trabalho deve incluir um diálogo com uma condição de nó que corresponda ao nome da
intenção para um recurso principal.

Não é possível usar a mesma área de trabalho para incluir recursos customizados conforme você usa para incluir um diálogo para um recurso principal. Deve-se
criar uma área de trabalho única dedicada que defina todos os recursos customizados que você deseja usar. Crie uma ou mais áreas de trabalho separadas para definir os
diálogos que você deseja usar como respostas para recursos principais.

## Procedimento

1. No menu do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selecione **Áreas de trabalho
vinculadas**.
1. Clique em **Vincular a área de trabalho**.

    Forneça as suas credenciais de conta do {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} para
dar permissão ao {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para acessar a sua
instância de serviço do {{site.data.keyword.conversationshort}} e recuperar informações da área de trabalho.

1. Selecione a instância do serviço do {{site.data.keyword.conversationshort}} que contém as áreas de trabalho que você deseja usar.
1. Selecione uma ou mais áreas de trabalho que você deseja vincular ao seu agente.
1. Clique em **Vincular as áreas de trabalho**.

[Construindo um diálogo customizado](/docs/services/virtual-agent/personalize.html#custom_dialog)

[Incluindo os seus próprios recursos](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

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
expostos a um comportamento inesperado enquanto você estiver fazendo mudanças. Essa abordagem é verdadeira para todos, exceto o recurso **Nenhum dos
acima**, que não pode ser desativado. Deve-se mudar o tipo de resposta de **Usar a sua própria conversa** para uma das outras opções de
tipo de resposta para este recurso antes de você poder desvincular uma área de trabalho que esteja associada a ele.

### Procedimento

1. No menu do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selecione **Áreas de trabalho
vinculadas**.
1. Clique para abrir a área de trabalho que você deseja desassociar com o agente.
1. Clique em **Desvincular a área de trabalho**.

[Vinculando as áreas de trabalho](/docs/services/virtual-agent/link_workspace.html)

