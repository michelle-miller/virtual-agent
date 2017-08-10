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

# Konfigurieren zentraler Funktionen 
{: #configure}

Zur Konfiguration Ihres Bots müssen Sie die Funktionen auswählen, die darin enthalten sein sollen.
{: shortdesc}

Eine Funktion ist die Fähigkeit Ihres virtuellen Agenten, mit der ein bestimmtes Kundenziel erkannt und erfüllt werden soll. Weitere Einzelheiten finden Sie unter [Funktionen](how-it-works.html#capabilities).

Wenn Sie eine zentrale Funktion verwenden möchten, müssen Sie lediglich angeben, wie sich der Agent verhalten soll, wenn die Funktion ausgeführt wird. Bei einigen Funktionen reicht es möglicherweise aus, wenn für eine Benutzeranfrage eine vordefinierte Textantwort zurückgegeben wird. Bei anderen Funktionen ist möglicherweise ein komplexer Konversationsfluss erforderlich, damit Informationen gesammelt werden können, die zum Durchführen einer Transaktion erforderlich sind. In einem solchen Fall sammelt der Agent Informationen und übergibt diese an die Anwendung, die die erforderlichen Geschäftsprozesse implementieren muss.

Standardmäßig sind alle zentralen Funktionen aktiviert und weisen vorformulierte Antworten auf. Zunächst müssen Sie entscheiden, ob alle Funktionen inaktiviert werden sollen, die Ihr Agent nicht benötigt. Bei Funktionen, die Sie beibehalten möchten, müssen Sie die vorformulierten Antworten durch Antworten ersetzen, die Informationen zu Ihrem Geschäft widerspiegeln.

Führen Sie die folgenden Schritte aus, um eine zentrale Funktion zu konfigurieren:

1.  Öffnen Sie die Seite **Capabilities (Funktionen)**, um eine Liste mit Funktionen anzuzeigen, die nach Kategorie gruppiert sind und vom aktuellen Agenten unterstützt werden.

1.  Überprüfen Sie die Funktionen und entscheiden Sie, welche Ihr Bot unterstützen soll. Alle Funktionen sind aktiviert, es sei denn, Sie inaktivieren sie.

    Klicken Sie zum Aktivieren oder Inaktivieren einer Funktion auf den Switch. Klicken Sie auf das Menü **More (Mehr)** ![Symbol mit drei horizontalen Linien](images/kabob.png) auf der Kategoriekachel und wählen Sie anschließend **Turn All Off (Alle inaktivieren)** aus, um alle Funktionen in einer Kategorie zu inaktivieren.

    Bei einer Funktion, die Sie nicht unterstützen möchten, bei der Sie jedoch vermuten, dass ein Kunde danach fragen könnte, können Sie alternativ entscheiden, sie aktiviert zu lassen, und eine Textantwort bereitstellen, in der erklärt wird, dass Sie diese Funktion nicht unterstützen. Wenn Sie beispielsweise keine Versicherung anbieten, könnten Sie die Funktion **Versicherung hinzufügen** aktivieren, statt sie zu inaktivieren. Wählen Sie als Antworttyp **Text** aus. Fügen Sie im zugehörigen Feld **Message (Nachricht)** die Textantwort *Wir bieten keine Versicherung für unsere Produkte an* hinzu.

1.  Klicken Sie zum Konfigurieren einer Funktion auf den Namen der Funktion.

1.  Wählen Sie den Antworttyp aus, der dem Benutzer angezeigt werden soll, wenn diese Funktion ausgelöst wird. Folgende Optionen stehen zur Verfügung:

    ![Zeigt, dass jede Absicht den Antworttypen Textantwort anzeigen, Integrierte Konversation verwenden, Eigene Konversation verwenden oder An menschlichen Agenten übertragen aufrufen kann](images/responsetypes.png)

    - **Text**

        Bei einfachen Anfragen können Sie mit dem Konfigurationstool eine Standardtextantwort angeben, die dem Benutzer angezeigt werden soll. Dieser Antworttyp ist bei Anfragen hilfreich, die einfache Antworten aufweisen und bei denen das Sammeln zusätzlicher Informationen oder jegliche Interaktion mit anderen Systemen nicht erforderlich ist. Bei der Absicht \"Anfrage bzgl. der Zahlungsmethode\" könnten Sie die Textantwort `Wir akzeptieren Kreditkarten von allen großen Kreditkartenunternehmen` angeben.

        Wenn Sie den Antworttyp **Text** auswählen, müssen Sie auch den Antworttext angeben.

    - **Built-In (Integriert)**

        Die vordefinierten Dialoge, in denen zusätzliche Informationen gesammelt werden oder in denen eine komplexe Handhabung implementiert wird, umfassen eine Reihe von Funktionen. Ein *Dialog* stellt die Struktur für eine Konversation mit dem Benutzer bereit. Weitere Informationen darüber, welche Funktionen diesen Antworttyp unterstützen und wie die Konversation bei einer Implementierung fließt, finden Sie unter [Integrierte Dialoge](configure.html#builtin_dialog_ovw).

        Wenn Sie den Antworttyp **Built-in (Integriert)** auswählen, müssen Sie möglicherweise auch zusätzliche Daten konfigurieren, die im Dialog verwendet werden, um dem Benutzer Auswahlmöglichkeiten aufzuzeigen (z. B. Filialstandorte oder Zahlungsmethoden). In vielen Fällen muss Ihre Anwendung für Ereignisse empfangsbereit sein, die durch den Dialog ausgelöst werden können und Aktionen in Ihren Datenbeständen implementieren. Weitere Einzelheiten finden Sie unter [Implementieren einer Logik zur Unterstützung einer integrierten Konversation](impl_intents.html#backend_transaction).

    - **Use your own conversation (Eigene Konversation verwenden)**

        Wenn Sie bei einer Funktion komplexe Kundeninteraktionen implementieren müssen, können Sie Ihren eigenen Dialog erstellen, in dem die Konversation mit dem Kunden gestaltet wird. Für diese Option sind zusätzliche Schritte erforderlich. Dazu zählt das Erstellen eines benutzerdefinierten Dialogs mit dem {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service und das Verknüpfen des Dialogs mit dem Agenten. Entsprechende Einzelheiten finden Sie unter [Erstellen eines benutzerdefinierten Dialogs](add-custom-dialog.html).

    - **Transfer to human agent (An menschlichen Agenten übertragen)**

        Sie können für jede Funktion, die Sie nicht mit dem virtuellen Agenten behandeln möchten, angeben, dass ein Ereignis ausgelöst werden soll, in dem ein menschlicher Agent angefordert wird. Ihre Anwendung kann anschließend über Ihre Prozesse zur Initialisierung einer Chatsitzung mit einem Kundendienstmitarbeiter auf dieses Ereignis antworten.

        Wenn Sie den Antworttyp **Transfer to human agent (An menschlichen Agenten übertragen)** auswählen, können Sie eine Nachricht angeben, die Kontext für die Kundenanfrage enthält, der auch an den menschlichen Agenten übergeben werden soll.

1.  Klicken Sie zum Speichern Ihrer Auswahl auf **Save (Speichern)**. Nehmen Sie alle weiteren Änderungen vor, die basierend auf dem Antworttyp erforderlich sind, und speichern Sie diese.

    Sie können auf den rückwärts gerichteten Pfeil klicken, um den Namen der Funktion zur Seite \"Funktionen\" zurückzugeben.

## Integrierte Dialoge 
{: #builtin_dialog_ovw}

In den folgenden Abschnitten werden die zentralen Funktionen beschrieben, bei denen die integrierten Konversationsflüsse dafür trainiert wurden, diese zu erkennen und darauf zu reagieren.

### Nächstgelegene Filiale suchen
{: #builtin_dialog_ovw__findNearestStore}

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Nächstgelegene Filiale suchen*. Für diese Funktion und die Funktion *Filialstandort* wird der gleiche Dialogfluss verwendet.

![Zeigt die Knoten der Dialoge mit den Absichten Nächstgelegene Filiale suchen und Filialstandort.](images/findNearestStore.png)

In dem einzigen zusätzlichen Schritt, der von Ihnen erforderlich ist, müssen Sie bei jeder Filiale Details zum Filialstandort hinzufügen. Sie können die Details zur Filiale über eine der folgenden Funktionen hinzufügen, auf die Sie über die Seite \"Konfigurieren\" Zugriff haben:

- Nächstgelegene Filiale suchen
- Filialstandort

### Zahlung leisten

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Zahlung leisten*.

![Zeigt die Knoten des Dialogs an.](images/makeAPayment.png)

Klicken Sie auf [hier](backend_payment_gif.html#backend_payment_gif), um zu sehen, wie die Benutzereingabe und die Antworten des virtuellen Agenten durch das System fließen.

Informationen zu zusätzlichen Schritten, die Sie ausführen müssen, damit diese Funktion vollständig unterstützt wird, finden Sie unter [Implementieren einer Logik zur Unterstützung einer integrierten Konversation](impl_intents.html#makeapayment).

### Geschäftszeiten

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Geschäftszeiten*.

![Zeigt die Knoten des Dialogs mit der Absicht Geschäftszeit.](images/storeHours.png)

Wenn Sie Geschäftszeiten angeben möchten, müssen Sie die Informationen zu den Geschäftszeiten beim Hinzufügen der Informationen zum Filialstandort über folgende Funktionen einschließen:

- Nächstgelegene Filiale suchen
- Filialstandort

### Filialstandort

Das oben stehende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Filialstandort*. Für diese Funktion und die Funktion [Nächstgelegene Filiale suchen](configure.html#builtin_dialog_ovw__findNearestStore) wird der gleiche Dialogfluss verwendet.

In dem einzigen zusätzlichen Schritt, der von Ihnen erforderlich ist, müssen Sie bei jeder Filiale Details zum Filialstandort hinzufügen. Sie können die Details zur Filiale über eine der folgenden Funktionen hinzufügen, auf die Sie über die Seite \"Konfigurieren\" Zugriff haben:

- Nächstgelegene Filiale suchen
- Filialstandort

### Telefonnummer der Filiale

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Telefonnummer der Filiale*.

![Zeigt die Knoten des Dialogs mit der Absicht Telefonnummer der Filiale.](images/storePhoneNumber.png)

Wenn Sie Telefonnummern einer Filiale angeben möchten, müssen Sie diese zu den Definitionen des Filialstandorts hinzufügen, die Sie über folgende Funktionen hinzufügen:

- Nächstgelegene Filiale suchen
- Filialstandort

### Adresse aktualisieren

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Adresse aktualisieren*.

![Zeigt die Knoten im Dialog Adresse aktualisieren.](images/updateAddress.png)

Informationen zu zusätzlichen Schritten, die Sie ausführen müssen, damit diese Funktion vollständig unterstützt wird, finden Sie unter [Implementieren einer Logik zur Unterstützung einer integrierten Konversation](impl_intents.html#updateaddress).

### Aktualisieren der Telefonnummer des Kontakts

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *Telefonnummer des Kontakts aktualisieren*.

![Zeigt die Knoten im Dialog Telefonnummer des Kontakts aktualisieren.](images/updatePhoneNumber.png)

Informationen zu zusätzlichen Schritten, die Sie ausführen müssen, damit diese Funktion vollständig unterstützt wird, finden Sie unter [Implementieren einer Logik zur Unterstützung einer integrierten Konversation](impl_intents.html#updatephone).

### Aktualisieren der E-Mail-Adresse

Das folgende Diagramm zeigt die Knoten in der integrierten Konversation für die Funktion *E-Mail-Adresse aktualisieren*.

![Zeigt den Knoten im Dialog zur Aktualisierung der E-Mail-Adresse an.](images/updateEmail.png)

Informationen zu zusätzlichen Schritten, die Sie ausführen müssen, damit diese Funktion vollständig unterstützt wird, finden Sie unter [Implementieren einer Logik zur Unterstützung einer integrierten Konversation](impl_intents.html#updateemail).
