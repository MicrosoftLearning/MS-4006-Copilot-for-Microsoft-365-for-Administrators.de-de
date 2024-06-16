## WWL-Mandanten – Nutzungsbedingungen

Wenn Ihnen im Rahmen einer Präsenzschulung ein Mandant zugewiesen worden ist, steht dieser für Praxislabs innerhalb der Präsenzschulung zur Verfügung. 

Mandanten sollten nicht für Zwecke außerhalb von Praxislabs freigegeben oder verwendet werden. Der in diesem Kurs verwendete Mandant ist ein Testmandant; er kann nach Abschluss des Kurses nicht verwendet oder erreicht werden und ist nicht für Erweiterungen geeignet. 

Mandanten dürfen nicht in ein kostenpflichtiges Abonnement konvertiert werden. Die im Rahmen dieses Kurses erworbenen Mandanten verbleiben im Eigentum der Microsoft Corporation, und wir behalten uns das Recht vor, jederzeit auf Mandanten zuzugreifen und diese zurückzuziehen. 

# Lernpfad 1 – Lab 1 – Übung 1 – Initialisieren Ihres Microsoft 365-Mandanten 

Adatum Corporation ist eine Tochtergesellschaft von Contoso Electronics. Adatum führt seine älteren Anwendungen (z. B. Microsoft Exchange Server 2019) in einer lokalen Bereitstellung aus. Kürzlich wurde jedoch Microsoft 365 abonniert, wodurch eine Hybridbereitstellung erstellt wird, in der die lokalen und Cloudbereitstellungen synchronisieren werden müssen. 

Als Microsoft 365-Administrator von Adatum wurden Sie mit der Bereitstellung von Microsoft 365 in der Hybridbereitstellung von Adatum mithilfe einer virtualisierten Lab-Umgebung beauftragt. In dieser Übung richten Sie den Microsoft 365-Testmandanten von Adatum ein, und Ihr Kursleiter zeigt Ihnen, wie Sie Ihre Microsoft 365-Anmeldeinformationen in Ihrer lab-gehosteten Umgebung abrufen. Sie verwenden diese Anmeldeinformationen in den restlichen Übungen in diesem Kurs. 

In Ihrer Laborumgebung hat Ihr Lab-Hostinganbieter bereits einen Microsoft 365-Testmandanten für Sie erhalten. Ihr Lab-Anbieter hat auch zwei Administratorkonten erstellt, die Sie in Ihrer VM-Lab-Umgebung verwenden werden: 

- Ein lokales Administratorkonto für die lokale Umgebung von Adatum (Adatum\Administrator).
- Ein Standardmäßiges Mandantenadministratorkonto in Microsoft 365 (der Anzeigename für dieses Benutzerkonto ist MOD-Administrator). 

Sie melden sich mit dem lokalen Adatum\Administratorkonto beim Client 1-PC (LON-CL1) an. Wenn Sie zum ersten Mal auf Microsoft 365 zugreifen, melden Sie sich zunächst mit dem Microsoft 365-Mandantenadministratorkonto (MOD-Administrator) an. Anschließend bereiten Sie den Microsoft 365-Mandanten von Adatum für die Microsoft Entra-ID und für spätere Labore mithilfe von Überwachungswarnungen und Microsoft Graph PowerShell vor.


### Aufgabe 1: Einrichten des Organisationsprofils von Adatum

In den Labs in diesem Kurs werden Sie Rollen spielen, indem Sie die Persona von Holly Dickson, der Microsoft 365-Administratorin von Adatum, übernehmen. In Ihrer Rolle als Holly wurden Sie beauftragt, das Profil des Unternehmens für den Microsoft 365-Testmandanten einzurichten. In dieser Aufgabe konfigurieren Sie die erforderlichen Optionen für den Mandanten von Adatum. Da Holly noch kein persönliches Microsoft 365-Benutzerkonto für sich selbst erstellt hat (Sie werden dies in der nächsten Übungsübung tun), wird Holly sich zunächst mit dem standardmäßigen Microsoft 365-Mandantenadministratorkonto und dem Kennwort bei Microsoft 365 anmelden, das von Ihrem Lab-Hostinganbieter erstellt wurde. Dieses Konto ist das **MOD-Administratorkonto**, dessen Alias "Administrator" ist. Der Benutzername für dieses Konto lautet **admin@xxxxxZZZZZZ.onmicrosoft.com** (wobei xxxxxZZZZZZ das Mandantenpräfix ist, das Ihrem Lab-Hostinganbieter zugewiesen wird). Der Anzeigename für dieses Konto ist MOD-Administrator.

