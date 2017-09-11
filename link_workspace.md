---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-08"

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

# Linking workspaces
{: #link_workspace}

Before you can use a custom capability or a custom dialog with a core capability, you must establish a connection between the virtual agent and the {{site.data.keyword.conversationshort}} service workspace that contains the artifacts you want to use.
{: shortdesc}

## About workspaces

A workspace is a {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service container that holds intents, entities, and a dialog, which are artifacts that are used to define and train a conversation flow. Your agent can use artifacts from the workspace, including trained intents and a dialog, as it interacts with your customers to customize and extend the scope of the things it can discuss.

You can link workspaces to achieve the following goals:

- Define your own capabilities: The workspace must include intents, sample utterances, and a dialog with node conditions that match each defined intent.
- Define a custom dialog for a core capability: The workspace must include a dialog with a node condition that matches the intent name for a core capability.

You *can* use the same workspace to add both custom capabilities and custom dialogs for core capabilities. However, it is simpler to manage things if you create a single dedicated workspace to define the custom capabilities that you want to use and one or more separate workspaces to define the dialogs you want to use as responses for core capabilities. If you do choose to use the same workspace for both, then be sure to add any nodes that contain custom dialogs for specific core capabilities at the top of the dialog tree to prevent utterances from being incorrectly routed to custom capabilites.

### Procedure

1.  Open the **Linked Workspaces** page for the current agent.
1.  Click **Link Workspace**.

    Provide your {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} account credentials to give {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} permission to access your {{site.data.keyword.conversationshort}} service instance and retrieve workspace information.

1.  Select the instance of the {{site.data.keyword.conversationshort}} service that contains the workspaces you want to use.
1.  Select one or more workspaces that you want to link to your agent.
1.  Click **Link workspaces**.

[Building a custom dialog](add-custom-dialog.html)

[Adding your own capabilities](add-custom-capabilities.html)

## Unlinking workspaces
{: #unlink_workspace}

If you decide that you do not want to maintain a connection between your virtual agent and a specific {{site.data.keyword.conversationshort}} workspace, you can unlink the workspace.

### Before you begin

Be sure that the workspace you want to unlink is not being actively used by a capability that requires it. Remember that a workspace that you link to the virtual agent is available for use by any capability that is associated with that agent, be it a custom capability or a core capability.

### About this task

When you unlink a workspace from a capability, the capability is automatically turned off. Disabling the capability ensures that active users are not exposed to unexpected behavior while you are making changes. This approach is true for all but the **None of the above** and **Connect to agent** capabilities. You must change the response type from **Use your own conversation** to one of the other response type options for these capabilities before you can unlink a workspace that is associated with them.

### Procedure

1.  Open the **Linked Workspaces** page for the current agent.
1.  Click to open the workspace that you want to disassociate with the agent.
1.  Click **Unlink this Workspace** ![trash can icon representing delete link relationship](images/trash.png).

[Linking workspaces](link_workspace.html)