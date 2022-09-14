---
wts:
  title: 01 – Erstellen eines virtuellen Computers im Portal (10 Min.)
  module: Module 02 - Core Azure Services (Workloads)
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

8. Once Validation is passed click the <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> button. It can take anywhere from five to seven minutes to deploy the virtual machine.

9. Sie erhalten Updates auf der Bereitstellungsseite und im Bereich **Benachrichtigungen** (Glockensymbol in der oberen Menüleiste).

# <a name="task-2-connect-to-the-virtual-machine"></a>Aufgabe 2: Herstellen einer Verbindung mit dem virtuellen Computer

In dieser Aufgabe stellen wir per RDP (Remotedesktopprotokoll) eine Verbindung zu unserem neuen virtuellen Computer her. 

1. Klicken Sie oben in der blauen Symbolleiste auf das Glockensymbol, und wählen Sie „Zu Ressource wechseln“ aus, nachdem die Bereitstellung erfolgreich abgeschlossen wurde. 

    **Hinweis:** Sie können auch den Link **Zu Ressource wechseln** auf der Bereitstellungsseite verwenden. 

2. Klicken Sie auf dem Blatt **Überblick** des virtuellen Computers auf die Schaltfläche **Verbinden**, und wählen Sie **RDP** im Dropdownfeld aus.

    ![Screenshot der Eigenschaften des virtuellen Computers mit hervorgehobener Schaltfläche „Verbinden“.](../images/0101.png)

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The following directions tell you how to connect to your VM from a Windows computer. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store and on a Linux computer you can use an open source RDP client.

2. On the <bpt id="p1">**</bpt>Connect to virtual machine<ept id="p1">**</ept> page, keep the default options to connect with the public IP address over port 3389 and click <bpt id="p2">**</bpt>Download RDP File<ept id="p2">**</ept>. A file will download on the bottom left of your screen.

3. **Öffnen** Sie die heruntergeladene RDP-Datei (unten links auf Ihrem Laborcomputer), und klicken Sie auf **Verbinden**, wenn Sie dazu aufgefordert werden. 

    ![Screenshot der Eigenschaften des virtuellen Computers mit hervorgehobener Schaltfläche „Verbinden“. ](../images/0102.png)

4. Melden Sie sich im Fenster **Windows-Sicherheit** mit den Administratoranmeldeinformationen an, die Sie beim Erstellen der VM verwendet haben: Benutzer **azureuser** und Kennwort **Pa$$w0rd1234**. 

5. You may receive a warning certificate during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> or to create the connection and connect to your deployed VM. You should connect successfully.

    ![Screenshot des Dialogfelds „Zertifikatwarnung“, in dem der Benutzer über ein nicht vertrauenswürdiges Zertifikat informiert wird, mit hervorgehobener Schaltfläche „Ja“. ](../images/0104.png)

A new Virtual Machine (myVM) will launch inside your Lab. Close the Server Manager and dashboard windows that pop up (click "x" at top right). You should see the blue background of your virtual machine. <bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have deployed and connected to a Virtual Machine running Windows Server. 

# <a name="task-3-install-the-web-server-role-and-test"></a>Aufgabe 3: Installieren und Testen der Webserverrolle

In dieser Aufgabe werden Sie die Webserverrolle auf dem soeben erstellten virtuellen Computer installieren und sicherstellen, dass die standardmäßige IIS-Begrüßungsseite angezeigt wird. 

1. Starten Sie PowerShell auf dem soeben bereitgestellten virtuellen Computer, indem Sie in der Suchleiste nach **PowerShell** suchen, mit der rechten Maustaste auf **Windows PowerShell** klicken und **Als Administrator ausführen** auswählen.

    ![Screenshot des Desktops des virtuellen Computers mit angeklickter Startschaltfläche und Auswahl von PowerShell mit „Als Administrator ausführen“ hervorgehoben.](../images/0105.png)

2. In PowerShell, install the <bpt id="p1">**</bpt>Web-Server<ept id="p1">**</ept> feature on the virtual machine by running the following command. (Paste in the command and hit ENTER for the installment to begin).

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. When completed, a prompt will state <bpt id="p1">**</bpt>Success<ept id="p1">**</ept> with a value <bpt id="p2">**</bpt>True<ept id="p2">**</ept>. You do not need to restart the virtual machine to complete the installation. Close the RDP connection to the VM by clicking the <bpt id="p1">**</bpt>x<ept id="p1">**</ept> on the blue bar at the top center of your virtual machine. You can also minimize it by clicking the <bpt id="p1">**</bpt><ph id="ph1">-</ph><ept id="p1">**</ept> on the blue bar at the top center.

    ![Screenshot der Windows PowerShell-Eingabeaufforderung mit dem erfolgreich abgeschlossenen Befehl „Install-WindowsFeature -name Web-Server -IncludeManagementTools“ und der Ausgabe, dass der Vorgang erfolgreich war.](../images/0106.png)

4. Navigieren Sie im Portal zurück zum Blatt **Überblick** für myVM, und verwenden Sie die Schaltfläche **In Zwischenablage kopieren**, um die öffentliche IP-Adresse von myVM zu kopieren. Öffnen Sie eine neue Browserregisterkarte, fügen Sie die öffentliche IP-Adresse in das URL-Textfeld ein, und drücken Sie die **Eingabetaste**, um die URL zu öffnen.

    ![Screenshot des Eigenschaftenbereichs für den virtuellen Computer im Azure-Portal mit der kopierten IP-Adresse.](../images/0107.png)

5. Die standardmäßige Begrüßungsseite des IIS-Webservers wird angezeigt.

    ![Screenshot der standardmäßigen Begrüßungsseite des IIS-Webservers, auf die über die öffentliche IP-Adresse in einem Webbrowser zugegriffen wird.](../images/0108.png)

<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have created a new VM running a web server that is accessible via its public IP address. If you had a web application to host, you could deploy application files to the virtual machine and host them for public access on the deployed virtual machine.


<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see verify that the deletion completed successfully. 