1. Wenn Sie die Virtual Machine-Umgebung Ihres Lab-Hostinganbieters öffnen, müssen Sie mit der Client 1-VM (LON-CL1) beginnen. Wenn Ihre VM-Umgebung mit einem der anderen Computer (z. B. LON-DC1) geöffnet wird, wechseln Sie jetzt zu **LON-CL1**.

2. Melden Sie sich bei **LON-CL1** als lokales **Administratorkonto** an, das von Ihrem Lab-Hostinganbieter mit dem Kennwort **Pa55w.rd** erstellt wurde. 

3. Wählen Sie auf der Taskleiste unten auf dem Bildschirm das **Microsoft Edge-Symbol** aus. Maximieren Sie bei Bedarf das Browserfenster, wenn es geöffnet wird.

4. Wechseln Sie in Ihrem Edge-Browser zur **Microsoft 365-Startseite**, indem Sie die folgende URL in die Adressleiste eingeben: **https://portal.office.com**. 

5. Geben Sie im daraufhin angezeigten Dialogfeld **Anmelden** den von Ihrem Labhostinganbieter bereitgestellten **Administratorbenutzernamen** ein (dies ist das MOD-Administratorkonto). Der Benutzername sollte das Format **admin@xxxxxZZZZZZ.onmicrosoft.com** haben, wobei xxxxxZZZZZZ das Mandantenpräfix ist, das Ihrem Lab-Hostinganbieter zugewiesen ist. Wählen Sie **Weiter** aus. <br/>

    **Hinweis:** In den Labanweisungen, die in Ihrer VM-Labumgebung angezeigt werden, bietet Ihr Labhostinganbieter ggf. die Möglichkeit, neben Ressourcendaten wie Benutzernamen, Kennwörtern, PowerShell-Befehlen und anderen Daten, die während dieser Labs eingegeben werden müssen, eine Schaltfläche **Text eingeben** (oder eine entsprechende Schaltfläche) auszuwählen. Andere Lab-Hostinganbieter können eine alternative Methode bereitstellen, z. B. die Möglichkeit, diese Informationen zu kopieren und einzufügen. Nutzen Sie diese Funktionalität, damit Sie diese Informationen nicht manuell eingeben müssen. 

6. Geben Sie im Dialogfeld **Kennwort eingeben** das **Administratorkennwort** ein, das von Ihrem Labhostinganbieter bereitgestellt wurde, und wählen Sie dann **Anmelden** aus. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus.

7. Aktivieren Sie im Dialogfeld **Angemeldet bleiben?** das Kontrollkästchen **Nicht mehr anzeigen**, und wählen Sie dann **Ja** aus. Wählen Sie im daraufhin angezeigten Dialogfeld **Kennwort speichern** die Option **Nie** aus.

8. Wenn in der Mitte des Bildschirms das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, gibt es keine Möglichkeit, es zu schließen. Wählen Sie stattdessen rechts neben dem Fenster das Vorwärtspfeilsymbol (**>**) zweimal aus, und wählen Sie dann das Häkchensymbol aus, um durch die Folien in diesem Nachrichtenfenster zu navigieren. 

9. Wenn eines der Fenster **Weitere Apps suchen** oder **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** in der oberen Ecke der Fenster aus, um es zu schließen. 

