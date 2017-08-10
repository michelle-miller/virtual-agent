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

# Adición de diálogos personalizados para las prestaciones básicas
{: #use_custom}

En cualquier prestación básica, puede optar por utilizar su propia conversación para interactuar con el usuario a fin de satisfacer el objetivo del usuario.
{: shortdesc}

## Creación de un diálogo personalizado
{: #custom_dialog}

Si una prestación principal que habilita requiere el manejo por parte de un diálogo personalizado, puede utilizar el servicio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} para crear el diálogo y a continuación enlazarlo al agente virtual.

### Acerca de esta tarea

El servicio {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} es un conjunto de herramientas y de API que puede utilizar para crear aplicaciones que utilizan interfaces de lenguaje natural para automatizar las interacciones con los clientes. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} utiliza el servicio {{site.data.keyword.conversationshort}} para definir las prestaciones entrenadas y el flujo de diálogo que utiliza el bot. Si el diálogo proporcionado no permite la flexibilidad que necesita, puede crear su propio diálogo utilizando las herramientas de servicio de {{site.data.keyword.conversationshort}}.

Por motivos de compatibilidad con el agente virtual, cualquier diálogo que cree debe cumplir las directrices de diseño definidas en [contrato de diálogo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Icono de enlace externo"){: new_window}. Estas directrices especifican cómo interactúa el diálogo con la interfaz de conversación del agente virtual, incluido cómo se visualizan los indicadores de solicitud a los usuarios y dónde se almacenará la información que proporcionen los usuarios de forma que sea accesible desde la interfaz de la ventana de conversación.

El repositorio de {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} también proporciona ejemplos que muestran cómo funcionan las interacciones del diálogo. Puede utilizar el ejemplo como modelo para su propio diálogo. Consulte la sección [Archivo JSON de flujos de diálogo de ejemplo![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/michelle-miller-patch-1/sample_dialog_flows.json "Icono de enlace externo"){: new_window}.

#### Procedimiento

Para crear un diálogo personalizado:

1.  Si no lo ha hecho ya, regístrese en el servicio {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Para obtener más información, consulte la documentación [Servicio {{site.data.keyword.conversationshort}}: Cómo empezar ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "Icono de enlace externo"){: new_window}.
1.  Cree un espacio de trabajo para contener el diálogo.

    Para obtener información sobre los espacios de trabajo, consulte la documentación [Servicio {{site.data.keyword.conversationshort}}: Creación de un espacio de trabajo ![Para obtener información sobre los espacios de trabajo, consulte la documentación ](../../icons/launch-glyph.svg "Para obtener información sobre los espacios de trabajo, consulte la documentación ")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace "Para obtener información sobre los espacios de trabajo, consulte la documentación "){: new_window}.

1.  Vaya directamente a la pestaña **{{site.data.keyword.dialogshort}}**. (No cree intenciones o entidades.)
1.  Cree un nodo de diálogo para cada prestación que desee personalizar.

    Un nodo de diálogo debe tener una condición que se evalúe en el nombre de intención para la prestación que lo utilizará.

    Utilice la sintaxis siguiente:

    ```java
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Por ejemplo, para la prestación **Contact us (Contáctenos)**, el *nombre-intención* es `Information-Contact_Us`. El diálogo probaría `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Si tiene un bot más antiguo y sus valores indican que desea revertir, de modo que la intención solo se pase al espacio de trabajo, en su lugar, utilice la sintaxis siguiente:

    ```java
    #intent-name
    ```
    {: screen}

    Por ejemplo, `#Information-Contact_Us`

    Para descubrir el nombre de intención asociado con una prestación, consulte [Nombres de intención](intent_codenames.html).

1.  Añada nodos según se requiera para crear el flujo de diálogo necesario.

    Para que sea compatible con {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, el diálogo debe cumplir determinadas directrices de diseño cuando almacene la información recopilada o utilice sucesos para la comunicación con la interfaz del widget de conversación. Cree un diálogo que cumpla las directrices de diseño de diálogos de {{site.data.keyword.virtualagentshort}} en [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Icono de enlace externo"){: new_window}.

1.  Enlace al agente los espacios de trabajo con diálogos que haya creado.

    Consulte [Enlace de espacios de trabajo](link_workspace.html) para obtener más detalles.

1.  En el separador **Core Capabilities (Prestaciones básicas)** de la página Configurar, cambie el tipo de respuesta de cada prestación para la que desee utilizar un diálogo personalizado al tipo de respuesta **Use your own conversation (Utilizar su propia conversación)**.
1.  Seleccione el espacio de trabajo que contiene el diálogo que desee utilizar en la lista de espacios de trabajo enlazados y a continuación pulse **Save (Guardar)** para acabar de establecer el enlace.

    Si todavía no ha enlazado el espacio de trabajo, puede pulsar aquí **Link a workspace (Enlazar un espacio de trabajo)** para enlazar un espacio de trabajo, creado anteriormente, con el agente.
