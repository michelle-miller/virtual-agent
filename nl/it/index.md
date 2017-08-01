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

# Panoramica
{: #index}

{{site.data.keyword.virtualagentfull}} è un insieme di componenti cognitivi
pre-configurati basati sul servizio {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Configurando
l'agent virtuale con le informazioni della propria azienda, è possibile implementare rapidamente
un bot di chat automatizzata che dialoga con i clienti per aiutarli a raggiungere gli obiettivi.
{: shortdesc}

{{site.data.keyword.watson}}&trade; {{site.data.keyword.virtualagentshort}} fornisce i seguenti componenti:

- Uno strumento di configurazione che può essere utilizzato per configurare il modo in cui
il bot risponde a diversi tipi di richieste.
- Un insieme di capacità che rappresentano gli obiettivi comuni o le azioni che i
clienti generalmente desiderano eseguire (ad esempio "Paga la mia fattura" o "Dimmi l'orario di
apertura").
- Un modello di linguaggio naturale addestrato ad identificare gli intenti in base all'input
del cliente.
- Un flusso di dialogo della conversazione che può gestire alcune richieste complesse
richiedendo ulteriori informazioni, generare risposte e attivare gli eventi che devono essere
gestiti dalla propria applicazione. Se il dialogo pre-definito non soddisfa le esigenze, è possibile
implementare un proprio dialogo personalizzato utilizzando gli strumenti del servizio {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}}.
- Un meccanismo di incremento delle capacità dell'agent con capacità personalizzate che vengono definite nello spazio di lavoro di
{{site.data.keyword.conversationshort}} e collegate all'agent.
- Un widget di chat che può essere integrato nella proprio pagina web, e un SDK  che può
essere utilizzato per sviluppare un widget di chat personalizzato.
- Una serie di API che possono essere utilizzate per integrare la propria applicazione con
l'agent virtuale.

## Panoramica dell'architettura
{: #arch_overview}

Il diagramma seguente illustra l'architettura di una implementazione
di {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} tipica:

![Panoramica dell'architettura](images/arch-overview.png)

L'implementazione include i seguenti componenti principali:

- Servizio **{{site.data.keyword.conversationshort}}**

    Un'istanza del servizio {{site.data.keyword.watson}}
{{site.data.keyword.conversationshort}}. Il servizio
{{site.data.keyword.conversationshort}} fornisce le risorse per le capacità: intenti,
entità e flusso di dialogo, insieme all'elaborazione cognitiva sottostante che potenzia le capacità
del bot di chat. L'utente interagisce direttamente con lo spazio di lavoro {{site.data.keyword.conversationshort}}
solo quando desidera implementare un dialogo personalizzato o una capacità personalizzata.

    Per ulteriori informazioni su intenti e dialoghi, fare riferimento alla
[documentazione
del servizio {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

- **Bot**

    Un bot basato sul servizio {{site.data.keyword.conversationshort}}, che include
una serie di capacità. Il bot è addestrato a riconoscere le richieste degli utenti relative al
coinvolgimento dei clienti, ad esempio richieste di informazioni generali sull'azienda o
pagamento di una fattura. Lo strumento di configurazione del bot fornito consente di
configurare informazioni specifiche dell'azienda, che possono essere fornite in risposta a domande
dell'utente, e di configurare le risposte per ogni capacità.

- **Sito web aziendale**

    L'applicazione aziendale che si interfaccia con i clienti, che gestisce le
comunicazioni con il bot {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} e con il proprio sistema di registrazione (ad
esempio database dei clienti o sistemi di fatturazione).

- **Finestra di chat**

    L'interfaccia di chat dell'agent virtuale, che i clienti utilizzano per conversare con il
bot. È possibile utilizzare il widget di chat fornito, con o senza personalizzazione, oppure è
possibile utilizzare il SDK client per implementare un proprio widget di chat.

