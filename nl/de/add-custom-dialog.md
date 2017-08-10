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

# Hinzufügen benutzerdefinierter Dialoge für zentrale Funktionen 
{: #use_custom}

Sie können bei jeder zentralen Funktion Ihre eigene Konversation für die Interaktion mit dem Benutzer verwenden, um das Ziel des Benutzers zu erreichen.
{: shortdesc}

## Erstellen eines benutzerdefinierten Dialogs 
{: #custom_dialog}

Wenn für eine von Ihnen aktivierte zentrale Funktion eine Behandlung durch einen benutzerdefinierten Dialog erforderlich ist, können Sie mithilfe des {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service den Dialog erstellen und ihn anschließend mit Ihrem virtuellen Agenten verknüpfen.

### Informationen zu dieser Aufgabe

Der {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service umfasst eine Reihe von Tools und Anwendungsprogrammierschnittstellen, mit denen Sie Anwendungen erstellen können, die natürlichsprachliche Schnittstellen zur Automatisierung von Interaktionen mit Kunden verwenden. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} definiert mithilfe des {{site.data.keyword.conversationshort}}-Service die trainierten Funktionen und den Dialogfluss, die vom Bot verwendet werden. Wenn der bereitgestellte Dialog nicht die erforderlich Flexibilität ermöglicht, können Sie mit den Tools des {{site.data.keyword.conversationshort}}-Service Ihren eigenen Dialog erstellen.

Für die Kompatibilität mit dem virtuellen Agenten müssen alle von Ihnen erstellten Dialoge den Gestaltungsrichtlinien entsprechen, die unter [Dialogvertrag ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Symbol für externen Link"){: new_window} definiert sind. Diese Richtlinien geben an, wie der Dialog mit der Chat-Schnittstelle des virtuellen Agenten interagiert. Darin inbegriffen ist die Angabe, wie Eingabeaufforderungen für Benutzer angezeigt werden und wo von Benutzern angegebene Informationen gespeichert werden können, damit über die Schnittstelle des Chatfensters darauf zugegriffen werden kann.

Das {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}}-Repository enthält auch Beispiele, die die Funktionsweise der Dialoginteraktionen veranschaulichen. Sie können das Beispiel als Modell für Ihren eigenen Dialog verwenden. Weitere Informationen finden Sie unter [JSON-Datei mit beispielhaften Dialogflüssen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/michelle-miller-patch-1/sample_dialog_flows.json "Symbol für externen Link"){: new_window}.

#### Verfahren

Gehen Sie wie folgt vor, um einen benutzerdefinierten Dialog zu erstellen:

1.  Sofern nicht bereits geschehen, melden Sie sich beim {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service an. Weitere Informationen finden Sie in der Dokumentation [{{site.data.keyword.conversationshort}}-Service - Erste Schritte![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted "Symbol für externen Link"){: new_window}.
1.  Erstellen Sie einen Arbeitsbereich, in dem Ihr Dialog enthalten sein soll.

    Weitere Informationen zu Arbeitsbereichen finden Sie in der Dokumentation [{{site.data.keyword.conversationshort}}-Service - Erstellen eines Arbeitsbereichs![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace "Symbol für externen Link"){: new_window}.

1.  Navigieren Sie direkt zur Registerkarte **{{site.data.keyword.dialogshort}}**. (Erstellen Sie keine Absichten oder Entitäten.)
1.  Erstellen Sie für jede Funktion, die Sie anpassen möchten, einen Dialogknoten.

    Ein Dialogknoten muss eine Bedingung aufweisen, die den Absichtsnamen für die Funktion bewertet, in der dieser verwendet wird.

    Verwenden Sie die folgende Syntax:

    ```java
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Beispiel: Der *intent-name* für die Funktion **Contact us (So erreichen Sie uns)** lautet `Information-Contact_Us`. In Ihrem Dialog würde ein Test für `$wva.intents.get(0).intent.equals('Information-Contact_Us')` durchgeführt.

    Wenn Sie über einen älteren Bot verfügen und Ihre Einstellungen angeben, dass die Absicht nur an Ihren Arbeitsbereich übergeben werden soll, dann verwenden Sie stattdessen folgende Syntax:

    ```java
    #intent-name
    ```
    {: screen}

    Beispiel: `#Information-Contact_Us`

    Unter [Absichtsnamen](intent_codenames.html) finden Sie Informationen darüber, wie Sie den Absichtsnamen erkennen können, der einer Funktion zugeordnet ist.

1.  Fügen Sie nach Bedarf Knoten hinzu, um den erforderlichen Dialogablauf zu erstellen.

    Damit Ihr Dialog mit {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} kompatibel ist, muss er beim Speichern gesammelter Informationen oder beim Verwenden von Ereignissen für die Kommunikation über die Schnittstelle des Chat-Widgets bestimmte Gestaltungsrichtlinien einhalten. Erstellen Sie einen Dialog, der den Gestaltungsrichtlinien von {{site.data.keyword.virtualagentshort}} für Dialoge unter [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md "Symbol für externen Link"){: new_window} entspricht.

1.  Verlinken Sie die Arbeitsbereiche mit Dialogen, die Sie für Ihren Agenten erstellt haben.

    Entsprechende Einzelheiten finden Sie unter [Verlinken von Arbeitsbereichen](link_workspace.html).

1.  Ändern Sie auf der Seite \"Konfigurieren\" auf der Registerkarte **Core Capabilities (Zentrale Funktionen)** den Antworttyp der einzelnen Funktionen, bei denen Sie für den Antworttyp **Use your own conversation (Eigene Konversation verwenden)** einen benutzerdefinierten Dialog verwenden möchten.
1.  Wählen Sie aus der Liste der verknüpften Arbeitsbereiche den Arbeitsbereich aus, der den gewünschten Dialog enthält, und klicken Sie anschließend auf **Save (Speichern)**, um das Herstellen der Verbindung zu beenden.

    Wenn Sie den Arbeitsbereich noch nicht verlinkt haben, können Sie von hier aus auf **Link a workspace (Arbeitsbereich verlinken)** klicken, um den Arbeitsbereich mit Ihrem Agenten zu verlinken, den Sie zuvor erstellt haben.
