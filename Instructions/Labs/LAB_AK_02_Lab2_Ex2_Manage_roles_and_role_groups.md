# Lernpfad 2, Lab 2, Übung 2: Verwalten von Rollen und Rollengruppen

In dieser Labübung fahren Sie in der Rolle von Holly Dickson fort, der neuen Microsoft 365-Administratorin von Adatum. Im Rahmen des Microsoft 365-Pilotprojekts von Adatum verwalten Sie die Delegierung von Administratorrechten, indem Sie Microsoft 365-Administratorrollen mehreren Microsoft 365-Benutzerkonten zuweisen, die von Ihrem Labhostinganbieter erstellt wurden. In dieser Übung lernen Sie die drei verschiedenen Methoden zum Zuweisen dieser Rollen kennen: 1) durch direktes Zuweisen einer Rolle zu einem Benutzerkonto im Microsoft 365 Admin Center, 2) durch Erstellen einer Rollengruppe, Zuweisen von Rollen zur Rollengruppe und anschließendes Zuweisen der Rollengruppe zu einem Benutzer im Microsoft 365 Admin Center und 3) durch Zuweisen einer Rolle zu einem Benutzer mithilfe von Windows PowerShell Nachdem Sie mehreren der vorhandenen Benutzerkonten Microsoft 365-Administratorrollen zugewiesen haben, testen Sie diese Zuweisungen, indem Sie überprüfen, ob die Benutzer über die Berechtigungen verfügen, gemäß ihren Rollen zu handeln. 


### ‎Aufgabe 1: Zuweisen einer Administratorrolle im Microsoft 365 Admin Center

Holly Dickson wurde die Microsoft 365-Rolle „Globaler Administrator“ zugewiesen. Da Sie als Holly fortfahren, verwenden Sie das Microsoft 365 Admin Center, um einem der Adatum-Benutzer Administratorrechte zuzuweisen. In dieser Aufgabe weisen Sie dem Benutzerkonto von Diego Siciliani die Rolle „Abrechnungsadministrator“ zu.

1. Sie haben das vorherige Lab auf LON-DC1 abgeschlossen. Sie sollten jetzt zurück zu **LON-CL1** wechseln, um die Microsoft 365-Verwaltungsaufgaben in dieser Labübung auszuführen. Als bewährte Methode sollten typische Microsoft 365-Verwaltungsaufgaben auf einem Clientcomputer statt auf dem Domänencontroller des Unternehmens ausgeführt werden.  <br/>

    Wechseln Sie zu **LON-CL1**. 

2. Auf **LON-CL1** im **Microsoft 365 Admin Center** in Ihrem Edge-Browser sollten Sie von einer früheren Labübung noch als Holly Dickson angemeldet sein. Wählen Sie im linken Bereich **Benutzer** und anschließend **Aktive Benutzer** aus. 

3. Wählen Sie in der Liste **Aktive Benutzer** den Namen **Diego Siciliani** aus.  <br/>

    **Hinweis:** Wählen Sie Diegos Namen aus. Aktivieren Sie nicht das Kontrollkästchen links neben seinem Namen. Das Kontrollkästchen wird in der Regel zum Auswählen mehrerer Benutzer verwendet, wenn Sie eine der benutzerbezogenen Aktionen auf der Menüleiste ausführen möchten, die oberhalb der Liste der Benutzer angezeigt wird, z. B. **Produktlizenzen verwalten** und **Rollen verwalten**. Wenn Sie einen Benutzernamen auswählen, wird ein Eigenschaftenbereich speziell für diesen Benutzer geöffnet.

4. Im erscheinenden Bereich **Diego Siciliani** wird standardmäßig die Registerkarte **Konto** angezeigt. Scrollen Sie auf dieser Registerkarte nach unten zum Abschnitt **Rollen**, und wählen Sie **Rollen verwalten** aus. 

5. Im Fenster **Administratorrollen verwalten** ist die Option **Benutzer (kein Admin Center-Zugriff)** standardmäßig aktiviert. Nachdem Sie Diego nun eine Administratorrolle zuweisen möchten, wählen Sie die Option **Admin Center-Zugriff** aus. Dadurch wird eine Liste der häufig verwendeten Administratorrollen für die Auswahl aktiviert. 

6. Diego wurde zum Abrechnungsadministrator höher gestuft, aber da diese Rolle nicht in der Liste der häufig verwendeten Rollen angezeigt wird, scrollen Sie nach unten, und wählen Sie **Alle nach Kategorie anzeigen** aus. 

7. Scrollen Sie in der Liste der Rollen, die nach Kategorie sortiert sind, nach unten zur Kategorie **Sonstige**, aktivieren Sie das Kontrollkästchen **Abrechnungsadministrator**, und wählen Sie dann **Änderungen speichern** aus. <br/>

    **Tipp:** Beachten Sie die Meldung, die oben im Bereich angezeigt wird, nachdem die Administratorrolle geändert wurde. Diese Meldung enthält die folgende bewährte Methode, die Sie berücksichtigen sollten, wenn Sie Administratorrollen in Ihren realen Bereitstellungen verwalten: **Erteilen Sie Benutzern nur den benötigten Zugriff, indem Sie die Rolle mit den geringstmöglichen Berechtigungen zuweisen.**

8. Wählen Sie im Fenster **Administratorrollen verwalten** das **X** in der oberen rechten Ecke des Bildschirms aus, um das Fenster zu schließen. Dadurch gelangen Sie zurück zur Liste **Aktive Benutzer**. 

9. Bleiben Sie bei LON-CL1 und im Microsoft 365 Admin Center als Holly Dickson angemeldet.

### ‎Aufgabe 2: Zuweisen einer Administratorrolle mithilfe einer Rollengruppe im Microsoft 365 Admin Center

In der vorherigen Aufgabe haben Sie eine Administratorrolle direkt dem Benutzerkonto von Diego Siciliani im Microsoft 365 Admin Center zugewiesen. In dieser Aufgabe weisen Sie stattdessen Rollen mithilfe einer Rollengruppe zu. Sie erstellen eine Sicherheitsrollengruppe, weisen ihr Benutzerverwaltungsrollen zu und weisen dann die Rollengruppe dem Benutzerkonto von Lynne Robbins im Microsoft 365 Admin Center zu.

