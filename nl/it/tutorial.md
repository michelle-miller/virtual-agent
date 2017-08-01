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

# Esercitazione: Aggiunta di capacità personalizzate
{: #tutorial}

Questa esercitazione illustra come migliorare le capacità dell'agent virtuale
aggiungendo proprie capacità.
{: shortdesc}

In questa esercitazione. verrà utilizzato lo spazio di lavoro che potenzia la demo
{{site.data.keyword.conversationshort}} semplice per aggiungere nuove capacità al
proprio agent. Lo spazio di lavoro simula il ruolo di co-pilota per qualcuno che guida
un'automobile. È possibile visualizzare la demo
[qui ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://conversation-simple.mybluemix.net/){: new_window}. Dopo aver importato lo spazio di lavoro nell'istanza
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

## Prerequisiti

È necessario disporre di un account {{site.data.keyword.IBM_notm}}
{{site.data.keyword.Bluemix_notm}} ed essere registrati per utilizzare il servizio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Per
ulteriori dettagli, vedere [https://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.

## Risultati

Dopo aver completato questa esercitazione, oltre a rispondere alle domande tipiche degli
utenti dell'azienda, l'agent sarà in grado di rispondere a domande e richieste che chi guida
un'automobile potrebbe chiedere al co-pilota, ad esempio *Quando pensi che
arriveremo?* o *Accendi la radio.*

### Lezioni in questa esercitazione

[Lezione 1: Importazione di uno spazio di lavoro in {{site.data.keyword.conversationshort}}](/docs/services/virtual-agent/tutorial.html#tutless1)

[Lezione 2: Collegamento di uno spazio di lavoro](/docs/services/virtual-agent/tutorial.html#tutless2)

[Lezione 3: Aggiunta di capacità personalizzate](/docs/services/virtual-agent/tutorial.html#tutless3)

[Lezione 4: Test delle capacità personalizzate](/docs/services/virtual-agent/tutorial.html#tutless4)

[Lezione 5: Risoluzione dei conflitti tra capacità](/docs/services/virtual-agent/tutorial.html#tutless5)

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

1. Scaricare il
file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json" download>car_demo_workspace.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> sul computer.
1. [Accedere ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/dashboard/watson){: new_window} alla propria istanza del servizio {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.
1. Fare clic su **Launch tool**.
1. Per importare uno spazio di lavoro da un file JSON, fare clic sull'icona
![Freccia verso l'alto su un vassoio per indicare un'azione di importazione](images/workspace_import.png).
1. Fare clic su **Choose a file** per selezionare il file
`car_demo_workspace.json` precedentemente scaricato.
1. Selezionare **Everything (Intents, Entities, and
{{site.data.keyword.dialogshort}})**, e poi fare clic
su **Import**.

### Risultati

Lo spazio di lavoro **Car Dashboard Tutorial** è stato aggiunto
all'istanza del servizio {{site.data.keyword.conversationshort}}.

## Lezione 2: Collegamento di uno spazio di lavoro
{: #tutless2}

In questa lezione, si apprenderà come collegare uno spazio di lavoro del servizio
{{site.data.keyword.conversationshort}} al proprio agent.

### Procedura

1. Dal menu di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, selezionare **Linked
Workspaces**.
1. Fare clic su **Link Workspace**.
1. Selezionare l'istanza del servizio {{site.data.keyword.conversationshort}}
in cui è stato importato lo spazio di lavoro nella lezione precedente.
1. Selezionare lo spazio di lavoro **Car Dashboard Tutorial**.
1. Fare clic su **Link workspaces**.

## Lezione 3: Aggiunta di capacità personalizzate
{: #tutless3}

In questa lezione, si apprenderà come aggiungere capacità personalizzate all'agent.

### Procedura

1. Dal menu di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, selezionare **Configure**.
1. Fare clic su **Custom capabilities**.
1. Fare clic su **Add Capabilities**.
1. Fare clic sullo spazio di lavoro **Car Dashboard Tutorial**
e poi su **Select Workspace**.

    La pagina Custom Capabilities ora visualizza un elenco di capacità.

## Lezione 4: Test delle capacità personalizzate
{: #tutless4}

In questa lezione, si otterranno altre informazioni sulle capacità personalizzate aggiunte.

### Informazioni su questa attività

Ora che le capacità sono state aggiunte all'agent, viene illustrato il funzionamento.

### Procedura

1. Dall'intestazione {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}, fare clic su **Preview**.
1. Porre una domanda che attiverà una capacità personalizzata. Immettere il testo,
*Can we listen to music?*

    L'agente valuta questa richiesta e la associa alla capacità personalizzata **#turn_on**. Nello
spazio di lavoro collegato, viene utilizzato il nodo di dialogo con una condizione che corrisponde
all'intento #turn_on. Come risultato, l'agent chiede che genere di musica ascoltare.

    > **Nota:** è possibile visualizzare la capacità a cui è associato
l'input dell'utente perché il nome della capacità è mostrato come link sotto la risposta.
1. Immettere un genere musicale, ad esempio *Classical* o
*Rock* per completare il dialogo.
1. Fare clic sul link **#turn_on** dalla cronologia di anteprima per
aprire la pagina capacità personalizzate.
1. Ora, porre una domanda che attiverà una capacità base. Immettere il testo,
*Tell me about yourself*.

    Fare clic sul link **System information** per aprire la pagina dei
dettagli della capacità. Le capacità base dispongono di una propria pagina dei
dettagli in cui è possibile personalizzare la risposta.

1. Ora, cercare di confondere l'agent immettendo il testo, *Can we listen to
some music?*

    L'agent riconosce che è stato già chiesto di ascoltare della musica e risponde
in questo modo.

## Lezione 5: Risoluzione dei conflitti tra capacità
{: #tutless5}

In questa lezione, si apprenderà come anticipare e risolvere i conflitti tra le capacità base e le capacità personalizzate.

### Informazioni su questa attività

Si desidera che l'utente abbia un'esperienza coerente quando interagisce con l'agent. Se le
risposte a determinate richieste variano tra le risposte fornite da una capacità base e
quelle fornite da una capacità personalizzata, si può generare confusione nell'utente. Identificare
dove potrebbero verificarsi questi conflitti e intraprendere le azioni opportune per garantire che
sia attivata solo una capacità per ogni tipo di richiesta.

### Procedura

1. Confrontare le capacità definite nell'applicazione di base con quelle definite nello
spazio di lavoro personalizzato.

    - Per riesaminare le capacità fornite con l'applicazione, vedere
[Capacità base](/docs/services/virtual-agent/intent_list.html) che contiene una descrizione di ogni
capacità base.
    - Per riesaminare gli intenti definiti nello spazio di lavoro di
{{site.data.keyword.conversationshort}}, aprire lo spazio di lavoro nello strumento
{{site.data.keyword.conversationshort}} e poi aprire la pagina
**Intents**. Espandere ogni intento per visualizzare i tipi di espressioni
verbali a cui è stato addestrato a rispondere.

1. In base alla descrizione e alla funzione di ognuna, fare un elenco di tutte le
capacità che si sospetta possano essere in competizione per la gestione delle espressioni
verbale degli utenti.

    Ad esempio, le seguenti capacità potrebbero entrambe cercare di rispondere allo
stesso input dell'utente:

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d6710e463" class="stentry thleft thbot">Capacità base</th>
    <th valign="bottom" align="left" id="d6710e465" class="stentry thleft thbot">Capacità personalizzata</th>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Ending</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#goodbyes</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Find nearest store</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#locate_amenity</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Greetings</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#greetings</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Security assurance</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#system_reliance</p></td>
    </tr>
    </table>

1. Disabilitare tutte le capacità personalizzate che si sceglie di non utilizzare.

    - Lo scopo delle capacità `Ending` e `#goodbyes`
si sovrappone interamente. Per assicurarsi che gli utenti abbiano un'esperienza coerente quando
terminano una conversazione con l'agent, è necessario scegliere di utilizzare l'una o l'altra, ma
non entrambe.

        Spesso viene creata una logica attivata al termine della
conversazione. Per garantire che il controllo su tale comportamento sia mantenuto dall'agent virtuale,
utilizzare la capacità base `Ending` invece di quella
personalizzata.

    - Le capacità `Find nearest store` e `#locate_amenity`
si sovrappongono. Immettere le seguenti espressioni verbali di esempio nel riquadro Preview per
verificare:

        - *find the nearest store* viene instradato a `#locate_amenity`.
        - *find my store* viene instradato a `Find nearest store`.

        La capacità personalizzata `#locate_amenity`
fornisce informazioni su una più ampia gamma di strutture ricreative o commerciali rispetto a un
negozio, ma alla capacità base è associata una efficace conversazione incorporata che
raccoglie un codice postale dall'utente e restituisce l'indirizzo del negozio più vicino. Per
trarre vantaggio dal comportamento incorporato, utilizzare la capacità base `Find nearest store`.

    - Anche le capacità relative alla sicurezza si sovrappongono. Per avere un'idea più
precisa di quali tipi di input dell'utente sono gestiti da ognuna, immettere queste espressioni
verbali di esempio nel riquadro Preview.

        - *Is my data protected?* viene instradato a `Security assurance`.
        - *Can I trust you with my information?* viene instradato a `#system_reliance`.

        La capacità `#system_reliance` dispone di dati di
addestramento più limitati rispetto alla capacità `Security assurance`, quindi
verrà utilizzata la capacità base invece di quella personalizzata.

    Per disabilitare una capacità personalizzata è necessario eliminarla dallo spazio
di lavoro di {{site.data.keyword.conversationshort}}.
    1. Dallo strumento {{site.data.keyword.conversationshort}}, espandere
l'intento `#goodbyes` nella pagina Intents, poi fare clic sull'icona
**Delete intent** per eliminarlo dallo spazio di lavoro.
    1. Espandere l'intento `#locate_amenity`, poi fare clic sull'icona
**Delete intent** per eliminarlo dallo spazio di lavoro.
    1. Espandere l'intento `#system_reliance`, poi fare clic sull'icona
**Delete intent** per eliminarlo dallo spazio di lavoro.

1. Dopo aver effettuato le modifiche allo spazio di lavoro personalizzato, automaticamente
viene eseguito un nuovo addestramento con i nuovi dati. Al completamento dell'addestramento,
tornare a {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}.

    Dalla pagina Configure, aprire la scheda **Custom
Capabilities** per confermare che le capacità rimosse (`#goodbyes`,
`#locate_amenity` e `#system_reliance`) non sono più elencate.

1. Le capacità `Greetings` e `#greetings`
si sovrappongono completamente. Si desidera che l'agent abbia un comportamento coerente e che
dimostri personalità. La capacità personalizzata `#greetings`
è stata progettata per rappresentare un tipo di personalità specifica che rispecchia il brand
aziendale, quindi sarà utilizzata la capacità personalizzata invece di quella base.

    Per disabilitare una capacità base, è necessario disattivarla.
    1. Dalla scheda **Core Capabilities** della pagina Configure di
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, individuare
la capacità `Greetings`.
    1. Fare clic sul riquadro per aprire la capacità e poi posizionare
l'interruttore su **Off**. Fare clic sulla freccia indietro per tornare alla
pagina di configurazione principale.

1. Eseguire ulteriori test immettendo domande dell'utente di prova nel riquadro Preview per
confermare che la capacità corretta stia gestendo l'input dell'utente come previsto. Ad
esempio, è possibile testare di nuovo le seguenti espressioni verbali:

    - *Can I trust you with my information?* deve essere gestito
dalla capacità `Security assurance`.
    - *find the nearest store* deve essere gestito dalla
capacità `Find nearest store`.

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