10. Die Seite **Willkommen bei Microsoft 365** wird in Ihrem Edge-Browser auf der Registerkarte **Home | Microsoft 365** angezeigt. Dies ist die Microsoft 365-Startseite des MOD-Administrators. <br/>

    Beachten Sie das Symbol, das in der oberen rechten Ecke des Bildschirms angezeigt wird. Dieses Symbol stellt das **MOD-Administratorkonto** dar, bei dem es sich um das Mandantenadministratorkonto handelt, das von Ihrem Lab-Hostinganbieter erstellt wurde, als das Sie sich soeben angemeldet haben. Die anderen vorhandenen Microsoft 365-Benutzerkonten, die von Ihrem Lab-Hostinganbieter erstellt wurden, weisen ein Bild auf, das jedem ihrer Konten zugeordnet ist. Wenn Sie sich daher als Benutzer in späteren Labs anmelden, wird das Bild des Benutzers anstelle der Initialen des Benutzers angezeigt. Wenn einem Benutzer wie dem MOD-Administrator jedoch kein Bild zugewiesen ist, werden entweder die Initialen des Benutzers anstelle des Bilds angezeigt, oder wie in diesem Fall ein Symbol, das dem Konto zugewiesen wurde. <br/>

    Wählen Sie auf der Seite **Willkommen bei Microsoft 365** in der Liste der Anwendungssymbole, die im Navigationsbereich angezeigt werden, **Administrator** aus. Dadurch wird das **Microsoft 365 Admin Center** auf einer neuen Browserregisterkarte geöffnet. 

11. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Alle anzeigen** und dann **Einstellungen ** aus. Wählen Sie in der Gruppe **Einstellungen** die Option **Organisationseinstellungen** aus. 

12. Auf der Seite **Organisationseinstellungen** wird standardmäßig die Registerkarte **Dienste** angezeigt. Wählen Sie die Registerkarte **Organisationsprofil** aus.

13. Wählen Sie auf der Registerkarte **Organisationsprofil** die Option **Organisationsinformationen** aus der Liste der Profildaten aus.

14. Geben Sie im angezeigten Bereich **Organisationsinformationen** die folgenden Informationen ein: <br/>

    - Name: **Adatum Corporation** (Anmerkung: Adatum Corporation ist eine Tochtergesellschaft der Contoso Inc. Der Microsoft-Testmandant, den Ihr Lab-Hostinganbieter für dieses Lab erhalten hat, wurde möglicherweise ursprünglich Contoso zugewiesen. Wenn **Contoso** (oder ein anderer Wert) als Organisationsname angezeigt wird, ändern Sie ihn in **Adatum Corporation**.)

    - Postadresse: **Hauptstraße 555**

    - Ort: **Redmond**

    - Bundesland oder Kanton: **Washington**

    - Postleitzahl: **98052**

    - Telefon: Nicht ändern

    - Technischer Kontakt: Nicht ändern

    - Bevorzugte Sprache: **Englisch**

15. Wählen Sie **Speichern**.

16. Beachten Sie oben im Bereich **Organisationsinformationen** die Meldung, die angibt, dass die Änderungen gespeichert wurden. Wählen Sie das **X** in der oberen Ecke des Bereichs aus, um diesen zu schließen.

17. Bleiben Sie für die nächste Aufgabe bei **LON-CL1** angemeldet, mit Microsoft Edge im **Microsoft 365 Admin Center** geöffnet.

### Aufgabe 2: Erstellen eines benutzerdefinierten Designs für das Pilotprojektteam von Adatum

In der vorherigen Aufgabe haben Sie gelernt, dass das System, wenn jemand bei Microsoft 365 angemeldet ist, entweder sein Foto (sofern vorhanden) oder ihre Initialen anzeigt, wenn kein Foto bereitgestellt wird. Holly Dickson, die Microsoft 365-Administratorin von Adatum, ist nicht zufrieden mit dem Anzeigen eines Bilds oder einer Initiale des angemeldeten Benutzers. Sie möchte ein benutzerdefiniertes Design für die Mitglieder ihres Pilotprojektteams erstellen, damit auch der Name des angemeldeten Benutzers angezeigt wird. Wenn die Teammitglieder dieses Design bevorzugen, wird am Ende des Pilotprojekts dieselbe Option im Standarddesign konfiguriert, sodass sie für alle Benutzer gilt. 

