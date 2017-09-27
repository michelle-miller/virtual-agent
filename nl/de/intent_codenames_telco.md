---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-27"

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

# Absichtsnamen (Telekommunikationsunternehmen)
{: #intent_codenames_telco}
{: #top}

[![Zurück](images/back-arrow.png)](intent_codenames.html)

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
| Anfrage zu Roaming | #Service_Management-Roaming_Inquiry |
| Anfrage zu internationalem Tarifmodell | #Service_Management-International_Rate_Plan_Inquiry |
| Anfrage zur Geräterückgabe | #Sales-Return_Device |
| Anfrage zur Netzabdeckung | #Service_Management-Coverage_Area_Inquiry |
| Anspruchsstatus auf Upgrade | #Account_Management-Upgrade_Eligibility_Status |
| Auftragsbearbeitung allgemein | #Order_Management-Misc |
| Bankdaten | #Payment-Bank_Information |
| Beendung | #Help-Ending |
| Begrüßung | #Help-Greetings |
| Berechtigte Benutzer | #Account_Management-Authorized_User |
| Bestellstatus | #Order_Management-Get_Product_Order_Status |
| Bestellung stornieren | #Order_Management-Cancel_Product_Order |
| Bestellung ändern | #Order_Management-Modify_Product_Order |
| Dienstleistungen einer Filiale | #Information-Store_Services |
| Dienstleistungen entfernen | #Service_Management-Remove_Service_Features |
| Dienstleistungen hinzufügen | #Service_Management-Add_Service_Features |
| E-Mail aktualisieren`*` | #Account_Management-Email_Change |
| Eine Zahlung tätigen`*` | #Payment-Make_A_Payment |
| Einzelgebührerklärung | #Billing-One_Time_Charges |
| Erstattung | #Payment-Refund_Payment |
| Fehlende oder falsche Zahlungen | #Payment-Missing_Misapplied_Payment |
| Fehlerbehebung | #Complaints-Troubleshooting |
| Filialtermin verschieben | #Information-Change_Store_Appointment |
| Geräteaktivierung | #Device_Management-Activation |
| Gerätetausch | #Device_Management-Swap_Device |
| Geräteverwaltung allgemein | #Device_Management-Misc |
| Handynummer ändern | #Service_Management-Change_Mobile_Phone_Number |
| Haustermin vereinbaren | #Information-Make_At_Home_Appointment |
| Haustermin verschieben | #Information-Change_At_Home_Appointment |
| Hilfe | #Help-Help |
| Keines der Obigen | #Off_Topic-None_of_the_Above |
| Kontakt | #Information-Contact_Us |
| Konto eröffnen | #Account_Management-Open_Account |
| Konto löschen | #Account_Management-Close_Cancel_Account |
| Kontoberechtigungen | #Account_Management-Privileges |
| Kontonamensänderung | #Account_Management-Name_Change |
| Kontoverwaltung allgemein | #Account_Management-Misc |
| Kreditstatus | #Billing-Credit_Status |
| Kundenkontonummer | #Account_Management-Account_Number_Inquiry |
| Kundenprofil | #Account_Management-Customer_Profile |
| Kundenreklamation | #Complaints-Misc |
| Kundentreueprogramm | #Account_Management-Customer_Loyalty_Program |
| Kundentreuestatus | #Account_Management-Loyalty_Status |
| Ladentermin vereinbaren | #Information-Make_Store_Appointment |
| Missbrauch | #Account_Management-Fraudulent_Use |
| Mit Kundenbetreuer verbinden | #Help-Connect_to_Agent |
| Netzbetreibersperre aufheben | #Service_Management-Network_Unlock |
| Netzprobleme | #Complaints-Network |
| Nächstgelegene Filiale finden`*` | #Information-Find_Nearest_Store |
| Offene Stellen | #Information-Jobs |
| Online-Kontozugriff | #Online_Account_Access-Misc |
| Online-Rechnungen | #Billing-Online_Statements |
| Papierrechnungen | #Billing-Paper_Statements |
| Prepaid-Tarif aktivieren | #Service_Management-Activate_Prepaid_Plan |
| Prepaid-Tarif aufladen | #Payment-Recharge |
| Prepaid-Tarif deaktivieren | #Service_Management-De_Activate_Prepaid_Plan |
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
| Roaming aktivieren | #Service_Management-Activate_Roaming |
| Roaming deaktivieren | #Service_Management-De_Activate_Roaming |
| Rufnummermitnahme | #Sales-Port_In |
| Serviceverwaltung allgemein | #Service_Management-Misc |
| Sicherheitsgarantie | #Help-Security_Assurance |
| Standort einer Filiale`*` | #Information-Store_Location |
| Systeminformationen | #Help-Misc |
| Tarifanfrage | #Service_Management-Price_Plan_Inquiry |
| Tarifänderung | #Service_Management-Price_Plan_Change |
| Telefonnummer aktualisieren`*` | #Account_Management-Update_Change_Contact_Phone_Number |
| Telefonnummer einer Filiale`*` | #Information-Store_Phone_Number |
| Termin vereinbaren | #Information-Make_Appointment |
| Termin verschieben | #Information-Change_Appointment |
| Verfügbare Produkte | #Information-Store_Products |
| Verkauf allgemein | #Sales-Misc |
| Versicherung hinzufügen | #Service_Management-Add_Insurance |
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
| Zeitspanne bis Upgrade | #Account_Management-Upgrade_Eligibility_Timing |
| Öffnungszeiten`*` | #Information-Store_Hours |
| Über uns | #Information-About_Us |


`*` [Integrierte Dialoge](configure.html#builtin_dialog_ovw)

[![Zurück nach oben](images/up-arrow.png)](intent_codenames_telco.html#top)