1. Auf LON-CL1 sollten Sie weiterhin im Microsoft 365 Admin Center als Holly Dickson angemeldet sein. Wenn nicht, dann tun Sie das jetzt.

2. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Teams und Gruppen** und dann **Aktive Teams und Gruppen** aus. 

3. Auf der Seite **Aktive Teams und Gruppen** wird standardmäßig die Registerkarte **Teams- und Microsoft 365-Gruppen** angezeigt. Wählen Sie die Registerkarte **Sicherheitsgruppen** aus.

4. Wählen Sie auf der Registerkarte **Sicherheitsgruppen** auf der Menüleiste **+ Sicherheitsgruppe hinzufügen** aus. Dadurch wird der Assistent **Sicherheitsgruppe hinzufügen** gestartet.

5. Geben Sie im Assistenten **Sicherheitsgruppe hinzufügen** auf der Seite **Grundeinstellungen** den Text **Rollengruppe für Benutzerverwaltung** in das Feld **Name** ein. Geben Sie **Diese Rollengruppe enthält Benutzerverwaltungsrollen.** in das Feld **Beschreibung** ein. Wählen Sie **Weiter** aus.

6. Aktivieren Sie auf der Seite **Einstellungen bearbeiten** die Option **Azure AD-Rollen können der Gruppe zugewiesen werden**, und wählen Sie dann **Weiter** aus.

7. Überprüfen sie auf der Seite **Gruppe hinzufügen überprüfen und fertigstellen** die Einstellungen. Wenn Einstellungen geändert werden müssen, wählen Sie die entsprechende Option **Bearbeiten** aus, und nehmen Sie die Änderung vor. Wenn alle Einstellungen richtig sind, wählen Sie **Gruppe erstellen** aus.

8. Nachdem die **Rollengruppe für Benutzerverwaltung** erstellt wurde, wählen Sie **Schließen** aus.

9. Nachdem Sie die Rollengruppe erstellt haben, müssen Sie ihr die entsprechenden Rollen zuweisen. Auf der Seite **Aktive Teams und Gruppen** wird die Registerkarte **Sicherheitsgruppen** angezeigt. Wählen Sie die **Rollengruppe für Benutzerverwaltung** aus, um den Detailbereich zu öffnen.

10. Im Bereich **Rollengruppe für Benutzerverwaltung** wird standardmäßig die Registerkarte **Allgemein** angezeigt. Wählen Sie im Abschnitt **Rollen** die Option **Rollen verwalten** aus.

11. Wählen Sie im angezeigten Bereich **Administratorrollen verwalten** die Option **Admin Center-Zugriff** aus. Aktivieren Sie in der Liste der häufigen Administratorrollen, die direkt unter dieser Option angezeigt werden, die Kontrollkästchen **Benutzeradministrator** und **Erfolgsmanager für das Benutzererlebnis**. Wählen Sie dann die Option **Alle nach Kategorie anzeigen** aus. Scrollen Sie nach unten zur Kategorie **Identität**. Sie sehen, dass die Rolle **Benutzeradministrator** bereits ausgewählt ist, da Sie diese weiter oben in der Liste der häufig verwendeten Rollen ausgewählt haben. Wählen Sie in der Kategorie **Identität** die Rolle **Helpdeskadministrator** aus, und wählen Sie dann **Änderungen speichern** aus. 

12. Im Bereich **Administratorrollen verwalten** sollten die drei ausgewählten Rollen unter der Option **Admin Center-Zugriff** angezeigt werden. Wählen Sie das **X** oben rechts im Bereich aus, um ihn zu schließen.

13. Wählen Sie auf der Registerkarte **Sicherheitsgruppen** die **Rollengruppe für Benutzerverwaltung** aus. Überprüfen Sie im angezeigten Bereich **Rollengruppe für Benutzerverwaltung**, ob die drei Rollen im Abschnitt **Rollen** angezeigt werden. Schließen Sie diesen Bereich.

14. Nachdem Sie der Rollengruppe nun die Rollen zugewiesen haben, müssen Sie die Rollengruppe dem Benutzerkonto von Lynne Robbins zuweisen. Wählen Sie im **Microsoft 365 Admin Center** die Option **Aktive Benutzer** aus.

15. Wählen Sie auf der Seite **Aktive Benutzer** den Namen **Lynne Robbins** aus. 

16. Im erscheinenden Bereich **Lynne Robbins** wird standardmäßig die Registerkarte **Konto** angezeigt. Bei der vorherigen Aufgabe haben Sie, als Sie dem Konto von Diego Siciliani die Rolle „Abrechnungsadministrator“ zugewiesen haben, die Option **Rollen verwalten** unter dem Abschnitt **Rollen** ausgewählt. Da Sie die Rollen von Lynne jedoch über eine Rollengruppe zuweisen, müssen Sie Lynne zum Mitglied der soeben erstellten Sicherheitsrollengruppe machen. Durch die Gruppenzuweisung erbt Lynne die Rollen, die der Rollengruppe zugewiesen sind. Wählen Sie daher im Abschnitt **Gruppen** die Option **Gruppen verwalten** aus. 

17. Wählen Sie im Bereich **Gruppen verwalten** die Option **+ Mitgliedschaften zuweisen** aus.

18. Aktivieren Sie im Bereich **Mitgliedschaften** das Kontrollkästchen **Rollengruppe für Benutzerverwaltung**, und wählen Sie dann **Hinzufügen (1)** aus.

19. Sobald oben auf der Seite die Benachrichtigung **Gespeichert** angezeigt wird, schließen Sie diesen Bereich. 

20. Um zu überprüfen, ob Lynne die Rollen geerbt hat, die „Rollengruppe für Benutzerverwaltung“ zugewiesen wurden, wählen Sie **Lynne Robbins** aus der Liste der aktiven Benutzer aus. 

21. Im erscheinenden Bereich **Lynne Robbins** sollten auf der Registerkarte **Konto**, die standardmäßig angezeigt wird, die drei Benutzerverwaltungsrollen angezeigt werden, die Lynne zugewiesen wurden. Wählen Sie im Abschnitt **Rollen** die Option **Rollen verwalten** aus.

