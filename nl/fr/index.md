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

# Présentation
{: #index}

{{site.data.keyword.virtualagentfull}} est un ensemble de composants cognitifs préconfigurés basé sur le service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. 
En configurant l'agent virtuel avec les informations de votre société, vous pouvez
rapidement implémenter un bot de discussion automatisé qui converse avec vos clients pour
les aider à atteindre leurs objectifs. 
{: shortdesc}

{{site.data.keyword.watson}}&trade; {{site.data.keyword.virtualagentshort}} fournit les composants suivants :

- Un outil de configuration permettant de configurer la manière dont le bot doit répondre aux divers types de demande.
- Un ensemble de capacités qui représentent les actions ou les objectifs courants généralement souhaités par les clients (tels que "Payer ma facture" ou "M'indiquer vos horaires d'ouverture").
- Un modèle de langage naturel entraîné à identifier les intentions en fonction de l'entrée du client. 
- Un flux de dialogues de conversation qui peut gérer des demandes complexes en demandant des informations supplémentaires, générer des réponses et déclencher des événements à traiter par votre application. Si le dialogue prédéfini ne répond pas à vos besoins, vous pouvez implémenter votre propre dialogue personnalisé à l'aide des outils du service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.
- Un mécanisme permettant d'étendre les capacités de l'agent avec des capacités personnalisées que vous définissez dans un espace de travail {{site.data.keyword.conversationshort}} et associer à l'agent.
- Un widget de discussion que vous pouvez imbriquer dans votre page Web et un SDK que vous pouvez utiliser pour développer un widget de discussion personnalisé. 
- Un ensemble d'API que vous pouvez utiliser pour intégrer votre application à l'agent virtuel.

## Présentation de l'architecture
{: #arch_overview}

Le diagramme suivant illustre l'architecture d'une implémentation type de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} : 

![Présentation de l'architecture](images/arch-overview.png)

L'implémentation inclut les principaux composants suivants : 

- **Service {{site.data.keyword.conversationshort}}**

    Instance du service {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Le service {{site.data.keyword.conversationshort}} fournit les artefacts des capacités : les intentions, les entités et le flux de dialogues, avec le traitement cognitif sous-jacent qui alimente les capacités du bot de discussion. Vous n'interagissez directement avec l'espace de travail {{site.data.keyword.conversationshort}} que lorsque vous souhaitez implémenter un dialogue personnalisé ou une capacité personnalisée. 

    Pour plus d'informations sur les intentions et les dialogues, reportez-vous à la [documentation du service {{site.data.keyword.conversationshort}}](http://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html) <!--
{a:target="_blank"} -->.

- **Bot**

    Un bot développé sur le service {{site.data.keyword.conversationshort}}, avec un ensemble de capacités. Ce bot est entraîné à reconnaître les demandes des utilisateurs liées à l'engagement des clients, telles que les demandes d'informations de base sur la société et de paiement des factures. L'outil de configuration de bot fourni permet de configurer les informations spécifiques de la société qui peuvent être fournies en réponse aux requêtes utilisateur et de configurer la réponse pour chaque capacité. 

- **Site Web de votre société**

    Application métier présentées à vos clients, qui gère les communications avec le bot {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} et vos systèmes d'enregistrement (tels que les bases de données client ou les systèmes de facturation).

- **Fenêtre de discussion**

    Interface de discussion de l'agent virtuel utilisée par les clients pour converser avec le bot. Vous pouvez utiliser le widget de discussion fourni, personnalisé ou non, ou le SDK client pour implémenter votre propre widget de discussion. 

