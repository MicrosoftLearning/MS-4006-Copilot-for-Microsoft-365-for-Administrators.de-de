# Lernpfad 2, Lab 2, Übung 1: Verwalten des sicheren Benutzerzugriffs 

Organisationen müssen sicherstellen, dass der Zugriff auf ihre Unternehmensdaten in Microsoft 365 immer geschützt ist. Microsoft 365 – und daher auch Copilot für Microsoft 365 – zeigt häufig vertrauliche Daten an, einschließlich E-Mails, Dokumente, Kundeninformationen und geistiges Eigentum. Unbefugter Zugriff auf Microsoft 365 kann zu Datenschutzverletzungen, Identitätsdiebstahl und anderen schädlichen Aktivitäten führen. Durch das Absichern des Benutzerzugriffs können Organisationen verhindern, dass nicht autorisierte Personen auf Unternehmensdaten zugreifen und möglicherweise Unternehmensdaten missbrauchen oder offenlegen, wenn Sie in Microsoft 365 und Copilot for Microsoft 365 arbeiten.

In der folgenden Labübung nehmen Sie die Rolle von Holly Dickson ein, der neuen Microsoft 365-Administratorin von Adatum. Sie verwenden mehrere Benutzerverwaltungsfunktionen, um Adatum auf die bevorstehende Copilot for Microsoft 365-Bereitstellung vorzubereiten. Sie beginnen mit dem Erstellen eines Microsoft 365-Benutzerkontos für Holly, der die Microsoft 365-Rolle „Globaler Administrator“ zugewiesen wird. 

**Hinweis:** Die von Ihrem Labhostinganbieter bereitgestellte VM-Umgebung beinhaltet über 20 bestehende Microsoft 365-Benutzerkonten sowie eine große Anzahl bestehender lokaler Benutzerkonten. In diesem Kurs werden mehrere der bestehenden Microsoft 365-Benutzerkonten verwendet. Obwohl das MOD-Administratorkonto von Ihrem Labhostinganbieter erstellt wurde, erstellen Sie Holly Dicksons Benutzerkonto, da eine bewährte Methode darin besteht, die Microsoft 365-Rolle „Globaler Administrator“ mehr als einem Benutzer zuzuweisen. Dabei lernen Sie auch, ein Microsoft 365-Benutzerkonto zu erstellen, falls Sie mit dem Prozess nicht vertraut sind.

Holly wurde dann vom CTO von Adatum aufgefordert, die Multi-Faktor-Authentifizierung (MFA) und Smart Lock von Microsoft Entra bereitzustellen. Diese Features tragen zur Verbesserung der Kennwortverwaltung in der gesamten Organisation bei, was der Vorbereitung auf Copilot for Microsoft 365 dient. Für Smart Lockout stellen Sie sie mithilfe der Gruppenrichtlinienverwaltung bereit. 


### Aufgabe 1: Erstellen eines Benutzerkontos für die Microsoft 365-Administratorin von Adatum

Holly Dickson ist die neue Microsoft 365-Administratorin von Adatum. Da noch kein Microsoft 365-Benutzerkonto für sie eingerichtet wurde, hat sie sich im vorherigen Lab zunächst mit dem MOD-Administratorkonto (der standardmäßige globale Administrator) bei Microsoft 365 angemeldet. In dieser Aufgabe bleiben Sie weiterhin als MOD-Administrator angemeldet, wo Sie ein Microsoft 365-Benutzerkonto für Holly erstellen. Außerdem weisen Sie die dem Konto von Holly die Microsoft 365-Rolle „Globaler Administrator“ zu. Diese Rolle erteilt Holly die erforderlichen Berechtigungen, um alle administrativen Funktionen in Microsoft 365 auszuüben. Nach dieser Aufgabe melden Sie sich mit dem neuen Konto von Holly an, und Sie absolvieren alle verbleibenden Labs mit Hollys Persona. 

**Lizenzhinweis:** Vor dem Erstellen des Hollys Kontos überprüfen Sie zuerst die Anzahl der verfügbaren Lizenzen. Dabei werden Sie feststellen, dass Ihr Labmandant zwar 20 Microsoft 365 E5-Lizenzen (ohne Teams) und 20 Microsoft Teams Enterprise-Lizenzen bereitstellt, aber alle diese Lizenzen bereits den Benutzerkonten zugewiesen wurden, die von Ihrem Labhostinganbieter erstellt wurden. Daher müssen Sie zuerst eine Lizenz jeder Sorte von einem anderen Benutzer entziehen, damit Sie sie Holly zuweisen können.

**Wichtig:** Als bewährte Methode in Ihrer realen Bereitstellung sollten Sie immer die Anmeldeinformationen des ersten globalen Administratorkontos notieren. In diesem Lab ist es das MOD-Administratorkonto, dessen Benutzername admin@xxxxxZZZZZZ.onmicrosoft.com ist. Hierbei ist xxxxxZZZZZZ das Mandantenpräfix, das Ihrem Labhostinganbieter zugewiesen ist. Sie sollten diese Kontoinformationen aus Sicherheitsgründen gut geschützt aufbewahren. **Dieses Konto sollte eine nicht personalisierte Identität** sein, die über die höchsten Berechtigungen verfügt, die in einem Mandanten möglich sind. Die MFA sollte **nicht** aktiviert werden, da sie nicht personalisiert ist. Da der Benutzername und das Kennwort für dieses erste globale Administratorkonto in der Regel von mehreren Benutzern gemeinsam verwendet werden, ist dieses Konto ein perfektes Ziel für Angriffe. Daher wird immer empfohlen, dass Organisationen personalisierte Dienstadministratorkonten (z. B. einen Exchange-Administrator, SharePoint-Administrator usw.) erstellen und so wenige persönliche globale Administratoren wie möglich haben. Die persönlichen globalen Administratoren, die Sie in Ihrer realen Bereitstellung erstellen, sollten jeweils einem einzelnen Benutzer (z. B. Holly Dickson) zugeordnet werden, und für jedes sollte die Multi-Faktor-Authentifizierung (MFA) von Microsoft Entra erzwungen werden.

1. Auf der VM **LON-CL1** sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Labübung noch geöffnet sein. Sie sollten bei Microsoft 365 als **MOD-Administrator** angemeldet sein. 

2. Da Sie einen neuen Benutzer hinzufügen, sollten Sie zunächst die Lizenzverfügbarkeit überprüfen, bevor Sie das Benutzerkonto hinzufügen. Wählen Sie im **Microsoft 365 Admin Center**-Navigationsbereich **Abrechnung** aus, um die Abrechnungsgruppe zu erweitern, und wählen Sie dann **Lizenzen** aus. 

3. Auf der Seite **Lizenzen** wird standardmäßig die Registerkarte **Abonnements** angezeigt. Beachten Sie in der Liste der Abonnements, dass Microsoft **365 E5 (ohne Teams)** und **Microsoft Teams Enterprise-Abonnements** keine verfügbaren Lizenzen haben. Ihr Labmandant stellt 20 Lizenzen für jedes Abonnement bereit, aber alle 40 Lizenzen wurden zugewiesen. Da Sie Holly sowohl eine **Microsoft 365 E5 (ohne Teams)**-Lizenz als auch eine **Microsoft Teams Enterprise**-Lizenz zuweisen müssen, müssen Sie die Lizenzen zunächst einem anderen Benutzerkonto entziehen, um sie für Holly verfügbar zu machen. 

