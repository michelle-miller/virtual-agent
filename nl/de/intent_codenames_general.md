---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-21"

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

# Absichtsnamen (Kundendiensts)
{: #intent_codenames_general}
{: #top}

[![Zurück](images/back-arrow.png) <!-- {display:block;"} -->](intent_codenames.html)

In der folgenden Tabelle werden die Absichtsnamen der einzelnen unterstützten Funktionen aufgelistet. Wenn Sie für eine Funktion Ihren eigenen {{site.data.keyword.conversationshort}}-Servicedialog bereitstellen möchten, muss Ihnen der entsprechende Absichtsname bekannt sein, damit Sie diesen im Dialog angeben können. Sie können den Namen hier suchen.
{: shortdesc}

| Zentrale Funktionen             | Funktion zugeordneter Absichtsname                     |
|---------------------------------|--------------------------------------------------------|
| Abfrage des Kontostands | #Billing-Balance_Inquiry |
| Abrechnung allgemein | #Billing-Misc |
| Adresse aktualisieren`*` | #Account_Management-Update_Change_Address |
| Aktualisierung der Zahlungsart | #Payment-Method_Of_Payment_Update |
| Akzeptierte Zahlungsarten | #Payment-Method_Of_Payment_Inquiry |
| Allgemeine Informationen | #Information-Misc |
| Anfrage der Rechnungsanschrift | #Account_Management-Billing_Address_Inquiry |
| Auftragsbearbeitung allgemein | #Order_Management-Misc |
| Bankdaten | #Payment-Bank_Information |
| Beendung | #Help-Ending |
| Begrüßung | #Help-Greetings |
| Berechtigte Benutzer | #Account_Management-Authorized_User |
| Bestellstatus | #Order_Management-Get_Product_Order_Status |
| Bestellung stornieren | #Order_Management-Cancel_Product_Order |
| Bestellung ändern | #Order_Management-Modify_Product_Order |
| Dienstleistungen der Filiale | #Information-Store_Services |
| E-Mail aktualisieren`*` | #Account_Management-Email_Change |
| Eine Zahlung tätigen`*` | #Payment-Make_A_Payment |
| Einzelgebührerklärung | #Billing-One_Time_Charges |
| Erstattung | #Payment-Refund_Payment |
| Fehlende oder falsche Zahlungen | #Payment-Missing_Misapplied_Payment |
| Hilfe | #Help-Help |
| Keines der Obigen | #Off_Topic-None_of_the_Above |
| Kontakt | #Information-Contact_Us |
| Konto eröffnen | #Account_Management-Open_Account |
| Konto löschen | #Account_Management-Close_Cancel_Account |
| Kontoberechtigungen | #Account_Management-Privileges |
| Kontonamensänderung`*` | #Account_Management-Name_Change |
| Kontoverwaltung allgemein | #Account_Management-Misc |
| Kundenkontonummer | #Account_Management-Account_Number_Inquiry |
| Kundenprofil | #Account_Management-Customer_Profile |
| Kundenreklamation | #Complaints-Misc |
| Kundentreueprogramm | #Account_Management-Customer_Loyalty_Program |
| Kundentreuestatus | #Account_Management-Loyalty_Status |
| Missbrauch | #Account_Management-Fraudulent_Use |
| Mit Kundenbetreuer verbinden | #Help-Connect_to_Agent |
| Nächstgelegene Filiale finden`*` | #Information-Find_Nearest_Store |
| Offene Stellen | #Information-Jobs |
| Online-Kontozugriff | #Online_Account_Access-Misc |
| Online-Rechnungen | #Billing-Online_Statements |
| Papierrechnungen | #Billing-Paper_Statements |
| Produkt bestellen | #Order_Management-Create_Product_Order |
| Profilkennwortabfrage | #Account_Management-Profile_Password |
| Profilsicherheitsfragen | #Account_Management-Profile_Security_Questions |
| Punkte einlösen | #Account_Management-Redeem_Points |
| Punkte übertragen | #Account_Management-Transfer_Points |
| Punktewert | #Account_Management-Points_Value |
| Ratenzahlung | #Payment-Installments |
| Rechnungserklärung | #Billing-Bill_Explanation |
| Rechnungskopie anfordern | #Billing-Bill_Copy |
| Rechnungskorrektur | #Billing-Request_Adjustment |
| Rechnungsreklamation | #Billing-Dispute |
| Rechnungszeitraum | #Billing-Billing_Cycle |
| Sicherheitsgarantie | #Help-Security_Assurance |
| Standort der Filiale`*` | #Information-Store_Location |
| Systeminformationen | #Help-Misc |
| Telefonnummer aktualisieren | #Account_Management-Update_Change_Contact_Phone_Number |
| Telefonnummer der Filiale`*` | #Information-Store_Phone_Number |
| Termin vereinbaren | #Information-Make_Appointment |
| Termin verschieben | #Information-Change_Appointment |
| Verfügbare Produkte | #Information-Store_Products |
| Verspätungszuschlag | #Payment-Late_Fees |
| Wiederkehrende Gebühren | #Billing-Recurring_Charges |
| Wiederkehrende Zahlungen (autopay) | #Payment-Recurring_Payment_Autopay |
| Zahlung auschieben | #Payment-Defer_Payment |
| Zahlungen allgemein | #Payment-Misc |
| Zahlungserinnerungen | #Billing-Payment_Reminders |
| Zahlungsfälligkeitsdatum | #Payment-Payment_Due_Date |
| Zahlungsfälligkeitsdatum ändern | #Payment-Payment_Due_Date_Change |
| Zahlungsmodalitäten | #Payment-Payment_Arrangement |
| Zahlungsnachforschung | #Payment-Research_Payment |
| Zahlungsorte | #Payment-Payment_Locations |
| Zahlungsüberprüfung | #Payment-Verify_Payment |
| Zahlungsübersicht | #Payment-Payment_History |
| Öffnungszeiten`*` | #Information-Store_Hours |
| Über uns | #Information-About_Us |

[![Zurück nach oben](images/up-arrow.png) <!-- {display:block;"} -->](intent_codenames_general.html#top)
