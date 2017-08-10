---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-10"

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

# Aggiunta di dialoghi personalizzati per le capacità base 
{: #use_custom}

Per ogni capacità base, è possibile scegliere di utilizzare le proprie conversazioni
per interagire con l'utente in modo da raggiungere l'obiettivo dell'utente.
{: shortdesc}

## Creazione di un dialogo personalizzato 
{: #custom_dialog}

Se una capacità base abilitata richiede la gestione di un dialogo personalizzato, è
possibile utilizzare il servizio {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} per
creare il dialogo e poi collegarlo all'agent virtuale.

### Informazioni su questa attività

Il servizio {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}} è un insieme di strumenti e API che possono essere
utilizzati per creare applicazioni che utilizzano le interfacce del linguaggio naturale per
automatizzare le interazioni con i clienti. {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} utilizza il servizio
{{site.data.keyword.conversationshort}} per definire le capacità addestrate e
il flusso di dialogo utilizzato dal bot. Se il dialogo fornito non offre la flessibilità
necessaria, è possibile creare un proprio dialogo utilizzando gli strumenti del servizio {{site.data.keyword.conversationshort}}.

Per compatibilità con l'agent virtuale, qualsiasi dialogo creato deve essere conforme alle
linee guida di progettazione indicate in
[contratto
di dialogo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Icona link esterno"){: new_window}. Queste linee guida specificano come il dialogo
interagisce con l'interfaccia di chat dell'agent virtuale, compreso come visualizzare le richieste
agli utenti e dove archiviare le informazioni fornite dagli utenti in modo che possano essere
accessibili dall'interfaccia della finestra di chat.

Il repository di {{site.data.keyword.virtualagentshort}}
{{site.data.keyword.dialogshort}} fornisce anche esempi che illustrano il funzionamento
delle interazioni di dialogo. È possibile utilizzare un esempio come modello per il proprio
dialogo. Vedere il
[file
JSON dei flussi di dialogo di esempio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/michelle-miller-patch-1/sample_dialog_flows.json "Icona link esterno"){: new_window}.

#### Procedura

Per creare un dialogo personalizzato:

1.  Se non si è già registrati, registrarsi al servizio {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. 
Per ulteriori informazioni, consultare la documentazione relativa alle
[operazioni
preliminari del servizio {{site.data.keyword.conversationshort}}
![Icona link
esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "Icona link esterno"){: new_window}.
1.  Creare uno spazio di lavoro per contenere il dialogo.

    Per informazioni sugli spazi di lavoro, consultare la documentazione relativa alla
[creazione
di uno spazio di lavoro del servizio {{site.data.keyword.conversationshort}}
![Icona link
esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace "Icona link esterno"){: new_window}.

1.  Andare direttamente alla scheda **{{site.data.keyword.dialogshort}}**. Non
creare alcun intento o entità.
1.  Creare un nodo di dialogo per ogni capacità che si desidera personalizzare.

    Un nodo di dialogo deve avere una condizione che si risolve in un nome intento per
la capacità che lo utilizzerà.

    Utilizzare la sintassi seguente:

    ```java
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Ad esempio, per la capacità **Contattaci**,
*intent-name* è `Information-Contact_Us`. Il dialogo dovrebbe
verificare la condizione
`$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Se si dispone di un bot precedente e le impostazioni indicano di ripristinare il
passaggio del intento solo allo spazio di lavoro, utilizzare invece la seguente sintassi:

    ```java
    #intent-name
    ```
    {: screen}

    Ad esempio, `#Information-Contact_Us`

    Per individuare il nome intento associato alla capacità, vedere
[Nomi intento](intent_codenames.html).

1.  Aggiungere i nodi necessari per creare il flusso di dialogo richiesto.

    Per essere compatibile con {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} il dialogo deve essere conforme ad alcune linee guida di
progettazione quando si archiviano le informazioni raccolte o si utilizzano gli eventi per
comunicare con l'interfaccia del widget di chat. Creare un dialogo che sia conforme alle linee
guida di progettazione del dialogo di {{site.data.keyword.virtualagentshort}}
all'indirizzo [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md
![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Icona link esterno"){: new_window}.

1.  Collegare gli spazi di lavoro ai dialoghi creati per l'agent.

    Per ulteriori dettagli, vedere [Collegamento degli
spazi di lavoro](link_workspace.html).

1.  Dalla scheda **Core Capabilities (Capacità base)** della pagina Configure (Configura), modificare
il tipo di risposta di ogni capacità per la quale si desidera utilizzare un dialogo
personalizzato sul tipo di risposta **Use your own conversation (Utilizzare una propria conversazione)**.
1.  Selezionare lo spazio di lavoro che contiene il dialogo da utilizzare dall'elenco di
spazi di lavoro collegati e fare clic su **Save (Salva)** per salvare e terminare la creazione del
link.

    Se lo spazio di lavoro non è ancora stato collegato, è possibile fare clic su
**Link a workspace (Collega uno spazio di lavoro)** da qui per collegare uno spazio
di lavoro creato precedentemente dall'agent.
