---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-27"

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

If a core capability that you enable requires handling by a custom dialog, you can use the {{site.data.keyword.conversationshort}} service to build the dialog and then link it to your virtual agent.

The {{site.data.keyword.conversationshort}} service is a set of tools and APIs you can use to build applications that use natural language interfaces to automate interactions with customers. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} uses the {{site.data.keyword.conversationshort}} service to define the trained capabilities and dialog flow that are used by the bot. If the provided dialog does not provide the flexibility you need, you can build your own dialog using the {{site.data.keyword.conversationshort}} service tools.

For compatibility with the virtual agent, any dialog you build must conform to the design guidelines defined in the [dialog contract ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}. These guidelines specify how the dialog interacts with the virtual agent chat interface, including how to display prompts to users and where to store information provided by users so that it can be accessed by the chat window interface.

## Using a sample dialog
{: #sample-dialogs}

Instead of building a dialog from scratch, you can use one of the dialogs that was created for the {{site.data.keyword.virtualagentfull}} capability packs as a starting point. The sample dialogs are available from a [GitHub repository](https://github.com/watson-virtual-agents/virtual-agent-dialog/tree/master/sample_dialogs). Download the json file that represents the workspace for the capability pack you are using. For example, the **`customer_service.english.dialog_workspace.json`** file is the workspace that contains the dialogs for the English **General customer service** capability pack. Fork the entire repository or download a single file that you want to use (To download, view the **Raw** format of the file, and then use the **Save as** functionality of your web browser).

### Procedure

To add a custom dialog:

1.  If you have not done so already, sign up for the {{site.data.keyword.conversationshort}} service. For more information, see the [{{site.data.keyword.conversationshort}} service Getting Started ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted){: new_window} documentation.
1.  Create a workspace to contain your dialog or import a sample workspace in which dialogs are already defined (See [Using a sample dialog](add-custom-dialog.html#sample-dialogs)).

    For information about workspaces, see the [{{site.data.keyword.conversationshort}} service Creating a workspace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace){: new_window} documentation.

1.  Navigate directly to the **{{site.data.keyword.dialogshort}}** tab. (Do not create any intents or entities.)
1.  Create a dialog node for each capability you want to customize. If you are using a sample dialog, find the node that conditions on the intent you want to edit.

    One dialog node must have a condition that evaluates to the intent name for the capability that will use it.

    Use the following syntax:

    ```java
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    For example, for the **Contact us** capability, the *intent-name* is `Information-Contact_Us`. Your dialog node condition must test for `$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    If you have an older bot and your settings indicate that you want to revert to passing the intent only to your workspace, then use the following syntax instead:

    ```java
    #intent-name
    ```
    {: screen}

    For example, `#Information-Contact_Us`

    To discover the intent name that is associated with a capability, see [Intent names](intent_codenames.html).

    If you are using a sample workspace, edit the existing intent name to use the longer syntax, unless your agent is configured to pass intents only to the workspace.

1.  Add nodes as needed to create the required dialog flow.

    To be compatible with the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, your dialog must comply with certain design guidelines when storing collected information or using events to communicate with the chat widget interface. Create a dialog that conforms to the {{site.data.keyword.virtualagentshort}} dialog design guidelines at [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}.

    **Note**: If you plan to create a custom dialog for the `Help-Ending` capability, you cannot add child nodes to it. The `Help-Ending` is handled differently by the agent code, and is allowed one dialog round-trip only by the service. If you add child nodes to it, an error will occur when the service attempts to process them.

1.  If you are using a sample workspace, remove any nodes from the dialog that you do not intend to customize.

1.  Return to your agent in [{{site.data.keyword.virtualagentfull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://virtual-agent.watson.ibm.com){: new_window}, and link the workspaces with dialogs that you created to your agent.

    See [Linking workspaces](link_workspace.html) for details.

1.  From the **Capabilities** page, change the response type of each capability for which you want to use a custom dialog to the **Use your own conversation** response type.
1.  Pick the workspace that contains the dialog you want to use from the list of linked workspaces, and then click **Save** to finish establishing the link.

    If you haven't linked the workspace yet, then you can click **Link a workspace** from here to link a workspace that you created earlier to your agent.
