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

# Tutoriel : ajout de capacités personnalisées 
{: #tutorial}

Ce tutoriel vous aide à comprendre comment étendre les capacités de votre agent virtuel en ajoutant vos propres capacités.
{: shortdesc}

Dans ce tutoriel, vous allez utiliser l'espace de travail qui alimente la simple démonstration {{site.data.keyword.conversationshort}} pour ajouter de nouvelles fonctionnalités à votre agent. L'espace de travail simule le rôle d'un copilote de pilote automobile. Vous pouvez consulter la démonstration [ici ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://conversation-simple.mybluemix.net/ "icône Lien externe"){: new_window}. Une fois que vous avez importé l'espace de travail dans votre instance de service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}, vous associerez cet espace de travail à votre agent. Vous ajouterez ensuite les intentions de l'espace de travail comme capacités personnalisées, puis résoudrez les conflits entre
les capacités de base et les capacités que vous ajoutez.

## Objectifs d'apprentissage

Après avoir terminé ce tutoriel, vous saurez comment effectuer les tâches suivantes :

- Associer un espace de travail à votre agent
- Utiliser un espace de travail associé pour ajouter des capacités personnalisées à votre agent
- Résoudre les conflits potentiels entre les capacités nouvelles et existantes

L'exécution de ce tutoriel prend environ 30 minutes. Si vous explorez d'autres concepts liés à ce tutoriel, son exécution peut être plus longue.

### Conditions préalables

Vous devez disposer d'un compte {{site.data.keyword.Bluemix_notm}} et être inscrit pour pouvoir utiliser le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Pour plus de détails, voir le [tutoriel Mise en route ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "icône Lien externe"){: new_window}. 

### Résultats

Une fois que vous aurez terminé ce tutoriel, en plus de répondre aux questions standard des utilisateurs sur votre société,
votre agent pourra répondre à des questions et des demandes telles que celles demandées par un pilote à
son copilote. Par exemple, *Quand penses-tu que nous arriverons ? * ou *Allume la radio.*

### Leçons de ce tutoriel

