# Lernpfad 2, Lab 2, Übung 1: Verwalten des sicheren Benutzerzugriffs 

Organisationen müssen sicherstellen, dass der Zugriff auf ihre Unternehmensdaten in Microsoft 365 immer geschützt ist. Microsoft 365 – und daher auch Copilot für Microsoft 365 – zeigt häufig vertrauliche Daten an, einschließlich E-Mails, Dokumente, Kundeninformationen und geistiges Eigentum. Unbefugter Zugriff auf Microsoft 365 kann zu Datenschutzverletzungen, Identitätsdiebstahl und anderen schädlichen Aktivitäten führen. Durch das Absichern des Benutzerzugriffs können Organisationen verhindern, dass nicht autorisierte Personen auf Unternehmensdaten zugreifen und möglicherweise Unternehmensdaten missbrauchen oder offenlegen, wenn Sie in Microsoft 365 und Copilot for Microsoft 365 arbeiten.

In der folgenden Labübung nehmen Sie die Rolle von Holly Dickson ein, der neuen Microsoft 365-Administratorin von Adatum. Sie verwenden mehrere Benutzerverwaltungsfunktionen, um Adatum auf die bevorstehende Copilot for Microsoft 365-Bereitstellung vorzubereiten. Sie beginnen mit dem Erstellen eines Microsoft 365-Benutzerkontos für Holly, der die Microsoft 365-Rolle „Globaler Administrator“ zugewiesen wird. 

**Hinweis:** Die von Ihrem Labhostinganbieter bereitgestellte VM-Umgebung beinhaltet über 20 bestehende Microsoft 365-Benutzerkonten sowie eine große Anzahl bestehender lokaler Benutzerkonten. In diesem Kurs werden mehrere der bestehenden Microsoft 365-Benutzerkonten verwendet. Obwohl das MOD-Administratorkonto von Ihrem Labhostinganbieter erstellt wurde, erstellen Sie Holly Dicksons Benutzerkonto, da eine bewährte Methode darin besteht, die Microsoft 365-Rolle „Globaler Administrator“ mehr als einem Benutzer zuzuweisen. Dabei lernen Sie auch, ein Microsoft 365-Benutzerkonto zu erstellen, falls Sie mit dem Prozess nicht vertraut sind.

Holly wurde dann vom CTO von Adatum aufgefordert, die Multi-Faktor-Authentifizierung (MFA) und Smart Lock von Microsoft Entra bereitzustellen. Diese Features tragen zur Verbesserung der Kennwortverwaltung in der gesamten Organisation bei, was der Vorbereitung auf Copilot for Microsoft 365 dient. Für Smart Lockout stellen Sie sie mithilfe der Gruppenrichtlinienverwaltung bereit. 

**WICHTIGE MFA-ANKÜNDIGUNG:** Aufgrund einer kürzlichen Änderung von Microsoft an den in diesem Kurs verwendeten Microsoft 365-Testmandanten mussten wir eine entsprechende Änderung an diesem Lab vornehmen. <br/>

**Ursprüngliches Labdesign:** Diese Labübung wurde ursprünglich so konzipiert, dass Sie als Holly Dickson eine Richtlinie für bedingten Zugriff erstellt haben, die MFA bei Adatum in Aufgabe 3 aktiviert hat. Dies ist die empfohlene Methode zur Aktivierung der MFA, wie Sie im Vorlesungsteil dieser Schulung gelernt haben. In Aufgabe 3 haben Sie eine Richtlinie für bedingten Zugriff erstellt, die MFA für alle Benutzer aktiviert hat, MIT AUSNAHME von Mitgliedern der Microsoft 365-Pilotprojektgruppe, die Sie in einer früheren Übung erstellt haben. Um Ihre Richtlinie in Aufgabe 4 zu testen, mussten Sie sich dann als Adele Vance anmelden. Da Adele kein Mitglied der Pilotprojektgruppe war, mussten Sie den MFA-Prozess abschließen, um sich bei Microsoft 365 anzumelden. Sie haben sich dann als Adele abgemeldet und wieder als Holly Dickson angemeldet. Da Holly Mitglied der Microsoft 365-Pilotprojektgruppe ist, musste sie nur ihren Benutzernamen und ihr Kennwort eingeben. Sie musste keine zweite Form der Authentifizierung mit MFA durchführen. Diese beiden Schritte in Aufgabe 4 haben Ihre Richtlinie für bedingten Zugriff verifiziert, d. h. nur Benutzer, die nicht Teil der Pilotprojektgruppe waren, mussten MFA verwenden. 

Die andere Auswirkung dieser Richtlinie besteht darin, dass Sie MFA nicht bei der Anmeldung bei den restlichen Labs als andere Testbenutzer verwenden mussten, die auch Mitglieder der Microsoft 365-Pilotprojektgruppe waren. Ausschlüsse von der MFA können zwar aus praktischen Gründen festgelegt werden, abhängig von den geschäftlichen Anforderungen eines Unternehmens, aber Unternehmen sollten die damit verbundenen Risiken sorgfältig bewerten und sparsam Ausschlüsse vornehmen – und das stets in Übereinstimmung mit den Best Practices für Sicherheit. In diesem Lab haben Sie den Ausschluss der Pilotprojektgruppe aus zwei Gründen erstellt: Damit Sie lernen, wie Sie einen Ausschluss in eine Richtlinie für bedingten Zugriff vornehmen, aber auch zur Zeitersparnis in den Schulungslabs, wenn Sie sich als Testbenutzer anmelden. <br/>

**Änderung beim Microsoft-Mandanten:** Microsoft hat jedoch seitdem eine Richtlinie für bedingten Zugriff im Microsoft 365-Testmandanten erstellt, der in dieser Übung verwendet wird, die MFA für alle Benutzerkonten vorschreibt. Leider hat die Richtlinie für bedingten Zugriff von Microsoft Vorrang vor der Richtlinie für bedingten Zugriff, die Sie in diesem Lab erstellen, um eine bestimmte Gruppe auszuschließen. Richtlinien für bedingten Zugriff in Microsoft Entra werden zusammen ausgewertet, und die Richtlinie mit der höchsten Priorität, die für einen Benutzer gilt, wird erzwungen. Wenn mehrere Richtlinien mit der gleichen Priorität vorhanden sind, gilt hier die restriktivste Richtlinie. In diesem Fall ist die Microsoft-Richtlinie restriktiver als die von Ihnen erstellte Richtlinie, da Ihre Benutzerausnahmen enthält. <br/>

