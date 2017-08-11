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

# Implementazione delle capacità base 
{: #impl_intents}

Comprendere le attività di sviluppo che devono essere completate per supportare i tipi di
risposta selezionati per alcune capacità.
{: shortdesc}

Considerare come si desidera gestire le seguenti capacità, come minimo:

- ***None of the above (Nessuna delle precedenti)***

    La risposta definita per questa capacità viene restituita agli utenti ogni
volta che immettono un input che il sistema non riesce a riconoscere e associare a una
capacità abilitata. Di conseguenza, può essere visualizzato agli utenti molto spesso,
specialmente se non sono state attivate molte capacità. Valutare quale dovrebbe essere la
risposta dell'agent virtuale. Una risposta di testo, ad esempio *Mi dispiace. Non
capisco la domanda.* è sufficiente. Se si desidera che gli utenti abbiano la possibilità di
contattare un agent umano, è possibile includere il testo, *Immettere 'operatore'
per essere trasferiti a un operatore.* Questo input attiva l'evento `agent`,
che viene spiegato di seguito. Per ulteriori informazioni, vedere
[Utilizzo di None of
the above (Nessuna delle precedenti)](impl_intents.html#none-of-the-above).

- **La capacità *Connect to agent (Metti in contatto con l'operatore)* e tutte le capacità con tipo di risposta *Transfer to human agent (Trasferire a un agent umano)***

    Queste capacità trasferiscono l'utente a un agent umano. È necessario aggiungere la
logica che trasferisce la conversazione al personale di supporto. Un approccio potrebbe essere di
aggiungere la logica che connette a un servizio esterno che è già utilizzato per gestire le
richieste in entrata sul sito del supporto clienti. I problemi che l'agent virtuale non può
risolvere possono essere trasferiti al personale di supporto come parte di una coda
di richieste di supporto esistente, per l'assegnazione della priorità e la risoluzione. Per
implementare la logica di trasferimento, attendere l'evento `agent` e
definire le funzioni da svolgere quando l'evento viene attivato. Per esempi vedere [dwAnswers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/search.html?f=&amp;type=question&amp;redirect=search/search&amp;q=watson-virtual-agent&amp;q=human "Icona link esterno"){: new_window}.

- **Capacità con tipo di risposta *Built-in (Incorporata)***

    Se si mantengono le impostazioni predefinite per le capacità base configurate
per utilizzare il tipo di risposta Use built-in conversation (Utilizzare conversazione incorporata), e queste capacità sono
abilitate, è necessario aggiungere una logica per supportare lo scambio di informazioni e le
transazioni commerciali gestite dalle conversazioni incorporate. Per ulteriori dettagli, vedere
[Implementazione della logica per il supporto
della conversazione incorporata](impl_intents.html#backend_transaction).

- **Capacità con tipo di risposta *Use your own conversation (Utilizzare una propria conversazione)***

    Per capacità complesse che richiedono un dialogo personalizzato per gestire lo
scambio di informazioni con l'utente, è possibile scrivere un dialogo utilizzando il servizio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Per
ulteriori dettagli, vedere [Aggiunta di dialoghi
personalizzati per le capacità base](add-custom-dialog.html).

## Implementazione della logica per il supporto della conversazione incorporata 
{: #backend_transaction}

Informazioni sullo scambio di informazioni e il completamento dei processi di business avviati quando gli utenti interagiscono con le capacità che sono configurate per utilizzare una conversazione incorporata.

### Informazioni su questa attività

Alcune delle capacità base configurate per utilizzare il tipo di risposta
conversazione incorporata, per impostazione predefinita possono occuparsi dei processi di business. L'applicazione deve essere in grado di registrare la transazione con i sistemi di backend di
registrazione.

- Se si implementa il widget di chat {{site.data.keyword.IBM_notm}} fornito, questo
riconosce gli eventi attivati da determinate risposte dell'utente. Tuttavia, ci sono ulteriori
operazioni da eseguire perché l'applicazione resti in attesa di questi eventi, in modo da poter
completare le transazioni attivate nei sistemi di backend.
- Se non si utilizza il widget di chat fornito, è necessario assicurarsi che l'interfaccia
utente personalizzata possa riconoscere gli eventi attivati dai flussi di conversazione incorporati
e li gestisca in modo appropriato.

Vedere il [flusso di dialogo Make a
payment (Effettua un
pagamento)](backend_payment_gif.html#backend_payment_gif) per avere un esempio di come sono archiviate le variabili private relative alla
carta di credito.

Ad esempio, con la capacità **Update address (Aggiorna indirizzo)**, un utente può
modificare l'indirizzo di fatturazione sul proprio account. È necessario scrivere un codice che
acquisisce il nuovo indirizzo dall'agent virtuale e aggiorna l'account dell'utente nel sistema di
registrazione con le nuove informazioni.

È importante notare che lo scopo di un dialogo è solo di raccogliere le informazioni
dall'utente. Le informazioni fornite dall'utente sono memorizzate in due modi:

- Le informazioni che non contengono dati sensibili o personali sono memorizzate nel
contesto del dialogo, che è un oggetto dati disponibile per il bot e per l'applicazione.
- Le informazioni che contengono dati sensibili o personali (ad esempio numeri di carta di
credito) sono memorizzate in variabili private, che sono disponibili solo per l'applicazione e non
sono passate al bot.

### Procedura

Per implementare completamente le transazioni di business attivate dalle
capacità con risposte di conversazioni incorporate, completare i seguenti passi:

1.  Aggiungere la logica all'applicazione che acquisisce le informazioni del profilo per
l'utente corrente dal sistema di backend per mostrarle nella finestra di chat prima di modificare
le informazioni. Ad esempio, mostra agli utenti il saldo prima del pagamento.

    Utilizzare l'azione `getUserProfileVariables`. Questa azione
acquisisce le variabili e le imposta nel profilo.

    ```java
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     var variables = data.message.action.args.variables; // specify the variables you want to get in this array
       for (var i = 0; i < variables.length; i++) {
           var value = something(variables[i])
           /*do something to get the value of variables[i]. might be an ajax call or getting
           data from local cookies. Depends on where you stored the information.*/
           window.IBMChat.profile.set(variables[i], value);
       }
       IBMChat.sendSilently('success'); // or cancel or failure
    });
    ```
    {: screen}

    Questo esempio utilizza una chiamata REST per ottenere informazioni sul saldo di una
fattura e la data di scadenza.

    ```java
    var xmlHttp = new XMLHttpRequest();
      xmlHttp.onreadystatechange = function() {
        if (xmlHttp.readyState == 4 &&  xmlHttp.status == 200)
          callback(xmlHttp.responseText);
      }
      xmlHttp.open("GET", url, true);
      xmlHttp.send(null);
    }
    /* Get information from the backend database and add it
    into the profile with IBMChat.profile.set(). */
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     /*
     data = {
       message: {
          text: ['some text'],
                action: {
                     name: 'getUserProfileVariables',
                     args: {
                         variables: [
                    "bill_amount",
                    "payment_due_date"
                ]
                     }
                }
       }

     }
     */

     httpGetAsync('http://yourdomain.com/userprofile', function(user) {
       /* The record on the backend system might return information like this.
       user = {
         "bill_amount": 42.01,
         "payment_due_date": "11/24/2008"
       }
       */
       var variables = data.message.action.args.variables;
       for (var i = 0; i < variables.length; i++) {
         var value = user[variables[i]]);
         window.IBMChat.profile.set(variables[i], value);
       /* Now the chat widget can use the values it retrieved from the backend service. */
       }
       IBMChat.sendSilently('success'); // or cancel or failure
     });
    });
    ```
    {: screen}

 Aggiungere la logica all'applicazione che prima attende l'azione che avvia il processo di
business, e poi esegue il processo di business.

    Per un elenco delle azioni associate a capacità che hanno tipi di risposta con
conversazione incorporata, vedere
[https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action
![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action "Icona link esterno"){: new_window}.

#### Make a payment (Effettua un pagamento)
{: #makeapayment}

Effettuare le seguenti operazioni per implementare il codice che supporta questa
transazione.
1.  L'applicazione deve richiamare il saldo corrente dell'utente e la data di
scadenza dal sistema di backend. Utilizzare il metodo
`action:getUserProfileVariables` per acquisire e impostare le variabili
`bill_amount` e `payment_due_date` nell'archivio dei profili.
1. L'applicazione deve restare in attesa dell'evento `payBill` e
definire la logica da eseguire quando l'evento viene attivato.
1. L'applicazione deve anche restare in attesa dell'evento
`sendPaymentReceipt` e definire la logica da eseguire quando l'evento viene
attivato.

#### Update address (Aggiorna indirizzo)
{: #updateaddress}

1. Il widget di chat utilizza un layout modulo per chiedere informazioni sul nuovo
indirizzo dell'utente e le archivia nel profilo automaticamente. Vengono archiviate queste variabili di
profilo:

    ```java
    user_street_address1
    user_street_address2
    user_locality
    user_state_or_province
    user_zipcode
    ```
    {: screen}

1.  L'applicazione deve restare in attesa dell'evento
`updateAddress`.

    ```java
    IBMChat.subscribe('action:updateAddress', function(data) {<your-code>}
    ```
    {: screen}

    Definire una funzione che acquisisce ed invia il nuovo indirizzo e tipo di
indirizzo (`address_type`) al sistema di backend quando viene attivata l'azione
`updateAddress`.

    Per raccogliere dati con molti valori, ad esempio un indirizzo postale, è
possibile utilizzare il layout modulo che viene generato nel widget di chat. Gli utenti immettono i
valori in più campi, e quindi inoltrano il modulo completo. Ad esempio, per inviare il nuovo
indirizzo al sito tramite una chiamata REST POST, è possibile utilizzare una logica simile alla
seguente.

    ```java
    /* When a user enters information into a form, it is automatically added
    to the user profile. So a typical flow would be to include a form layout in the
    chat window, and then call this action after the form is submitted */
    IBMChat.subscribe('action:updateAddress', function(data) {
      var record = {
        "first_name": IBMChat.profile.get('first_name'),
        "last_name": IBMChat.profile.get('last_name'),
        "user_street_address1": IBMChat.profile.get('user_street_address1'),
        "user_street_address2": IBMChat.profile.get('user_street_address2'),
        "user_locality": IBMChat.profile.get('user_locality'),
        "user_state_or_province": IBMChat.profile.get('user_state_or_province'),
        "user_zipcode": IBMChat.profile.get('user_zipcode')
      };
      httpPostAsync('/updateRecord/', record, function(err, response) {
        if (err) IBMChat.receive('There was an error updating the address.');
      });
    });
    ```
    {: screen}

    Per ulteriori informazioni sui layout incorporati, vedere [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout "Icona link esterno"){: new_window}.

#### Update contact phone number (Aggiorna il numero telefonico del contatto)
{: #updatephone}

1. Il widget di chat utilizza un layout modulo per chiedere il nuovo numero di
telefono dell'utente e lo archivia nel profilo automaticamente. Vengono archiviate queste variabili di
profilo:

    ```java
    user_phone_number
    phone_number_type
    ```
    {: screen}

1. L'applicazione deve restare in attesa dell'evento
`updatePhoneNumber` e definire la logica per acquisire e inviare il nuovo numero
di telefono e tipo al sistema di backend quando l'evento viene attivato.

#### Update email (Aggiorna indirizzo email)
{: #updateemail}

1. Il widget di chat utilizza un layout modulo per chiedere il nuovo indirizzo email
dell'utente e lo archivia nel profilo automaticamente. Vengono archiviate queste variabili di
profilo:

    ```java
    user_email_address
    email_type
    ```
    {: screen}

1. L'applicazione deve restare in attesa dell'evento `updateEmail`
e definire la logica per acquisire e inviare il nuovo indirizzo email al sistema di backend quando
l'evento viene attivato. Inoltre invia informazioni sui tipi di notifica per i quali utilizzare il
nuovo indirizzo (`email_type`).

## Utilizzo di None of the above (Nessuna delle precedenti)
{: #none-of-the-above}

Comprendere come la capacità **None of the above (Nessuna delle precedenti)**
viene utilizzata dall'agent virtuale.

A differenza di altre capacità base, la capacità **None of the
above (Nessuna delle precedenti)** non può essere disabilitata. Il motivo è che viene utilizzata come un
raccoglitore polivalente per tutte le espressioni verbali che non sono associate a nessuna delle
capacità configurate. Questa funzionalità è utile perché è possibile fornire una risposta
standard, ad esempio *Non posso esserti di aiuto*, per le richieste degli
utenti relative a capacità che non sono ancora disponibili per l'agent. Inoltre risponde alle domande
assurde che a volte i clienti fanno per gioco, quando iniziano a interagire per la prima volta con
l'agent, ad esempio *Cosa dovrei mangiare oggi a pranzo?*

A causa del suo ruolo univoco nel funzionamento dell'agent virtuale, è importante come si
configura questo comportamento. La capacità **None of the above (Nessuna delle precedenti)** viene
attivata spesso e in modi non sempre ovvi, tra cui:

- Quando si disabilita qualsiasi altra capacità base, le espressioni verbali che
attivano la capacità disabilitata sono instradate alla capacità **None of the above (Nessuna delle precedenti)**
per avere una risposta.
- Quando un'espressione verbale non corrisponde a nessuna delle capacità base
abilitate, viene passata alla capacità **None of the above (Nessuna delle precedenti)** per avere una
risposta. Se si fornisce uno spazio di lavoro collegato con le capacità personalizzate, sia lo
spazio di lavoro di base che lo spazio di lavoro personalizzato valutano l'espressione verbale per
trovare una corrispondenza. Se non viene trovata alcuna corrispondenza, viene utilizzata la
risposta associata alla capacità base **None of the above (Nessuna delle precedenti)**.
- È possibile configurare la capacità **None of the
above (Nessuna delle precedenti)** con un tipo di risposta **Use your own conversation (Utilizzare una propria conversazione)** e
collegarla a uno spazio di lavoro con un dialogo personalizzato. Quando per un'espressione verbale non si trova
nessuna corrispondenza di intento nello spazio di lavoro di base, l'espressione verbale viene
passata alla capacità **None of
the above (Nessuna delle precedenti)**, che la passa allo spazio di lavoro personalizzato per avere una risposta.
- Quando si scollega uno spazio di lavoro, se lo spazio di lavoro collegato è associato
alla capacità **None of the above (Nessuna delle precedenti)**, è necessario eseguire alcune azioni
prima di poter continuare a scollegare lo spazio di lavoro. Qualsiasi altra capacità associata
allo spazio di lavoro che si desidera scollegare viene automaticamente disabilitata. Ma, dal
momento che la capacità **None of the above (Nessuna delle precedenti)** non può essere
disabilitata, è necessario decidere un comportamento di risposta alternativo. Ad esempio, è
possibile modificare il tipo di risposta in **Text (Testo)** e
aggiungere un messaggio di testo da utilizzare nella risposta.
