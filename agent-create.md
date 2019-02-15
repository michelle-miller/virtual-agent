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

# Creating an agent
{: #agent-create}

When you subscribe to the service, you are provisioned a bot with an English-language **General Customer Service** capability pack enabled. You can create additional bots with other capability packs or that converse with customers in languages other than English.
{: shortdesc}

To switch to using an agent with a different capability pack as your primary agent, first create a new agent with the capability pack you want, then you can delete the agent that was provisioned for you initially. Be sure to make the switch before you spend too much time configuring the General Customer Service agent. See [Deleting an agent](/docs/services/virtual-agent/agent-create.html#delete) for more information.

If you spend time configuring an agent instance to get it just right, and want to deploy it for use but still be able to experiment with it or try out enhancement ideas, you can clone the agent to create a copy for testing purposes. See [Cloning an agent](/docs/services/virtual-agent/agent-create.html#clone) for more details.

## Agent limits

The number of agents you can create depends on your service plan.

| Service plan     |      Number of agents |
|------------------|----------------------:|
| Trial            |                     2 |
| Standard         |                    10 |
| Premium          |                   100 |

Keep in mind that the API calls made from multiple deployed bots are added together and count toward the total number of virtual agent responses allotted to your subscription.

### Procedure

Follow these steps to create an agent.

1.  From the main menu ![Icon with three horizontal lines](images/hamburger.png) , click **Create New Agent**.

1.  Choose the type of capability pack that you want the agent to be provisioned with when it is created.
   The tile identifies which languages are supported. However, not all capabilities are available in every language. Click the **View Details** link to see a full list of supported capabilities per language.

1.  Click **Select** on a capability pack tile to create a new agent that is provisioned with that pack type.

1.  If applicable, choose the language, and then provide the requested information for the agent.
   >**Note:** The agent label that you specify here is displayed only in the Watson Virtual Agent administration tooling that you use to manage the agent. It is not the name of the virtual agent persona that interacts with your users; you can define or change that from the **Settings** page.

1.  Click **Create**.

## Cloning an agent
{: #clone}

Clone an agent to create a new agent with the same configuration and settings as the original. After you clone the agent, the original and the clone are no longer tied to one another. Changes you make to one are **not** applied to the other.

You cannot create a clone of an agent in a language that is different from the language of the original.

### Procedure

Follow these steps to create an agent.

1.  Open the **Settings** page of the agent that you want to clone.

1.  Scroll down, and then click **Clone Agent**.

1.  Provide the requested information for the agent.
   >**Note:** The agent label that you specify here is displayed only in the Watson Virtual Agent administration tooling that you use to manage the agent. It is not the name of the virtual agent persona that interacts with your users; you define that elsewhere.

1.  Click **Clone**.

## Deleting an agent
{: #delete}

If you are not using an agent, delete it so it does not continue to count toward your agent number limit.

### Procedure

Follow these steps to create an agent.

1.  Open the **Settings** page of the agent that you want to delete.

1.  Scroll down, and then click **Delete Agent**.

1.  When prompted, type the text `delete`, and then click **OK**.
