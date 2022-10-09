---
wts:
  title: 02 – Erstellen einer Web-App (10 Min.)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="02---create-a-web-app-10-min"></a>02 – Erstellen einer Web-App (10 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir eine Web-App, in der ein Docker-Container ausgeführt wird. Der Docker-Container enthält eine Willkommensnachricht. 

Azure App Service ist eine Sammlung von vier Diensten, die zum Hosten und Ausführen von Webanwendungen dienen. Die vier Dienste (Web-Apps, Mobile Apps, API-Apps und Logic Apps) sehen unterschiedlich aus, funktionieren jedoch letztendlich alle sehr ähnlich. Web-Apps ist der am häufigsten verwendete Dienst der vier Dienste. Diesen Dienst werden wir in diesem Lab verwenden.

# <a name="task-1-create-a-web-app"></a>Aufgabe 1: Erstellen einer Web-App 

In dieser Aufgabe erstellen Sie eine Azure App Service-Web-App. 

1. Melden Sie sich beim [Azure-Portal](http://portal.azure.com/)an. 

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **App Services**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**.

3. Geben Sie auf der Registerkarte **Grundlagen** des Blatts **Web-App** die folgenden Einstellungen an (ersetzen Sie **xxxx** im Namen der Web-App durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Behalten Sie ansonsten die Standardeinstellungen bei, auch für den App Service-Plan. 

    | Einstellung | Wert |
    | -- | -- |
    | Subscription | **Standarddaten verwenden** |
    | Ressourcengruppe | **Neue Ressourcengruppe erstellen**|
    | Name | **myDockerWebAppxxxx** |
    | Veröffentlichen | **Docker-Container** |
    | Betriebssystem | **Linux** |
    | Region | **USA, Osten** |
    
    **Hinweis:** Denken Sie daran, **xxxx** so zu ändern, dass der Name Ihrer Web-App eindeutig ist.

4. Klicken Sie auf **Weiter > Docker**, und konfigurieren Sie die Containerinformationen.  

    | Einstellung | Wert |
    | -- | -- |
    | Optionen | **Einzelner Container** |
    | Imagequelle | **Docker Hub** |
    | Zugriffstyp | **Public** |
    | Image und Tag | **mcr.microsoft.com/azuredocs/aci-helloworld** |
    
 **Hinweis:** Der Startupbefehl ist optional und wird in dieser Übung nicht benötigt.

5. Klicken Sie auf **Überprüfen und erstellen** und dann auf **Erstellen**. 

# <a name="task-2-test-the-web-app"></a>Aufgabe 2: Testen der Web-App

In dieser Aufgabe testen wir die Web-App.

1. Warten Sie, bis die Web-App bereitgestellt wurde.

2. Klicken Sie in **Benachrichtigungen** auf **Zur Ressource gehen**. 

3. Suchen Sie auf dem Blatt **Überblick** den Eintrag **URL**. Kopieren Sie die URL in die Zwischenablage.

    ![Screenshot des Web-App-Eigenschaftenblatts. Die URL wird hervorgehoben.](../images/0801.png)

4. Öffnen Sie eine neue Browserregisterkarte, fügen Sie die URL ein, und drücken Sie die Eingabetaste. Die Begrüßungsmeldung „Willkommen bei Azure Container Instances!“ wird angezeigt.

    ![Screenshot der Seite „Willkommen bei Azure Container Instances“.](../images/0802.png)

5. Wechseln Sie zurück zum Blatt **Übersicht** Ihrer Web-App, und scrollen Sie nach unten. Dort sehen Sie verschiedene Diagramme mit ein- und ausgehenden Daten und Anforderungen. Wenn Sie Schritt 4 einige Male wiederholen, sollte die entsprechende Telemetrie in diesen Diagrammen angezeigt werden. Dies umfasst die Anzahl der Anforderungen und die durchschnittliche Antwortzeit. 

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.

Herzlichen Glückwunsch! Sie haben erfolgreich einen Azure App Service erstellt.