4. Wählen Sie im **Microsoft 365 Admin Center**-Navigationsbereich **Benutzer** und dann **Aktive Benutzer** aus. In der Liste **Aktive Benutzer** wird die Liste der vorhandenen Benutzerkonten angezeigt, die von Ihrem Labhostinganbieter erstellt wurden. Da Christie Cline in eine neue Rolle im Unternehmen annimmt und nicht mehr Teil des Microsoft 365-Pilotprojekts ist, entziehen Sie ihrem Konto die **Microsoft 365 E5 (ohne Teams)**- und **Microsoft Teams Enterprise**-Lizenzen, damit Sie sie dem neuen Konto von Holly Dickson zuweisen können.

5. Wählen Sie auf der Seite **Aktive Benutzer** in der Liste der Benutzer **Christie Cline** aus. Wählen Sie Christies verlinkten Namen und nicht das Kontrollkästchen neben ihrem Namen aus.

6. Im erscheinenden Bereich **Christie Cline** wird standardmäßig die Registerkarte **Konto** angezeigt. Wählen Sie die Registerkarte **Lizenzen und Apps** aus. Aktivieren Sie unter **Lizenzen (2)** die Kontrollkästchen neben **Microsoft 365 E5 (ohne Teams)** und **Microsoft Teams Enterprise**, um sie zu löschen, und wählen Sie dann **Änderungen **speichern aus. Nachdem die Änderungen gespeichert wurden, schließen Sie den Bereich **Christie Cline**. 

7. Sie können jetzt ein Benutzerkonto für Holly Dickson erstellen, die die neue Microsoft 365-Administratorin von Adatum ist. Dabei weisen Sie Holly die Microsoft 365-Rolle „Globaler Administrator“ zu, die ihr globalen Zugriff auf die meisten Verwaltungsfeatures und -daten in Microsoft-Onlinediensten gewährt. Außerdem weisen Sie Holly die beiden Lizenzen zu, die Sie Christie Cline gerade entzogen haben. <br/>

    Wählen Sie im Fenster **Aktive Benutzer** die Option **Benutzer hinzufügen** aus, die in der Menüleiste oberhalb der Liste der aktiven Benutzer angezeigt wird. Dadurch wird der Assistent **Benutzer hinzufügen** gestartet.

8. Geben Sie auf der **Grundeinstellungen** des Assistenten **Benutzer hinzufügen** die folgenden Informationen ein:

    - Vorname: **Holly**

    - Nachname: **Dickson** 

    - Anzeigename: Wenn Sie per TAB-TASTE in dieses Feld wechseln, wird **Holly Dickson** angezeigt.

    - Benutzername: **Holly** <br/>
    
        ‎**WICHTIG:** Rechts neben dem Feld **Benutzername** ist das Feld „Domäne“. Es wird mit der Clouddomäne **xxxxxZZZZZZ.onmicrosoft.com** vorab ausgefüllt, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist.<br/>
    
    - Deaktivieren Sie das Kontrollkästchen **Kennwort automatisch erstellen**, wodurch ein neues Feld für die Eingabe eines vom Administrator definierten Kennworts angezeigt wird.

    - Geben Sie das neue administrative Kennwort in das Feld **Kennwort** ein, das angezeigt wird 

    - Deaktivieren Sie das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern**. 

9. Wählen Sie **Weiter** aus. Wenn das Dialogfeld **Kennwort speichern** oben auf dem Bildschirm angezeigt wird, wählen Sie **Nie** aus.

10. Geben Sie auf der Seite **Produktlizenzen zuweisen** die folgenden Informationen ein: <br/>

    - Standort: **USA**

    - Lizenzen: Aktivieren Sie unter der Option **Benutzer eine Produktlizenz zuweisen** die Kontrollkästchen **Microsoft 365 E5" (kein Teams)** und **"Microsoft Teams Enterprise"**.

11. Wählen Sie **Weiter** aus.

12. Wählen Sie auf der Seite **Optionale Einstellungen** den Dropdownpfeil rechts neben **Rollen** aus. 

13. Wählen Sie im Abschnitt **Rollen** die Option **Admin Center-Zugriff** aus. Wenn Sie diese Option auswählen, werden die am häufigsten verwendeten Microsoft 365-Administratorrollen darunter aktiviert.  <br/>

    **Hinweis:** Alle Administratorrollen werden angezeigt, wenn Sie **Alle nach Kategorie anzeigen** auswählen, was nach der letzten häufigen Rolle angezeigt wird. Für Holly müssen Sie nicht alle Administratorrollen nach Kategorie anzeigen, da Holly die Rolle „Globaler Administrator“ zugewiesen wird, die in der Liste der häufig verwendeten Rollen angezeigt wird.

14. Aktivieren Sie das Kontrollkästchen **Globaler Administrator**. <br/>

    **Hinweis:** Es wird eine Warnmeldung angezeigt, dass Adatum bereits über sieben globale Administratoren verfügt. In einer normalen Umgebung wäre das zu viel und wird nicht empfohlen. Für dieses Lab hat der Labhostinganbieter dem MOD-Administrator und sechs anderen Benutzerkonten die Rolle „Globaler Administrator“ zugewiesen, was in einer realen Bereitstellung normalerweise nicht der Fall wäre. Im Rahmen dieses Labs in Ihrer fiktiven Adatum-Labumgebung ignorieren Sie diese Meldung jedoch. **Gemäß den Best Practices sollten Sie zwei bis vier globale Administratoren in einer echten Microsoft 365-Bereitstellung haben.** 

15. Wählen Sie **Weiter** aus.

16. Überprüfen Sie im Fenster **Überprüfen und fertigstellen** Ihre Auswahl. Wenn etwas geändert werden muss, wählen Sie den entsprechenden Link **Bearbeiten** aus, und nehmen Sie die erforderlichen Änderungen vor. Wenn alles korrekt ist, wählen Sie andernfalls **Hinzufügen fertig stellen** aus. 

17. Wählen Sie auf der Seite **Holly Dickson zu aktiven Benutzern hinzugefügt** im Abschnitt **Benutzerdetails** die Option **Anzeigen** aus, um zu überprüfen, ob das Kennwort von Holly mit dem vom Labhostinganbieter bereitgestellten **Administratorkennwort** für das Mandantenadministratorkonto (d. h. das MOD-Administratorkonto) übereinstimmt.  <br/>

    **Hinweis:** Wenn Sie versehentlich ein anderes Kennwort eingegeben haben, müssen Sie nach der Rückkehr zur Seite **Aktive Benutzer** das Symbol zum **Zurücksetzen eines Kennworts** auswählen (das Schlüsselsymbol, das angezeigt wird, wenn Sie auf Hollys Konto zeigen), um ihr Kennwort in den richtigen Wert zu ändern.

18. Wählen Sie **Schließen** aus.

19. Bleiben Sie bei der Client-VM 1 (LON-CL1) angemeldet, und lassen Sie das Microsoft 365 Admin Center in Ihrem Browser für die nächste Aufgabe geöffnet.


### Aufgabe 2 – Aktualisieren der Microsoft 365-Pilotprojektgruppe

Nach Abschluss der vorherigen Aufgabe sollten Sie beim **Microsoft 365 Admin Center** weiterhin mit dem Konto **MOD-Administrator** angemeldet sein. In dieser Aufgabe beginnen Sie mit der Implementierung des Microsoft 365-Pilotprojekts von Adatum als Holly Dickson, der neuen Microsoft 365-Administratorin von Adatum. Daher beginnen Sie diese Aufgabe, indem Sie sich bei Microsoft 365 als MOD-Administrator abmelden und sich wieder als Holly anmelden. 

