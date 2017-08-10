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

# Analyse de l'activité des utilisateurs 
{: #dashboard}

La page Metrics (Métriques) contient un tableau de bord avec des visualisations qui permettent d'obtenir des informations à partir des données collectées par l'agent virtuel.
{: shortdesc}

Votre instance de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} doit être déployée et les utilisateurs doivent participer à des conversations avec votre agent virtuel pendant au moins 30 minutes avant que le tableau de bord ne contienne des données à partager.

## A propos des métriques

Les métriques de la page sont mises à jour toutes les 30 minutes avec les données des conversations qui ont lieu entre l'agent virtuel et vos utilisateurs. Elles fournissent des informations telles que les suivantes :

- Le nombre de conversations ayant lieu
- Le nombre d'utilisateurs, nouveaux et existants, conversant avec l'agent virtuel
- Ce que les clients souhaitent le plus et le moins effectuer ou apprendre (en fonction des intentions les plus déclenchées et les moins déclenchées)

Les métriques peuvent vous aider à rechercher les domaines dans lesquels un travail supplémentaire pourrait améliorer considérablement les performances de Virtual Agent :

- Comparer les sujets répandus aux intentions et entités que le service est entraîné à reconnaître. Les écarts peuvent vous aider à découvrir de nouvelles intentions ou une terminologie que vous pouvez apprendre à l'agent virtuel.
- Examiner les intentions identifiées le plus souvent justes avant que les utilisateurs ne demandent à parler à un agent humain. L'étude des causes d'escalade peut vous aider à définir les priorités de vos futurs efforts de formation. Vous pouvez déterminer si les demandes des utilisateurs sont mal interprétées, s'il manque une intention courante dans votre service, si les réponses associées à une intention doivent être améliorées, etc.

Les métriques peuvent également vous aider à planifier les affectations de ressources d'agent humain en fonction des données sur les zones géographiques dans lesquelles l'utilisation de Virtual Agent est le plus ou le moins fréquent et des pics de durée de conversation.

Les métriques analysent les données des conversations de manière détaillée, en se concentrant sur les artefacts qui constituent les capacités et notamment sur les artefact suivants :

- **Entités**

    Une *entité* représente un terme ou un objet correspondant à une intention et qui fournit un contexte spécifique pour une intention. Par exemple, une entité peut représenter une ville dans laquelle l'utilisateur souhaite
rechercher un site d'entreprise ou le montant d'un règlement de facture. Dans l'interface utilisateur, le nom d'une entité est toujours préfixé du caractère `@`.

- **Intentions**

    Une *intention* représente l'objectif de l'entrée d'un utilisateur. Chaque capacité utilise un discriminant de langage naturel qui peut évaluer l'énoncé d'un utilisateur et rechercher une intention prédéfinie si une telle intention est présente. Dans l'interface utilisateur, le nom d'une intention est toujours préfixé du caractère `#`.

### Procédure

