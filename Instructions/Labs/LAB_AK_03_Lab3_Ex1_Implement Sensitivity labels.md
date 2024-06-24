# Lernpfad 3 – Lab 3 – Übung 1 – Implementieren von Vertraulichkeitsbezeichnungen mit Microsoft Entra ID Protection

In Ihrer Rolle als Holly Dickson, der neuen Microsoft 365-Administratorin von Adatum, haben Sie Microsoft 365 in einer virtualisierten Laborumgebung bereitgestellt. Während Sie mit Ihrem Microsoft 365-Pilotprojekt fortfahren, sind Ihre nächsten Schritte die Implementierung von Vertraulichkeitsbezeichnungen mit Microsoft Entra ID Protection bei Adatum. In diesem Lab erstellen und veröffentlichen Sie eine Bezeichnung, und Sie testen eine veröffentlichte Bezeichnung. Dabei testen Sie jedoch nicht die Bezeichnung, die Sie in diesem Lab erstellen. Stattdessen testen Sie eine andere Bezeichnung.

**Wichtig:** Wenn Sie eine neue Vertraulichkeitsbezeichnung und Bezeichnungsrichtlinie veröffentlichen, kann es bis zu 24 Stunden dauern, bis sie über Microsoft 365 verteilt werden. Daher können Sie die Bezeichnung, die Sie in diesem Lab erstellen, nicht testen. Stattdessen testen Sie eine bereits vorhandene Vertraulichkeitsbezeichnung mit dem Namen **Projekt - Falcon**. Diese bereits vorhandene Bezeichnung ist fast identisch mit der Bezeichnung, das Sie erstellen werden. Sie können im Grunde genommen dieselben Ergebnisse sehen, als wenn Sie die von Ihnen erstellte Bezeichnung hätten testen können. 


### Aufgabe 1 – Installieren des Microsoft Entra ID Protection Unified Labeling-Clients

Um Vertraulichkeitsbezeichnungen als Teil Ihres Pilotprojekts bei Adatum zu implementieren, müssen Sie zuerst den Microsoft Entra ID Protection-Client aus dem Microsoft Download Center installieren.

**Hinweis:** Da die Umbenennung von Azure AD zu Microsoft Entra-ID noch nicht abgeschlossen ist, wurde der Azure Information Protection-Client in diesem Dokument noch nicht umbenannt. Zu einem bestimmten Zeitpunkt wird er dann in den Microsoft Entra ID Protection-Client umbenannt.

1. Am Ende des vorherigen Labs waren Sie auf LON-CL2. Wechseln Sie zu **LON-CL1**.  <br/>

    Sie sollten weiterhin bei LON-CL1 als lokales **Adatum\Administratorkonto** angemeldet sein, und in Ihrem Edge-Browser sollten Sie weiterhin bei Microsoft 365 als **Holly Dickson** angemeldet sein. 

2. Öffnen Sie in **Microsoft Edge** eine neue Registerkarte, und geben Sie die folgende URL in die Adressleiste ein (oder nutzen Sie die Funktion Kopieren und Einfügen): **https://www.microsoft.com/en-us/download/confirmation.aspx?id=53018** <br/>

    Dadurch wird der Download für den Azure Information Protection Unified Label-Client gestartet.

3. Im Fenster **Downloads**, das oben rechts auf der Seite angezeigt wird, wird der Download der Datei **AzInfoProtection_UI.exe** angezeigt. Nachdem die Datei heruntergeladen wurde, wählen Sie den Link **Datei öffnen **aus, der unter dem Dateinamen angezeigt wird.  <br/>

    **Hinweis:** Tests haben gezeigt, dass es manchmal bis zu 10 bis 15 Sekunden dauern kann, bis der **Microsoft Azure Information Protection-Assistent** geöffnet wird. Wählen Sie die Option **Datei öffnen** nicht ein zweites Mal, bis Sie sicher sind, dass der Assistent nicht gestartet wurde.

4. Der **Microsoft Azure Information Protection-Assistent** wird geöffnet. Wenn der Assistent nicht auf dem Desktop angezeigt wird, wählen Sie das Symbol für den Assistenten auf der Taskleiste aus, um den Assistenten anzuzeigen.

5. Deaktivieren Sie im daraufhin angezeigten Fenster **Azure Information Protection-Client installieren** die **Hilfe zur Verbesserung von Azure Information Protection durch Senden von Nutzungsstatistiken an Microsoft** und aktivieren Sie dann die Schaltfläche **Ich stimme zu**.

6. Sobald die Installation abgeschlossen ist, wählen Sie **Schließen** aus.

7. Schließen Sie in Ihrem Edge-Browser die Registerkarte **Herunterladen** in dieser Aufgabe, um den Azure Information Protection-Client herunterzuladen.

Sie haben den Azure Information Protection Unified Label-Client erfolgreich auf dem virtuellen Computer LON-CL1 installiert.


### Aufgabe 2 – Erstellen Sie eine Vertraulichkeitsbezeichnung

In dieser Übung erstellen Sie eine Vertraulichkeitsbezeichnung und fügen sie der Standardrichtlinie hinzu, damit sie für alle Benutzer des Adatum-Mandanten gültig ist.

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson**angemeldet sein.

2. In Ihrem Edge-Browser sollte weiterhin eine Registerkarte für das **Microsoft 365 Admin Center**geöffnet sein. Wenn nicht, öffnen Sie eine neue Registerkarte, und geben Sie die folgende URL ein: **https://admin.microsoft.com**.

3. Wählen Sie im **Microsoft 365 Admin Center **bei Bedarf **... Alle** im Navigationsbereich anzeigen. Wählen Sie **Compliance** unter der Gruppe **Admin Center** aus.

4. Wählen Sie im **Microsoft Purview **Compliance-Portal im Navigationsbereich **Informationsschutz** und dann **Bezeichnungen** aus. 

