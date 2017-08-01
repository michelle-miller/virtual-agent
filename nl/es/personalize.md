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

# Personalización del agente
{: #personalize}

Asegúrese de que el agente virtual responde a las cuestiones que importan a los clientes, y que sus respuestas transmiten con exactitud la información sobre los servicios que ofrece la empresa o ayudan a los clientes a completar transacciones empresariales.
{: shortdesc}

## Acerca de esta tarea

Puede personalizar el agente realizando las acciones siguientes:

[Adición de diálogos personalizados para las prestaciones básicas](/docs/services/virtual-agent/personalize.html#use_custom)

[Adición de sus propias prestaciones](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Adición de diálogos personalizados para las prestaciones básicas
{: #use_custom}

En cualquier prestación básica, puede optar por utilizar su propia conversación para interactuar con el usuario a fin de satisfacer el objetivo del usuario.

### Creación de un diálogo personalizado
{: #custom_dialog}

Si una prestación principal que habilita requiere el manejo por parte de un diálogo personalizado, puede utilizar el servicio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} para crear el diálogo y a continuación enlazarlo al agente virtual.

#### Acerca de esta tarea

El servicio {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} es un conjunto de herramientas y APIs que puede utilizar para crear aplicaciones que utilizan interfaces de lenguaje natural para automatizar las interacciones con los clientes. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} utiliza el servicio {{site.data.keyword.conversationshort}} para definir las prestaciones entrenadas y el flujo de diálogo que utiliza el bot. Si el diálogo proporcionado no permite la flexibilidad que necesita, puede crear su propio diálogo utilizando las herramientas de servicio de {{site.data.keyword.conversationshort}}.

Por razones de compatibilidad con el agente virtual, cualquier diálogo que cree debe cumplir las directrices de diseño de [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}. Estas directrices especifican cómo interactúa el diálogo con la interfaz de conversación del agente virtual, incluido cómo se visualizan los indicadores de solicitud a los usuarios y dónde se almacenará la información que proporcionen los usuarios de forma que sea accesible desde la interfaz de la ventana de conversación.

El repositorio de {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} también proporciona ejemplos que muestran cómo funcionan las interacciones del diálogo. Puede utilizar el ejemplo como modelo para su propio diálogo. Consulte el [archivo JSON de flujos de diálogo de ejemplo ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/sample_dialog_flows.json){: new_window}.

#### Procedimiento

Para crear un diálogo personalizado:

1. Si no lo ha hecho ya, regístrese en el servicio {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Para obtener más información, consulte la documentación [Servicio {{site.data.keyword.conversationshort}}: Cómo empezar ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.
1. Cree un espacio de trabajo para contener el diálogo.

    Para obtener información sobre los espacios de trabajo, consulte la documentación [Servicio {{site.data.keyword.conversationshort}}: Creación de un espacio de trabajo  ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/create-workspace.html){: new_window}.

1. Vaya directamente a la pestaña **{{site.data.keyword.dialogshort}}**. (No cree intenciones o entidades.)
1. Cree un nodo de diálogo para cada prestación que desee personalizar.

    Un nodo de diálogo debe tener una condición que se evalúe en el nombre de intención para la prestación que lo utilizará.

    Utilice la sintaxis siguiente:

    ```
    $wva.intents.get(0).intent.equals('nombre-intención')
    ```
    {: screen}

    Por ejemplo, para la prestación **Contáctenos**, el *nombre-intención* es `Information-Contact_Us`. El diálogo probaría `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Si tiene un bot más antiguo y las preferencias están establecidas para revertir a pasar la intención sólo al espacio de trabajo, utilizará en su lugar la sintaxis siguiente:

    ```
    #nombre-intención
    ```
    {: screen}

    Por ejemplo, `#Information-Contact_Us`

    Para descubrir el nombre de intención asociado con una prestación, consulte [Nombres de intención](/docs/services/virtual-agent/intent_codenames.html).

1. Añada nodos según se requiera para crear el flujo de diálogo necesario.

    Para que sea compatible con {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, el diálogo debe cumplir determinadas directrices de diseño cuando almacene la información recopilada o utilice sucesos para la comunicación con la interfaz del widget de conversación. Cree un diálogo que cumpla las directrices de diseño de diálogos de {{site.data.keyword.virtualagentshort}} de [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}.

1. Enlace al agente los espacios de trabajo con diálogos que haya creado.

    Consulte [Enlace de espacios de trabajo](/docs/services/virtual-agent/link_workspace.html) para obtener más detalles.

1. En el separador **Prestaciones básicas** de la página Configurar, cambie el tipo de respuesta de cada prestación para la que desee utilizar un diálogo personalizado al tipo de respuesta **Utilizar su propia conversación**.
1. Seleccione el espacio de trabajo que contiene el diálogo que desee utilizar en la lista de espacios de trabajo enlazados y a continuación pulse **Guardar** para acabar de establecer el enlace.

    Un espacio de trabajo que ya se utilice para añadir prestaciones personalizadas no se visualizará como opción. No puede utilizar el mismo espacio de trabajo para añadir prestaciones personalizadas que el que utiliza para añadir un diálogo a una prestación básica. 

    Si no ha enlazado aún el espacio de trabajo, puede pulsar aquí **Enlazar un espacio de trabajo** para enlazar al agente el espacio de trabajo que ha creado anteriormente.

## Adición de sus propias prestaciones
{: #add_custom_capabilities}

Para ampliar lo que el agente virtual puede tratar con los clientes, añada sus propias prestaciones.

### Antes de empezar

Cuando utiliza un espacio de trabajo para proporcionar un diálogo personalizado para una prestación básica, sólo necesita proporcionar un diálogo en el espacio de trabajo. El agente ya se ha entrenado para reconocer las expresiones que se correlacionan con las prestaciones básicas, así que no es necesario proporcionar intenciones, entidades ni datos de entrenamiento. Cuando proporciona un espacio de trabajo que define sus propias prestaciones, además del diálogo debe proporcionar intenciones y entidades. También debe proporcionar un número considerable de expresiones de ejemplo que el servicio pueda utilizar para entrenar las intenciones a las que desea dar soporte. Utilice la documentación, las demos y las herramientas que se proporcionan con el servicio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} para crear un espacio de trabajo con prestaciones personalizadas. Consulte la [documentación de {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/index.html){: new_window} para obtener más información.

### Acerca de esta tarea

Sólo puede crear un único espacio de trabajo para definir prestaciones personalizadas. Cada intención que añada al espacio de trabajo pasará a estar disponible como una prestación personalizada cuando el enlace el espacio de trabajo al agente. El espacio de trabajo debe contener todas las prestaciones que desee añadir al agente. No añada intenciones al espacio de trabajo que no desee que pueda manejar el agente.

### Procedimiento

1. En la instancia del servicio {{site.data.keyword.conversationshort}}, cree un espacio de trabajo que defina las prestaciones personalizadas. Consulte la [documentación del servicio {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

    Siga estas directrices:
    - Añada una rama para cada prestación a la que desee dar soporte como nodo base (a lo que se hace referencia como *conversación alternativa* en la interfaz de usuario de la herramienta {{site.data.keyword.conversationshort}}) en el diálogo. Por ejemplo, no defina un nodo base en el diálogo que reconozca y responda a mensajes de bienvenida de los usuarios y a continuación añada nodos hijo que coincidan con otros intenciones de prestación personalizada debajo de él.
    - Evite manejar discrepancias de entrada de usuario con bucles recursivos. Cree sólo giros de diálogo que tengan un final definitivo.
    - No cree una intención personalizada con el mismo nombre que una intención utilizada por una prestación básica. Consulte [Nombres de intención](/docs/services/virtual-agent/intent_codenames.html) para ver una lista de los nombres que se deben evitar.

1. Enlace el espacio de trabajo al agente. Consulte [Enlace de espacios de trabajo](/docs/services/virtual-agent/link_workspace.html)
1. En la página **Configurar**, abra el separador **Prestaciones personalizadas**.
1. Pulse **Añadir prestaciones**.
1. Seleccione el espacio de trabajo que ha enlazado al agente en el Paso 2 y a continuación pulse **Seleccionar espacio de trabajo**.

    Las intenciones definidas en el espacio de trabajo enlazado ahora se listan como prestaciones habilitadas.

    > **Nota:** no puede inhabilitar prestaciones individuales. Si desea eliminar una prestación personalizada, puede suprimir la intención del espacio de trabajo en la herramienta del servicio {{site.data.keyword.conversationshort}}.
    Puede eliminar todas las prestaciones a la vez pulsando **Eliminar prestaciones privadas**. La eliminación de las prestaciones no suprime la asociación entre el agente y el espacio de trabajo en el que están definidas las prestaciones.

### Resultados

Después de añadir prestaciones personalizadas, cada expresión de usuario que evalúa {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} se pasa al espacio de trabajo básico y al espacio de trabajo de prestaciones personalizadas para su evaluación. Se desencaderá la prestación que coincida mejor con la intención de la entrada del usuario y se utilizará el diálogo asociado con ella.

![Muestra que un usuario pasa una expresión a Watson Virtual Agent. Este la pasa al espacio de trabajo incorporado y al espacio de trabajo de prestaciones enlazadas para su evaluación. El espacio de trabajo incorporado tiene una confianza de 0,85 en comparación con la confianza del espacio de trabajo de prestaciones enlazadas de 0,55. El espacio de trabajo incorporado pasa una respuesta a Watson Virtual Agent para pasarla al usuario.](images/workspace-confidences.png)

### Prueba de prestaciones personalizadas
{: #test_custom_capabilities}

Después de añadir sus propias prestaciones, realice algunas pruebas para asegurarse de que se comportan de la forma esperada.

#### Acerca de esta tarea

Cuando añade sus propias prestaciones, puede definir fácilmente una que sea similar en comportamiento a una prestación básica existente. Si es así, asegúrese de que ambas no compitan entre ellas para responder a determinadas consultas de usuario.

#### Procedimiento

1. Utilice el panel Vista previa para formular preguntas o realizar los tipos de solicitudes que espera que hagan los clientes.

    Debajo de la respuesta se muestra la prestación que se ha desencadenado para abordar la solicitud. Si la prestación que se muestra no es la que espera, puede realizar cambios para corregir cómo se direccionan las expresiones a las prestaciones.

1. Compare las prestaciones definidas en la aplicación básica con las prestaciones definidas en el espacio de trabajo personalizado.

    - Para revisar las prestaciones proporcionadas con la aplicación, consulte [Prestaciones básicas](/docs/services/virtual-agent/intent_list.html) para ver una descripción de cada prestación básica.
    - Para revisar las intenciones definidas en el espacio de trabajo de {{site.data.keyword.conversationshort}}, abra el espacio de trabajo en la herramienta {{site.data.keyword.conversationshort}} y a continuación abra la página **Intenciones**. Expanda cada intención para ver los tipos de expresiones que está entrenado para responder.

1. Utilice el panel Vista Previa para probar expresiones que sospecha que podrían causar un conflicto.

    En función de las respuestas, compruebe si las prestaciones que se solapan manejan consultas de usuario lo suficientemente distintas entre ellas para que puedan coexistir sin que causen una experiencia incoherente al usuario. Si las dos prestaciones compiten por los mismos tipos de expresiones, una de ellas se deberá inhabilitar. Puede tratar las prestaciones que se solapan de las formas siguientes:
    - **Inhabilitar la prestación personalizada**

        1. En la herramienta {{site.data.keyword.conversationshort}}, busque la intención en la página **Intenciones**, expándala y a continuación pulse el icono **Suprimir intención** para suprimirla del espacio de trabajo.
        1. Cuando se han realizado cambios en el espacio de trabajo, este se vuelve a entrenar automáticamente. Cuando se haya completado el entrenamiento, vuelva a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.
        1. En la página Configurar, abra el separador **Prestaciones personalizadas** para confirmar que la prestación ya no aparece en la lista.

    - **Inhabilite la prestación básica**

        1. En el separador **Prestaciones básicas** de la página Configurar de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, busque la prestación que desee inhabilitar.
        1. Pulse la ficha para abrir la prestación y a continuación pase el conmutador de encendido a apagado.

    - **Edite los datos de entrenamiento para la prestación personalizada**

        Si la prestación personalizada trata un objetivo de cliente similar pero con un alcance más amplio, puede eliminar las expresiones de ejemplo de los datos de entrenamiento para la prestación personalizada para excluir ejemplos que se solapen con los tipos de expresiones que abarca la prestación básica. No puede acceder al espacio de trabajo para la prestación básica; sólo puede editar el espacio de trabajo para la prestación personalizada para realizar cambios. Para determinar qué expresiones se direccionan a la prestación básica, utilice el panel Vista previa para probar varias expresiones y ver cuáles desencadenan la prestación básica.

        > **Atención:** si opta por este enfoque, prepárese para realizar muchas pruebas y revisión. Es difícil predecir cómo el aprendizaje por máquina reaccionará a los cambios de los datos de entrenamiento. Deberá realizar muchas pruebas para confirmar que los cambios tienen el impacto deseado.
        Edite el espacio de trabajo para la prestación personalizada siguiendo estos pasos:
        1. En la herramienta {{site.data.keyword.conversationshort}}, busque la intención de la página **Intenciones** y a continuación expanda la intención para ver la lista de expresiones de ejemplo.
        1. Seleccione el recuadro junto a las expresiones que se solapan con expresiones que gestionan las prestaciones básicas y a continuación pulse **Eliminar ejemplos**.
        1. Cuando se han realizado cambios en el espacio de trabajo, este se vuelve a entrenar automáticamente. 

    - **Mantener ambas prestaciones**

        En algunos casos, aunque las prestaciones son similares, abordan casos de uso lo suficientemente distintos, de forma que puede mantener ambos habilitadas.

1. Especifique de nuevo las expresiones de prueba en el panel Vista previa para confirmar que los cambios dan como resultado el comportamiento esperado. Si no es así, realice cambios adicionales.

## Cómo se utiliza Ninguna de las anteriores
{: #none_of_the_above}

Comprenda cómo el agente virtual utiliza la prestación **Ninguna de las anteriores**.

A diferencia de todas las otras prestaciones básicas, la prestación **Ninguna de las anteriores** no se puede inhabilitar. La razón por la que no se puede inhabilitar es que se utiliza como una prestación general para todas las expresiones que no se correlacionan con ninguna de las prestaciones configuradas. Esta funcionalidad resulta útil porque puede proporcionar una respuesta estándar, por ejemplo, *No puedo ayudarle con eso*, para solicitudes de usuarios para prestaciones que el agente aún no tiene. También responde a preguntas que no tienen sentido que a veces los clientes realizan para divertirse cuando empiezan a interactuar con el agente, por ejemplo, *¿Qué debo tomar para almorzar?*

Debido a su rol exclusivo en el funcionamiento del agente virtual, es importante la configuración de su comportamiento. La prestación **Ninguna de las anteriores** se desencadena a menudo y de maneras que no resultan siempre obvias, y que incluyen:

- Cuando inhabilita cualquier otra prestación básica, las expresiones que desencadenan la prestación inhabilitada se redireccionan a la prestación **Ninguna de las anteriores** para obtener una respuesta.
- Cuando una expresión no coincide con ninguna de las prestaciones básicas habilitadas, se pasa a la prestación **Ninguna de las anteriores** para obtener una respuesta. Si proporciona un espacio de trabajo enlazado con prestaciones personalizadas, tanto el espacio de trabajo básico como el espacio de trabajo personalizado evalúan la expresión para buscar una coincidencia. Si no se encuentra ninguna coincidencia, se utiliza la respuesta asociada con la prestación principal **Ninguna de las anteriores**.
- Puede configurar la capacidad **Ninguna de las anteriores** para tener un tipo de respuesta **Utilizar su propia conversación** y enlazarlo a un espacio de trabajo con un diálogo personalizado. Cuando no se encuentre ninguna coincidencia de intención para una expresión en el espacio de trabajo básico, la expresión se pasará a la prestación **Ninguna de las anteriores**, que la pasará al espacio de trabajo personalizado para obtener una respuesta.
- Cuando desenlaza un espacio de trabajo, si el espacio de trabajo enlazado está asociado con la prestación **Ninguna de las anteriores**, debe realizar alguna acción antes de poder continuar para desenlazar el espacio de trabajo. Cualquier otra prestación asociada con el espacio de trabajo que desee desenlazar se inhabilitará automáticamente. Sin embargo, puesto que **Ninguna de las anteriores** no se puede inhabilitar, debe decidir sobre un comportamiento de respuesta alternativo. Por ejemplo, puede cambiar el tipo de respuesta a **Visualizar una respuesta de texto** y añadir un mensaje de texto para utilizar en la respuesta.

