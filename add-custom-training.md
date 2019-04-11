---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-15"

---

{:shortdesc: .shortdesc}
{:deprecated: .deprecated}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Augmenting the training data of core capabilities
{: #add-custom-training}

You can extend the types of user utterances that a core capability can understand and respond to by augmenting its training data.
{: shortdesc}

This service is deprecated: All instances of this service are deprecated. Existing instances cannot be used after 19 March 2019.
{: deprecated}

Tailoring the training data for a core capability is a good way to make it recognize phrases that your customers use most often. For example, your users might always ask about insurance as it applies to specific devices that you sell. You can help teach the service to recognize the pattern of such utterances. It can be taught that utterances with the pattern, *Do you insure `device-name`?* are about adding insurance, and not about the devices themselves, for example.

## About this task

You cannot access the workspace for a core capability to update its training data directly. To add to the training data for a core capability, you must add a custom capability that has the same intent name as the core capability to your own {{site.data.keyword.conversationshort}} workspace. From there, you can add your own examples of typical user utterances. The service checks both versions of the capability, the one trained by IBM, and the one trained by you as it analyzes and classifies the input. Adding custom data increases the likelihood that the classifier will recognize and match the input from your customers to this capability correctly at run time.

You cannot augment the training data of a core capability that is configured to use a built-in response type. At run time, after the service identifies the intent of the user input, and maps the intent to the custom workspace, it must use the dialog that is associated with the custom workspace; it cannot switch back to the Core workspace where the built-in dialogs are defined.

## Before you begin
{: #choose-workspace}

Decide where to add the training data.

- If you did not create your own {{site.data.keyword.conversationshort}} workspace to use with the agent, then complete these steps before you complete this procedure:

   1.  If you did not do so already, sign up for the {{site.data.keyword.conversationshort}} service. For more information, see the [{{site.data.keyword.conversationshort}} service Getting Started ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/assistant/getting-started.html){: new_window} documentation.
   1.  Create a workspace to contain your training data.

    For information about workspaces (now called skills), see the [{{site.data.keyword.conversationshort}} service Creating a skill ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/assistant/skill-add.html) {: new_window} documentation.

- If you already have a workspace that contains custom capabilities, add the training data to it.
- If you defined a custom dialog for this core capability that you want to continue to use, and the dialog is defined in a separate workspace from the one with your custom capabilities, then you must reorganize a bit. Move the custom dialog from its existing workspace to the workspace in which your custom capabilities are defined. Any custom dialogs for which you are not augmenting training data can remain in the workspace that is dedicated to custom dialogs.

### Procedure

To augment the training data of a core capability:

1.  Log in to the instance of the {{site.data.keyword.conversationshort}} service that contains the workspace that will contain your training data. See [Before you begin](/docs/services/virtual-agent/add-custom-training.html#choose-workspace) for things to consider as you choose a workspace to use.

1.  From the **Intents** tab, click **Create new**, and then add an intent with the same name as the intent name for the core capability.

    See [Intent codenames](/docs/services/virtual-agent/intent_codenames.html) for a list of the intent names that are associated with each capability.
    To add training data for the `Add insurance` core capability, for example, you would add an intent named `Service_Management-Add_Insurance`. The `#` is added as a prefix to the intent name by the tool.

1.  In the **User example** field, add a phrase that mimics the type of utterances your customers typically use.

    For example, *Do you insure the iPhone 7?*
    Press **Enter** to finish adding the phrase.

1.  Repeat the previous step to add more example utterances. Aim to add at least 20 example utterances. And the more valid examples you can add, the better.  Click **Done** to add the intent and its associated user examples to your workspace.

    For more information about intents, see [Creating intents ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/assistant/intents.html) {: new_window}.

1.  Wait for the classifier training to finish.
1.  Return to your agent in [{{site.data.keyword.virtualagentfull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://virtual-agent.watson.ibm.com){: new_window}.
1.  Link the workspace that contains the training data to your agent. See [Linking workspaces](/docs/services/virtual-agent/link_workspace.html) for details.

    If the workspace is already linked, then you can skip this step.
    {: tip}

1.  To inform the agent about your augmented version of the core capability, add it as a custom capability. See [Adding your own capabilities](/docs/services/virtual-agent/add-custom-capabilities.html) for the detailed steps to follow.

    If you added the training data to a workspace with custom capabilities that were already added to your agent, then you can skip this step.
    {: tip}

## What to do next

From the {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} **Capabilities** page, you can choose the response type to provide for this core capability. All types are supported for core capabilities with augmented training data except the **Built-in** response type.

If you choose to use your own conversation as the response, then follow these guidelines for creating the custom dialog:

- Add the custom dialog for the capability to the same workspace in which the training data is defined.
- When you define the base node condition, you must check for the intent as specified in the syntax used for both core and custom capabilities.

  For example: `#Service_Management-Add_Insurance OR $wva.intents.get(0).intent.equals('Service_Management-Add_Insurance')`

For more information, see [Adding custom dialogs for core capabilities](/docs/services/virtual-agent/add-custom-dialog.html).

If you disable the core capability from the **Capabilities** page, then the IBM-defined capability and the custom capability of the same name are both disabled.
