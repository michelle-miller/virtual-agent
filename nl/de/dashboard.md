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

# Analysieren der Benutzeraktivität
{: #dashboard}

Die Seite \"Kundenprojektmetriken\" enthält ein Dashboard mit Visualisierungen, mit denen Sie Erkenntnisse aus Daten gewinnen können, die vom virtuellen Agenten erfasst wurden.
{: shortdesc}

## Vorbereitung

Ihre Instanz von {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} muss bereitgestellt werden und Benutzer müssen sich für eine Dauer von mindestens 30 Sekunden an Konversationen mit Ihrem virtuellen Agenten beteiligen, bevor das Dashboard Daten freigeben kann.

## Informationen zu dieser Aufgabe

Die Metriken auf der Seite werden alle 30 Minuten mit Daten aus Konversationen zwischen dem virtuellen Agenten und Ihren Benutzern aktualisiert. Sie bieten Einblick in folgende Dinge:

- Wie viele Konversationen finden statt
- Wie viele Benutzer (neue und zurückkehrende) führen Konversationen mit dem virtuellen Agenten
- Wie lauten die interessantesten und die am wenigsten interessanten Themen für Kunden (basierend darauf, welche Absichten am häufigsten und am seltensten ausgelöst werden)

Die Metriken können Ihnen dabei helfen, Bereiche zu finden, in denen die Leistung des virtuellen Agenten durch etwas zusätzliche Arbeit deutlich verbessert werden kann:

- Vergleichen Sie beliebte Themen mit den Absichten und Entitäten, für deren Erkennung der Service trainiert ist. Durch Lücken können Sie neue Absichten oder Terminologie entdecken, die Sie dem virtuellen Agenten beibringen können.
- Überprüfen Sie die Absichten, die am häufigsten ermittelt werden, kurz bevor Benutzer anfordern, mit einem menschlichen Agenten zu sprechen. Durch die Überprüfung der Ursachen für die Eskalationen können Sie zukünftigem Trainingsaufwand einen Schwerpunkt zuordnen. Sie können bestimmen, ob Benutzeranfragen falsch interpretiert werden, ob Ihrem Service insgesamt eine gemeinsame Absicht fehlt, ob die einer Absicht zugeordneten Antworten verbessert werden müssen usw.

Mithilfe der Metriken können Sie auch Zuweisungen von menschlichen Agentenressourcen planen, die auf Daten zu Standorten basieren, bei denen die Verwendung des virtuellen Agenten am gängigsten bzw. am wenigsten gängig ist; zudem können Sie die Spitzenkonversationszeiten planen.

Die Metriken analysieren die Daten der Konversationen auf einer niedrigen Ebene. Sie konzentrieren sich dabei auf die Artefakte, die Funktionen umfassen. Dazu zählen:

- **Entitäten**

    Eine <cite class="cite">Entität</cite> stellt einen Begriff oder ein Objekt dar, der bzw. das für eine Absicht relevant und der bzw. das einen bestimmten Kontext für eine Absicht bereitstellt. Eine Entität könnte beispielsweise einen Ort, in dem der Benutzer einen Geschäftsstandort sucht, oder den Betrag einer Rechnungszahlung darstellen. In der Benutzerschnittstelle ist dem Namen einer Entität immer das Zeichen `@` vorangestellt.

- **Absichten**

    Eine <cite class="cite">Absicht</cite> stellt den Zweck einer Benutzereingabe dar. Jede Funktion verwendet ein Klassifikationsmerkmal für die natürliche Sprache, mit dem die Äußerung eines Benutzers bewertet und eine vordefinierte Absicht gefunden werden kann. In der Benutzerschnittstelle ist dem Namen einer Absicht immer das Zeichen `#` vorangestellt.

## Verfahren

1. Öffnen Sie die Seite **Kundenprojektmetriken**.

    Im oberen Bereich der Seite ist eine Zusammenfassung der Schlüsseldatenpunkte enthalten, durch die sie schnell erkennen können, wie es dem virtuellen Agenten geht. Für jeden Datenpunkt wird der Prozentsatz der Änderung, die in dem Zeitraum aufgetreten ist, in Klammern angezeigt. (N/A) für <cite class="cite">Not Available</cite> (nicht verfügbar) wird so lange angezeigt, bis der Zeitraum verstrichen ist. Dann kann eine Änderung gemessen und angezeigt werden.

    Die in der Zusammenfassung angezeigten Zahlen können sich manchmal von den Zahlen auf anderen Seiten unterscheiden. Die Gesamtzahl der hier angezeigten Interaktionen könnte sich beispielsweise von der auf der Registerkarte **Interaktionen** angezeigten Gesamtzahl unterscheiden. Der Unterschied kann entstehen, da die Daten der Zusammenfassung alle 30 Minuten zusammengefasst und aktualisiert werden, während die Registerkarte **Interaktionen** in Echtzeit aktualisiert wird.

    Führen Sie bei den Daten auf den einzelnen Registerkarten einen Drilldown durch, um weitere Informationen zu erhalten.
    - **<b>Übersicht**</b>

        Finden Sie heraus, worüber Ihre Benutzer mehr erfahren möchten oder was Sie machen möchten, wenn sie sich mit dem virtuellen Agenten befassen, und welche Benutzerziele der virtuelle Agent nicht erfüllen konnte.
        - Das interaktive Diagramm **Absichten &amp; Entitäten** bietet einen Einblick darin, wie der {{site.data.keyword.conversationshort}}-Service die Benutzereingabe interpretiert. Es zeigt, welche Entitäten der Service verwendet hat, um die Absicht des Benutzers ermitteln zu können.

            Mithilfe der folgenden Syntax können Sie die Informationen im Diagramm schneller interpretieren:
            - `#<intent-name>`
            - `@<entity-name>`

            Klicken Sie auf eine Absicht, um zu sehen, mithilfe welcher Entitäten der Service die Benutzereingabe verstanden hat. Klicken Sie alternativ auf eine Entität, um zu sehen, welche Absichten der Service mithilfe dieser Entität ermitteln konnte.

        - Das Diagramm **Themen** erfasst Wörter oder Ausdrücke, die Benutzer in Konversationen am häufigsten äußern. Mithilfe des Diagramms können Sie verstehen, an welchen Themen Benutzer am meisten interessiert sind. Die Wörter in diesem Diagramm unterscheiden sich von den Entitäten, die im Diagramm \"Absichten &amp; Entitäten\" erfasst werden. Entitäten sind Wörter, bei denen der {{site.data.keyword.conversationshort}}-Service dafür trainiert wurde, diese zu verstehen und bestimmten Absichten zuzuordnen. Bei den Wörtern im Diagramm \"Themen\" handelt es sich einfach um Wörter, die in Konversationen von Benutzern am häufigsten auftreten. Die beiden Diagramme überschneiden sich möglicherweise. Behalten Sie die Wörter im Diagramm \"Themen\" im Blick, um mit Ihren Benutzern auf dem Laufenden zu bleiben und neue Dinge zu erkennen, über die sie möglicherweise mehr erfahren möchten. Dauerhaft gängige Themen könnten gut für neue Entitäten geeignet sein, mit deren Hilfe {{site.data.keyword.watson}} vorhandene Absichten erkennt, oder die neue Absichten vorschlagen könnten, die Sie {{site.data.keyword.watson}} beibringen können.

    - **<b>Benutzer**</b>

        Rufen Sie Informationen zum Standort Ihrer Benutzer und zum Umfang der Konversationen ab.

    - **<b>Interaktionen**</b>

        Schauen Sie sich die Aufzeichnungen der einzelnen Konversationen an.

        Die Aufzeichnungen enthalten keine personenbezogenen Daten. Sogar der Name des Benutzers, der an der Konversation teilgenommen hat, bleibt privat; stattdessen wird der Begriff <cite class="cite">Nicht angegeben</cite> verwendet. Alle anderen personenbezogenen Daten, die Benutzer im Verlauf der Konversation angeben, wie z. B. Telefonnummern oder Postleitzahlen, werden durch Variablen ersetzt, die die Art der bereitgestellten Daten angeben, jedoch nicht die Daten selbst.

        > **Hinweis:** Der Begriff *Interaktion* stellt eine Konversation zwischen dem Benutzer und dem virtuellen Agenten dar. Sie beginnt, wenn der Benutzer beginnt, mit dem virtuellen Agenten zu chatten, und endet, wenn die Sitzung im Chatfenster beendet wird (dies geschieht, wenn der Benutzer abgemeldet wird oder sich abmeldet und wenn der Benutzer das Chatfenster schließt oder aktualisiert). Eine Interaktion beinhaltet häufig mehr als nur einen Wortwechsel; Benutzer können auf Schaltflächen klicken, Grafiken wie z. B Karten anzeigen und weitere Transaktionen durchführen. Und anders als bei einem Anruf bei der Kundenunterstützung wird die Interaktion in der Chatsitzung mit dem virtuellen Agenten nicht beendet, sobald sich der Benutzer nicht mehr damit befasst. Der virtuelle Agent hat keine anderen Verpflichtungen. Er ist für den Fall da, dass der Benutzer etwas anderes machen oder fragen möchte. Wenn der Benutzer beispielsweise eine bestimmte Frage stellt und 20 Minuten später eine andere Frage stellt (und dies in derselben Sitzung im Chatfenster), dann werden beide Wortwechsel wie eine einzelne Interaktion mit einer Dauer von etwa 25 Minuten behandelt.

1. Wenn Sie aussagekräftige Daten ermitteln, die Sie für andere freigeben möchten, können Sie diese im CSV-Format exportieren.

