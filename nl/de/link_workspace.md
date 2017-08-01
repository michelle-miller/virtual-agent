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

# Verknüpfen von Arbeitsbereichen
{: #link_workspace}

Bevor Sie eine benutzerdefinierte Funktion oder einen benutzerdefinierten Dialog mit einer zentralen Funktion verwenden können, müssen Sie eine Verbindung zwischen dem virtuellen Agenten und dem Arbeitsbereich des {{site.data.keyword.conversationshort}}-Service, der die gewünschten Artefakte enthält, herstellen.
{: shortdesc}

## Informationen zu dieser Aufgabe

Ein Arbeitsbereich ist ein {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service-Container, der Absichten, Entitäten und einen Dialog enthält. Dies sind Artefakte, mit denen ein Konversationsfluss definiert und trainiert wird. Ihr Agent kann Artefakte aus diesem Arbeitsbereich verwenden, einschließlich trainierter Absichten und eines Dialogs, da er mit Ihren Kunden interagiert, um den Bereich der Dinge anzupassen und zu erweitern, die er besprechen kann.

Sie können Arbeitsbereiche verknüpfen, um folgende Ziele zu erreichen:

 - Definieren Sie Ihre eigenen Funktionen: Der Arbeitsbereich muss Absichten, beispielhafte Äußerungen und einen Dialog mit Knotenbedingungen enthalten, die allen definierten Absichten entsprechen. 
 - Definieren Sie einen benutzerdefinierten Dialog für eine zentrale Funktion: Der Arbeitsbereich muss einen Dialog mit einer Knotenbedingung enthalten, die mit dem Absichtsnamen für eine zentrale Funktion übereinstimmt.

Sie können zum Hinzufügen benutzerdefinierter Funktionen nicht den Bereich verwenden, den Sie auch zum Hinzufügen eines Dialogs für eine zentrale Funktion verwenden. Sie müssen einen einzelnen dedizierten Arbeitsbereich erstellen, in dem alle benutzerdefinierten Funktionen definiert sind, die Sie verwenden möchten. Erstellen Sie mindestens einen separaten Arbeitsbereich, um die Dialoge zu definieren, die Sie als Antworten bei zentralen Funktionen verwenden möchten.

## Verfahren

1. Wählen Sie aus dem {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Menü die Option **Verlinkte Arbeitsbereiche** aus.
1. Klicken Sie auf **Arbeitsbereich verlinken**.

    Geben Sie Ihre {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}-Kontoberechtigungsnachweise an, um {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} eine Berechtigung für den Zugriff auf Ihre Instanz des {{site.data.keyword.conversationshort}}-Service und das Abrufen von Informationen aus dem Arbeitsbereich zu erteilen.

1. Wählen Sie die Instanz des {{site.data.keyword.conversationshort}}-Service aus, die die gewünschten Arbeitsbereiche enthält.
1. Wählen Sie mindestens einen Arbeitsbereich aus, den Sie mit Ihrem Agenten verknüpfen möchten.
1. Klicken Sie auf **Arbeitsbereiche verlinken**.

[Erstellen eines benutzerdefinierten Dialogs](/docs/services/virtual-agent/personalize.html#custom_dialog)

[Hinzufügen Ihrer eigenen Funktionen](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Aufheben der Verknüpfung von Arbeitsbereichen
{: #unlink_workspace}

Wenn Sie die Verbindung zwischen Ihren virtuellen Agenten und einem bestimmten {{site.data.keyword.conversationshort}}-Arbeitsbereich nicht beibehalten möchten, können Sie die Verknüpfung des Arbeitsbereichs aufheben.

### Vorbereitung

Stellen Sie sicher, dass der Arbeitsbereich, dessen Verknüpfung sie aufheben möchten, nicht aktiv von einer Funktion verwendet wird, für die dieser Arbeitsbereich erforderlich ist. Vergessen Sie nicht, dass ein Arbeitsbereich, der mit dem virtuellen Agenten verknüpft ist, für jede Funktion zur Verwendung zur Verfügung steht, die diesem Agenten zugeordnet ist; dies kann eine benutzerdefinierte Funktion oder eine zentrale Funktion sein.

### Informationen zu dieser Aufgabe

Wenn Sie die Verknüpfung eines Arbeitsbereichs mit einer Funktion aufheben, wird die Funktion automatisch inaktiviert. Durch die Inaktivierung der Funktion wird sichergestellt, dass aktive Benutzer keinem unerwarteten Verhalten ausgesetzt werden, während Sie Änderungen vornehmen. Dieses Konzept gilt für alle Funktionen bis auf die Funktion **Keines der Obigen**, die nicht inaktiviert werden kann. Sie müssen den Antworttyp bei dieser Funktion von **Eigene Konversation verwenden** in eine der anderen Optionen für Antworttypen ändern, bevor Sie die Verknüpfung eines Arbeitsbereichs aufheben, der dieser Funktion zugeordnet ist.

### Verfahren

1. Wählen Sie aus dem {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Menü die Option **Verlinkte Arbeitsbereiche** aus.
1. Klicken Sie hier, um den Arbeitsbereich zu öffnen, dessen Verknüpfung zum Agenten Sie aufheben möchten.
1. Klicken Sie auf **Aufheben der Verknüpfung des Arbeitsbereichs**.

[Verknüpfen von Arbeitsbereichen](/docs/services/virtual-agent/link_workspace.html)

