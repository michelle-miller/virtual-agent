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

# Implementing core capabilities
{: #impl_intents}

Understand development tasks that must be completed to support the response types selected for certain capabilities.
{: shortdesc}

Consider how you want to handle the following capabilities, at a minimum:

- ***None of the above***

    The response that you define for this capability is returned to users whenever they enter input that the system cannot recognize and map to an enabled capability. As a result, it can be displayed to users a lot, especially if you do not turn on many capabilities. Think about how you want the virtual agent to respond. A text response, such as *I'm sorry. I don't understand what you are asking about.* is sufficient. If you want users to have the option of contacting a human agent, you can include the text, *Enter 'agent' to be transferred to a human agent.* This input triggers the `agent` event, which is explained below. See [How none of the above is used](impl_intents.html#none-of-the-above) for more information.

- **The *Connect to agent* capability and all capabilities with the *Transfer to human agent* response type**

    These capabilities transfer the user to a human agent. You must add logic that transfers the conversation to your support personnel. One approach you can take is to add logic that connects to an external service that is already used to manage incoming requests at your customer support site. Issues that the virtual agent cannot address can be transferred to your support staff as part of their existing queue of support requests to be prioritized and addressed. To implement the transfer logic, listen for the `agent` event, and define the functions to perform when the event is triggered. See [dwAnswers ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/search.html?f=&amp;type=question&amp;redirect=search/search&amp;q=watson-virtual-agent&amp;q=human){: new_window} for ideas.

- **Capabilities with the *Built-in* response type**

    If you keep the default settings for the core capabilities that are configured to use the built-in conversation response type, and these capabilities are enabled, then you must add some logic to support the information exchange and business transactions that are handled by the built-in conversations. See [Implementing logic to support built-in conversation](impl_intents.html#backend_transaction) for more details.

- **Capabilities with the *Use your own conversation* response type**

    For complex capabilities that require a custom dialog to handle the exchange of information with the user, you can write a dialog using the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service. See [Adding custom dialogs for core capabilities](add-custom-dialog.html) for more details.

## Implementing logic to support built-in conversation
{: #backend_transaction}

Learn how to exchange information and complete business processes that can occur when users interact with capabilities that are configured to use built-in conversation.

### About this task

Some of the core capabilities that are configured to use the built-in conversation response type by default can transact business processes. Your application must be able to register the transaction with the backend systems of record.

- If you implement the provided {{site.data.keyword.IBM_notm}} chat widget, it recognizes events that are triggered by certain user responses. However, there are additional steps you must take to listen for those events in your application so that you can complete the initiated transactions in your backend systems.
- If you are not using the provided chat widget, then you must ensure that your custom user interface can recognize events that are triggered by the built-in conversation flows and handle them appropriately.

Watch the [Make a payment dialog flow process](backend_payment_gif.html#backend_payment_gif) to see an example of how the private credit card variables are stored.

For example, with the **Update address** capability, a user can change the billing address on their account. You must write code that gets the new address from the virtual agent and updates the user's account in your system of record with the new information.

It is important to note that the purpose of a dialog is only to gather information from the user. Information provided by the user is stored in either of two ways:

- Information that is not sensitive or private is stored in the dialog context, which is a data object available to both the bot and to your application.
- Sensitive or private information (such as credit card numbers) is stored in private variables, which are available only to your application and are not passed to the bot.

### Procedure

To fully implement business transactions triggered from capabilities with built-in conversation responses, complete the following steps:

1.  Add logic to your application that gets profile information for the current user from the backend system to show in the chat window before the information is changed. For example, show users an account balance before they pay it.

    Use the `getUserProfileVariables` action. This action both gets the variables and sets them in the profile.

    ```java
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     var variables = data.message.action.args.variables; // specify the variables you want to get in this array
       for (var i = 0; i < variables.length; i++) {
           var value = something(variables[i])
           /*do something to get the value of variables[i]. might be an ajax call or getting
           data from local cookies. Depends on where you stored the information.*/
           window.IBMChat.profile.set(variables[i], value);
       }
       IBMChat.sendSilently('success'); // or cancel or failure
    });
    ```
    {: screen}

    This example uses a REST call to get information about a bill balance and due date.

    ```java
    var xmlHttp = new XMLHttpRequest();
      xmlHttp.onreadystatechange = function() {
        if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
          callback(xmlHttp.responseText);
      }
      xmlHttp.open("GET", url, true);
      xmlHttp.send(null);
    }
    /* Get information from the backend database and add it
    into the profile with IBMChat.profile.set(). */
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     /*
     data = {
       message: {
          text: ['some text'],
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

     httpGetAsync('http://yourdomain.com/userprofile', function(user) {
       /* The record on the backend system might return information like this.
       user = {
         "bill_amount": 42.01,
         "payment_due_date": "11/24/2008"
       }
       */
       var variables = data.message.action.args.variables;
       for (var i = 0; i < variables.length; i++) {
         var value = user[variables[i]]);
         window.IBMChat.profile.set(variables[i], value);
       /* Now the chat widget can use the values it retrieved from the backend service. */
       }
       IBMChat.sendSilently('success'); // or cancel or failure
     });
    });
    ```
    {: screen}

 Add logic to your application that first listens for the action that initiates the business process, and then performs the business process.

    For a list of actions that are associated with capabilities that have built-in conversation response types, see [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action){: new_window}.

### Make a payment
{: #makeapayment}

Perform the following steps to implement code that supports this transaction.
1.  Your application must retrieve the user's current balance and due date from the backend system. Use the `action:getUserProfileVariables` method to get and set the `bill_amount` and `payment_due_date` variables in the profile store.
1. Your application must listen for the `payBill` event and define the logic to perform when the event is triggered.
1. Your application must also listen for the `sendPaymentReceipt` event and define the logic to perform when the event is triggered.

### Update address
{: #updateaddress}

1. The chat widget uses a form layout to ask for the user's new address information and stores it to the profile automatically. It stores these profile variables:

    ```
    user_street_address1
    user_street_address2
    user_locality
    user_state_or_province
    user_zipcode
    ```
    {: screen}

1.  Your application must listen for the `updateAddress` event.

    ```
    IBMChat.subscribe('action:updateAddress', function(data) {<your-code>}
    ```
    {: screen}

    Define a function that gets and sends the new address and the address type (`address_type`) to the backend system when the `updateAddress` action is triggered.

    To collect data with many values, such as a street address, you can use the form layout that is built into the chat widget. Users enter values into multiple fields, and then submit the entire form. For example, to send the new address to your site through a REST POST call, you can use logic like this.

    ```
    /* When a user enters information into a form, it is automatically added
    to the user profile. So a typical flow would be to include a form layout in the
    chat window, and then call this action after the form is submitted */
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
        if (err) IBMChat.receive('There was an error updating the address.');
      });
    });
    ```
    {: screen}

For more information about built-in layouts, see [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout){: new_window}.

### Update contact phone number
{: #updatephone}

1. The chat widget uses a form layout to ask for the user's new phone number and stores it to the profile automatically. It stores these profile variables:

    ```
    user_phone_number
    phone_number_type
    ```
    {: screen}

1. Your application must listen for the `updatePhoneNumber` event and define the logic to get and send the new phone number and type to the backend system when the event is triggered.

### Update email
{: #updateemail}

1. The chat widget uses a form layout to ask for the user's new email address and stores it to the profile automatically. It stores these profile variables:

    ```
    user_email_address
    email_type
    ```
    {: screen}

1. Your application must listen for the `updateEmail` event and define the logic to get and send the new email address to the backend system when the event is triggered. It also send information about which notification types to use the new address for (`email_type`).

## How none of the above is used
{: #none-of-the-above}

Understand how the **None of the above** capability is used by the virtual agent.
{: shortdesc}

Unlike all other core capabilities, the **None of the above** capability cannot be disabled. The reason it cannot be disabled is that it serves as a kind of catch-all for utterances that do not map to any of the configured capabilities. This functionality is useful because you can provide a standard response, such as *I cannot help you with that*, for requests from users for capabilities that your agent doesn't have yet. It also responds to nonsensical questions that customers sometimes ask for fun when they first start to interact with the agent, such as *What should I have for lunch?*

Because of its unique role in the functioning of the virtual agent, how you configure its behavior matters. The **None of the above** capability is triggered often and in ways that are not always obvious, including:

- When you disable any other core capability, utterances that trigger the disabled capability are rerouted to the **None of the above** capability for a response.
- When an utterance does not match any of the enabled core capabilities, it is passed to the **None of the above** capability for a response. If you provide a linked workspace with custom capabilities, both the core workspace and the custom workspace evaluate the utterance to find a match. If no match is found, then the response that is associated with the **None of the above** core capability is used.
- You can configure the **None of the above** capability to have a **Use your own conversation** response type and link it to a workspace with a custom dialog. When no intent match for an utterance is found in the core workspace, the utterance is passed to the **None of the above** capability, which passes it to the custom workspace for a response.
- When you unlink a workspace, if the linked workspace is associated with the **None of the above** capability, then you must take action before you can continue to unlink the workspace. Any other capability that is associated with the workspace that you want to unlink is automatically disabled. But, because the **None of the above** cannot be disabled, you must decide on an alternate response behavior. For example, you can change the response type to **Text**, and add a text message to use in the response.