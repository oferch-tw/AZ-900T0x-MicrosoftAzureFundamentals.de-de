---
wts:
  title: 04 – Erstellen eines virtuellen Netzwerks (20 Min.)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="04---create-a-virtual-network-20-min"></a>04 – Erstellen eines virtuellen Netzwerks (20 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir ein virtuelles Netzwerk, stellen zwei virtuelle Computer in diesem virtuellen Netzwerk bereit, und konfigurieren sie dann so, dass die virtuellen Computer einander innerhalb des virtuellen Netzwerks pingen können.

# <a name="task-1-create-a-virtual-network"></a>Aufgabe 1: Erstellen eines virtuellen Netzwerks 

In dieser Aufgabe erstellen wir ein virtuelles Netzwerk. 

Hinweis: Deaktivieren Sie vor Beginn des Labs sowohl die öffentliche als auch die private Firewall auf Ihrem virtuellen Computer, indem Sie „Startmenü > Einstellungen > Netzwerk und Internet > Windows-Firewall“ öffnen.

1. Melden Sie sich unter <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a> beim Azure-Portal an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Virtuelle Netzwerke**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**. 

3. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellung | Wert | 
    | --- | --- |
    | Subscription | **Standarddaten beibehalten** |
    | Ressourcengruppe | **Neue Ressourcengruppe erstellen** |
    | Name | **vnet1** |
    | Region | **(USA) USA, Osten** |
    
   
4. Click the <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> button. Ensure the validation passes. Then hit create to deploy the resource.


# <a name="task-2-create-two-virtual-machines"></a>Aufgabe 2: Erstellen von zwei virtuellen Computern

In dieser Aufgabe erstellen wir zwei virtuelle Computer im virtuellen Netzwerk. 

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Virtuelle Computer**, klicken Sie auf **+ Hinzufügen, +Erstellen, +Neu**, und wählen Sie **Virtueller Computer** im Dropdownfeld aus. 

2. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

   | Einstellung | Wert | 
   | --- | --- |
   | Subscription | **Standarddaten verwenden** |
   | Resource group |  **Standard in Dropdownfeld auswählen** |
   | Name des virtuellen Computers | **vm1**|
   | Region | **(USA) USA, Osten** |
   | Image | **Windows Server 2019 Datacenter, Gen2** |
   | Username| **azureuser** |
   | Kennwort| **Pa$$w0rd1234** |
   | Öffentliche Eingangsports| Wählen Sie **Ausgewählte Ports zulassen** aus.  |
   | Ausgewählte eingehende Ports| **RDP (3389)** |
   

3. Select the <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> tab. Make sure the virtual machine is placed in the <bpt id="p2">**</bpt>vnet1<ept id="p2">**</ept> virtual network. Review the default settings, but do not make any other changes. 

4. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>. After the Validation passes, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Deployment times can vary but it can generally take between three to six minutes to deploy.

5. Überwachen Sie Ihre Bereitstellung, fahren Sie jedoch mit dem nächsten Schritt fort. 

6. Create a second virtual machine by repeating steps <bpt id="p1">**</bpt>2 to 4<ept id="p1">**</ept> above. Make sure you use a different virtual machine name, that the virtual machine is in the same virtual network, and is using a new public IP address:

    | Einstellung | Wert |
    | --- | --- |
    | Resource group | **Standard in Dropdownmenü auswählen (wie bei Aufgabe 1-3 und Aufgabe 2-2)** |
    | Name des virtuellen Computers |  **VM2** |
    | Virtuelles Netzwerk | **vnet1** |
    | Öffentliche IP-Adresse | **vm2-ip** |

7. Warten Sie, bis beide virtuelle Computer bereitgestellt wurden und der Status als *Wird ausgeführt* angezeigt wird.

# <a name="task-3-test-the-connection"></a>Aufgabe 3: Testen der Verbindung 

In this task, we will try to test whether the virtual machines can communicate (ping) each other. If not we will install a rule to allow an ICMP connection. Usually ICMP connections are automatically blocked.

1. From the <bpt id="p1">**</bpt>All resources<ept id="p1">**</ept> blade, search for <bpt id="p2">**</bpt>vm1<ept id="p2">**</ept>, open its <bpt id="p3">**</bpt>Overview<ept id="p3">**</ept> blade, and make sure its <bpt id="p4">**</bpt>Status<ept id="p4">**</ept> is <bpt id="p5">**</bpt>Running<ept id="p5">**</ept>. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

2. Wählen Sie auf dem Blatt **Übersicht** die Option **Verbinden** aus, und wählen Sie dann **RDP** im Dropdownfeld aus.

    **Hinweis:** In den folgenden Anweisungen erfahren Sie, wie Sie von einem Windows-Computer aus eine Verbindung zu Ihrem virtuellen Computer herstellen. 

3. Behalten Sie auf dem Blatt **Verbindung herstellen über RDP** die Standardoptionen für die Verbindung per IP-Adresse über Port 3389 bei, und klicken Sie auf **RDP-Datei herunterladen**.

4. Öffnen Sie die heruntergeladene RDP-Datei (unten links in Ihrer VM), und klicken Sie auf **Verbinden**, wenn Sie dazu aufgefordert werden. 

5. Geben Sie im Fenster **Windows-Sicherheit** den Benutzernamen **azureuser** und das Kennwort **Pa$$$w0rd1234** ein, und klicken Sie dann auf **OK**.

6. You may receive a certificate warning during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> to create the connection and connect to your deployed VM. You should connect successfully. Close the Windows Server and Dashboard windows that pop up. You should see a Blue Windows background. You are now in your virtual machine.

7. Stellen Sie auf **beiden** neu erstellten virtuellen Computern über RDP eine Verbindung her, und deaktivieren Sie die öffentliche und die private Firewall, indem Sie die „Startmenü > Einstellungen > Netzwerk und Internet-> Windows-Firewall“ öffnen.

8. Öffnen Sie PowerShell auf dem virtuellen Computer, indem Sie auf die Schaltfläche **Start** klicken, **PowerShell** in das Suchfeld eingeben, mit der rechten Maustaste auf **Windows PowerShell** klicken und **Als Administrator ausführen** auswählen.

9. Senden Sie in PowerShell einen Ping an vm2, indem Sie Folgendes eingeben:

   ```PowerShell
   ping vm2
   ```

 10. You should be successful. You have pinged VM2 from VM1.


<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have configured and deployed two virtual machines in a virtual network, and then you were able to connect them.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