22. Beachten Sie im erscheinenden Bereich **Administratorrollen verwalten** unter der Option **Admin Center-Zugriff** die drei ausgewählten Rollen und den Namen der Gruppe, aus der sie Lynne zugewiesen wurden. Beachten Sie außerdem, dass die drei Rollen ausgegraut sind. Das bedeutet, dass Sie die Auswahl der Rollen über dieses Fenster nicht aufheben können. Da die Rollen Lynne über eine Rollengruppe zugewiesen wurden, die diese Rollen enthielt, können Sie die Zuweisung der Rollen nur aufheben, indem Sie Lynne als Mitglied der Rollengruppe entfernen. Sie haben gerade überprüft, ob Lynne diese Rollen zugewiesen sind. Schließen Sie den Bereich **Administratorrollen verwalten**.

23. Bleiben Sie bei LON-CL1 und im Microsoft 365 Admin Center als Holly Dickson angemeldet.

### Aufgabe 3: Zuweisen einer Administratorrolle mit Windows PowerShell  

In dieser Aufgabe verwenden Sie Windows PowerShell, um einem Benutzerkonto eine Rolle zuzuweisen. Dadurch lernen Sie die Verwaltungsfunktion in PowerShell kennen, da einige Administratoren PowerShell für solche Verwaltungsvorgänge bevorzugen.  

In dieser Aufgabe möchte Holly Patti Fernandez die Rolle „Dienstsupportadministrator“ zuweisen. Um einen Benutzer mithilfe des Microsoft Graph-Moduls von PowerShell einer Administratorrolle hinzuzufügen, müssen Sie zuerst die Objekt-ID des Benutzers und die Objekt-ID der Rolle abrufen. Wenn die Rolle noch nicht aktiviert wurde (d. h., dass sie keinem Benutzer zugewiesen oder überhaupt nicht aktiviert wurde), müssen Sie die Rolle zuerst aktivieren, bevor Sie sie einem Benutzer mithilfe von PowerShell zuweisen können. In dieser Aufgabe aktivieren Sie zuerst die Rolle „Dienstsupportadministrator“, bevor Sie sie Patti Fernandez zuweisen.

PowerShell ermöglicht es Ihnen auch, alle Benutzer anzuzeigen, die einer bestimmten Rolle zugewiesen sind, was bei der Überwachung Ihrer Microsoft 365-Bereitstellung sehr wichtig sein kann. In dieser Aufgabe lernen Sie auch, wie Sie PowerShell verwenden, um alle Benutzer anzuzeigen, die einer bestimmten Rolle zugewiesen sind. 

1. Wählen Sie auf LON-CL1 das Windows PowerShell-Symbol auf der Taskleiste aus, das noch von einem vorherigen Lab vorhanden ist. Wenn Sie das PowerShell-Fenster geschlossen haben, öffnen Sie eine Instanz mit erhöhten Rechten, indem Sie dieselbe Anweisung wie zuvor verwenden. 

2. Ihre PowerShell-Sitzung sollte weiterhin mit dem Microsoft Graph-Modul von PowerShell aus der vorherigen Übung verbunden sein, in der Sie eine gelöschte Gruppe mithilfe von PowerShell wiederhergestellt haben. Wenn Sie PowerShell jedoch zuvor geschlossen und gerade erneut geöffnet haben, importieren Sie das Untermodul „Microsoft.Graph.Identity.DirectoryManagement“ mithilfe der Schritte aus der vorherigen Labübung. 

3. Um Microsoft 365-Benutzerwartungsaufgaben über das Microsoft Graph-Modul von PowerShell zu erledigen, müssen Sie zuerst das Untermodul „Microsoft.Graph.Users“ importieren und Lese-/Schreibberechtigungen anfordern. Um dieses Untermodul zu importieren, geben Sie in der Eingabeaufforderung den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE:   <br/>

        Import-Module Microsoft.Graph.Users

4. In der früheren Labübung haben Sie eine Verbindung mit Microsoft Graph hergestellt und die Berechtigungen „Directory.ReadWrite.All“ angefordert, um die Cmdlets auszuführen, die die gelöschte Gruppe wiederhergestellt haben. Um Benutzer- und Rollenobjekte in dieser Aufgabe zu aktualisieren, muss Holly jetzt Lese-/Schreibberechtigungen für jedes Objekt anfordern. Um diese Berechtigungen anzufordern, geben Sie den folgenden Befehl in der Eingabeaufforderung ein, und drücken Sie dann die EINGABETASTE:  <br/>

        Connect-MgGraph -Scopes 'User.ReadWrite.All', 'RoleManagement.ReadWrite.Directory'

5. Wählen Sie im angezeigten Fenster **Konto auswählen** das Konto von Holly Dickson aus. 

6. Aktivieren Sie im daraufhin erscheinenden Dialogfeld **Angeforderte Berechtigungen** das Kontrollkästchen **Zustimmung im Namen Ihrer Organisation**, und wählen Sie dann **Akzeptieren** aus.

7. Holly möchte **Patti Fernandez** die Rolle **Dienstsupportadministrator** zuweisen. Um diese Rolle mithilfe des Microsoft Graph-Moduls von PowerShell zuzuweisen, müssen Sie zuerst die Objekt-ID der Rolle „Dienstsupportadministrator“ abrufen, damit Sie sie Patti zuweisen können. In Microsoft Graph-Modul von PowerShell können Sie jedoch nur Rollen zuweisen, die aktiviert wurden. Aktivierte Rollen sind Rollen, die entweder über eine Rollenvorlage aktiviert oder Benutzern bereits über PowerShell oder das Microsoft 365 Admin Center zugewiesen wurden. <br/>

    **Wichtig:** Bevor Sie diesen Schritt ausführen, überprüfen Sie, ob sich Ihr PowerShell-Fenster im Vollbildmodus befindet. Der Rollenname wird in der letzten Spalte ganz rechts auf dem Bildschirm angezeigt. Wenn Sie sich nicht im Vollbildmodus befinden, wird der Rollenname nicht angezeigt, der jeder Objekt-ID zugeordnet ist. 

    Um alle aktivierten Rollen in Microsoft 365 anzuzeigen, geben Sie in der Eingabeaufforderung den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE: <br/>
    
        Get-MgDirectoryRole    <br/>

    **Hinweis:** Mit diesem Befehl werden die Rollen angezeigt, die bisher in Microsoft 365 aktiviert wurden. Wenn die Rolle „Dienstsupportadministrator“ in dieser Liste vorhanden wäre, könnten Sie direkt mit Schritt 13 fortfahren, um die Rolle Patti zuzuweisen. Da „Dienstsupportadministrator“ jedoch nicht in dieser Liste der aktivierten Rollen enthalten ist, müssen Sie die Schritte 8 bis 12 befolgen, um die Rolle über die entsprechende Rollenvorlage zu aktivieren, bevor Sie Patti die Rolle in Schritt 13 zuweisen können. 

