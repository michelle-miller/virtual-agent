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

# Pubblicazione dell'agent a scopo di demo
{: #publish}

In meno di 10 minuti, è possibile pubblicare l'agent in un sito di test per condividerlo con
i colleghi e valutare insieme se soddisfa le esigenze dell'organizzazione.
{: shortdesc}

Per pubblicare l'agent in un sito di test, completare la seguente procedura:

1.  Determinare dove deve essere visualizzata la finestra di chat del bot sulla pagina. Nell'elemento HTML `<div>`
che definisce l'area di destinazione, aggiungere un attributo ID se non ne è stato definito uno. L'attributo
ID verrà utilizzato successivamente per fare riferimento all'elemento. Ad esempio, `<div id="ibm-chat-root"></div>`.

1.  Seguire le istruzioni in [Acquisizione delle chiavi API](publish.html#api-keys)
per richiamare le seguenti chiavi:
    - Client ID
    - Client secret token

1.  Dal menu principale ![Icona con tre lineeorizzontali](images/hamburger.png), fare clic su **Documentation (Documentazione)**, e poi

scorrere verso il basso fino alla sezione **Publish (Pubblica)**.

1.  Se sono presenti più agent, fare clic sulla freccia verso il basso per ottenere l'ID bot
per l'agent da pubblicare.

    Questo ID bot è l'ID generato dal servizio e assegnato al bot.

    Viene generato un blocco script che viene visualizzato nella pagina. Questo script può
essere copiato e posizionato in un pagina HTML per il rendering dell'agent nella pagina. È
necessario sostituire alcuni valori nello script con i valori appropriati per l'istanza in uso.

1.  Copiare il blocco script e incollarlo in un editor di testo o HTML.

    ``` Javascript
    <script src='https://unpkg.com/@watson-virtual-agent/chat-widget@1.6.0/dist/chat.min.js'>
    </script>
    <script>
      IBMChat.init({
        el: 'ibm_chat_root',
        baseURL: 'https://api.ibm.com/virtualagent/run/api/v1',
        botID: 'YOUR_BOT_ID',
        XIBMClientID: 'YOUR_IBM_CLIENT_ID',
        XIBMClientSecret: 'YOUR_IBM_CLIENT_SECRET'
      });
    </script>
    ```

1.  Sostituire i seguenti valori di attributo:
    - **el**: specificare l'ID dell'elemento scelto nel passo 1.
    - **XIBMClientID**: aggiungere il valore di ID client copiato in
precedenza.
    - **XIBMClientSecret**: aggiungere il valore del token segreto client copiato in
precedenza.

   Utilizzare i valori di baseURL e botID specificati nello script; questi sono generati dal
servizio.

   **Importante:** mantenere riservati i valori di XIBMClientID e
XIBMClientSecret.

1.  Incorporare e inizializzare il widget di chat Watson Virtual Agent incollando lo script
modificato nella propria pagina web.

   Aggiungere lo script il più vicino possibile alla tag `</body>` per
impedire che lo script blocchi il rendering del resto della pagina. Questa collocazione assicura
anche che il rendering di tutti gli elementi associati allo script sarà eseguito completamente
nel momento in cui viene eseguito lo script.

1.  Aggiornare la pagina web e fare una prova dell'agent.

   Il widget di chat è associato e sottoposto a rendering con l'elemento HTML indicato al
passo 1. È possibile nascondere o mostrare e posizionare tale elemento. Il widget si estende
all'intera altezza e larghezza dell'elemento. La larghezza massima è 768 pixel e l'altezza minima è
300 pixel.

Quando si è pronti per
rendere operativo l'agent per i clienti, è necessario eseguire alcune operazioni aggiuntive. Per
ulteriori dettagli, vedere [Integrazione dell'agent](integrate.html).

## Acquisizione delle chiavi API
{: #api-keys}

Per dimostrare che si dispone dell'autorizzazione per utilizzare i servizi API di Watson Virtual Agent, le seguenti chiavi devono essere associate a tutte le chiamate API al servizio:

- Client ID
- Client secret token

Utilizzare questa procedura per richiamare le credenziali.

1.  Andare al sito web [IBM developerWorks API
Explorer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/api/ "Icona link esterno"){: new_window} e accedere con lo stesso ID IBM che è stato utilizzato
per registrarsi alla sottoscrizione del servizio. Creare un nome utente se necessario. Fare clic
sul link **My APIs (Le mie API)** nell'intestazione della pagina.

1.  Individuare il riquadro di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} e poi fare clic sull'icona chiave associata ad esso.

1.  Se non è selezionata, selezionare la chiave che si desidera utilizzare. Per la chiave
vengono generate due credenziali, mostrate con i relativi valori oscurati nei due campi. Passare
con il mouse sui campi.

1.  Fare clic sul pulsante **SHOW (Mostra)** per rimuovere
l'oscuramento dai valori dei campi.

1.  Sarà necessario fornire questi valori successivamente, quindi si consiglia di copiarli
in un file di testo.
    - Il primo campo contiene la chiave ID client.
    - Il secondo campo contiene il token segreto client.

  ![Aggiungi nodo](images/api-explorer.jpg)
