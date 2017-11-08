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

# Verlinken von Arbeitsbereichen 
{: #link_workspace}

Bevor Sie eine benutzerdefinierte Funktion oder einen benutzerdefinierten Dialog mit einer zentralen Funktion verwenden können, müssen Sie eine Verbindung zwischen dem virtuellen Agenten und dem Arbeitsbereich des {{site.data.keyword.conversationshort}}-Service, der die gewünschten Artefakte enthält, herstellen.
{: shortdesc}

## Informationen zu Arbeitsbereichen

Ein Arbeitsbereich ist ein {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service-Container, der Absichten, Entitäten und einen Dialog enthält. Dies sind Artefakte, mit denen ein Konversationsfluss definiert und trainiert wird. Ihr Agent kann Artefakte aus diesem Arbeitsbereich verwenden, einschließlich trainierter Absichten und eines Dialogs, da er mit Ihren Kunden interagiert, um den Bereich der Dinge anzupassen und zu erweitern, die er besprechen kann.

Sie können Arbeitsbereiche verlinken, um folgende Ziele zu erreichen:

- Definieren Sie Ihre eigenen Funktionen: Der Arbeitsbereich muss Absichten, beispielhafte Äußerungen und einen Dialog mit Knotenbedingungen enthalten, die allen definierten Absichten entsprechen.
- Definieren Sie einen benutzerdefinierten Dialog für eine zentrale Funktion: Der Arbeitsbereich muss einen Dialog mit einer Knotenbedingung enthalten, die mit dem Absichtsnamen für eine zentrale Funktion übereinstimmt.

Sie *können* in demselben Arbeitsbereich benutzerdefinierte Funktionen und benutzerdefinierte Dialoge für zentrale Funktionen hinzufügen. Die Verwaltung von Dingen gestaltet sich jedoch einfacher, wenn Sie einen einzelnen dedizierten Arbeitsbereich für die Definition benutzerdefinierter Funktionen erstellen, die Sie verwenden möchten, und mindestens einen separaten Arbeitsbereich für die Definition der als Antworten auf zentrale Funktionen zu verwendenden Dialoge. Wenn Sie für beides denselben Arbeitsbereich verwenden möchten, müssen Sie sicherstellen, dass alle Knoten mit benutzerdefinierten Dialogen für bestimmte zentrale Funktionen im oberen Bereich der Dialog-Baumstruktur hinzugefügt werden, um zu verhindern, dass Äußerungen falsch zu benutzerdefinierten Funktionen weitergeleitet werden.

### Verfahren

1.  Öffnen Sie die Seite **Linked Workspaces (Verlinkte Arbeitsbereiche)** für den aktuellen Agenten.
1.  Klicken Sie auf **Link Workspace (Arbeitsbereich verlinken)**.

    Geben Sie Ihre {{site.data.keyword.Bluemix_notm}}-Kontoberechtigungsnachweise an, um {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} eine Berechtigung für den Zugriff auf Ihre Instanz des {{site.data.keyword.conversationshort}}-Service und das Abrufen von Informationen aus dem Arbeitsbereich zu erteilen.

1.  Wählen Sie die Instanz des {{site.data.keyword.conversationshort}}-Service aus, die die gewünschten Arbeitsbereiche enthält.
1.  Wählen Sie mindestens einen Arbeitsbereich aus, den Sie mit Ihrem Agenten verlinken möchten.
1.  Klicken Sie auf **Link workspaces (Arbeitsbereiche verlinken)**.

[Erstellen eines benutzerdefinierten Dialogs](add-custom-dialog.html)

[Hinzufügen Ihrer eigenen Funktionen](add-custom-capabilities.html)

## Aufheben der Verknüpfung von Arbeitsbereichen 
{: #unlink_workspace}

Wenn Sie die Verbindung zwischen Ihren virtuellen Agenten und einem bestimmten {{site.data.keyword.conversationshort}}-Arbeitsbereich nicht beibehalten möchten, können Sie die Verknüpfung des Arbeitsbereichs aufheben.

### Vorbereitung

Stellen Sie sicher, dass der Arbeitsbereich, dessen Verknüpfung Sie aufheben möchten, nicht aktiv von einer Funktion verwendet wird, für die dieser Arbeitsbereich erforderlich ist. Vergessen Sie nicht, dass ein Arbeitsbereich, der mit dem virtuellen Agenten verlinkt ist, für jede Funktion zur Verwendung zur Verfügung steht, die diesem Agenten zugeordnet ist; dies kann eine benutzerdefinierte Funktion oder eine zentrale Funktion sein.

### Informationen zu dieser Aufgabe

Wenn Sie die Verknüpfung eines Arbeitsbereichs mit einer Funktion aufheben, wird die Funktion automatisch inaktiviert. Durch die Inaktivierung der Funktion wird sichergestellt, dass aktive Benutzer keinem unerwarteten Verhalten ausgesetzt werden, während Sie Änderungen vornehmen. Dieses Konzept gilt für alle Funktionen bis auf die Funktion **None of the above (Keines der Obigen)**, die nicht inaktiviert werden kann. Sie müssen den Antworttyp bei dieser Funktion von **Use your own conversation (Eigene Konversation verwenden)** in eine der anderen Optionen für Antworttypen ändern, bevor Sie die Verknüpfung eines Arbeitsbereichs aufheben, der dieser Funktion zugeordnet ist.

### Verfahren

1.  Öffnen Sie die Seite **Linked Workspaces (Verlinkte Arbeitsbereiche)** für den aktuellen Agenten.
1.  Klicken Sie hier, um den Arbeitsbereich zu öffnen, dessen Verknüpfung zum Agenten Sie aufheben möchten.
1.  Klicken Sie auf **Unlink this workspace (Verlinkung dieses Arbeitsbereichs aufheben)** ![Papierkorbsymbol, das das Löschen einer Verknüpfungsbeziehung darstellt](images/trash.png).

[Verlinken von Arbeitsbereichen](link_workspace.html)
