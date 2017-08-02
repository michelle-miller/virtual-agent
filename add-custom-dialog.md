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

# Adding custom dialogs for core capabilities
{: #use_custom}

For any core capability, you can choose to use your own conversation to interact with the user in order to satisfy the user's goal.
{: shortdesc}

## Building a custom dialog
{: #custom_dialog}

If a core capability that you enable requires handling by a custom dialog, you can use the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service to build the dialog and then link it to your virtual agent.

### About this task

The {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service is a set of tools and APIs you can use to build applications that use natural language interfaces to automate interactions with customers. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} uses the {{site.data.keyword.conversationshort}} service to define the trained capabilities and dialog flow that are used by the bot. If the provided dialog does not provide the flexibility you need, you can build your own dialog using the {{site.data.keyword.conversationshort}} service tools.

For compatibility with the virtual agent, any dialog you build must conform to the design guidelines defined in the [dialog contract ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}. These guidelines specify how the dialog interacts with the virtual agent chat interface, including how to display prompts to users and where to store information provided by users so that it can be accessed by the chat window interface.

The {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}} repository also provides examples that illustrate how the dialog interactions work. You can use the sample as a model for your own dialog. See the [sample dialog flows JSON file ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/michelle-miller-patch-1/sample_dialog_flows.json){: new_window}.

#### Procedure

To build a custom dialog:

1.  If you have not done so already, sign up for the {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service. For more information, see the [{{site.data.keyword.conversationshort}} service Getting Started ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted){: new_window} documentation.
1.  Create a workspace to contain your dialog.

    For information about workspaces, see the [{{site.data.keyword.conversationshort}} service Creating a workspace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace){: new_window} documentation.

1.  Navigate directly to the **{{site.data.keyword.dialogshort}}** tab. (Do not create any intents or entities.)
1.  Create a dialog node for each capability you want to customize.

    One dialog node must have a condition that evaluates to the intent name for the capability that will use it.

    Use the following syntax:

    ```java
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    For example, for the **Contact us** capability, the *intent-name* is `Information-Contact_Us`. Your dialog would test for `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    If you have an older bot, and your settings indicate you want to revert to passing the intent only to your workspace, then use the following syntax instead:

    ```java
    #intent-name
    ```
    {: screen}

    For example, `#Information-Contact_Us`

    To discover the intent name that is associated with a capability, see [Intent names](intent_codenames.html).

1.  Add nodes as needed to create the required dialog flow.

    To be compatible with the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, your dialog must comply with certain design guidelines when storing collected information or using events to communicate with the chat widget interface. Create a dialog that conforms to the {{site.data.keyword.virtualagentshort}} dialog design guidelines at [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}.

1.  Link the workspaces with dialogs that you created to your agent.

    See [Linking workspaces](link_workspace.html) for details.

1.  From the **Core Capabilities** tab of the Capabilities page, change the response type of each capability for which you want to use a custom dialog to the **Use your own conversation** response type.
1.  Pick the workspace that contains the dialog you want to use from the list of linked workspaces, and then click **Save** to finish establishing the link.

    If you haven't linked the workspace yet, then you can click **Link a workspace** from here to link a workspace that you created earlier to your agent.
