---
wts:
  title: 01 – Erstellen eines virtuellen Computers im Portal (10 Min.)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 010d6a19a66f6ac92627720379a4eb850b2ee423
ms.sourcegitcommit: 4a0bfef63f98844f16e2a364d156e96382b8fac5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2022
ms.locfileid: "144556869"
---
# <a name="01---create-a-virtual-machine-in-the-portal-10-min"></a>01 – Erstellen eines virtuellen Computers im Portal (10 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir einen virtuellen Computer im Azure-Portal, stellen eine Verbindung zum virtuellen Computer her, installieren die Webserverrolle und testen dann. 

**Hinweis:** Nehmen Sie sich bei dieser exemplarischen Vorgehensweise die Zeit, auf die Informationssymbole zu klicken und diese zu lesen. 

# <a name="task-1-create-the-virtual-machine"></a>Aufgabe 1: Erstellen des virtuellen Computers 
1. Melden Sie sich beim Azure-Portal an: **https://portal.azure.com**

3. Suchen Sie auf dem Blatt **Alle Dienste** im Portalmenü nach **Virtuelle Computer**, und wählen Sie die Option aus. Klicken Sie dann auf **+Hinzufügen**, und wählen Sie **+Virtueller Azure-Computer** im Dropdownfeld aus.

4. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellungen | Werte |
    |  -- | -- |
    | Subscription | **Standarddaten verwenden** |
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Name des virtuellen Computers | **myVM** |
    | Region | **(USA) USA, Osten**|
    | Verfügbarkeitsoptionen | Keine Optionen für die Infrastrukturredundanz erforderlich|
    | Image | **Windows Server 2019 Datacenter, Gen2**|
    | Size | **Standard D2s v3**|
    | Benutzername des Administratorkontos | **azureuser** |
    | Kennwort für das Administratorkonto (sorgfältig eingeben!) | **Pa$$w0rd1234**|
    | Regeln für eingehende Ports – | **Ausgewählte Ports zulassen**|
    | Eingangsports auswählen | **RDP (3389)** und **HTTP (80)**| 

5. Wechseln Sie zur Registerkarte „Netzwerk“, und vergewissern Sie sich, dass **HTTP (80) und RDP (3389)** im Abschnitt **Eingangsports auswählen** ausgewählt sind.

6. Wechseln Sie zur Registerkarte „Verwaltung“, und wählen Sie im Abschnitt **Überwachung** die folgende Einstellung aus:

    | Einstellungen | Werte |
    | -- | -- |
    | Startdiagnose | **Deaktivieren**|

7. Übernehmen Sie die Standardwerte für die restlichen Einstellungen, und klicken Sie dann auf die Schaltfläche **Überprüfen + erstellen** am unteren Rand der Seite.

8. Sobald die Validierung bestanden ist, klicken Sie auf die Schaltfläche **Erstellen**. Die Bereitstellung des virtuellen Computers kann zwischen fünf und sieben Minuten dauern.

9. Sie erhalten Updates auf der Bereitstellungsseite und im Bereich **Benachrichtigungen** (Glockensymbol in der oberen Menüleiste).

# <a name="task-2-connect-to-the-virtual-machine"></a>Aufgabe 2: Herstellen einer Verbindung mit dem virtuellen Computer

In dieser Aufgabe stellen wir per RDP (Remotedesktopprotokoll) eine Verbindung zu unserem neuen virtuellen Computer her. 

1. Klicken Sie oben in der blauen Symbolleiste auf das Glockensymbol, und wählen Sie „Zu Ressource wechseln“ aus, nachdem die Bereitstellung erfolgreich abgeschlossen wurde. 

    **Hinweis:** Sie können auch den Link **Zu Ressource wechseln** auf der Bereitstellungsseite verwenden. 

2. Klicken Sie auf dem Blatt **Überblick** des virtuellen Computers auf die Schaltfläche **Verbinden**, und wählen Sie **RDP** im Dropdownfeld aus.

    ![Screenshot der Eigenschaften des virtuellen Computers mit hervorgehobener Schaltfläche „Verbinden“.](../images/0101.png)

    **Hinweis:** In den folgenden Anweisungen erfahren Sie, wie Sie von einem Windows-Computer aus eine Verbindung zu Ihrem virtuellen Computer herstellen. Auf einem Mac benötigen Sie einen RDP-Client wie etwa den Remotedesktopclient aus dem Mac App Store. Auf Linux-Computern können Sie einen Open-Source-RDP-Client verwenden.

2. Behalten Sie auf der Seite **Verbindung mit virtuellem Computer herstellen** die Standardoptionen zum Herstellen der Verbindung mit der öffentlichen IP-Adresse über Port 3389 bei, und klicken auf **RDP-Datei herunterladen**. Auf der linken Seite des Bildschirms wird eine Datei heruntergeladen.

