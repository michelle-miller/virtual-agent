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

# Enlace a los espacios de trabajo
{: #link_workspace}

Para utilizar una prestación personalizada o un diálogo personalizado con una prestación básica, primero debe establecer una conexión entre el agente virtual y el espacio de trabajo del servicio {{site.data.keyword.conversationshort}} que contiene los artefactos que desea utilizar.
{: shortdesc}

## Acerca de esta tarea

Un espacio de trabajo es un contenedor de servicio de {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} que contiene intenciones, entidades y un diálogo, que son artefactos que se utilizan para definir y entrenar un flujo de conversación. El agente puede utilizar artefactos del espacio de trabajo, que incluye intenciones entrenadas y un diálogo, cuando interactúa con los clientes para personalizar y ampliar el ámbito de los temas que puede tratar.

Puede enlazar espacios de trabajo para conseguir los objetivos siguientes:

 - Definir sus propias prestaciones: el espacio de trabajo debe incluir intenciones, expresiones de ejemplo y un diálogo con condiciones de nodo que coincidan con cada intención definida. 
 - Definir un diálogo personalizado con una prestación básica: el espacio de trabajo debe incluir un diálogo con una condición de nodo que coincida con el nombre de la intención para una prestación básica.

No puede utilizar el mismo espacio de trabajo para añadir prestaciones personalizadas que el que utiliza para añadir un diálogo a una prestación básica. Debe crear un único espacio de trabajo dedicado que defina todas las prestaciones personalizadas que desee utilizar. Cree uno o más espacios de trabajo distintos para definir los diálogos que desea utilizar como respuestas para las prestaciones básicas.

## Procedimiento

1. En el menú de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, seleccione **Espacios de trabajo enlazados**.
1. Pulse **Enlazar espacio de trabajo**.

    Proporcione las credenciales de su cuenta de {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} para dar a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} permiso para acceder a la instancia de servicio de {{site.data.keyword.conversationshort}} y obtener la información del espacio de trabajo.

1. Seleccione la instancia del servicio {{site.data.keyword.conversationshort}} que contenga los espacios de trabajo que desee utilizar.
1. Seleccione uno o más espacios de trabajo que desee enlazar al agente.
1. Pulse **Enlazar espacios de trabajo**.

[Creación de un diálogo personalizado](/docs/services/virtual-agent/personalize.html#custom_dialog)

[Adición de sus propias prestaciones](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Desenlace de espacios de trabajo
{: #unlink_workspace}

Si decide que no desea mantener una conexión entre el agente virtual y un espacio de trabajo específico de {{site.data.keyword.conversationshort}}, puede desenlazar el espacio de trabajo.

### Antes de empezar

Asegúrese de que el espacio de trabajo que desea desenlazar no esté siendo activamente utilizado por una prestación que lo requiera. Recuerde que un espacio de trabajo que enlaza al agente virtual está disponible para que lo utilice cualquier prestación asociada con ese agente, ya sea una prestación personalizada o una prestación básica.

### Acerca de esta tarea

Cuando desenlaza un espacio de trabajo de una prestación, la prestación automáticamente se desactiva. La inhabilitación de la prestación garantiza que los usuarios activos no se exponen a un comportamiento inesperado mientras se realizan los cambios. Este método es aplicable a todas las prestaciones excepto **Ninguna de las anteriores**, que no se puede inhabilitar. Para desenlazar un espacio de trabajo asociado con ella, primero debe cambiar el tipo de respuesta de **Utilizar su propia conversación** a una de las otras opciones de tipo de respuesta para esta prestación.

### Procedimiento

1. En el menú de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, seleccione **Espacios de trabajo enlazados**.
1. Pulse para abrir el espacio de trabajo que desea desasociar del agente.
1. Pulse **Desenlazar espacio de trabajo**.

[Enlace de espacios de trabajo](/docs/services/virtual-agent/link_workspace.html)

