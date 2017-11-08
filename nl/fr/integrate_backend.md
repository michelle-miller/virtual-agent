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

# Ajout de l'agent à un canal de support existant
{: #integrate_backend}

L'API {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} est conçue pour prendre en charge la transition aisée d'une conversation entre l'agent virtuel et une personne physique ou un autre service de bot au sein d'une infrastructure de support existante. En fait, l'équipe LivePerson, Inc. s'est associée à {{site.data.keyword.IBM}} pour implémenter une telle intégration. Pour plus de détails, voir [Intégration LiveEngage ](integrate_backend.html#liveperson) ci-dessous.
{: shortdesc}

Pour créer vous-même une solution simple, vous pouvez coder votre
application de sorte que les capacités configurées pour être transférées à un agent humain
soient transmises à un canal existant surveillé par le service d'assistance. Pour plus d'informations sur le transfert d'une conversation à Slack, par exemple, voir [Réponses dW ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://developer.ibm.com/answers/questions/318623/where-can-i-find-documentation-examples-on-integra/ "icône Lien externe"){: new_window}. 

Pour utiliser l'API {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} afin d'intégrer l'agent virtuel dans un canal de support existant, procédez comme suit :

1.  Extrayez les clés d'API nécessaires pour effectuer des appels d'API. Pour plus de détails, voir [Obtention des clés d'API](api-keys.html). 

1.  Utilisez les API REST {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} pour interagir avec le bot à l'aide d'un programme. Accédez au portail de l'**[explorateur d'API d'{{site.data.keyword.IBM_notm}} developerWorks](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}** pour accéder aux API REST sur {{site.data.keyword.Bluemix_notm}}.

1.  Pour obtenir l'ID bot, effectuez l'une des opérations suivantes : 
    - Pour obtenir l'ID bot à partir de l'interface utilisateur des outils de configuration {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, procédez comme suit : 
      1.  Dans le menu principal ![Icône avec trois lignes horizontales](images/hamburger.png) de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, cliquez sur **Documentation**, puis sur l'onglet **Publish (Publication)**. 
      1.  Copiez la valeur botID à partir du bloc de script. 

    - Pour obtenir l'ID bot à partir du site Web de l'explorateur d'API, procédez comme suit : 
      1.  Connectez-vous à l'[explorateur d'API IBM developerWorks ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://developer.ibm.com/api/ "icône Lien externe"){: new_window}.
Cliquez sur **My APIs (Mes API)**, puis cliquez sur la mosaïque {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.
      1.  Cliquez sur **Documentation > Retrieve Bot (Extraire le bot)** dans la barre de navigation.
      1.  Cliquez sur **USE (UTILISER)** en haut de la fenêtre de référence de l'explorateur d'API.
      1.  Faites défiler la page sous la section *Path and Query parameters (Paramètres de chemin et de requête)*, puis cliquez sur **TEST (TESTER)**.
      >**Remarque :** vous devez sélectionner une clé à utiliser avec l'API pour pouvoir effectuer le test.

      1.  L'ID bot est affiché dans le paramètre `bot_id`, dans la réponse résultante. 

## Intégration LiveEngage
{: #liveperson}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} est conçu pour fonctionner en harmonie avec ses homologues humains.

Par exemple, LivePerson, Inc., un fournisseur de solutions de messagerie
professionnelle cloud mobiles et en ligne, s'est associé à IBM pour imbriquer un bot {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} dans leur
expérience de discussion LiveEngage. **LiveEngage** est une
plateforme d'entreprise cloud qui permet aux clients de communiquer directement
leurs marques favorites. La nouvelle offre, **LiveEngage with
Watson**, ajoute les réponses d'un bot {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} à l'interaction, des représentants du service clients
n'intervenant sans faille et en temps réel que si nécessaire. 

Le bot LivePerson exploite un grand nombre des comportements suivants, qui sont offerts par {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} : 

- Acceptation des conversations qui lui sont acheminées par le service externe. 
- Déclenchement du transfert des conversations vers le service externe dans les cas suivants : 
    - Le client demande à parler à un agent humain. 
    - Une capacité est configurée pour acheminer la demande vers un agent humain. 
    - Le client pose une question à laquelle le bot ne peut pas répondre.
- Identification et indication du point dans la conversation à partir duquel l'utilisateur ne comprend plus le bot ou ne s'intéresse plus à la conversation.
- Reconnaissance de la fin de la conversation et notification du service pour permettre le lancement des activités requises par l'interaction. 
- Lorsque vous transférez une conversation, les informations sur l'intention de l'utilisateur sont incluses de sorte que la conversation puisse être acheminée à l'agent
humain le plus à même de répondre aux demandes de ce type. 
- Lorsque vous transférez une conversation, l'historique de la discussion est inclus de sorte que la personne qui reprend le problème comprenne le contexte de
la conversation ayant eu lieu jusqu'à présent.

Pour demander l'accès à l'offre, reportez-vous au [site Web de LivePerson ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://engage.liveperson.com/usage/watson/?utm_medium=website&utm_source=IBM&utm_campaign=Watson "icône Lien externe"){: new_window}.
