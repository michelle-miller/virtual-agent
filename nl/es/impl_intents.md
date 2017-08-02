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

# Implementación de las prestaciones básicas
{: #impl_intents}

Comprenda las tareas de desarrollo que debe realizar para dar soporte a los tipos de respuesta seleccionados para determinadas prestaciones.
{: shortdesc}

Considere cómo desea utilizar las prestaciones siguientes, como mínimo:

- ***Ninguna de las anteriores***

    La respuesta que define para esta prestación se devuelve a los usuarios siempre que estos especifican una entrada que el sistema no puede reconocer y correlacionar con una prestación habilitada. Como resultado, se puede mostrar mucho a los usuarios, especialmente si no activa muchas prestaciones. Piense cómo desea que responda el agente virtual. Una respuesta de texto, como *Lo siento. No comprendo lo que pregunta.* es suficiente. Si desea que los usuarios tengan la opción de ponerse en contacto con un agente humano, puede incluir el texto, *Especifique 'agente' para ser transferido a un agente humano.* Esta entrada desencadena el suceso `agente`, que se explica a continuación. Consulte [Cómo se utiliza Ninguna de las anteriores](/docs/services/virtual-agent/personalize.html#none_of_the_above) para obtener más información.

- **Intención *Conectar con agente* y prestaciones con el tipo de respuesta *Transferir a agente humano***

    Estas prestaciones transfieren al usuario a un agente humano. Debe añadir lógica que transfiera la conversación al personal de soporte. Un método que puede realizar es añadir lógica que conecte a un servicio externo que ya se utilice para gestionar solicitudes entrantes en el sitio de soporte al cliente. Los temas que el agente virtual no pueda tratar se transferirán al personal de soporte como parte de su cola existente de solicitudes de soporte para ser priorizados y tratados. Para implementar la lógica de transferencia, esté a la escucha del suceso `agente` y defina las funciones que se realizarán cuando se desencadene el suceso. Consulte [dwAnswers ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/search.html?f=&amp;type=question&amp;redirect=search/search&amp;q=watson-virtual-agent&amp;q=human){: new_window} para obtener ideas.

- **Prestaciones con el tipo de respuesta *Utilizar conversación incorporada***

    Si mantiene los valores predeterminados para las prestaciones básicas configuradas para utilizar el tipo de respuesta de conversación incorporada, y estas prestaciones están habilitadas, debe añadir lógica para dar soporte al intercambio de información y a las transacciones empresariales que manejan las conversaciones incorporadas. Consulte [Implementación de lógica para dar soporte a conversación incorporada](/docs/services/virtual-agent/impl_intents.html#backend_transaction) para obtener más detalles.

- **Prestaciones con el tipo de respuesta *Utilizar su propia conversación***

    En el caso de prestaciones complejas que requieren un diálogo personalizado para manejar el intercambio de información con el usuario, puede escribir un diálogo mediante el servicio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Consulte [Adición de diálogos personalizados para las prestaciones básicas](/docs/services/virtual-agent/personalize.html#use_custom) para obtener más detalles.

## Implementación de lógica para dar soporte a la conversación incorporada
{: #backend_transaction}

Obtenga información sobre cómo intercambiar información y completar procesos empresariales que se pueden producir cuando los usuarios interactúan con prestaciones configuradas para utilizar conversación incorporada.

### Acerca de esta tarea

Algunas de las prestaciones básicas configuradas para utilizar el tipo de respuesta de conversación incorporada de forma predeterminada pueden tramitar procesos empresariales. La aplicación debe poder registrar la transacción con los sistemas backend de registros.

- Si implementa el widget de conversación de {{site.data.keyword.IBM_notm}} proporcionado, este reconoce sucesos que desencadenan determinadas respuestas de usuario. Sin embargo, debe realizar pasos adicionales para estar a la escucha de estos sucesos en la aplicación, de forma que pueda completar las transacciones iniciadas en los sistemas backend.
- Si no utiliza el widget de conversación proporcionado, debe asegurarse de que la interfaz de usuario personalizada puede reconocer los sucesos que desencadenan los flujos de conversación incorporada y que los maneja de la forma adecuada.

Por ejemplo, con la prestación **Actualizar dirección**, un usuario puede cambiar la dirección de facturación de su cuenta. Debe escribir código que obtenga la nueva dirección del agente virtual y actualice la cuenta del usuario en el sistema de registros con la nueva información.

Es importante que tenga en cuenta que la finalidad de un diálogo sólo es recopilar información del usuario. La información proporcionada por el usuario se almacena de una de las dos maneras siguientes:

- La información que no es confidencial o privada se almacena en el contexto del diálogo, que es un objeto de datos disponible para el bot y para la aplicación.
- La información confidencial o privada (por ejemplo, números de tarjeta de crédito) se almacena en variables privadas, que están disponibles solo para la aplicación y no se pasan al bot.

### Procedimiento

Para implementar completamente transacciones empresariales desencadenadas desde prestaciones con respuestas de conversación incorporada, realice los pasos siguientes:

1. Añada lógica a la aplicación que obtenga información de perfil del usuario actual desde el sistema backend para mostrar en la ventana de conversación antes de que se modifique la información. Por ejemplo, mostrar a los usuarios un saldo de cuenta antes de que lo paguen.

    Utilice la acción `getUserProfileVariables`. Esta acción obtiene las variables y las establece en el perfil.

    ```
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     var variables = data.message.action.args.variables; // especifique las variables que desee obtener en esta matriz
       for (var i = 0; i < variables.length; i++) {
           var value = something(variables[i]) 
           /*acción para obtener el valor de variables[i]. Podría ser una llamada ajax u obtener
           datos de cookies locales. Depende de dónde ha almacenado la información.*/
           window.IBMChat.profile.set(variables[i], value);
       }
       IBMChat.sendSilently('éxito'); // o cancelar o error
    });
    ```
    {: screen}

    Este ejemplo utiliza una llamada REST para obtener información sobre un saldo de factura y una fecha de vencimiento.

    ```
    var xmlHttp = new XMLHttpRequest();
      xmlHttp.onreadystatechange = function() { 
        if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
          callback(xmlHttp.responseText);
      }
      xmlHttp.open("GET", url, true);
      xmlHttp.send(null);
    }
    /* Obtenga información sobre la base de datos backend y añádala al
    perfil con IBMChat.profile.set(). */
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     /*
     data = {
       message: {
          text: ['algún texto'],
                action: {
                     name: 'getUserProfileVariables',
                     args: {
                         variables: [
                    "bill_amount",
                    "payment_due_date"
                ]
                     }
                }
       }
       
     }
     */
      
     httpGetAsync('http://sudominio.com/userprofile', function(user) {
       /* El registro en el sistema backend podría devolver información como esta.
       user = {
         "bill_amount": 42.01,
         "payment_due_date": "11/24/2008"
       }
       */
       var variables = data.message.action.args.variables;
       for (var i = 0; i < variables.length; i++) {
         var value = user[variables[i]]);
         window.IBMChat.profile.set(variables[i], value);
       /* Ahora el widget de conversación puede utilizar los valores que ha recuperado del servicio backend. */ }
       IBMChat.sendSilently('éxito'); // o cancelar o error
     });
    });
    ```
    {: screen}

1. Añada lógica a la aplicación que primero está a la escucha de la acción que inicia el proceso empresarial y a continuación realiza el proceso empresarial.

    Para ver una lista de las acciones asociadas con prestaciones que tienen tipos de respuesta de conversación incorporada, consulte [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action){: new_window}.

### Realizar un pago
{: #makeapayment}

Realice los pasos siguientes para implementar código que dé soporte a esta transacción.
1. La aplicación debe obtener el saldo actual del usuario y la fecha de vencimiento del sistema backend. Utilice el método `action:getUserProfileVariables` para obtener y establecer las variables `bill_amount` y `payment_due_date` en el almacén del perfil.
1. La aplicación debe estar a la escucha del suceso `payBill` y definir la lógica que se realizará cuando se desencadene el suceso.
1. La aplicación también debe estar a la escucha del suceso `sendPaymentReceipt` y definir la lógica que se realizará cuando se desencadene el suceso.

### Actualizar dirección
{: #updateaddress}

1. El widget de conversación utiliza un diseño de formulario para solicitar la información de nueva dirección del usuario y la almacena en el perfil automáticamente. Almacena estas variables de perfil:

    ```
    user_street_address1
    user_street_address2
    user_locality
    user_state_or_province
    user_zipcode
    ```
    {: screen}

1. La aplicación debe estar a la escucha del suceso `updateAddress`.

    ```
    IBMChat.subscribe('action:updateAddress', function(data) {<your-code>}
    ```
    {: screen}

    Defina una función que obtenga y envíe la nueva dirección y el tipo de dirección (`address_type`) al sistema backend cuando se desencadene la acción `updateAddress`.

    Para recopilar datos con muchos valores, por ejemplo, una dirección de calle, puede utilizar el diseño de formulario incorporado en el widget de conversación. Los usuarios especifican valores en varios campos y a continuación envían todo el formulario. Por ejemplo, para enviar la nueva dirección a su sitio mediante una llamada REST POST, puede utilizar lógica como la siguiente.

    ```
    /* Cuando un usuario especifica información en un formulario, este se añade automáticamente
    al perfil del usuario. Por lo tanto un flujo típico sería incluir un diseño de formulario
    en la ventana de conversación y a continuación llamar a esta acción después del envío del
    formulario */
    IBMChat.subscribe('action:updateAddress', function(data) {
      var record = {
        "first_name": IBMChat.profile.get('first_name'),
        "last_name": IBMChat.profile.get('last_name'),
        "user_street_address1": IBMChat.profile.get('user_street_address1'),
        "user_street_address2": IBMChat.profile.get('user_street_address2'),
        "user_locality": IBMChat.profile.get('user_locality'),
        "user_state_or_province": IBMChat.profile.get('user_state_or_province'),
        "user_zipcode": IBMChat.profile.get('user_zipcode')
      };
      httpPostAsync('/updateRecord/', record, function(err, response) {
       if (err) IBMChat.receive('Se ha producido un error al actualizar la dirección.');
      });
    });
    ```
    {: screen}

    Para obtener más información sobre los diseños incorporados, consulte [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout){: new_window}.

### Actualizar número de teléfono de contacto
{: #updatephone}

1. El widget de conversación utiliza un diseño de formulario para solicitar el nuevo número de teléfono del usuario y lo almacena en el perfil automáticamente. Almacena estas variables de perfil:

    ```
    user_phone_number
    phone_number_type
    ```
    {: screen}

1. La aplicación debe estar a la escucha del suceso `updatePhoneNumber` y definir la lógica para obtener y enviar el nuevo número de teléfono y tipo al sistema backend cuando se desencadene el suceso.

### Actualizar correo electrónico
{: #updateemail}

1. El widget de conversación utiliza un diseño de formulario para solicitar la nueva dirección de correo electrónico del usuario y la almacena en el perfil automáticamente. Almacena estas variables de perfil:

    ```
    user_email_address
    email_type
    ```
    {: screen}

1. La aplicación debe estar a la escucha del suceso `updateEmail` y definir la lógica para obtener y enviar la nueva dirección de correo electrónico al sistema backend cuando se desencadene el suceso. También envía información sobre qué tipos de notificación utilizan la nueva dirección para (`email_type`).
