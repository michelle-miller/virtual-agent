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

# Publicar el agente para su uso en demos
{: #publish}

En menos de 10 minutos, puede publicar el agente en un sitio de prueba para compartirlo con sus compañero y evaluar si cumple con los requisitos de su organización.
{: shortdesc}

Para publicar el agente en un sitio de prueba, realice estos pasos:

1.  Determine el lugar de la página donde desea que se muestre la ventana de conversación. En el elemento `<div>` HTML que define el área de destino, añada un atributo de ID, si no hay ninguno definido. Posteriormente, utilizará el atributo de ID para hacer referencia al elemento. Por ejemplo, `<div id="ibm-chat-root"></div>`.

1.  Siga las instrucciones de la sección [Obtener claves de API](publish.html#api-keys) para recuperar las siguientes claves:
    - ID de cliente
    - Señal de secreto de cliente

1.  En el menú principal ![Icono con tres barras horizontales](images/hamburger.png), pulse **Documentation (Documentación)** y luego baje a la sección **Publish (Publicar)**.

1.  Si tiene varios agentes, pulse la flecha hacia abajo para obtener el ID de bot del agente que desea publicar.

    Este ID de bot es el ID generado por el servicio y asignado a su bot.

    Se genera un bloque de scripts y se muestra en la página. Este script se pude copiar y colocar en una página HTML para representar el agente en la página. Debe sustituir algunos de los valores en el script por los valores adecuados para su instancia. 

1.  Copie el bloque de scripts y péguelo en un editor de texto o HTML.

    ``` Javascript
    <script src='https://unpkg.com/@watson-virtual-agent/chat-widget@1.6.0/dist/chat.min.js'>
    </script>
    <script>
      IBMChat.init({
        el: 'ibm_chat_root',
        baseURL: 'https://api.ibm.com/virtualagent/run/api/v1',
        botID: 'YOUR_BOT_ID',
        XIBMClientID: 'YOUR_IBM_CLIENT_ID',
        XIBMClientSecret: 'YOUR_IBM_CLIENT_SECRET'
      });
    </script>
    ```

1.  Sustituya los siguientes valores de atributo:
    - **el**: Especifique el ID del elemento que ha decidido utilizar en el Paso 1.
    - **XIBMClientID (IDClienteXIBM)**: Añada el valor de ID de cliente que ha copiado antes.
    - **XIBMClientSecret (SecretoClienteXIBM)**: Añada el valor de señal de secreto de cliente que ha copiado antes.

   Utilice los valores baseURL y botID especificados en el script. Estos valores los genera el servicio.

   **Importante:** Guarde los valores de XIBMClientID y XIBMClientSecret del modo más privado posible.

1.  Incorpore e inicialice el widget de conversación de Watson Virtual Agent pegando el script revisado en su página web.

   Añada el script lo más cerca posible de la etiqueta de cierre `</body>` para impedir que el script bloquee la visualización del resto de la página. Esta ubicación también garantiza que independiente del elemento que ha asociado al script, se mostrará completamente cuando se ejecute el script.

1.  Renueve la página web y pruebe el agente

   El widget de conversación está asociado y se visualiza en el elemento HTML que ha designado en el Paso 1. Puede ocultar o mostrar y posicionar dicho elemento. El widget se amplía a la anchura y altura completas del elemento. La anchura máxima es de 768 píxeles y la altura mínima es de 300 píxeles.

Cuando esté listo para que funcione el agente ayudando directamente a sus clientes, debe realizar algunos pasos adicionales. Consulte la sección [Integración del agente](integrate.html) para obtener más detalles.

## Obtención de las claves de API
{: #api-keys}

Para demostrar que tiene permiso para utilizar los servicios de la API de Watson Virtual Agent, las siguientes claves deben estar asociadas a cualquier llamada de API realizada al servicio:

- ID de cliente
- Señal de secreto de cliente

Siga estos pasos para recuperar las credenciales.

1.  Vaya al sitio web [IBM developerWorks API Explorer ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/api/ "Icono de enlace externo"){: new_window} e inicie sesión con el mismo ID de IBM que ha utilizado para iniciar sesión para la suscripción del servicio. Cree un nombre de usuario si es necesario. Pulse el enlace **My APIs (Mis API)** en la cabecera de página.

1.  Busque la ficha {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} y, a continuación, pulse el icono de clave asociado al mismo.

1.  Si está seleccionada, seleccione la clave que desea utilizar. Se generarán dos credenciales para la clave que se muestran con los valores difuminados en los dos campos. Pase el ratón por los campos.

1.  Pulse el botón **SHOW (MOSTRAR)** para eliminar el difuminado de los valores de los campos.

1.  Deberá proporcionar estos valores posteriormente, por lo tanto, cópielos en un archivo de texto.
    - El primer campo contiene la clave del ID de cliente.
    - El segundo campo contiene la señal del secreto de cliente.

  ![Añadir nodo](images/api-explorer.jpg)
