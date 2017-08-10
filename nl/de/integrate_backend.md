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

# Hinzufügen des Agenten zu einem vorhandenen Supportkanal
{: #integrate_backend}

Die {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-API wurde zur Unterstützung der einfachen Übertragung einer Konversation zwischen dem virtuellen Agenten und einem Menschen oder einem anderen Bot-Service innerhalb einer vorhandenen Unterstützungsinfrastruktur entwickelt. Genau genommen hat sich das Team von LivePerson, Inc. mit {{site.data.keyword.IBM}} zusammengetan, um eine solche Integration zu implementieren. Weitere Einzelheiten finden Sie nachfolgend unter [LiveEngage-Integration](integrate_backend.html#liveperson).
{: shortdesc}

Wenn Sie selbst eine einfache Lösung erstellen möchten, können Sie Ihre Anwendung so codieren, dass alle Funktionen, die für eine Übertragung auf einen menschlichen Agenten konfiguriert sind, an einen vorhandenen Kanal übergeben werden, der von Supportmitarbeitern überwacht wird. Weitere Informationen zur Übertragung einer Konversation, z. B. zu Slack, finden Sie unter [dW-Antworten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/318623/where-can-i-find-documentation-examples-on-integra/ "Symbol für externen Link"){: new_window}.

Führen Sie die folgenden Schritte aus, um den virtuellen Agenten über die {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-API in einen vorhandenen Supportkanal zu übertragen:

1.  Rufen Sie die API-Schlüssel ab, die zum Durchführen von API-Aufrufen erforderlich sind. Weitere Einzelheiten finden Sie unter [Abrufen von API-Schlüsseln](publish.html#api-keys).

1.  Interagieren Sie über die {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-REST-APIs programmgesteuert mit dem Bot. Rufen Sie das Portal **[{{site.data.keyword.IBM_notm}} developerWorks API Explorer](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}** auf, um auf die REST-APIs unter {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} zuzugreifen.

1.  Führen Sie zum Abrufen der Bot-ID einen der folgenden Schritte aus:
    - Führen Sie die folgenden Schritte aus, um die Bot-ID über die Benutzerschnittstelle des {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Konfigurationstools abzurufen:
      1.  Klicken Sie im Hauptmenü ![Symbol mit drei horizontalen Linien](images/hamburger.png) von {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} auf **Documentation (Dokumentation)** und anschließend auf die Registerkarte **Publish (Veröffentlichen)**.
      1.  Kopieren Sie den botID-Wert aus dem Skriptblock.

    - Führen Sie die folgenden Schritte aus, um die Bot-ID über die API Explorer-Website abzurufen:
      1.  Melden Sie sich bei [IBM developerWorks API Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/api/ "Symbol für externen Link"){: new_window} an. Klicken Sie auf **My APIs (Meine APIs)** und anschließend auf die {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Kachel.
      1.  Klicken Sie in der Navigationsleiste auf **Documentation>Retrieve Bot** (Dokumentation>Bot abrufen).
      1.  Klicken Sie im oberen Bereich des API Explorer-Referenzfensters auf **USE (Verwenden)**.
      1.  Blättern Sie unter dem Abschnitt *Path and Query parameters* (Pfad und Abfrageparameter) nach unten und klicken Sie auf **TEST**.
      >**Hinweis:** Bevor Sie einen Test durchführen können, müssen Sie einen Schlüssel für die Verwendung mit der API auswählen.

      1.  Die Bot-ID wird in der resultierenden Antwort im Parameter `bot_id` angezeigt.

## LiveEngage-Integration
{: #liveperson}

{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} wurde entwickelt, um in Einklang mit dem menschlichen Gegenstück zu arbeiten.

Beispiel: LivePerson, Inc., Anbieter mobiler Cloud- und Online-Lösungen für Geschäftsnachrichten, ist mit IBM eine Partnerschaft eingegangen, um ein {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Bot in das LiveEngage-Chaterlebnis zu integrieren. **LiveEngage** ist eine auf Unternehmen abgestimmte, cloudbasierte Plattform, über die Verbraucher direkt Nachrichten an ihre Lieblingsmarken senden können. Das neue Angebot, **LiveEngage with Watson (LiveEngage mit Watson)**, fügt Antworten aus einem {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Bot zur Interaktion hinzu. Dabei werden bei Bedarf Ansprechpartner aus dem Bereich Human Care nahtlos und in Echtzeit eingebracht.

Der LivePerson-Bot nutzt viele der folgenden, von {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} angebotenen Verhaltensweisen:

- Akzeptieren von Konversationen, die vom externen Service an den Agenten weitergeleitet werden.
- Auslösen der Übertragung von Konversationen auf den externen Service, unter folgenden Bedingungen:
    - Der Kunde möchte mit einem menschlichen Agenten sprechen.
    - Eine Funktion ist so konfiguriert, dass eine Weiterleitung an einen menschlichen Agenten erfolgt.
    - Der Kunde fragt nach einem Thema, das der Bot aufgrund seiner Konstruktion nicht erkennen und mit dem er sich nicht befassen kann.
- Identifizieren und Melden des Punkts in der Konversation, an dem der Benutzer den Bot nicht mehr versteht oder das Interesse an der Konversation verliert.
- Erkennen des Endes der Konversation und Benachrichtigen des Service, damit dieser mit Aktivitäten nach der Interaktion beginnt.
- Einschließen von Informationen zur Benutzerabsicht bei der Übertragung einer Konversation, damit die Konversation an den menschlichen Agenten weitergeleitet werden kann, der die meiste Erfahrung im Umgang mit Anforderungen dieser Art hat.
- Einschließen des Chatverlaufsprotokolls bei der Übertragung einer Konversation, damit die Person, die die Problembehandlung übernimmt, den Kontext der bisher stattgefundenen Konversation nachvollziehen kann.

Informationen zum Anfordern von Zugriff auf das Angebot finden Sie auf der [LivePerson-Website ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://engage.liveperson.com/usage/watson/?utm_medium=website&utm_source=IBM&utm_campaign=Watson "Symbol für externen Link"){: new_window}.
