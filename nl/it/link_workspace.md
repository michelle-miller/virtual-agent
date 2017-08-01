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

# Collegamento degli spazi di lavoro
{: #link_workspace}

Prima di poter utilizzare una capacità personalizzata o un dialogo personalizzato con una
capacità base, è necessario stabilire una connessione tra l'agent virtuale e lo spazio di lavoro del servizio
{{site.data.keyword.conversationshort}} che contiene le risorse da utilizzare.
{: shortdesc}

## Informazioni su questa attività

Uno spazio di lavoro è un contenitore del servizio {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}} che contiene gli intenti, le entità e un dialogo,
che sono le risorse utilizzate per definire e addestrare un flusso di conversazione. L'agent può
utilizzare le risorse dello spazio di lavoro, inclusi gli intenti addestrati e un dialogo, perché
interagisce con i clienti per personalizzare e estendere l'ambito degli argomenti di cui parlare.

È possibile collegare gli spazi di lavoro per raggiungere i seguenti obiettivi:

 - Definire le proprie capacità: lo spazio di lavoro deve includere gli intenti, le
espressioni verbali di esempio e un dialogo con condizioni di nodo corrispondenti a ognuno degli
intenti definiti. 
 - Definire un dialogo personalizzato per una capacità base: lo spazio di lavoro deve
includere un dialogo con una condizione di nodo che corrisponde al nome dell'intento per una
capacità base.

Non è possibile utilizzare lo stesso spazio di lavoro per aggiungere capacità personalizzate così come si aggiunge un dialogo per una capacità base. È necessario creare
un singolo spazio di lavoro dedicato che definisce tutte le capacità personalizzate che si
desidera utilizzare. Creare uno o più spazi di lavoro separati per definire i dialoghi da
utilizzare come risposta alle capacità base.

## Procedura

1. Dal menu di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, selezionare **Linked
Workspaces**.
1. Fare clic su **Link Workspace**.

    Fornire le credenziali dell'account {{site.data.keyword.IBM_notm}}
{{site.data.keyword.Bluemix_notm}} per fornire a {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} l'autorizzazione ad accedere alla propria istanza
del servizio {{site.data.keyword.conversationshort}} e richiamare le informazioni
sullo spazio di lavoro.

1. Selezionare l'istanza del servizio {{site.data.keyword.conversationshort}} che
contiene gli spazi di lavoro da utilizzare.
1. Selezionare uno o più spazi di lavoro da collegare all'agent.
1. Fare clic su **Link workspaces**.

[Creazione di un dialogo personalizzato](/docs/services/virtual-agent/personalize.html#custom_dialog)

[Aggiunta delle proprie capacità](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Scollegamento degli spazi di lavoro
{: #unlink_workspace}

Se si decide che non si desidera mantenere una connessione tra l'agent virtuale e uno
specifico spazio di lavoro di {{site.data.keyword.conversationshort}}, è possibile
scollegare lo spazio di lavoro.

### Prima di iniziare

Assicurarsi che lo spazio di lavoro da scollegare non sia attivamente utilizzato da una
capacità che lo richiede. Tenere presente che uno spazio di lavoro che è collegato a un agent
virtuale è disponibile per l'uso da parte di tutte le capacità associate a tale agent, sia che
sia una capacità personalizzata che una capacità base.

### Informazioni su questa attività

Quando si scollega uno spazio di lavoro da una capacità, la capacità viene
automaticamente disattivata. Disabilitando la capacità si è certi che gli utenti attivi non
saranno esposti a comportamenti non previsti durante il periodo in cui sono eseguite le modifiche. Questo
approccio è valido per tutto tranne la capacità **None of the above**, che non può essere disabilitata.  È
necessario modificare il tipo di risposta da **Use your own conversation** in
una delle altre opzioni di tipo di risposta per la capacità prima di poter scollegare
uno spazio di lavoro associato.

### Procedura

1. Dal menu di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, selezionare **Linked
Workspaces**.
1. Fare clic per aprire lo spazio di lavoro per cui si desidera eliminare l'associazione
all'agent.
1. Fare clic su **Unlink Workspace**.

[Collegamento degli spazi di lavoro](/docs/services/virtual-agent/link_workspace.html)