Benutzerdefinierte Designs müssen einer oder mehreren Microsoft 365-Gruppen zugeordnet sein. Um diese Änderung zu implementieren, muss Holly zunächst eine Microsoft 365-Gruppe für die Mitglieder des Pilotprojektteams erstellen. Anschließend kann sie ein benutzerdefiniertes Design erstellen, das dieser Gruppe zugeordnet ist, mit dem die Einstellung den Namen des angemeldeten Benutzers anzeigen kann. In dieser Aufgabe erstellen Sie eine Microsoft 365-Gruppe für die Mitglieder des Microsoft 365-Pilotprojektteams von Adatum. Anschließend erstellen Sie ein benutzerdefiniertes Design, das den Namen des angemeldeten Benutzers anzeigt, und Sie weisen das Pilotprojektteam diesem Design zu. Sie werden auch andere Optionen überprüfen, die mit benutzerdefinierten Designs konfiguriert werden können, und Sie können beliebige Farbänderungen vornehmen.

**Wichtig:** Am Ende dieser Aufgabe versuchen Sie, das von Ihnen erstellte benutzerdefinierte Design zu speichern. Es gibt ein bekanntes Plattformproblem im Microsoft 365 Admin Center, bei dem es manchmal das benutzerdefinierte Design speichert, und in anderen Fällen wird aber eine Meldung zurückgegeben, die besagt: „Leider konnte Ihr Design nicht gespeichert werden. Versuchen Sie es später noch mal.“ Wenn Sie diese Nachricht erhalten, gibt es nichts, was Sie tun können, außer fortzufahren. Wenn Sie versuchen, das Design zu einem späteren Zeitpunkt zu speichern, wird normalerweise derselbe Fehler zurückgegeben. Dieses Problem wirkt sich nicht auf zukünftige Labs aus, abgesehen davon, dass der Namen des Benutzers nicht neben dem Benutzersymbol oder den Initialen in der Überschriftenzeile angezeigt wird. Trotz dieses bekannten Problems möchten wir, dass Sie mit dieser Aufgabe weitermachen, um Erfahrung beim Erstellen eines Designs zu sammeln, auch wenn es möglicherweise nicht in Ihrem Testmandanten gespeichert wird.

1. Sie sollten weiterhin bei LON-CL1 als lokales **Adatum\Administratorkonto** angemeldet sein, und in Ihrem Edge-Browser sollten Sie weiterhin bei Microsoft 365 als **MOD-Administrator** angemeldet sein. 

2. Wählen Sie im**Microsoft 365 Admin Center** **Teams & Gruppen** im Navigationsbereich aus, und wählen Sie dann darunter **Aktive Teams & Gruppen** aus. 

3. Auf der Seite **Aktive Teams und Gruppen** gibt es eine Registerkarte zum Anzeigen der einzelnen Gruppentypen. Die Registerkarte **Teams & Microsoft 365-Gruppen** wird standardmäßig angezeigt. Auf dieser Registerkarte werden die vorhandenen Microsoft 365-Gruppen angezeigt.  <br/>

    Wählen Sie die Option **+Microsoft 365-Gruppe hinzufügen** aus, die in der Menüleiste oberhalb der Liste der Teams- und Microsoft 365-Gruppen angezeigt wird. Dadurch wird der **Assistent zum Hinzufügen einer Microsoft 365-Gruppe** initiiert. 

4. Geben Sie im **Assistenten zum Hinzufügen einer Microsoft 365-Gruppe** auf der Seite **Grundlagen einrichten** **M365 Pilotprojekt** im Feld **Name** ein, und geben Sie dann **Mitglieder des Microsoft 365-Pilotprojektteams** im Feld **Beschreibung** ein (Hinweis: Auch wenn Sie keine Beschreibung eingeben, müssen Sie in dieses Feld klicken, um die Schaltfläche **Weiter** zu aktivieren). Wählen Sie **Weiter** aus.

5. Jetzt weisen Sie den MOD-Administrator als Besitzer der Gruppe **Pilotprojekt M365** zu. Wählen Sie im Fenster **Besitzer zuweisen**** +Besitzer** zuweisen aus.
    
