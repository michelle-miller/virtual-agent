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

# Analyzing user activity
{: #dashboard}

The Metrics page contains a dashboard with visualizations that help you gain insights from data that is collected by the virtual agent.
{: shortdesc}

Your instance of the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} must be deployed, and users must participate in conversations with your virtual agent for at least 30 minutes before the dashboard has any data to share.

## About metrics

The metrics on the page are updated every 30 minutes with data from conversations that occur between the virtual agent and your users. They provide insights into things like:

- How many conversations are taking place
- How many users, both new and returning, are engaging in conversations with the virtual agent
- What customers want to do or learn about most and least (based on which intents are most- and least-often triggered)

The metrics can help you find areas where some additional work might greatly improve the performance of the virtual agent:

- Compare popular topics to the intents and entities that the service is trained to recognize. Any gaps can help you discover new intents or terminology that you can teach the virtual agent about.
- Review the intents that are identified most often just before users request to speak to a human agent. Investigating the causes of escalations can help you prioritize where to focus future training efforts. You can determine whether user inquiries are being misinterpreted, whether your service is missing a common intent altogether, whether the responses that are associated with an intent need improving, and so on.

The metrics can also help you plan human agent resource assignments based on data about the geographic locations in which use of the virtual agent is most and least common, and peak conversation times.

The metrics analyze the data of conversations at a low-level, focusing on the artifacts that comprise capabilities, including:

- **Entities**

    An *entity* represents a term or object that is relevant to an intent and that provides a specific context for an intent. For example, an entity might represent a city where the user wants to find a business location, or the amount of a bill payment. In the user interface, the name of an entity is always prefixed with the `@` character.

- **Intents**

    An *intent* represents the purpose of a user's input. Each capability uses a natural language classifier that can evaluate a user utterance and find a predefined intent if it is present. In the user interface, the name of an intent is always prefixed with the `#` character.

### Procedure

1.  Open the **Metrics** page for the current agent.

    The top of the page has a summary of key data points and gives you a quick sense of how the virtual agent is doing. For each data point, the percentage of change that occurred over the time period that is selected is shown in parentheses. (N/A) for *not available* is displayed until the time period elapses, and a change can be measured and displayed.

    The numbers shown in the summary can sometimes differ from the numbers shown on other pages. For example, the total number of interactions shown here might differ from the total shown on the **Interactions** tab. The difference can occur because the summary information is aggregated and updated on a 30-minute interval while the **Interactions** tab is updated in real time.

    Drill down into the data on each tab to learn more.
    - **Agent Metrics**

        Find out what your users want to learn about or do when they engage with the virtual agent, and which user goals the virtual agent was unable to satisfy.
        - The **Intents &amp; Entities** interactive diagram provides insight into how the {{site.data.keyword.conversationshort}} service is interpreting user input. It shows which entities were used by the service to help it identify the user's intent.

            The following syntax is used to help you to more quickly interpret the information in the diagram:
            - `#<intent-name>`
            - `@<entity-name>`

            Click an intent to see which entities helped the service understand the user input as it did. Or click an entity to see which intents it helped the service to identify.

        - The **Topics** chart captures words or phrases that are uttered most often by users in conversation. Review the chart to understand what users are most interested in talking about. The words in this chart are distinct from the entities that are captured in the Intents &amp; Entities diagram. Entities are words that the {{site.data.keyword.conversationshort}} service was trained to understand and associate with particular intents. The words that are captured in the Topics chart are simply words that are most often encountered in user conversations. The two might overlap and might not. Keep an eye on the words in the Topics chart to stay in tune with your users, and discover new things they might want to do or learn about. Popular topics that remain popular might be good candidates for new entities that can help {{site.data.keyword.watson}} recognize existing intents, or might suggest new intents for you to teach {{site.data.keyword.watson}} about.

    - **User Metrics**

        Get information about where your users are located, and the volume of conversations.

    - **Interactions**

        Look at the transcripts of individual conversations.

        The transcripts do not contain personally identifiable information. Even the name of the user who participated in the conversation is kept private. A user ID, such as 509JAJT8PX, is used in its place. Any other personally identifiable information that users provide during the conversation, such as phone numbers or postal codes, is replaced by variables that indicate the types of data that were provided, but not the data itself.

        > **Note:** The term *interaction* represents a conversation that takes place between the user and the virtual agent. It starts when the user starts to chat with the virtual agent and ends when the chat window session ends (which occurs when the user is logged out, logs out, closes the chat window, or refreshes the chat window). An interaction often includes more than just an exchange of words; users can click buttons, view graphics such as maps, and perform other transactions. And, unlike a phone call to customer support, the interaction with the virtual agent chat session does not end as soon as the user stops engaging with it. The virtual agent doesn't have anywhere else to be; it hangs around in case the user wants to do or ask about something else. For example, if the user asks about something, then 20 minutes later asks about something else (and does so within the same chat window session), then both exchanges are treated as a single interaction with a duration of about 25 minutes.

1.  If you discover meaningful data that you want to share with others, you can export it in CSV format.
