---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-15"

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

# Release notes
{: #release-notes}

## Changes
{: shortdesc}

### June 2018
{: #June2018}

- **Removed from catalog**: No new instances of the {{site.data.keyword.virtualagentshort}} service can be created as of June 19, 2018.

### May 2018
{: #May2018}

- **Information security**: The documentation includes some new details about data privacy. Read more in [Information security](/docs/services/virtual-agent/information-security.html).

### February 2018
{: #February2018}

- Starting February 16, 2018, the free trial of {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} is no longer available.

### September 2017
{: #September2017}

- You can now augment the training data that is used to teach the service about a core capability. See [Augmenting the training data of core capabilities](/docs/services/virtual-agent/add-custom-training.html) for more information.
- Pass user ID and location information to the /dialogs API endpoint or to the provided chat widget when you initialize it to capture information that the service metrics can subsequently leverage. See [Analyzing user activity](/docs/services/virtual-agent/dashboard.html) for more information.
- Provide a country parameter with the zipcode information that is requested by the built-in dialog for the **Find nearest store** capability to help the bot calculate locations outside the US and Canada.
- Subscriptions are now listed by name, instead of subscription ID. If you have more than one subscriptions, the name that you specified for the subscription when you set it up in IBM Marketplace is displayed at the top of the menu. Any agents that were created under this subscription plan are listed below it. You can click the subscription name to select a different subscription instance and work with its agents. If you have only one subscription, then the subscription name is not displayed at all.
- A new capability pack, **Customer Service for Insurance**, is available (currently in English only) that contains common customer service capabilities specific to the insurance industry. Also, the **Customer Service for Energy and Utilities** and **Customer Service for Retail Banking** capability packs are available in Brazilian Portuguese, French, German, Italian, and Spanish. See [Capability packs](/docs/services/virtual-agent/how-it-works.html#capability-packs) for more details.

### July 2017
{: #July2017}

- You can now create multiple agents, including a clone of an existing agent, and manage them all from the same {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} interface. See [Creating an agent](/docs/services/virtual-agent/agent-create.html) for more details.
- {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} now supports capabilities in the following languages in addition to English: Brazilian Portuguese, French, German, Italian, and Spanish.
    >**Note**: Some words in the user interface of non-English language packs remain in English currently. The team is actively working to translate them into the appropriate languages.
    >**Note**: As is typical with cloud-based applications, the functionality is continuously improved, but the product documentation is translated on a periodic basis. Between translation cycles, the English-language version might be more current than the translated versions of the product documentation.
- When you configure an agent, you can choose from among a set of pre-trained capability packs that provide common customer service capabilities for key industries. See [Capability packs](/docs/services/virtual-agent/how-it-works.html#capability-packs) for more information.
    >**Note:** Existing bot instances are provisioned with an English-language **Customer Service for Telco** capability pack when they are migrated to the new release. New bot instances are provisioned with an English-language **General Customer Service** capability pack.
- The user interface was updated to make it easier to configure capabilities and manage your agents.
- Expanded the number of regional data centers outside the US that linked {{site.data.keyword.conversationshort}} service workspaces can be hosted by.

### June 2017
{: #June2017}

- When you add custom capabilities, Watson Virtual Agent checks for potential conflicts between the custom capabilities you added and the core capabilities that are enabled. It highlights these potential conflicts so you can address them before publishing the agent. See [Resolving validation conflicts](/docs/services/virtual-agent/personalize.html#validate_custom_capabilities) for more details.

### April 2017
{: #April2017}

- You can now augment the subjects that the agent can discuss with your customers by adding your own capabilities. Just link the agent to an {{site.data.keyword.conversationshort}} service workspace with intents, entities, and dialogs that you define. To test it out, you can follow the steps in the [tutorial](/docs/services/virtual-agent/tutorial.html).
- When referring to an agent's ability to recognize an intent and respond to it, the term <cite class="cite">capability</cite> is being used instead of <cite class="cite">intent</cite>. The new term better captures the scope of the agent's ability to both recognize the user's goal (intent) and respond to it appropriately.
- It just got easier to associate the {{site.data.keyword.conversationshort}} workspaces that you want to use with your agent. New linking functionality was added that seamlessly connects to your {{site.data.keyword.conversationshort}} service instance and shows you the workspaces that you have access to, so you can pick the ones you want use.
- Thanks to the new linked workspace experience, you are no longer required to provide the {{site.data.keyword.conversationshort}} service API version level of the workspaces that you want to use. In fact, version support will likely change as new features are added to the underlying {{site.data.keyword.conversationshort}} service that can benefit the virtual agent. We will keep you informed about any version changes that impact existing functionality. The currently supported {{site.data.keyword.conversationshort}} service API version is 2017-02-03. For more information about features in this version, see the [{{site.data.keyword.conversationshort}} release notes](/docs/services/assistant/release-notes.html){: new_window}.
- For existing customers, if you are using a custom conversation as the response type for certain capabilities and rely on the bot passing only the intent and not the user input to the {{site.data.keyword.conversationshort}} service workspace, then you can instruct the bot to continue to do so. Otherwise, the new default behavior is to pass the user input with the intent, so that your workspace can find and extract entities from the user input and make use of them. To choose to retain the old behavior, select the checkbox in the Settings page. In the previous release, you could choose to enable the new approach per intent by setting the **Allow my workspace to extract entities from the user input** field to `Yes`. The per-intent level setting was replaced by this global setting, which makes it easier to anticipate how each intent will behave.

    If you choose to revert to passing only the intent, then you must use the following syntax in the {{site.data.keyword.conversationshort}} service node that matches the intent:

    ```none
    #<code>intent-name
    ```

    where `intent-name` is the code name of the intent that you are configuring.

    Otherwise, you can use this syntax in the condition:

    ```none
    $wva.intents.get(0).intent.equals('intent-name')
    ```

- Fixed a bug in which the bot was treating the next top-level utterance as a new conversation and was resetting the context after the current dialog branch or flow was completed. Now, the context is retained and sent to the new top-level utterance so that any variables that were saved by the previous flow will be available to the next flow.
- You can use the same workspace to both provide a custom dialog for a core capability and to define custom capabilities.
- If you have multiple subscriptions and log into an instance that is associated with a subscription that has expired, you are informed of the expiration and are provided with a link to a functioning instance from your other subscription. 
- Custom workspaces now look for and can handle context that is passed from a previous dialog node.

### March 2017
{: #March2017}

- A new welcome experience is displayed on first use that guides you through the steps that are critical for personalizing the agent, including naming the agent and replacing the canned responses for intents that you want to support. If you are a returning user, the experience will not be displayed.
- The following intents were added to these categories:

    - **Account management**

        - Customer loyalty program: Answers general questions about available loyalty programs.
        - Fraudulent use: Helps users who suspect that their account or credit card has been accessed or used without their approval.
        - Loyalty status: Answers questions about the customer's current status in the loyalty program.
        - Open account: Helps a user open an account.
        - Points value: Answers questions about available points and how points can be used.
        - Redeem points: Helps a user redeem points.
        - Transfer points: Helps a user transfer points.

    - **Help**

        - Security assurance: Answers questions about the security of any information that the user provides to the virtual agent.

    - **Information**

        - Make appointment: Helps the user schedule an appointment when no location is specified.
        - Make home appointment: Helps the user schedule an at-home appointment.

    - **Payment**

        - Bank information: Adds the user's bank information to their account.

    For existing users, the new intents are switched off by default; you can turn on the ones you want to use. For a full list of the supported intents, see [Core capabilities](/docs/services/virtual-agent/capabilities_list.html).

- Fixed a bug which prevented a context parameter with a value that has a data type other than String from being passed to a custom conversation dialog. Also addressed an issue which prevented context from being passed at all to a custom dialog defined for the <cite class="cite">None of the above</cite> intent.

### February 2017
{: #February2017}

- Notifications are now available from the bell icon in the page header. Click the icon to see a list of useful notifications, such as new features or intents that were added to the service since you used it last, or information about a planned service maintenance window.
- The actions of the virtual agent are more transparent to users. The chat widget now shows messages, such as <cite class="cite">Agent is thinking</cite> while the agent processes a request, and <cite class="cite">I cannot complete your request</cite> if the agent is unable to respond to a request after several attempts.
- Performance stability improvements and minor usability fixes were added.

### January 2017
{: #January2017}

- The design of the page navigation was enhanced. Click the menu in the page header to find links to the Configure, Engagement Metrics, and Documentation pages.
- The Try it out sidebar was replaced with a Preview pane that you can choose to open by clicking **Preview** in the page header. The Preview pane displays in front of the current page and provides a chat interface that you can use to test the agent. To close the pane, click **Preview** again.
- To make it easier to configure intents, each response that is displayed in the Preview pane also shows the intent that was calculated by the virtual agent for the input. If you want to update the response for the intent, you can click the intent name to go straight to its configuration page.
- You can now pass context variables to a custom dialog if you provide your own chat interface. The Bot API supports including context variables in the message body that is sent to the `/messages` endpoint. For intents that you configure with the **Use your own conversation** response type, you can program your own user interface application to add the context information to the message that is sent to the custom dialog for processing. For more information, see the following links:

    - [{{site.data.keyword.conversationshort}} service Context variables documentation](/docs/services/assistant/dialog-runtime.html#context){: new_window}
    - [{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} API ](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent#id7931){: new_window}

### December 2016
{: #December2016}

- You can purchase the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} Premium plan that adds premium features, such as data isolation, to enhance the security and reliance of the service. Go to [{{site.data.keyword.IBM_notm}} Marketplace](https://www.ibm.com/marketplace/cloud/cognitive-customer-engagement/){: new_window}  to find more information.

### October 2016
{: #October2016}

- Over 50 intents were added.
- The code names of the following intents changed. If you created your own dialog in a {{site.data.keyword.conversationshort}} service workspace to customize responses for these intents, then you must edit the workspace dialog to reflect the new intent names:

<table cellpadding="4" cellspacing="0" summary="Lists the intents that were renamed." border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d5840e203" class="stentry thleft thbot">Original name</th>
<th valign="bottom" align="left" id="d5840e205" class="stentry thleft thbot">New name</th>
</tr>
<tr class="strow"><td valign="top" headers="d5840e203" class="stentry"><p class="p wrapper">Account_Self_Service-Misc</p></td>
<td valign="top" headers="d5840e205" class="stentry"><p class="p wrapper">Online_Account_Access-Misc</p></td>
</tr>
<tr class="strow"><td valign="top" headers="d5840e203" class="stentry"><p class="p wrapper">Information-Coverage_Area_Inquiry</p></td>
<td valign="top" headers="d5840e205" class="stentry"><p class="p wrapper">Service_Management-Coverage_Area_Inquiry </p></td>
</tr>
<tr class="strow"><td valign="top" headers="d5840e203" class="stentry"><p class="p wrapper">Information-Porting_Inquiry</p></td>
<td valign="top" headers="d5840e205" class="stentry"><p class="p wrapper">Sales-Port_In </p></td>
</tr>
<tr class="strow"><td valign="top" headers="d5840e203" class="stentry"><p class="p wrapper">Information-Return_Device_Inquiry</p></td>
<td valign="top" headers="d5840e205" class="stentry"><p class="p wrapper">Sales-Return_Device </p></td>
</tr>
<tr class="strow"><td valign="top" headers="d5840e203" class="stentry"><p class="p wrapper">Network_Management-Misc</p></td>
<td valign="top" headers="d5840e205" class="stentry"><p class="p wrapper">Complaints-Network</p></td>
</tr>
<tr class="strow"><td valign="top" headers="d5840e203" class="stentry"><p class="p wrapper">Service_Management-International_Rate_Plan_Change_Or_Inquiry</p></td>
<td valign="top" headers="d5840e205" class="stentry"><p class="p wrapper">Service_Management-International_Rate_Plan_Inquiry</p></td>
</tr>
</table>

 <!-- {#release-notes__datasimpletable_v2t_sxc_rx} -->