8. Um eine Rolle über das Microsoft Graph-Modul von PowerShell zu aktivieren, müssen Sie zuerst die Vorlage suchen, um die Objekt-ID der Vorlage abzurufen. Sie müssen die Objekt-ID der Vorlage kennen, um die Rolle über die Vorlage zu aktivieren. Es gibt zwei Möglichkeiten, um Rollenvorlagen anzuzeigen: Sie können entweder die gesamte Liste der Rollenvorlagen oder die Vorlage für eine bestimmte Rolle anzeigen. Zu Lernzwecken führen Sie beide Methoden aus, damit Sie den Unterschied sehen können. <br/>

    Beginnen wir damit, die vollständige Liste der Rollenvorlagen zusammen mit der Objekt-ID und dem Anzeigenamen anzuzeigen. Geben Sie dazu den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE: <br/>

        Get-MgDirectoryRoleTemplate | Format-List Id, DisplayName   <br/>

    Wie Sie feststellen, müssen Sie, nachdem Sie diesen Befehl ausgeführt haben, durch die Liste der Rollenvorlagen scrollen und nach der Rolle „Dienstsupportadministrator“ suchen. Sie können leicht sehen, wie mühsam das sein kann. Führen Sie alternativ den folgenden Befehl aus, um eine bestimmte Rollenvorlage abzufragen – in diesem Fall die Rollenvorlage „Dienstsupportadministrator“: <br/>

        Get-MgDirectoryRoleTemplate | ? DisplayName -eq "Service Support Administrator"   <br/>

    Nachdem Sie diesen Befehl ausgeführt haben, sehen Sie, dass nur die angeforderte Rollenvorlage angezeigt wird. Natürlich kann es vorkommen, dass das Anzeigen der gesamten Liste der Rollenvorlagen erforderlich ist. Wenn Sie jedoch eine einzelne Rollenvorlage nachschlagen müssen, ist das Ausführen des zweiten PowerShell-Befehls wesentlich effizienter, als durch die gesamte Liste der Vorlagen scrollen zu müssen.
    
9. Nachdem Sie nun die Rollenvorlage „Dienstsupportadministrator“ im vorherigen Schritt abgefragt haben, markieren Sie die **ID** (z. B. fe930be7-5e62-47db-91af-98c3a49a38b1), und drücken Sie **STRG+C**, um sie in die Zwischenablage zu kopieren. Wenn Sie sie kopieren, wird die Markierung ausgeblendet.

10. Sie erstellen nun eine Variable, die die Attribute für die Vorlage „Dienstsupportadministrator“ erfasst. Wenn Sie den folgenden Befehl eingeben, drücken Sie **STRG+V**, um die Vorlagen-ID für „Dienstsupportadministrator“ einzufügen, die Sie im vorherigen Schritt in die Zwischenablage kopiert haben. <br/>

    Geben Sie in der Eingabeaufforderung den folgenden Befehl ein, und drücken Sie die Eingabetaste: <br/>

        $ServiceSupportRoleTemplate = @{ RoleTemplateID = "paste in template ID here" }  <br/>

    Beispiel: $ServiceSupportRoleTemplate = @{ RoleTemplateID = "fe930be7-5e62-47db-91af-98c3a49a38b1" }

11. Sie können nun die Rolle „Dienstsupportadministrator“ basierend auf den Attributen der Vorlage aktivieren, die Sie in der Variablen „$ServiceSupportRoleTemplate“ erfasst haben. Geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE:  <br/>

        New-MgDirectoryRole -BodyParameter $ServiceSupportRoleTemplate

12. Um zu überprüfen, ob die Rolle „Dienstsupportadministrator“ aktiviert wurde, geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE. Durch diesen Befehl wird die Liste der aktivierten Rollen angezeigt:  <br/>
            
        Get-MgDirectoryRole <br/>

    **Hinweis:** Mit diesem Befehl wird die Objekt-ID aller aktivierten Rollen angezeigt, einschließlich der Rolle „Dienstsupportadministrator“, die Sie soeben über die Vorlage aktiviert haben. In Schritt 15 kopieren Sie die Objekt-ID der Rolle „Dienstsupportadministrator“ und fügen Sie ein, wenn Sie Patti diese Rolle zuweisen.

13. Um Patti Fernandez die neu aktivierte Rolle „Dienstsupportadministrator“ zuzuweisen, müssen Sie zuerst die Objekt-ID für das Benutzerkonto von Patti abrufen. Geben Sie dazu den folgenden Befehl ein, und drücken Sie die EINGABETASTE: <br/>

        Get-MgUser | Format-List ID, DisplayName