**Auswirkung auf diese Labübung:** Obwohl Microsoft in diesem Testmandanten MFA über eine Richtlinie für bedingten Zugriff erzwingt, erstellen Sie weiterhin Ihre eigene Richtlinie für bedingten Zugriff, wie sie ursprünglich in Aufgabe 3 entworfen wurde. Die Aufgabe wurde geringfügig im Vergleich zur ursprünglichen Version verändert, sodass Sie die Richtlinie sehen können, die Microsoft in den Testmandanten integriert hat. Abgesehen davon hat sich die von Ihnen erstellte Richtlinie nicht gegenüber dem ursprünglichen Design geändert: Sie schreibt MFA für alle Benutzer vor, mit Ausnahme der Mitglieder der Microsoft 365-Pilotprojektgruppe. Da die Richtlinie, die Microsoft in den Testmandanten des Labs integriert hat, jedoch die restriktivere der beiden Richtlinien ist, hat diese Richtlinie Vorrang bei der Erzwingung. Es gibt zwei Auswirkungen dieses Szenarios. Erstens müssen Sie aufgrund der Microsoft-Richtlinie MFA verwenden, wenn Sie sich im Rahmen der restlichen Labs als Testbenutzer anmelden. Zweitens, da Microsoft Entra Ihre Richtlinie ignoriert, ist es sinnlos, sie zu testen. Daher wurde die ursprüngliche Aufgabe 4 entfernt, die die von Ihnen erstellte Richtlinie für bedingten Zugriff getestet hat. Obwohl Sie Ihre Richtlinie jetzt nicht testen können, möchten wir, dass Sie sie in Aufgabe 3 erstellen, damit Sie diese Erfahrung für Ihre realen Bereitstellungen machen. 

### Aufgabe 1: Erstellen eines Benutzerkontos für die Microsoft 365-Administratorin von Adatum

Holly Dickson ist die neue Microsoft 365-Administratorin von Adatum. Da noch kein Microsoft 365-Benutzerkonto für sie eingerichtet wurde, hat sie sich im vorherigen Lab zunächst mit dem MOD-Administratorkonto (der standardmäßige globale Administrator) bei Microsoft 365 angemeldet. In dieser Aufgabe bleiben Sie weiterhin als MOD-Administrator angemeldet, wo Sie ein Microsoft 365-Benutzerkonto für Holly erstellen. Außerdem weisen Sie die dem Konto von Holly die Microsoft 365-Rolle „Globaler Administrator“ zu. Diese Rolle erteilt Holly die erforderlichen Berechtigungen, um alle administrativen Funktionen in Microsoft 365 auszuüben. Nach dieser Aufgabe melden Sie sich mit dem neuen Konto von Holly an, und Sie absolvieren alle verbleibenden Labs mit Hollys Persona. 

**Lizenzhinweis:** Vor dem Erstellen des Hollys Kontos überprüfen Sie zuerst die Anzahl der verfügbaren Lizenzen. Dabei werden Sie feststellen, dass Ihr Labmandant zwar 20 Microsoft 365 E5-Lizenzen und 20 Enterprise Mobility + Security E5-Lizenzen bereitstellt, aber alle diese Lizenzen bereits den Benutzerkonten zugewiesen wurden, die von Ihrem Labhostinganbieter erstellt wurden. Daher müssen Sie zuerst eine Lizenz jeder Sorte von einem anderen Benutzer entziehen, damit Sie sie Holly zuweisen können.

**Wichtig:** Als bewährte Methode in Ihrer realen Bereitstellung sollten Sie immer die Anmeldeinformationen des ersten globalen Administratorkontos notieren. In diesem Lab ist es das MOD-Administratorkonto, dessen Benutzername admin@xxxxxZZZZZZ.onmicrosoft.com ist. Hierbei ist xxxxxZZZZZZ das Mandantenpräfix, das Ihrem Labhostinganbieter zugewiesen ist. Sie sollten diese Kontoinformationen aus Sicherheitsgründen gut geschützt aufbewahren. **Dieses Konto sollte eine nicht personalisierte Identität** sein, die über die höchsten Berechtigungen verfügt, die in einem Mandanten möglich sind. Die MFA sollte **nicht** aktiviert werden, da sie nicht personalisiert ist. Da der Benutzername und das Kennwort für dieses erste globale Administratorkonto in der Regel von mehreren Benutzern gemeinsam verwendet werden, ist dieses Konto ein perfektes Ziel für Angriffe. Daher wird immer empfohlen, dass Organisationen personalisierte Dienstadministratorkonten (z. B. einen Exchange-Administrator, SharePoint-Administrator usw.) erstellen und so wenige persönliche globale Administratoren wie möglich haben. Die persönlichen globalen Administratoren, die Sie in Ihrer realen Bereitstellung erstellen, sollten jeweils einem einzelnen Benutzer (z. B. Holly Dickson) zugeordnet werden, und für jedes sollte die Multi-Faktor-Authentifizierung (MFA) von Microsoft Entra erzwungen werden. Microsoft hat MFA also bereits standardmäßig für alle Benutzer in Ihrem Microsoft 365-Testmandanten aktiviert.

1. Auf der VM **LON-CL1** sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Labübung noch geöffnet sein. Sie sollten bei Microsoft 365 als **MOD-Administrator** angemeldet sein. 

2. Da Sie einen neuen Benutzer hinzufügen, sollten Sie zunächst die Lizenzverfügbarkeit überprüfen, bevor Sie das Benutzerkonto hinzufügen. Wählen Sie im **Microsoft 365 Admin Center**-Navigationsbereich **Abrechnung** aus, um die Abrechnungsgruppe zu erweitern, und wählen Sie dann **Lizenzen** aus. 

3. Auf der Seite **Lizenzen** wird standardmäßig die Registerkarte **Abonnements** angezeigt. Beachten Sie in der Liste der Abonnements, dass die Abonnements **Enterprise Mobility + Security E5** und **Microsoft 365 E5** keine verfügbaren Lizenzen haben. Ihr Labmandant stellt 20 Lizenzen für jedes Abonnement bereit, aber alle 40 Lizenzen wurden zugewiesen. Da Sie Holly sowohl eine **Enterprise Mobility + Security E5**-Lizenz als auch eine **Microsoft 365 E5**-Lizenz zuweisen müssen, müssen Sie die Lizenzen zunächst einem anderen Benutzerkonto entziehen, um sie für Holly verfügbar zu machen. 

4. Wählen Sie im **Microsoft 365 Admin Center**-Navigationsbereich **Benutzer** und dann **Aktive Benutzer** aus. In der Liste **Aktive Benutzer** wird die Liste der vorhandenen Benutzerkonten angezeigt, die von Ihrem Labhostinganbieter erstellt wurden. Da Christie Cline in eine neue Rolle im Unternehmen annimmt und nicht mehr Teil des Microsoft 365-Pilotprojekts ist, entziehen Sie ihrem Konto die **Enterprise Mobility + Security E5**- und **Microsoft 365 E5**-Lizenzen, damit Sie sie dem neuen Konto von Holly Dickson zuweisen können.

5. Wählen Sie auf der Seite **Aktive Benutzer** in der Liste der Benutzer **Christie Cline** aus. Wählen Sie Christies verlinkten Namen und nicht das Kontrollkästchen neben ihrem Namen aus.

6. Im erscheinenden Bereich **Christie Cline** wird standardmäßig die Registerkarte **Konto** angezeigt. Wählen Sie die Registerkarte **Lizenzen und Apps** aus. Deaktivieren Sie unter **Lizenzen (2)** die Kontrollkästchen neben **Enterprise Mobility + Security E5** und **Microsoft 365 E5**, und wählen Sie dann **Änderungen speichern** aus. Nachdem die Änderungen gespeichert wurden, schließen Sie den Bereich **Christie Cline**. 

