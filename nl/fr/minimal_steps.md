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

# Etapes suivantes du développement
{: #minimal_steps}

Comprendre les tâches de développement requises pour implémenter intégralement l'agent.
{: shortdesc}

Vous devez effectuer les tâches suivantes :

- Imbriquer l'agent virtuel dans votre application.

    A partir de la page **Publish (Publication)** de l'application
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}},
vous pouvez rapidement copier et coller le bot dans une page Web pour le tester et le
partager avec d'autres utilisateurs de votre organisation pour une évaluation initiale. 
Au moment d'héberger l'agent afin qu'il puisse être utilisé par le client, vous devez effectuer des étapes supplémentaires pour l'implémenter
de manière sécurisée et sans faille. Pour plus de détails, voir [Intégration de l'agent à votre interface utilisateur d'application](/docs/services/virtual-agent/integrate.html). 

- Créez une logique d'application qui prenne en charge les demandes d'informations ou les transactions métier qui peuvent se produire lors des conversations utilisateur. Travaillez avec les administrateurs qui ont configuré les capacités que votre organisation prendra en charge. Ils peuvent vous aider à comprendre le comportement attendu de l'agent virtuel en fonction de la capacité. Pour plus de détails, voir [Implémentation de capacités de base](/docs/services/virtual-agent/impl_intents.html).

Vous pouvez éventuellement fournir un dialogue personnalisé pour une capacité de base ou étendre les capacités de base avec vos propres capacités. Pour plus de détails, voir [Personnalisation de l'agent](/docs/services/virtual-agent/personalize.html). 