1.  Ouvrez la page **Metrics (Métriques)** de l'agent actuel.

    Le haut de la page comporte un récapitulatif des principaux points de données et vous donne un aperçu rapide du fonctionnement de Virtual Agent. Pour chaque point de données, le pourcentage de changements au cours de la période sélectionnée est affiché entre parenthèses. (N/A), qui signifie *non disponible*, est affiché tant que la période n'est pas écoulée et qu'un changement ne peut pas être mesuré et affiché.

    Les nombres indiqués dans le récapitulatif peuvent parfois différer de ceux affichés sur les autres pages. Par exemple, le nombre total d'interactions affichées ici peut différer du total affiché dans l'onglet **Interactions**. La différence peut provenir du fait que les informations récapitulatives sont agrégées et mises à jour sur une période de 30 minutes alors que l'onglet **Interactions** est mis à jour en temps réel.

    Exploration en aval des données de chaque onglet pour en savoir plus.
    - **Agent Metrics (Métriques d'agent)**

        Découvrez ce que vos utilisateurs souhaitent apprendre ou effectuer lorsqu'ils abordent l'agent virtuel et quels objectifs utilisateur l'agent virtuel n'a pas pu satisfaire.
        - Le diagramme interactif **Intents &amp; Entities (Intentions et entités)** fournit des informations sur la manière dont le service {{site.data.keyword.conversationshort}} interprète l'entrée utilisateur. Il indique quelles entités ont été utilisées par le service pour l'aider à identifier l'intention de l'utilisateur.

            La syntaxe suivante est utilisée pour vous aider à interpréter plus rapidement les informations du diagramme :
            - `#<intent-name>`
            - `@<entity-name>`

            Cliquez sur une intention pour découvrir quelle intention a aidé le service à comprendre l'entrée utilisateur comme il l'a fait. Vous pouvez également cliquer sur une entité pour découvrir quelles intentions elle a aidé le service à identifier.

        - Le diagramme **Topics (Sujets)** capture les mots ou les phrases que les utilisateurs énoncent le plus souvent dans une conversation. Examinez-le pour découvrir de quels sujets les utilisateurs préfèrent parler. Les mots de ce diagramme sont distincts des entités capturées dans le diagramme Intents &amp; Entities (Intentions et entités). Les entités sont des mots que le service {{site.data.keyword.conversationshort}} a été entraîné à comprendre et associer à des intentions particulières. Les mots capturés dans le diagramme Topics (Sujets) sont simplement les mots les plus fréquemment rencontrés dans les conversations des utilisateurs. Les deux peuvent éventuellement se chevaucher. Gardez un oeil sur les mots du diagramme Topics (Sujets) pour rester en phase avec vos utilisateurs et découvrir les nouvelles choses qu'ils souhaitent effectuer ou apprendre. Les sujets répandus qui le restent peuvent représenter de bons candidats pour de nouvelles entités susceptibles d'aider {{site.data.keyword.watson}} à reconnaître des intentions existantes, ou suggérer de nouvelles intentions à apprendre à {{site.data.keyword.watson}}.

    - **User Metrics (Métriques utilisateur)**

        Obtenez des informations sur la localisation géographique de vos utilisateurs et sur le volume de conversations.

    - **Interactions**

        Consultez les retranscriptions de conversations individuelles.

        Les retranscriptions ne contiennent pas d'informations identifiant la personne. Même le nom de l'utilisateur qui a participé à la conversation reste privé. Un ID utilisateur, tel que 509JAJT8PX, est utilisé à sa place. Les autres informations identifiant la personne que les utilisateurs fournissent au cours de la conversation, telles que les numéros de téléphone ou les codes postaux, sont remplacées par des variables qui indiquent les types de données fournies, et non les données elles-mêmes.

        > **Remarque :** le terme *interaction* représente une conversation entre l'utilisateur et l'agent virtuel. L'interaction démarre lorsque l'utilisateur commence à discuter avec l'agent virtuel et se termine à la fin de la session de la fenêtre de discussion (qui a lieu lorsque l'utilisateur est déconnecté, qu'il se déconnecte, qu'il ferme la fenêtre de discussion ou qu'il l'actualise). Une interaction inclut souvent plusieurs échanges de mots ; les utilisateurs peuvent cliquer sur des boutons, afficher des graphiques tels que des cartes et effectuer d'autres transactions. De plus, contrairement à un appel téléphonique au service clients, l'interaction avec la session de discussion de Virtual Agent ne se termine pas dès que l'utilisateur l'interrompt. L'agent virtuel n'a pas d'autre rendez-vous ; il reste là au cas où l'utilisateur souhaite effectuer autre chose ou poser une autres question. Par exemple, si l'utilisateur pose une question, puis que 20 minutes après il en pose une autre (à l'intérieur de la même session de fenêtre de discussion), les deux échanges sont traités comme une même interaction d'une durée d'environ 25 minutes.

1.  Si vous découvrez des données significatives que vous souhaitez partager avec des tiers, vous pouvez les exporter au format CSV.
