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

# Personalisieren des Agenten
{: #personalize}

Stellen Sie sicher, dass der virtuelle Agent auf die Probleme reagiert, die für Ihre Kunden von Bedeutung sind. Stellen Sie zudem sicher, dass die Antworten Informationen zu den von Ihrem Unternehmen angebotenen Services vermitteln oder Kunden beim Abschließen von Geschäftstransaktionen helfen.
{: shortdesc}

## Informationen zu dieser Aufgabe

Sie können den Agenten personalisieren, indem Sie die folgenden Aktionen ausführen:

[Hinzufügen benutzerdefinierter Dialoge für zentrale Funktionen](/docs/services/virtual-agent/personalize.html#use_custom)

[Hinzufügen Ihrer eigenen Funktionen](/docs/services/virtual-agent/personalize.html#add_custom_capabilities)

## Hinzufügen benutzerdefinierter Dialoge für zentrale Funktionen
{: #use_custom}

Sie können bei jeder zentralen Funktion Ihre eigene Konversation für die Interaktion mit dem Benutzer verwenden, um das Ziel des Benutzers zu erreichen.

### Erstellen eines benutzerdefinierten Dialogs
{: #custom_dialog}

Wenn für eine von Ihnen aktivierte zentrale Funktion eine Behandlung durch einen benutzerdefinierten Dialog erforderlich ist, können Sie mithilfe des {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service den Dialog erstellen und ihn anschließend mit Ihrem virtuellen Agenten verknüpfen.

#### Informationen zu dieser Aufgabe

Der {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service umfasst eine Reihe von Tools und Anwendungsprogrammierschnittstellen, mit denen Sie Anwendungen erstellen können, die natürlichsprachliche Schnittstellen zur Automatisierung von Interaktionen mit Kunden verwenden. {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} definiert mithilfe des {{site.data.keyword.conversationshort}}-Service die trainierten Funktionen und den Dialogfluss, die vom Bot verwendet werden. Wenn der bereitgestellte Dialog nicht die erforderlich Flexibilität ermöglicht, können Sie mit den Tools des {{site.data.keyword.conversationshort}}-Service Ihren eigenen Dialog erstellen.

Für die Kompatibilität mit dem virtuellen Agenten müssen alle von Ihnen erstellten Dialoge den Gestaltungsrichtlinien unter [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window} entsprechen. Diese Richtlinien geben an, wie der Dialog mit der Chat-Schnittstelle des virtuellen Agenten interagiert. Darin inbegriffen ist die Angabe, wie Eingabeaufforderungen für Benutzer angezeigt werden und wo von Benutzern angegebene Informationen gespeichert werden können, damit über die Schnittstelle des Chatfensters darauf zugegriffen werden kann.

Das {{site.data.keyword.virtualagentshort}} {{site.data.keyword.dialogshort}}-Repository enthält auch Beispiele, die die Funktionsweise der Dialoginteraktionen veranschaulichen. Sie können das Beispiel als Modell für Ihren eigenen Dialog verwenden. Siehe die [JSON-Datei mit beispielhaften Dialogflüssen ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/sample_dialog_flows.json){: new_window}.

#### Verfahren

Gehen Sie wie folgt vor, um einen benutzerdefinierten Dialog zu erstellen:

1. Sofern nicht bereits geschehen, melden Sie sich beim {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service an. Weitere Informationen finden Sie in der Dokumentation [{{site.data.keyword.conversationshort}}-Service - Erste Schritte ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.
1. Erstellen Sie einen Arbeitsbereich, in dem Ihr Dialog enthalten sein soll.

    Weitere Informationen zu Arbeitsbereichen finden Sie in der Dokumentation [{{site.data.keyword.conversationshort}}-Service - Erstellen eines Arbeitsbereichs ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/create-workspace.html){: new_window}.

1. Navigieren Sie direkt zur Registerkarte **{{site.data.keyword.dialogshort}}**. (Erstellen Sie keine Absichten oder Entitäten.)
1. Erstellen Sie für jede Funktion, die Sie anpassen möchten, einen Dialogknoten.

    Ein Dialogknoten muss eine Bedingung aufweisen, die den Absichtsnamen für die Funktion bewertet, in der dieser verwendet wird.

    Verwenden Sie die folgende Syntax:

    ```
    $wva.intents.get(0).intent.equals('intent-name')
    ```
    {: screen}

    Beispiel: Der *intent-name* für die Funktion **So erreichen Sie uns** lautet `Information-Contact_Us`. In Ihrem Dialog würde ein Test für `$wva.intents.get(0).intent.equals('Information-Contact_Us')` durchgeführt.

    Wenn Sie über einen älteren Bot verfügen und Ihre Vorgaben so festgelegt sind, dass die Absicht nur an Ihren Arbeitsbereich übergeben werden soll, dann verwenden Sie stattdessen folgende Syntax:

    ```
    #intent-name
    ```
    {: screen}

    Beispiel: `#Information-Contact_Us`

    Unter [Absichtsnamen](/docs/services/virtual-agent/intent_codenames.html) finden Sie Informationen darüber, wie Sie den Absichtsnamen erkennen können, der einer Funktion zugeordnet ist.

1. Fügen Sie nach Bedarf Knoten hinzu, um den erforderlichen Dialogablauf zu erstellen.

    Damit Ihr Dialog mit {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} kompatibel ist, muss er beim Speichern gesammelter Informationen oder beim Verwenden von Ereignissen für die Kommunikation über die Schnittstelle des Chat-Widgets bestimmte Gestaltungsrichtlinien einhalten. Erstellen Sie einen Dialog, der den Gestaltungsrichtlinien von {{site.data.keyword.virtualagentshort}} für Dialoge unter [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md){: new_window} entspricht.

1. Verlinken Sie die Arbeitsbereiche mit Dialogen, die Sie für Ihren Agenten erstellt haben.

    Entsprechende Einzelheiten finden Sie unter [Verlinken von Arbeitsbereichen](/docs/services/virtual-agent/link_workspace.html).

1. Ändern Sie auf der Seite \"Konfigurieren\" auf der Registerkarte **Zentrale Funktionen** den Antworttyp der einzelnen Funktionen, bei denen Sie für den Antworttyp **Eigene Konversation verwenden** einen benutzerdefinierten Dialog verwenden möchten.
1. Wählen Sie aus der Liste der verknüpften Arbeitsbereiche den Arbeitsbereich aus, der den gewünschten Dialog enthält, und klicken Sie anschließend auf **Speichern**, um das Herstellen der Verbindung zu beenden.

    Ein Arbeitsbereich, der bereits zum Hinzufügen benutzerdefinierter Funktionen verwendet wird, wird nicht als Option angezeigt. Sie können zum Hinzufügen benutzerdefinierter Funktionen nicht den Bereich verwenden, den Sie auch zum Hinzufügen eines Dialogs für eine zentrale Funktion verwenden. 

    Wenn Sie den Arbeitsbereich noch nicht verknüpft haben, können Sie von hier aus auf **Verknüpfen eines Arbeitsbereichs** klicken, um den Arbeitsbereich mit Ihrem Agenten zu verknüpfen, den Sie zuvor erstellt haben.

## Hinzufügen Ihrer eigenen Funktionen
{: #add_custom_capabilities}

Fügen Sie Ihre eigenen Funktionen hinzu, um die Inhalte zu erweitern, die der virtuelle Agent mit Ihren Kunden besprechen kann.

### Vorbereitung

Wenn Sie über einen Arbeitsbereich einen benutzerdefinierten Dialog für eine zentrale Funktion angeben, müssen Sie in dem Arbeitsbereich nur einen Dialog angeben. Der Agent wurde bereits so trainiert, dass er Äußerungen erkennen kann, die den zentralen Funktionen zugeordnet sind. Sie müssen daher keine Absichten, Entitäten und Trainingsdaten angeben. Wenn Sie einen Arbeitsbereich angeben, in dem Ihre eigenen Funktionen definiert sind, müssen Sie zusätzlich zu dem Dialog Absichten und Entitäten angeben. Zudem müssen Sie eine Vielzahl von beispielhaften Äußerungen angeben, die der Service zum Trainieren der Absichten verwenden kann, die Sie unterstützen möchten. Verwenden Sie die Dokumentation, Demos und Tools, die im Lieferumfang des {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service enthalten sind, um einen Arbeitsbereich mit benutzerdefinierten Funktionen zu erstellen. Weitere Informationen finden Sie in der [Dokumentation zu {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/index.html){: new_window}.

### Informationen zu dieser Aufgabe

Sie können nur einen Arbeitsbereich für die Definition benutzerdefinierter Funktionen erstellen. Jede Absicht, die Sie mit dem Arbeitsbereich verlinken, wird als benutzerdefinierte Funktion verfügbar gemacht, wenn Sie den Arbeitsbereich mit dem Agenten verlinken. Der Arbeitsbereich muss alle Funktionen enthalten, die Sie zu Ihrem Agenten hinzufügen möchten. Fügen Sie keine Absichten zum Arbeitsbereich hinzu, die Ihr Agent nicht behandeln soll.

### Verfahren

1. Erstellen Sie über Ihre {{site.data.keyword.conversationshort}}-Serviceinstanz einen Arbeitsbereich, der Ihre benutzerdefinierten Funktionen definiert. Siehe die [Dokumentation zum {{site.data.keyword.conversationshort}}-Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

    Beachten Sie folgende Richtlinien:
    - Fügen Sie für jede Funktion, die Sie im Dialog als Basisknoten unterstützen möchten (in der Benutzerschnittstelle des {{site.data.keyword.conversationshort}}-Tools auch als <cite class="cite">alternative Konversation</cite> bezeichnet), einen Zweig hinzu. Definieren Sie beispielsweise keinen Basisknoten in Ihrem Dialog, der Begrüßungsansagen für Benutzer erkennt und darauf reagiert, um anschließend untergeordnete Knoten hinzuzufügen, die mit anderen untergeordneten Absichten benutzerdefinierter Funktionen übereinstimmen.
    - Vermeiden Sie die Behandlung von Abweichungen von Benutzereingaben mit rekursiven Schleifen. Erstellen Sie nur Dialogwendungen, die ein definitives Ende haben.
    - Erstellen Sie keine benutzerdefinierte Absicht, deren Name mit dem Namen der Absicht identisch ist, die von einer zentralen Funktion verwendet wird. Eine Liste mit zu vermeidenden Namen finden Sie unter [Namen von Absichten](/docs/services/virtual-agent/intent_codenames.html).

1. Verlinken Sie den Arbeitsbereich mit dem Agenten. Siehe [Verlinken von Arbeitsbereichen](/docs/services/virtual-agent/link_workspace.html)
1. Öffnen Sie auf der Seite **Konfigurieren** die Registerkarte **Benutzerdefinierte Funktionen**.
1. Klicken Sie auf **Funktionen hinzufügen**.
1. Wählen Sie den Arbeitsbereich aus, den Sie in Schritt 2 mit dem Agenten verlinkt haben, und klicken Sie anschließend auf **Arbeitsbereich auswählen**.

    Die im verlinkten Arbeitsbereich definierten Absichten werden jetzt als aktivierte Funktionen aufgeführt.

    > **Hinweis:** Einzelne Funktionen können nicht inaktiviert werden. Wenn Sie eine benutzerdefinierte Funktion entfernen möchten, können Sie die Absicht im {{site.data.keyword.conversationshort}}-Service-Tool aus dem Arbeitsbereich löschen.

    Sie können alle Funktionen gleichzeitig entfernen, indem Sie auf **Private Funktionen entfernen** klicken. Durch das Löschen der Funktionen wird die Zuordnung zwischen dem Agenten und dem Arbeitsbereich, in dem die Funktionen definiert sind, nicht gelöscht.

### Ergebnisse

Nach dem Hinzufügen benutzerdefinierter Funktionen wird jede Äußerung, die von {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} bewertet wird, zur Bewertung an den zentralen Arbeitsbereich und an Ihren Arbeitsbereich mit den benutzerdefinierten Funktionen übergeben. Die Funktion, die am besten mit der Absicht der Benutzereingabe übereinstimmt, wird ausgelöst und der ihr zugeordnete Dialog wird verwendet.

![Zeigt an, wie ein Benutzer eine Äußerung an Watson Virtual Agent übergibt. Er übergibt die Äußerung zur Bewertung an den integrierten Arbeitsbereich und an den Arbeitsbereich mit den verknüpften Funktionen. Der integrierte Arbeitsbereich weist eine Konfidenz von ,85 auf, während der Arbeitsbereich mit den verknüpften Funktionen eine Konfidenz von ,55 aufweist. Der integrierte Arbeitsbereich übergibt eine Antwort zurück an Watson Virtual Agent, die an den Benutzer übergeben werden soll.](images/workspace-confidences.png)

### Testen benutzerdefinierter Funktionen
{: #test_custom_capabilities}

Führen Sie einige Tests durch, nachdem Sie Ihre eigenen Funktionen hinzugefügt haben, um sicherzustellen, dass sich die Funktionen wie erwartet verhalten.

#### Informationen zu dieser Aufgabe

Wenn Sie Ihre eigenen Funktionen hinzufügen, können Sie ohne großen Aufwand eine Funktion definieren, die in ihrer Verhaltensweise einer vorhandenen zentralen Funktion ähnelt. Wenn dies der Fall ist, müssen Sie sicherstellen, dass die beiden Funktionen beim Antworten auf bestimmte Benutzeranfragen nicht miteinander konkurrieren.

#### Verfahren

1. Im Bereich \"Vorschau\" können Sie Fragen stellen oder die Art von Anforderungen, die Ihre Kunden erwartungsgemäß stellen.

    Unter der Antwort wird die Funktion angezeigt, die für die Anforderung ausgelöst wurde. Wenn die angezeigte Funktion nicht Ihren Erwartungen entspricht, können Sie Änderungen vornehmen und korrigieren, wie die Äußerung an die Funktionen weitergeleitet wird.

1. Vergleichen Sie die Funktionen, die in der zentralen Anwendung definiert sind, mit den im benutzerdefinierten Arbeitsbereich definierten Funktionen.

    - Eine Beschreibung der einzelnen zentralen Funktionen zur Überprüfung der mit der Anwendung bereitgestellten Funktionen finden Sie unter [Zentrale Funktionen](/docs/services/virtual-agent/intent_list.html).
    - Öffnen Sie zur Überprüfung der im {{site.data.keyword.conversationshort}}-Arbeitsbereich definierten Absichten im {{site.data.keyword.conversationshort}}-Tool den Arbeitsbereich und anschließend die Seite **Absichten**. Blenden Sie die einzelnen Absichten ein, um die Äußerungstypen anzuzeigen, bei denen sie dafür trainiert sind, darauf zu antworten.

1. Im Bereich \"Vorschau\" können Sie Äußerungen testen, bei denen Sie den Verdacht haben, dass sie einen Konflikt auslösen könnten.

    Überprüfen Sie basierend auf den Antworten, ob sich überschneidende Funktionen Benutzeranfragen bearbeiten, die sich genug voneinander unterscheiden, sodass sich überschneidende Funktionen koexistieren können, ohne dass dies zu einer zusammenhanglosen Erfahrung für den Benutzer führt. Wenn die zwei Funktionen um die gleichen Arten von Äußerungen konkurrieren, muss eine Funktion inaktiviert werden. Sie können sich überschneidende Funktionen auf folgende Weisen bearbeiten:
    - **Zentrale Funktion inaktivieren**

        1. Suchen Sie mit dem {{site.data.keyword.conversationshort}}-Tool auf der Seite **Absichten** nach der Absicht, blenden Sie diese ein und klicken Sie anschließend auf das Symbol **Absicht löschen**, um die Absicht aus dem Arbeitsbereich zu löschen.
        1. Nachdem Sie die Änderungen am Arbeitsbereich vorgenommen haben, wird dieser automatisch erneut trainiert. Kehren Sie nach Abschluss des Trainings zu {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} zurück.
        1. Öffnen Sie über die Seite \"Konfiguration\" die Registerkarte **Benutzerdefinierte Funktionen**, um zu bestätigen, dass die Funktion nicht mehr aufgeführt wird.

    - **Zentrale Funktion inaktivieren**

        1. Suchen Sie auf der Seite \"Konfiguration\" von {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} auf der Registerkarte **Zentrale Funktionen** die Funktion, die Sie inaktivieren möchten.
        1. Klicken Sie auf die Kachel, um die Funktion zu öffnen, und schalten Sie anschließend den Schalter aus.

    - **Bearbeiten der Trainingsdaten für die benutzerdefinierte Funktion**

        Wenn die benutzerdefinierte Funktion einem ähnlichen Kundenziel entspricht, jedoch in größerem Umfang, können Sie beispielhafte Äußerungen aus den Trainingsdaten entfernen, damit Beispiele aus der benutzerdefinierten Funktion ausgeschlossen werden, bei denen die Arten der Äußerungen von den zentralen Funktion stammen. Sie können bei der zentralen Funktion nicht auf den Arbeitsbereich zugreifen; Sie können den Arbeitsbereich nur bearbeiten, damit die Änderungen der benutzerdefinierten Funktion wirksam werden. Verwenden Sie zur Bestimmung, welche Äußerungen an die zentrale Funktion weitergeleitet werden, den Bereich \"Vorschau\", um verschiedene Äußerungen zu testen und zu sehen, welche Äußerungen die zentrale Funktion auslösen.

        > **Achtung:** Wenn Sie diesen Ansatz auswählen, sollten Sie darauf eingestellt sein, dass Sie viele Tests durchführen und Überarbeitungen vornehmen müssen. Eine Vorhersage, wie maschinelles Lernen auf Änderungen von Trainingsdaten reagiert, ist nur schwer möglich. Sie müssen viele Tests durchführen, um zu bestätigen, dass Ihre Änderungen die beabsichtigte Wirkung haben.

        Bearbeiten Sie den Arbeitsbereich für die benutzerdefinierte Funktion, indem Sie die folgenden Schritte ausführen:
        1. Suchen Sie mit dem {{site.data.keyword.conversationshort}}-Tool auf der Seite **Absichten** nach der Absicht und blenden Sie die Absicht anschließend ein, um die Liste der beispielhaften Äußerungen anzuzeigen.
        1. Aktivieren Sie das Kästchen neben den Äußerungen, die sich mit Äußerungen überschneiden, die von zentralen Funktionen bearbeitet werden, und klicken Sie anschließend auf **Beispiele entfernen**.
        1. Nachdem Sie die Änderungen am Arbeitsbereich vorgenommen haben, wird dieser automatisch erneut trainiert. 

    - **Beide Funktionen behalten**

        In einigen Fällen ähneln sich die Funktionen zwar; die Anwendungsfälle, an die sie sich richten, sind jedoch so unterschiedlich, dass beide Funktionen aktiviert bleiben können.

1. Geben Sie die Testäußerungen erneut im Bereich \"Vorschau\" ein, um zu bestätigen, dass Ihre Änderungen zum erwarteten Verhalten führen. Ist dies nicht der Fall, nehmen Sie weitere Änderungen vor.

## Wie Keines der Obigen verwendet wird
{: #none_of_the_above}

Verstehen Sie, wie die Funktion **Keines der Obigen** vom virtuellen Agenten verwendet wird.

Anders als alle anderen zentralen Funktionen kann die Funktion **Keines der Obigen** nicht inaktiviert werden. Der Grund dafür ist, dass sie als eine Art Catch-All für Äußerungen dient, die zu keiner der konfigurierten Funktionen zugeordnet werden können. Diese Funktion ist nützlich, da Sie für Funktionen, über die Ihr Agent noch nicht verfügt, eine Standardantwort (z. B. <cite class="cite">Ich kann Ihnen dabei nicht helfen</cite>) für Anforderungen von Benutzern bereitstellen können. Sie reagiert auch auf unsinnige Fragen, die Benutzer manchmal aus Spaß stellen, wenn sie zum ersten Mal mit dem Agenten interagieren (z. B. <cite class="cite">Was soll ich zu Mittag essen?</cite>)

Aufgrund ihrer eindeutigen Rolle bei der Funktionsweise des virtuellen Agenten, ist es wichtig, wie Sie das zugehörige Verhalten konfigurieren. Die Funktion **Keines der Obigen** wird häufig ausgelöst, und zwar auf eine nicht immer offensichtliche Art und Weise, wie z. B.:

- Wenn Sie eine andere zentrale Funktion inaktivieren, werden Äußerungen, durch die die inaktivierte Funktion ausgelöst wird, bei einer Antwort zur Funktion **Keines der Obigen** umgeleitet.
- Wenn eine Äußerung keiner der aktivierten zentralen Funktionen entspricht, wird sie bei einer Antwort an die Funktion **Keines der Obigen** übergeben. Wenn Sie einen verknüpften Arbeitsbereich mit benutzerdefinierten Funktionen bereitstellen, wird die Äußerung im zentralen Arbeitsbereich und im benutzerdefinierten Arbeitsbereich bewertet, um eine Übereinstimmung zu finden. Wenn keine Übereinstimmung gefunden wird, wird die Antwort verwendet, die der zentralen Funktion **Keines der Obigen** zugeordnet ist.
- Sie können die Funktion **Keines der Obigen** so konfigurieren, dass sie den Antworttyp **Eigene Konversation verwenden** enthält, und sie mit einem Arbeitsbereich mit benutzerdefiniertem Dialog verknüpfen. Wenn für eine Äußerung im zentralen Arbeitsbereich keine Übereinstimmung mit einer Absicht gefunden wird, wird die Äußerung an die Funktion **Keines der Obigen** übergeben, die die Äußerung bei einer Antwort an den benutzerdefinierten Arbeitsbereich übergibt.
- Wenn Sie die Verknüpfung eines Arbeitsbereichs aufheben und der verknüpfte Arbeitsbereich der Funktion **Keines der Obigen** zugeordnet ist, müssen Sie Maßnahmen ergreifen, bevor Sie mit der Aufhebung der Verknüpfung des Arbeitsbereichs fortfahren können. Alle anderen Funktionen, die dem Arbeitsbereich zugeordnet sind und deren Verknüpfung Sie aufheben möchten, werden automatisch inaktiviert. Da die Funktion **Keines der Obigen** nicht inaktiviert werden kann, müssen Sie jedoch für ein alternatives Antwortverhalten entscheiden. Sie können den Antworttyp beispielsweise in **Textantwort anzeigen** ändern und eine Textnachricht hinzufügen, die in der Antwort verwendet werden soll.

