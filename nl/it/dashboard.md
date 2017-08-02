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

# Analisi dell'attività degli utenti
{: #dashboard}

La pagina Engagement Metrics contiene un dashboard con le visualizzazioni che consentono di accede agli approfondimenti dai data raccolti dall'agent virtuale.
{: shortdesc}

## Prima di iniziare

L'istanza di {{site.data.keyword.IBM_notm}}
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} deve essere
distribuita e gli utenti devono partecipare a conversazioni con l'agent virtuale per almeno 30
minuti prima che il dashboard disponga di dati da condividere.

## Informazioni su questa attività

Le metriche sulla pagina sono aggiornate ogni 30 minuti con i dati dalle conversazioni
avvenute tra l'agent virtuale e gli utenti. Forniscono approfondimenti su:

- Quante conversazioni avvengono
- Quanti utenti, nuovi o ricorrenti, sono coinvolti nelle conversazioni con l'agent virtuale
- Cosa vogliono fare i clienti o su cosa vogliono informazioni (in base a quali intenti
sono attivati più o meno spesso)

Le metriche consentono di individuare le aree in cui un lavoro aggiuntivo potrebbe
migliorare significativamente le prestazioni dell'agent virtuale:

- Confrontare gli argomenti comuni con gli intenti e le entità che il servizio è addestrato a riconoscere. Eventuali
divergenze consentono di rilevare nuovi intenti o una terminologia su cui istruire l'agent virtuale.
- Riesaminare gli intenti identificati come più frequenti prima che gli utenti chiedano
di parlare con un agent umano. Indagando sulle cause delle escalation è possibile    stabilire
l'ordine di priorità per gli intenti su cui concentrare gli sforzi di addestramento futuri. È
possibile determinare se le richieste dell'utente sono state fraintese, se al servizio manca
completamente un
intento comune, se le risposte associate a un intento devono essere migliorare e altro.

Le metriche possono anche consentire di pianificare l'assegnazione delle risorse di agent umani
in base ai dati sulle aree geografiche in cui l'utilizzo dell'agent virtuale è più o meno comune e
gli orari di picco delle conversazioni.

Le metriche analizzano i dati delle conversazioni a basso livello, concentrandosi sulle
risorse che comprendono le capacità:

- **Entità**

    Un'*entità* rappresenta un termine o oggetto che è rilevante
per un intento e che fornisce un contesto specifico per un intento. Ad esempio, un'entità potrebbe
essere rappresentata da una città in cui l'utente vuole trovare una sede aziendale o l'importo di
pagamento di una fattura. Nell'interfaccia utente, il nome di un'entità ha sempre come prefisso il
carattere `@`.

- **Intenti**

    Un *intento* rappresenta lo scopo dell'input di un utente. Ogni
capacità utilizza un classificatore di linguaggio naturale che può valutare le espressioni
verbali dell'utente e individuare un intento predefinito, se presente. Nell'interfaccia utente, il nome di
un intento ha sempre come prefisso il carattere `#`.

## Procedura

1. Aprire la pagina **Engagement Metrics**.

    Nella parte superiore della pagina è presente un riepilogo dei punti di dati chiave e
sono illustrate le motivazioni delle azione dell'agent virtuale. Per ogni punto di dati, la
percentuale di modifica avvenuta nel periodo di tempo selezionato viene mostrata tra parentesi. Viene
visualizzato (N/A) per *non disponibile* fino a quando il periodo di tempo non
è trascorso, ed è possibile misurare e visualizzare una modifica.

    I numeri mostrati nel riepilogo a volte possono essere diversi da quelli mostrati
in altre pagine. Ad esempio, il numero totale di interazioni visualizzate qui potrebbe essere
diverso dal totale mostrato nelle scheda **Interactions**. La differenza può
esistere perché le informazioni di riepilogo sono aggregate e aggiornate ad intervalli di 30
minuti, mentre la scheda **Interactions** è aggiornata in tempo reale.

    Per ulteriori informazioni eseguire il drill-down nei dati su ogni scheda.
    - **<b>Overview**</b>

        Scoprire cosa gli utenti vogliono fare o cosa vogliono sapere quando entrano in
