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

# Personalizzazione dell'agent
{: #personalize}

Assicurare che l'agent virtuale fornisca una risposta alle questioni rilevanti per i clienti. E
che le risposte trasmettano con precisione le informazioni sui servizi offerti dall'azienda o
aiutino i clienti a completare le transazioni commerciali.
{: shortdesc}

## Informazioni su questa attività

È possibile personalizzare l'agent eseguendo le azioni seguenti:

[Aggiunta di dialoghi personalizzati per le
capacità base](/docs/services/virtual-agent/personalize.html#use_custom)

[Aggiunta delle proprie
capacità](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Aggiunta di dialoghi personalizzati per le capacità base
{: #use_custom}

Per ogni capacità base, è possibile scegliere di utilizzare le proprie conversazioni
per interagire con l'utente in modo da raggiungere l'obiettivo dell'utente.

### Creazione di un dialogo personalizzato
{: #custom_dialog}

Se una capacità base abilitata richiede la gestione di un dialogo personalizzato, è
possibile utilizzare il servizio {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} per
creare il dialogo e poi collegarlo all'agent virtuale.

#### Informazioni su questa attività

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
[https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}. 
Queste linee guida specificano come il dialogo interagisce con l'interfaccia di chat dell'agent
virtuale, compreso come visualizzare le richieste agli utenti e dove archiviare le informazioni
fornite dagli utenti in modo che possano essere accessibili dall'interfaccia della finestra di chat.

Il repository di {{site.data.keyword.virtualagentshort}}
{{site.data.keyword.dialogshort}} fornisce anche esempi che illustrano il funzionamento
delle interazioni di dialogo. È possibile utilizzare un esempio come modello per il proprio dialogo. Vedere
il
[file
JSON dei flussi di dialogo di esempio ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/sample_dialog_flows.json){: new_window}.

#### Procedura

Per creare un dialogo personalizzato:

1. Se non si è già registrati, registrarsi al servizio {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}}. Per ulteriori informazioni, consultare la documentazione relativa alle [operazioni preliminari del servizio {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.
1. Creare uno spazio di lavoro per contenere il dialogo.

    Per informazioni sugli spazi di lavoro, consultare la documentazione relativa alla [ creazione di uno spazio di lavoro del servizio {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/create-workspace.html){: new_window}.

1. Andare direttamente alla scheda **{{site.data.keyword.dialogshort}}**. Non
creare alcun intento o entità.
1. Creare un nodo di dialogo per ogni capacità che si desidera personalizzare.

    Un nodo di dialogo deve avere una condizione che si risolve in un nome intento per
la capacità che lo utilizzerà.

    Utilizzare la sintassi seguente:

    ```
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Ad esempio, per la capacità **Contact us**,
*intent-name* è `Information-Contact_Us`. Il dialogo dovrebbe
verificare la condizione
`$wva.intents.get(0).intent.equals('Information-Contact_Us')`.

    Se si dispone di un bot precedente e le preferenze sono impostate per ripristinare
il passaggio del solo intento allo spazio di lavoro, utilizzare invece la seguente
sintassi:

    ```
    #intent-name
    ```
    {: screen}

    Ad esempio, `#Information-Contact_Us`

    Per individuare il nome intento associato alla capacità, vedere
[Nomi intento](/docs/services/virtual-agent/intent_codenames.html).

1. Aggiungere i nodi necessari per creare il flusso di dialogo richiesto.

    Per essere compatibile con {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} il dialogo deve essere conforme ad alcune linee guida di
progettazione quando si archiviano le informazioni raccolte o si utilizzano gli eventi per
comunicare con l'interfaccia del widget di chat. Creare un dialogo che sia conforme alle linee
guida di progettazione del dialogo di {{site.data.keyword.virtualagentshort}}
disponibili
all'indirizzo [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window}.

1. Collegare gli spazi di lavoro ai dialoghi creati per l'agent.

    Per ulteriori dettagli, vedere [Collegamento degli
spazi di lavoro](/docs/services/virtual-agent/link_workspace.html).

1. Dalla scheda **Core Capabilities** della pagina Configure, modificare
il tipo di risposta di ogni capacità per la quale si desidera utilizzare un dialogo
personalizzato sul tipo di risposta **Use your own conversation**.
1. Selezionare lo spazio di lavoro che contiene il dialogo da utilizzare dall'elenco di
spazi di lavoro collegati e fare clic su **Save** per terminare la creazione del
link.

    Uno spazio di lavoro che è già stato utilizzato per aggiungere capacità personalizzate non sarà
visualizzato come opzione. Non è possibile utilizzare lo stesso spazio di lavoro per
aggiungere capacità personalizzate così come si aggiunge un dialogo per una capacità base.

    Se lo spazio di lavoro non è ancora stato collegato, è possibile fare clic su **Link a
workspace** da qui per collegare lo spazio di lavoro creato precedentemente dall'agent.

## Aggiunta delle proprie capacità
{: #add_custom_capabilities}

Per espandere gli argomenti su cui l'agent virtuale può parlare con i clienti,
aggiungere le proprie capacità.

### Prima di iniziare

Quando si utilizza uno spazio di lavoro per fornire un dialogo personalizzato per una
capacità base, è necessario solo fornire un dialogo nello spazio di lavoro. L'agent è già
stato addestrato a riconoscere le espressioni verbali che sono associate alle capacità base, quindi non è
necessario fornire gli intenti, le entità e i dati di addestramento. Quando si fornisce uno
spazio di lavoro che definisce le proprie capacità, è necessario fornire gli intenti e le
entità oltre al dialogo. È inoltre necessario fornire un numero elevato di espressioni di esempio
che il servizio può utilizzare per l'addestramento sugli intenti che si desidera supportare. Utilizzare
la documentazione, le demo e gli strumenti forniti con il
servizio {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} per
creare uno spazio di lavoro con capacità personalizzate. Per ulteriori
informazioni, consultare la documentazione di [{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/index.html){: new_window}.

### Informazioni su questa attività

È possibile creare solo uno spazio di lavoro per definire le capacità personalizzate. Ogni
intento che viene aggiunto allo spazio di lavoro sarà reso disponibile come capacità personalizzata quando si collega lo spazio di lavoro all'agent. Lo spazio di lavoro deve contenere
tutte le capacità che si desidera aggiungere all'agent. Non aggiungere allo spazio di
lavoro intenti che non devono essere gestiti dall'agent.

### Procedura

1. Dall'istanza del servizio {{site.data.keyword.conversationshort}}, creare uno
spazio di lavoro che definisca le capacità personalizzate. Consultare la documentazione del
servizio [{{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

    Seguire queste linee guida:
    - Aggiungere una ramo per ogni capacità che si desidera supportare come nodo di
base (indicato come una *conversazione alternativa* nell'interfaccia
utente dello strumento {{site.data.keyword.conversationshort}}) nel dialogo. Ad esempio,
non definire un nodo di base nel dialogo che riconosce e risponde ai saluti dell'utente, e poi
aggiungere al di sotto nodi figlio corrispondenti ad altri intenti di capacità personalizzate.
    - Evitare di gestire le incongruenze di input dell'utente con loop ricorsivi. Creare
solo diramazioni di dialogo con una fine definitiva.
    - Non creare un intento personalizzato con lo stesso nome di un intento che viene
utilizzato da una capacità base. Per un elenco di nomi da evitare, vedere
[Nomi intento](/docs/services/virtual-agent/intent_codenames.html).

1. Collegare lo spazio di lavoro all'agent. Vedere
[Collegamento degli spazi di lavoro](/docs/services/virtual-agent/link_workspace.html).
1. Dalla pagina **Configure**, aprire la scheda **Custom
capabilities**.
1. Fare clic su **Add Capabilities**.
1. Selezionare lo spazio di lavoro collegato all'agent nel passo 2, e poi fare clic su **Select Workspace**.

    Gli intenti definiti nello spazio di lavoro collegato sono ora elencati come
capacità abilitate.

    > **Nota:** non è possibile disabilitare singole capacità. Se si
desidera rimuovere una capacità personalizzata, è possibile eliminare l'intento dallo spazio
di lavoro nello strumento del servizio {{site.data.keyword.conversationshort}}.

    È possibile rimuovere tutte le capacità contemporaneamente facendo clic su **Remove Private Capabilities**. Rimuovendo
le capacità non viene eliminata l'associazione tra l'agent e lo spazio di lavoro in cui sono
state definite le capacità.

### Risultati

Dopo aver aggiunto le capacità personalizzate, ogni espressione verbale dell'utente
valutata da {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}
viene passata sia allo spazio di lavoro di base che allo spazio di lavoro delle
capacità personalizzate per la valutazione. La capacità che meglio corrisponde all'intento
dell'input dell'utente viene attivata e viene utilizzato il dialogo ad essa associato.

![Mostra il passaggio di un'espressione verbale dall'utente a Watson Virtual Agent. Le
parole sono passate sia allo spazio di lavoro incorporato che allo spazio di lavoro delle
capacità collegate per la valutazione. Lo spazio di lavoro incorporato ha un'affidabilità di
0,85 rispetto a un'affidabilità di 0,55 dello spazio di lavoro delle capacità collegate. Lo
spazio di lavoro incorporato restituisce una risposta a Watson Virtual
Agent da passare all'utente.](images/workspace-confidences.png)

### Test delle capacità personalizzate
{: #test_custom_capabilities}

Dopo aver aggiunto le proprie capacità, effettuare dei test per assicurarsi che il
comportamento sia quello previsto.

#### Informazioni su questa attività

Quando si aggiungono le proprie capacità, è possibile definirne facilmente una
simile nel comportamento a una capacità base esistente. In tal caso, assicurarsi che le due
capacità non vadano in competizione tra loro per rispondere ad alcune domande dell'utente.

#### Procedura

1. Utilizzare il riquadro Preview per porre domande o effettuare i tipi di richiesta che ci
si aspetta dai clienti.

    Sotto la risposta, viene visualizzata la capacità che è stata attivata per
soddisfare le richiesta. Se la capacità visualizzata non è quella prevista, effettuare modifiche
per correggere come vengono instradate le espressioni verbali verso le capacità.

1. Confrontare le capacità definite nell'applicazione di base con quelle definite nello
spazio di lavoro personalizzato.

    - Per riesaminare le capacità fornite con l'applicazione, vedere
[Capacità base](/docs/services/virtual-agent/intent_list.html) che contiene una descrizione di ogni
capacità base.
    - Per riesaminare gli intenti definiti nello spazio di lavoro di
{{site.data.keyword.conversationshort}}, aprire lo spazio di lavoro nello strumento
{{site.data.keyword.conversationshort}} e poi aprire la pagina **Intents**. Espandere
ogni intento per visualizzare i tipi di espressioni verbali a cui è stato addestrato a
rispondere.

1. Utilizzare il riquadro Preview per testare le espressioni verbali che si suppone
possano causare un conflitto.

    In base alle risposte, controllare se le capacità sovrapposte gestiscono
domande dell'utente che sono sufficientemente distinte le une dalle altre da far coesistere le
capacità sovrapposte senza creare un'esperienza confusa per l'utente. Se le due capacità
competono per lo stesso tipo di espressioni verbali, una delle due deve essere disabilitata. È
possibile trattare le capacità sovrapposte nei seguenti modi:
    - **Disabilitare la capacità personalizzata**

        1. Dallo strumento {{site.data.keyword.conversationshort}},
individuare l'intento nella pagina **Intents**, espanderlo e poi fare clic sull'icona
**Delete intent** per eliminarlo dallo spazio di lavoro.
        1. Dopo aver effettuato le modifiche allo spazio di lavoro, automaticamente
viene eseguito un nuovo addestramento. Al completamento dell'addestramento, tornare a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.
        1. Dalla pagina Configure, aprire la scheda **Custom
Capabilities** per confermare che la capacità non è più elencata.

    - **Disabilitare la capacità base**

        1. Dalla scheda **Core Capabilities** della pagina Configure
di {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}},
individuare la capacità da disabilitare.
        1. Fare clic sul riquadro per aprire la capacità e poi posizionare
l'interruttore su Off.

    - **Modificare i dati di addestramento per la capacità personalizzata**

        Se la capacità personalizzata soddisfa un obiettivo del cliente simile ma con
un ambito più ampio, è possibile rimuovere le espressioni verbali di esempio dai dati di
addestramento per la capacità personalizzata per escludere gli esempi che si sovrappongono
con i tipi di espressioni verbali gestiti dalla capacità base. Non è possibile accedere allo
spazio di lavoro per la capacità base; è possibile solo modificare lo spazio di lavoro per
la capacità personalizzata per effettuare modifiche. Per determinare quali espressioni
verbali sono instradate alla capacità base, utilizzare il riquadro Preview per effettuare
un test delle diverse espressioni e individuare quale attiva la capacità base.

        > **Attenzione:** se si sceglie questo approccio potrebbero essere
richiesti molti test e revisioni. È difficile prevedere come il machine learning reagirà alle
modifiche dei dati di addestramento. Sarà necessario eseguire molti test per confermare che le
modifiche apportate abbiano l'impatto desiderato.
        Modificare lo spazio di lavoro della capacità personalizzata eseguendo
queste operazioni:
        1. Dallo strumento {{site.data.keyword.conversationshort}}, individuare l'intento nella pagina
**Intents** e poi espandere l'intento per visualizzare l'elenco delle
espressioni verbali di esempio.
        1. Selezionare la casella accanto alle espressioni verbali che si sovrappongono
con le espressioni gestite dalle capacità base e poi fare clic su **Remove examples**.
        1. Dopo aver effettuato le modifiche allo spazio di lavoro, automaticamente viene
eseguito un nuovo addestramento.

    - **Mantenere entrambe le capacità**

        In alcuni casi, anche se le capacità sono simili, sono destinate a casi
d'uso sufficientemente distinti da poterle tenere entrambe abilitate.

1. Immettere di nuovo le espressioni verbali di test nel riquadro Preview per confermare
che le modifiche danno origine al comportamento previsto. In caso contrario, effettuare ulteriori
modifiche.

## Utilizzo di None of the above
{: #none_of_the_above}

Comprendere come la capacità **None of the above**
viene utilizzata dall'agent virtuale.

A differenza di altre capacità base, la capacità **None of the
above** non può essere disabilitata. Il motivo è che viene utilizzata come un
raccoglitore polivalente per tutte le espressioni verbali che non sono associate a nessuna delle
capacità configurate. Questa capacità è utile perché è possibile fornire una risposta
standard, ad esempio *Non posso esserti di aiuto*, per le richieste degli
utenti per capacità che l'agent non ha ancora disponibili. Inoltre risponde alle domande
assurde che a volte i clienti fanno per gioco, quando iniziano a interagire per la prima volta con
l'agent, ad esempio *Cosa dovrei mangiare oggi a pranzo?*

A causa del suo ruolo univoco nel funzionamento dell'agent virtuale, è importante come si
configura questo comportamento. La capacità **None of the above** viene
attivata spesso e in modi non sempre ovvi, tra cui:

- Quando si disabilita qualsiasi altra capacità base, le espressioni verbali che
attivano la capacità disabilitata sono instradate alla capacità **None of the above**
per avere una risposta.
- Quando un'espressione verbale non corrisponde a nessuna delle capacità base
abilitate, viene passata alla capacità **None of the above** per avere una
risposta. Se si fornisce uno spazio di lavoro collegato con le capacità personalizzate, sia lo
spazio di lavoro di base che lo spazio di lavoro personalizzato valutano l'espressione verbale per
trovare una corrispondenza. Se non viene trovata alcuna corrispondenza, viene utilizzata la
risposta associata alla capacità base **None of the above**.
- È possibile configurare la capacità **None of the
above** con un tipo di risposta **Use your own conversation** e
collegarla a uno spazio di lavoro con un dialogo personalizzato. Quando per un'espressione verbale non si trova
nessuna corrispondenza di intento nello spazio di lavoro di base, l'espressione verbale viene
passata alla capacità **None of
the above**, che la passa allo spazio di lavoro personalizzato per avere una risposta.
- Quando si scollega uno spazio di lavoro, se lo spazio di lavoro collegato è associato
alla capacità **None of the above**, è necessario eseguire alcune azioni
prima di poter continuare a scollegare lo spazio di lavoro. Qualsiasi altra capacità associata
allo spazio di lavoro che si desidera scollegare viene automaticamente disabilitata. Ma, dal
momento che la capacità **None of the above** non può essere
disabilitata, è necessario decidere un comportamento di risposta alternativo. Ad esempio, è
possibile modificare il tipo di risposta in **Display a text response** e
aggiungere un messaggio di testo da utilizzare nella risposta.

