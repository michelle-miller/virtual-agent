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

# Adding the agent to an existing support channel
{: #integrate_backend}

The {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} API is designed to support the easy transition of a conversation between the virtual agent and a human or other bot service within an existing support infrastructure. In fact, the LivePerson, Inc. team has partnered with {{site.data.keyword.IBM}} to implement just such an integration. For more details, see [LiveEngage integration](integrate_backend.html#liveperson) below.
{: shortdesc}

To build a simple solution yourself, you can code your application such that any capabilities that are configured to be transferred to a human agent are passed to an existing channel that is monitored by support personnel. See [dW Answers ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/318623/where-can-i-find-documentation-examples-on-integra/){: new_window} for information about transferring a conversation to Slack, for example.

To use the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} API to integrate the virtual agent into an existing support channel, complete these steps:

1.  Retrieve the API keys that are necessary to make API calls. See [Getting API keys](api-keys.html) for details.

1.  Use the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} REST APIs to interact with the bot programmatically. Go to the **[{{site.data.keyword.IBM_notm}} developerWorks API Explorer](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}**  portal to access the REST APIs on {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}.

1.  To get the bot ID, do one of the following things:
    - To get the bot ID from the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} configuration tool user interface, complete the following steps:
      1.  From the main menu ![Icon with three horizontal lines](images/hamburger.png)  of {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, click **Documentation**, and then click the **Publish** tab.
      1.  Copy the botID value from the script block.

    - To get the bot ID from the API Explorer web site, follow these steps:
      1.  Sign in to [IBM developerWorks API Explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/api/){: new_window}. Click **My APIs**, and then click the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} tile.
      1.  Click **Documentation>Retrieve Bot** from the navigation bar.
      1.  Click **USE** from the top of the API explorer reference window.
      1.  Scroll down below the *Path and Query parameters* section, and click **TEST**.
      >**Note:** You must pick a key to use with the API before you can test.

      1.  The bot ID is displayed in the `bot_id` parameter in the resulting response.

## LiveEngage integration
{: #liveperson}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} is designed to work in harmony with its human counterparts.

For example, LivePerson, Inc., a provider of cloud mobile and online business messaging solutions, has partnered with IBM to embed a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} bot into their LiveEngage chat experience. **LiveEngage** is an enterprise-class, cloud-based platform that enables consumers to message their favorite brands directly. The new offering, **LiveEngage with Watson**, adds answers from a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} bot to the interaction, with human care representatives brought in seamlessly, in real-time, only if necessary.

The LivePerson bot leverages many of the following behaviors, which are offered by {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}:

- Accept conversations that are routed to it from the external service.
- Trigger the transfer of conversations to the external service under the following conditions:
    - The customer asks to speak to a human agent.
    - A capability is configured to route to a human agent.
    - The customer asks about a subject that the bot is not designed to recognize and address.
- Identify and report the point in the conversation at which the user stops understanding the bot or loses interest in the conversation.
- Recognize when the conversation ends and notify the service to enable any post-interaction activities to begin.
- When transferring a conversation, include information about the user intent so that the conversation can be routed to the human agent who is most adept at addressing requests of that type.
- When transferring a conversation, include the chat history so the person taking over the issue understands the context of the conversation that has taken place so far.

To request access to the offering, see the  [LivePerson website ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://engage.liveperson.com/usage/watson/?utm_medium=website&utm_source=IBM&utm_campaign=Watson){: new_window}.