6. Aktivieren Sie im daraufhin angezeigten Bereich **Besitzer zuweisen** das Kontrollkästchen neben **MOD-Administrator**, und wählen Sie dann unten im Bereich die Schaltfläche **(1) hinzufügen** aus.

7. Auf der Seite **Besitzer zuweisen** sollte der MOD-Administrator als Besitzer der Gruppe angezeigt werden. Wählen Sie **Weiter** aus.

8. Jetzt weisen Sie der Gruppe Pilotprojekt M365 Mitglieder zu. Wählen Sie auf der Seite **Mitglieder hinzufügen** **+Mitglieder hinzufügen** aus.

9. Aktivieren Sie im daraufhin angezeigten Bereich **Mitglieder hinzufügen** die Kontrollkästchen neben den folgenden Benutzern (in alphabetischer Reihenfolge): **Alex Wilber**, **Allan Deyoung**, **Diego Siciliani**, **Isaiah Langer**, **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**, **MOD Administrator**, **Nestor Wilke** und **Patti Fernandez**. Wählen Sie dann unten im Bereich die Schaltfläche **(10) hinzufügen** aus.

10. Überprüfen Sie auf der Seite **Mitglieder hinzufügen** diese 10 Benutzer als Mitglieder der Gruppe. Wenn Sie einen Benutzer verpasst haben, wählen Sie **+Mitglieder hinzufügen** aus, und fügen Sie dann den/die Benutzer hinzu, den/die Sie verpasst haben. Wenn alle 10 Benutzer auf dieser Seite angezeigt werden, wählen Sie **Weiter** aus.

11. Geben Sie auf der Seite **Einstellungen bearbeiten** die folgenden Informationen ein: <br/>

    - Geben Sie **m365pilotproject** in das Feld **E-Mail-Adresse der Gruppe** ein.
    - Wählen Sie im Feld **Datenschutz** die Option **Privat** aus.
    - Überprüfen Sie unter dem Abschnitt **Microsoft Teams zu Ihrer Gruppe hinzufügen**, ob das Kontrollkästchen **Team für diese Gruppe erstellen** aktiviert ist (wählen Sie es aus, wenn es leer ist), und wählen Sie dann **Weiter** aus.

12. Überprüfen Sie auf der Seite **Überprüfen und Beenden des Hinzufügens von Gruppen** den von Ihnen eingegebenen Inhalt. Wenn etwas korrigiert werden muss, wählen Sie **Bearbeiten** unter dem spezifischen Bereich aus, der Anpassung benötigt, nehmen Sie alle erforderlichen Korrekturen vor, und wählen Sie dann **Weiter** aus, um mit dieser Seite fortzufahren. Sobald alles korrekt ist, wählen Sie **Gruppe erstellen** aus.

13. Sobald das Fenster **Gruppe Pilotprojekt M365 erstellt** angezeigt wird, beachten Sie den Kommentar oben auf der Seite, dass es 5 Minuten dauern kann, bis die neue Gruppe in der Liste der aktiven Gruppen angezeigt wird.  </br>

    Wählen Sie **Schließen** aus. Dadurch gelangen Sie zur Seite **Aktive Teams und Gruppen**, auf der die Registerkarte **Teams & Microsoft 365-Gruppen** angezeigt werden soll. Da die Gruppe Pilotprojekt M365 eine Microsoft 365-Gruppe war, sollte sie schließlich auf dieser Registerkarte angezeigt werden. Wählen Sie bei Bedarf die Option **Aktualisieren** auf der Menüleiste aus, bis die Gruppe Pilotprojekt M365 in der Liste der Teams- und Microsoft 365-Gruppen angezeigt wird.

14. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Einstellungen** und dann **Organisationseinstellungen** aus. 

15. Auf der Seite **Organisationseinstellungen** wird standardmäßig die Registerkarte **Dienste** angezeigt. Wählen Sie die Registerkarte **Organisationsprofil** aus.

16. Auf der Registerkarte **Organisationsprofil** wird die Liste der Organisationsprofildaten angezeigt. Wählen Sie in der Liste der Daten **Benutzerdefinierte Designs** aus.