14. Nachdem Sie nun die Objekt-ID der kürzlich aktivierten Rolle „Dienstsupportadministrator“ und die Objekt-ID des Benutzerkontos von Patti kennen, können Sie Patti die Rolle zuweisen. Führen Sie die folgenden Schritte aus, um diesen Vorgang abzuschließen: <br/>

    a. Mit dem vorherigen Befehl haben Sie die Liste der aktiven Benutzer angezeigt. Markieren Sie den **Id**-Wert für das Konto von Patti, und kopieren Sie ihn mit **STRG+C** in die Zwischenablage. Die Markierung verschwindet, sobald er in die Zwischenablage kopiert wurde.  <br/>

    b. Führen Sie den folgenden Befehl aus, der eine Variable erstellt, die das Verzeichnisobjekt für das Benutzerkonto von Patti enthält. Fügen Sie beim Eingeben dieses Befehls mit **STRG+V** die ID ein, die Sie soeben für das Benutzerkonto von Patti kopiert haben. <br/>

        $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/paste in Patti's user account ID here" }  <br/>

    Beispiel: $UserObject = @{ "@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/22fddbf7-42d2-4698-be65-ebc972a023e3" }

    c. In Schritt 12 haben Sie die Liste der aktivierten Rollen angezeigt. Markieren Sie die ID für die Rolle „Dienstsupportadministrator“, und kopieren Sie sie mit **STRG+C** in die Zwischenablage. <br/>

    d. Führen Sie den folgenden Befehl aus, der die Variable, die das Benutzerkonto von Patti ($UserObject) enthält, der Verzeichnisrolle zuweist. Fügen Sie beim Eingeben dieses Befehls mit **STRG+V** die ID ein, die Sie soeben für die Rolle „Dienstsupportadministrator“ kopiert haben. <br/> 

        New-MgDirectoryRoleMemberByRef -DirectoryRoleId 'paste in the ID of the role here' -BodyParameter $UserObject
                
15. Sie sollten nun überprüfen, ob Patti die Rolle „Dienstsupportadministrator“ zugewiesen wurde. Sie haben zuvor die Objekt-ID dieser Rolle in die Zwischenablage kopiert und in den vorherigen Befehl eingefügt. Sie sollten sie ebenfalls in diesen Befehl einfügen. Geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE:
    
        Get-MgDirectoryRoleMember -DirectoryRoleId 'paste in the ID of the role here' 
                
16. Im vorherigen Befehl werden nur die IDs der Benutzer angezeigt, denen die ausgewählte Rolle zugewiesen ist. Sie können jedoch die angezeigte ID mit Pattis ID abgleichen, um zu überprüfen, ob ihrem Konto die Rolle **Dienstsupportadministrator** zugewiesen wurde. Wie Sie sehen können, ist Patti die einzige Benutzerin, der die Rolle zugewiesen ist. 

17. Wiederholen wir nun diesen Vorgang, um alle Benutzer anzuzeigen, denen die Rolle „Globaler Administrator“ zugewiesen ist. Wiederholen Sie Schritt 15, um zu überprüfen, wie vielen Adatum-Benutzern die Rolle **Globaler Administrator** zugewiesen wurde. Um diesen Befehl zu vervollständigen, müssen Sie zuerst die ID der Rolle „Globaler Administrator“ in die Zwischenablage kopieren (**STRG+C**). Sie finden diese ID in der Liste der aktivierten Rollen, wenn Sie Schritt 12 ausgeführt haben. <br/>

    **Warnung:** Kopieren Sie die ID der Rolle „Globaler Administrator“ und NICHT die ID der Rollenvorlage „Globaler Administrator“.

18. Überprüfen Sie, ob mehrere Adatum-Benutzer vorhanden sind, denen die Rolle „Globaler Administrator“ zugewiesen wurde. In einem realen Szenario würde der Microsoft 365-Administrator diesen PowerShell-Befehl verwenden, um zu überwachen, wie viele globale Administratoren in der Microsoft 365-Bereitstellung vorhanden sind. Dann würde er die Rolle „Globaler Administrator“ allen Benutzern entziehen, die sie nicht besitzen sollten. Zur Erinnerung: Der Richtwert sind zwei bis vier globale Administratoren pro Microsoft 365-Bereitstellung, je nach Größe der Organisation.  <br/>

    Im Falle dieses Labs, in dem Ihr Labhostinganbieter die Rolle „Globaler Administrator“ auch anderen Benutzern als dem MOD-Administrator zugewiesen hat (und Sie haben sie Holly Dickson zugewiesen), lassen Sie diese Benutzer wie sie sind. In dieser fiktiven Adatum-Bereitstellung ergibt es keinen Sinn, Zeit aufzuwenden, um diese Rolle aus den Konten zu entfernen. Darüber hinaus basieren einige der zukünftigen Labaufgaben auf diesen Benutzern, denen die Rolle „Globaler Administrator“ zugewiesen ist. <br/>

    **WICHTIG:** Bedenken Sie jedoch, dass der Microsoft 365-Administrator in Ihrer realen Bereitstellung die Rolle „Globaler Administrator“ regelmäßig überwachen sollte, um die Anzahl der zugewiesenen Benutzer zwischen 2 und 4 zu halten.
    
19. Lassen Sie Ihre Windows PowerShell-Sitzung für zukünftige Labübungen geöffnet, minimieren Sie sie jedoch, bevor Sie mit der nächsten Aufgabe fortfahren.


### Aufgabe 4: Überprüfen von Rollenzuweisungen 

In dieser Aufgabe beginnen Sie mit der Untersuchung der Administratoreigenschaften von zwei Benutzerinnen, Joni Sherman und Lynne Robbins. Anschließend melden Sie sich auf der Microsoft 365-Startseite auf der Client-VM 2 (LON-CL2) mit dem Konto jedes Benutzers an, um mehrere der Änderungen zu bestätigen, die Sie beim Delegieren der Administratorrechte in den vorherigen Aufgaben vorgenommen haben. Schließlich führen Sie als Lynne Robbins zwei wichtige Verwaltungsaufgaben für Benutzerkonten durch: das Zurücksetzen von Kennwörtern und das Blockieren von Benutzerkonten.

1. Auf LON-CL1 sollten Sie weiterhin im Microsoft 365 Admin Center als Holly Dickson angemeldet sein. Wenn nicht, dann tun Sie das jetzt.

2. Wenn im **Microsoft 365 Admin Center** nicht die Seite **Aktive Benutzer** angezeigt wird, navigieren Sie jetzt zu dieser.  

3. Wählen Sie in der Liste **Aktive Benutzer** den Namen **Joni Sherman** aus. 

4. Im Eigenschaftenfenster von **Joni Sherman** wird standardmäßig die Registerkarte **Konto** angezeigt. Im Abschnitt **Rollen** sollte zu sehen sein, dass Joni **keinen Administratorzugriff** hat. Wählen Sie das **X** in der oberen rechten Ecke aus, um das Eigenschaftenfenster von Joni zu schließen.

