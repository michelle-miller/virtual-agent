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

# Integrazione dell'agent con l'interfaccia utente dell'applicazione
{: #integrate}

Per integrare il client front-end di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} con la propria applicazione, è possibile aggiungere
l'interfaccia di chat fornita da {{site.data.keyword.IBM_notm}} direttamente al sito web
visualizzato dai clienti, estendere la finestra di chat fornita per personalizzarla in base
alle proprie esigenze o creare una propria interfaccia di chat.
{: shortdesc}

[Aggiunta del widget di chat fornito alla propria UI](/docs/services/virtual-agent/integrate.html#add_chat)

[Creazione di una interfaccia di chat personalizzata](/docs/services/virtual-agent/integrate.html#custom_chat)

## Aggiunta del widget di chat fornito alla propria UI
{: #add_chat}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}
viene distribuito con un widget di chat che può essere utilizzato direttamente nella propria
interfaccia utente.

### Informazioni su questa attività

Questo diagramma illustra il flusso della conversazione nel sistema quando si utilizza
il widget di chat fornito da {{site.data.keyword.IBM_notm}}.

![Mostra una configurazione standard in cui viene
utilizzato il widget di chat fornito.](images/builtin_chat_new.png)

### Procedura

1. Per utilizzare il widget fornito, aprire il repository GitHub del [widget di chat di {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/chat-widget){: new_window} e completare i passi indicati nel file `README.md`.

    Il widget di chat fornito può esser esteso. Se contiene elementi che si desidera
modificare, è possibile personalizzarli. Ad esempio, per modificare un layout utilizzato dal widget
di chat fornito, è possibile scrivere un layout personalizzato che lo sostituisce. Qui è disponibile
un esempio: [https://github.com/watson-virtual-agents/chat-widget/tree/1.2.12/examples/basic-custom-layout. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/chat-widget/tree/1.2.12/examples/basic-custom-layout){: new_window} Tenere
presente che il layout potrebbe essere utilizzato da più di un intento.

1. Per informazioni sulle operazioni da effettuare per supportare le transazioni del widget
di chat che possono essere richieste per le capacità che utilizzano la conversazione
incorporata, vedere [Implementazione della logica per il supporto della conversazione incorporata](/docs/services/virtual-agent/impl_intents.html#backend_transaction).

### Operazioni successive

Se l'estensione delle personalizzazioni che si desidera effettuare è così ampia che
risulta impossibile implementare le modifiche aggiornando il widget di chat fornito, è possibile
creare una propria interfaccia di chat.

## Creazione di una interfaccia di chat personalizzata
{: #custom_chat}

Se il widget di chat fornito non soddisfa le proprie esigenze, è possibile sviluppare la
propria interfaccia di chat JavaScript per consentire agli utenti di interagire con l'agent virtuale. In
questo modo si ha il controllo completo su layout, aspetto e comportamento dell'interfaccia di chat.

### Informazioni su questa attività

Questo diagramma illustra il flusso della conversazione nel sistema quando si fornisce
un'interfaccia di chat personalizzata.

![Mostra che il widget di chat IBM viene sostituito completamente da un'interfaccia utente personalizzata.](images/custom_ui_new.png)

### Procedura

Per sviluppare un'interfaccia di chat personalizzata con JavaScript, utilizzare le seguenti
risorse:

- **SDK client {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}**

    Un SDK JavaScript per lo sviluppo di applicazioni che interagiscono con
{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}. Il SDK
client utilizza un host [GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/client-sdk){: new_window}.

- **API Explorer**

    Un portale che fornisce accesso alle API REST di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} su {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}. È
possibile accedere alle API di {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} da
[{{site.data.keyword.IBM_notm}} developerWorks API Explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}.

