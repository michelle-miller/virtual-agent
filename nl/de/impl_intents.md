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

# Implementieren zentraler Funktionen
{: #impl_intents}

Verstehen Sie Entwicklungsaufgaben, die zur Unterstützung der für bestimmte Funktionen ausgewählten Antworttypen ausgeführt werden müssen.
{: shortdesc}

Überlegen Sie, wie Sie mindestens die folgenden Funktionen behandeln möchten:

- ***Keines der Obigen***

    Die von Ihnen für diese Funktion definierte Antwort wird an Benutzer zurückgegeben, wenn diese eine Eingabe machen, die vom System nicht erkannt wird und einer aktivierten Funktion zugeordnet wird. Folglich kann sie Benutzern häufig angezeigt werden, insbesondere dann, wenn Sie nicht viele Funktionen aktiviert haben. Überlegen Sie sich, wie der virtuelle Agent antworten soll. Eine Textantwort, wie z. B. <cite class="cite">Es tut mir Leid, ich verstehe leider nicht, wonach Sie fragen.</cite> genügt. Wenn Sie Benutzern die Möglichkeit geben möchten, sich an einen menschlichen Agenten zu wenden, können Sie folgenden Text einschließen: <cite class="cite">Geben Sie\"Agent\" ein, um an einen menschlichen Agenten weitergeleitet zu werden.</cite> Durch diese Eingabe wird das Ereignis `Agent` ausgelöst, das nachfolgend erläutert wird. Weitere Informationen finden Sie unter [Wie Keines der Obigen verwendet wird](/docs/services/virtual-agent/personalize.html#none_of_the_above).

- **Absicht *Mit Agenten verbinden* und Funktionen mit dem Antworttyp *An menschlichen Agenten weiterleiten***

    Über diese Funktionen wird der Benutzer an einen menschlichen Agenten weitergeleitet. Sie müssen eine Logik hinzufügen, die die Konversation an Ihre Supportmitarbeiter weiterleitet. Ein möglicher Ansatz besteht darin, eine Logik hinzuzufügen, die eine Verbindung zu einem externen Service herstellt, mit dem bereits eingehende Anforderungen auf Ihrer Site zur Kundenunterstützung verwaltet werden. Probleme, mit denen sich der virtuelle Agent nicht befassen kann, werden als Bestandteil der zugehörigen vorhandenen Warteschlange für zu priorisierende und zu bearbeitende Support-Anforderungen an die Mitarbeiter des Support-Teams weitergeleitet. Zur Implementierung der Transferlogik müssen Sie für das Ereignis `Agent` empfangsbereit sein und die durchzuführenden Funktionen bei der Auslösung des Ereignisses definieren. Entsprechende Ideen finden Sie unter [dwAnswers ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/search.html?f=&amp;type=question&amp;redirect=search/search&amp;q=watson-virtual-agent&amp;q=human){: new_window}.

- **Funktionen mit dem Antworttyp *Integrierte Konversation verwenden***

    Wenn Sie die Standardeinstellungen für die zentralen Funktionen beibehalten, die für die Verwendung des Antworttypen für integrierte Konversationen konfiguriert sind, und diese Funktionen aktiviert sind, müssen Sie eine entsprechende Logik hinzufügen, um den Informationsaustausch und die Geschäftstransaktionen zu unterstützen, die in den integrierten Konversationen bearbeitet werden. Weitere Einzelheiten finden Sie unter [Implementieren einer Logik zur Unterstützung einer integrierten Konversation](/docs/services/virtual-agent/impl_intents.html#backend_transaction).

- **Funktionen mit dem Antworttyp *Eigene Konversation verwenden***

    Bei komplexen Funktionen, bei denen der Informationsaustausch mit dem Benutzer in einem benutzerdefinierten Dialog ausgeführt werden muss, können Sie mithilfe des {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}-Service einen Dialog schreiben. Weitere Einzelheiten finden Sie unter [Hinzufügen benutzerdefinierter Dialoge für zentrale Funktionen](/docs/services/virtual-agent/personalize.html#use_custom).

## Implementieren einer Logik zur Unterstützung einer integrierten Konversation
{: #backend_transaction}

Hier erfahren Sie, wie Informationen und vollständige Geschäftsprozesse ausgetauscht werden, die bei einer Interaktion der Benutzer mit Funktionen auftreten können, in denen die integrierte Konversation verwendet wird.

### Informationen zu dieser Aufgabe

Einige der zentralen Funktionen, die so konfiguriert wurden, dass der Antworttyp für eine integrierte Konversation verwendet wird, können Geschäftsprozesse standardmäßig abwickeln.Ihre Anwendung muss die Transaktion mit den Back-End-Systemen des Datensatzes registrieren können.

- Wenn Sie das bereitgestellte {{site.data.keyword.IBM_notm}} Chat-Widget implementieren, werden Ereignisse erkannt, die durch bestimmte Benutzerantworten ausgelöst wurden. Sie müssen jedoch weitere Schritte ausführen, um in Ihrer Anwendung für diese Ereignisse empfangsbereit zu sein, damit Sie die eingeleiteten Transaktionen auf Ihren Back-End-Systemen abschließen können.
- Wenn Sie das bereitgestellte Chat-Widget nicht verwenden, müssen Sie sicherstellen, dass Ihre benutzerdefinierte Schnittstelle durch integrierte Konversationsflüsse ausgelöste Ereignisse erkennt und diese entsprechend bearbeitet. 

Bei der Funktion **Adresse aktualisieren** beispielsweise kann ein Benutzer die Rechnungsadresse in seinem Konto ändern. Sie müssen Code schreiben, der die neue Adresse über den virtuellen Agenten abruft und das Benutzerkonto in Ihren Datenbeständen mit den neuen Informationen aktualisiert.

Zu beachten ist, dass der Zweck eines Dialogs nur darin besteht, Benutzerinformationen zu sammeln. Es gibt zwei Möglichkeiten zum Speichern der vom Benutzer bereitgestellten Informationen:

- Informationen, die nicht vertraulich oder privat sind, werden im Dialogkontext gespeichert. Dies ist ein Datenobjekt, das im Bot und in Ihrer Anwendung verfügbar ist.
- Vertrauliche oder private Informationen (z. B. Kreditkartennummern) werden in privaten Variablen gespeichert. Diese sind nur in Ihrer Anwendung verfügbar und werden nicht an den Bot übergeben.

### Verfahren

Führen Sie die folgenden Schritte aus, um Geschäftstransaktionen vollständig zu implementieren, die über Funktionen mit Antworten in einer integrierten Konversation ausgelöst wurden:

1. Fügen Sie eine Logik zu Ihrer Anwendung hinzu, die über das Back-End-System Profilinformationen für den aktuellen Benutzer abruft, die im Chatfenster angezeigt werden sollen, bevor die Informationen geändert werden. Beispiel: Zeigen Sie Benutzern einen Kontosaldo an, bevor sie ihn zahlen.

    Verwenden Sie die Aktion `getUserProfileVariables`. Mit dieser Aktion werden die Variablen abgerufen und im Profil festgelegt.

    ```
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     var variables = data.message.action.args.variables; // Geben Sie die Variablen an, die in diesem Array für
       (var i = 0; i < variables.length; i++) {
           var value = something(variables[i]) abgerufen werden sollen
           /*Führen Sie eine Aktion aus, um den Wert von 'variables[i]' abzurufen. Dies könnte ein Ajax-Aufruf sein oder der Abruf
           von Daten über lokale Cookies. Dies hängt davon ab, wo Sie die Informationen gespeichert haben.*/
           window.IBMChat.profile.set(variables[i], value);
       }
       IBMChat.sendSilently('success'); // bzw. 'cancel' oder 'failure'
    });
    ```
    {: screen}

    In diesem Beispiel wird ein REST-Aufruf zum Abrufen von Informationen zu einem Rechnungssaldo und -fälligkeitsdatum verwendet.

    ```
    var xmlHttp = new XMLHttpRequest();
      xmlHttp.onreadystatechange = function() { 
        if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
          callback(xmlHttp.responseText);
      }
      xmlHttp.open("GET", url, true);
      xmlHttp.send(null);
    }
    /* Rufen Sie Informationen von der Back-End-Datenbank ab und fügen Sie diese
    zum Profil mit IBMChat.profile.set() hinzu. */
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     /*
     data = {
       message: {
          text: ['some text'],
                action: {
                     name: 'getUserProfileVariables',
                     args: {
                         variables: [
                    "bill_amount",
                    "payment_due_date"
                ]
                     }
                }
       }
       
     }
     */
      
     httpGetAsync('http://yourdomain.com/userprofile', function(user) {
       /* Der Datensatz im Back-End-System gibt möglicherweise Informationen wie diese zurück.
       user = {
         "bill_amount": 42.01,
         "payment_due_date": "11/24/2008"
       }
       */
       var variables = data.message.action.args.variables;
       for (var i = 0; i < variables.length; i++) {
         var value = user[variables[i]]);
         window.IBMChat.profile.set(variables[i], value);
       /* Nun können im Chat-Widget die Werte verwendet werden, die vom Back-End-Service abgerufen wurden. */
       }
       IBMChat.sendSilently('success'); // bzw. 'cancel' oder 'failure'
     });
    });
    ```
    {: screen}

1. Fügen Sie eine Logik zu Ihrer Anwendung hinzu, die zunächst für die Aktion empfangsbereit ist, die den Geschäftsprozess eingeleitet hat, und anschließend den Geschäftsprozess ausführt.

    Eine Liste der Aktionen, die Funktionen mit Antworttypen für integrierte Konversationen zugeordnet sind, finden Sie unter [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action){: new_window}.
    - **Zahlung leisten** {: #makeapayment}

        Führen Sie die folgenden Schritte aus, um Code zu implementieren, der diese Transaktion unterstützt.
        1. Ihre Anwendung muss den aktuellen Saldo und das Fälligkeitsdatum des Benutzers vom Back-End-System abrufen. Verwenden Sie die Methode `action:getUserProfileVariables`, um die Variablen `bill_amount` und `payment_due_date` im Profilspeicher abzurufen und festzulegen.
        1. Ihre Anwendung muss für das Ereignis `payBill` empfangsbereit sein und die beim Auslösen des Ereignisses durchzuführende Logik definieren.
        1. Zudem muss Ihre Anwendung für das Ereignis `sendPaymentReceipt` empfangsbereit sein und die beim Auslösen des Ereignisses durchzuführende Logik definieren.

    - **Adresse aktualisieren** {: #updateaddress}

        1. Im Chat-Widget wird ein Formularlayout verwendet, in dem nach den neuen Adressinformationen des Benutzers gefragt wird, die automatisch im Profil gespeichert werden. Folgende Profilvariablen werden darin gespeichert:

            ```
            user_street_address1
            user_street_address2
            user_locality
            user_state_or_province
            user_zipcode
            ```
            {: screen}

        1. Ihre Anwendung muss für das Ereignis `updateAddress` empfangsbereit sein.

            ```
            IBMChat.subscribe('action:updateAddress', function(data) {<your-code>}
            ```
            {: screen}

            Definieren Sie eine Funktion, über die die neue Adresse und der Adresstyp (`address_type`) abgerufen und an das Back-End-System gesendet werden, wenn die Aktion `updateAddress` ausgelöst wird.

            Sie können das in das Chat-Widget integrierte Formularlayout verwenden, um Daten mit vielen Werten zu sammeln, z. B. eine Straßenadresse. Benutzer geben Werte in mehrere Felder ein und übergeben anschließend das gesamte Formular. Sie können beispielsweise eine Logik wie die folgende verwenden, um die neue Adresse über einen REST-POST-Aufruf an Ihre Site zu senden.

            ```
            /* Wenn ein Benutzer Informationen in ein Formular eingibt, werden diese automatisch zum
            Benutzerprofil hinzugefügt. In einem typischen Fluss würde demnach ein Formularlayout in das
            Chatfenster eingeschlossen und nach der Übergabe des Formulars würde diese Aktion aufgerufen */
            IBMChat.subscribe('action:updateAddress', function(data) {
              var record = {
                "first_name": IBMChat.profile.get('first_name'),
                "last_name": IBMChat.profile.get('last_name'),
                "user_street_address1": IBMChat.profile.get('user_street_address1'),
                "user_street_address2": IBMChat.profile.get('user_street_address2'),
                "user_locality": IBMChat.profile.get('user_locality'),
                "user_state_or_province": IBMChat.profile.get('user_state_or_province'),
                "user_zipcode": IBMChat.profile.get('user_zipcode')
              };
              httpPostAsync('/updateRecord/', record, function(err, response) {
                if (err) IBMChat.receive('There was an error updating the address.');
              });
            });
            ```
            {: screen}

            Weitere Informationen zu integrierten Layouts finden Sie unter [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout){: new_window}.

    - **Aktualisieren der Telefonnummer des Kontakts** {: #updatephone}

        1. Im Chat-Widget wird ein Formularlayout verwendet, in dem nach der neuen Telefonnummer des Benutzers gefragt wird, die automatisch im Profil gespeichert werden. Folgende Profilvariablen werden darin gespeichert:

            ```
            user_phone_number
            phone_number_type
            ```
            {: screen}

        1. Ihre Anwendung muss für das Ereignis `updatePhoneNumber` empfangsbereit sein und die beim Auslösen des Ereignisses durchzuführende Logik definieren, mit der die neue Telefonnummer und der -typ abgerufen und an das Back-End-System gesendet werden.

    - **Aktualisieren der E-Mail-Adresse** {: #updateemail}

        1. Im Chat-Widget wird ein Formularlayout verwendet, in dem nach der neuen E-Mail-Adresse des Benutzers gefragt wird, die automatisch im Profil gespeichert werden. Folgende Profilvariablen werden darin gespeichert:

            ```
            user_email_address
            email_type
            ```
            {: screen}

        1. Ihre Anwendung muss für das Ereignis `updateEmail` empfangsbereit sein und die beim Auslösen des Ereignisses durchzuführende Logik definieren, mit der die neue E-Mail-Adresse abgerufen und an das Back-End-System gesendet wird. Zudem sendet sie Informationen darüber, für welche Benachrichtigungstypen die neue Adresse verwendet werden soll (`email_type`).

