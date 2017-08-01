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

# Personnalisation de l'agent
{: #personalize}

Assurez-vous que l'agent virtuel répond aux problèmes importants pour vos clients. Vérifiez également que ses réponses transmettent précisément les informations sur les services offerts par votre société ou qu'elles aident les clients à réaliser des transactions commerciales. 
{: shortdesc}

## A propos de cette tâche

Vous pouvez personnaliser l'agent en effectuant les actions suivantes :

[Ajout de dialogues personnalisés pour les capacités de base](/docs/services/virtual-agent/personalize.html#use_custom)

[Ajout de vos propres capacités](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Ajout de dialogues personnalisés pour les capacités de base
{: #use_custom}

Pour toute capacité de base, vous pouvez choisir d'utiliser votre propre conversation afin d'interagir avec l'utilisateur pour remplir son objectif. 

### Création d'un dialogue personnalisé
{: #custom_dialog}

Si une capacité de base que vous activez doit être gérée par un dialogue personnalisé, vous pouvez utiliser le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} pour créer le dialogue, puis l'associer à votre agent virtuel.

#### A propos de cette tâche

Le service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} est un ensemble d'outils et d'API que vous utilisez pour développer des applications qui utilisent des interfaces en langage naturel pour automatiser les interactions avec les clients. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} utilise le service {{site.data.keyword.conversationshort}} pour définir les capacités apprises et le flux de dialogue utilisés par le bot. Si le dialogue fourni n'offre pas la flexibilité dont vous avez besoin, vous pouvez développer votre propre dialogue à l'aide des outils du service {{site.data.keyword.conversationshort}}.

A des fins de compatibilité avec l'agent virtuel, tout dialogue que vous créez doit respecter les instructions de conception disponibles à la page [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}. Ces instructions indiquent comment le dialogue interagit avec l'interface de discussion de l'agent virtuel et notamment comment afficher les invites aux utilisateurs et où stocker les informations fournies par ces derniers afin qu'elles soient accessibles par l'interface de la fenêtre de discussion.

Le référentiel {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} fournit également des exemples qui illustrent le mode de fonctionnement des interactions des dialogues. Vous pouvez en utiliser un comme modèle pour votre propre dialogue. Reportez-vous à l'[exemple de fichier JSON de flux de dialogues ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/sample_dialog_flows.json){: new_window}.

#### Procédure

Pour créer un dialogue personnalisé : 

1. Si vous ne l'avez pas déjà fait, inscrivez-vous au service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Pour plus d'informations, reportez-vous au [Guide d'initiation du service {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.
1. Créez un espace de travail qui contiendra votre dialogue.

    Pour plus d'informations sur les espaces de travail, reportez-vous au document relatif à la [création d'un espace de travail avec le service {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/create-workspace.html){: new_window}.

1. Accédez directement à l'onglet **{{site.data.keyword.dialogshort}}**. (Ne créez pas d'intentions ou d'entités.)
1. Créez un noeud de dialogue pour chaque capacité à personnaliser. 

    Un dialogue doit comporter une condition définie sur le nom d'intention de la capacité qui l'utilisera. 

    Utilisez la syntaxe suivante : 

    ```
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Par exemple, si pour la capacité **Contact us**, la valeur *intent-name* est `Information-Contact_Us`, votre dialogue teste `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Si vous disposez d'un bot plus ancien et que vos préférences sont définies de sorte à ne transmettre que l'intention à vos espaces de travail (ancien comportement), utilisez la syntaxe suivante à la place : 

    ```
    #intent-name
    ```
    {: screen}

    Par exemple, `#Information-Contact_Us`

    Pour découvrir le nom d'intention associé à une capacité, voir [Noms d'intention](/docs/services/virtual-agent/intent_codenames.html).

1. Ajoutez des noeuds si nécessaire pour créer le flux de dialogue requis. 

    A des fins de compatibilité avec {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, votre dialogue doit respecter certaines directives de conception lors du stockage des informations collectées ou de l'utilisation d'événements pour communiquer avec l'interface du widget de discussion. Créez un dialogue qui respecte les instructions de conception de dialogue {{site.data.keyword.virtualagentshort}}, accessibles à l'adresse suivante : [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}.

1. Associez les espaces de travail avec les dialogues que vous avez créés à votre agent.

    Pour plus de détails, voir [Association d'espaces de travail](/docs/services/virtual-agent/link_workspace.html).

1. Dans l'onglet **Core Capabilities (Capacités de base)** de la page Configure (Configuration), remplacez le type de réponse de chaque capacité pour laquelle vous souhaitez utiliser un dialogue personnalisé par le type de réponse **Use your own conversation (Utiliser votre propre conversation)**. 
1. Sélectionnez l'espace de travail qui contient le dialogue à utiliser dans la liste des espaces de travail associés, puis cliquez sur **Save (Sauvegarder)** pour finir d'établir le lien. 

    Un espace de travail déjà utilisé pour ajouter des capacités personnalisées n'est pas affiché comme option. Vous ne pouvez pas utiliser le même espace de travail pour ajouter des capacités personnalisées que celui que vous utilisez pour ajouter un dialogue pour une capacité de base. 

    Si vous n'avez pas encore associé l'espace de travail, vous pouvez cliquer sur **Link a workspace (Associer un espace de travail)** à partir de là pour associer l'espace de travail que vous avez créé précédemment à votre agent.

## Ajout de vos propres capacités
{: #add_custom_capabilities}

Pour étendre les possibilités de discussion de l'agent virtuel avec vos clients, ajoutez vos propres capacités. 

### Avant de commencer

Si vous utilisez un espace de travail afin de fournir un dialogue personnalisé pour une capacité de base, il vous suffit de fournir un dialogue dans l'espace de travail. L'agent ayant déjà été formé pour reconnaître les énoncés mappés aux capacités de base, vous n'avez pas besoin de fournir d'intentions, d'entités et de données de formation. Si vous fournissez un espace de travail qui définit vos propres capacités, vous devez fournir des intentions et des entités en plus du dialogue. Vous devez également fournir un grand nombre d'exemples d'énoncé que le service peut utiliser pour former les intentions que vous souhaitez prendre en charge. Utilisez la documentation, les démonstrations et les outils fournis avec le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} pour créer un espace de travail avec des capacités personnalisées. Pour plus d'informations, reportez-vous à la [documentation de {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/index.html){: new_window}.

### A propos de cette tâche

Vous ne pouvez créer qu'un espace de travail pour définir des capacités personnalisées. Chaque intention que vous ajoutez à l'espace de travail est mis à disposition comme capacité personnalisée lorsque vous associez l'espace de travail à l'agent. L'espace de travail doit contenir toutes les capacités que vous souhaitez ajouter à votre agent. N'ajoutez pas à l'espace de travail des intentions que vous ne souhaitez pas que l'agent puisse traiter. 

### Procédure

1. A partir de votre instance de service {{site.data.keyword.conversationshort}}, créez un espace de travail qui définit vos capacités personnalisées. Reportez-vous à la [documentation du service {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

    Respectez les consignes suivantes : 
    - Ajoutez une branche pour chaque capacité à prendre en charge comme noeud de base (appelé *conversation de remplacement* dans l'interface utilisateur de l'outil {{site.data.keyword.conversationshort}}) dans le dialogue. Par exemple, vous ne devez pas définir un noeud de base dans votre dialogue qui reconnaît les messages d'accueils des utilisateurs et y répond, puis ajouter dessous des noeuds enfant qui correspondent à d'autres intentions de capacité personnalisée. 
    - Evitez de traiter les non concordances d'entrées utilisateur avec des boucles récursives. Ne créez que des tournures de dialogue comportant une fin définitive.
    - Ne créez pas une intention personnalisée de même nom qu'une intention utilisée par une capacité de base. Pour une liste de noms à éviter, voir [Noms d'intention](/docs/services/virtual-agent/intent_codenames.html).

1. Associez l'espace de travail à l'agent. Voir [Association d'espaces de travail](/docs/services/virtual-agent/link_workspace.html)
1. Dans la page **Configure (Configuration)**, ouvrez l'onglet **Custom capabilities (Capacités personnalisées)**.
1. Cliquez sur **Add Capabilities (Ajouter des capacités)**.
1. Sélectionnez l'espace de travail que vous avez associé à l'agent à l'étape 2, puis cliquez sur **Select Workspace (Sélectionner un espace de travail)**.

    Les intentions définies dans l'espace de travail associé sont maintenant répertoriées comme capacités activées. 

    > **Remarque :** vous ne pouvez pas désactiver des capacités individuelles. Si vous souhaitez supprimer une capacité personnalisée, vous pouvez supprimer l'intention de l'espace de travail dans l'outil du service {{site.data.keyword.conversationshort}}.
    Vous pouvez supprimer simultanément toutes les capacités en cliquant sur **Remove Private Capabilities (Supprimer les capacités privées)**. La suppression des capacités ne supprime pas l'association entre l'agent et l'espace de travail dans lequel les capacités sont définies. 

### Résultats

Une fois que vous avez ajouté des capacités personnalisées, chaque énoncé utilisateur évalué par {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} est transmis à l'espace de travail de base et à votre espace de travail personnalisé pour évaluation. La capacité qui correspond le mieux à l'intention de l'entrée de l'utilisateur est déclenchée et le dialogue associé est utilisé.

![Illustre un utilisateur transmettant un énoncé à Watson Virtual Agent. Il le transmet à la fois à l'espace de travail Built-in et à l'espace de travail Linked capabilities (Capacités associées) pour évaluation. Le niveau de fiabilité de l'espace de travail est de 0,85 alors que celui de l'espace de travail Linked capabilities (Capacités associées) est de 0,55. L'espace de travail Built-in (Intégré) retransmet une réponse à Watson Virtual Agent qui la transmet à l'utilisateur.](images/workspace-confidences.png)

### Test des capacités personnalisées
{: #test_custom_capabilities}

Une fois que vous avez ajouté vos propres capacités, effectuez des tests pour vous assurer qu'elles se comportent comme prévu. 

#### A propos de cette tâche

Si vous ajoutez vos propres capacités, vous pouvez facilement en définir une dont le comportement est similaire à celui d'une capacité de base existante. Dans ce cas, vérifiez que les deux n'entrent pas en concurrence entre elles lorsqu'elles répondent à certaines requêtes utilisateur.

#### Procédure

1. Utilisez la sous-fenêtre Preview (Aperçu) pour poser des questions ou créer les types de demande que vos clients sont susceptibles d'envoyer. 

    Sous la réponse, la capacité déclenchée pour répondre à la demande est affichée. Si la capacité affichée ne correspond pas à celle prévue, vous pouvez effectuer des modifications pour corriger le routage de l'énoncé aux capacités. 

1. Comparez les capacités définies dans l'application de base à celles définies dans l'espace de travail personnalisé. 

    - Pour examiner les capacités fournies avec l'application, reportez-vous à la rubrique  [Capacités de base](/docs/services/virtual-agent/intent_list.html) qui décrit chaque capacité de base.
    - Pour examiner les intentions définies dans l'espace de travail {{site.data.keyword.conversationshort}}, ouvrez cet espace de travail dans l'outil {{site.data.keyword.conversationshort}}, puis ouvrez la page **Intents (Intentions)**. Développez chaque intention pour afficher les types d'énoncé qu'elle est entraînée à fournir en réponse. 

1. Utilisez le panneau Preview (Aperçu) pour tester les énoncés qui selon vous risquent de provoquer un conflit. 

    En fonction des réponses, vérifiez si des capacités qui se chevauchent traitent des requêtes utilisateurs assez distinctes les unes des autres pour pouvoir coexister sans prêter à confusion pour l'utilisateur. Si deux capacités sont en concurrence pour les mêmes types d'énoncé, vous devez en désactiver une. Vous pouvez traiter des capacités qui se chevauchent de l'une des manières suivantes : 
    - **Désactivation de la capacité personnalisée**

        1. Dans l'outil {{site.data.keyword.conversationshort}}, recherchez l'intention dans la page **Intents (Intentions)**, développez-la, puis cliquez sur l'icône **Delete intent (Supprimer l'intention)** pour la supprimer de l'espace de travail.
        1. Une fois que vous avez modifié l'espace de travail, ce dernier est automatiquement formé à nouveau. Une fois que la formation est terminée, retournez à {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.
        1. Dans la page Configure (Configuration), ouvrez l'onglet **Custom Capabilities (Capacités personnalisées)** pour vous assurer que la capacité n'est plus répertoriée.

    - **Désactivation de la capacité base**

        1. Dans l'onglet **Core Capabilities (Capacités de base)** de la page Configure (Configuration) de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, recherchez la capacité à désactiver. 
        1. Cliquez sur la mosaïque pour ouvrir la capacité, puis basculez le commutateur On (Activé) sur Off (Désactivé). 

    - **Edition des données de formation pour la capacité personnalisée**

        Si la capacité personnalisée répond à un objectif client similaire, mais de portée plus vaste, vous pouvez supprimer les exemples d'énoncé des données de formation pour que la capacité personnalisée exclut les exemples qui se chevauchent avec les types d'énoncé traités par la capacité de base. Vous ne pouvez pas accéder à l'espace de travail de la capacité de base ; vous ne pouvez qu'éditer l'espace de travail de la capacité personnalisée pour appliquer les modifications. Pour déterminer les énoncés acheminés à la capacité de base, utilisez la sous-fenêtre Preview (Aperçu) afin de tester divers énoncés et découvrir ceux qui déclenchent la capacité de base.

        > **Attention :** si vous choisissez cette approche, soyez prêts à effectuer de nombreux tests et révisions. Il est difficile de prévoir la réaction de l'apprentissage automatique aux modifications des données de formation. Vous devrez effectuer de nombreux tests pour vous assurer que vos modifications ont l'impact attendu.

        Editez l'espace de travail de la capacité personnalisée de la manière suivante : 
        1. Dans l'outil {{site.data.keyword.conversationshort}}, recherchez l'intention dans la page **Intents (Intentions)**, puis développez l'intention pour afficher la liste des exemples d'énoncé.
        1. Cochez les cases en regard des énoncés traités par des capacités de base, puis cliquez sur **Remove examples (Supprimer les exemples)**.
        1. Une fois que vous avez modifié l'espace de travail, ce dernier est automatiquement formé à nouveau. 

    - **Conservation des deux capacités**

        Dans certains cas, bien que les capacités soient similaires, elles traitent des scénarios d'utilisation assez distincts pour que vous puissiez les laisser toutes deux activées. 

1. Entrez de nouveau les énoncés de test dans la sous-fenêtre Preview (Aperçu) pour vous assurer que vos modifications entraînent le comportement attendu. Si ce n'est pas le cas, effectuez des modifications supplémentaires. 

## Utilisation de la capacité None of the above (Aucun des choix ci-dessus)
{: #none_of_the_above}

Découvrez comment la capacité **None of the above (Aucun des choix ci-dessus)** est utilisée par l'agent virtuel.

Contrairement à toutes les autres capacités de base, la capacité **None of the above (Aucun des choix ci-dessus)** ne peut pas être désactivée. En effet, elle sert de fourre-tout pour les énoncés mappés à aucune des capacités configurées. Cette fonctionnalité est utile car vous pouvez fournir une réponse standard, comme *Je ne peux pas vous aider*, pour les demandes utilisateur de capacités dont votre agent ne dispose pas encore. Elle permet également de répondre à des questions absurdes que les clients posent parfois pour s'amuser lorsqu'ils commencent à interagir avec l'agent. Par exemple, *Que dois-je manger ce midi ?*

Son rôle étant unique dans le fonctionnement de l'agent virtuel, la configuration de son comportement est importante. La capacité **None of the above (Aucun des choix ci-dessus)** est souvent déclenchée et de manières pas toujours évidentes. Par exemple : 

- Si vous désactivez une autre capacité de base, les énoncés qui déclenchent la capacité désactivée sont réacheminés vers la capacité **None of the above (Aucun des choix ci-dessus)** pour une réponse.
- Si un énoncé ne correspond à aucune des capacités de base activées, il est transmis à la capacité **None of the above (Aucun des choix ci-dessus)** pour une réponse. Si vous fournissez un espace de travail associé avec des capacités personnalisées, l'espace de travail de base et l'espace de travail personnalisé évaluent tous deux l'énoncé pour rechercher une correspondance. Si aucune correspondance n'est trouvée, la réponse associée à la capacité de base **None of the above (Aucun des choix ci-dessus)** est utilisée.
- Vous pouvez configurer la capacité **None of the above (Aucun des choix ci-dessus)** de sorte à avoir un type de réponse **Use your own conversation (Utiliser votre propre conversation)** et à l'associer à un espace de travail avec un dialogue personnalisé. Si aucune intention ne correspond à un énoncé dans l'espace de travail de base, l'énoncé est transmis à la capacité **None of the above (Aucun des choix ci-dessus)**, qui la transmet à l'espace de travail personnalisé pour une réponse.
- Si vous dissociez un espace de travail et que cet espace de travail est associé à la capacité **None of the above (Aucun des choix ci-dessus)**, vous devez effectuer une action pour pouvoir continuer à dissocier l'espace de travail. Toute autre capacité associée à l'espace de travail à dissocier est automatiquement désactivée. Toutefois, la capacité **None of the above (Aucun des choix ci-dessus)** ne pouvant pas être désactivée, vous devez déterminer un comportement de réponse de remplacement. Par exemple, vous pouvez remplacer le type de réponse par **Display a text response (Afficher une réponse textuelle)** et ajouter un message textuel à utiliser dans la réponse. 