7. Sie können jetzt ein Benutzerkonto für Holly Dickson erstellen, die die neue Microsoft 365-Administratorin von Adatum ist. Dabei weisen Sie Holly die Microsoft 365-Rolle „Globaler Administrator“ zu, die ihr globalen Zugriff auf die meisten Verwaltungsfeatures und -daten in Microsoft-Onlinediensten gewährt. Außerdem weisen Sie Holly die beiden Lizenzen zu, die Sie Christie Cline gerade entzogen haben. <br/>

    Wählen Sie im Fenster **Aktive Benutzer** die Option **Benutzer hinzufügen** aus, die in der Menüleiste oberhalb der Liste der aktiven Benutzer angezeigt wird. Dadurch wird der Assistent **Benutzer hinzufügen** gestartet.

8. Geben Sie auf der **Grundeinstellungen** des Assistenten **Benutzer hinzufügen** die folgenden Informationen ein:

    - Vorname: **Holly**

    - Nachname: **Dickson** 

    - Anzeigename: Wenn Sie per TAB-TASTE in dieses Feld wechseln, wird **Holly Dickson** angezeigt.

    - Benutzername: **Holly** <br/>
    
        ‎**WICHTIG:** Rechts neben dem Feld **Benutzername** ist das Feld „Domäne“. Es wird mit der Clouddomäne **xxxxxZZZZZZ.onmicrosoft.com** vorab ausgefüllt, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist.<br/>
    
    - Deaktivieren Sie das Kontrollkästchen **Kennwort automatisch erstellen**, wodurch ein neues Feld für die Eingabe eines vom Administrator definierten Kennworts angezeigt wird.

    - Geben Sie im erscheinenden neuen Feld **Kennwort** das **Administratorkennwort** ein, das Ihr Labhostinganbieter für das Mandantenadministratorkonto (z. B. das MOD-Administratorkonto) bereitgestellt hat.

    - Deaktivieren Sie das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern**. 

9. Wählen Sie **Weiter** aus. Wenn das Dialogfeld **Kennwort speichern** oben auf dem Bildschirm angezeigt wird, wählen Sie **Nie** aus.

10. Geben Sie auf der Seite **Produktlizenzen zuweisen** die folgenden Informationen ein: <br/>

    - Standort: **USA**

    - Lizenzen: Aktivieren Sie unter der Option **Benutzer eine Produktlizenz zuweisen** die Kontrollkästchen **Enterprise Mobility + Security E5** und **Microsoft 365 E5**.

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

### Aufgabe 2: Hinzufügen von Holly zur Microsoft 365-Pilotprojektgruppe

Nach Abschluss der vorherigen Aufgabe sollten Sie beim **Microsoft 365 Admin Center** weiterhin mit dem Konto **MOD-Administrator** angemeldet sein. In dieser Aufgabe beginnen Sie mit der Implementierung des Microsoft 365-Pilotprojekts von Adatum als Holly Dickson, der neuen Microsoft 365-Administratorin von Adatum. Daher beginnen Sie diese Aufgabe, indem Sie sich bei Microsoft 365 als MOD-Administrator abmelden und sich wieder als Holly anmelden. 

In einer vorherigen Aufgabe haben Sie eine Microsoft 365-Gruppe für die Mitglieder des Pilotprojektteams von Adatum erstellt, sodass Sie ein benutzerdefiniertes Design für diese Gruppe erstellen können. In dieser Aufgabe fügen Sie Holly zu dieser Gruppe hinzu. 

1. Auf der VM LON-CL1 sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Aufgabe noch geöffnet sein. Sie sollten bei Microsoft 365 als **MOD-Administrator** angemeldet sein. <br/>

    Beachten Sie auf der Registerkarte **Microsoft 365 Admin Center** in der oberen rechten Ecke des Bildschirms, dass der Name des MOD-Administrators und ein Megafonsymbol angezeigt werden. Der Name wird aufgrund des benutzerdefinierten Designs angezeigt, das Sie in der vorherigen Labübung erstellt haben, die einer Gruppe von Microsoft 365-Pilotprojektbenutzern zugeordnet war, zu denen auch der MOD-Administrator gehörte. Bedenken Sie das, sobald Sie sich wieder als Holly Dickson anmelden. <br/>

    Wählen Sie das Benutzersymbol für den **MOD-Administrator** in der oberen rechten Ecke Ihres Browsers aus. Wählen Sie im angezeigten Fenster **MOD-Administrator** die Option **Abmelden** aus. <br/>
    
    **Wichtig:** Wenn Sie sich von einem Benutzerkonto abmelden und sich bei einem anderen anmelden, sollten Sie alle Browserregisterkarten mit Ausnahme der Registerkarte **Abmelden** schließen. Diese bewährte Methode hilft, Verwirrung zu vermeiden, indem die Fenster geschlossen werden, die dem vorherigen Benutzer zugeordnet sind. Nachdem Sie sich vom MOD-Administratorkonto abgemeldet haben, nehmen Sie sich einen Moment Zeit, um alle anderen Browserregisterkarten zu schließen, mit Ausnahme der Registerkarte **Abmelden**. 
    
2. Geben Sie in Ihrem Microsoft Edge-Browser auf der Registerkarte **Abmelden** die folgende URL in die Adressleiste ein, um sich wieder bei Microsoft 365 anzumelden: **https://portal.office.com**. 

3. Wählen Sie im Fenster **Konto auswählen** nur das Mandantenadministratorkonto des MOD-Administrators (das admin@xxxxxZZZZZZ.onmicrosoft.com-Konto) aus, von dem Sie sich gerade abgemeldet haben. Wählen Sie **Anderes Konto verwenden** aus. 

4. Geben Sie im Fenster **Anmelden** **Holly@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das vom Labhostinganbieter bereitgestellte Mandantenpräfix ist. Wählen Sie **Weiter** aus.

5. Geben Sie im Fenster **Kennwort eingeben** das **Administratorkennwort** ein, das Ihr Labhostinganbieter für das Mandantenadministratorkonto (z. B. das MOD-Administratorkonto) bereitgestellt hat und das Sie Hollys Konto zugewiesen haben. Wählen Sie dann **Anmelden** aus. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus.  <br/>

    **Hinweis:** Ab diesem Zeitpunkt sind Holly und der MOD-Administrator die einzigen Benutzer, denen das von Ihrem Labhostinganbieter bereitgestellte **Administratorkennwort** zugewiesen wurde. Allen anderen Benutzern wird das vom Labhostinganbieter bereitgestellte **Benutzerkennwort** zugewiesen.

6. Wenn in der Mitte des Bildschirms das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, gibt es keine Möglichkeit, es zu schließen. Wählen Sie stattdessen rechts neben dem Fenster das Vorwärtspfeilsymbol (**>**) zweimal aus, und wählen Sie dann das Häkchensymbol aus, um durch die Folien in diesem Nachrichtenfenster zu navigieren. 

7. Wenn das Fenster **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** in der oberen rechten Ecke des Fensters aus, um es zu schließen. 