In einer vorherigen Aufgabe haben Sie eine Microsoft 365-Gruppe für die Mitglieder des Pilotprojektteams von Adatum erstellt, sodass Sie ein benutzerdefiniertes Design für diese Gruppe erstellen können. In dieser Aufgabe fügen Sie Holly zu dieser Gruppe hinzu. 

1. Auf der VM LON-CL1 sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Aufgabe noch geöffnet sein. Sie sollten bei Microsoft 365 als **MOD-Administrator** angemeldet sein. <br/>

    Beachten Sie auf der Registerkarte **Microsoft 365 Admin Center** in der oberen rechten Ecke des Bildschirms, dass der Name des MOD-Administrators und ein Megafonsymbol angezeigt werden. Der Name wird aufgrund des benutzerdefinierten Designs angezeigt, das Sie in der vorherigen Labübung erstellt haben, die einer Gruppe von Microsoft 365-Pilotprojektbenutzern zugeordnet war, zu denen auch der MOD-Administrator gehörte. Bedenken Sie das, sobald Sie sich wieder als Holly Dickson anmelden. <br/>

    Wählen Sie das Benutzersymbol oder den Kreis mit den Initialen "MA" für den **MOD-Administrator** in der oberen rechten Ecke Ihres Browsers aus. Wählen Sie im angezeigten Fenster **MOD-Administrator** die Option **Abmelden** aus. <br/>
    
    **Wichtig:** Wenn Sie sich von einem Benutzerkonto abmelden und sich bei einem anderen anmelden, sollten Sie alle Browserregisterkarten mit Ausnahme der Registerkarte **Abmelden** schließen. Diese bewährte Methode hilft, Verwirrung zu vermeiden, indem die Fenster geschlossen werden, die dem vorherigen Benutzer zugeordnet sind. Nachdem Sie sich vom MOD-Administratorkonto abgemeldet haben, nehmen Sie sich einen Moment Zeit, um alle anderen Browserregisterkarten zu schließen, mit Ausnahme der Registerkarte **Abmelden**. 
    
2. Geben Sie in Ihrem Microsoft Edge-Browser auf der Registerkarte **Abmelden** die folgende URL in die Adressleiste ein, um sich wieder bei Microsoft 365 anzumelden: **https://portal.office.com**. 

3. Wählen Sie im Fenster **Konto auswählen** nur das Mandantenadministratorkonto des MOD-Administrators (das admin@xxxxxZZZZZZ.onmicrosoft.com-Konto) aus, von dem Sie sich gerade abgemeldet haben. Wählen Sie **Anderes Konto verwenden** aus. 

4. Geben Sie im Fenster **Anmelden** **Holly@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist. Wählen Sie **Weiter** aus.

5. Geben Sie im Fenster **Kennwort eingeben** das neue Administratorkennwort ein, das Sie dem Konto von Holly zugewiesen haben, und wählen Sie dann **Anmelden** aus. 

6. Wenn das Dialogfeld **Angemeldet bleiben?** angezeigt wird, aktivieren Sie das Kontrollkästchen **Nicht mehr anzeigen**, und wählen Sie dann **Ja** aus. 

7. Wenn in der Mitte des Bildschirms das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, gibt es keine Möglichkeit, es zu schließen. Wählen Sie stattdessen rechts neben dem Fenster das Vorwärtspfeilsymbol (**>**) zweimal aus, und wählen Sie dann das Häkchensymbol aus, um durch die Folien in diesem Nachrichtenfenster zu navigieren. 

8. Wenn das Fenster **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** in der oberen Ecke des Fensters aus, um es zu schließen. 

9. Die Seite **Willkommen bei Microsoft 365** wird in Ihrem Edge-Browser auf der Registerkarte **Startseite | Microsoft 365** angezeigt. Das ist die Microsoft 365-Willkommensseite von Holly. Sie sehen, dass Hollys Initialen in der oberen rechten Ecke des Bildschirms angezeigt werden, ihr Name jedoch nicht. Das liegt daran, dass Hollys Konto zu dem Zeitpunkt, als Sie die Microsoft 365-Pilotprojektbenutzer zur Gruppe hinzugefügt haben, die dem benutzerdefinierten Design in der vorherigen Labübung zugeordnet war, nicht vorhanden war. Da Holly ihren Namen oben in jedem Microsoft 365-Fenster sehen möchte, wenn sie beim System angemeldet ist, möchte sie zuerst ihr Konto zur Gruppe der Microsoft 365-Pilotprojektbenutzer hinzufügen. <br>

    Wählen Sie in der Spalte der Anwendungssymbole, die im Navigationsbereich an der Seite des Bildschirms angezeigt werden, **Administrator** aus. Dadurch wird das **Microsoft 365 Admin Center** auf einer neuen Browserregisterkarte geöffnet. 

10. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Teams und Gruppen** und dann **Aktive Teams und Gruppen** aus. 

11. Auf der Seite **Aktive Teams und Gruppen** gibt es eine Registerkarte zum Anzeigen der einzelnen Gruppentypen. Die Registerkarte **Teams- und Microsoft 365-Gruppen** wird standardmäßig angezeigt. Wählen Sie auf dieser Registerkarte **M365 pilot project** aus.

12. Im angezeigten Bereich **M365 pilot project** wird standardmäßig die Registerkarte **Allgemein** angezeigt. Wählen Sie die Registerkarte **Mitgliedschaft** aus.

13. Auf der Registerkarte **Mitgliedschaft** wird die Unterregisterkarte **Besitzer** standardmäßig im Navigationsbereich angezeigt, der sich an der Seite des Bereichs befindet. Wählen Sie die Unterregisterkarte **Mitglieder** aus, die darunter angezeigt wird.

14. Wählen Sie auf der Unterregisterkarte **Mitglieder** die Option **+ Mitglieder hinzufügen** aus.

15. Wählen Sie im daraufhin angezeigten Bereich **Gruppenmitglieder zu M365 pilot project hinzufügen** das Feld **Nach Name oder E-Mail-Adresse suchen** aus. Scrollen Sie in der angezeigten Benutzerliste nach unten, und wählen Sie **Holly Dickson** aus. Wählen Sie die Schaltfläche **Hinzufügen (1)** aus, und schließen Sie dann den Bereich **Gruppenmitglieder zu M365 pilot project hinzufügen**, nachdem Holly der Gruppe hinzugefügt wurde.

16. Bleiben Sie bei LON-CL1 angemeldet, und öffnen Sie das **Microsoft 365 Admin Center** in Ihrem Browser für die nächste Aufgabe.


### Aufgabe 3: Erstellen einer Richtlinie für bedingten Zugriff zum Implementieren von MFA

