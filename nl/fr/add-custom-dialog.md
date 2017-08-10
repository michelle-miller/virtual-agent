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

# Ajout de dialogues personnalisés pour les capacités de base 
{: #use_custom}

Pour toute capacité de base, vous pouvez choisir d'utiliser votre propre conversation afin d'interagir avec l'utilisateur pour remplir son objectif.
{: shortdesc}

## Création d'un dialogue personnalisé 
{: #custom_dialog}

Si une capacité de base que vous activez doit être gérée par un dialogue personnalisé, vous pouvez utiliser le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} pour créer le dialogue, puis l'associer à votre agent virtuel.

### A propos de cette tâche

Le service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} est un ensemble d'outils et d'API que vous utilisez pour développer des applications qui utilisent des interfaces en langage naturel pour automatiser les interactions avec les clients. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} utilise le service {{site.data.keyword.conversationshort}} pour définir les capacités apprises et le flux de dialogue utilisés par le bot. Si le dialogue fourni n'offre pas la flexibilité dont vous avez besoin, vous pouvez développer votre propre dialogue à l'aide des outils du service {{site.data.keyword.conversationshort}}.

A des fins de compatibilité avec l'agent virtuel, tout dialogue que vous créez doit respecter les instructions de conception disponibles dans le [contrat du dialogue ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "icône Lien externe"){: new_window}. Ces instructions indiquent comment le dialogue interagit avec l'interface de discussion de l'agent virtuel et notamment comment afficher les invites aux utilisateurs et où stocker les informations fournies par ces derniers afin qu'elles soient accessibles par l'interface de la fenêtre de discussion.

Le référentiel {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} fournit également des exemples qui illustrent le mode de fonctionnement des interactions des dialogues. Vous pouvez en utiliser un comme modèle pour votre propre dialogue. Reportez-vous à l'[exemple de fichier JSON de flux de dialogues ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/michelle-miller-patch-1/sample_dialog_flows.json "icône Lien externe"){: new_window}.

#### Procédure

Pour créer un dialogue personnalisé :

1.  Si vous ne l'avez pas déjà fait, inscrivez-vous au service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Pour plus d'informations, reportez-vous au [{{site.data.keyword.conversationshort}}Guide d'initiation du service ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "icône Lien externe"){: new_window}.
1.  Créez un espace de travail qui contiendra votre dialogue.

    Pour plus d'informations sur les espaces de travail, reportez-vous au document relatif à la [{{site.data.keyword.conversationshort}}création d'un espace de travail avec le service ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace "icône Lien externe"){: new_window}.

1.  Accédez directement à l'onglet **{{site.data.keyword.dialogshort}}**. (Ne créez pas d'intentions ou d'entités.)
1.  Créez un noeud de dialogue pour chaque capacité à personnaliser.

    Un dialogue doit comporter une condition définie sur le nom d'intention de la capacité qui l'utilisera.

    Utilisez la syntaxe suivante :

    ```java
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Par exemple, si pour la capacité **Contact us**, la valeur *intent-name* est `Information-Contact_Us`, votre dialogue teste `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Si vous disposez d'un bot plus ancien et que vos paramètres indiquent que vous ne souhaitez transmettre que l'intention à vos espaces de travail (ancien comportement), utilisez la syntaxe suivante à la place :

    ```java
    #intent-name
    ```
    {: screen}

    Par exemple, `#Information-Contact_Us`

    Pour découvrir le nom d'intention associé à une capacité, voir [Noms d'intention](intent_codenames.html).

1.  Ajoutez des noeuds si nécessaire pour créer le flux de dialogue requis.

    A des fins de compatibilité avec {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, votre dialogue doit respecter certaines directives de conception lors du stockage des informations collectées ou de l'utilisation d'événements pour communiquer avec l'interface du widget de discussion. Créez un dialogue qui respecte les instructions de conception de dialogue {{site.data.keyword.virtualagentshort}}, accessibles à l'adresse suivante : [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "icône Lien externe"){: new_window}.

1.  Associez les espaces de travail avec les dialogues que vous avez créés à votre agent.

    Pour plus de détails, voir [Association d'espaces de travail](link_workspace.html).

1.  Dans l'onglet **Core Capabilities (Capacités de base)** de la page Configure (Configuration), remplacez le type de réponse de chaque capacité pour laquelle vous souhaitez utiliser un dialogue personnalisé par le type de réponse **Use your own conversation (Utiliser votre propre conversation)**.
1.  Sélectionnez l'espace de travail qui contient le dialogue à utiliser dans la liste des espaces de travail associés, puis cliquez sur **Save (Sauvegarder)** pour finir d'établir le lien.

    Si vous n'avez pas encore associé l'espace de travail, vous pouvez cliquer sur **Link a workspace (Associer un espace de travail)** à partir de là pour associer un espace de travail que vous avez créé précédemment à votre agent.
