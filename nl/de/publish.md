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

# Veröffentlichen des Agenten als Demo
{: #publish}

Sie können den Agenten in weniger als 10 Minuten auf einer Testwebsite veröffentlichen, um ihn mit Kollegen gemeinsam zu nutzen und gemeinsam zu beurteilen, ob der Agent die Bedürfnisse Ihrer Organisation erfüllt. {: shortdesc}

Führen Sie die folgenden Schritte aus, um den Agenten auf einer Testwebsite zu veröffentlichen:

1.  Bestimmen Sie, wo auf der Seite das Chatfenster des Bots angezeigt werden soll. Fügen Sie bei dem HTML-Element `<div>`, das den Zielbereich definiert, ein ID-Attribut hinzu, wenn keines definiert ist. Sie verwenden das ID-Attribut zu einem späteren Zeitpunkt, um auf das Element zu verweisen. Beispiel: `<div id="ibm-chat-root"></div>`.

1.  Befolgen Sie die Anweisungen unter [Abrufen von API-Schlüsseln](publish.html#api-keys), um folgende Schlüssel abzurufen:
    - Client-ID
    - Geheimer Clientschlüssel

1.  Klicken Sie im Hauptmenü ![Icon with three horizontal lines](images/hamburger.png) auf **Documentation (Dokumentation)** und blättern Sie dann abwärts zum Abschnitt **Publish (Veröffentlichen)**.

1.  Wenn Sie mehrere Agenten haben, klicken Sie auf den Abwärtspfeil, um die Bot-ID für den Agenten abzurufen, den Sie veröffentlichen möchten.

    Diese Bot-ID ist die ID, die vom Service generiert und Ihrem Bot zugeordnet wurde.

    Ein Scriptblock wird erstellt und auf der Seite angezeigt. Dieses Script kann kopiert und in eine HTML-Seite eingestellt werden, um den Agenten auf der Seite auszugeben. Sie
müssen einige der Werte im Script durch die entsprechenden Werte für Ihre Instanz ersetzen.

1.  Kopieren Sie den Scriptblock und fügen Sie ihn in einen Text- oder HTML-Editor ein.

    ``` Javascript
    <script src='https://unpkg.com/@watson-virtual-agent/chat-widget@1.6.0/dist/chat.min.js'>
    </script>
    <script>
      IBMChat.init({
        el: 'ibm_chat_root',
        baseURL: 'https://api.ibm.com/virtualagent/run/api/v1',
        botID: 'YOUR_BOT_ID',
        XIBMClientID: 'YOUR_IBM_CLIENT_ID',
        XIBMClientSecret: 'YOUR_IBM_CLIENT_SECRET'
      });
    </script>
    ```

1.  Ersetzen Sie folgende Attributwerte:
    - **el**: Geben Sie die ID des Elements an, das Sie in Schritt 1 zur Verwendung ausgewählt haben.
    - **XIBMClientID**: Fügen Sie den Wert der Client-ID hinzu, die Sie zuvor kopiert haben.
    - **XIBMClientSecret**: Fügen Sie den Wert des geheimen Clientschlüssels hinzu, den Sie zuvor kopiert haben.

   Verwenden Sie die im Skript angegebenen Werte baseURL und botID; sie werden vom Service generiert.

   **Wichtig:** Halten Sie die Werte von XIBMClientID und XIBMClientSecret so privat wie möglich.

1.  Integrieren und initialisieren Sie das Watson Virtual Agent-Chat-Widget, indem Sie das überarbeitete Skript auf Ihrer Webseite einfügen.

   Fügen Sie das Skript so nah wie möglich am schließenden Tag `</body>` hinzu, um zu verhindern, dass das Skript das Rendering der restlichen Seite blockiert. Zudem wird mit dieser Platzierung sichergestellt, dass unabhängig davon, welches Element Sie dem Skript zugeordnet haben, dieses Element bis zur Ausführung des Skripts vollständig gerendert wird.

1.  Aktualisieren Sie die Webseite und testen Sie den Agenten.

   Das Chat-Widget wird dem HTML-Element zugeordnet, das Sie in Schritt 1 entworfen haben, und mit ihm gerendert haben. Sie können dieses Element ein- oder ausblenden und positionieren. Das Widget wird auf die Standardhöhe und -breite des Elements erweitert. Die maximale Breite umfasst 768 Pixel und die minimale Höhe 300 Pixel.

Wenn Sie bereit sind, den Agenten für die direkte Hilfe Ihrer Kunden einzusetzen, müssen Sie einige zusätzliche Schritte ausführen.
Weitere Einzelheiten finden Sie unter [Integrieren des Agenten](integrate.html).

## Abrufen von API-Schlüsseln
{: #api-keys}

Folgende Schlüssel müssen API-Aufrufen zugeordnet werden, die an den Service gesendet werden, um zu beweisen, dass Sie über eine Berechtigung für die Verwendung der Watson Virtual Agent-API-Services verfügen:

- Client-ID
- Geheimer Clientschlüssel

Führen Sie die folgenden Schritte aus, um die Berechtigungsnachweise abzurufen.

1.  Rufen Sie die Website [IBM developerWorks API Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/api/ "Symbol für externen Link"){: new_window} auf und melden Sie sich mit derselben IBM ID an, mit der Sie sich für das Serviceabonnement angemeldet haben. Erstellen Sie bei Bedarf einen Benutzernamen. Klicken Sie in der Seitenüberschrift auf den Link **My APIs (Meine APIs)**.

1.  Suchen Sie nach der {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Kachel und klicken Sie anschließend auf das ihr zugeordnete Schlüsselsymbol.

1.  Sofern nicht bereits geschehen, wählen Sie den Schlüssel aus, den Sie verwenden möchten. Für den Schlüssel werden zwei Berechtigungsnachweise generiert. Sie werden in zwei Feldern angezeigt, wobei die zugehörigen Werte verschlüsselt sind. Bewegen Sie den Mauscursor über die Felder.

1.  Klicken Sie auf die Schaltfläche **SHOW (Anzeigen)**, um die Verschlüsselung aus den Feldwerten zu entfernen.

1.  Sie müssen diese Werte später angeben. Daher sollten Sie sie in ein Textfeld kopieren.
    - Das erste Feld enthält den Schlüssel der Client-ID.
    - Das zweite Feld enthält den geheimen Clientschlüssel.

  ![Knoten hinzufügen](images/api-explorer.jpg)