17. Im nun angezeigten Bereich **Microsoft 365 für Ihre Organisation anpassen** können Sie das Standarddesign anpassen, das Benutzern angezeigt wird, wenn sie bei Microsoft 365 angemeldet sind, und Sie können zusätzliche benutzerdefinierte Designs hinzufügen. Sie möchten ein neues benutzerdefiniertes Design erstellen, das nur für die Mitglieder der Gruppe **M365-Pilotprojekt** gilt, die Sie zuvor erstellt haben. Wählen Sie daher die Option **+ Design hinzufügen** aus.

18. Im angezeigten Bereich **Neues Gruppendesign** wird standardmäßig die Registerkarte **Allgemein** angezeigt. Geben Sie das **Pilotprojektdesign "M365"** im Feld **Name** ein.

19. Wählen Sie innerhalb des Felds **Gruppen** aus. Wählen Sie in der liste der angezeigten Gruppen das **Pilotprojekt M365** aus, wenn es in der Liste der Gruppen angezeigt wird. <br/>

    **Hinweis:** Wenn das **M365-Pilotprojekt** nicht in der Liste der Gruppen angezeigt wird, geben Sie **M365** in das Feld **Gruppen** ein. Ein Suchergebnisfeld sollte angezeigt werden, in dem die Gruppe **Pilotprojekt M365** angezeigt wird. Wählen Sie das **Pilotprojekt M365** aus. 

20. Aktivieren Sie das Kontrollkästchen **Anzeigename des Benutzers anzeigen**. Dies ist die Einstellung, die Holly für die Mitglieder des Pilotprojektteams M365 anpassen möchte. Diese Option zeigt den Namen des angemeldeten Benutzers neben den Initialen in jeder Fensterüberschrift an.
 
21. Wählen Sie die Registerkarte **Logos** aus, und nehmen Sie sich etwas Zeit, um sich die Optionen anzusehen. Gehen Sie für die Registerkarte **Farben** genauso vor. Beachten Sie die verschiedenen Design- und Brandingoptionen, die sie ändern können. <br/>

    Für dieses Lab können Sie eine der Optionen ändern oder die Standardwerte belassen. Beispielsweise können Sie in Ihrer realen Umgebung das Logo Ihres Unternehmens hinzufügen und das Hintergrundbild als Standard für alle Ihre Benutzer festlegen. In diesem Lab können Sie die Farben für den Navigationsbereich, die Textfarbe, die Symbolfarbe und die Akzentfarbe ändern. <br/>

    **Sehen Sie sich die verschiedenen Optionen für dieses Design an, das von den Mitgliedern des Microsoft 365-Pilotprojektteams verwendet wird. Nehmen Sie alle gewünschten Änderungen vor.** <br/>

    **Tipp:** Einige Farbmuster lenken Benutzer ab. Wenn Sie eine der Farben ändern, empfiehlt es sich, die Verwendung von Farben mit hohem Kontrast zu vermeiden, z. B. Neonfarben und hochauflösende Farben wie helles Rosa und Weiß.

22. Wählen Sie **Speichern**. 

    **Hinweis:** Wie bereits zu Beginn dieser Aufgabe erwähnt, gibt es ein bekanntes Plattformproblem im Microsoft 365 Admin Center, bei dem ein neues benutzerdefiniertes Design manchmal gespeichert und in anderen Fällen die folgende Meldung angezeigt wird: „Leider konnte Ihr Design nicht gespeichert werden. Versuchen Sie es später noch mal.“ Wenn Sie diese Nachricht erhalten, wirkt sich dies nicht auf zukünftige Labs aus. Da Ihr benutzerdefiniertes Design nicht gespeichert wurde, zeigt das System lediglich nicht den Namen des Benutzers neben dem Benutzersymbol oder den Initialen in der Überschriftenzeile an, und eventuell vorgenommene Farbänderungen werden nicht reflektiert. Wir haben Sie gebeten, diese Aufgabe trotzdem zu erledigen, auch wenn Sie diese Nachricht erhalten können, um Erfahrung beim Erstellen eines Designs wie diesem zu sammeln. Wenn Sie also diesen Fehler erhalten, überspringen Sie den nächsten Schritt, der das benutzerdefinierte Design testet. Sie können jedoch trotzdem die verbleibenden Schritte ausführen, die den nächsten Schritt ausführen, um mehr über das Standarddesign zu erfahren. Ob Ihr benutzerdefiniertes Design gespeichert wurde oder nicht: Schließen Sie den Bereich **Design für M365-Pilotprojekt**.