Wie in Ihrer Schulung erwähnt wurde, gibt es drei Möglichkeiten, die MFA zu implementieren: mit Richtlinien für bedingten Zugriff, mit Sicherheitsstandardeinstellungen und mit der Legacymethode „MFA pro Benutzer“ (nicht für größere Organisationen empfohlen). In dieser Übung aktivieren Sie die MFA über eine Richtlinie für bedingten Zugriff, was die von Microsoft empfohlene Methode darstellt. Adatum hat Holly angewiesen, die MFA für alle Microsoft 365-Benutzer zu aktivieren – sowohl intern als auch extern. Zum Testen der Microsoft 365-Pilotprojektimplementierung von Adatum möchte Holly jedoch die Mitglieder der M365-Pilotprojektgruppe davon ausschließen, dass die MFA zur Anmeldung verwendet werden muss. Nach Abschluss des Pilotprojekts aktualisiert Holly die Richtlinie so, dass der Ausschluss dieser Gruppe aus der MFA-Anforderung entfernt wird. Die Richtlinie enthält auch zwei weitere Anforderungen. Sie schreibt die MFA für alle Cloud-Apps vor und erzwingt diese auch dann, wenn sich ein Benutzer von einem vertrauenswürdigen Standort anmeldet. 

1. Auf der VM LON-CL1 sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Aufgabe noch geöffnet sein. Sie sollten bei Microsoft 365 als **Holly Dickson** angemeldet sein.
   
2. Wählen Sie im **Microsoft 365 Admin Center** unter dem Abschnitt **Admin Center** im Navigationsbereich die Option **Identität** aus. Dadurch wird das Microsoft Entra Admin Center auf einer neuen Browserregisterkarte geöffnet. Wenn das Fenster **Konto auswählen** angezeigt wird, wählen Sie **Holly Dicksons Konto** aus.

3. Wählen Sie im **Microsoft Entra Admin Center** im Navigationsbereich die Option **Schutz** und dann **Bedingter Zugriff** aus.

4. Wählen Sie auf der Seite **Bedingter Zugriff | Übersicht** im mittleren Navigationsbereich **Richtlinien** aus.

5. Wählen Sie auf der Seite **Bedingter Zugriff | Richtlinien**, in der Menüleiste oben die Option **+ Neue Richtlinie** aus.

6. Geben Sie im Fenster **Neue Richtlinie für bedingten Zugriff** den Text **MFA für alle Microsoft 365-Benutzer** im Feld **Name** ein.

7. Zunächst definieren Sie die MFA-Anforderung für Benutzer. Wählen Sie unter der Gruppe **Benutzer** die Option **0 Benutzer und Gruppen ausgewählt** aus. Dadurch werden zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**.

8. Wählen Sie auf der Registerkarte **Einschließen** die Option **Alle Benutzer** aus. Beachten Sie die angezeigte Warnmeldung. Diese werden Sie in den nächsten beiden Schritten beheben.

9. Wählen Sie die Registerkarte **Ausschließen** aus. Um eine Systemsperre zu vermeiden, wie in der vorherigen Warnmeldung angegeben, sollten Sie Ihre globalen Administratoren ausschließen – in diesem Fall Holly. Holly möchte auch die anderen Microsoft 365-Pilotprojektgruppenmitglieder zur Beschleunigung der Tests ausschließen. Sobald Microsoft 365 bei ADatum live geht, entfernt Holly die Pilotprojektgruppe aus der Liste „Ausschließen“ in dieser Richtlinie für bedingten Zugriff und schließt nur sich selbst, den MOD Administrator, und mehrere andere globale Administratoren aus. Jetzt möchte Holly jedoch die gesamte Pilotprojektgruppe ausschließen. <br/>

    Aktivieren Sie dazu das Kontrollkästchen **Benutzer und Gruppen**. 

10. Wählen Sie im angezeigten Fenster **Ausgeschlossene Benutzer und Gruppen auswählen** die Microsoft 365-Pilotprojektgruppe aus. Die Registerkarte **Alle** wird standardmäßig angezeigt. Um die Pilotprojektgruppe schnell zu finden, wählen Sie die Registerkarte **Gruppen** aus. Aktivieren Sie in der Liste der aktiven Gruppen das Kontrollkästchen neben der Gruppe **M365 pilot project**, und aktivieren Sie dann die Schaltfläche **Auswählen** unten im Fenster. Beachten Sie im Fenster **Neue Richtlinie für bedingten Zugriff** die Meldung, die unter dem Abschnitt **Benutzer** angezeigt wird. 

11. Sie definieren nun die MFA-Anforderung für alle Cloud-Apps. Wählen Sie unter dem Abschnitt **Zielressourcen** die Option **Keine Zielressourcen ausgewählt** aus. Dadurch werden zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**.

12. Wählen Sie das Dropdownfeld **Wählen Sie aus, worauf diese Richtlinie angewendet werden soll.** aus, um die verschiedenen Optionen im Dropdownmenü anzuzeigen. Wählen Sie **Cloud-Apps** aus. 

13. Beachten Sie auf der Registerkarte **Einschließen**, dass die Standardeinstellung **Keine** ist. Wenn Sie diese Einstellung nicht geändert haben, benötigt keine der Cloud-Apps die MFA – und das schließt Microsoft 365 ein. Selbst wenn Sie diese Richtlinie erstellt und die Option ausgewählt haben, die MFA für alle Benutzer zu erzwingen, aber diese Einstellung unter **Zielressourcen** auf **Keine** festgelegt ist, dann müsste kein Benutzer, der sich bei Microsoft 365 anmeldet, MFA verwenden. <br/>

    Wählen Sie auf der Registerkarte **Einschließen** die Option **Apps auswählen** aus. Dadurch werden zwei Abschnitte angezeigt: **Filter bearbeiten** und **Auswählen**. Wählen Sie unter dem Abschnitt **Auswählen** die Option **Keine** aus. 

14. Scrollen Sie im angezeigten Bereich **Cloud-Apps auswählen** durch die Liste der Apps, um alle Apps zu sehen, für die Sie MFA vorschreiben könnten. **Wählen Sie KEINE der Apps aus.** Wir scrollen durch diese Liste, um ein Gefühl dafür zu bekommen, wie präzise Sie vorgehen können, falls Sie beschließen, die MFA in Ihrer echten Anwendung auf bestimmte Apps zu beschränken.  <br/>

    Für Adatum möchte Holly die MFA für alle Cloud-Apps erzwingen, was in der Regel ein häufigeres Geschäftsszenario ist als die Auswahl bestimmter Apps. Wählen Sie auf der Registerkarte **Einschließen** die Option **Alle Cloud-Apps** aus. Adatum schließt keine Cloud-Apps aus der Multi-Faktor-Authentifizierung aus. Sie können die Registerkarte **Ausschließen** auswählen, um die dortigen Optionen zu sehen. Sie funktioniert im Wesentlichen genauso wie die Registerkarte **Einschließen**. Sie können diese Registerkarte anzeigen, aber KEINE Cloud-Apps zum Ausschluss auswählen. 

15. Schließlich definieren Sie die MFA-Anforderung für alle Benutzeranmeldungsstandorte. In einigen Szenarios schreiben Organisationen möglicherweise nur die MFA vor, wenn sich ein Benutzer von einem nicht vertrauenswürdigen Standort anmeldet. Adatum möchte jedoch die MFA für alle eingeschlossenen Benutzer erzwingen, unabhängig davon, von wo aus sie sich anmelden. <br/>

    Wählen Sie unter **Bedingungen** die Option **0 Bedingungen ausgewählt** aus. Dadurch wird eine Liste der potenziellen Bedingungen angezeigt, auf die die Richtlinie überprüft. Wählen Sie für diese Labübung unter der Bedingung **Standorte** die Option **Nicht konfiguriert** aus. Dadurch werden die Umschaltfläche **Konfigurieren** und zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**. Beide Registerkarten sind derzeit deaktiviert.