[Leçon 1 : importation d'un espace de travail dans {{site.data.keyword.conversationshort}}](tutorial.html#tutless1)

[Leçon 2 : association d'un espace de travail](tutorial.html#tutless2)

[Leçon 3 : ajout de capacités personnalisées](tutorial.html#tutless3)

[Leçon 4 : test des capacités personnalisées](tutorial.html#tutless4)

[Leçon 5 : résolution des conflits entre les capacités](tutorial.html#tutless5)

## Leçon 1 : importation d'un espace de travail dans Conversation 
{: #tutless1}

Dans cette leçon, vous allez apprendre comment importer un espace de travail dans le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.

### Avant de commencer

Vous devez disposer d'un compte {{site.data.keyword.Bluemix_notm}} et être inscrit pour le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.

### A propos de cette tâche

Pour simplifier le processus de création d'un espace de travail {{site.data.keyword.conversationshort}}, vous importerez le fichier `car_demo_workspace.json` qui contient les artefacts préconfigurés de la démonstration {{site.data.keyword.conversationshort}} simple.

### Procédure

1.  Téléchargez le fichier [car_demo_workspace.json ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json "icône Lien externe"){: new_window} sur votre ordinateur.
1.  [Connectez-vous ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://console.ng.bluemix.net/dashboard/watson "icône Lien externe"){: new_window} à votre instance de service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.
1.  Cliquez sur **Launch tool (Lancer l'outil)**.
1.  Pour importer un espace de travail à partir d'un fichier JSON, cliquez sur l'icône ![Flèche vers le haut au-dessus d'une boîte de réception pour indiquer une action d'importation](images/workspace_import.png).
1.  Cliquez sur **Choose a file (Choisir un fichier)** pour rechercher le fichier `car_demo_workspace.json` que vous avez téléchargé précédemment.
1.  Sélectionnez **Everything (Intents, Entities, and {{site.data.keyword.dialogshort}}) (Tout (Intentions, Entités et Dialogue))**, puis cliquez sur **Import (Importer)**.

### Résultats

L'espace de travail **Car Dashboard Tutorial (Tutoriel Tableau de bord automobile)** est ajouté à votre instance de service {{site.data.keyword.conversationshort}}.

## Leçon 2 : association d'un espace de travail 
{: #tutless2}

Dans cette leçon, vous allez apprendre comment associer un espace de travail du service {{site.data.keyword.conversationshort}} à votre agent.

### Procédure

1.  Dans le menu {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, sélectionnez **Linked Workspaces (Espaces de travail associés)**.
1.  Cliquez sur **Link Workspace (Associer un espace de travail)**.
1.  Sélectionnez l'instance du service {{site.data.keyword.conversationshort}} dans lequel vous avez importé l'espace de travail à la leçon précédente.
1.  Sélectionnez l'espace de travail **Car Dashboard Tutorial (Tutoriel Tableau de bord automobile)**.
1.  Cliquez sur **Link workspaces (Associer des espaces de travail)**.

## Leçon 3 : ajout de capacités personnalisées 
{: #tutless3}

Dans cette leçon, vous allez apprendre comment ajouter des capacités personnalisées à votre agent.

### Procédure

1.  Dans le menu {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, sélectionnez **Capabilities (Capacités)**.
1.  Cliquez sur l'onglet **Custom capabilities (Capacités personnalisées)**.
1.  Cliquez sur **Add Capabilities (Ajouter des capacités)**.
1.  Cliquez sur l'espace de travail **Car Dashboard Tutorial (Tutoriel Tableau de bord automobile)**, puis sur **Select Workspace (Sélectionner un espace de travail)**.

    La page Custom Capabilities (Capacités personnalisées) affiche maintenant une liste des capacités.

## Leçon 4 : Test des capacités personnalisées 
{: #tutless4}

Dans cette leçon, vous allez en apprendre davantage sur les capacités personnalisées que vous avez ajoutées.

### A propos de cette tâche

Maintenant que vous avez ajouté des capacités à l'agent, découvrez ce qu'elles peuvent accomplir.

### Procédure

1.  Dans l'en-tête {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, cliquez sur **Preview (Aperçu)**.
1.  Posez une question qui déclenchera une capacité personnalisée. Entrez le texte *Pouvons-nous écouter de la musique ?*

    L'agent évalue cette demande et la mappe à la capacité personnalisée **#turn_on**. Dans l'espace de travail associé, le noeud de dialogue contenant une condition qui correspond à l'intention #turn_on est utilisé. L'agent demande donc le genre de musique à écouter.

    > **Remarque :** vous pouvez voir à quelle capacité l'entrée utilisateur est mappée car le nom de la capacité est affiché sous forme de lien sous la réponse.

1.  Entrez un genre de musique, tel que *Classique* ou *Rock* pour compléter le dialogue.
1.  Click **Edit (Editer)** en regard de la capacité identifiée (#turn_on) dans l'historique d'aperçu pour ouvrir la page des capacités personnalisées.
1.  Posez maintenant une question qui déclenchera une capacité de base. Entrez le texte *Parlez-moi de vous*.

    Cliquez sur **Edit (Editer)** en regard du lien *System information (Informations système)* pour ouvrir la page des détails des capacités. Chaque capacité de base possède sa propre page de détails de capacité dans laquelle vous pouvez personnaliser la réponse.

1.  Essayez maintenant d'induire l'agent en erreur en entrant le texte *Pouvons-nous écouter de la musique ?*

    L'agent sait que vous avez déjà demandé à écouter de la musique et vous le dit.

## Leçon 5 : résolution de conflits entre les capacités 
{: #tutless5}

Dans cette leçon, vous allez apprendre à résoudre les conflits entre les capacités de base et les capacités personnalisées.

### A propos de cette tâche

Une fois que vous avez associé l'espace de travail personnalisé, vous êtes averti qu'il existe des conflits entre les capacités de base et certaines des capacités que vous avez ajoutées.

| Capacité de base    | Capacité personnalisée |
|--------------------|-------------------|
| Ending (Formule de politesse)             | #goodbyes         |
| Find nearest store (Rechercher le magasin le plus proche) | #locate_amenity   |
| Greetings (Salutations)          | #greetings        |
| Security assurance (Assurance sécurité) | #system_reliance  |

### Procédure

1.  Désactivez les capacités personnalisées que vous choisissez de ne pas utiliser.

    - Les objectifs des capacités `Ending (Formule de politesse)` et `#goodbyes` se chevauchent entièrement. Pour vous assurer que l'expérience des utilisateurs soit cohérente lorsqu'ils terminent une conversation avec votre agent, vous devez choisir d'utiliser l'une ou l'autre,
mais non les deux.

        Il est courant de construire une logique déclenchée à la fin d'une conversation. Pour garantir qu'un tel comportement reste sous le contrôle de Virtual Agent, utilisez la capacité de base `Ending (Formule de politesse)` au lieu de la capacité personnalisée.

    - Les capacités `Find nearest store (Rechercher le magasin le plus proche)` et `#locate_amenity` se chevauchent. Entrez les exemples d'énoncé suivants dans la sous-fenêtre Preview (Aperçu) pour le constater :

        - *find the nearest store* est acheminé vers `#locate_amenity`.
        - *find my store* est acheminé vers `Find nearest store (Rechercher le magasin le plus proche)`.

        La capacité personnalisée `#locate_amenity` fournit des informations sur une gamme plus vaste de commodités qu'un magasin seul, mais la capacité de base est associée à une conversation intégrée intéressante qui collecte un code postal pour l'utilisateur et renvoie l'adresse du magasin le plus proche. Pour bénéficier de ce comportement intégré, utilisez la capacité de base `Find nearest store (Rechercher le magasin le plus proche)`.

    - Les capacités liées à la sécurité se chevauchent également. Pour mieux comprendre quels types d'entrée utilisateur sont traitées par chacune d'elles, entrez ces exemples d'énoncé dans la sous-fenêtre Preview (Aperçu).

        - *Mes données sont-elles protégées ?* est acheminé vers `Security assurance (Assurance sécurité)`.
        - *Puis-je vous communiquer mes informations en toute sécurité ?* est acheminé vers `#system_reliance`.

        La capacité `#system_reliance` contenant des données de formation limitées par rapport à la capacité `Security assurance (Assurance sécurité)`, utilisez la capacité de base au lieu de la capacité personnalisée.

    Pour désactiver une capacité personnalisée, vous devez la supprimer de l'espace de travail {{site.data.keyword.conversationshort}}.
    1.  Dans l'outil {{site.data.keyword.conversationshort}}, développez l'intention `#goodbyes` dans la page Intents (Intentions), puis cliquez sur l'icône **Delete intent (Supprimer l'intention)** pour la supprimer de l'espace de travail.
    1.  Développez l'intention `#locate_amenity`, puis cliquez sur l'icône **Delete intent (Supprimer l'intention)** pour la supprimer de l'espace de travail.
    1.  Développez l'intention `#system_reliance`, puis cliquez sur l'icône **Delete intent (Supprimer l'intention)** pour la supprimer de l'espace de travail.

1.  Lorsque vous apportez des modifications à l'espace de travail personnalisé, ce dernier est automatiquement formé à nouveau avec ces nouvelles données. Une fois que la formation de l'espace de travail est terminée, retournez à {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.

    Dans la page Capabilities (Capacités), ouvrez l'onglet **Custom Capabilities (Capacités personnalisées)** pour vous assurer que les capacités que vous avez supprimées (`#goodbyes`, `#locate_amenity` et `#system_reliance`) ne sont plus répertoriées.

1.  Les capacités `Greetings (Salutations)` et `#greetings` se chevauchent entièrement. Nous souhaitons que l'agent adopte un comportement cohérent et montre une certaine personnalité. La capacité personnalisée `#greetings` étant conçue pour exprimer un type de personnalité spécifique qui reflète
la marque de la société, utilisez la capacité personnalisée au lieu de la capacité de base.

    Pour désactiver une capacité de base, vous devez la désactiver.
    1.  Dans l'onglet **Core Capabilities (Capacités de base)** de la page Capabilities (Capacités) de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, recherchez la capacité`Greetings (Salutations)`.
    1.  Cliquez sur la mosaïque pour l'ouvrir, puis basculez le commutateur On (Activé) sur **Off (Désactivé)**. Cliquez sur la flèche arrière pour retourner à la page de configuration principale.

1.  Effectuez davantage de tests en entrant des requêtes utilisateur de test dans la sous-fenêtre Preview (Aperçu) pour vous assurer que la capacité appropriée traite l'entrée utilisateur comme prévu. Par exemple, vous pouvez tester à nouveau les énoncés suivants :

    - *Puis-je vous communiquer mes informations en toute sécurité ?* doit être traité par la capacité `Security assurance (Assurance sécurité)`.
    - *find the nearest store* doit être traité par la capacité `Find nearest store (Rechercher le magasin le plus proche)`.

## Récapitulatif du tutoriel 
{: #tutless_sum}

En découvrant {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, vous avez étendu votre agent avec des capacités personnalisées.

### Points étudiés

En suivant ce tutoriel, vous avez appris les concepts suivants :

- Espaces de travail associés
- Capacités
- Capacités en conflit
