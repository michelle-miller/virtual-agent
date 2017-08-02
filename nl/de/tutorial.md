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

# Lernprogramm: Hinzufügen benutzerdefinierter Funktionen
{: #tutorial}

Dieses Lernprogramms hilft Ihnen dabei, zu verstehen, wie die Funktionen Ihres virtuellen Agenten durch Hinzufügen Ihrer eigenen Funktionen erweitert werden.
{: shortdesc}

In diesem Lernprogramm fügen Sie in dem Arbeitsbereich, in dem die einfache {{site.data.keyword.conversationshort}}-Demoversion betrieben wird, neue Funktionen zu Ihrem Agenten hinzu. Der Arbeitsbereich simuliert die Rolle eines Beifahrers in einem Auto. Sie können sich das Demo [hier ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://conversation-simple.mybluemix.net/){: new_window} anschauen. Nach dem Importieren des Arbeitsbereichs in Ihre Instanz des {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service verknüpfen Sie den Arbeitsbereich mit Ihrem Agenten. Anschließend fügen Sie die Arbeitsbereichsabsichten in Form von zentralen Funktionen hinzu und befassen sich mit allen Konflikten, die zwischen den zentralen Funktionen und den von Ihnen hinzugefügten Funktionen auftreten.

## Lernziele

Nach Abschluss dieses Lernprogramms wissen Sie, wie die folgenden Aufgaben ausgeführt werden:

- Verlinken eines Arbeitsbereichs mit Ihrem Agenten
- Verwenden eines verlinkten Arbeitsbereichs zum Hinzufügen benutzerdefinierter Funktionen zu Ihrem Agenten
- Umgang mit potenziellen Konflikten zwischen vorhandenen und neuen Funktionen

Zur Ausführung dieses Lernprogramms werden ca. 30 Minuten benötigt. Wenn Sie sich mit weiteren Konzepten beschäftigen, die zu diesem Lernprogramm gehören, kann auch mehr Zeit erforderlich sein. 

## Voraussetzungen

Sie müssen über ein {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}-Konto verfügen und sich für die Verwendung des {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-{{site.data.keyword.conversationshort}}service angemeldet haben. Entsprechende Einzelheiten finden Sie unter [https://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/getting-started.html){: new_window}.

## Ergebnisse

Nach Abschluss dieses Lernprogramms und nach der Beantwortung typischer Benutzerfragen zu Ihrem Unternehmen kann Ihr Agent Fragen und Anforderungen beantworten, die ein Autofahrer von seinem Beifahrer gefragt werden könnte, z. B.: <cite class="cite">Wann kommen wir schätzungsweise an?</cite> oder <cite class="cite">Kannst du bitte das Radio einschalten?</cite>

### Lerneinheiten in diesem Lernprogramm

[Lerneinheit 1: Importieren eines Arbeitsbereichs in {{site.data.keyword.conversationshort}}](/docs/services/virtual-agent/tutorial.html#tutless1)

[Lerneinheit 2: Verlinken eines Arbeitsbereichs](/docs/services/virtual-agent/tutorial.html#tutless2)

[Lerneinheit 3: Hinzufügen benutzerdefinierter Funktionen](/docs/services/virtual-agent/tutorial.html#tutless3)

[Lerneinheit 4: Testen benutzerdefinierter Funktionen](/docs/services/virtual-agent/tutorial.html#tutless4)

[Lerneinheit 5: Beheben von Konflikten zwischen Funktionen](/docs/services/virtual-agent/tutorial.html#tutless5)

## Lerneinheit 1: Importieren eines Arbeitsbereichs in die Konversation
{: #tutless1}

In dieser Lerneinheit lernen Sie, wie Sie einen Arbeitsbereich in den {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-{{site.data.keyword.conversationshort}}sservice importieren.

### Vorbereitung

Sie müssen über ein {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}}-Konto verfügen und sich bei dem {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-{{site.data.keyword.conversationshort}}sservice angemeldet haben. 

### Informationen zu dieser Aufgabe

Zur Vereinfachung des Erstellungsprozesses eines {{site.data.keyword.conversationshort}}-Arbeitsbereichs importieren Sie die Datei `car_demo_workspace.json`, die vordefinierte Artefakte aus dem einfachen {{site.data.keyword.conversationshort}}-Demo enthält.

### Verfahren

1. Laden Sie die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/virtual-agent/car_demo_workspace.json" download>car_demo_workspace.json<img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> auf Ihren Computer herunter.
1. [Melden Sie sich ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/dashboard/watson){: new_window} bei Ihrer {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Serviceinstanz an.
1. Klicken Sie auf **Tool starten**.
1. Klicken Sie zum Importieren eines Arbeitsbereichs aus einer JSON-Datei auf das Symbol ![Pfeil nach oben über einem Posteingang zur Angabe einer Importaktion](images/workspace_import.png).
1. Klicken Sie auf **Datei auswählen**, um nach der Datei `car_demo_workspace.json` zu suchen, die Sie vorher heruntergeladen haben.
1. Wählen Sie **Alles (Absichten, Entitäten und {{site.data.keyword.dialogshort}})** aus und klicken Sie anschließend auf **Importieren**.

### Ergebnisse

Der Arbeitsbereich **Lernprogramm für Armaturenbrett** wird zu Ihrer Instanz des {{site.data.keyword.conversationshort}}-Service hinzugefügt.

## Lerneinheit 2: Verlinken eines Arbeitsbereichs
{: #tutless2}

In dieser Lerneinheit lernen Sie, wie Sie den Arbeitsbereich eines {{site.data.keyword.conversationshort}}-Service mit Ihrem Agenten verlinken.

### Verfahren

1. Wählen Sie aus dem {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Menü die Option **Verlinkte Arbeitsbereiche** aus.
1. Klicken Sie auf **Arbeitsbereich verlinken**.
1. Wählen Sie die Instanz des {{site.data.keyword.conversationshort}}-Service aus, in den Sie den Arbeitsbereich in der vorherigen Lerneinheit importiert haben.
1. Wählen Sie den Arbeitsbereich **Lernprogramm für Armaturenbrett** aus.
1. Klicken Sie auf **Arbeitsbereiche verlinken**.

## Lerneinheit 3: Hinzufügen benutzerdefinierter Funktionen
{: #tutless3}

In dieser Lerneinheit lernen Sie, wie Sie benutzerdefinierte Funktionen zu Ihrem Agenten hinzufügen.

### Verfahren

1. Wählen Sie aus dem {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Menü die Option **Konfigurieren** aus.
1. Klicken Sie auf die Registerkarte **Benutzerdefinierte Funktionen**.
1. Klicken Sie auf **Funktionen hinzufügen**.
1. Klicken Sie auf den Arbeitsbereich **Lernprogramm für Armaturenbrett** und anschließend auf **Arbeitsbereich auswählen**.

    Auf der Seite "Benutzerdefinierte Funktionen" wird jetzt eine Liste mit Funktionen angezeigt.

## Lerneinheit 4: Testen benutzerdefinierter Funktionen
{: #tutless4}

In dieser Lerneinheit erfahren Sie mehr über die benutzerdefinierten Funktionen, die Sie hinzugefügt haben.

### Informationen zu dieser Aufgabe

Jetzt, wo Sie Funktionen zum Agenten hinzugefügt haben, können Sie mehr über den Zweck dieser Funktionen erfahren.

### Verfahren

1. Klicken Sie im {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Header auf **Vorschau**.
1. Stellen Sie eine Frage, die eine benutzerdefinierte Funktion auslöst. Geben Sie den Text <cite class="cite">Können wir Musik hören?</cite> ein.

    Der Agent bewertet diese Anforderung und ordnet sie der benutzerdefinierten Funktion **#turn_on** zu. Im verlinkten Arbeitsbereich wird der Dialogknoten mit einer Bedingung verwendet, die der Absicht "#turn_on" entspricht. Folglich fragt der Agent, welche Musikrichtung gespielt werden soll.

    > **Hinweis:** Sie können die Funktion sehen, der die Benutzereingabe zugeordnet wird, da der Funktionsname als Link unter der Antwort angezeigt wird.
1. Geben Sie eine Musikrichtung ein, z. B. <cite class="cite">Klassik</cite> oder <cite class="cite">Rock</cite>, um den Dialog zu beenden.
1. Klicken Sie zum Öffnen der Seite mit den benutzerdefinierten Funktionen auf den Link **#turn_on** aus dem Vorschauverlauf.
1. Stellen Sie nun eine Frage, die eine zentrale Funktion auslöst. Geben Sie den Text <cite class="cite">Erzählen Sie mir etwas über sich</cite> ein.

    Klicken Sie auf den Link **Systeminformationen**, um die Funktionsdetailseite zu öffnen. Zentrale Funktionen verfügen jeweils über eine eigene Funktionsdetailseite, auf der Sie die Antwort anpassen können.

1. Versuchen Sie nun, den Agenten durcheinander zu bringen, indem Sie den Text <cite class="cite">Können wir Musik hören?</cite> eingeben.

    Der Agent erkennt, dass Sie diese Frage bereits gestellt haben, und teilt Ihnen dies mit.

## Lerneinheit 5: Beheben von Konflikten zwischen Funktionen
{: #tutless5}

In dieser Lerneinheit lernen Sie, wie Sie bei Konflikten zwischen zentralen und benutzerdefinierten Funktionen vermitteln und diese Konflikte beheben können.

### Informationen zu dieser Aufgabe

Sie möchten, dass die Erfahrung des Benutzers bei der Interaktion mit dem Agenten konsistent ist. Wenn die Antworten auf bestimmte Abfragen zwischen Antworten einer zentralen Funktion und Antworten einer benutzerdefinierten Funktion schwanken, kann dies beim Benutzer für Verwirrung sorgen. Ermitteln Sie, wo solche Konflikte auftreten könnten und ergreifen Sie Maßnahmen, um sicherzustellen, dass bei jedem Abfragetyp nur jeweils eine Funktion ausgelöst wird.

### Verfahren

1. Vergleichen Sie die Funktionen, die in der zentralen Anwendung definiert sind, mit den im benutzerdefinierten Arbeitsbereich definierten Funktionen.

    - Eine Beschreibung der einzelnen zentralen Funktionen zur Überprüfung der mit der Anwendung bereitgestellten Funktionen finden Sie unter [Zentrale Funktionen](/docs/services/virtual-agent/intent_list.html).
    - Öffnen Sie zur Überprüfung der im {{site.data.keyword.conversationshort}}-Arbeitsbereich definierten Absichten im {{site.data.keyword.conversationshort}}-Tool den Arbeitsbereich und anschließend die Seite **Absichten**. Blenden Sie die einzelnen Absichten ein, um die Äußerungstypen anzuzeigen, bei denen sie dafür trainiert sind, darauf zu antworten.

1. Erstellen Sie basierend auf den einzelnen Beschreibungen und Funktionen eine Liste mit allen Funktionen, bei denen Sie den Verdacht haben, dass sie bei der Behandlung einer Äußerung des Benutzers miteinander konkurrieren könnten.

    Beispiel: Folgende Funktionen könnten versuchen, sich an die gleiche Benutzereingabe zu richten:

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d6710e463" class="stentry thleft thbot">Zentrale Funktion</th>
    <th valign="bottom" align="left" id="d6710e465" class="stentry thleft thbot">Benutzerdefinierte Funktion</th>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Ende</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#goodbyes</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Nächstgelegene Filiale suchen</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#locate_amenity</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Begrüßungsansagen</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#greetings</p></td>
    </tr>
    <tr class="strow"><td valign="top" headers="d6710e463" class="stentry"><p class="p wrapper">Sicherheitsgarantie</p></td>
    <td valign="top" headers="d6710e465" class="stentry"><p class="p wrapper">#system_reliance</p></td>
    </tr>
    </table>

1. Inaktivieren Sie alle benutzerdefinierten Funktionen, die Sie nicht verwenden möchten.

    - Der Zweck der Funktionen `Ende` und `#goodbyes` überschneidet sich völlig. Sie müssen sich für eine der Funktionen entscheiden, um sicherzustellen, dass die Erfahrung der Benutzer konsistent ist, wenn sie eine Konversation mit Ihrem Agenten beenden. Sie können nicht beide Funktionen verwenden.

        Es ist allgemein üblich, eine Logik zu erstellen, die am Ende einer Konversation ausgelöst wird. Verwenden Sie statt der benutzerdefinierten Funktion die zentrale Funktion `Ende`, um sicherzustellen, dass der virtuelle Agent ein derartiges Verhalten kontrolliert.

    - Die Funktionen `Nächstgelegene Filiale suchen` und `#locate_amenity` überschneiden sich. Geben Sie zur Verdeutlichung für sich selbst im Bereich \"Vorschau\" folgende beispielhafte Äußerungen ein:

        - <cite class="cite">Nächstgelegene Filiale suchen</cite> wird an `#locate_amenity` weitergeleitet.
        - <cite class="cite">Eigene Filiale suchen</cite> wird an `Nächstgelegene Filiale suchen` weitergeleitet.

        Die benutzerdefinierte Funktion `#locate_amenity` stellt neben Informationen zu einer Filiale Informationen zu einer breiteren Auswahl von Einrichtungen bereit. Der zentralen Funktion ist jedoch eine nette integrierte Konversation zugeordnet, in der eine Postleitzahl des Benutzers erfasst wird und die Adresse der nächstgelegenen Filiale zurückgegeben wird. Verwenden Sie die zentrale Funktion `Nächstgelegene Filiale finden`, um Nutzen aus dem integrierten Verhalten zu ziehen.

    - Auch die sicherheitsrelevanten Funktionen überschneiden sich. Geben Sie folgende beispielhafte Äußerungen in den Bereich \"Vorschau\" ein, um ein besseres Gespür dafür zu kriegen, welche Art von Benutzereingabe von den einzelnen Funktionen bearbeitet wird.

        - <cite class="cite">Sind meine Daten geschützt?</cite> wird an `Sicherheitsgarantie` weitergeleitet.
        - <cite class="cite">Kann ich Ihnen meine Informationen anvertrauen?</cite> wird an `#system_reliance` weitergeleitet.

        Die Funktion `#system_reliance` weist im Vergleich zur Funktion `Sicherheitsgarantie` begrenzte Trainingsdaten auf. Daher verwenden Sie statt der benutzerdefinierten Funktion die zentrale Funktion.

    Zur Inaktivierung einer benutzerdefinierten Funktion müssen Sie diese aus dem {{site.data.keyword.conversationshort}}-Arbeitsbereich löschen.
    1. Blenden Sie im {{site.data.keyword.conversationshort}}-Tool auf der Seite \"Absichten\" die Absicht `#goodbyes` ein und klicken Sie anschließend auf das Symbol **Absicht löschen**, um die Absicht aus dem Arbeitsbereich zu löschen.
    1. Blenden Sie die Absicht `#locate_amenity` ein und klicken Sie anschließend auf das Symbol **Absicht löschen**, um die Absicht aus dem Arbeitsbereich zu löschen.
    1. Blenden Sie die Absicht `#system_reliance` ein und klicken Sie anschließend auf das Symbol **Absicht löschen**, um die Absicht aus dem Arbeitsbereich zu löschen.

1. Wenn Sie am benutzerdefinierten Bereich Änderungen vornehmen, wird dieser automatisch mit den neuen Daten erneut trainiert. Kehren Sie nach Abschluss des Trainings im Arbeitsbereich zu {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} zurück.

    Öffnen Sie über die Seite \"Konfiguration\" die Registerkarte **Benutzerdefinierte Funktionen**, um zu bestätigen, dass die von Ihnen entfernten Funktionen (`#goodbyes`, `#locate_amenity` und `#system_reliance`) nicht mehr aufgeführt werden.

1. Die Funktionen `Begrüßungsansagen` und `#greetings` überschneiden sich komplett. Wir möchten, dass der Agent ein konsistentes Verhalten aufweist und eine Persönlichkeit hat. Die benutzerdefinierte Funktion `#greetings` wurde entworfen, um die Gefühle eines bestimmten Persönlichkeitstyps zum Ausdruck zu bringen, der die Unternehmensmarke widerspiegelt, damit Sie statt der zentralen Funktion die benutzerdefinierte Funktion verwenden.

    Zur Inaktivierung einer zentralen Funktion müssen Sie diese inaktivieren.
    1. Suchen Sie auf der Seite \"Konfigurieren\" von {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} auf der Registerkarte **Zentrale Funktionen** die Funktion `Begrüßungsansagen`.
    1. Klicken Sie auf die Kachel, um die Funktion zu öffnen, und schalten Sie anschließend den Schalter **Aus**. Klicken Sie auf den Rückwärtspfeil, um zur Hauptkonfigurationsseite zurückzukehren.

1. Führen Sie weitere Tests durch, indem Sie im Bereich \"Vorschau\" Testbenutzerabfragen eingeben, um zu bestätigen, dass die entsprechende Funktion die Benutzereingabe wie erwartet behandelt. Sie können beispielsweise folgende Äußerungen erneut testen:

    - <cite class="cite">Kann ich Ihnen meine Informationen anvertrauen?</cite> sollte von der Funktion `Sicherheitsgarantie` behandelt werden.
    - <cite class="cite">Nächstgelegene Filiale suchen</cite> sollte von der Funktion `Nächstgelegene Filiale suchen` behandelt werden.

## Zusammenfassung des Lernprogramms
{: #tutless_sum}

Während Sie etwas über {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} gelernt haben, haben Sie Ihren Agenten durch benutzerdefinierte Funktionen erweitert.

### Absolvierte Lerneinheiten

Bei der Durchführung dieses
Lernprogramms haben Sie die folgenden Konzepte kennengelernt: 

- Verknüpfte Arbeitsbereiche 
- Funktionen
- In Konflikt stehende Funktionen