16. Legen Sie die Umschaltfläche **Konfigurieren** auf **Ja**fest, wodurch die beiden Registerkarten aktiviert werden. 

17. Überprüfen Sie auf der Registerkarte **Einschließen**, ob **Alle Netzwerke und Standorte** ausgewählt ist (wählen Sie die Option bei Bedarf aus). Wählen Sie die Registerkarte **Ausschließen** aus. Wenn Ihre Organisation bestimmte IP-Adressen oder Adressbereiche als „vertrauenswürdig“ erkennt, können Sie die MFA-Anforderung ausschließen, wenn sich ein Benutzer von einem dieser Standorte anmeldet. Adatum möchte jedoch die MFA für alle Benutzeranmeldeversuche erzwingen, unabhängig von ihrem Standort. Das gilt sowohl für interne als auch für externe Benutzeranmeldungen. Überprüfen Sie, ob die Option **Ausgewählte Netzwerke und Standorte** ausgewählt ist, und vergewissern Sie sich, dass im Abschnitt **Auswählen** **Keine** steht. Indem keine Standorte angegeben werden, stellt diese Einstellung sicher, dass keine Standorte von der MFA ausgeschlossen werden. 

18. Wählen Sie unter dem Abschnitt **Zugriffssteuerungen** unter der Gruppe **Gewähren** die Option **0 Steuerungen ausgewählt** aus. Dadurch wird der Bereich **Erteilen** angezeigt.

19. Überprüfen Sie im angezeigten Bereich **Gewähren**, ob die Option **Zugriff gewähren** ausgewählt ist. Wählen Sie sie bei Bedarf aus. Beachten Sie alle verfügbaren Zugriffssteuerungen, die mit dieser Richtlinie aktiviert werden können. Diese Richtlinie erfordert nur MFA. Aktivieren Sie daher das Kontrollkästchen **Mehrstufige Authentifizierung erforderlich**. Wählen Sie die Schaltfläche **Auswählen** unten im Bereich **Gewähren** aus, die den Bereich schließt. 

20. Wählen Sie unten im Fenster **Neue Richtlinie für bedingten Zugriff** im Feld **Richtlinie aktivieren** die Option **Ein** aus.

21. Beachten Sie die Warnmeldung und Optionen, die unten auf der Seite angezeigt werden, die Sie davor warnen, sich nicht auszusperren. Wählen Sie die Option **Ich habe verstanden, dass mein Konto von dieser Richtlinie betroffen ist. Ich möchte dennoch fortfahren.** aus. Tatsächlich wird Holly nicht betroffen sein, da sie Mitglied der M365-Pilotprojektgruppe ist, die von dieser Richtlinie ausgeschlossen ist.

22. Wählen Sie die Schaltfläche **Erstellen** aus, um die Richtlinie zu erstellen.

23. Überprüfen Sie im angezeigten Fenster **Bedingter Zugriff | Richtlinien**, ob die Richtlinie **MFA für alle Microsoft 365-Benutzer** angezeigt wird und der **Status ** auf **Ein** festgelegt ist.

24. Bleiben Sie bei LON-CL1 angemeldet, und lassen alle Ihre Microsoft Edge-Browserregisterkarten für die nächste Aufgabe geöffnet.


### Aufgabe 4: Testen der MFA für einen eingeschlossenen und ausgeschlossenen Benutzer

Um die soeben erstellte Richtlinie für bedingten Zugriff zu testen, melden Sie sich bei Microsoft 365 als Holly ab, und melden Sie sich dann wieder als Adele Vance an. Adele ist kein Mitglied der M365-Pilotprojektgruppe, daher sollte Microsoft Entra bei der Anmeldung die MFA erzwingen. Sobald Sie sich als Adele angemeldet und sich vergewissert haben, dass die MFA funktioniert, melden Sie sich als Adele ab und dann wieder als Holly an. Da Holly ein Mitglied der M365-Pilotprojektgruppe ist, die von der Verwendung der MFA in der Richtlinie für bedingten Zugriff ausgeschlossen wurde, sollten Sie die MFA bei der Anmeldung als Holly nicht verwenden müssen. Ebenso müssen Sie MFA nicht verwenden, wenn Sie sich als die verschiedenen Mitglieder der M365-Pilotprojektgruppe in den verbleibenden Labs in diesem Kurs anmelden.

**Wichtig:** Um die MFA zu implementieren, müssen Sie Ihr Mobiltelefon verwenden, um einen Prüfcode zu erhalten, damit Sie ihn als zweite Authentifizierungsform bei Ihrem Mandanten eingeben können. Wenn Sie kein Mobiltelefon haben, können Sie Ihre Richtlinie für bedingten Zugriff trotzdem testen. Bei Kursteilnehmern ohne Telefon müssen Sie sich bei der Anmeldung als Adele Vance mit einer zweiten Authentifizierungsform anmelden. An diesem Punkt können Sie die Anmeldung einfach abbrechen und sich dann wieder als Holly anmelden, die keine MFA benötigt. Obwohl Sie die MFA-Anmeldung für Adele nicht abschließen, können Sie überprüfen, dass das System beim Versuch, sich als Adele anzumelden, diese erfordert.

1. Auf der VM LON-CL1 sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Aufgabe noch geöffnet sein. Sie sollten bei Microsoft 365 als **Holly Dickson** angemeldet sein. Sie beginnen mit der Abmeldung von Microsoft 365. Wählen Sie auf der Registerkarte **Microsoft 365 Admin Center** den Namen von Holly in der oberen rechten Ecke Ihres Browsers aus. Wählen Sie im angezeigten Fenster **Holly Dickson** die Option **Abmelden** aus. 
    
2. Sobald Sie von Microsoft 365 als Holly abgemeldet sind, schließen Sie Ihre Browsersitzung, um Ihren Cache zu löschen. Wählen Sie dann auf der Taskleiste das **Edge**-Symbol aus, um eine neue Browsersitzung zu öffnen. Wechseln Sie in Ihrem Browser zur **Microsoft 365-Startseite**, indem Sie die folgende URL in die Adressleiste eingeben: **https://portal.office.com/** 

3. Wählen Sie im erscheinenden Fenster **Konto auswählen** die Option **Anderes Konto verwenden** aus. 

4. Geben Sie im Fenster **Anmelden** **AdeleV@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist, und wählen Sie dann **Weiter** aus. Geben Sie im Fenster **Passwort eingeben** das von Ihrem Labor-Hosting-Anbieter bereitgestellte **Benutzerkennwort** ein und wählen Sie **Anmelden**.

5. Da MFA für alle Benutzer mit Ausnahme der Mitglieder der M365-Pilotprojektgruppe (zu denen Adele nicht zählt) aktiviert ist, wird das Fenster **Weitere Informationen erforderlich** angezeigt. Wählen Sie **Weiter** aus. Dadurch wird die **Microsoft Authenticator**-Seite geöffnet. Diese ist der Ausgangspunkt für die Anmeldung mit MFA. <br/>

    **Wichtig:** Wenn Sie kein Mobiltelefon besitzen, ist das der weiteste Punkt, wenn Sie versuchen, sich als Adele anzumelden. Obwohl Sie die Anmeldung nicht abschließen können, haben Sie überprüft, ob der erste Teil Ihrer Richtlinie für bedingten Zugriff funktioniert, da Adele sich mit MFA anmelden muss. Fahren Sie an diesem Punkt mit Schritt 18 fort, damit Sie sich wieder als Holly anmelden können.

