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

# Création d'un agent
{: #agent-create}

Lorsque vous vous abonnez au service, un bot est mis à votre disposition avec un pack de capacités **General Customer Service (Service clients général)** en anglais activé. 
Vous pouvez créer des bots supplémentaires avec d'autres packs de capacités ou qui conversent avec les clients dans des langues
autres que l'anglais.
{: shortdesc}

Pour spécifier un agent avec une autre capacité comme agent principal, créez un
agent avec le pack de capacités de votre choix, après quoi vous pourrez supprimer l'agent
provisionné pour vous initialement. Veillez à bien changer d'agent avant d'avoir passé trop de temps à configurer l'agent General Customer Service (Service clients général). Pour plus d'informations, voir [Suppression d'un agent](agent-create.html#delete). 

Si vous passez du temps à configurer une instance d'agent pour la peaufiner et que vous souhaitez
la déployer pour l'utiliser, tout en continuant de la tester ou d'essayer de l'améliorer, vous pouvez cloner l'agent
afin de créer une copie à des fins de test. Pour plus de détails, voir [Clonage d'un agent](agent-create.html#clone). 

## Nombre maximal d'agents

Le nombre d'agents que vous pouvez créer dépend de votre plan de service.

| Plan de service  |      Nombre d'agents  |
|------------------|----------------------:|
| Evaluation       |                     2 |
| Standard         |                    10 |
| Premium          |                   100 |

Gardez à l'esprit que les appels d'API effectués à partir de plusieurs bots
déployés sont cumulés et entrent en compte dans le nombre total de réponses
d'agent virtuel allouées à votre abonnement. 

### Procédure

Pour créer un agent, procédez comme suit :

1.  A partir du menu principal ![Icône avec trois lignes horizontales](images/hamburger.png), cliquez sur **Create New Agent (Créer un agent)**.

1.  Choisissez le type de pack de capacités à provisionner pour l'agent lorsqu'il est créé.
   La mosaïque identifie les langues prises en charge. Toutefois, les capacités ne sont pas toutes disponibles dans chacune des langues. Cliquez sur le lien **View Details (Afficher les détails)** pour afficher une liste complète des capacités prises en charge par langue. 

1.  Cliquez sur **Select (Sélectionner)** sur une mosaïque de pack de capacités pour créer un agent provisionné avec ce type de pack.

1.  Si applicable, choisissez la langue, puis spécifiez les informations demandées pour l'agent.
   >**Remarque :** le libellé d'agent que vous spécifiez ici n'est affiché que dans les outils d'administration Watson Virtual Agent que vous utilisez pour gérer l'agent. 
Il ne s'agit pas du nom de Virtual Agent qui interagit avec vos utilisateurs ; vous
pouvez définir ou modifier cela à partir de la page **Settings
(Paramètres)**.
1.  Cliquez sur **Create (Créer)**.

## Clonage d'un agent
{: #clone}

Clonez un agent pour en créer un nouveau avec la même configuration et les mêmes
paramètres que celui d'origine. Une fois que vous avez cloné l'agent, l'agent d'origine
et le clone ne sont plus liés l'un à l'autre. Les modifications que vous apportez à
l'un ne sont **pas** appliquées à l'autre. 

Vous ne pouvez pas créer un clone d'un agent dans une langue autre que celle de
l'agent d'origine.

### Procédure

Pour créer un agent, procédez comme suit : 

1.  Ouvrez la page **Settings (Paramètres)** de l'agent à
cloner.

1.  Faites-défiler la page, puis cliquez sur **Clone Agent (Cloner l'agent)**.

1.  Fournissez les informations demandées pour l'agent.
   >**Remarque :** le libellé d'agent que vous spécifiez ici n'est
affiché que dans les outils d'administration Watson Virtual Agent que vous utilisez pour
gérer l'agent. Il ne s'agit pas du nom de Virtual Agent qui interagit avec vos
utilisateurs ; vous le définissez ailleurs.
1.  Cliquez sur **Clone (Cloner)**. 

## Suppression d'un agent
{: #delete}

Si vous n'utilisez pas un agent, supprimez-le de sorte qu'il ne soit plus pris en
compte dans le nombre maximal d'agents. 

### Procédure

Pour créer un agent, procédez comme suit : 

1.  Ouvrez la page **Settings (Paramètres)** de l'agent à supprimer.

1.  Faites-défiler la page, puis cliquez sur **Delete Agent (Supprimer l'agent)**.

1.  Lorsque vous y êtes invité, entrez le texte `delete`, puis cliquez sur **OK**.