3. **Öffnen** Sie die heruntergeladene RDP-Datei (unten links auf Ihrem Laborcomputer), und klicken Sie auf **Verbinden**, wenn Sie dazu aufgefordert werden. 

    ![Screenshot der Eigenschaften des virtuellen Computers mit hervorgehobener Schaltfläche „Verbinden“. ](../images/0102.png)

4. Melden Sie sich im Fenster **Windows-Sicherheit** mit den Administratoranmeldeinformationen an, die Sie beim Erstellen der VM verwendet haben: Benutzer **azureuser** und Kennwort **Pa$$w0rd1234**. 

5. Möglicherweise wird bei der Anmeldung eine Zertifikatwarnung angezeigt. Klicken Sie auf **Ja**, um die Verbindung herzustellen und sich mit Ihrem bereitgestellten virtuellen Computer zu verbinden. Die Verbindung sollte erfolgreich hergestellt werden.

    ![Screenshot des Dialogfelds „Zertifikatwarnung“, in dem der Benutzer über ein nicht vertrauenswürdiges Zertifikat informiert wird, mit hervorgehobener Schaltfläche „Ja“. ](../images/0104.png)

Ein neuer virtueller Computer (myVM) wird in Ihrem Lab gestartet. Schließen Sie den Server-Manager und die geöffneten Dashboard-Fenster (klicken Sie oben rechts auf das „X“). Jetzt sollten Sie den blauen Hintergrund Ihres virtuellen Computers sehen. **Glückwunsch!** Sie haben einen virtuellen Computer mit Windows Server bereitgestellt und sich mit ihm verbunden. 

# <a name="task-3-install-the-web-server-role-and-test"></a>Aufgabe 3: Installieren und Testen der Webserverrolle

In dieser Aufgabe werden Sie die Webserverrolle auf dem soeben erstellten virtuellen Computer installieren und sicherstellen, dass die standardmäßige IIS-Begrüßungsseite angezeigt wird. 

1. Starten Sie PowerShell auf dem soeben bereitgestellten virtuellen Computer, indem Sie in der Suchleiste nach **PowerShell** suchen, mit der rechten Maustaste auf **Windows PowerShell** klicken und **Als Administrator ausführen** auswählen.

    ![Screenshot des Desktops des virtuellen Computers mit angeklickter Startschaltfläche und Auswahl von PowerShell mit „Als Administrator ausführen“ hervorgehoben.](../images/0105.png)

2. Installieren Sie das Feature **Webserver** in PowerShell auf dem virtuellen Computer, indem Sie den folgenden Befehl ausführen. (Kopieren Sie den Befehl ein und drücken Sie auf die EINGABETASTE, um mit der Installation zu beginnen.)

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. Nach Abschluss wird eine **Erfolgsmeldung** mit dem Wert **Wahr** angezeigt. Sie müssen den virtuellen Computer nicht neu starten, um die Installation abzuschließen. Schließen Sie die RDP-Verbindung zur VM, indem Sie auf das **x** in der blauen Leiste oben in der Mitte Ihres virtuellen Computers klicken. Sie können die VM auch minimieren, indem Sie auf das **-** in der blauen Leiste oben in der Mitte klicken.

    ![Screenshot der Windows PowerShell-Eingabeaufforderung mit dem erfolgreich abgeschlossenen Befehl „Install-WindowsFeature -name Web-Server -IncludeManagementTools“ und der Ausgabe, dass der Vorgang erfolgreich war.](../images/0106.png)

4. Navigieren Sie im Portal zurück zum Blatt **Überblick** für myVM, und verwenden Sie die Schaltfläche **In Zwischenablage kopieren**, um die öffentliche IP-Adresse von myVM zu kopieren. Öffnen Sie eine neue Browserregisterkarte, fügen Sie die öffentliche IP-Adresse in das URL-Textfeld ein, und drücken Sie die **Eingabetaste**, um die URL zu öffnen.

    ![Screenshot des Eigenschaftenbereichs für den virtuellen Computer im Azure-Portal mit der kopierten IP-Adresse.](../images/0107.png)

5. Die standardmäßige Begrüßungsseite des IIS-Webservers wird angezeigt.

    ![Screenshot der standardmäßigen Begrüßungsseite des IIS-Webservers, auf die über die öffentliche IP-Adresse in einem Webbrowser zugegriffen wird.](../images/0108.png)

**Glückwunsch!** Sie haben eine neue VM erstellt, die über ihre öffentliche IP-Adresse erreichbar ist. Wenn Sie eine Webanwendung hosten müssen, können Sie Anwendungsdateien auf dem virtuellen Computer bereitstellen und sie für öffentlichen Zugriff auf dem bereitgestellten virtuellen Computer hosten.


**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu überprüfen, ob der Löschvorgang erfolgreich abgeschlossen wurde. 