8. Die Seite **Willkommen bei Microsoft 365** wird in Ihrem Edge-Browser auf der Registerkarte **Startseite | Microsoft 365** angezeigt. Das ist die Microsoft 365-Willkommensseite von Holly. Sie sehen, dass Hollys Initialen in der oberen rechten Ecke des Bildschirms angezeigt werden, ihr Name jedoch nicht. Das liegt daran, dass Hollys Konto zu dem Zeitpunkt, als Sie die Microsoft 365-Pilotprojektbenutzer zur Gruppe hinzugefügt haben, die dem benutzerdefinierten Design in der vorherigen Labübung zugeordnet war, nicht vorhanden war. Da Holly ihren Namen oben in jedem Microsoft 365-Fenster sehen möchte, wenn sie beim System angemeldet ist, möchte sie zuerst ihr Konto zur Gruppe der Microsoft 365-Pilotprojektbenutzer hinzufügen. <br>

    Wählen Sie in der Spalte der Anwendungssymbole, die auf der linken Seite des Bildschirms angezeigt werden, **Administrator** aus. Dadurch wird das **Microsoft 365 Admin Center** auf einer neuen Browserregisterkarte geöffnet. 

9. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Teams und Gruppen** und dann **Aktive Teams und Gruppen** aus. 

10. Auf der Seite **Aktive Teams und Gruppen** gibt es eine Registerkarte zum Anzeigen der einzelnen Gruppentypen. Die Registerkarte **Teams- und Microsoft 365-Gruppen** wird standardmäßig angezeigt. Wählen Sie auf dieser Registerkarte **M365 pilot project** aus.

11. Im angezeigten Bereich **M365 pilot project** wird standardmäßig die Registerkarte **Allgemein** angezeigt. Wählen Sie die Registerkarte **Mitgliedschaft** aus.

12. Auf der Registerkarte **Mitgliedschaft** wird die Unterregisterkarte **Besitzer** standardmäßig im Navigationsbereich angezeigt, der sich auf der linken Seite des Bereichs befindet. Wählen Sie die Unterregisterkarte **Mitglieder** aus, die darunter angezeigt wird.

13. Wählen Sie auf der Unterregisterkarte **Mitglieder** die Option **+ Mitglieder hinzufügen** aus.

14. Wählen Sie im daraufhin angezeigten Bereich **Gruppenmitglieder zu M365 pilot project hinzufügen** das Feld **Nach Name oder E-Mail-Adresse suchen** aus. Scrollen Sie in der angezeigten Benutzerliste nach unten, und wählen Sie **Holly Dickson** aus. Wählen Sie die Schaltfläche **Hinzufügen (1)** aus, und schließen Sie dann den Bereich **Gruppenmitglieder zu M365 pilot project hinzufügen**, nachdem Holly der Gruppe hinzugefügt wurde.

15. Wählen Sie auf der Seite **Aktive Teams und Gruppen** das Symbol **Aktualisieren** aus, das oben auf dem Bildschirm links neben der Adressleiste angezeigt wird. Sie sehen, dass Holly Dicksons Name neben ihren Initialen in der oberen rechten Ecke des Bildschirms angezeigt wird (Hinweis: Möglicherweise müssen Sie zweimal aktualisieren, um Hollys Namen zu sehen).

16. Wählen Sie im **Microsoft 365 Admin Center** im Navigationsbereich **Benutzer** und dann **Aktive Benutzer** aus.

17. Wenn Sie im Fenster **Aktive Benutzer** mit dem Mauszeiger auf den **Anzeigenamen** eines Benutzers zeigen, wird rechts neben dem Benutzernamen ein **Schlüsselsymbol** angezeigt. Durch Auswählen des Schlüsselsymbols können Sie das Kennwort eines Benutzers zurücksetzen. Sie müssen die Kennwörter für Adele Vance, Alex Wilber, Joni Sherman, Lynne Robbins und Patti Fernandez zurücksetzen und auf das **Administratorkennwort** festlegen, das von Ihrem Labhostinganbieter für das Mandantenadministratorkonto (d. h. das MOD-Administratorkonto) bereitgestellt wurde und das Sie zuvor Holly Dickson zugewiesen haben.<br/>

    Zeigen Sie mit der Maus auf **Adele Vance**, und wählen Sie das angezeigte Schlüsselsymbol aus.

18. Deaktivieren Sie im Bereich **Kennwort zurücksetzen**, der für Adele angezeigt wird, das Kontrollkästchen **Kennwort automatisch erstellen**. 

19. Geben Sie im erscheinenden Feld **Kennwort** das **Administratorkennwort** ein, das Ihr Labhostinganbieter für das Mandantenadministratorkonto (z. B. das MOD-Administratorkonto) bereitgestellt hat. Wählen Sie das Augensymbol (**Kennwort anzeigen**) am Ende des Felds **Kennwort** aus, um den eingegebenen Wert anzuzeigen. Stellen Sie sicher, dass Sie das Mandantenkennwort richtig eingegeben haben.

20. Deaktivieren Sie das Kontrollkästchen **Benutzer muss sein Kennwort bei der ersten Anmeldung ändern**.

21. Wählen Sie **Kennwort zurücksetzen** aus. Wenn das Dialogfeld **Kennwort speichern** oben auf dem Bildschirm angezeigt wird, wählen Sie **Nie** aus. Wählen Sie dann **Schließen** im Bereich **Das Kennwort wurde zurückgesetzt.** aus.

22. Wiederholen Sie die Schritte 17 bis 21 für **Alex Wilber**, **Joni Sherman**, **Lynne Robbins** und **Patti Fernandez**. Ändern Sie deren Kennwörter in das **Administratorkennwort**, das Ihr Labhostinganbieter für das Mandantenadministratorkonto (z. B. das MOD-Administratorkonto) bereitgestellt hat. Vergessen Sie in Schritt 19 nicht, das eingegebene Kennwort anzuzeigen, um zu überprüfen, ob es sich um den richtigen Wert handelt.

23. Bleiben Sie bei LON-CL1 angemeldet, und öffnen Sie das **Microsoft 365 Admin Center** in Ihrem Browser für die nächste Aufgabe.


### Aufgabe 3: Bereitstellen der MFA mithilfe einer Richtlinie für bedingten Zugriff

Wie in Ihrer Schulung erwähnt wurde, gibt es drei Möglichkeiten, die MFA zu implementieren: mit Richtlinien für bedingten Zugriff, mit Sicherheitsstandardeinstellungen und mit der Legacymethode „MFA pro Benutzer“ (nicht für größere Organisationen empfohlen). In dieser Übung aktivieren Sie die MFA über eine Richtlinie für bedingten Zugriff, was die von Microsoft empfohlene Methode darstellt. Adatum hat Holly angewiesen, die MFA für alle Microsoft 365-Benutzer zu aktivieren – sowohl intern als auch extern. Zum Testen der Microsoft 365-Pilotprojektimplementierung von Adatum möchte Holly jedoch die Mitglieder der M365-Pilotprojektgruppe davon ausschließen, dass die MFA zur Anmeldung verwendet werden muss. Nach Abschluss des Pilotprojekts aktualisiert Holly die Richtlinie so, dass der Ausschluss dieser Gruppe aus der MFA-Anforderung entfernt wird. Die Richtlinie enthält auch zwei weitere Anforderungen. Sie schreibt die MFA für alle Cloud-Apps vor und erzwingt diese auch dann, wenn sich ein Benutzer von einem vertrauenswürdigen Standort anmeldet. 

