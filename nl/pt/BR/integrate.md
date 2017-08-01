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

# Integrando o agente com a interface com o usuário de seu aplicativo
{: #integrate}

Para integrar o cliente de front-end do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} com o seu
aplicativo, é possível incluir a interface de bate-papo fornecida pelo {{site.data.keyword.IBM_notm}} no estado em que se encontra
em seu website voltado para o cliente, estender a janela de bate-papo fornecida para customizá-lo para
as suas necessidades ou construir a sua própria interface de bate-papo.
{: shortdesc}

[Incluindo o widget de bate-papo fornecido em sua UI](/docs/services/virtual-agent/integrate.html#add_chat)

[Construindo uma interface de bate-papo customizada](/docs/services/virtual-agent/integrate.html#custom_chat)

## Incluindo o widget de bate-papo fornecido em sua UI
{: #add_chat}

O {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} é fornecido com um widget de bate-papo que pode ser usado no estado em
que se encontra em sua interface com o usuário.

### Sobre essa Tarefa

Esse diagrama ilustra como a conversa flui através do sistema quando você usa o widget de bate-papo que é fornecido pela {{site.data.keyword.IBM_notm}}.

![Mostra uma configuração padrão onde o widget de bate-papo fornecido é usado.](images/builtin_chat_new.png)

### Procedimento

1. Para usar o widget fornecido, abra o [{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} Widget de bate-papo ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/chat-widget){: new_window} repositório GitHub e conclua as etapas no arquivo `README.md`.

    O widget de bate-papo fornecido é extensível. Se ele contiver elementos que você deseja mudar, será possível customizá-los. Por exemplo, para mudar um
layout que é usado pelo widget de bate-papo fornecido, é possível escrever um layout customizado que o substitui. Consulte o exemplo aqui:
[https://github.com/watson-virtual-agents/chat-widget/tree/1.2.12/examples/basic-custom-layout. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/chat-widget/tree/1.2.12/examples/basic-custom-layout){: new_window} Tenha em mente que o layout pode ser usado por mais de uma intenção.

1. Para obter informações sobre as etapas que deve-se tomar para suportar transações de widget de bate-papo que podem ocorrer para recursos que usam a
conversa integrada, veja [Implementando a lógica para suportar conversa integrada](/docs/services/virtual-agent/impl_intents.html#backend_transaction).

### O que fazer em seguida

Se a extensão de customizações que você deseja fazer for tão difundida que é impossível implementar as suas mudanças fazendo atualizações no widget de bate-papo
fornecido, então, será possível criar a sua própria interface de bate-papo.

## Construindo uma interface de bate-papo customizada
{: #custom_chat}

Se o widget de bate-papo fornecido não atender às suas necessidades, será possível desenvolver a sua própria interface de bate-papo do JavaScript para permitir
que os seus usuários interajam com o agente virtual. Isso lhe dá controle completo sobre o layout, a aparência e o comportamento da interface de bate-papo.

### Sobre essa Tarefa

Esse diagrama ilustra como a conversa flui através do sistema quando você fornece uma interface de bate-papo customizada.

![Mostra o IBM Chat Widget descarregado para a área de troca para uma interface de usuário customizada.](images/custom_ui_new.png)

### Procedimento

Para desenvolver uma interface de bate-papo customizada com o JavaScript, use os recursos a seguir:

- **{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}SDK de cliente**

    Um SDK do JavaScript para desenvolver aplicativos que interagem com o {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}. O SDK do cliente está hospedado no [GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/client-sdk){: new_window}.

- **Explorer de API**

    Um portal que fornece acesso às APIs de REST do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} no
{{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}. É possível acessar as APIs do {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} por meio do
[{{site.data.keyword.IBM_notm}} developerWorks API Explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}.

