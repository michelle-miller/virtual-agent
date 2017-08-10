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

# Erstellen eines Agenten
{: #agent-create}

Wenn Sie den Service abonnieren, wird ein Bot mit aktiviertem Funktionspack namens **General Customer Service (Allgemeiner Kundendienst)** in englischer Sprache für Sie bereitgestellt. Sie können weitere Bots mit anderen Funktionspacks erstellen oder Bots für Kunden in anderen Sprachen als Englisch.
{: shortdesc}

Wenn Sie statt Ihres primären Agenten einen Agenten mit einem anderen Funktionspack verwenden möchten, müssen Sie zunächst einen neuen Agenten mit Ihrem gewünschten Funktionspack erstellen. Anschließend können Sie den Agenten löschen, der anfangs für Sie bereitgestellt worden ist. Stellen Sie sicher, dass Sie diesen Wechsel vornehmen, bevor Sie zu viel Zeit in die Konfiguration des Agenten \"General Customer Service\" (Allgemeiner Kundendienst) stecken. Weitere Informationen finden Sie unter [Löschen eines Agenten](agent-create.html#delete).

Wenn Sie Zeit damit verbringen, eine Agenteninstanz so zu konfigurieren, dass sie Ihren Anforderungen entspricht, und diese für die Verwendung implementieren möchten, aber weiterhin damit experimentieren möchten bzw. Verbesserungsideen austesten möchten, können Sie den Agenten klonen und für Testzwecke eine Kopie erstellen. Weitere Einzelheiten finden Sie unter [Klonen eines Agenten](agent-create.html#clone).

## Agentenbegrenzungen

Wie viele Agenten Sie erstellen können, hängt von Ihrem Serviceplan ab.

| Serviceplan      |      Anzahl der Agenten |
|------------------|----------------------:|
| Test             |                     2 |
| Standard         |                    10 |
| Premium          |                   100 |

Beachten Sie, dass die API-Aufrufe, die über mehrere bereitgestellte Bots durchgeführt werden, addiert werden und in die Gesamtzahl der Ihrem Abonnement zugewiesenen virtuellen Agentenantworten mit eingerechnet werden.

### Verfahren

Führen Sie die folgenden Schritte aus, um einen Agenten zu erstellen.

1.  Klicken Sie im Hauptmenü ![Symbol mit drei horizontalen Linien](images/hamburger.png) auf **Create New Agent (Neuen Agenten erstellen)**.

1.  Wählen Sie den Typ des Funktionspacks aus, mit dem der Agent bei seiner Erstellung bereitgestellt werden soll. Die Kachel gibt an, welche Sprachen unterstützt werden. Es sind jedoch nicht alle Funktionen in jeder Sprache verfügbar. Klicken Sie auf den Link **Show Details (Details anzeigen)**, um eine vollständige Liste der unterstützten Funktionen pro Sprache anzuzeigen.

1.  Klicken Sie auf einer Funktionspack-Kachel auf **Select (Auswählen)**, um einen neuen Agenten zu erstellen, der mit diesem Packtyp bereitgestellt wird.

1.  Wählen Sie ggf. die Sprache aus und geben Sie anschließend die angeforderten Informationen für den Agenten an.
   >**Hinweis:** Die hier von Ihnen angegebene Bezeichnung des Agenten wird nur in den Watson Virtual Agent-Administrationstools angezeigt, mit denen Sie den Agenten verwalten. Es ist nicht der Name der Persönlichkeit des virtuellen Agenten, der mit Ihrem Benutzer interagiert. Sie können dies auf der Seite **Settings (Einstellungen)** entsprechend definieren oder ändern.
1.  Klicken Sie auf **Create (Erstellen)**.

## Klonen eines Agenten
{: #clone}

Klonen Sie einen Agenten, um einen neuen Agenten mit der Konfiguration und den Einstellungen des ursprünglichen Agenten zu erstellen. Nach dem Klonen des Agenten sind der ursprüngliche Agent und der neue Agent nicht mehr aneinander gebunden. Änderungen, die Sie an einem der Agenten vornehmen, finden **nicht** auf den anderen Agenten Anwendung.

Sie können den Klon eines Agenten nicht in einer Sprache erstellen, die sich von der Sprache der ursprünglichen Agenten unterscheidet.

### Verfahren

Führen Sie die folgenden Schritte aus, um einen Agenten zu erstellen.

1.  Öffnen Sie die Seite **Settings (Einstellungen)** des Agenten, den Sie klonen möchten.

1.  Blättern Sie abwärts und klicken Sie anschließend auf **Clone Agent (Agent klonen)**.

1.  Geben Sie die angeforderten Informationen für den Agenten an.
   >**Hinweis:** Die hier von Ihnen angegebene Bezeichnung des Agenten wird nur in den Watson Virtual Agent-Administrationstools angezeigt, mit denen Sie den Agenten verwalten. Es ist nicht der Name der Persönlichkeit des virtuellen Agenten, der mit Ihrem Benutzer interagiert. Sie können dies an einer anderen Stelle definieren.
1.  Klicken Sie auf **Clone (Klonen)**.

## Löschen eines Agenten
{: #delete}

Wenn Sie einen Agenten nicht verwenden, sollten Sie ihn löschen, damit er nicht weiter bei der Begrenzung der Anzahl Ihrer Agenten mit eingerechnet wird.

### Verfahren

Führen Sie die folgenden Schritte aus, um einen Agenten zu erstellen.

1.  Öffnen Sie die Seite **Settings (Einstellungen)** des Agenten, den Sie löschen möchten.

1.  Blättern Sie abwärts und klicken Sie anschließend auf **Delete Agent (Agent löschen)**.

1.  Wenn Sie dazu aufgefordert werden, geben Sie den Text `Delete` (Löschen) ein und klicken Sie anschließend auf **OK**.
