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

# Esercitazione: Aggiunta di capacità personalizzate 
{: #tutorial}

Questa esercitazione illustra come migliorare le capacità dell'agent virtuale
aggiungendo proprie capacità.
{: shortdesc}

In questa esercitazione, verrà utilizzato lo spazio di lavoro che potenzia la demo
{{site.data.keyword.conversationshort}} semplice per aggiungere nuove capacità al
proprio agent. Lo spazio di lavoro simula il ruolo di co-pilota per qualcuno che guida
un'automobile. È possibile verificare la demo
[qui
![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://conversation-simple.mybluemix.net/ "Icona link esterno"){: new_window}. Dopo aver importato lo spazio di lavoro nell'istanza
del servizio {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}},
lo spazio di lavoro verrà collegato all'agent. Poi verranno aggiunti gli intenti dello spazio
di lavoro come capacità personalizzate e infine verranno risolti eventuali conflitti tra le
capacità base e le capacità aggiunte.

## Obiettivi di apprendimento

Dopo aver completato questa esercitazione, l'utente sarà in grado di svolgere le seguenti
attività:

- Collegare uno spazio di lavoro all'agent
- Utilizzare un spazio di lavoro collegato per aggiungere capacità personalizzate all'agent
- Risolvere potenziali conflitti tra capacità nuove ed esistenti

Per completare quest'esercitazione sono necessari circa 30 minuti. Se si esplorano altri
concetti relativi a questa esercitazione, sarà necessario più tempo.

### Prerequisiti

È necessario disporre di un account {{site.data.keyword.IBM_notm}}
{{site.data.keyword.Bluemix_notm}} ed essere registrati per utilizzare il servizio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Per
i dettagli, vedere [
Getting started tutorial![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "Icona link esterno"){: new_window}.

### Risultati

Dopo aver completato questa esercitazione, oltre a rispondere alle domande tipiche degli
utenti dell'azienda, l'agent sarà in grado di rispondere a domande e richieste che chi guida
un'automobile potrebbe chiedere al co-pilota, ad esempio *Quando pensi che
arriveremo?* o *Accendi la radio.*

### Lezioni in questa esercitazione

[Lezione 1: Importazione di uno spazio di lavoro in {{site.data.keyword.conversationshort}}](tutorial.html#tutless1)

[Lezione 2: Collegamento di uno spazio di lavoro](tutorial.html#tutless2)

[Lezione 3: Aggiunta di capacità personalizzate](tutorial.html#tutless3)

[Lezione 4: Test delle capacità personalizzate](tutorial.html#tutless4)

[Lezione 5: Risoluzione dei conflitti tra capacità](tutorial.html#tutless5)

## Lezione 1: Importazione di uno spazio di lavoro in Conversation 
{: #tutless1}

In questa lezione, si apprenderà come importare uno spazio di lavoro nel servizio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.

### Prima di iniziare

È necessario disporre di un account {{site.data.keyword.IBM_notm}}
{{site.data.keyword.Bluemix_notm}} ed essere registrati al servizio
{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}}.

### Informazioni su questa attività

Per semplificare il processo di creazione di uno spazio di lavoro
{{site.data.keyword.conversationshort}}, verrà importato il file
`car_demo_workspace.json` che contiene le risorse pregenerate dalla demo
{{site.data.keyword.conversationshort}} semplice.

### Procedura

1.  Scaricare il file [car_demo_workspace.json ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json "Icona link esterno"){: new_window} sul proprio computer.
1.  [Accedere ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/dashboard/watson "Icona link esterno"){: new_window} all'istanza del servizio {{site.data.keyword.conversationshort}} di {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}.
1.  Fare clic su **Launch tool (Avvia strumento)**.
1.  Per importare uno spazio di lavoro da un file JSON, fare clic sull'icona
![Freccia verso l'alto su un vassoio per indicare un'azione di importazione](images/workspace_import.png).
1.  Fare clic su **Choose a file (Scegli un file)** per selezionare il file
`car_demo_workspace.json` precedentemente scaricato.
1.  Selezionare **Everything (Intents, Entities, and
{{site.data.keyword.dialogshort}}) - - Tutto (Intenti, entità e dialogo)**, e poi
fare clic su **Import (Importa)**.

### Risultati

Lo spazio di lavoro **Car Dashboard Tutorial (Esercitazione cruscotto automobile)** è stato aggiunto
all'istanza del servizio {{site.data.keyword.conversationshort}}.

## Lezione 2: Collegamento di uno spazio di lavoro 
{: #tutless2}

In questa lezione, si apprenderà come collegare uno spazio di lavoro del servizio
{{site.data.keyword.conversationshort}} al proprio agent.

### Procedura

1.  Dal menu di {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selezionare **Linked Workspaces (Spazi di lavoro collegati)**.
1.  Fare clic su **Link Workspace (Collega spazio di lavoro)**.
1.  Selezionare l'istanza del servizio {{site.data.keyword.conversationshort}}
in cui è stato importato lo spazio di lavoro nella lezione precedente.
1.  Selezionare lo spazio di lavoro **Car Dashboard Tutorial (Esercitazione cruscotto automobile)**.
1.  Fare clic su **Link workspaces (Collega spazi di lavoro)**.

## Lezione 3: Aggiunta di capacità personalizzate 
{: #tutless3}

In questa lezione, si apprenderà come aggiungere capacità personalizzate all'agent.

### Procedura

1.  Dal menu di {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, selezionare **Capabilities (Capacità)**.
1.  Fare clic su **Custom capabilities (Capacità personalizzate)**.
1.  Fare clic su **Add Capabilities (Aggiungi capacità)**.
1.  Fare clic sullo spazio di lavoro **Car Dashboard Tutorial (Esercitazione cruscotto automobile)**
e poi su **Select Workspace (Seleziona spazio di lavoro)**.

    La pagina Custom Capabilities (Capacità personalizzate) ora visualizza un elenco di capacità.

## Lezione 4: Test delle capacità personalizzate 
{: #tutless4}

In questa lezione, si otterranno altre informazioni sulle capacità personalizzate aggiunte.

### Informazioni su questa attività

Ora che le capacità sono state aggiunte all'agent, viene illustrato il funzionamento.

### Procedura

1.  Dall'intestazione {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, fare clic su **Preview (Anteprima)**.
1.  Porre una domanda che attiverà una capacità personalizzata. Immettere il testo,
*Can we listen to music?* (Possiamo ascoltare un po' di musica)

    L'agente valuta questa richiesta e la associa alla capacità personalizzata **#turn_on**. Nello
spazio di lavoro collegato, viene utilizzato il nodo di dialogo con una condizione che corrisponde
all'intento #turn_on. Come risultato, l'agent chiede che genere di musica ascoltare.

    > **Nota:** è possibile visualizzare la capacità a cui è associato
l'input dell'utente perché il nome della capacità è mostrato come link sotto la risposta.

1.  Immettere un genere musicale, ad esempio *Classical* o
*Rock* (Classica o rock) per completare il dialogo.
1.  Fare clic su **Edit (Modifica)** accanto alla capacità
identificata (#turn_on) dalla cronologia precedente per aprire la pagina delle capacità
personalizzate.
1.  Ora, porre una domanda che attiverà una capacità base. Immettere il testo,
*Tell me about yourself* (Parlami di te).

    Fare clic su **Edit (Modifica)** accanto al link *System
information (Informazioni di sistema)* per aprire la pagina dei
dettagli della capacità. Le capacità base dispongono di una propria pagina dei
dettagli in cui è possibile personalizzare la risposta.

1.  Ora, cercare di confondere l'agent immettendo il testo, *Can we listen to
some music?* (Possiamo ascoltare un po' di musica)

    L'agent riconosce che è stato già chiesto di ascoltare della musica e risponde
in questo modo.

## Lezione 5: Risoluzione dei conflitti tra capacità 
{: #tutless5}

In questa lezione, si apprenderà come risolvere i conflitti tra le capacità base
e le capacità personalizzate.

### Informazioni su questa attività

Dopo aver collegato lo spazio di lavoro personalizzato,  si riceve una notifica
sull'esistenza di conflitti fra le capacità base e alcune delle capacità personalizzate
aggiunte.

| Capacità base      | Capacità personalizzata |
|--------------------|-------------------|
| Ending             | #goodbyes         |
| Find nearest store | #locate_amenity   |
| Greetings          | #greetings        |
| Security assurance | #system_reliance  |

### Procedura

1.  Disabilitare tutte le capacità personalizzate che si sceglie di non utilizzare.

    - Lo scopo delle capacità `Ending (Fine)` e `#goodbyes`
si sovrappone interamente. Per assicurarsi che gli utenti abbiano un'esperienza coerente quando
terminano una conversazione con l'agent, è necessario scegliere di utilizzare l'una o l'altra, ma
non entrambe.

        Spesso viene creata una logica attivata al termine della
conversazione. Per garantire che il controllo su tale comportamento sia mantenuto dall'agent virtuale,
utilizzare la capacità base `Ending (Fine)` invece di quella
personalizzata.

    - Le capacità `Find nearest store (Trova il negozio più vicino)` e `#locate_amenity`
si sovrappongono. Immettere le seguenti espressioni verbali di esempio nel riquadro Preview (Anteprima) per
verificare:

        - *find the nearest store (Trova il negozio più vicino)* viene instradato a `#locate_amenity`.
        - *find my store (Trova il mio negozio)* viene instradato a `Find nearest store (Trova il negozio più vicino)`.

        La capacità personalizzata `#locate_amenity`
fornisce informazioni su una più ampia gamma di strutture ricreative o commerciali rispetto a un
negozio, ma alla capacità base è associata una efficace conversazione incorporata che
raccoglie un codice postale dall'utente e restituisce l'indirizzo del negozio più vicino. Per
trarre vantaggio dal comportamento incorporato, utilizzare la capacità base `Find nearest store (Trova il negozio più vicino)`.

    - Anche le capacità relative alla sicurezza si sovrappongono. Per avere un'idea più
precisa di quali tipi di input dell'utente sono gestiti da ognuna, immettere queste espressioni
verbali di esempio nel riquadro Preview (Anteprima).

        - *Is my data protected?* (I miei dati sono protetti?) viene instradato a `Security assurance (Garanzia di sicurezza)`.
        - *Can I trust you with my information?* (Posso fidarmi per le mie informazioni?) viene instradato a `#system_reliance`.

        La capacità `#system_reliance` dispone di dati di
addestramento più limitati rispetto alla capacità `Security assurance (Garanzia di sicurezza)`, quindi
verrà utilizzata la capacità base invece di quella personalizzata.

    Per disabilitare una capacità personalizzata è necessario eliminarla dallo spazio
di lavoro di {{site.data.keyword.conversationshort}}.
    1.  Dallo strumento {{site.data.keyword.conversationshort}}, espandere l'intento
`#goodbyes` nella pagina Intents (Intenti), poi fare clic sull'icona
**Delete intent (Elimina intento)** per eliminarlo dallo spazio di lavoro.
    1.  Espandere l'intento `#locate_amenity`, poi fare clic sull'icona
**Delete intent (Elimina intento)*** per eliminarlo dallo spazio di lavoro.
    1.  Espandere l'intento `#system_reliance`, poi fare clic sull'icona
**Delete intent (Elimina intento)*** per eliminarlo dallo spazio di lavoro.

1.  Dopo aver effettuato le modifiche allo spazio di lavoro personalizzato, automaticamente
viene eseguito un nuovo addestramento con i nuovi dati. Al completamento dell'addestramento,
tornare a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.

    Dalla pagina Capabilities (Capacità), aprire la scheda **Custom Capabilities (Capacità personalizzate)**
per confermare che le capacità rimosse (`#goodbyes`,
`#locate_amenity` e `#system_reliance`) non sono più elencate.

1.  Le capacità `Greetings (Salve)` e `#greetings`
si sovrappongono completamente. Si desidera che l'agent abbia un comportamento coerente e che
dimostri personalità. La capacità personalizzata `#greetings`
è stata progettata per rappresentare un tipo di personalità specifica che rispecchia il brand
aziendale, quindi sarà utilizzata la capacità personalizzata invece di quella base.

    Per disabilitare una capacità base, è necessario disattivarla.
    1.  Dalla scheda **Core Capabilities (Capacità base)** della pagina Capabilities (Capacità) di
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, individuare
la capacità `Greetings (Salve)`.
    1.  Fare clic sul riquadro per aprire la capacità e poi posizionare
l'interruttore su **Off (Disattivo)**. Fare clic sulla freccia indietro per tornare alla
pagina di configurazione principale.

1.  Eseguire ulteriori test immettendo domande dell'utente di prova nel riquadro Preview (Anteprima) per
confermare che la capacità corretta stia gestendo l'input dell'utente come previsto. Ad
esempio, è possibile testare di nuovo le seguenti espressioni verbali:

    - *Can I trust you with my information?*  (Posso fidarmi per le mie informazioni?) deve essere gestito
dalla capacità `Security assurance (Garanzia di sicurezza)`.
    - *find the nearest store (Trova il negozio più vicino)* deve essere gestito dalla
capacità `Find nearest store (Trova il negozio più vicino)`.

## Riepilogo dell'esercitazione 
{: #tutless_sum}

Durante l'esercitazione su {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, sono state ampliate le capacità personalizzate dell'agent.

### Lezioni apprese

Completando questa esercitazione, sono state acquisite informazioni sui seguenti
concetti:

- Spazi di lavoro collegati
- Capacità
- Capacità in conflitto