6. Auf der angezeigten Seite **Microsoft Authenticator** können Sie diese mobile App herunterladen oder eine andere Methode für die MFA-Verifizierung verwenden. Für die Zwecke dieses Labs empfehlen wir Ihnen, Ihr Mobiltelefon zu verwenden, damit Sie keine Zeit aufwenden müssen, um die Microsoft Authenticator-App zu installieren, die Sie nach diesem Schulungskurs möglicherweise nicht mehr verwenden werden. Wählen Sie die Option **Ich möchte eine andere Methode einrichten.** unten auf der Seite aus. **Wichtig:** Verwechseln Sie diesen Link nicht mit der darüber angezeigten Option **Ich möchte eine andere Authentifikator-App verwenden**. 

7. Wählen Sie im daraufhin angezeigten Dialogfeld **Andere Methode auswählen** den Dropdownpfeil im Feld **Welche Methode möchten Sie verwenden?** aus, und wählen Sie **Telefon** und dann **Bestätigen** aus. 

8. Wählen Sie im angezeigten Fenster **Telefon** unter **Welche Telefonnummer möchten Sie verwenden?** Ihr Land oder Ihre Region aus, und geben Sie dann im Feld daneben Ihre Telefonnummer ein (im Format **nnn-nnn-nnnn**). Überprüfen Sie, ob die Option **Code empfangen** ausgewählt ist, und wählen Sie dann **Weiter** aus.

9. Rufen Sie den Prüfcode aus der Textnachricht ab, die an Ihr Mobiltelefon gesendet wird.

10. Geben Sie im Fenster **Telefon** den sechsstelligen Prüfcode in das Codefeld ein, und wählen Sie dann **Weiter** aus. Wenn im Fenster **Telefon** eine Meldung angezeigt wird, dass Ihr Telefon erfolgreich registriert wurde, wählen Sie **Weiter** aus.

11. Wählen Sie auf der Seite **Erfolg!** die Option **Fertig** aus.

12. Microsoft hat eine neue Sicherheitsrichtlinie in den Testmandanten implementiert, die in ihren Schulungslaboren verwendet werden. Alle vordefinierten Testbenutzerkonten sind so konfiguriert, dass die Kursteilnehmer ihr erstes Kennwort bei der nächsten Anmeldung ändern müssen. Sie haben dies schon gesehen, als Sie sich bei Microsoft 365 als MOD-Administrator in der ersten Übungsübung angemeldet haben. Sie müssen dies jetzt mit Adele tun. <br>

    Geben Sie im daraufhin angezeigten Fenster **Kennwort aktualisieren** das von Ihrem Lab-Hostanbieter bereitgestellte **Benutzerkennwort** in das Feld **Aktuelles Kennwort** ein. Geben Sie dann im Feld **Neues Kennwort** und **Kennwort bestätigen** das neue Benutzerkennwort ein, das Sie für alle Testbenutzer am Anfang des Labs definiert haben. Wählen Sie **anmelden** aus.

13. Wenn das Dialogfeld **Angemeldet bleiben?** angezeigt wird, aktivieren Sie das Kontrollkästchen **Nicht mehr anzeigen**, und wählen Sie dann **Ja** aus. 

14. Wenn ein Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, aktivieren Sie zweimal den Pfeil nach rechts, und aktivieren Sie dann das Häkchen.

15. Wenn ein Fenster **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** aus, um es zu schließen.

16. Wählen Sie auf der Seite **Willkommen bei Microsoft 365** das **Word**-Symbol aus, das in der Spalte der App-Symbole auf der linken Seite des Bildschirms angezeigt wird. Dadurch wird **Microsoft Word Online **geöffnet. Dadurch wird überprüft, ob Sie nach der Anmeldung mit MFA auf eine Microsoft 365-App zugreifen können.  <br/>

    **Wichtig:** Sie haben nun überprüft, ob der erste Teil der Richtlinie für bedingten Zugriff, die Sie erstellt haben, funktioniert. Die Richtlinie schreibt vor, dass sich Benutzer, die kein Mitglied des Microsoft 365-Pilotprojektteams sind, mit MFA anmelden müssen. Sie haben überprüft, ob das funktioniert, als Sie sich als Adele angemeldet haben. Sie melden sich jetzt als Adele ab und als Holly wieder an. Dabei überprüfen Sie, ob der zweite Teil der Richtlinie für bedingten Zugriff ebenfalls funktioniert. Sie sollten die MFA bei der Anmeldung als Holly NICHT verwenden müssen, da sie Mitglied der M365-Pilotprojektgruppe ist, die von der MFA-Anforderung in der Richtlinie für bedingten Zugriff ausgeschlossen ist.

17. Wählen Sie auf der Registerkarte **Microsoft 365 Admin Center** das Symbol für das Konto von Adele in der oberen rechten Ecke Ihres Browsers aus. Wählen Sie im angezeigten Fenster **Adele Vance** die Option **Abmelden** aus. <br/>
    
18. Schließen Sie Ihre Browsersitzung, um den Cache zu löschen. Wählen Sie auf der Taskleiste das **Edge**-Symbol aus, um eine neue Browsersitzung zu öffnen. Wechseln Sie in Ihrem Browser zur **Microsoft 365-Startseite**, indem Sie die folgende URL in die Adressleiste eingeben: **https://portal.office.com/**. 

19. Wählen Sie im Fenster **Konto auswählen** **Holly@xxxxxZZZZZZ.onmicrosoft.com** aus, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist, und wählen Sie dann **Weiter** aus. Geben Sie im Fenster **Kennwort eingeben** das neue Administratorkennwort ein, das Sie für alle Testbenutzer am Anfang des Labs definiert und später dem Konto von Holly zugewiesen haben. Wählen Sie **anmelden** aus.

20. Da die MFA für alle Benutzer mit Ausnahme der Mitglieder des M365-Pilotprojektteams (zu denen Holly zählt) erforderlich ist, wird die MFA nicht erzwungen. Da MFA nicht erforderlich ist, zeigt das System die **Microsoft 365-Startseite** auf der **Startseite | Microsoft 365** Registerkarte an. 

21. Wenn ein Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, aktivieren Sie zweimal den Pfeil nach rechts, und aktivieren Sie dann das Häkchen.

22. Wenn ein Fenster **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** aus, um es zu schließen.

23. Wählen Sie auf der Seite **Willkommen bei Microsoft 365** das Symbol **Administrator** im Seitenbereich aus, um zum **Microsoft 365 Admin Center**zu navigieren. <br/>

    **Wichtig:** Sie haben nun überprüft, ob der zweite Teil der Richtlinie für bedingten Zugriff, die Sie erstellt haben, funktioniert. Die Richtlinie schließt Mitglieder der Microsoft 365-Pilotprojektgruppe von der Anmeldung mit MFA aus. Holly ist Mitglied dieser Gruppe, und sie musste sich nicht mit MFA anmelden.

24. Bleiben Sie bei LON-CL1 angemeldet, und lassen Sie das **Microsoft 365 Admin Center** in Ihrem Browser geöffnet.


### Aufgabe 5: Bereitstellen von Microsoft Entra Smart Lockout

Der CTO von Adatum hat Sie gebeten, Microsoft Entra Smart Lockout bereitzustellen. Dieses Feature hilft dabei, Angreifer auszusperren, die versuchen, Ihre Benutzerkennwörter zu erraten oder Brute-Force-Methoden zu verwenden, um in Ihr Netzwerk zugelassen zu werden. Smart Lockout kann Anmeldungen gültiger Benutzer erkennen und anders behandeln als Anmeldungen von Angreifern und anderen unbekannten Quellen. 