1. Auf der VM LON-CL1 sollte das **Microsoft 365 Admin Center** in Microsoft Edge aus der vorherigen Aufgabe noch geöffnet sein. Sie sollten bei Microsoft 365 als **Holly Dickson** angemeldet sein.
   
2. Wählen Sie im **Microsoft 365 Admin Center** unter dem Abschnitt **Admin Center** im Navigationsbereich die Option **Identität** aus. Dadurch wird das Microsoft Entra Admin Center auf einer neuen Browserregisterkarte geöffnet. Wenn das Fenster **Konto auswählen** angezeigt wird, wählen Sie **Holly Dicksons Konto** aus.

3. Wählen Sie im **Microsoft Entra Admin Center** im Navigationsbereich die Option **Schutz** und dann **Bedingter Zugriff** aus.

4. Wählen Sie auf der Seite **Bedingter Zugriff | Übersicht** im mittleren Navigationsbereich **Richtlinien** aus.

5. Überprüfen Sie auf der Seite **Bedingter Zugriff | Richtlinien** die Standardrichtlinien, die für Ihr Microsoft 365-Abonnement verfügbar sind. Beachten Sie die Richtlinie mit dem Titel **Multi-Faktor-Authentifizierung für Microsoft Partner und Microsoft-Anbieter**. Dies ist die Richtlinie für bedingten Zugriff, die von Microsoft erstellt wurde, die MFA für alle Benutzer in allen Cloud-Apps vorschreibt. Wählen Sie diese Richtlinie aus, damit Sie sehen können, wie Microsoft die MFA für alle Benutzer in diesem Testmandanten erzwingt.

6. Wählen Sie auf der Seite **Multi-Faktor-Authentifizierung für Microsoft Partner und Microsoft-Anbieter** unter der Gruppe **Benutzer** die Option **Alle Benutzer eingeschlossen und bestimmte Benutzer ausgeschlossen** aus. Dadurch werden zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**.

7. Beachten Sie auf der Registerkarte **Einschließen**, dass **Alle Benutzer** ausgewählt ist. Um Ihre Neugier zu befriedigen, versuchen wir, diese Richtlinie zu ändern, indem Sie die MFA deaktivieren. Wählen Sie **Keine** und dann die Schaltfläche **Speichern** aus. <br/>

    **Beobachten Sie, was passiert:** Am oberen Rand der Seite wurde kurz ein Feld mit der Meldung **Multi-Faktor-Authentifizierung für Microsoft Partner und Microsoft-Anbieter konnte nicht aktualisiert werden** angezeigt. Das System hat Sie dann zurück zur Seite **Bedingter Zugriff | Richtlinien** geführt. Wenn diese Meldung nicht angezeigt wird, wiederholen Sie diesen Schritt.  <br/>

    Das gleiche geschieht, wenn Sie auf der Registerkarte **Einschließen** die Option **Benutzer und Gruppen** auswählen und bestimmte Benutzer oder Gruppen anstelle aller Benutzer auswählen. Tatsächlich hat Microsoft eine Sicherheitsfirewall integriert, sodass bei einem Versuch, diese Richtlinie zu ändern, ein Fehler auftritt, wenn Sie versuchen, die Richtlinie zu speichern. 

8. Microsoft hat einen Ausschluss in diese Richtlinie integriert. Werfen wir einen Blick darauf. Wählen Sie auf der Seite **Richtlinien** die Richtlinie **Multi-Faktor-Authentifizierung für Microsoft Partner und Microsoft-Anbieter** und dann **Alle Benutzer eingeschlossen und bestimmte Benutzer ausgeschlossen** aus. Wählen Sie dieses Mal die Registerkarte **Ausschließen** aus. 

9. Beachten Sie, dass Microsoft das Kontrollkästchen **Verzeichnisrollen** aktiviert hat. Wählen Sie das Feld unter dieser Option aus. Im Menü der Rollen, die Sie aus der MFA ausschließen können, ist die einzige von Microsoft ausgewählte Rolle **Verzeichnissynchronisierungskonten**. Diese Rolle wird automatisch dem Microsoft Entra Connect Sync-Dienstkonto zugewiesen und soll nicht anderweitig verwendet werden. Es ist eine spezielle Rolle, die nur zum Ausführen von Verzeichnissynchronisierungsaufgaben berechtigt ist. Diese Rolle ist entscheidend für die Synchronisierung einer lokalen Active Directory Domain Services-Instanz (AD DS) mit Microsoft Entra ID, wodurch Identitäten koexistieren können. Microsoft schreibt keine MFA für diese Rolle vor, da der Synchronisierungsdienst ohne Unterbrechungen ausgeführt werden muss, die durch MFA-Aufforderungen verursacht werden können. Darüber hinaus ist dieses Dienstkonto mit sehr eingeschränkten Berechtigungen konfiguriert und wird nicht für interaktive Anmeldungen verwendet, wodurch das Sicherheitsrisiko reduziert ist.   <br/>

    Wie bei dem vorherigen Schritt, in dem Sie versucht haben, die MFA-Einstellung so zu ändern, dass keine Benutzer oder ausgewählte Benutzer eingeschlossen werden, können Sie nun versuchen, andere Rollen auszuwählen, um die MFA-Einstellung zu umgehen. Es wird jedoch derselbe Fehler mit der Meldung **Multi-Faktor-Authentifizierung für Microsoft Partner und Microsoft-Anbieter konnte nicht aktualisiert werden** angezeigt, wenn Sie versuchen, die Richtlinie zu speichern. Die Sicherheitsfirewall von Microsoft lässt keine Änderung dieser Richtlinie für bedingten Zugriff zu, die sich auf diejenigen auswirkt, die MFA verwenden müssen.

10. Wenn die Seite **Multi-Faktor-Authentifizierung für Microsoft Partner und Microsoft-Anbieter** noch geöffnet ist, wählen Sie in der oberen Ecke das **X** aus, um sie zu schließen. Kehren Sie dann zur Seite **Bedingter Zugriff | Richtlinien** zurück. Falls Sie versucht haben, eine Änderung an der Richtlinie zu speichern, ist der Versuch fehlgeschlagen, und Sie sollten bereits auf der Seite **Bedingter Zugriff | Richtlinien** sein.

11. Wählen Sie auf der Seite **Bedingter Zugriff | Richtlinien**, in der Menüleiste oben die Option **+ Neue Richtlinie** aus.

12. Geben Sie im Fenster **Neue Richtlinie für bedingten Zugriff** den Text **MFA für alle Microsoft 365-Benutzer** im Feld **Name** ein.

13. Zunächst definieren Sie die MFA-Anforderung für Benutzer. Wählen Sie unter der Gruppe **Benutzer** die Option **0 Benutzer und Gruppen ausgewählt** aus. Dadurch werden zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**.

14. Wählen Sie auf der Registerkarte **Einschließen** die Option **Alle Benutzer** aus. Beachten Sie die angezeigte Warnmeldung. Diese werden Sie in den nächsten beiden Schritten beheben.

