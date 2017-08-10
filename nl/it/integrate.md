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

# Integrazione dell'agent
{: #integrate}

Per pubblicare l'agent per l'uso in produzione, è necessario effettuare ulteriori operazioni
per supportare le funzioni eseguite dall'agent e per renderlo disponibile agli utenti in modo
sicuro.
{: shortdesc}

## Scelta di un metodo di integrazione

È possibile integrare l'agent in uno dei seguenti modi:

- Aggiungere l'interfaccia di chat fornita da {{site.data.keyword.IBM_notm}} al
proprio sito web destinato ai clienti.
  Vedere [Aggiunta del widget di chat fornito alla propria UI](integrate_add-chat.html).

- Estendere la finestra di chat fornita per personalizzarla in base alle esigenze.
  Vedere [Aggiunta del widget di chat fornito alla propria UI](integrate_add-chat.html).

- Creare una propria interfaccia di chat utilizzando il SDK client fornito.
  Vedere
[Creazione di una interfaccia di chat personalizzata](integrate_custom-chat.html).

- Aggiungere l'agent ad un canale di supporto esistente e utilizzare l'API per interagire
con l'agent tramite programma.
  Vedere [Aggiunta dell'agent a un
canale di supporto](integrate_backend.html).

### Prima di iniziare

Qualsiasi sia il metodo utilizzato per pubblicare l'agent per l'uso in produzione,
valutare se creare prima un clone dell'agent. L'esistenza di una copia dell'agent non integrata
consente di testare le modifiche o le aggiunte alla funzionalità nella copia di test, prima di
applicarle all'agent utilizzato in ambiente di produzione. Per ulteriori informazioni, vedere
[Clonazione dell'agent](agent-create.html#clone).