Der CTO ist bestrebt, Smart Lockout zu implementieren, da das Feature Angreifer aussperrt, während Adatum-Benutzer weiterhin auf ihre Konten zugreifen und produktiv sein können. Der CTO hat Holly gebeten, Smart Lockout so zu konfigurieren, dass Benutzer dasselbe Kennwort nicht mehr als einmal verwenden können. Außerdem sollen sie keine Kennwörter verwenden können, die zu einfach oder zu häufig sind. 

**Hinweis:** Sie können Einstellungen für die Kontosperrungsrichtlinie sowohl im Gruppenrichtlinienverwaltungs-Editor als auch in Microsoft Entra über das Smart Lockout-Feature verwalten. In dieser Labaufgabe lernen Sie, wie Sie auf jede Methode zugreifen, obwohl Sie nur die Smart Lockout-Einstellungen in Microsoft Entra aktualisieren. Sie müssen den Domänencontroller des Unternehmens (LON-DC1) verwenden, um auf den Gruppenrichtlinienverwaltungs-Editor zuzugreifen. 

1. In den vorherigen Aufgaben haben Sie in LON-CL1 gearbeitet. In dieser Aufgabe arbeiten Sie über den Domänencontroller von Adatum, LON-DC1. <br/>

    Wechseln Sie zu **LON-DC1**.

2. Auf **LON-DC1-** müssen Sie **STRG+ALT+ENTF** drücken, um sich anzumelden. Ihr Kursleiter zeigt Ihnen, wie Sie diese Option in Ihrer VM-Umgebung finden. Melden Sie sich bei LON-DC1 mit dem lokalen Adatum-Administratorkonto an, das von Ihrem Labhostinganbieter (**Administrator**) mit dem Kennwort **Pa55w.rd** erstellt wurde.

3. Auf LON-DC1 wird der **Server-Manager** beim Start automatisch gestartet. Wählen Sie im **Server-Manager** in der oberen rechten Menüleiste **Extras** aus, und wählen Sie dann im Dropdownmenü **Gruppenrichtlinienverwaltung** aus. Maximieren Sie das angezeigte Fenster **Gruppenrichtlinienverwaltung**.

4. Sie sollten die Gruppenrichtlinie bearbeiten, die die Kontosperrrichtlinie Ihrer Organisation enthält. Erweitern Sie bei Bedarf in der Stammkonsolenstruktur im Seitenbereich **Forest:Adatum.com**, dann **Domänen** und dann **Adatum.com**.  <br/>

    ‎Klicken Sie unter **Adatum.com** mit der rechten Maustaste auf **Standarddomänenrichtlinie**, und wählen Sie dann im Menü **Bearbeiten** aus.

5. Maximieren Sie das angezeigte Fenster **Gruppenrichtlinienverwaltungs-Editor**.

6. Erweitern Sie in der Struktur **Standarddomänenrichtlinie** im Seitenbereich unter **Computerkonfiguration** die Option **Richtlinien**, und erweitern Sie dann **Windows-Einstellungen**, **Sicherheitseinstellungen** und dann **Kontorichtlinien**.

7. Wählen Sie im Ordner **Kontorichtlinien** die Option **Kontosperrrichtlinie** aus.

8. Wie Sie im daraufhin angezeigten Bereich sehen können, wurde keiner der Smart Lockout-Parameter definiert. Anstatt diese Sperrparameter im Gruppenrichtlinienverwaltungs-Editor zu verwalten, verwenden Sie das Microsoft Entra Admin Center. Sie können den Gruppenrichtlinienverwaltungs-Editor zwar verwenden, aber diese Methode wird in der Regel in lokalen Active Directory-Umgebungen verwendet. Wir haben Ihnen diesen Editor gezeigt, damit Sie diese Alternative kennenlernen. Organisationen, die ausschließlich cloudbasierte Dienste wie Microsoft 365 verwenden, oder die das Microsoft Entra Admin Center für benutzerfreundlicher als den Gruppenrichtlinienverwaltungs-Editor halten, bevorzugen das **Microsoft Entra Admin Center** zum Zuweisen der entsprechenden Werte im Entra ID-Kontext. <br/>  

    Beachten Sie außerdem, dass sich das Sperrverhalten und die Anpassungsoptionen zwischen den beiden Methoden unterscheiden. Mit dem Gruppenrichtlinienverwaltungs-Editor haben Sie genauere Kontrolle über Richtlinieneinstellungen, einschließlich „Kontensperrungsschwelle“, „Sperrdauer“ und „Kontosperrungszähler zurücksetzen nach“. Bei dieser Methode müssen Sie jedoch mit der Gruppenrichtlinie und der Active Directory-Verwaltung vertraut sein. Zudem kann die Kontosperrrichtlinie in Microsoft Entra nicht so umfangreich angepasst werden. ’Die Verwendung ist jedoch einfacher, obwohl einige der in der Gruppenrichtlinie verfügbaren Optimierungsoptionen fehlen. <br/>

    Für Adatum hat Holly beschlossen, das Microsoft Entra Admin Center zum Konfigurieren der Kontosperrungsrichtlinie des Unternehmens zu verwenden. ‎Wählen Sie auf der Taskleiste unten auf dem Bildschirm das **Microsoft Edge-Symbol** aus. Maximieren Sie bei Bedarf das Browserfenster, wenn es geöffnet wird.

9. Wechseln Sie in Ihrem Edge-Browser zur **Microsoft 365-Startseite**, indem Sie die folgende URL in die Adressleiste eingeben: **https://portal.office.com**. 

10. Im Dialogfeld **Anmelden** müssen Sie sich als Holly Dickson anmelden. Geben Sie **Holly@xxxxxZZZZZZ.onmicrosoft.com**ein, wobei xxxxxZZZZZZ das Mandantenpräfix ist, das von Ihrem Labhostinganbieter zugewiesen wurde. Wählen Sie **Weiter** aus. <br/>

11. Geben Sie im Dialogfeld **Kennwort eingeben** das neue Administratorkennwort ein, das Sie dem Konto von Holly zugewiesen haben, und wählen Sie dann **Anmelden** aus. 

12. Aktivieren Sie im Dialogfeld **Angemeldet bleiben?** das Kontrollkästchen **Nicht mehr anzeigen**, und wählen Sie dann **Ja** aus. Wählen Sie im daraufhin angezeigten Dialogfeld **Kennwort speichern** die Option **Nie** aus.

13. Wenn in der Mitte des Bildschirms das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, gibt es keine Möglichkeit, es zu schließen. Wählen Sie stattdessen rechts neben dem Fenster das Vorwärtspfeilsymbol (**>**) zweimal aus, und wählen Sie dann das Häkchensymbol aus, um durch die Folien in diesem Nachrichtenfenster zu navigieren. 

14. Wenn eines der Fenster **Weitere Apps suchen** oder **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** in der oberen Ecke der Fenster aus, um es zu schließen. 

15. Wählen Sie auf der Seite **Willkommen bei Microsoft 365** in der Liste der Anwendungssymbole, die im Seitenbereich des Fensters angezeigt werden, **Administrator** aus. Dadurch wird das **Microsoft 365 Admin Center** auf einer neuen Browserregisterkarte geöffnet. 