15. Wählen Sie die Registerkarte **Ausschließen** aus. Um eine Systemsperre zu vermeiden, wie in der vorherigen Warnmeldung angegeben, sollten Sie Ihre globalen Administratoren ausschließen – in diesem Fall Holly. Holly möchte auch die anderen Microsoft 365-Pilotprojektgruppenmitglieder zur Beschleunigung der Tests ausschließen. Sobald Microsoft 365 live ist, entfernt Holly die Pilotprojektgruppe aus der Liste „Ausschließen“ in dieser Richtlinie für bedingten Zugriff und schließt nur sich selbst und mehrere andere globale Administratoren aus. Für den Moment möchte Holly jedoch die gesamte Gruppe ausschließen. <br/>

    Wählen Sie dazu **Benutzer und Gruppen** aus. 

16. Wählen Sie im angezeigten Fenster **Ausgeschlossene Benutzer und Gruppen auswählen** die Microsoft 365-Pilotprojektgruppe aus. Die Registerkarte **Alle** wird standardmäßig angezeigt. Um die Pilotprojektgruppe schnell zu finden, wählen Sie die Registerkarte **Gruppen** aus. Aktivieren Sie in der Liste der aktiven Gruppen das Kontrollkästchen neben der Gruppe **M365 pilot project**, und aktivieren Sie dann die Schaltfläche **Auswählen** unten im Fenster. Beachten Sie im Fenster **Neue Richtlinie für bedingten Zugriff** die Meldung, die unter dem Abschnitt **Benutzer** angezeigt wird. 

17. Sie definieren nun die MFA-Anforderung für alle Cloud-Apps. Wählen Sie unter dem Abschnitt **Zielressourcen** die Option **Keine Zielressourcen ausgewählt** aus. Dadurch werden zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**.

18. Wählen Sie das Dropdownfeld **Wählen Sie aus, worauf diese Richtlinie angewendet werden soll.** aus, um die verschiedenen Optionen im Dropdownmenü anzuzeigen. Wählen Sie **Cloud-Apps** aus. 

19. Beachten Sie auf der Registerkarte **Einschließen**, dass die Standardeinstellung **Keine** ist. Wenn Sie diese Einstellung nicht geändert haben, benötigt keine der Cloud-Apps die MFA – und das schließt Microsoft 365 ein. Selbst wenn Sie diese Richtlinie erstellt und die Option ausgewählt haben, die MFA für alle Benutzer zu erzwingen, aber diese Einstellung unter **Zielressourcen** auf **Keine** festgelegt ist, dann müsste kein Benutzer, der sich bei Microsoft 365 anmeldet, MFA verwenden. <br/>

    Wählen Sie auf der Registerkarte **Einschließen** die Option **Apps auswählen** aus. Dadurch werden zwei Abschnitte angezeigt: **Filter bearbeiten** und **Auswählen**. Wählen Sie unter dem Abschnitt **Auswählen** die Option **Keine** aus. Scrollen Sie im angezeigten Bereich **Cloud-Apps auswählen** durch die Liste der Apps, um alle Apps zu sehen, für die Sie MFA vorschreiben könnten. **Wählen Sie KEINE der Apps aus.** Wir scrollen durch diese Liste, um ein Gefühl dafür zu bekommen, wie präzise Sie vorgehen können, falls Sie beschließen, die MFA auf bestimmte Apps zu beschränken.  <br/>

    Für Adatum möchte Holly die MFA für alle Cloud-Apps erzwingen, was in der Regel ein häufigeres Geschäftsszenario ist als die Auswahl bestimmter Apps. Wählen Sie auf der Registerkarte **Einschließen** die Option **Alle Cloud-Apps** aus. Adatum schließt keine Cloud-Apps aus der Multi-Faktor-Authentifizierung aus. Sie können die Registerkarte **Ausschließen** auswählen, um die dortigen Optionen zu sehen. Sie funktioniert im Wesentlichen genauso wie die Registerkarte **Einschließen**. Sie können diese Registerkarte anzeigen, aber KEINE Cloud-Apps zum Ausschluss auswählen. 

20. Schließlich definieren Sie die MFA-Anforderung für alle Benutzeranmeldungsstandorte. In einigen Szenarios schreiben Organisationen möglicherweise nur die MFA vor, wenn sich ein Benutzer von einem nicht vertrauenswürdigen Standort anmeldet. Adatum möchte jedoch die MFA für alle eingeschlossenen Benutzer erzwingen, unabhängig davon, wo sie sich anmelden. <br/>

    Wählen Sie unter **Bedingungen** die Option **0 Bedingungen ausgewählt** aus. Dadurch wird eine Liste der potenziellen Bedingungen angezeigt, auf die die Richtlinie überprüft. Wählen Sie für diese Labübung unter der Bedingung **Standorte** die Option **Nicht konfiguriert** aus. Dadurch werden die Umschaltfläche **Konfigurieren** und zwei Registerkarten angezeigt: **Einschließen** und **Ausschließen**. Beide Registerkarten sind derzeit deaktiviert.

21. Legen Sie die Umschaltfläche **Konfigurieren** auf **Ja**fest, wodurch die beiden Registerkarten aktiviert werden. 

22. Überprüfen Sie auf der Registerkarte **Einschließen**, ob **Alle Standorte** ausgewählt ist (wählen Sie die Option bei Bedarf aus). Wählen Sie die Registerkarte **Ausschließen** aus. Wenn Ihre Organisation bestimmte IP-Adressen oder Adressbereiche als „vertrauenswürdig“ erkennt, können Sie die MFA-Anforderung ausschließen, wenn sich ein Benutzer von einem dieser Standorte anmeldet. Adatum möchte jedoch die MFA für alle Benutzeranmeldeversuche erzwingen, unabhängig von ihrem Standort. Das gilt sowohl für interne als auch für externe Benutzeranmeldungen. Überprüfen Sie, ob die Option **Ausgewählte Standorte** ausgewählt ist, und vergewissern Sie sich, dass im Abschnitt **Auswählen** **Keine** steht. Indem keine Standorte angegeben werden, stellt diese Einstellung sicher, dass keine Standorte von der MFA ausgeschlossen werden. 

23. Wählen Sie unter dem Abschnitt **Zugriffssteuerungen** unter der Gruppe **Gewähren** die Option **0 Steuerungen ausgewählt** aus. Dadurch wird der Bereich **Erteilen** angezeigt.

24. Überprüfen Sie im angezeigten Bereich **Gewähren**, ob die Option **Zugriff gewähren** ausgewählt ist. Wählen Sie sie bei Bedarf aus. Aktivieren Sie dann das Kontrollkästchen **Multi-Faktor-Authentifizierung erforderlich**. Beachten Sie alle anderen verfügbaren Zugriffssteuerungen, die mit dieser Richtlinie aktiviert werden können. Für diese Richtlinie benötigen Sie nur die MFA. Wählen Sie die Schaltfläche **Auswählen** unten im Bereich **Gewähren** aus, die den Bereich schließt. 

25. Wählen Sie unten im Fenster **Neu** im Feld **Richtlinie aktivieren** die Option **Ein** aus.

26. Beachten Sie die Option, die unten auf der Seite angezeigt wird und Sie warnt, sich nicht selbst auszusperren. Wählen Sie die Option **Ich habe verstanden, dass mein Konto von dieser Richtlinie betroffen ist. Ich möchte dennoch fortfahren.** aus. Tatsächlich wird Holly nicht betroffen sein, da sie Mitglied der M365-Pilotprojektgruppe ist, die von dieser Richtlinie ausgeschlossen ist.

