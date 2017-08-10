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

# Creazione di un agent
{: #agent-create}

Quando si sottoscrive il servizio, viene fornito un bot con un pacchetto di capacità in
lingua inglese **General Customer Service (Servizio clienti generico)** abilitato. È possibile creare
ulteriori bot con altri pacchetti di capacità o bot che utilizzano una lingua di conversazione con i
clienti diversa dall'inglese.
{: shortdesc}

Per passare a utilizzare un agent con un pacchetto di capacità diverso come agent primario,
creare prima un nuovo agent con il pacchetto di capacità desiderato, quindi è possibile eliminare
l'agent che era stato fornito inizialmente. Assicurarsi di effettuare il passaggio prima di
spendere troppo tempo nella configurazione dell'agent General Customer Service (Servizio clienti generico). Per ulteriori
informazioni, vedere [Eliminazione di un agent](agent-create.html#delete).

Se si è impiegato del tempo per configurare un'istanza dell'agent nel modo giusto, e si
desidera distribuirla per l'uso ma essere ancora in grado di sperimentarla o provare nuovi
miglioramenti, è possibile clonare l'agent per creare una copia a scopo di test. Per
ulteriori dettagli, vedere [Clonazione di un agent](agent-create.html#clone).

## Limiti degli agent

Il numero di agent che è possibile creare dipende dal piano di servizio.

| Piano di servizio |      Numero di agent |
|------------------|----------------------:|
| Prova            |                     2 |
| Standard         |                    10 |
| Premium          |                   100 |

Tenere presente che le chiamate API effettuate da più bot distribuiti vengono sommate e
contate nel numero totale di risposte di agent virtuali assegnate alla sottoscrizione.

### Procedura

Eseguire queste operazioni per creare un agent.

1.  Dal menu principale ![Icona con tre linee orizzontali](images/hamburger.png), fare clic su **Create New Agent (Crea nuovo agent)**.

1.  Scegliere il tipo di pacchetto di capacità che deve essere fornito all'agent quando
viene creato.
   Il riquadro identifica le lingue supportate. Tuttavia, non tutte le capacità sono
disponibili in tutte le lingue. Fare clic sul link **View Details (Visualizza dettagli)** per visualizzare un elenco completo delle capacità supportate per lingua.

1.  Fare clic su **Select (Seleziona)** in un riquadro del pacchetto di
capacità per creare un nuovo agent fornito con tale tipo di pacchetto.

1.  Se applicabile, scegliere la lingua, e poi fornire le informazioni richieste per l'agent.
   >**Nota:** l'etichetta dell'agent specificata qui viene visualizzata solo
nello strumento di amministrazione di Watson Virtual Agent utilizzato per gestire l'agent. Questo
non è il nome dell'agent virtuale tipo che interagisce con gli utenti; il nome può essere
definito o modificato dalla pagina **Settings (Impostazioni)**.

1.  Fare clic su **Create (Crea)**.

## Clonazione di un agent
{: #clone}

Clonare un agent per creare un nuovo agent con la stessa configurazione e impostazioni dell'originale. Dopo aver clonato l'agent, l'originale e il clone non sono più legati tra loro. Le modifiche
apportate a uno **non** sono applicate all'altro.

Non è possibile creare un clone di un agent in una lingua diversa dalla lingua dell'originale.

### Procedura

Eseguire queste operazioni per creare un agent.

1.  Aprire la pagina **Settings (Impostazioni)** dell'agent da clonare.

1.  Scorrere verso il basso e poi fare clic su **Clone Agent (Clona agent)**.

1.  Fornire le informazioni richieste per l'agent.
   >**Nota:** l'etichetta dell'agent specificata qui viene visualizzata solo
nello strumento di amministrazione di Watson Virtual Agent utilizzato per gestire l'agent. Questo
non è il nome dell'agent virtuale tipo che interagisce con gli utenti; il nome viene definito
altrove.

1.  Fare clic su **Clone (Clona)**.

## Eliminazione di un agent
{: #delete}

Se un agent non viene utilizzato, eliminarlo in modo da non continuare a conteggiarlo nel
limite del numero di agent.

### Procedura

Eseguire queste operazioni per creare un agent.

1.  Aprire la pagina **Settings (Impostazioni)** dell'agent da eliminare.

1.  Scorrere verso il basso e poi fare clic su **Delete Agent (Elimina agent)**.

1.  Quando richiesto, immettere il testo `delete`, e poi fare clic su
**OK**.
