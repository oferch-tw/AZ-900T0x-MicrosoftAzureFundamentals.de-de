---
wts:
    title: '04 - Erstellen eines virtuellen Netzwerks (20 Min.)'
    module: 'Modul 02 - Azure-Kerndienste (Workloads)'
---
# 04 – Erstellen eines virtuellen Netzwerks (20 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir ein virtuelles Netzwerk, stellen zwei virtuelle Computer in diesem virtuellen Netzwerk bereit und konfigurieren sie dann so, dass ein virtueller Computer den anderen innerhalb dieses virtuellen Netzwerks pingen kann.

# Aufgabe 1: Erstellen eines virtuellen Netzwerks 

In dieser Aufgabe erstellen wir ein virtuelles Netzwerk. 

Hinweis: Bevor Sie mit dem Lab beginnen, deaktivieren Sie sowohl den öffentlichen als auch den privaten Firewall auf Ihrem virtuellen Computer, indem Sie „Startmenü“ > „Einstellungen“ > „Netzwerk und Internet“ > „Windows Firewall suchen“ öffnen.

1. Melden Sie sich beim Azure-Portal an unter: <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Virtuelle Netzwerke**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**. 

3. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Standardwert verwenden** |
    | Ressourcengruppe | **Erstellen einer neuen Ressourcengruppe** |
    | Name | **vnet1** |
    | Region | **(USA) USA, Osten** |
    
   
4. Klicken Sie auf die Schaltfläche **Überprüfen + erstellen**. Stellen Sie sicher, dass die Validierung erfolgreich ist. Klicken Sie anschließend auf „erstellen“, um die Ressource bereitzustellen.


# Aufgabe 2: Erstellen von zwei virtuellen Computern

In dieser Aufgabe erstellen wir zwei virtuelle Computer im virtuellen Netzwerk. 

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Virtuelle Computer**, klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**, und wählen Sie **+ Virtueller Computer** im Dropdownfeld aus. 

2. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

   | Einstellung | Wert | 
   | --- | --- |
   | Abonnement | **Standardwert verwenden** |
   | Ressourcengruppe |  **Standard im Dropdownfeld auswählen** |
   | Name des virtuellen Computers | **vm1**|
   | Region | **(USA) USA, Osten** |
   | Bild | **Windows Server 2019 Datacenter – Gen2** |
   | Benutzername| **azureuser** |
   | Kennwort| **Pa$$w0rd1234** |
   | Öffentliche eingehende Ports| Wählen Sie **Ausgewählte Ports zulassen** aus  |
   | Ausgewählte eingehende Ports| **RDP (3389)** |
   

3. Wählen Sie die Registerkarte **Netzwerk** aus. Vergewissern sie sich, dass sich der virtuelle Computer im virtuellen Netzwerk **vnet1** befindet. Überprüfen Sie die Standardeinstellungen, nehmen Sie jedoch keine weiteren Änderungen vor. 

4. Klicken Sie auf **Überprüfen + erstellen**. Klicken Sie nach Abschluss der Validierung auf **Erstellen**. Die Bereitstellungszeiten können variieren, die Bereitstellung kann jedoch im Allgemeinen zwischen drei und sechs Minuten dauern.

5. Überwachen Sie Ihre Bereitstellung, fahren Sie jedoch mit dem nächsten Schritt fort. 

6. Erstellen Sie einen zweiten virtuellen Computer, indem Sie die oben genannten Schritte **2 bis 4** wiederholen. Achten Sie darauf, dass der virtuelle Computer einen anderen Namen hat, sich im gleichen virtuellen Netzwerk befindet und eine neue öffentliche IP-Adresse verwendet:

    | Einstellung | Wert |
    | --- | --- |
    | Ressourcengruppe | **Standard in Dropdownfeld auswählen (wie bei Aufgabe 1-3 und Aufgabe 2-2)** |
    | Name des virtuellen Computers |  **vm2** |
    | Virtuelles Netzwerk | **vnet1** |
    | Öffentliche IP-Adresse | **vm2-ip** |

7. Warten Sie, bis beide virtuelle Computer bereitgestellt wurden und mit dem Status *Wird ausgeführt* angezeigt werden.

# Aufgabe 3: Testen der Verbindung 

In dieser Aufgabe überprüfen wir mit einem Ping, ob die virtuellen Computer miteinander kommunizieren können. Falls nicht, werden wir eine Regel installieren, um eine ICMP-Verbindung zu erlauben. ICMP-Verbindungen werden normalerweise automatisch blockiert.

1. Suchen Sie auf dem Blatt **Alle Ressourcen** nach **vm1**, öffnen Sie das zugehörige Blatt **Übersicht**, und stellen Sie sicher, dass für **Status Wird ausgeführt** angezeigt wird. Möglicherweise müssen Sie die Seite **Aktualisieren**.

2. Wählen Sie auf dem Blatt **Überblick** die Option **Verbinden** aus, und wählen Sie **RDP** im Dropdownfeld aus.

    **HINWEIS**: In den folgenden Anweisungen erfahren Sie, wie Sie von einem Windows-Computer aus eine Verbindung zu Ihrem virtuellen Computer herstellen. 

3. Übernehmen Sie auf dem Blatt **Mit RDP verbinden** die Standardoptionen, um sich mit der IP-Adresse und Port 3389 zu verbinden, und klicken Sie auf **RDP-Datei herunterladen**.

4. Öffnen Sie die heruntergeladene RDP-Datei (links unten in Ihrer VM), und klicken Sie auf **Verbinden**, wenn Sie dazu aufgefordert werden. 

5. Geben Sie im Fenster **Windows-Sicherheit** den Benutzernamen **azureuser** und das Kennwort **Pa$$w0rd1234** ein, und klicken Sie dann auf **OK**.

6. Möglicherweise erhalten Sie während des Anmeldevorgangs eine Zertifikatwarnung. Klicken Sie auf **Ja**, um die Verbindung herzustellen und sich mit Ihrer bereitgestellten VM zu verbinden. Die Verbindung sollte erfolgreich hergestellt werden. Schließen Sie den Windows Server und das Dashboard-Fenster, das geöffnet wurde. Jetzt sollte ein blauer Windows-Hintergrund angezeigt werden. Sie befinden sich jetzt auf Ihrem virtuellen Computer.

7. Deaktivieren Sie auf Ihrem neu erstellen virtuellen Computer sowohl den öffentlichen als auch den privaten Firewall, indem Sie „Startmenü“ > „Einstellungen“ > „Netzwerk und Internet“ > „Windows Firewall suchen“ öffnen.

8. Öffnen Sie PowerShell auf dem virtuellen Computer, indem Sie auf die Schaltfläche **Start** klicken, **PowerShell** in das Suchfeld eingeben, mit der rechten Maustaste auf **Windows PowerShell** klicken und **Als Administrator ausführen** auswählen.

9. Senden Sie in PowerShell einen Ping an vm2, indem Sie Folgendes eingeben:

   ```PowerShell
   ping vm2
   ```

10. Der Ping sollte erfolgreich sein. Sie haben einen Ping von vm1 an vm2 gesendet.


**Herzlichen Glückwunsch!** Sie haben zwei virtuelle Computer in einem virtuellen Netzwerk konfiguriert und bereitgestellt und eine Verbindung zwischen den Computern hergestellt.

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