27. Wählen Sie die Schaltfläche **Erstellen** aus, um die Richtlinie zu erstellen.

28. Überprüfen Sie im angezeigten Fenster **Bedingter Zugriff | Richtlinien**, ob die Richtlinie **MFA für alle Microsoft 365-Benutzer** angezeigt wird und der **Status ** auf **Ein** festgelegt ist.

29. Bleiben Sie bei LON-CL1 angemeldet, und lassen alle Ihre Microsoft Edge-Browserregisterkarten für die nächste Aufgabe geöffnet.

**Hinweis:** Wie bereits erwähnt, gibt es keine Möglichkeit, Ihre Richtlinie für bedingten Zugriff im aktuellen Microsoft 365-Testmandanten zu testen. Die Richtlinie für bedingten Zugriff von Microsoft erzwingt MFA für alle Benutzer. Wenn Sie über mehrere Richtlinien verfügen, die MFA erfordern, gilt die restriktivste Richtlinie. In diesem Fall ist die Microsoft-Richtlinie restriktiver als die Richtlinie, die Sie soeben erstellt haben, die Ausnahmen für die Mitglieder der Pilotprojektgruppe enthielt. Obwohl Sie Ihre Richtlinie nicht mit diesem Testmandanten testen können, empfehlen wir Ihnen, diese Erfahrung beim Erstellen einer Richtlinie für bedingten Zugriff zu nutzen, um die MFA in Ihren realen Microsoft 365-Bereitstellungen zu erzwingen.


### Aufgabe 4: Bereitstellen von Microsoft Entra Smart Lockout

Der CTO von Adatum hat Sie gebeten, Microsoft Entra Smart Lockout bereitzustellen. Dieses Feature hilft dabei, Angreifer auszusperren, die versuchen, Ihre Benutzerkennwörter zu erraten oder Brute-Force-Methoden zu verwenden, um in Ihr Netzwerk zugelassen zu werden. Smart Lockout kann Anmeldungen gültiger Benutzer erkennen und anders behandeln als Anmeldungen von Angreifern und anderen unbekannten Quellen. 

Der CTO ist bestrebt, Smart Lockout zu implementieren, da das Feature Angreifer aussperrt, während Adatum-Benutzer weiterhin auf ihre Konten zugreifen und produktiv sein können. Der CTO hat Holly gebeten, Smart Lockout so zu konfigurieren, dass Benutzer dasselbe Kennwort nicht mehr als einmal verwenden können. Außerdem sollen sie keine Kennwörter verwenden können, die zu einfach oder zu häufig sind. 

**Hinweis:** Sie können Einstellungen für die Kontosperrungsrichtlinie sowohl im Gruppenrichtlinienverwaltungs-Editor als auch in Microsoft Entra über das Smart Lockout-Feature verwalten. In dieser Labaufgabe lernen Sie, wie Sie auf jede Methode zugreifen, obwohl Sie nur die Smart Lockout-Einstellungen in Microsoft Entra aktualisieren. Sie müssen den Domänencontroller des Unternehmens (LON-DC1) verwenden, um auf den Gruppenrichtlinienverwaltungs-Editor zuzugreifen. 

1. In den vorherigen Aufgaben haben Sie in LON-CL1 gearbeitet. In dieser Aufgabe arbeiten Sie über den Domänencontroller von Adatum, LON-DC1. <br/>

    Wechseln Sie zu **LON-DC1**.

2. Auf **LON-DC1-** müssen Sie **STRG+ALT+ENTF** drücken, um sich anzumelden. Ihr Kursleiter zeigt Ihnen, wie Sie diese Option in Ihrer VM-Umgebung finden. Melden Sie sich bei LON-DC1 mit dem lokalen Adatum-Administratorkonto an, das von Ihrem Labhostinganbieter (**Administrator**) mit dem Kennwort **Pa55w.rd** erstellt wurde.

3. Auf LON-DC1 wird der **Server-Manager** beim Start automatisch gestartet. Wählen Sie im **Server-Manager** in der oberen rechten Menüleiste **Extras** aus, und wählen Sie dann im Dropdownmenü **Gruppenrichtlinienverwaltung** aus. Maximieren Sie das angezeigte Fenster **Gruppenrichtlinienverwaltung**.

4. Sie sollten die Gruppenrichtlinie bearbeiten, die die Kontosperrrichtlinie Ihrer Organisation enthält. Erweitern Sie bei Bedarf in der Stammkonsolenstruktur im linken Bereich **Forest:Adatum.com**, dann **Domänen** und dann **Adatum.com**.  <br/>

    ‎Klicken Sie unter **Adatum.com** mit der rechten Maustaste auf **Standarddomänenrichtlinie**, und wählen Sie dann im Menü **Bearbeiten** aus.

5. Maximieren Sie das angezeigte Fenster **Gruppenrichtlinienverwaltungs-Editor**.

6. Erweitern Sie in der Struktur **Standarddomänenrichtlinie** im linken Bereich unter **Computerkonfiguration** die Option **Richtlinien**, und erweitern Sie **Windows-Einstellungen**, dann **Sicherheitseinstellungen** und dann **Kontorichtlinien**.

7. Wählen Sie im Ordner **Kontorichtlinien** die Option **Kontosperrrichtlinie** aus.

8. Wie Sie im rechten Bereich sehen können, wurden keiner der Smart Lockout-Parameter definiert. Anstatt diese Sperrparameter im Gruppenrichtlinienverwaltungs-Editor zu verwalten, verwenden Sie das Microsoft Entra Admin Center. Sie können den Gruppenrichtlinienverwaltungs-Editor zwar verwenden, aber diese Methode wird in der Regel in lokalen Active Directory-Umgebungen verwendet. Wir haben Ihnen diesen Editor gezeigt, damit Sie diese Alternative kennenlernen. Organisationen, die ausschließlich cloudbasierte Dienste wie Microsoft 365 verwenden, oder die das Microsoft Entra Admin Center für benutzerfreundlicher als den Gruppenrichtlinienverwaltungs-Editor halten, bevorzugen das **Microsoft Entra Admin Center** zum Zuweisen der entsprechenden Werte im Entra ID-Kontext. <br/>  

    Beachten Sie außerdem, dass sich das Sperrverhalten und die Anpassungsoptionen zwischen den beiden Methoden unterscheiden. Mit dem Gruppenrichtlinienverwaltungs-Editor haben Sie genauere Kontrolle über Richtlinieneinstellungen, einschließlich „Kontensperrungsschwelle“, „Sperrdauer“ und „Kontosperrungszähler zurücksetzen nach“. Bei dieser Methode müssen Sie jedoch mit der Gruppenrichtlinie und der Active Directory-Verwaltung vertraut sein. Zudem kann die Kontosperrrichtlinie in Microsoft Entra nicht so umfangreich angepasst werden. ’Die Verwendung ist jedoch einfacher, obwohl einige der in der Gruppenrichtlinie verfügbaren Optimierungsoptionen fehlen. <br/>

    Für Adatum hat Holly beschlossen, das Microsoft Entra Admin Center zum Konfigurieren der Kontosperrungsrichtlinie des Unternehmens zu verwenden. ‎Wählen Sie auf der Taskleiste unten auf dem Bildschirm das **Microsoft Edge-Symbol** aus. Maximieren Sie bei Bedarf das Browserfenster, wenn es geöffnet wird.

