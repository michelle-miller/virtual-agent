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

# How it works
{: #how-it-works}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} adds the power of cognitive conversation to the customer satisfaction equation. Make the {{site.data.keyword.virtualagentshort}} chat bot the first point of contact for user questions and requests. The bot can process natural language to  understand what customers are asking about, and can classify the customer need. Depending on the need, it can respond and complete simple business transactions, or route more complicated requests to a human with subject matter expertise.

You choose which user goals you want the bot to handle by selecting the capabilities that you want the bot to have. Use the provided configuration tool to enable and customize capabilities.
{: shortdesc}

## Capabilities
{: #capabilities}

A *capability* is the ability of your {{site.data.keyword.virtualagentshort}} chat bot to recognize and satisfy a specific customer goal. For example, the **Find nearest store** capability uses natural language processing techniques to evaluate a customer utterance such as, *Where are you located?* and recognize from it the customer's goal. To satisfy that goal, it engages in a dialog with the customer to discover the customer's current location, and returns address information for the store nearest the customer.

For each capability, machine learning and linguistics experts at IBM have built training data and used it to iteratively train machine-learning classifiers that can recognize and respond to any user input that matches the goal satisfied by that capability.

To make the bot building process easier, IBM offers capability packs that bring together the most commonly requested capabilities for general customer support scenarios, plus specialized packs that address the most common support needs for key industries.

## Capability packs
{: #capability-packs}

A *capability pack* groups the most important capabilities for your industry together for you. With tens of thousands of example utterances and counter examples, the IBM team has designed groupings of capabilities that address similar customer goals, but that can seemlessly coexist without competing with one another to respond to user queries.

The following table summarizes the packs that are offered. Click the **details** links to see a list of capabilities and descriptions for each supported language.

| Language | Customer Service (General) | Energy  | Retail Banking | Telco   |
|----------|----------------------------|---------|----------------|---------|
| English  | [details](/docs/services/virtual-agent/capabilities_list_general.html?locale=en)   | [details](/docs/services/virtual-agent/capabilities_list_energy.html?locale=en) | [details](/docs/services/virtual-agent/capabilities_list_banking.html?locale=en)        | [details](/docs/services/virtual-agent/capabilities_list_telco.html?locale=en) |
| French   | [details](/docs/services/virtual-agent/capabilities_list_general.html?locale=fr)   | n/a     | n/a            | [details](/docs/services/virtual-agent/capabilities_list_telco.html?locale=fr) |
| German   | [details](/docs/services/virtual-agent/capabilities_list_general.html?locale=de) | n/a     | n/a            | [details](/docs/services/virtual-agent/capabilities_list_telco.html?locale=de) |
| Italian | [details](/docs/services/virtual-agent/capabilities_list_general.html?locale=it) | n/a | n/a | [details](/docs/services/virtual-agent/capabilities_list_telco.html?locale=it) |
| Portuguese (Brazilian) | [details](/docs/services/virtual-agent/capabilities_list_general.html?locale=pt-br)   | n/a     | n/a            | [details](/docs/services/virtual-agent/capabilities_list_telco.html?locale=pt-br) |
| Spanish | [details](/docs/services/virtual-agent/capabilities_list_general.html?locale=es)   | n/a     | n/a            | [details](/docs/services/virtual-agent/capabilities_list_telco.html?locale=es) |

*n/a means not available now.

If the core capabilities do not address a common goal that your customers have, then you can add your own capabilities to supplement those provided in a pack. For example, if you own a bakery, your customers might often ask about the cupcake flavors that you offer. You can add a *Cupcake menu* capability to handle such questions. See [Adding your own capabilities](add-custom-capabilities.html) for more information.

### How {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} differs from {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}
{: #how-they-differ}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} is the service at the heart of the chat bot functionality. It contains the machine learning classifiers that can understand natural language and, given a phrase or sentence, perceive its meaning and categorize it according to classes you have identified as being of interest to you. IBM provides tooling that you can use to build the training data that teaches the machine learning classifier. The tooling also enables you to build the dialog that your bot uses to converse with your customers.

The {{site.data.keyword.conversationshort}} tooling is intuitive and designed such that anyone, even those with no development or machine learning expertise, can use it to construct a powerful chat-driven application. However, it takes time to build the training data and construct a dialog. That's where {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} comes in.

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} is built on {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. But with {{site.data.keyword.virtualagentshort}}, you get the bot service itself, plus the bot is pre-trained - its training performed by experts and researchers in the machine learning and linguistics fields. You just choose which capabilities you want to enable. For example, enable the **Update email address** capability, and just like that, your bot can understand and react to requests related to email address changes.

The {{site.data.keyword.virtualagentshort}} configuration tool makes it easy to choose the capabilities to enable, and to customize how the bot behaves when a capability is triggered during a customer interaction.

You always have the flexibility to add more and more customization to the bot because you can - at any time - link a {{site.data.keyword.conversationshort}} service workspace to your agent to immediately expand its abilities.

## Architectural overview
{: #arch_overview}

The following diagram illustrates the architecture of a typical {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} implementation:

![Architectural overview](images/arch-overview.png)

The implementation includes the following major components:

- **{{site.data.keyword.conversationshort}} service**

    An instance of the {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service. The {{site.data.keyword.conversationshort}} service provides the artifacts for capabilities: the intents, entities, and dialog flow, along with the underlying cognitive processing that power the chat bot's capabilities. You interact directly with the {{site.data.keyword.conversationshort}} service when you want to implement a custom dialog or custom capability only.

    For more information about intents and dialogs, refer to the [{{site.data.keyword.conversationshort}} service documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/index.html#about){: new_window}.

- **Bot**

    A bot built on the {{site.data.keyword.conversationshort}} service, including a set of capabilities. The bot is trained to recognize user inquiries related to customer engagement, such as requests for basic company information and bill paying. The provided bot configuration tool enables you to configure company-specific information that can be provided in response to user queries, and to configure the response for each capability.

- **Your company website**

    Your customer-facing business application, which handles communication with the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} bot and with your systems of record (such as customer databases or billing systems).

- **Chat window**

    The virtual agent chat interface, which customers use to converse with the bot. You can use the provided chat widget, with or without customization, or you can use the client SDK to implement your own chat widget.