16. Wählen Sie im Navigationsbereich des **Microsoft 365 Admin Center** die Option **Alle anzeigen** aus. Wählen Sie unter **Admin Center** die Option **Identität** aus, wodurch das **Microsoft Entra Admin Center** auf einer neuen Registerkarte angezeigt wird.

17. Wählen Sie im **Microsoft Entra Admin Center** im Navigationsbereich die Option **Schutz** und dann **Authentifizierungsmethoden** aus.

18. Wählen Sie auf der Seite **Authentifizierungsmethoden | Richtlinien** im mittleren Bereich unter dem Abschnitt **Verwalten** die Option **Kennwortschutz** aus.

19. Geben Sie im Fenster **Authentifizierungsmethoden | Kennwortschutz** im Detailbereich auf der rechten Seite die folgenden Informationen ein:

    - Im Abschnitt **Benutzerdefinierte intelligente Sperre**:

        - **Sperrschwellenwert**: Dieses Feld gibt an, wie viele fehlgeschlagene Anmeldungen für ein Konto vor der ersten Sperrung zulässig sind. Der Standardwert ist 10. Für Testzwecke hat Adatum diesen Wert auf **3** festgelegt.

        - **Sperrdauer in Sekunden**: Das ist die Dauer jeder Sperrung in Sekunden. Der Standardwert ist 60 Sekunden (eine Minute). Adatum hat Sie gebeten, diesen Wert in **90** Sekunden zu ändern.

    - Im Abschnitt **Benutzerdefinierte gesperrte Kennwörter**:

        - **Benutzerdefinierte Liste erzwingen**: Wählen Sie **Ja** aus.

        - **Liste benutzerdefinierter gesperrter Kennwörter**: Geben Sie die folgenden Werte ein. Drücken Sie nach der Eingabe jedes Werts die EINGABETASTE, damit sich jeder Wert in einer separaten Zeile befindet:

            - **Password01**

            - **F00tball01**

            - **Se@Hawks1**

            - **Never4get!!**

    - Wählen Sie im Abschnitt **Modus** die Option **Erzwungen** aus.

20. Wählen Sie **Speichern** in der Menüleiste oben auf der Seite aus.

21. Sie sollten nun die Funktion für gesperrte Kennwörter testen. Wählen Sie das Benutzersymbol von Holly Dickson in der oberen rechten Ecke des Bildschirms aus, und wählen Sie im daraufhin angezeigten Menü **Konto anzeigen** aus. 

22. Wählen Sie im angezeigten Fenster **Mein Konto** in der Kachel **Kennwort** die Option **KENNWORT ÄNDERN** aus.

23. Eine neue Registerkarte mit dem Fenster **Kennwort ändern** wird angezeigt. Geben Sie im Feld **Altes Kennwort** das vorhandene Kennwort von Holly ein, bei dem es sich um das neue administrative Kennwort handelt. <br/>

    Geben Sie **Never4get!!** unter **Neues Kennwort erstellen** und **Neues Kennwort bestätigen** ein, und wählen Sie dann **Übermitteln** aus. Beachten Sie die angezeigte Fehlermeldung.

24. Schließen Sie im Browser die Registerkarte **Kennwort ändern**. 

25. Sie werden nun die Sperrschwellenfunktionalität testen. Dazu verwenden Sie das Konto von Patti Fernandez. Wählen Sie das Benutzersymbol von Holly Dickson in der oberen rechten Ecke des Bildschirms aus, und wählen Sie im daraufhin angezeigten Menü **Abmelden** aus.  

26. Nachdem Sie sich als Holly abgemeldet haben, wird das Fenster **Konto auswählen** auf der Registerkarte **Bei Microsoft Entra anmelden** angezeigt. Die bewährte Methode, wenn Sie sich von einem Microsoft-Onlinedienst als ein Benutzer abmelden und sich als ein anderer anmelden, besteht darin, alle Browserregisterkarten zu schließen, mit Ausnahme der Registerkarte **Abmelden** oder **Anmelden**. Schließen Sie in diesem Fall die anderen Registerkarten, und lassen Sie die Registerkarte **Anmelden** geöffnet.  <br/>

    Wählen Sie im Fenster **Konto auswählen** die Option **Anderes Konto verwenden** aus. 

27. Geben Sie im Fenster **Anmelden** **pattif@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter zugeteilte Mandantenpräfix ist, und wählen Sie dann **Weiter** aus. 

28. Geben Sie im Fenster **Kennwort eingeben** eine beliebige Mischung aus Buchstaben und Zahlen ein, und wählen Sie dann **Anmelden** aus. Sie sehen, dass die Fehlermeldung „Ungültiges Kennwort“ angezeigt wird. 

    Wiederholen Sie diesen Schritt noch zweimal. 
    
    Da Sie den **Schwellenwert für Sperre** auf **3** festgelegt haben, sollten Sie eine Fehlermeldung erhalten, die angibt, dass dieses Konto nach dem dritten fehlgeschlagenen Anmeldeversuch gesperrt ist. <br/>

    **Hinweis:** Wenn Sie diese Sperrmeldung nach dem dritten Versuch nicht erhalten, hat das System diese Sperrschwellenänderung noch nicht im gesamten Dienst angewendet. Es kann mehrere Minuten dauern, bis die Änderung in Kraft tritt. Warten Sie ein paar Minuten, und melden Sie sich dann erneut mit einem falschen Kennwort an. Beim Testen dieses Labs gab es unterschiedliche Ergebnisse. Die Änderung wurde manchmal fast sofort überall angewendet, sodass Sie nach dem dritten Anmeldeversuch gesperrt werden. In anderen Fällen dauerte es zwischen fünf und zehn Minuten, bevor die Sperrmeldung angezeigt wird. Fahren Sie mit diesem Vorgang fort, bis Sie die Sperrmeldung erhalten. Dann wird das Konto von Patti vorübergehend gesperrt, um unbefugten Zugriff zu verhindern.

29. Sie dürfen sich erst nach der **Sperrdauer von 90 Sekunden**, die Sie zuvor festgelegt haben, erneut als Patti anmelden. <br/>

    Nachdem Sie gesperrt wurden, warten Sie 90 Sekunden, und melden Sie sich dann wieder als **pattif@xxxxxZZZZZZ.onmicrosoft.com** an. Hierbei ist xxxxxZZZZZZ das Mandantenpräfix, das Ihnen vom Labhostinganbieter zugewiesen wurde. Geben Sie im Feld **Kennwort** das Kennwort von Patti ein. Dabei handelt es sich um das **Benutzerkennwort**, das von Ihrem Labhostinganbieter bereitgestellt wird. 
 
30. Wie Sie sich erinnern, werden alle vordefinierten Testbenutzerkonten in Ihrem Testmandanten so konfiguriert, dass Sie ihr erstes Kennwort bei der nächsten Anmeldung ändern müssen. Wenn das Fenster **Kennwort aktualisieren** angezeigt wird, ist dies die Überprüfung, dass ihr Anmeldeversuch mit dem tatsächlichen Kennwort von Patti erfolgreich war. <br>

    **Hinweis:** Sie müssen den Anmeldevorgang für Patti nicht abschließen, da dies Ihre letzte Übung im Lab ist, die den LON-DC1-Domänencontroller verwendet. Sie können alle Anwendungen auf LON-DC1 schließen.
 
# Fahren Sie mit „Lab 2, Übung 2“ fort.