5. Wählen Sie in der Liste **Aktive Benutzer** den Namen **Lynne Robbins** aus. 

6. In **Eigenschaftenfenster** von Lynne Robbins sollte zu sehen sein, dass Lynne die Rolle **Benutzeradministrator** zugewiesen wurde. Schließen Sie das Eigenschaftenfenster von Lynne.

7. Wechseln Sie zur Client-VM 2 (**LON-CL2**).

8. Melden Sie sich auf **LON-CL2** im Anmeldebildschirm mit dem lokalen **Administratorkonto** mit dem Kennwort **Pa55w.rd** an.

9. Wenn das Fenster **Netzwerke** angezeigt wird, wählen Sie **Ja** aus.

10. Wählen Sie auf der Taskleiste das Symbol **Microsoft Edge** aus. Maximieren Sie bei Bedarf Ihr Edge-Browserfenster.

11. Navigieren Sie in Ihrem **Edge**-Browser zu **https://portal.office.com**. 

12. Sie beginnen mit der Anmeldung bei Microsoft 365 als **Joni Sherman**. Geben Sie im Fenster **Anmelden** **JoniS@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist. <br/>

    **Wichtig:** Ihr Lab-Hostinganbieter hat dem MOD-Administratorkonto ein **Administratives Kennwort** zugewiesen, und Sie haben dem Konto von Holly Dickson beim Erstellen dieses Kontos das gleiche **Administratives Kennwort** zugewiesen. Ihr Lab-Hostinganbieter hat jedoch allen anderen vordefinierten Benutzerkonten ein anderes **Benutzerkennwort** zugewiesen. In Zukunft müssen Sie bei der Anmeldung als anderer Benutzer als MOD-Administrator oder Holly Dickson dieses **Benutzerkennwort** und NICHT das **Administrative Kennwort** eingeben. <br/>

    Da Sie sich als Joni Sherman anmelden, geben Sie dieses **Benutzerkennwort** im Fenster **Kennwort eingeben** ein. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus.

13. Aktivieren Sie im Fenster **Angemeldet bleiben?** das Kontrollkästchen **Nicht mehr anzeigen**, und wählen Sie dann **Ja** aus. Wenn das Fenster **Kennwort speichern** angezeigt wird, wählen Sie **Nie** aus.

14. Wenn in der Mitte der Seite das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, wählen Sie zweimal den Vorwärtspfeil (>) und dann das Häkchen aus, um es zu schließen.

15. Wenn das Fenster **Nach weiteren Apps suchen** angezeigt wird, wählen Sie das **X** in der oberen rechten Ecke des Fensters aus, um es zu schließen.

16. Im Fenster **Willkommen bei Microsoft 365**, der Microsoft 365-Startseite von Joni, befindet sich auf der linken Seite des Bildschirms ein Navigationsbereich mit den Anwendungen, auf die der Benutzer zugreifen kann. Sie sehen, dass die Option **Administrator** im Bereich **Apps** nicht angezeigt wird. Das liegt daran, dass Joni nie eine Microsoft 365-Administratorrolle zugewiesen wurde. 

17. Sie melden sich jetzt bei Microsoft 365 als Joni ab. Wählen Sie in **Microsoft Edge**oben rechts auf der Seite **Willkommen bei Microsoft 365** das Benutzersymbol für **Joni Sherman** (der Kreis in der oberen rechten Ecke mit dem Bild von Joni) und im angezeigten Fenster von **Joni Sherman** die Option **Abmelden** aus. 

18. Sie melden sich jetzt wieder als **Lynne Robbins** bei Microsoft 365 an. In Ihrer aktuellen **Edge**-Browserregisterkarte sollte die Meldung **Joni, Sie sind jetzt abgemeldet** angezeigt werden. In diesem Fenster haben Sie die Möglichkeit, sich wieder als Joni oder als anderer Benutzer anzumelden. <br/>

    Wählen Sie **Zu einem anderen Konto wechseln** aus, und geben Sie im angezeigten Feld **E-Mail-Adresse** die Adresse **LynneR@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist. Wählen Sie dann **Anmelden** aus. Geben Sie im Fenster **Passwort eingeben** das von Ihrem Labor-Hosting-Anbieter bereitgestellte **Benutzerkennwort** ein und wählen Sie **Anmelden**. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus. 

19. Wenn das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, wählen Sie zweimal den Vorwärtspfeil (>) und dann das Häkchen aus, um das Fenster zu schließen.

20. Wenn das Fenster **Nach weiteren Apps suchen** angezeigt wird, wählen Sie das **X** in der oberen rechten Ecke des Fensters aus, um es zu schließen.

21. Beachten Sie im Fenster **Willkommen bei Microsoft 365**, der Microsoft 365-Startseite von Lynne, dass das Symbol **Administrator** im Navigationsbereich auf der linken Seite des Bildschirms angezeigt wird. Dieses Symbol wird angezeigt, da Lynne eine Microsoft 365-Administratorrolle zugewiesen wurde. Wählen Sie das Symbol **Admin** aus, um das Microsoft 365 Admin Center zu öffnen.

22. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Benutzer** und dann **Aktive Benutzer** aus. 

23. Als **Benutzeradministrator** verfügt Lynne über die Berechtigung zum Ändern von Benutzerkennwörtern. Lynne wurde kürzlich von **Diego Siciliani** und **Pradeep Gupta** kontaktiert, die beide berichteten, dass ihre Kennwörter kompromittiert wurden. Gemäß der Unternehmensrichtlinie von Adatum muss Lynne ihre Kennwörter auf einen temporären Wert zurücksetzen und dann erzwingen, dass das Kennwort bei der nächsten Anmeldung zurückgesetzt wird.   <br/>

    ‎Beachten Sie in der Liste **Aktive Benutzer**, während Sie die Maus von einem Benutzerkonto zum anderen bewegen, das **Schlüsselsymbol (Kennwort zurücksetzen)**, das rechts neben dem Namen jedes Benutzers angezeigt wird. Wählen Sie das Schlüsselsymbol aus, das rechts neben dem Namen von **Diego Siciliani** angezeigt wird.