9. Wechseln Sie in Ihrem Edge-Browser zur **Microsoft 365-Startseite**, indem Sie die folgende URL in die Adressleiste eingeben: **https://portal.office.com**. 

10. Im Dialogfeld **Anmelden** müssen Sie sich als Holly Dickson anmelden. Geben Sie **Holly@xxxxxZZZZZZ.onmicrosoft.com**ein, wobei xxxxxZZZZZZ das Mandantenpräfix ist, das von Ihrem Labhostinganbieter zugewiesen wurde. Wählen Sie **Weiter** aus. <br/>

11. Geben Sie im Dialogfeld **Kennwort eingeben** das eindeutige **Administratorkennwort** ein, das von Ihrem Labhostinganbieter bereitgestellt wurde, und wählen Sie dann **Anmelden** aus. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus.

12. Aktivieren Sie im Dialogfeld **Angemeldet bleiben?** das Kontrollkästchen **Nicht mehr anzeigen**, und wählen Sie dann **Ja** aus. Wählen Sie im daraufhin angezeigten Dialogfeld **Kennwort speichern** die Option **Nie** aus.

13. Wenn in der Mitte des Bildschirms das Dialogfeld **Willkommen bei Microsoft 365** angezeigt wird, gibt es keine Möglichkeit, es zu schließen. Wählen Sie stattdessen rechts neben dem Fenster das Vorwärtspfeilsymbol (**>**) zweimal aus, und wählen Sie dann das Häkchensymbol aus, um durch die Folien in diesem Nachrichtenfenster zu navigieren. 

14. Wenn das Fenster **Weitere Apps suchen** oder **Mit Microsoft 365 erstellen** angezeigt wird, wählen Sie das **X** in der oberen rechten Ecke der Fenster aus, um es zu schließen. 

15. Wählen Sie auf der Seite **Willkommen bei Microsoft 365** in der Liste der Anwendungssymbole, die im linken Bereich angezeigt werden, **Administrator** aus. Dadurch wird das **Microsoft 365 Admin Center** auf einer neuen Browserregisterkarte geöffnet. 

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

23. Eine neue Registerkarte mit dem Fenster **Kennwort ändern** wird angezeigt. Geben Sie im Feld **Altes Kennwort** das aktuelle Kennwort von Holly ein, bei dem es sich um das **Administratorkennwort** handelt, das Ihr Labhostinganbieter für das Mandantenadministratorkonto (z. B. das MOD-Administratorkonto) bereitgestellt hat. <br/>

    Geben Sie **Never4get!!** unter **Neues Kennwort erstellen** und **Neues Kennwort bestätigen** ein, und wählen Sie dann **Übermitteln** aus. Beachten Sie die angezeigte Fehlermeldung.

24. Schließen Sie im Browser die Registerkarte **Kennwort ändern**. 

25. Jetzt sollten Sie die Sperrschwellenfunktion testen. Wählen Sie das Benutzersymbol von Holly Dickson in der oberen rechten Ecke des Bildschirms aus, und wählen Sie im daraufhin angezeigten Menü **Abmelden** aus.  

26. Nachdem Sie sich als Holly abgemeldet haben, wird das Fenster **Konto auswählen** auf der Registerkarte **Bei Microsoft Entra anmelden** angezeigt. Die bewährte Methode, wenn Sie sich von einem Microsoft-Onlinedienst als ein Benutzer abmelden und sich als ein anderer anmelden, besteht darin, alle Browserregisterkarten zu schließen, mit Ausnahme der Registerkarte **Abmelden** oder **Anmelden**. Schließen Sie in diesem Fall die anderen Registerkarten, und lassen Sie die Registerkarte **Anmelden** geöffnet.  <br/>

    Wählen Sie im Fenster **Konto auswählen** die Option **Anderes Konto verwenden** aus. 

27. Melden Sie sich im Fenster **Anmelden** als Patti Fernandez an. Geben Sie **pattif@xxxxxZZZZZZ.onmicrosoft.com** ein, wobei xxxxxZZZZZZ das Mandantenpräfix ist, das Ihnen von Ihrem Labhostinganbieter zugewiesen wurde, und wählen Sie dann **Weiter** aus. 

28. Geben Sie im Fenster **Kennwort eingeben** eine beliebige Mischung aus Buchstaben und Zahlen ein, und wählen Sie dann **Anmelden** aus. Sie sehen, dass die Fehlermeldung „Ungültiges Kennwort“ angezeigt wird. 

    Wiederholen Sie diesen Schritt noch zweimal. 
    
    Da Sie den **Schwellenwert für Sperre** auf **3** festgelegt haben, sollten Sie eine Fehlermeldung erhalten, die angibt, dass dieses Konto nach dem dritten fehlgeschlagenen Anmeldeversuch gesperrt ist. <br/>

    **Hinweis:** Wenn Sie diese Sperrmeldung nach dem dritten Versuch nicht erhalten, hat das System diese Sperrschwellenänderung noch nicht im gesamten Dienst angewendet. Es kann mehrere Minuten dauern, bis die Änderung in Kraft tritt. Warten Sie ein paar Minuten, und melden Sie sich dann erneut mit einem falschen Kennwort an. Beim Testen dieses Labs gab es unterschiedliche Ergebnisse. Die Änderung wurde manchmal fast sofort überall angewendet, sodass Sie nach dem dritten Anmeldeversuch gesperrt werden. In anderen Fällen dauerte es zwischen fünf und zehn Minuten, bevor die Sperrmeldung angezeigt wird. Fahren Sie mit diesem Vorgang fort, bis Sie die Sperrmeldung erhalten. Dann wird das Konto von Patti vorübergehend gesperrt, um unbefugten Zugriff zu verhindern.

29. Sie dürfen sich erst nach der **Sperrdauer von 90 Sekunden**, die Sie zuvor festgelegt haben, erneut als Patti anmelden. <br/>

    Nachdem Sie gesperrt wurden, warten Sie 90 Sekunden, und melden Sie sich dann wieder als **pattif@xxxxxZZZZZZ.onmicrosoft.com** an. Hierbei ist xxxxxZZZZZZ das Mandantenpräfix, das Ihnen vom Labhostinganbieter zugewiesen wurde. Geben Sie im Feld **Kennwort** das Kennwort von Patti ein. Dabei handelt es sich um das **Benutzerkennwort**, das von Ihrem Labhostinganbieter bereitgestellt wird. Führen Sie bei Bedarf den MFA-Anmeldevorgang aus. Überprüfen Sie, ob Sie sich erfolgreich als Patti anmelden können.

30. Sobald die Anmeldung erfolgreich war, können Sie alle geöffneten Anwendungen schließen. Das ist Ihre letzte Labübung mit dem LON-DC1-Domänencontroller.
 
# Fahren Sie mit „Lab 2, Übung 2“ fort.