contatto con l'agent virtuale e quali obiettivi dell'utente l'agent virtuale non è riuscito a
soddisfare.
        - Il diagramma interattivo **Intents &amp; Entities**
fornisce un approfondimento sulle modalità con cui il servizio {{site.data.keyword.conversationshort}}
interpreta l'input dell'utente. Il diagramma mostra quali entità sono state utilizzate dal
servizio per consentire di identificare l'intento dell'utente.

            La seguente sintassi è utilizzata per facilitare una più rapida interpretazione
delle informazioni nel diagramma:
            - `#<nome-intento>`
            - `@<nome-entità>`

            Fare clic su un intento per visualizzare quali entità hanno consentito al
servizio di comprendere l'input dell'utente. Oppure fare clic su un'entità per visualizzare di quali
intenti ha consentito l'identificazione da parte del servizio.

        - Il grafico **Topics** cattura le parole o frasi pronunciate più
spesso dagli utenti nella conversazione. Esaminare il grafico per comprendere su cosa gli
utenti sono più interessati a parlare. Le parole in questo grafico sono distinte dalle entità
catturate nel diagramma Intents &amp; Entities. Le entità sono parole che il servizio
{{site.data.keyword.conversationshort}} è stato addestrato a comprendere e ad associare a
particolari intenti. Le parole che sono catturate nel grafico Topics sono semplicemente parole che
sono presenti più spesso nelle conversazioni. Potrebbe esserci una sovrapposizione dei due, ma
anche non esserci. Tenere sotto controllo le parole nel grafico Topics per essere sincronizzati con
i propri utenti, e rilevare nuovi argomenti di cui gli utenti vogliono parlare e nuove cose da fare. Gli
argomenti popolari, e che rimangono popolari, potrebbero essere buoni candidati per nuove entità che
possono consentire a {{site.data.keyword.watson}} di riconoscere gli intenti
esistenti o potrebbero suggerire nuovi intenti per i quali addestrare {{site.data.keyword.watson}}.

    - **<b>Users**</b>

        Ottenere informazioni su dove si trovano gli utenti e sul volume di conversazioni.

    - **<b>Interactions**</b>

        Esaminare le trascrizioni di singole conversazioni.

        Le trascrizioni non contengono informazioni personali. Anche il nome dell'utente
che hanno partecipato a una conversazione viene mantenuto privato; al suo posto viene
utilizzato *Not Provided*. Altre informazioni personali che gli utenti
forniscono durante la conversazione, ad esempio numeri di telefono o codici postali, sono
sostituite da variabili che indicano i tipi di dati forniti, non i dati stessi.

        > **Nota:** il termine *interazione* rappresenta una
conversazione che avviene tra l'utente e l'agent virtuale. L'interazione inizia quando l'utente
avvia la chat con l'agent virtuale e termina quando termina la sessione della finestra di chat
(questo avviene quando l'utente si scollega, viene scollegato, chiude la finestra o aggiorna la
finestra di chat). Un'interazione spesso include più di un semplice scambio di parole; gli utenti
possono fare clic su pulsanti, visualizzare immagini (ad es. mappe) e eseguire altre
transazioni. A differenza di una telefonata al supporto clienti, l'interazione con la sessione
di chat dell'agent non termina fino a quando non l'utente non termina il contatto. L'agent
virtuale resta disponibile nel caso in cui l'utente voglia fare o chiedere altro. Ad esempio, se
l'utente chiede qualcosa, e dopo 20 minuti chiede qualcos'altro (e lo fa nella stessa sessione
della finestra di chat), entrambi gli scambi sono trattati come una singola
interazione con una durata di circa 25 minuti.
1. Se si rilevano dati significativi che si desidera condividere con altri, è possibile
esportarli in formato CSV.

