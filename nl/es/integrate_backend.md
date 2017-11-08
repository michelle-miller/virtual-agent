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

# Añadir el agente a un canal de soporte existente 
{: #integrate_backend}

La API de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} se ha diseñado para dar soporte a una transición fácil de una conversación entre el agente virtual y un humano u otro servicio bot en una infraestructura de soporte existente. De hecho, el equipo de LivePerson, Inc. se ha asociado con {{site.data.keyword.IBM}} simplemente para implementar dicha integración. Para obtener más información consulte el tema [Integración de LiveEngage](integrate_backend.html#liveperson) más adelante.
{: shortdesc}

Para crear una solución sencilla por su cuenta, puede codificar su aplicación de modo que cualquier prestación configurada para ser transferida a un agente humano se pase a un canal existente supervisado por el personal de soporte. Consulte la sección [Respuestas dW![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/318623/where-can-i-find-documentation-examples-on-integra/ "Icono de enlace externo"){: new_window} para obtener información acerca de cómo transferir una conversación a Slack, por ejemplo. 

Para utilizar la API de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para integrar el agente virtual con un canal de soporte existente, siga estos pasos: 

1.  Recupere las claves de la API necesarias para realizar llamadas a la API. Consulte la sección [Obtención de las claves de API](publish.html#api-keys) para obtener más detalles. 

1.  Utilice las API REST de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para interactuar con el bot de forma programada. Vaya al portal de **[{{site.data.keyword.IBM_notm}} developerWorks API Explorer](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}** para acceder a las API REST en {{site.data.keyword.Bluemix_notm}}.

1.  Para obtener el ID de bot, realice una de las acciones siguientes: 
    - Para obtener el ID de bot desde la interfaz de usuario de la herramienta de configuración de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, realice los pasos siguientes: 
      1.  En el menú principal ![Icono con tres barras horizontales](images/hamburger.png) de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, pulse **Documentation (Documentación)** y luego pulse la pestaña **Publish (Publicar)**. 
      1.  Copie el valor de botID en el bloque de script. 

    - Para obtener el ID de bot del sitio web de API Explorer, siga estos pasos: 
      1.  Inicie sesión en [IBM developerWorks API Explorer ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/api/ "Icono de enlace externo"){: new_window}. Pulse **My APIs (Mis API)** y pulse la ficha {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}. 
      1.  Pulse **Documentation>Retrieve Bot (Documentación>Recuperar bot)** en la barra de navegación. 
      1.  Pulse **USE (USAR)** en la parte superior de la ventana de referencia de API Explorer. 
      1.  Desplácese debajo de la sección *Path and Query parameters (Parámetros de vía de acceso y consulta)* y pulse **TEST (PROBAR)**.
      >**Nota:** Debe seleccionar una clave para utilizarla con la API antes de realizar la prueba. 

      1.  Se muestra el ID de bot en el parámetro `bot_id` de la respuesta resultante. 

## Integración de LiveEngage
{: #liveperson}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} se ha diseñado de modo que funcione armónicamente con sus homólogos humanos. 

Por ejemplo, LivePerson, Inc., un proveedor de soluciones de mensajería móvil de nube y de mensajería empresarial en línea, se ha asociado con IBM para incorporar un bot de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} en su experiencia de conversación de LiveEngage. **LiveEngage** es una plataforma de clase empresarial, basada en la nube, que permite a los consumidores enviar mensajes directamente a sus marcas favoritas. La nueva oferta, **LiveEngage with Watson (LiveEngage con Watson)**, añade respuestas desde un bot de {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para la interacción, con representantes de atención humanos que atienden de forma transparente en tiempo real, solo si es necesario. 

El bot de LivePerson aprovecha muchos de los siguientes comportamientos que ofrece {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}:

- Aceptar conversaciones cuyo origen es el servicio externo. 
- Activar la transferencia de las conversaciones al servicio externo bajo las condiciones siguientes: 
    - El cliente solicita hablar con un agente humano. 
    - Se configura una prestación para dirigirlo a un agente humano. 
    - El cliente pregunta acerca de un tema que el bot no está diseñado para reconocer y cubrir. 
- Identificar y notificar el punto de la conversación en que el usuario deja de comprender al bot o pierde interés en la conversación. 
- Reconocer cuándo finaliza la conversación y notificarlo al servicio para que se inicie cualquier actividad posterior a la interacción. 
- Durante la transferencia de una conversación, incluir información acerca de la intención del usuario, de modo que se pueda direccionar la conversación al agente humano más apto para tratar las solicitudes de este tipo. 
- Durante la transferencia de una conversación incluir el historial de conversación, de modo que la persona que se haga cargo del problema comprenda el contexto de la conversación realizada hasta ese momento. 

Para solicitar acceso a la oferta, consulte el sitio web de [LivePerson![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://engage.liveperson.com/usage/watson/?utm_medium=website&utm_source=IBM&utm_campaign=Watson "Icono de enlace externo"){: new_window}.