5. Auf der Seite **Bezeichnungen** wird eine Warnmeldung in einem hellgelb schattierten Feld in der Mitte der Seite angezeigt, die Folgendes angibt: **Ihre Organisation hat die Option zum Verarbeiten von Inhalten in Office-Onlinedateien, für die verschlüsselte Vertraulichkeitsbezeichnungen verwendet wurden und die in OneDrive oder SharePoint gespeichert sind, nicht aktiviert. Sie können sie hier aktivieren, beachten Sie jedoch, dass für Multi-Geo-Umgebungen zusätzliche Konfiguration erforderlich ist.** <br/>

    Wählen Sie die Schaltfläche** Jetzt aktivieren** aus, die auf der rechten Seite dieser Nachricht angezeigt wird. Dadurch kann Adatum die Vertraulichkeitsbezeichnungen innerhalb der Microsoft 365-Umgebung anwenden. <br/>

    Beachten Sie, wie sich die Nachricht jetzt geändert hat, um Folgendes anzugeben: **Sie können jetzt Vertraulichkeitsbezeichnungen mit Datenschutz- und Zugriffssteuerungseinstellungen für Teams, SharePoint-Websites und Microsoft 365-Gruppen erstellen.** 

6. Wählen Sie auf der Seite **Bezeichnungen** die Option **+Bezeichnung erstellen** aus, die in der Menüleiste in der Mitte des Bildschirms unterhalb der vorherigen Nachricht angezeigt wird. Dadurch wird der **Assistent für neue Vertraulichkeitsbezeichnungen** initiiert.

7. Geben Sie im **Assistenten für neue Vertraulichkeitsbezeichnungen** auf der Seite **Grundlegende Details für diese Bezeichnung bereitstellen** die folgenden Informationen ein:

    - Name: **PII**
    
    - Anzeigename: **PII**

    - Beschreibung für Benutzer: **Dokumente, Dateien und E-Mails mit PII**

    - Beschreibung für Administratoren: **Dokumente, Dateien und E-Mails mit PII**

    - Bezeichnungsfarbe: Wählen Sie eine der Farben aus, die Sie Ihren Vertraulichkeitsbezeichnungen zuweisen möchten

8. Wählen Sie **Weiter** aus.

9. Überprüfen Sie auf der Seite **Bereich für diese Bezeichnung definieren**, ob das Kontrollkästchen **Elemente** aktiviert ist (aktivieren Sie es bei Bedarf), und wählen Sie dann **Weiter** aus.

10. Aktivieren Sie auf der Seite **Schutzeinstellungen für bezeichnete Elemente auswählen** beide Kontrollkästchen für **Verschlüsselung anwenden oder entfernen** und **Inhaltskennzeichnung anwenden**, und wählen Sie dann **Weiter** aus.

11. Auf der Seite **Verschlüsselung** definieren Sie, wer auf Elemente zugreifen kann, auf die diese Bezeichnung angewendet wurde. Wählen Sie **Verschlüsselung entfernen, wenn die Option "Datei" oder "E-Mail" oder "Kalenderereignis verschlüsselt ist** aus, und wählen Sie dann **Weiter**.

12. Schalten Sie auf der Seite **Inhaltsmarkierung** den **Umschalter Inhaltsmarkierung** auf **Ein**. Dadurch werden drei Optionen angezeigt, mit denen Sie anpassen können, wie Sie Dateien und E-Mails markieren möchten. <br/>

    Aktivieren Sie alle drei Kontrollkästchen. Wählen Sie unter jeder Einstellung **Text anpassen** aus. Dadurch wird ein Bereich geöffnet, um diese bestimmte Einstellung anzupassen. Geben Sie die folgenden Informationen im Bereich **Anpassen** für jede Option ein (wählen Sie **Speichern** aus, nachdem Sie die Einstellungen für jede Option eingegeben haben): <br/>

    - **Ein Wasserzeichen hinzufügen** 
        - Wasserzeichentext: **Vertraulich - Nicht teilen** (Hinweis: Nach Eingabe kopieren Sie diesen Wert (STRG+C), damit Sie ihn in die anderen beiden Texteinstellungen einfügen können (STRG+V)).
        - Schriftgröße: **25**
        - Schriftfarbe: **Blau:**
        - Textlayout: **Diagonal**
            
    - **Hinzufügen einer Kopfzeile** 
        - Kopfzeilentext: **Vertraulich – Nicht teilen**
        - Schriftgröße: **25**
        - Schriftfarbe: **Rot:**
        - Text ausrichten: **Mittig**
            
    - **Hinzufügen einer Fußzeile**
        - Fußzeilentext: **Vertraulich – Nicht teilen**
        - Schriftgröße: **25**
        - Schriftfarbe: **Rot:**
        - Text ausrichten: **Mittig**

13. Wählen Sie auf der Seite **Inhaltsmarkierung** die Option **Weiter** aus. 

14. Schalten Sie auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** den Umschalter **Automatische Bezeichnung für Dateien und E-Mails** auf **Ein**. Dies ermöglicht eine Reihe von Optionen, die Sie in den nächsten Schritten aktualisieren werden.

15. Wählen Sie unter **Inhalt erkennen, der diesen Bedingungen entspricht**, **+Bedingung hinzufügen** und dann **Inhalt enthält** aus.

16. Wählen Sie im Fenster **Inhalt enthält** den Dropdownpfeil **Hinzufügen** und dann **Typen vertraulicher Informationen** aus.

17. Zeigen Sie im Fenster **Typen vertraulicher Informationen** mit der Maus links neben die Spaltenüberschrift **Name**. Aktivieren Sie das angezeigte Kontrollkästchen, das automatisch alle Typen vertraulicher Informationen auswählt. Wählen Sie **Hinzufügen** aus, wodurch alle diese vertraulichen Informationstypen zu Ihrer Bezeichnung hinzugefügt werden.

18. Auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** werden alle von Ihnen ausgewählten Typen vertraulicher Informationen angezeigt. Scrollen Sie nach unten im Fenster, und aktualisieren Sie die folgenden Einstellungen:

    - Wenn Inhalte diesen Bedingungen entsprechen: Wählen Sie **Bezeichnung automatisch anwenden** aus.

    - Diese Meldung wird Benutzern angezeigt, wenn die Bezeichnung angewendet wird: **Vertraulicher Inhalt wurde erkannt und wird verschlüsselt**.
        
19. Wählen Sie **Weiter** aus.

20. Lassen Sie auf der Seite **Schutzeinstellungen für Gruppen und Websites definieren** beide Kontrollkästchen leer, und wählen Sie **Weiter** aus.

