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

# Personalización del agente
{: #integrate}

Para publicar el agente para uso de producción, debe realizar pasos adicionales para dar soporte a las funciones realizadas por el agente y ponerlo a disposición de los usuarios de forma segura.
{: shortdesc}

## Elija un método de integración

Puede integrar el agente de uno de los modos siguientes:

- Añadir la interfaz de conversación proporcionada por {{site.data.keyword.IBM_notm}} tal cual en el sitio web para los clientes. Consulte [Adición del widget de conversación proporcionado a la interfaz de usuario](integrate_add-chat.html).

- Ampliar la ventana de conversación proporcionada para personalizarla según sus necesidades.
Consulte [Adición del widget de conversación proporcionado a la interfaz de usuario](integrate_add-chat.html).

- Crear su propia interfaz de conversación utilizando el SDK de cliente proporcionado.
  Consulte [Creación de una interfaz de conversación personalizada](integrate_custom-chat.html).

- Añadir el agente a un canal de soporte existente y utilizar la API para interactuar con el agente mediante programación.
  Consulte [Adición del agente a un canal de soporte](integrate_backend.html).

### Antes de empezar

Independientemente del método que use para publicar el agente para uso de producción, considere hacer un clon del agente previamente. Tener una copia no integrada del agente le permite probar cambios o adiciones a la funcionalidad en la copia de prueba antes de realizarlos en el agente que se utiliza en un entorno de producción. Consulte la sección [Clonación del agente](agent-create.html#clone) para obtener más información.
