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

# Aggiunta di agent a un canale di supporto esistente
{: #integrate_backend}

L'API di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}
è progettata per supportare una facile transizione di una conversazione tra l'agent virtuale e un
agent umano o altro servizio bot in un'infrastruttura di supporto esistente. In effetti, il team
di LivePerson Inc. ha lavorato come partner insieme a {{site.data.keyword.IBM}} per implementare
questa integrazione. Per ulteriori dettagli, vedere
[Integrazione con LiveEngage](integrate_backend.html#liveperson) di seguito.
{: shortdesc}

Per creare da soli una soluzione semplice, è possibile codificare l'applicazione in modo che
le capacità configurate per essere trasferite a un agent umano siano trasferite a un canale
esistente monitorato dal personale del supporto. Per informazioni sul trasferimento di una
conversazione a Slack, ad esempio, vedere
[dW
Answers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/318623/where-can-i-find-documentation-examples-on-integra/ "Icona link esterno"){: new_window}.

Per utilizzare l'API di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} per integrare l'agent virtuale in un canale di
supporto esistente, completare i passi seguenti:

1.  Richiamare le chiavi API necessarie per effettuare le chiamate API. Per i dettagli,
vedere [Acquisizione delle chiavi API](publish.html#api-keys).

1.  Utilizzare le API REST di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} per interagire con il bot da
programma. Andare al portale
**[{{site.data.keyword.IBM_notm}}
developerWorks API Explorer](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window} per accedere alle API REST su {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}.

1.  Per ottenere l'ID bot, effettuare una delle seguenti operazioni:
    - Per ottenere l'ID bot dall'interfaccia utente dello strumento di configurazione di
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, completare i
seguenti passi:
      1.  Dal menu principale ![Icona con tre linee orizzontali](images/hamburger.png)
di {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, fare clic
su **Documentation (Documentazione)** e poi sulla scheda **Publish (Pubblica)**.
      1.  Copiare il valore botID dal blocco dello script.

    - Per ottenere l'ID bot dal sito web API Explorer, seguire questa procedura:
      1.  Accedere a [IBM developerWorks API
Explorer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/api/ "Icona link esterno"){: new_window}. Fare
clic su **My APIs (Le mie API)**, e poi sul riquadro {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}}.
      1.  Fare clic su **Documentation > Retrieve Bot (Documentazione > Richiama bot)** nella barra di navigazione.
      1.  Fare clic su **USE (Usa)** nella parte superiore della
finestra di riferimento API explorer.
      1.  Scorrere verso il basso sotto la sezione *Path and Query parameters (Percorso e parametri di query)* e fare clic su **TEST**.
      >**Nota:** è necessario selezionare una chiave da utilizzare con l'API
prima di poter eseguire il test.

      1.  L'ID bot viene visualizzato nel parametro `bot_id` nella
risposta ricevuta.

## Integrazione con LiveEngage
{: #liveperson}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} è
progettato per operare in sintonia con le controparti umane.

Ad esempio, LivePerson Inc., un fornitore di soluzioni di messaggistica di business online
e mobili su cloud, ha collaborato con IBM per incorporare un bot di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} nell'esperienza di chat di LiveEngage. **LiveEngage**
è una piattaforma a livello aziendale basata su cloud che consente ai clienti di scambiare
messaggi con i brand preferiti direttamente. La nuova offerta, **LiveEngage
with Watson**, aggiunge le risposte da un bot di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} all'interazione, con l'intervento dei rappresentanti
del supporto in tempo reale, senza soluzione di continuità, solo quando necessario.

Il bot LivePerson utilizza molti dei comportamenti offerti da
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} indicati di
seguito:

- Accettare le conversazioni che sono instradate dal servizio esterno.
- Attivare il trasferimento di conversazioni al servizio esterno nelle seguenti condizioni:
    - Il cliente chiede di parlare con una persona.
    - Una capacità è stata configurata per essere instradata a un agent umano.
    - Il cliente chiede informazioni su un argomento che il bot non è progettato per riconoscere e
rispondere.
- Identificare e riportare il punto della conversazione in cui l'utente ha smesso di comprendere
il bot o ha perso interesse nella conversazione.
- Riconoscere quando una conversazione termina e inviare una notifica al servizio per
consentire l'inizio di eventuali attività post-interazione.
- Quando si trasferisce una conversazione, includere informazioni sull'intento dell'utente
in modo che la conversazione possa essere instradata all'agent umano con maggiore esperienza nel
rispondere a richieste di quel tipo.
- Quando si trasferisce una conversazione, includere la cronologia di chat, in modo che la
persona a cui viene passato il problema comprenda il contesto della conversazione avvenuta fino a
quel momento.

Per richiedere l'accesso all'offerta, vedere il
[sito
web LivePerson ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://engage.liveperson.com/usage/watson/?utm_medium=website&utm_source=IBM&utm_campaign=Watson "Icona link esterno"){: new_window}.