21. Aktivieren Sie auf der Seite **Automatische Bezeichnung für schematisierte Datenressourcen (Vorschau)** nicht die automatische Bezeichnung für schematisierte Datenressourcen (Vorschau). Wählen Sie **Weiter** aus. 

22. Überprüfen Sie auf der Seite **Einstellungen und Fertig stellen** die von Ihnen eingegebenen Informationen. Wenn Einstellungen korrigiert werden müssen, wählen Sie die entsprechende Option **Bearbeiten** aus, und nehmen Sie alle erforderlichen Änderungen vor. Wenn alle Informationen richtig angezeigt werden, wählen Sie **Bezeichnung erstellen** aus.

23. Es sollte ein Dialogfeld mit einem **Clientfehler** angezeigt werden, das besagt, dass das generierte Regelblob für die Bezeichnung, die Sie erstellen möchten, zu lang ist. Die maximale Größe der Auswahl vertraulicher Informationstypen, die Sie gleichzeitig pro Regel treffen können, beträgt **49152**. Indem Sie alle Typen vertraulicher Informationen im Fenster **Typen vertraulicher Informationen** ausgewählt haben, haben Sie diesen Grenzwert überschritten. <br/>

    **HINWEIS: Wir haben Sie absichtlich dazu angeleitet, alle Typen vertraulicher Informationen auszuwählen, damit Sie diesen Fehler erhalten würden.** Wir wollten, dass dieser Fehler auftritt, sodass Sie, wenn dies in Ihren Produktionsumgebungen geschieht, wissen, warum Sie den Fehler erhalten haben und wie Sie ihn beheben können.  <br/>

    Um dieses Problem zu beheben, wählen Sie im Dialogfeld **Clientfehler** **OK** aus, und scrollen Sie dann auf der Seite **Einstellungen und Fertig stellen** nach unten zum Abschnitt **Automatische Bezeichnung für Dateien und E-Mails**, und wählen Sie **Bearbeiten** aus.
    
24. Damit sollten Sie zur Seite **Schutzeinstellungen für bezeichnete Elemente auswählen** im Assistenten zurückkehren. Wählen Sie auf dieser Seite **Weiter** aus, wählen Sie **Weiter** auf der Seite **Verschlüsselung** und dann " **Weiter** auf der Seite **Inhaltskennzeichnung** aus. Dadurch gelangen Sie zur Seite **Automatische Bezeichnung für Dateien und E-Mails**. 

25. Wählen Sie auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** rechts neben der Bedingung**Inhalt** das **Papierkorbsymbol** aus. Dadurch wird die vorhandene **Inhaltsbedingung** für die von Ihnen erstellte **PII-Bezeichnung** entfernt. <br/>

    In den verbleibenden Schritten fügen Sie eine neue Bedingung hinzu, die nur zwei Vertraulichkeitsinformationstypen und nicht alle Vertraulichkeitsinformationstypen enthält, wie Sie es ursprünglich getan haben.

26. Wählen Sie auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** unter **Inhalt erkennen, der diesen Bedingungen entspricht** **+Bedingung hinzufügen** und dann **Inhalt enthält** aus.

27. Wählen Sie im Fenster **Inhalt enthält** den Dropdownpfeil **Hinzufügen** und dann **Typen vertraulicher Informationen** aus.

28. Wählen Sie im Fenster **Typen vertraulicher Informationen** in der Liste der Typen vertraulicher Informationen nur die Kontrollkästchen **ABA-Routingnummer** und **USA Sozialversicherungsnummer (SSN)** aus, und wählen Sie dann **Hinzufügen** aus. Zurück auf der Seite **Automatische Bezeichnung für Dateien und E-Mails** werden beide typen vertraulicher Informationen angezeigt. Wählen Sie **Weiter** aus.

29. Lassen Sie auf der Seite **Schutzeinstellungen für Gruppen und Websites definieren** die beiden Kontrollkästchen leer, und wählen Sie **Weiter** aus.

30. Aktivieren Sie auf der Seite **Automatische Bezeichnung für schematisierte Datenressourcen (Vorschau)** die automatische Bezeichnung für Datenbankspalten nicht. Wählen Sie **Weiter** aus.

31. Wählen Sie auf der Seite **Einstellungen überprüfen und fertig stellen** die Option **Bezeichnung erstellen** aus.

32. Wählen Sie auf der Seite **Vertraulichkeitsbezeichnung** die Option **Richtlinie noch nicht erstellen** und dann **Fertig** aus. Dadurch gelangen Sie zur **Bezeichnungsseite**.

33. Jetzt ist es an der Zeit, die **PII-Bezeichnung** zu veröffentlichen. Wählen Sie auf der Seite **Bezeichnungen** die Option **Aktualisieren** auf der Menüleiste aus, wenn die **PII-Bezeichnung** nicht in der Liste der Bezeichnungen angezeigt wird. Sobald die **PII-Bezeichnung** angezeigt wird, aktivieren Sie das Kontrollkästchen, das links davon angezeigt wird. 

34. Wählen Sie die Option **Bezeichnung veröffentlichen** aus, die in der Menüleiste oberhalb der Liste der Bezeichnungen angezeigt wird. Dadurch wird ein Assistent für **Richtlinien erstellen** initiiert.

35. Im Assistenten für **Richtlinien erstellen** auf der Seite **Vertraulichkeitsbezeichnungen zum Veröffentlichen auswählen** ist die **PII-Bezeichnung** bereits aufgeführt, also wählen Sie **Weiter** aus. 

36. Wählen Sie auf der Seite **Administratoreinheiten zuweisen** die Option **Weiter** aus, da Sie diese PII-Richtlinie nicht nur einer ausgewählten Gruppe von Administratoreinheiten, sondern dem vollständigen Verzeichnis von Adatum zuweisen.

