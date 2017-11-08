---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-12"

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

# Tutorial: Adding custom capabilities
{: #tutorial}

This tutorial helps you understand how to augment the capabilities of your virtual agent by adding your own capabilities.
{: shortdesc}

In this tutorial, you will use the workspace that powers the simple {{site.data.keyword.conversationshort}} demo to add new capabilities to your agent. The workspace simulates the role of a co-pilot for someone driving a car. You can check out the demo [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://conversation-simple.mybluemix.net/){: new_window}. After importing the workspace to your {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service instance, you will link the workspace to your agent. You will then add the workspace intents as custom capabilities, and finally address any conflicts that arise between the core capabilities and the capabilities that you add.

## Learning objectives

After you complete this tutorial, you will know how to perform the following tasks:

- Link a workspace to your agent
- Use a linked workspace to add custom capabilities to your agent
- Address potential conflicts between existing and new capabilities

This tutorial should take approximately 30 minutes to finish. If you explore other concepts related to this tutorial, it could take longer to complete.

### Prerequisites

You must have an {{site.data.keyword.Bluemix_notm}} account and be signed up to use the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service. See the [Getting started tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted){: new_window} for details.

### Results

After completing this tutorial, in addition to answering typical user questions about your company, your agent will be able to address questions and requests that someone driving a car might ask of their co-pilot, such as *When do you think we will arrive?* or *Turn on the radio.*

### Steps in this tutorial

[Step 1: Importing a workspace to {{site.data.keyword.conversationshort}}](tutorial.html#tutless1)

[Step 2: Linking a workspace](tutorial.html#tutless2)

[Step 3: Adding custom capabilities](tutorial.html#tutless3)

[Step 4: Testing custom capabilities](tutorial.html#tutless4)

[Step 5: Resolving conflicts between capabilities](tutorial.html#tutless5)

## Step 1: Importing a workspace to Conversation
{: #tutless1}

By performing this step, you will learn how to import a workspace to the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service.

### Before you begin

You must have an {{site.data.keyword.Bluemix_notm}} account and be signed up for the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service.

### About this task

To simplify the process of creating a {{site.data.keyword.conversationshort}} workspace, you will import the `car_demo_workspace.json` file that contains prebuilt artifacts from the simple {{site.data.keyword.conversationshort}} demo.

### Procedure

1.  Download the [car_demo_workspace.json ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json){: new_window} file to your computer. (You can use the *Save as* functionality of your web browser to download it.)
1.  [Log in ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/dashboard/watson){: new_window} to {{site.data.keyword.Bluemix_notm}}.
1.  Click your {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service instance to open it.
1.  Click **Launch tool**.
1.  To import a workspace from a JSON file, click the ![Arrow facing up above an inbox to indicate an import action](images/workspace_import.png) icon.
1.  Click **Choose a file** to browse for the `car_demo_workspace.json` file that you downloaded earlier.
1.  Select **Everything (Intents, Entities, and {{site.data.keyword.dialogshort}})**, and then click **Import**.

### Results

The **Car Dashboard Tutorial** workspace is added to your {{site.data.keyword.conversationshort}} service instance.

## Step 2: Linking a workspace
{: #tutless2}

This step and the next step work together to add intents from a {{site.data.keyword.conversationshort}} service workspace to your agent as custom capabilities.

In this step, you will link a workspace with a set of defined intents to the agent. In the next step, you will add the intents from the linked workspace to the agent as custom capabilities.

When you add custom capabilities to the agent, you give the agent the ability to recognize and respond to more intents than the built-in customer service capabilities that it can recognize automatically.

### Procedure

1.  Return to your agent in [{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}](https://virtual-agent.watson.ibm.com/).
1.  From the menu, select **Linked Workspaces**.
1.  Click **Link Workspace**.
1.  Select the instance of the {{site.data.keyword.conversationshort}} service to which you imported the workspace in the previous step.
1.  Select the **Car Dashboard Tutorial** workspace.
1.  Click **Link workspaces**.

## Step 3: Adding custom capabilities
{: #tutless3}

By completing this step, you will learn how to add custom capabilities to your agent. These custom capabilities enable the agent to recognize utterances that a user might say to control a car dashboard. In practice, you can create a workspace in which you define intents that represent common goals of your users in particular, and link the workspace to your agent to add those intents as custom capabilities.

### Procedure

1.  From the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} menu, select **Capabilities**.
1.  Expand the **Custom** section.
1.  Click **Add Capabilities**.
1.  Click the **Car Dashboard Tutorial** workspace, and then click **Save**.

The intents that were defined in the workspace are now listed as custom capabilities and are enabled for use by your agent.

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} automatically begins to validate the custom capabilities that you added. It compares the utterances that existing core capabilities are designed to address to those the new custom capabilities are designed to address to look for possible conflicts.

## Step 4: Testing custom capabilities
{: #tutless4}

By completing this step, you will learn more about the capabilities that were created when you linked the Car Dashboard Tutorial workspace to the agent and added the intents from the workspace as custom capabilities.

### About this task

While the newly-added custom capabilities are being validated, let's find out what they can do.

### Procedure

1.  From the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} header, click **Preview**.
1.  Ask a question that will trigger a custom capability. Enter the text, *Can we listen to music?*

    The agent evaluates this request and maps it to the **`#turn_on`** custom capability. In the linked workspace, the dialog node with a condition that matches the #turn_on intent is used. As a result, the agent asks what genre of music to play.

    > **Note:** You can see the capability that the user input is mapped to because the capability name is displayed below the response.

1.  Enter a music genre, such as *Classical* or *Rock* to complete the dialog.
1.  Now, ask a question that will trigger a core capability. Enter the text, *Tell me about yourself*.

    Click **Edit** next to the *System information* capability name to open the capability details page. Core capabilities each have their own capability details page where you can customize the response.

1.  Now, try to confuse the agent by entering the text, *Can we listen to some music?*

    The agent recognizes that you already asked to play music, and tells you so.

## Step 5: Resolving conflicts between capabilities
{: #tutless5}

By completing this step, you will learn how to resolve conflicts between core and custom capabilities.

### About this task

After the validation of the newly-added custom capabilities is completed, you are notified that conflicts exist between core capabilities and some of the capabilities you added. You will address these conflicts next.

### Procedure

1.  Click **Resolve** to see a list of the conflicts.
1.  Disable any conflicting core capabilities that you do not need.

    - The `#turn_on` intent that you added as a custom capability conflicts with several of the core capabilities. However, its function is useful, so we will keep the `#turn_on` capability and disable the core capabilities that conflict with it. These include:

      - Bill adjustment
      - Bill explanation*
      - One-time charge explanation*
      - Recurring charges

    *These core capabilities might not be listed as conflicts after the first validation run completes, but conflicts are typically found with these core capabilities on subsequent validation runs.

    - The `Help` core capability conflicts with several custom capabilities. This core capability can be safely disabled.

    To disable a core capability from the *Review and resolve conflicts* page, find the core capabilities that you want to disable, and switch the On toggle next to each one to **Off**. Close the *Review and resolve conflicts* page.

    The validation process runs again automatically.

1.  Disable any custom capabilities that serve a purpose that is already met by a core capability.

    - The purpose of the `Ending` and `#goodbyes` capabilities entirely overlaps. The same is true for the `Greetings` and `#greetings` capabilities. To ensure that users have a consistent experience when they start and finish a conversation with your agent, you must choose to use one or the other, but not both.

    It is common to build logic that is triggered at the end of a conversation. To guarantee that control over any such behavior is maintained by the virtual agent, you will use the core `Ending` core capability instead of the custom one. You will also use the core `Greetings` capability instead of the custom one.

    To disable a custom capability, you must delete it from the {{site.data.keyword.conversationshort}} workspace.
    1.  From the {{site.data.keyword.conversationshort}} tool, expand the `#goodbyes` intent on the Intents page, and then click the **Delete intent** icon to delete it from the workspace.
    1.  Expand the `#greetings` intent, and then click the **Delete intent** icon to delete it from the workspace.
    1.  To preserve the integrity of the source workspace, open the Dialogs tab and remove the dialog nodes that condition on the `#goodbyes` and `#greetings` intents.
    1.  When you make changes to the custom workspace, it is automatically retrained with the new data. After the workspace training is complete, return to your agent in [{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}](https://virtual-agent.watson.ibm.com/).
    1.  From the Capabilities page, click **Revalidate**.

1.  Do more testing by entering test user queries in the Preview pane to confirm that the appropriate capability is handling the user input in the way you expect.

## Tutorial summary
{: #tutless_sum}

While learning about {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, you augmented your agent with custom capabilities.

### What you learned

By completing this tutorial, you learned about the following concepts:

- Linked workspaces
- Capabilities
- Conflicting capabilities
