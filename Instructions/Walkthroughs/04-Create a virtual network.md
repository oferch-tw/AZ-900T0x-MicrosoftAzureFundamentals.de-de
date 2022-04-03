---
wts:
  title: 04 – Erstellen eines virtuellen Netzwerks (20 Min.)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 08aafa461c0facc43e735bd81ba97aa9650952fa
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907798"
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
    
   
4. Klicken Sie auf **Überprüfen + erstellen**. Stellen Sie sicher, dass die Validierung erfolgreich ist. Klicken Sie anschließend auf „erstellen“, um die Ressource bereitzustellen.


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
   

3. Wählen Sie die Registerkarte **Netzwerk** aus. Stellen Sie sicher, dass sich der virtuelle Computer im virtuellen Netzwerk **vnet1** befindet. Überprüfen Sie die Standardeinstellungen, nehmen Sie jedoch keine weiteren Änderungen vor. 

4. Klicken Sie auf **Überprüfen + erstellen**. Klicken Sie nach Abschluss der Validierung auf **Erstellen**. Die Bereitstellungszeiten können variieren, die Bereitstellung kann jedoch im Allgemeinen zwischen drei und sechs Minuten dauern.

5. Überwachen Sie Ihre Bereitstellung, fahren Sie jedoch mit dem nächsten Schritt fort. 

6. Erstellen Sie einen zweiten virtuellen Computer, indem Sie die oben genannten Schritte **2 bis 4** wiederholen. Stellen Sie sicher, dass Sie einen anderen Namen für den virtuellen Computer verwenden, dass sich der virtuelle Computer im selben virtuellen Netzwerk befindet und dass er eine neue öffentliche IP-Adresse verwendet:

    | Einstellung | Wert |
    | --- | --- |
    | Resource group | **Standard in Dropdownmenü auswählen (wie bei Aufgabe 1-3 und Aufgabe 2-2)** |
    | Name des virtuellen Computers |  **VM2** |
    | Virtuelles Netzwerk | **vnet1** |
    | Öffentliche IP-Adresse | **vm2-ip** |

7. Warten Sie, bis beide virtuelle Computer bereitgestellt wurden und der Status als *Wird ausgeführt* angezeigt wird.

# <a name="task-3-test-the-connection"></a>Aufgabe 3: Testen der Verbindung 

In dieser Aufgabe werden testen, ob die virtuellen Computer miteinander kommunizieren (pingen) können. Falls nicht, werden wir eine Regel erstellen, um die ICMP-Verbindung zu erlauben. ICMP-Verbindungen werden normalerweise automatisch blockiert.

1. Suchen Sie auf dem Blatt **Alle Ressourcen** nach **vm1**, öffnen Sie das zugehörige Blatt **Übersicht**, und stellen Sie sicher, dass für **Status** **Wird ausgeführt** angezeigt wird. Möglicherweise müssen Sie die Seite **aktualisieren**.

2. Wählen Sie auf dem Blatt **Übersicht** die Option **Verbinden** aus, und wählen Sie dann **RDP** im Dropdownfeld aus.

    **Hinweis:** In den folgenden Anweisungen erfahren Sie, wie Sie von einem Windows-Computer aus eine Verbindung zu Ihrem virtuellen Computer herstellen. 

3. Behalten Sie auf dem Blatt **Verbindung herstellen über RDP** die Standardoptionen für die Verbindung per IP-Adresse über Port 3389 bei, und klicken Sie auf **RDP-Datei herunterladen**.

4. Öffnen Sie die heruntergeladene RDP-Datei (unten links in Ihrer VM), und klicken Sie auf **Verbinden**, wenn Sie dazu aufgefordert werden. 

5. Geben Sie im Fenster **Windows-Sicherheit** den Benutzernamen **azureuser** und das Kennwort **Pa$$$w0rd1234** ein, und klicken Sie dann auf **OK**.

6. Während des Anmeldevorgangs wird unter Umständen eine Zertifikatwarnung angezeigt. Klicken Sie auf **Ja**, um die Verbindung herzustellen und sich mit Ihrem bereitgestellten virtuellen Computer zu verbinden. Die Verbindung sollte erfolgreich hergestellt werden. Schließen Sie den Windows Server und die geöffneten Dashboard-Fenster. Jetzt sollte ein blauer Windows-Hintergrund angezeigt werden. Sie befinden sich jetzt auf Ihrem virtuellen Computer.

7. Stellen Sie auf **beiden** neu erstellten virtuellen Computern über RDP eine Verbindung her, und deaktivieren Sie die öffentliche und die private Firewall, indem Sie die „Startmenü > Einstellungen > Netzwerk und Internet-> Windows-Firewall“ öffnen.

8. Öffnen Sie PowerShell auf dem virtuellen Computer, indem Sie auf die Schaltfläche **Start** klicken, **PowerShell** in das Suchfeld eingeben, mit der rechten Maustaste auf **Windows PowerShell** klicken und **Als Administrator ausführen** auswählen.

9. Senden Sie in PowerShell einen Ping an vm2, indem Sie Folgendes eingeben:

   ```PowerShell
   ping vm2
   ```

 10. Der Ping sollte erfolgreich sein. Sie haben einen Ping von vm1 an vm2 gesendet.


**Glückwunsch!** Sie haben zwei virtuelle Computer in einem virtuellen Netzwerk bereitgestellt und eine Verbindung zwischen den Computern hergestellt.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