37. Auf der Seite **Für Benutzer und Gruppen veröffentlichen** können Sie auswählen, ob Ihre Richtlinie allen Benutzern und Gruppen zur Verfügung gestellt werden soll, oder Sie können die Richtlinie auf ausgewählte Benutzer und Gruppen beschränken. Für dieses Lab möchten Sie die Richtlinie allen Benutzern zur Verfügung stellen. Die Option **Benutzer und Gruppen** ist standardmäßig bereits ausgewählt (wenn nicht, wählen Sie sie jetzt aus). Dadurch wird Ihre Richtlinie allen Benutzern und Gruppen zur Verfügung gestellt. Wählen Sie **Weiter** aus.  <br/>

    **Hinweis:** Wenn Sie dies in Ihrer realen Bereitstellung tun, wenn Sie Ihre Richtlinie auf eine ausgewählte Anzahl von Benutzern oder Gruppen beschränken möchten, würden Sie **Bearbeiten** auswählen und diese Auswahl treffen. 

38. Wählen Sie auf der Seite **Richtlinieneinstellungen** das Kontrollkästchen **Benutzer müssen eine Begründung für die Entfernung einer Kennzeichnung oder die Herabstufung ihrer Klassifizierung angeben** aus, und wählen Sie dann **Weiter** aus. 

39. Wählen Sie auf der Seite **Standardbezeichnung auf Dokumente anwenden** im daraufhin angezeigten Dropdownmenü **PII** aus, und wählen Sie dann **Weiter**.

40. Wählen Sie auf der Seite **Standardbezeichnung auf E-Mails anwenden** im daraufhin angezeigten Dropdownmenü **PII** aus, und wählen Sie dann **Weiter**.

41. Wählen Sie auf der Seite **Standardbezeichnung auf Besprechungen und Kalenderereignisse anwenden** im angezeigten Dropdownmenü **PII** aus, und wählen Sie dann **Weiter**.

42. Wählen Sie auf der Seite **Standardbezeichnung auf Fabric- und Power BI-Inhalt anwenden** im angezeigten Dropdownmenü **PII** aus, und wählen Sie dann **Weiter**.

43. Geben Sie auf der Seite **Richtlinie benennen** die **PII-Richtlinie **in das Feld** Name **ein, und geben Sie dann die folgende Beschreibung für diese Richtlinie für Vertraulichkeitsbezeichnungen ein (oder nutzen Sie die Funktion Kopieren und Einfügen): **Zweck dieser Richtlinie ist es, vertrauliche Informationen wie ABA-Bank-Routingnummern und US-Sozialversicherungsnummern in E-Mails und Dokumenten zu erkennen und diese Informationen zu verschlüsseln, wenn sie entdeckt werden. Der Benutzer muss eine Erläuterung zum Entfernen der Klassifizierungsbezeichnung angeben.** Wählen Sie **Weiter** aus.

44. Überprüfen Sie auf der Seite **Überprüfen und Fertig stellen** die eingegebenen Informationen. Wenn etwas korrigiert werden muss, wählen Sie die entsprechende Option zum **Bearbeiten** aus, und nehmen Sie die erforderlichen Korrekturen vor. Wenn alle Informationen richtig sind, wählen Sie **Senden** aus.

45. Wählen Sie auf der Seite **Neue Richtlinie erstellt** die Option **Fertig** aus.


### Aufgabe 3 – Zuweisen einer bereits vorhandenen Vertraulichkeitsbezeichnung zu einem Dokument

Wie in den Anweisungen zu Beginn dieses Labs beschrieben, ist es nicht möglich, die Vertraulichkeitsbezeichnung und die Bezeichnungsrichtlinie, die Sie in der vorherigen Aufgabe erstellt haben, sofort zu testen. Dies liegt daran, dass es bis zu 24 Stunden dauert, bis eine neue Bezeichnungsrichtlinie über Microsoft 365 verteilt wird und ihre Bezeichnung in Anwendungen wie Microsoft Word und Outlook sichtbar wird.

Stattdessen testen Sie eine der bereits vorhandenen Vertraulichkeitsbezeichnungen von Microsoft 365. Für dieses Lab verwenden Sie die Vertraulichkeitsbezeichnung **Projekt - Falcon**, die eine Bezeichnung mit der Einstufung "Streng vertraulich" ist. Diese Bezeichnung ähnelt der Bezeichnung, die Sie in der vorherigen Aufgabe erstellt haben. Die einzige Ausnahme besteht darin, dass sie keine Kopf- oder Fußzeile enthält. Durch Verwendung dieser bereits vorhandenen Bezeichnung erhalten Sie eine gute Vorstellung davon, wie die von Ihnen erstellte Bezeichnung bei Adatum funktioniert.

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson**angemeldet sein.

2. Sie überprüfen zuerst die **Project – Falcon-** Vertraulichkeitsbezeichnung, die Sie in dieser Aufgabe auf ein Dokument anwenden werden.  In Ihrem Edge-Browser sollte weiterhin eine Registerkarte für das **Microsoft Purview**-Portal aus der vorherigen Aufgabe geöffnet sein. Wählen Sie im **Microsoft Purview**-Portal unter der Gruppe **Informationsschutz** im Navigationsbereich **Bezeichnungen** aus. 

3. Wählen Sie auf der Seite **Bezeichnungen** in der Liste der Bezeichnungen den rechten Pfeil (**>**) neben **Streng vertraulich** aus, um die untergeordneten Bezeichnungen unter dieser Bezeichnung anzuzeigen. Dadurch wird die bereits vorhandene **Project – Falcon**-Bezeichnung angezeigt.

4. Wählen Sie die **Projekt – Falcon**-Bezeichnung (nicht das Kontrollkästchen; sondern den Bezeichnungsnamen) aus. Dadurch wird ein Detailbereich für die **Projekt – Falcon**-Bezeichnung geöffnet. Überprüfen Sie die für diese Bezeichnung definierten Informationen, und schließen Sie dann den Bereich.  

5. Sie werden nun einem Dokument die **Project – Falcon**-Vertraulichkeitsbezeichnung zuweisen. Wählen Sie die Registerkarte **Home | Microsoft 365** in Ihrem Browser, um zur Microsoft 365-Startseite zurückzukehren. Wählen Sie auf der linken Seite des Bildschirms das Symbol **Apps** aus. Klicken Sie auf der daraufhin angezeigten Seite **Apps** mit der rechten Maustaste auf die Kachel **Word**, und wählen Sie **In neuer Registerkarte öffnen** aus. 

