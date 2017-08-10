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

# Abrufen von API-Schlüsseln
{: #api-keys}

Folgende Schlüssel müssen API-Aufrufen zugeordnet werden, die an den Service gesendet werden, um zu beweisen, dass Sie über eine Berechtigung für die Verwendung der Watson Virtual Agent-API-Services verfügen:

- Client-ID
- Geheimer Clientschlüssel

{: shortdesc}

Führen Sie die folgenden Schritte aus, um die Berechtigungsnachweise abzurufen.

1.  Rufen Sie die Website [IBM developerWorks API Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/api/ "Symbol für externen Link"){: new_window} auf und melden Sie sich mit derselben IBM ID an, mit der Sie sich für das Serviceabonnement angemeldet haben. Erstellen Sie bei Bedarf einen Benutzernamen. Klicken Sie in der Seitenüberschrift auf den Link **My APIs (Meine APIs)**.

1.  Suchen Sie nach der {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}-Kachel und klicken Sie anschließend auf das ihr zugeordnete Schlüsselsymbol.

1.  Sofern nicht bereits geschehen, wählen Sie den Schlüssel aus, den Sie verwenden möchten. Für den Schlüssel werden zwei Berechtigungsnachweise generiert. Sie werden in zwei Feldern angezeigt, wobei die zugehörigen Werte verschlüsselt sind. Bewegen Sie den Mauscursor über die Felder.

1.  Klicken Sie auf die Schaltfläche **SHOW (Anzeigen)**, um die Verschlüsselung aus den Feldwerten zu entfernen.

1.  Sie müssen diese Werte später angeben. Daher sollten Sie sie in ein Textfeld kopieren.
    - Das erste Feld enthält den Schlüssel der Client-ID.
    - Das zweite Feld enthält den geheimen Clientschlüssel.

  ![Knoten hinzufügen](images/api-explorer.jpg)
