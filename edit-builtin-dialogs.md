---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-26"

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

# Editing built-in dialogs
{: #edit-builtin-capabilities}

If you like the built-in dialogs that are provided with select capabilities, but want to reword a response, or add more dialog turns to it, you can do so.
{: shortdesc}

The Conversation workspaces that contain the dialogs are published to GitHub. You can find the workspace that contains the dialog you want to edit, download it, make your changes, and then link your revised version of the workspace to your agent and treat it as a custom dialog. To see the conversation flows that are defined by the built-in dialogs, see [Built-in dialogs](configure.html#builtin_dialog_ovw).

## Procedure

1.  Go to the [GitHub repository](https://github.com/watson-virtual-agents/virtual-agent-dialog/tree/master/sample_dialogs) that contains the dialogs.
1.  Find the JSON file that contains the dialog you want to edit.

    For example, the **`customer_service.english.dialog_workspace.json`** file is the workspace that contains the built-in dialogs for the English **General customer service** capability pack. Fork the entire repository or download a single file that you want to use (View the **Raw** format of the file, and then use the **Save as** functionality of your web browser).

1.  Log in to your {{site.data.keyword.conversationshort}} service instance.
1.  From the Workspaces page, import the workspace JSON file.

    For information about importing workspaces, see the [{{site.data.keyword.conversationshort}} service documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/conversation/configure-workspace.html#creating-workspaces){: new_window}.

1.  Make edits or additions to the dialogs that you want to change. Remove any dialogs that you do not change.
1.  Return to your agent in [{{site.data.keyword.virtualagentfull}}](https://virtual-agent.watson.ibm.com).
1.  Link the revised workspace to the agent. See [Linking workspaces](link_workspace.html).
1.  From the **Capabilities** page, for each core capability that uses a built-in dialog that you edited, change the response type from **Built-in** to **Use your own conversation**.
1.  Pick the workspace that contains the revised dialog you want to use from the list of linked workspaces, and then click **Save** to finish establishing the link.