6. In der Registerkarte **Word | Microsoft 365**, wählen Sie unter dem Abschnitt **Neu erstellen **oben auf der Seite **Leeres Dokument** aus.

7. Wenn ein Fenster **Ihre Datenschutzoptionen** angezeigt wird, wählen Sie **Schließen**.

8. Wenn im Word-Menüband Symbole für jedes Feature angezeigt werden, die Symbole jedoch nicht nach Gruppe getrennt werden, wählen Sie den Abwärtspfeil ganz rechts im Menüband aus, und wählen Sie dann in **Menübandlayout** **Klassisches Menüband** aus. Dadurch wird das Menüband auf die herkömmliche Menübandformatvorlage umgestellt, die nach Featuregruppe (z. B. Rückgängig, Zwischenablage, Schriftart, Absatz, Formatvorlagen usw.) aufgeteilt wird.

9. Geben Sie im **Word-Dokument** den folgenden Text ein: **Testen einer Vertraulichkeitsbezeichnung auf einem Dokument mit personenbezogenen Informationen (PII); in diesem Fall eine US-Sozialversicherungsnummer: 111-11-1111.**

10. Da Sie Vertraulichkeitsbezeichnungen zu Beginn dieser Übung aktiviert haben, sollte **Word** oben auf der Seite eine **Vertraulichkeitsgruppe** im Menüband anzeigen. Wählen Sie den Abwärtspfeil in der Gruppe **Vertraulichkeit** aus. Im daraufhin angezeigten Dropdownmenü sollte die Liste der Vertraulichkeitsbezeichnungstypen angezeigt werden. Wählen Sie **Streng vertraulich** aus, und wählen Sie dann im daraufhin angezeigten Untermenü **Projekt - Falcon** aus. <br/>

    **Hinweis:** Nach 24 Stunden wird die Bezeichnung, die Sie im vorherigen Vorgang erstellt haben, im Untermenü „Streng vertraulich“ neben der „Projekt – Falcon“-Bezeichnung angezeigt. Ersteinmal verwenden Sie aber die Bezeichnung **Projekt - Falcon** an ihrer Stelle.

11. Beachten Sie im Dokument, wie die Bezeichnung ein **VERTRAULICH - Projekt Falcon**-Wasserzeichen am oberen Rand des Dokuments angebracht hat. Die Projekt - Falcon-Bezeichnung wurde genau wie die von Ihnen erstellte Bezeichnung konfiguriert, bei der das Wasserzeichen diagonal in der Mitte der Seite angezeigt werden soll. Warum wird sie also oben auf der Seite angezeigt? Die Antwort lautet, dass Sie **Word für das Web **verwenden, das standardmäßig wie hier angezeigt wird. Um zu sehen, wie es für jemanden angezeigt wird, der das Dokument liest, müssen Sie das Dokument in der **Leseansicht** anzeigen, was Sie jetzt tun werden. <br/>

    Wählen Sie die Registerkarte **Ansicht** und dann im Word-Menüband die Option **Leseansicht** aus. Beachten Sie, wie das Wasserzeichen diagonal verlaufend in der Mitte des Dokuments angezeigt wird. So wird das Wasserzeichen für jemanden angezeigt, der das Dokument liest. Beachten Sie, dass bei Verwendung der Word-Desktop-App das Wasserzeichen angezeigt wird, das durch die Bezeichnung festgelegt wurde, was in diesem Fall genauso wie hier in der Leseansicht angezeigt wird. <br/>

    Um die Leseansicht zu beenden, wählen Sie **Dokument bearbeiten** in der Menüleiste oben auf der Seite aus. Wählen Sie im angezeigten Dropdownmenü **Bearbeiten** aus.

12. Bei diesem ersten Validierungstest entfernen Sie diese Vertraulichkeitsbezeichnung, die auf dieses Dokument angewendet wird. Eine der Bezeichnungsrichtlinienoptionen erfordert, dass Benutzer eine Begründung zum Entfernen einer Bezeichnung oder zum Auswählen einer niedrigeren Klassifizierungsbezeichnung angeben. Sie überprüfen nun, ob diese Einstellung ordnungsgemäß funktioniert. <br/>

    Wählen Sie in der Gruppe **Vertraulichkeit** im Word-Menüband den Abwärtspfeil aus. Beachten Sie im daraufhin angezeigten Dropdownmenü, dass neben **Streng vertraulich** ein Häkchen angezeigt wird. Halten Sie die Maus über **Streng vertraulich**, um das Untermenü anzuzeigen. Beachten Sie, wie neben **Projekt - Falcon **ein Häkchen angezeigt wird. Die Häkchen identifizieren die aktuelle Bezeichnung, die auf das Dokument angewendet wird.  <br/>
 
    Um die Bezeichnung aus diesem Dokument zu entfernen, wählen Sie die **Projekt - Falcon**-Bezeichnung aus, die in diesem Dropdownmenü angezeigt wird.
    
13. Wählen Sie im daraufhin angezeigten Fenster **Begründung erforderlich** die Option **Sonstige (Erläutern)** aus. Geben Sie im Feld **Erklärung, warum Sie diese Bezeichnung ändern** **Testen, was passiert, wenn eine Bezeichnung von einem Dokument entfernt wird** ein und wählen Sie dann **Ändern**.

14. Beachten Sie, wie das Wasserzeichen im Dokument verschwunden ist. Wählen Sie in der Gruppe **Vertraulichkeit** im Word-Menüband den Abwärtspfeil aus. Beachten Sie im daraufhin angezeigten Dropdownmenü, dass während **Streng vertraulich** > **Projekt - Falcon** angezeigt wird, keine Häkchen daneben angezeigt werden. Dies gibt an, dass die Vertraulichkeitsbezeichnung nicht mehr auf dieses Dokument angewendet wird.  

15. Wenn Sie die Vertraulichkeitsbezeichnung erneut auf das Dokument anwenden möchten, wählen Sie im Dropdownmenü **Streng vertraulich** > **Projekt – Falcon** aus. Beachten Sie, wie das Wasserzeichen wieder im Dokument angezeigt wird.