24. Wenn im Fenster **Kennwort zurücksetzen** für Diego das Kontrollkästchen **Kennwort automatisch erstellen** ein Häkchen aufweist, wählen Sie dieses Kontrollkästchen aus, um es zu deaktivieren. Dadurch kann Lynne Diego manuell ein temporäres Kennwort zuweisen.  

25. Geben Sie **diego** in das Feld **Kennwort** ein. Rechts neben dem Kennwort zeigt das System eine Meldung an, dass es sich um ein **schwaches Kennwort** handelt. Beachten Sie außerdem die Meldung, die unterhalb des Felds angezeigt wird, die die Anforderungen an ein starkes Kennwort enthält. Beachten Sie schließlich, dass die Schaltfläche **Kennwort zurücksetzen** unten im Bereich nicht aktiviert ist. **Diese Schaltfläche wird nur aktiviert, wenn Sie ein starkes Kennwort eingeben.**  

26. Vergewissern Sie sich, dass das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern** aktiviert ist. Wenn nicht, aktivieren Sie es jetzt. Geben Sie **Pa55w.rd** in das Feld **Kennwort** ein. Beachten Sie, dass das Feld **Kennwort** angibt, dass es sich um ein starkes Kennwort handelt. <br/>

    Deaktivieren Sie nun jedoch das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern**. Beachten Sie die angezeigte Fehlermeldung, die angibt, dass das Kennwort (Pa55w.rd) ein Wort, einen Ausdruck oder eine Zahlenfolge enthält, die leicht erraten werden können. In diesem Fall haben Sie eine Variation des Worts **password** eingegeben, wodurch dieser Fehler ausgelöst wird. Das System erlaubt Ihnen, dieses Kennwort einzugeben, wenn Sie erzwingen, dass der Benutzer es bei der ersten Anmeldung ändert. Wenn Sie jedoch nicht erzwingen, dass der Benutzer bei der ersten Anmeldung ein anderes Kennwort eingibt, ist dieses Kennwort nicht zulässig.

27. Nachdem diese beiden fehlgeschlagenen Kennwortversuche aufgetreten sind, hat Lynne beschlossen, Microsoft 365 das automatische Generieren eines Kennworts zu ermöglichen. Aktivieren Sie das Kontrollkästchen **Kennwort automatisch erstellen**. <br/>
    
28. Das automatisch generierte Kennwort ist nur ein temporäres Kennwort, da Lynne erzwingen möchte, dass Diego es bei der nächsten Anmeldung ändert. Überprüfen Sie daher, ob das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern** aktiviert ist. Wenn nicht, aktivieren Sie es.

29. **Kennwortzurücksetzung** auswählen.

30. Wenn Sie zum Speichern des Kennworts aufgefordert werden, wählen Sie **Nie** aus, um das Fenster zu schließen.

31. Sie sollten eine Fehlermeldung erhalten, dass Sie Diegos Kennwort nicht zurücksetzen können, weil ihm eine Administratorrolle zugewiesen wurde. In Diegos Fall haben Sie ihm früher in dieser Übung die Rolle „Abrechnungsadministrator“ zugewiesen. Da nur globale Administratoren das Kennwort eines anderen Administrators ändern können und Lynne kein globaler Administrator ist, muss sie Holly Dickson bitten, diese Änderung vorzunehmen. Wählen Sie im Bereich **Kennwort zurücksetzen** die Option **Schließen** aus. 

32. Wenn ein Fenster mit einer Umfrage angezeigt wird, wählen Sie **Abbrechen** aus.

33. Wählen Sie in der Liste **Aktive Benutzer** das **Schlüsselsymbol (Kennwort zurücksetzen)** für **Pradeep Gupta** aus. 

34. Überprüfen Sie im Fenster **Kennwort zurücksetzen** für Pradeep, ob das Kontrollkästchen **Kennwort automatisch erstellen** aktiviert ist. Wenn nicht, aktivieren Sie es jetzt, damit das System automatisch ein Kennwort für Pradeep generiert.  <br/>

    Das ist nur ein temporäres Kennwort, da Lynne erzwingen möchte, dass Pradeep es bei seiner nächsten Anmeldung ändert. Überprüfen Sie daher, ob das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern** aktiviert ist. Wenn nicht, aktivieren Sie es.
    
35. Wählen Sie die Schaltfläche **Kennwort zurücksetzen** aus.

36. Im Fenster **Das Kennwort wurde zurückgesetzt.** sollte eine Meldung vorhanden sein, dass Sie das Kennwort für Pradeep erfolgreich zurückgesetzt haben. Wählen Sie **Schließen** aus.

37. Die Verwaltung hat kürzlich festgestellt, dass Alex Wilbers Benutzername möglicherweise kompromittiert wurde. Daher wurde Lynne gebeten, das Konto von Alex zu blockieren, damit sich niemand mit seinem Benutzernamen anmelden kann, bis die Verwaltung in der Lage ist, den Umfang des Problems zu bestimmen. Aktivieren Sie in der Liste **Aktive Benutzer** das Kontrollkästchen links neben **Alex Wilbers** Namen (wählen Sie nicht den Namen von Alex selbst aus).  <br/>

    **Wichtig:** Da Sie einen globalen Befehl anstelle eines Befehls für das Konto von Alex ausführen möchten, soll nur das Konto von Alex in der Liste der aktiven Benutzer ausgewählt werden. Wenn ein anderes Benutzerkonto ausgewählt ist, müssen Sie die Auswahl dieses Benutzerkontos aufheben, bevor Sie fortfahren. Scrollen Sie durch die Liste der aktiven Benutzer, und achten Sie darauf, dass kein anderes Benutzerkonto ausgewählt ist. Wenn ein anderes Konto als Alex‘ Konto ausgewählt ist, deaktivieren Sie das Kontrollkästchen des Kontos. **Nur Alex Wilbers Konto sollte ausgewählt sein.**

38. Wählen Sie in der Menüleiste oben auf der Seite die **Auslassungspunkte (...)** aus, um ein Dropdownmenü mit zusätzlichen Aktionen anzuzeigen. Wählen Sie im daraufhin angezeigten Menü **Anmeldestatus bearbeiten** aus.