23. Wenn Ihr benutzerdefiniertes Design nicht gespeichert wurde, fahren Sie mit dem nächsten Schritt fort. Wenn Ihr benutzerdefiniertes Design jedoch gespeichert wurde, wählen Sie oben auf der Adressleiste das Symbol **Aktualisieren** aus. Beachten Sie nach dem Aktualisieren des Bildschirms, dass der Name von **MOD-Administrator** links neben dem Kreis mit den MA-Initialen oder dem Symbol angezeigt wird, das für dieses Konto von Ihrem Labhostinganbieter ausgewählt wurde. Wenn sich Mitglieder des Microsoft 365-Pilotprojektteams bei Microsoft 365 anmelden, zeigt dieses benutzerdefinierte Design ihren Benutzernamen an, genau wie hier der Name des MOD-Administrators angezeigt wird. 

24. Wählen Sie in der Liste der Organisationsprofildaten **Benutzerdefinierte Designs** aus.

25. Beachten Sie im angezeigten Bereich **Microsoft 365 für Ihre Organisation anpassen**, wie es das **Standarddesign** und das **Design von Pilotprojekt M365** anzeigt (sofern dieses im vorherigen Schritt gespeichert wurde). Wählen Sie das **Standarddesign** aus. 

26. Beachten Sie im **Standarddesignbereich**, wie die Option **Anzeigename des Benutzers anzeigen** für das Standarddesign nicht ausgewählt ist. Wenn Holly später entscheidet, die Option **Anzeigename des Benutzers anzeigen** als dauerhaftes Feature anzuzeigen, wählt sie diese Option im **Standarddesignbereich** aus, sodass sie für alle Adatum-Benutzer gilt, und sie löscht das **Design von Pilotprojekt M365**. <br/>

    **Hinweis:** Wenn die Fehlermeldung „Leider konnte Ihr Design nicht gespeichert werden. Versuchen Sie es später noch mal.“ angezeigt wurde, als Sie zuvor versucht haben, Ihr benutzerdefiniertes Design zu speichern, wählen Sie die Option **Anzeigename des Benutzers anzeigen** im Standarddesign und dann **Speichern** aus. Wir möchten sehen, was passiert, wenn diese Option ausgewählt ist, auch wenn Sie Ihr benutzerdefiniertes Design nicht speichern konnten. Wenn Sie diese Option für das Standarddesign festlegen, wählen Sie oben auf der Adressleiste das Symbol **Aktualisieren** aus. Beachten Sie nach dem Aktualisieren des Bildschirms, dass der Name von **MOD-Administrator** links neben dem Kreis mit den MA-Initialen oder dem Symbol angezeigt wird, das für dieses Konto von Ihrem Labhostinganbieter ausgewählt wurde.
 
27. Schließen Sie den Bereich **Standarddesign**.

28. Bleiben Sie für die nächste Aufgabe bei **LON-CL1** angemeldet, mit Microsoft Edge im **Microsoft 365 Admin Center** geöffnet.

### Aufgabe 3: Installieren von Microsoft Graph PowerShell 

Microsoft Graph PowerShell ist erforderlich, um beim Installieren von Microsoft 365 mehrere Konfigurationsaufgaben auszuführen. Da zukünftige Übungsübungen mehrere dieser Aufgaben mit Windows PowerShell ausführen, sollten Sie zunächst das Microsoft Graph PowerShell-Modul installieren. Mit diesem Modul können Sie viele der Microsoft 365-Benutzer- und Organisationsverwaltungsaufgaben über PowerShell ausführen. Es eignet sich hervorragend für Massenaufgaben wie Kennwortzurücksetzungen, Kennwortrichtlinien, Lizenzverwaltung und Berichterstellung usw.  

