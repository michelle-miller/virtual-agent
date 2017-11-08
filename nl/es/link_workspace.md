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

# Enlace a los espacios de trabajo 
{: #link_workspace}

Para utilizar una prestación personalizada o un diálogo personalizado con una prestación básica, primero debe establecer una conexión entre el agente virtual y el espacio de trabajo del servicio {{site.data.keyword.conversationshort}} que contiene los artefactos que desea utilizar.
{: shortdesc}

## Acerca del espacio de trabajo

Un espacio de trabajo es un contenedor de servicio de {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} que contiene intenciones, entidades y un diálogo, que son artefactos que se utilizan para definir y entrenar un flujo de conversación. El agente puede utilizar artefactos del espacio de trabajo, que incluye intenciones entrenadas y un diálogo, cuando interactúa con los clientes para personalizar y ampliar el ámbito de los temas que puede tratar.

Puede enlazar espacios de trabajo para conseguir los objetivos siguientes:

- Definir sus propias prestaciones: el espacio de trabajo debe incluir intenciones, expresiones de ejemplo y un diálogo con condiciones de nodo que coincidan con cada intención definida.
- Definir un diálogo personalizado con una prestación básica: el espacio de trabajo debe incluir un diálogo con una condición de nodo que coincida con el nombre de la intención para una prestación básica.

*Puede* utilizar el mismo espacio de trabajo para añadir prestaciones personalizadas y diálogos personalizados a las prestaciones básicas. No obstante, es más sencillo gestionar estas cosas si crea un único espacio de trabajo dedicado para definir las prestaciones personalizadas que desea utilizar y uno o varios espacios de trabajo separados para definir los diálogos que desea utilizar como respuestas de las prestaciones básicas. Si opta por utilizar el mismo espacio de trabajo para ambas cosas, asegúrese de que cualquier nodo que contenga los diálogos personalizados se haya añadido a las prestaciones básicas específicas en la parte superior del árbol de diálogo en la parte superior del árbol de diálogos, para evitar así que se direccionen incorrectamente las expresiones a las prestaciones personalizadas. 

### Procedimiento

1.  Abra la página **Linked Workspaces (Espacios de trabajo enlazados)** para el agente actual. 
1.  Pulse **Link Workspace (Enlazar espacio de trabajo)**.

    Proporcione las credenciales de su cuenta de {{site.data.keyword.Bluemix_notm}} para dar a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} permiso para acceder a la instancia de servicio de {{site.data.keyword.conversationshort}} y obtener la información del espacio de trabajo.

1.  Seleccione la instancia del servicio {{site.data.keyword.conversationshort}} que contenga los espacios de trabajo que desee utilizar.
1.  Seleccione uno o más espacios de trabajo que desee enlazar al agente.
1.  Pulse **Link workspaces (Enlazar espacios de trabajo)**.

[Creación de un diálogo personalizado ](add-custom-dialog.html)

[Adición de sus propias prestaciones](add-custom-capabilities.html)

## Desenlace de espacios de trabajo 
{: #unlink_workspace}

Si decide que no desea mantener una conexión entre el agente virtual y un espacio de trabajo específico de {{site.data.keyword.conversationshort}}, puede desenlazar el espacio de trabajo.

### Antes de empezar

Asegúrese de que el espacio de trabajo que desea desenlazar no esté siendo activamente utilizado por una prestación que lo requiera. Recuerde que un espacio de trabajo que enlaza al agente virtual está disponible para que lo utilice cualquier prestación asociada con ese agente, ya sea una prestación personalizada o una prestación básica.

### Acerca de esta tarea

Cuando desenlaza un espacio de trabajo de una prestación, la prestación automáticamente se desactiva. La inhabilitación de la prestación garantiza que los usuarios activos no se exponen a un comportamiento inesperado mientras se realizan los cambios. Este método es aplicable a todas las prestaciones excepto **None of the above (Ninguna de las anteriores)**, que no se puede inhabilitar. Para desenlazar un espacio de trabajo asociado con ella, primero debe cambiar el tipo de respuesta de **Use your own conversation** a una de las otras opciones de tipo de respuesta para esta prestación.

### Procedimiento

1.  Abra la página **Linked Workspaces (Espacios de trabajo enlazados)** para el agente actual. 
1.  Pulse para abrir el espacio de trabajo que desea desasociar del agente.
1.  Pulse **Unlink this Workspace (Desenlazar este espacio de trabajo)** ![icono de papelera que representa la relación de supresión de enlace](images/trash.png) .

[Enlace de espacios de trabajo](link_workspace.html)