16. Sie speichern nun das Dokument, damit Sie es in der nächsten Aufgabe freigeben können. Ein Dokumentnamenfeld, das einen Dropdownpfeil enthält, wird in der oberen linken Ecke der Seite rechts neben dem Word-Symbol angezeigt (Word kann **Dokument** oder **Dokument1** als temporären Dateinamen anzeigen). Wählen Sie den Dropdownpfeil. Bestätigen Sie im angezeigten Dropdownmenü, dass der **Dateispeicherort ****Holly Dickson > Dokumente **lautet. <br/>

    Benennen Sie die Datei im Feld **Dateiname** in **ProtectedDocument1** um, und klicken Sie dann außerhalb dieses Dateinamenmenüs (im Dokument klicken). Beachten Sie, dass der neue Name, der der Datei zugewiesen ist, in der Titelleiste angezeigt wird. 

17. Lassen Sie die Registerkarte **ProtectedDocument1** geöffnet, in der das Dokument angezeigt wird. Sie kehren zu diesem Dokument in der nächsten Aufgabe zurück, um das Dokument mit Joni Sherman zu teilen.

Sie haben gerade erfolgreich ein Word-Dokument erstellt, das die streng vertrauliche Bezeichnung mit dem Titel **Projekt –Falcon** enthält. 


### Aufgabe 4 – Schützen eines Dokuments mithilfe von Microsoft Entra ID Protection

Im vorherigen Vorgang haben Sie ein Word-Dokument erstellt und mit der Vertraulichkeitsbezeichnung **Projekt - Falcon** geschützt. Diese Beschriftung hat ein Wasserzeichen in das Dokument eingefügt. In dieser Aufgabe geben Sie das Dokument frei, das Sie mit Joni Sherman erstellt haben, und Sie werden Joni auf die Berechtigung "Schreibgeschützt" beschränken. Auf diese Weise können Sie sehen, wie Microsoft Entra ID Protection das Dokument basierend auf den von Ihnen konfigurierten Parametern schützt.

Um zu überprüfen, ob der Schutz, den Sie dem Dokument zugewiesen haben, funktioniert, senden Sie das Dokument zuerst an zwei Personen – an Joni Sherman und ihre eigene persönliche E-Mail-Adresse. Anschließend überprüfen Sie, ob Joni das Dokument nur anzeigen und nicht bearbeiten kann, und Sie überprüfen, ob Sie nicht auf das Dokument zugreifen können, da es nicht für Sie freigegeben wurde. Schließlich ändern Sie die Berechtigung für das Dokument, damit Joni es bearbeiten kann, und Sie senden dieses aktualisierte Dokument zu Testzwecken per E-Mail an sie. Der Zweck der beiden E-Mails an Joni, eine mit einem Dokumentlink, der schreibgeschützten Zugriff und eine andere mit einem Dokumentlink bietet, der die Möglichkeit zum Bearbeiten des Dokuments bietet, besteht darin, zu sehen, wie Microsoft Entra ID Protection verschiedene Ebenen des Dokumentschutzes bieten kann. 

1. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 angemeldet sein, da **Holly Dickson** aus der vorherigen Aufgabe mit geöffneter **Word**-Registerkarte angemeldet ist.

2. Wählen Sie in Ihrem Edge-Browser die **Apps | Microsoft 365**-Registerkarte. 

3. Klicken Sie auf der Seite **Apps** mit der rechten Maustaste auf die Kachel **Outlook**, und wählen Sie **In neuer Registerkarte öffnen** aus. Dadurch wird das Postfach von Holly in Outlook im Web auf einer neuen Browserregisterkarte geöffnet. 

4. Wählen Sie in **Outlook im Web** im oberen linken Teil des Bildschirms **Neue E-Mail** aus.

5. Geben Sie die folgenden Informationen in das E-Mail-Formular ein:

    - In folgende Zeichenfolge: Geben Sie **Joni** ein, und wählen Sie dann **Joni Sherman** aus der Benutzerliste aus. 

    - CC: Geben Sie Ihre eigene persönliche E-Mail-Adresse ein (geben Sie NICHT die E-Mail-Adresse von Holly ein; geben Sie stattdessen Ihre eigene persönliche E-Mail-Adresse ein), und wählen Sie dann die angezeigte Nachricht **Diese Adresse verwenden<your email address>** aus

    - Hinzufügen eines Betreffs: **Test geschützter Dokumente – Berechtigung „Schreibgeschützt“**

    - Textkörper der Nachricht: Geben Sie **Öffnen Sie das an diese E-Mail angefügte geschützte Dokument, und versuchen Sie, es zu ändern.**

6. Im Textkörper der Nachricht fügen Sie unter dem Text, den Sie im vorherigen Schritt hinzugefügt haben, einen Link zu dem Dokument an, das Sie in der vorherigen Aufgabe erstellt haben. Dazu müssen Sie das Dokument jedoch zuerst mit Joni Sherman teilen, und im Zuge dessen nur die Berechtigungen **Schreibgeschützt** anwenden. Um dies zu tun, müssen Sie diese E-Mail verlassen und zu Ihrem Dokument zurückkehren und es mit Joni teilen. Nachdem Sie den Link kopiert haben, der während des Freigabevorgangs erstellt wurde, kehren Sie zu dieser E-Mail zurück und fügen ihn in den Link ein. <br/>

    Wählen Sie im Edge-Browser die Registerkarte **ProtectedDocument1** aus, die weiterhin das Dokument anzeigt, das Sie in der vorherigen Aufgabe erstellt haben. Wählen Sie oben rechts auf der Seite unter dem Namen und den Initialen von Holly Dickson die Schaltfläche **Teilen** aus. Wählen Sie im angezeigten Dropdownmenü **Teilen** aus.

7. Wählen Sie im daraufhin angezeigten Fenster **"ProtectedDocument1" teilen** das Zahnradsymbol (**Linkeinstellungen**) aus, das neben der Schaltfläche **Link kopieren** angezeigt wird. 

8. Wählen Sie im daraufhin angezeigten Fenster **Linkeinstellungen** die Option **Personen, die Sie auswählen** aus.
    
