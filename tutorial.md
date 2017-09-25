---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-25"

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

You must have an {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} account and be signed up to use the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service. See the [Getting started tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted){: new_window} for details.

### Results

After completing this tutorial, in addition to answering typical user questions about your company, your agent will be able to address questions and requests that someone driving a car might ask of their co-pilot, such as *When do you think we will arrive?* or *Turn on the radio.*

### Lessons in this tutorial

[Lesson 1: Importing a workspace to {{site.data.keyword.conversationshort}}](tutorial.html#tutless1)

[Lesson 2: Linking a workspace](tutorial.html#tutless2)

[Lesson 3: Adding custom capabilities](tutorial.html#tutless3)

[Lesson 4: Testing custom capabilities](tutorial.html#tutless4)

[Lesson 5: Resolving conflicts between capabilities](tutorial.html#tutless5)

## Lesson 1: Importing a workspace to Conversation
{: #tutless1}

In this lesson, you will learn how to import a workspace to the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service.

### Before you begin

You must have an {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} account and be signed up for the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service.

### About this task

To simplify the process of creating a {{site.data.keyword.conversationshort}} workspace, you will import the `car_demo_workspace.json` file that contains prebuilt artifacts from the simple {{site.data.keyword.conversationshort}} demo.

### Procedure

1.  Download the [car_demo_workspace.json ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json){: new_window} file to your computer.
1.  [Log in ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/dashboard/watson){: new_window} to {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}.
1.  Click your {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} service instance to open it.
1.  Click **Launch tool**.
1.  To import a workspace from a JSON file, click the ![Arrow facing up above an inbox to indicate an import action](images/workspace_import.png) icon.
1.  Click **Choose a file** to browse for the `car_demo_workspace.json` file that you downloaded earlier.
1.  Select **Everything (Intents, Entities, and {{site.data.keyword.dialogshort}})**, and then click **Import**.

### Results

The **Car Dashboard Tutorial** workspace is added to your {{site.data.keyword.conversationshort}} service instance.

## Lesson 2: Linking a workspace
{: #tutless2}

In this lesson, you will learn how to link a {{site.data.keyword.conversationshort}} service workspace to your agent.

### Procedure

1.  From the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} menu, select **Linked Workspaces**.
1.  Click **Link Workspace**.
1.  Select the instance of the {{site.data.keyword.conversationshort}} service to which you imported the workspace in the previous lesson.
1.  Select the **Car Dashboard Tutorial** workspace.
1.  Click **Link workspaces**.

## Lesson 3: Adding custom capabilities
{: #tutless3}

In this lesson, you will learn how to add custom capabilities to your agent.

### Procedure

1.  From the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} menu, select **Capabilities**.
1.  Click the **Custom capabilities** tab.
1.  Click **Add Capabilities**.
1.  Click the **Car Dashboard Tutorial** workspace, and then click **Save**.

    The Custom Capabilities page now displays a list of capabilities.

## Lesson 4: Testing custom capabilities
{: #tutless4}

In this lesson, you will learn more about the custom capabilities that you added.

### About this task

Now that you have added capabilities to the agent, find out what they can do.

### Procedure

1.  From the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} header, click **Preview**.
1.  Ask a question that will trigger a custom capability. Enter the text, *Can we listen to music?*

    The agent evaluates this request and maps it to the **`#turn_on`** custom capability. In the linked workspace, the dialog node with a condition that matches the #turn_on intent is used. As a result, the agent asks what genre of music to play.

    > **Note:** You can see the capability that the user input is mapped to because the capability name is displayed as a link below the response.

1.  Enter a music genre, such as *Classical* or *Rock* to complete the dialog.
1.  Click **Edit** next to the identified capability (#turn_on) from the preview history to open the custom capabilities page.
1.  Now, ask a question that will trigger a core capability. Enter the text, *Tell me about yourself*.

    Click **Edit** next to the *System information* link to open the capability details page. Core capabilities each have their own capability details page where you can customize the response.

1.  Now, try to confuse the agent by entering the text, *Can we listen to some music?*

    The agent recognizes that you already asked to play music, and tells you so.

## Lesson 5: Resolving conflicts between capabilities
{: #tutless5}

In this lesson, you will learn how to resolve conflicts between core and custom capabilities.

### About this task

After you link the custom workspace, you are notified that conflicts exist between core capabilities and some of the capabilities you added.

| Core capability    | Custom capability |
|--------------------|-------------------|
| Ending             | #goodbyes         |
| Find nearest store | #locate_amenity   |
| Greetings          | #greetings        |
| Security assurance | #system_reliance  |

### Procedure

1.  Disable any custom capabilities that you choose to not use.

    - The purpose of the `Ending` and `#goodbyes` capabilities entirely overlaps. To ensure that users have a consistent experience when they finish a conversation with your agent, you must choose to use one or the other, but not both.

        It is common to build logic that is triggered at the end of a conversation. To guarantee that control over any such behavior is maintained by the virtual agent, you will use the core `Ending` capability instead of the custom one.

    - The `Find nearest store` and `#locate_amenity` capabilities overlap. Enter the following sample utterances in the Preview pane to see for yourself:

        - *find the nearest store* is routed to `#locate_amenity`.
        - *find my store* is routed to `Find nearest store`.

        The custom `#locate_amenity` capability provides information about a wider range of amenities besides just a store, but the core capability has a nice built-in conversation associated with it that collects a zip code form the user, and returns the address of the store nearest them. To take advantage of the built-in behavior, use the core `Find nearest store` capability.

    - The security-related capabilities also overlap. To get a better sense of what types of user input are handled by each one, enter these sample utterances in the Preview pane.

        - *Is my data protected?* is routed to `Security assurance`.
        - *Can I trust you with my information?* is routed to `#system_reliance`.

        The `#system_reliance` capability has limited training data compared to the `Security assurance` capability, so you will use the core capability instead of the custom one.

    To disable a custom capability, you must delete it from the {{site.data.keyword.conversationshort}} workspace.
    1.  From the {{site.data.keyword.conversationshort}} tool, expand the `#goodbyes` intent on the Intents page, and then click the **Delete intent** icon to delete it from the workspace.
    1.  Expand the `#locate_amenity` intent, and then click the **Delete intent** icon to delete it from the workspace.
    1.  Expand the `#system_reliance` intent, and then click the **Delete intent** icon to delete it from the workspace.

1.  When you make changes to the custom workspace, it is automatically retrained with the new data. After the workspace training is complete, return to the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.

    From the Capabilities page, open the **Custom Capabilities** tab to confirm that the capabilities you removed (`#goodbyes`, `#locate_amenity`, and `#system_reliance`) are no longer listed.

1.  The `Greetings` and `#greetings` capabilities completely overlap one another. We want the agent to exhibit consistent behavior and to have some personality. The custom `#greetings` capability is designed to emote a specific personality type that reflects the company brand, so you will use the custom capability instead of the core one.

    To disable a core capability, you must turn it off.
    1.  From Capabilities page of {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, find the `Greetings` capability in the **Help** section.
    1.  Click the tile to open it, and then switch the On toggle to **Off**. Click the back arrow to return to the main configuration page.

1.  Do more testing by entering test user queries in the Preview pane to confirm that the appropriate capability is handling user input as expected. For example, you can test the following utterances again:

    - *Can I trust you with my information?* should be handled by the `Security assurance` capability.
    - *find the nearest store* should be handled by the `Find nearest store` capability.

## Tutorial summary
{: #tutless_sum}

While learning about {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, you augmented your agent with custom capabilities.

### Lessons learned

By completing this tutorial, you learned about the following concepts:

- Linked workspaces
- Capabilities
- Conflicting capabilities