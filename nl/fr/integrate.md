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

# Intégration de l'agent
{: #integrate}

Pour publier l'agent à des fins de production, vous devez effectuer des étapes
supplémentaires pour prendre en charge les fonctions effectuées par l'agent et permettre
aux utilisateurs d'accéder à ce dernier de manière sécurisée.
{: shortdesc}

## Choisissez une méthode d'intégration

Vous pouvez intégrer l'agent de l'une des manières suivantes : 

- Ajoutez l'interface de discussion fournie par {{site.data.keyword.IBM_notm}} telle quelle au site Web présenté à vos clients.
  Voir [Ajout du widget de discussion fourni à votre interface utilisateur](integrate_add-chat.html).

- Développez la fenêtre de discussion fournie pour la personnaliser en fonction de vos besoins.
  Voir [Ajout du widget de discussion fourni à votre interface utilisateur](integrate_add-chat.html).

- Créez votre propre interface de discussion à l'aide du SDK client fourni.
  Voir [Création d'une interface de discussion personnalisée](integrate_custom-chat.html).

- Ajoutez l'agent à un canal de support existant et utilisez l'API afin d'interagir avec l'agent à l'aide d'un programme. Voir [Ajout de l'agent à un canal de support existant](integrate_backend.html).

### Avant de commencer

Quelle que soit la méthode que vous utilisez pour publier l'agent à des fins de
production, il est recommandé de cloner l'agent au préalable. Disposer d'une copie non
intégrée de l'agent vous permet de tester les modifications ou ajouts de fonctionnalité
sur la copie de test avant de les appliquer à l'agent utilisé dans un environnement de
production. Pour plus d'informations, voir [Clonage de l'agent](agent-create.html#clone).