9. Unter **Weitere Einstellungen** ist die aktuelle Option **Kann bearbeiten**. Sie beabsichtigen, dieses Dokument mit Joni Sherman zu teilen, aber Sie möchten, dass Joni das Dokument nur anzeigen kann. Um diese Berechtigungsänderung vorzunehmen, wählen Sie **Kann bearbeiten** aus. Überprüfen Sie im daraufhin angezeigten Menü die verfügbaren Optionen. Sie können sehen, dass **Kann bearbeiten** ein Häkchen daneben aufweist, was angibt, dass es sich um die aktuelle Einstellung handelt. Um Joni auf schreibgeschützte Berechtigung zu beschränken, wählen Sie **Kann anzeigen** und dann **Übernehmen** aus.

10. Dadurch werden Sie zum Fenster ** "ProtectedDocument1" teilen** zurückgeführt. Geben Sie **Joni** in das Feld **Name, Gruppe oder E-Mail hinzufügen** ein. Eine Liste der Benutzer, deren Name mit **Joni** beginnt, sollte angezeigt werden. Wählen Sie **Joni Sherman** aus.

11. Zeigen Sie im Fenster ** "ProtectedDocument1" teilen** mit der Maus auf das Symbol "Auge", das rechts neben dem Namen von Joni angezeigt wird. Dadurch sollte **Kann anzeigen** angezeigt werden. Dabei handelt es sich um die aktuelle Einstellung, die Sie für dieses Dokument zugewiesen haben. Das Symbol "Auge" ist die Bezeichnung für "Kann anzeigen". Wählen Sie die Schaltfläche **Link kopieren** aus. 

12. Sobald die Nachricht **Link kopiert** unten im Fenster ** "ProtectedDocument1" teilen** angezeigt wird, wählen Sie das X in der oberen rechten Ecke des Fensters aus, um es zu schließen.

13. Wählen Sie in Ihrem Edge-Browser die Registerkarte **Mail - Holly Dickson -Outlook** aus, um zu Ihrer E-Mail-Nachricht zurückzukehren. Fügen Sie im Textkörper der Nachricht unter dem zuvor hinzugefügten Text (STRG+V) in den Link zum freigegebenen Dokument ein, den Sie soeben in die Zwischenablage kopiert haben. Ein Link für die Datei mit dem Namen **ProtectedDocument1.docx** sollte angezeigt werden. 

14. Wählen Sie **Send** (Senden) aus.

15. Es sollte eine Nachricht **Empfänger können nicht auf Links zugreifen** angezeigt werden. Diese Nachricht ist ein Ergebnis von Microsoft Entra ID Protection, der die Tatsache erkennt, dass Sie Ihre persönliche E-Mail-Adresse in die E-Mail aufgenommen haben, die keine Berechtigung für den Zugriff auf das Dokument hat. Wählen Sie für diesen Lab-Test **Trotzdem senden** aus.

16. Wechseln Sie zu **LON-CL2**. 

17. Auf **LON-CL2** sollten Sie in **Outlook im Web** als **Lynne Robbins** aus der vorherigen Übung des Labs angemeldet sein. Melden Sie sich als Lynne ab.

18. Schließen Sie in Ihrem Edge-Browser alle Registerkarten mit Ausnahme der Registerkarte **Abmelden**. Geben Sie auf dieser Registerkarte die folgende URL in die Adressleiste ein: **https://outlook.office365.com** 

19. Wählen Sie im Fenster **Konto auswählen** die Option **Anderes Konto verwenden** aus.

20. Geben Sie im Fenster **Anmelden** **JoniS@xxxxxZZZZZZ.onmicrosoft** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist, und wählen Sie dann **Weiter** aus.

21. Geben Sie im Fenster **Passwort eingeben** das von Ihrem Labor-Hosting-Anbieter bereitgestellte **Benutzerkennwort** ein und wählen Sie dann **Anmelden**. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus.

22. Wenn ein **Willkommensfenster** angezeigt wird, wählen Sie das X aus, um es zu schließen.

23. Im **Posteingang **von Joni in** Outlook im Web**sollte die E-Mail angezeigt werden, die Holly soeben gesendet hat, deren Betreffzeile angibt, dass das Dokument nur die Berechtigung "Schreibgeschützt" besitzt. Öffnen Sie diese E-Mail.

24. Wählen Sie in der E-Mail die angefügte Datei aus, um sie zu öffnen.

25. Wählen Sie im daraufhin angezeigten Fenster **Datenschutzoption** die Option **Schließen**. Das Dokument wird in **Word im Web **in einer neuen Browserregisterkarte mit dem Titel **ProtectedDocument1.docx** geöffnet. Beachten Sie, wie das Dokument in der Leseansicht in **Word im Web** angezeigt wird. Dies ist der Hinweis an Joni, dass sie nur die Berechtigung "Schreibgeschützt" besitzt und das Dokument nicht bearbeiten kann. Um dies zu überprüfen, versuchen Sie, das Dokument auszuwählen. Beachten Sie die angezeigte Meldung, die Folgendes angibt: **Schreibgeschützt. Das Dokument ist schreibgeschützt.** Beachten Sie das Wasserzeichen, das in der **Projekt - Falcon**-Richtlinie angegeben ist. <br/>

    Nachdem Sie das Dokument überprüft haben, schließen Sie die Registerkarte **ProtectedDocument1.docx**. 

26. Sie testen nun, was passiert, wenn Sie versuchen, das Dokument zu öffnen, das an Ihre persönliche E-Mail-Adresse gesendet wurde. Verwenden Sie Ihr Mobiltelefon oder Kursraum-PC, um auf Ihr persönliches Postfach zuzugreifen. Öffnen Sie die E-Mail, die Holly soeben an Ihre persönliche E-Mail-Adresse gesendet hat, und versuchen Sie dann, die angefügte Datei zu öffnen. 

27. Da Sie nicht über die Berechtigung zum Zugriff auf das Dokument verfügen, sollte ein Fenster **Konto auswählen** angezeigt werden. In einem realen Szenario können Sie sich optional mit einem Konto anmelden, das über die Berechtigung für den Zugriff auf die Datei verfügt, oder den Zugriff vom **Holly@xxxxxZZZZZZ.onmicrosoft.com** Konto anfordern. <br/>

    Für diesen Test haben Sie lediglich überprüft, dass Sie nicht auf die Datei zugreifen können, da sie nicht für Sie freigegeben wurde. Sie haben auch überprüft, dass Joni nur die Datei anzeigen konnte, aber nicht bearbeiten konnte. Sie ändern nun die Freigabeberechtigungen für die Datei, indem Sie Joni erlauben, sie zu bearbeiten. Sie werden dies tun, um zu sehen, wie sich diese Erfahrung von der unterscheidet, die Sie gerade abgeschlossen haben. 