1. Bei LON-CL1 sollten Sie weiterhin als lokales **Adatum\Administratorkonto** angemeldet sein. Zum Installieren von Microsoft Graph PowerShell müssen Sie eine Instanz mit erhöhten Rechten von **Windows PowerShell** öffnen. Geben Sie **Power** in das Suchfeld ein, das in der unteren linken Ecke der Taskleiste angezeigt wird. Klicken Sie in der Liste der Suchergebnisse mit der rechten Maustaste auf **Windows PowerShell** (Windows PowerShell ISE nicht auswählen), und wählen Sie **Als Administrator ausführen** im daraufhin angezeigten Dropdownmenü aus. 

2. Schließen Sie das PowerShell-Fenster. Geben Sie in **Windows PowerShell** den folgenden Befehl an der Eingabeaufforderung ein, um das Microsoft Graph PowerShell-Modul aus dem PowerShell-Katalog zu installieren, und drücken Sie dann die Eingabetaste: <br/>

        Install-Module Microsoft.Graph -Scope CurrentUser

3. Sie werden aufgefordert zu bestätigen, ob Sie das Modul aus einem nicht vertrauenswürdigen Repository (PSGallery) installieren möchten. Geben Sie **A** ein, um **[A] Ja für alle** auszuwählen, und drücken Sie dann die Eingabetaste.  <br/>

    **Hinweis:** Ihre Antwort initiiert die Installation aller Microsoft Graph-Untermodule. Nachdem alle Installationsmeldungen für jedes Untermodul die Anzeige abgeschlossen haben, dauert es bis zu 5 bis 10 zusätzliche Minuten, bis die Microsoft Graph PowerShell-Installation abgeschlossen ist. Während dieser Zeit blinkt der Cursor weiterhin unter der Nachricht des nicht vertrauenswürdigen Repositorys. <br/>

    **Dies kann ein guter Moment sein, um eine kurze Pause zu nehmen.**

4. Nach der Installation von Microsoft Graph PowerShell wird eine Eingabeaufforderung angezeigt. Nun wird die Liste der installierten Untermodule angezeigt. Führen Sie hierzu den folgenden Befehl aus:

        Get-InstalledModule Microsoft.Graph.* | select *name*

5. Überprüfen Sie, ob die Liste der installierten Untermodule die folgenden drei Untermodule enthält, die in späteren Lab-Übungen verwendet werden: 

    - Microsoft.Graph.Groups
    - Microsoft.Graph.Identity.DirectoryManagement
    - Microsoft.Graph.Users
    
    Wenn alle drei Untermodule in der Liste der installierten Untermodule angezeigt werden, fahren Sie mit dem nächsten Schritt fort. Wenn jedoch eines dieser drei Untermodule nicht in der Liste angezeigt wird, führen Sie den folgenden PowerShell-Befehl aus, um das fehlende Untermodul manuell zu installieren:

        Install-Module -Name <module name> -Scope CurrentUser

    Wenn das Modul "Microsoft.Graph.Identity.DirectoryManagement" beispielsweise nicht installiert wurde, führen Sie den folgenden Befehl aus:

        Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement

6. Die Ausführungsrichtlinieneinstellungen von PowerShell bestimmen, welche PowerShell-Skripts auf einem Windows-System ausgeführt werden können. Wenn Sie diese Richtlinie auf **Uneingeschränkt** festlegen, kann Holly alle Konfigurationsdateien laden und alle Skripts ausführen. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein und drücken Sie dann die EINGABETASTE:   <br/>

        Set-ExecutionPolicy unrestricted

    Wenn Sie aufgefordert werden, zu überprüfen, ob Sie die Ausführungsrichtlinie ändern möchten, geben Sie **A** ein, um **[A] Ja für alle** auszuwählen. 

7. Lassen Sie Ihr PowerShell-Fenster geöffnet, minimieren Sie es jedoch. Sie werden es in einer späteren Lab-Übung verwenden.


**Herzlichen Glückwunsch! Sie haben alle Schritte zum Initialisieren Ihres Lab-Mandanten abgeschlossen. Sie sind jetzt bereit, die verbleibenden Lab-Übungen durchzuführen.**

# Ende von Lab 1