39. Überprüfen Sie im angezeigten Bereich **Anmeldung blockieren**, ob die E-Mail-Adresse von Alex unter der Überschrift **Anmeldung blockieren** angezeigt wird. Aktivieren Sie das Kontrollkästchen **Diesen Benutzer an der Anmeldung hindern**, und wählen Sie dann **Änderungen speichern** aus. 

40. Im Fenster **Anmeldung blockieren** sollte eine Meldung angezeigt werden, dass Alex jetzt daran gehindert wird, sich anzumelden. Das heißt, dass niemand sich mit Alex‘ Benutzernamen anmelden kann, falls sein Benutzername tatsächlich kompromittiert wurde. Darüber hinaus wird Alex innerhalb von 60 Minuten automatisch von Microsoft-Diensten abgemeldet. Wählen Sie das **X** in der oberen rechten Ecke des Bereichs aus, um ihn zu schließen. 

41. Lynne wurde soeben informiert, dass **Nestor Wilkes** Benutzername ebenfalls potenziell kompromittiert wurde. Wiederholen Sie die Schritte 33 bis 36, um zu verhindern, dass Nestor oder andere seinen Benutzernamen zum Anmelden verwenden. <br/>

    Wenn Sie versucht haben, die Anmeldung von Nestor zu blockieren, sollten Sie die Fehlermeldung **Ihre Änderungen konnten nicht gespeichert werden.** erhalten haben. Sie haben diesen Fehler erhalten, weil Nestor ein globaler Administrator ist und Lynne nicht. Nur ein globaler Administrator kann verhindern, dass ein anderer globaler Administrator sich anmelden kann. Lynne muss Holly Dickson bitten, diese Änderung vorzunehmen. <br/>

    Schließen Sie den Bereich **Anmeldung blockieren**.

42. Sie haben zuvor Alex Wilber daran gehindert, sich anzumelden. Um zu überprüfen, ob er blockiert ist, versuchen Sie, sich als Alex anzumelden. Melden Sie sich bei Microsoft 365 ab, indem Sie das Benutzersymbol für **Lynne Robbins** (den Kreis mit dem Bild von Lynne in der oberen rechten Ecke) und dann im angezeigten Fenster **Lynne Robbins** die Option **Abmelden** auswählen. 

43. Sie sollten alle Browserregisterkarten mit Ausnahme der Registerkarte **Abmelden** schließen, nachdem Sie abgemeldet wurden. Navigieren Sie auf der Registerkarte **Abmelden** zu **https://portal.office.com**. 

44. Wählen Sie im Fenster **Konto auswählen** die Option **Anderes Konto verwenden** aus. Geben Sie im Fenster **Anmelden** **AlexW@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist. Geben Sie im Fenster **Passwort eingeben** das von Ihrem Labor-Hosting-Anbieter bereitgestellte **Benutzerkennwort** ein.  <br/>

    Das Fenster **Konto auswählen** sollte erscheinen, und es sollte eine Fehlermeldung angezeigt werden: **Ihr Konto wurde gesperrt. Wenden Sie sich an einen Mitarbeiter Ihrer Supportabteilung, um das Konto entsperren zu lassen.** Sie haben gerade überprüft, dass Alex (oder jemand, der an Alex‘ Benutzername und Kennwort gelangt ist) sich nicht anmelden kann. <br/>

    **Hinweis:** Es kann einige Minuten dauern, bis die Kontoblockierung vollständig implementiert wurde. Bis die Blockierung im System implementiert wurde, kann sich Alex möglicherweise noch anmelden, aber keiner der Microsoft 365-Dienste steht ihm zur Verfügung, und sie werden nicht im Microsoft 365-Portal angezeigt. Sobald die Blockierung eines Kontos aufgehoben wurde, sind die Dienste wieder verfügbar. <br/>

    Wenn Sie sich als Alex anmelden können, melden Sie sich ab, und warten Sie einige Minuten. Das ist eine gute Gelegenheit für eine kurze Pause. Versuchen Sie dann, sich wieder als Alex anzumelden. Zu diesem Zeitpunkt sollten Sie hoffentlich die Fehlermeldung erhalten, dass Alex‘ Konto am Anmelden gehindert wurde. 
    
45. Wechseln Sie zurück zu **LON-CL1**. 

46. Auf **LON-CL1** sollten Sie in Ihrem Edge-Browser weiterhin bei **Microsoft 365** als Holly Dickson angemeldet sein. Die Liste **Aktive Benutzer** sollte im **Microsoft 365 Admin Center** noch von früher in dieser Aufgabe angezeigt werden. 

47. Nach weiteren Untersuchungen hat der CTO von Adatum festgestellt, dass Alex Wilbers Konto tatsächlich nicht kompromittiert wurde. Daher hat der CTO Holly gebeten, die Blockierung von Alex‘ Benutzerkonto zu entfernen. Wiederholen Sie die Schritte 33 bis 36, um die Blockierung seines Kontos aufzuheben. Beachten Sie, dass das Fenster **Anmeldung blockieren** aus Schritt 35 jetzt stattdessen **Anmeldungsblockierung aufheben** anzeigt.  <br/>

    Im Fenster **Anmeldungsblockierung aufheben** ist das Kontrollkästchen **Diesen Benutzer an der Anmeldung hindern** derzeit aktiviert. Deaktivieren Sie dieses Kontrollkästchen, und wählen Sie dann **Änderungen speichern** aus. <br/>
    
    **WICHTIG:** Es wird eine Warnmeldung angezeigt, dass es bis zu 15 Minuten dauern kann, bis Alex sich erneut anmelden kann. Angesichts der Zeiteinschränkungen bei der Schulung probieren Sie **NICHT** aus, ob Alex sich wieder anmelden kann. Wenn Sie möchten, können Sie versuchen, sich zu einem späteren Zeitpunkt als Alex anzumelden, wenn Sie Pause machen oder Zeit haben und es testen möchten. Bleiben Sie vorerst auf LON-CL1, und schließen Sie einfach das Fenster **Anmeldungsblockierung aufheben**.
    
48. Lassen Sie auf LON-CL1 Ihren Browser und alle Registerkarten geöffnet, und fahren Sie mit der nächsten Übung fort. 


# Ende von Lab 2