28. Wechseln Sie zu **LON-CL1**. 

29. Auf LON-CL1 sollten Sie in Ihrem Edge-Browser weiterhin bei Microsoft 365 als **Holly Dickson**angemeldet sein, und Sie sollten Registerkarten sowohl für **Word **als auch für **Outlook** geöffnet haben. Wählen Sie die Registerkarte **E-Mail - Holly Dickson** aus. 

30. Erstellen Sie im Postfach von Holly eine weitere E-Mail an Joni Sherman. Schließen Sie Ihre persönliche E-Mail-Adresse NICHT in die CC-Zeile ein. Geben Sie die folgenden Informationen in das E-Mail-Formular ein:

    - In folgende Zeichenfolge: Geben Sie **Joni** ein, und wählen Sie dann **Joni Sherman** aus der Benutzerliste aus. 

    - CC: Nicht ausfüllen

    - Hinzufügen eines Betreffs: **Test geschützter Dokumente – Berechtigung „Bearbeiten“**

    - Textkörper der Nachricht: Geben Sie **Öffnen Sie das an diese E-Mail angefügte geschützte Dokument, und versuchen Sie, es zu ändern.**

31. Genau wie bei der vorherigen E-Mail müssen Sie das Dokument jetzt mit Joni teilen, aber diesmal mit Bearbeitungsberechtigung. Gehen Sie dafür wie folgt vor: <br/>

    - Wählen Sie in Ihrem Browser die Registerkarte ** ProtectedDocument1** aus, und wählen Sie dann auf der rechten Seite der Menüleiste die Schaltfläche **Teilen** aus. Wählen Sie im angezeigten Dropdownmenü **Teilen** aus. 
    - Geben Sie im Fenster ** "ProtectedDocument1" teilen** **Joni** in das Feld **Name, Gruppe oder E-Mail hinzufügen** ein, und wählen Sie dann **Joni Sherman **aus.
    - Rechts neben dem Namen von Joni befindet sich ein Bleistiftsymbol (**Kann bearbeiten**). Dies ist die Standardberechtigung beim Freigeben eines Dokuments. Wählen Sie die Schaltfläche **Link kopieren** aus, um zu sehen, was passiert.
    - Beachten Sie die angezeigte Nachricht **Link kopiert**. Die Nachricht gibt an, dass jeder das Dokument bearbeiten kann, obwohl Sie den Namen von Joni angegeben haben. Dies ist nicht das, was Sie möchten. Sie möchten Joni als einzige Person erlauben, das Dokument zu bearbeiten. Um diese Einschränkung zu aktivieren, wählen Sie das Zahnradsymbol (**Linkeinstellungen**) neben der Schaltfläche **Link kopieren** aus. 
    - Wählen Sie im daraufhin angezeigten Fenster **Linkeinstellungen** die Option **Personen, die Sie auswählen** aus. Diese Option dient dazu, die Berechtigung für ausgewählte Benutzer einzuschränken. 
    - Wenn unter**Weitere Einstellungen** **Kann bearbeiten** angezeigt wird, wählen Sie **Übernehmen** aus. Wenn jedoch **Kann anzeigen** angezeigt wird, wählen Sie **Kann anzeigen** aus, und wählen Sie dann im daraufhin angezeigten Menü **Kann bearbeiten** und dann **Übernehmen** aus. 
    - Wählen Sie im Fenster ** "ProtectedDocument1" teilen** die Schaltfläche **Link kopieren** aus.
    - Beachten Sie die angezeigte Nachricht **Link kopiert**. Dieses Mal gibt die Nachricht an, dass nur die von Ihnen angegebenen Personen das Dokument bearbeiten können. In diesem Fall ist die Bearbeitung auf Joni beschränkt, da sie die einzige Person ist, die Sie angegeben haben. 
    - Wählen Sie die Registerkarte **Mail - Holly Dickson - Outlook** in Ihrem Browser aus, und fügen Sie dann den Link in den Textkörper der E-Mail-Nachricht ein. 

32. Wählen Sie **Send** (Senden) aus.

33. Wechseln Sie zu **LON-CL2**. 

34. Auf **LON-CL2** sollten Sie weiterhin als **Joni Sherman** bei **Outlook im Web** angemeldet sein. Im **Posteingang **von Joni sollte die E-Mail angezeigt werden, die Holly gerade gesendet hat, deren Betreffzeile angibt, dass das Dokument über die Berechtigung "Bearbeiten" verfügt. Öffnen Sie diese E-Mail.

35. Wählen Sie in der E-Mail die angefügte Datei aus, um sie zu öffnen.

36. Wenn Joni nur die Berechtigung "Schreibgeschützt" hatte, wurde das Dokument im Leseansichtsbereich geöffnet. Daher konnte Joni das Dokument nicht bearbeiten. Diese Version des Dokuments stellt Joni die Berechtigung "Bearbeiten" bereit. Dieses Mal sollte das Dokument in Word im normalen Bearbeitungsmodus geöffnet werden. Stellen Sie sicher, dass Sie Text in das Dokument eingeben können. 

    **Hinweis:**  In dieser Aufgabe haben Sie gerade überprüft, dass Microsoft Entra ID Protection das Dokument basierend auf den von Ihnen konfigurierten PII-Richtlinienparametern geschützt hat. Als Joni nur die Berechtigung "Schreibgeschützt" zugewiesen wurde, wurde das Dokument in der Leseansicht geöffnet und sie konnte es nicht ändern. Als Joni die Berechtigung "Bearbeiten" zugewiesen wurde, wurde das Dokument in Word geöffnet und sie konnte es ändern. Da Holly das Dokument nicht für Sie freigegeben hat, konnten Sie es nicht öffnen, als sie das Dokument in einer E-Mail an Ihr persönliches Postfach gesendet hat. 

## Ende von Lab 3


# Herzlichen Glückwunsch! Sie haben gerade das letzte Lab in diesem Kurs abgeschlossen.
