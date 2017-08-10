---

Copyright:
Jahre: 2015, 2017
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

# Integrieren des Agenten
{: #integrate}

Um den Agenten für die produktive Nutzung zu veröffentlichen, müssen Sie weitere Schritte ausführen, um die vom Agenten durchgeführten Funktionen zu unterstützen und ihn auf sichere Weise für die Benutzer verfügbar zu machen.
{: shortdesc}

## Auswählen eines Integrationsverfahrens

Es gibt folgende Möglichkeiten, den Agenten zu integrieren:

- Fügen Sie die von {{site.data.keyword.IBM_notm}} bereitgestellte Chatschnittstelle unverändert zu Ihrer Website für Kunden hinzu. Siehe [Hinzufügen des bereitgestellten Chat-Widgets zu Ihrer Benutzerschnittstelle](integrate_add-chat.html).

- Erweitern Sie das bereitgestellte Chatfenster, um es Ihren Bedürfnissen entsprechend anzupassen. Siehe [Hinzufügen des bereitgestellten Chat-Widgets zu Ihrer Benutzerschnittstelle](integrate_add-chat.html).

- Erstellen Sie Ihre eigene Chatschnittstelle mithilfe des bereitgestellten Client-SDK.
  Siehe [Erstellen einer benutzerdefinierten Chatschnittstelle](integrate_custom-chat.html).

- Fügen Sie den Agenten zu einem bestehenden Supportkanal hinzu und verwenden Sie die API, um mit dem Agenten über das Programm zu interagieren. Siehe [Hinzufügen eines Agenten zu einem Supportkanal](integrate_backend.html).

### Vorbereitung

Unabhängig davon, welches Verfahren Sie verwenden, um den Agenten für die produktive Nutzung zu veröffentlichen, sollten Sie den Agenten im Vorfeld klonen. Mit einer nichtintegrierten Kopie des Agenten können Sie anhand der Testkopie Änderungen oder Funktionsergänzungen testen, bevor Sie diese auf den Agenten anwenden, der in einer Produktionsumgebung verwendet wird. Weitere Informationen finden Sie unter [Klonen des Agenten](agent-create.html#clone).
