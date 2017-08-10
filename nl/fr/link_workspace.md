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

# Association d'espaces de travail 
{: #link_workspace}

Pour pouvoir utiliser une capacité personnalisée ou un dialogue personnalisé avec une capacité de base, vous devez établir une connexion entre l'agent virtuel et l'espace de travail due service {{site.data.keyword.conversationshort}} qui contient les artefacts à utiliser.
{: shortdesc}

## A propos des espaces de travail

Un espace de travail est un conteneur du service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} qui contient des intentions, des entités et un dialogue, qui représentent les artefacts utilisés pour définir et former un flux de conversation. Votre agent peut utiliser les artefacts de l'espace de travail, y compris les intentions formées et un dialogue, lorsqu'il interagit avec vos clients pour personnaliser et étendre la portée de ce dont il peut discuter.

Vous pouvez associer des espaces de travail pour atteindre les objectifs suivants :

- Définir vos propres capacités : l'espace de travail doit inclure des intentions, des exemples d'énoncé et un dialogue avec des conditions de noeud qui correspondent à chaque intention définie.
- Définir un dialogue personnalisé pour une capacité de base : l'espace de travail doit inclure un dialogue avec une condition de noeud qui correspond au nom d'intention d'une capacité de base.

Vous *pouvez* utiliser le même espace de travail pour ajouter à la fois des capacités personnalisées et des dialogues personnalisés pour des capacités de base. Toutefois, les opérations de gestion sont plus simples si vous créez un seul espace de travail dédié pour définir les capacités personnalisées à utiliser et un ou plusieurs espaces de travail distincts pour définir les dialogues à utiliser comme réponses pour les capacités de base. Si vous choisissez d'utiliser le même espace de travail pour les capacités et les dialogues, veillez à bien ajouter les noeuds qui contiennent des dialogues personnalisés pour des capacités de base spécifiques au début de l'arborescence des dialogues pour éviter que les énoncés ne soient acheminés à tord vers des capacités personnalisées. 

### Procédure

1.  Ouvrez la page **Linked Workspaces (Espaces de travail associés)** de l'agent actuel.
1.  Cliquez sur **Link Workspace (Associer un espace de travail)**.

    Spécifiez les données d'identification de votre compte {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} pour permettre à {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} d'accéder à votre instance de service {{site.data.keyword.conversationshort}} et d'extraire les informations sur les espaces de travail.

1.  Sélectionnez l'instance du service {{site.data.keyword.conversationshort}} qui contient les espaces de travail à utiliser.
1.  Sélectionnez un ou plusieurs espaces de travail à associer à votre agent.
1.  Cliquez sur **Link workspaces (Associer des espaces de travail)**.

[Création d'un dialogue personnalisé](add-custom-dialog.html)

[Ajout de vos propres capacités](add-custom-capabilities.html)

## Dissociation d'espaces de travail 
{: #unlink_workspace}

Si vous décidez de ne plus maintenir de connexion entre votre agent virtuel et un espace de travail {{site.data.keyword.conversationshort}} spécifique, vous pouvez dissocier cet espace de travail.

### Avant de commencer

Assurez-vous que l'espace de travail à dissocier n'est pas activement utilisé par une capacité qui en a besoin. N'oubliez pas qu'un espace de travail que vous associez à l'agent virtuel peut être utilisé par toute capacité associée à cet agent, qu'il s'agisse d'une capacité personnalisée ou d'une capacité de base.

### A propos de cette tâche

Lorsque vous dissociez un espace de travail d'une capacité, cette dernière est automatiquement désactivée. La désactivation de la capacité garantit que les utilisateurs actifs ne sont pas exposés à un comportement inattendu lorsque vous apportez des modifications. Cette approche est vraie pour toutes les capacités, exceptée la capacité **None of the above (Aucun des choix ci-dessus)**, qui ne peut pas être désactivée. Vous devez remplacer le type de réponse **Use your own conversation (Utiliser votre propre conversation)** par l'une des autres options de type de réponse de cette capacité pour pouvoir dissocier un espace de travail qui y est associé.

### Procédure

1.  Ouvrez la page **Linked Workspaces (Espaces de travail associés)** de l'agent actuel.
1.  Cliquez dessus pour ouvrir l'espace de travail à dissocier de l'agent.
1.  Cliquez sur **Unlink this Workspace (Dissocier cet espace de travail)** ![icône de corbeille représentant la suppression de relation de lien](images/trash.png).

[Association d'espaces de travail](link_workspace.html)
