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

# Ajout du widget de discussion fourni à votre interface utilisateur 
{: #integrate_add-chat}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} est fourni avec un widget de discussion que vous pouvez utiliser tel quel dans votre interface utilisateur.
{: shortdesc}

Ce diagramme illustre la circulation de la conversation à travers le système lorsque vous utilisez le widget de discussion fourni par {{site.data.keyword.IBM_notm}}.

![Illustre une configuration standard dans laquelle le widget de discussion fourni est utilisé.](images/builtin_chat_new.png)

1.  Pour utiliser le widget fourni, ouvrez le référentiel GitHub du [widget de discussion {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://github.com/watson-virtual-agents/chat-widget "icône Lien externe"){: new_window}, puis suivez les étapes du fichier `README.md`. 

    Le widget de discussion fourni est extensible. S'il contient des éléments que vous souhaitez modifier, vous pouvez les personnaliser. Par exemple, pour modifier une présentation utilisée par le widget de discussion fourni, vous pouvez écrire une présentation personnalisée qui la remplace. Voir l'exemple à l'adresse suivante : [https://github.com/watson-virtual-agents/chat-widget/tree/1.2.12/examples/basic-custom-layout. ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externen")](https://github.com/watson-virtual-agents/chat-widget/tree/1.2.12/examples/basic-custom-layout "icône Lien externen"){: new_window} Gardez à l'esprit que la présentation peut être utilisée par plusieurs intentions.

1.  Pour plus d'informations sur les étapes à suivre pour prendre en charge les transactions du widget de discussion qui peuvent avoir lieu pour les capacités qui utilisent la conversation intégrée, voir [Implémentation de la logique de prise en charge de la conversation intégrée](impl_intents.html#backend_transaction).

Si les personnalisations que vous souhaitez effectuer sont tellement répandues qu'il est impossible d'implémenter vos modifications en mettant à jour le widget de discussion fourni, vous pouvez créer votre propre interface de discussion. Voir [Création d'une interface de discussion personnalisée](integrate_custom-chat.html).
