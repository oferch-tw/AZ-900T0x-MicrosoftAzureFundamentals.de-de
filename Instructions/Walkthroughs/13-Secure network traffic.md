---
wts:
  title: 13 – Sicherer Netzwerkdatenverkehr (10 Min.)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="13---secure-network-traffic-10-min"></a>13 – Sicherer Netzwerkdatenverkehr (10 Min.)

In dieser Anleitung konfigurieren wir eine Netzwerksicherheitsgruppe.

# <a name="task-1-create-a-virtual-machine"></a>Aufgabe 1: Erstellen einer VM

In dieser Aufgabe erstellen wir einen virtuellen Windows Server 2019 Datacenter-Computer. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Computer**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**.

3. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellungen | Werte |
    |  -- | -- |
    | Subscription | **Standardeinstellung verwenden** |
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Name des virtuellen Computers | **SimpleWinVM** |
    | Region | **(USA) USA, Osten**|
    | Image | **Windows Server 2019 Datacenter, Gen2**|
    | Size | **Standard D2s v3**|
    | Benutzername des Administratorkontos | **azureuser** |
    | Kennwort für das Administratorkonto | **Pa$$w0rd1234**|
    | Regeln für eingehende Ports | **None**|

4. Wechseln Sie zur Registerkarte **Netzwerk**, und konfigurieren Sie die folgende Einstellung:

    | Einstellungen | Werte |
    | -- | -- |
    | NIC-Netzwerksicherheitsgruppe | **None**|

5. Wechseln Sie zur Registerkarte **Verwaltung**, und wählen Sie im Abschnitt **Überwachung** die folgende Einstellung aus:

    | Einstellungen | Werte |
    | -- | -- |
    | Startdiagnose | **Deaktivieren**|

6. Übernehmen Sie die verbleibenden Standardeinstellungen, und klicken Sie dann auf die Schaltfläche **Überprüfen + erstellen** am unteren Rand der Seite.

7. Once Validation is passed click the <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> button. It can take about five minutes to deploy the virtual machine.

8. Monitor the deployment. It may take a few minutes for the resource group and virtual machine to be created. 

9. Klicken Sie im Bereitstellungsblatt oder im Infobereich auf **Zu Ressource wechseln**. 

10. Klicken Sie auf dem Blatt **SimpleWinVM** des virtuellen Computers auf **Netzwerk**, und überprüfen Sie die Registerkarte **Regeln für eingehende Ports**. Beachten Sie, dass der Netzwerkschnittstelle des virtuellen Computers oder dem Subnetz, an das die Netzwerkschnittstelle angeschlossen ist, keine Netzwerksicherheitsgruppe zugeordnet ist.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Identify the name of the network interface. You will need it in the next task.

# <a name="task-2-create-a-network-security-group"></a>Aufgabe 2: Erstellen einer Netzwerksicherheitsgruppe

In dieser Aufgabe erstellen wir eine Netzwerksicherheitsgruppe und ordnen sie der Netzwerkschnittstelle zu. 

1. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Netzwerksicherheitsgruppen**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**.

2. Geben Sie die folgenden Einstellungen auf der Registerkarte **Grundlagen** des Blatts **Netzwerksicherheitsgruppe erstellen** an.

    | Einstellung | Wert |
    | -- | -- |
    | Subscription | **Standardabonnement verwenden** |
    | Resource group | **Standard im Dropdownfeld auswählen** |
    | Name | **myNSGSecure** |
    | Region | **(USA) USA, Osten**  |

3. Klicken Sie auf **Überprüfen + erstellen** und nach der Validierung auf **Erstellen**.

4. Klicken Sie nach dem Erstellen des NSG auf **Zu Ressource wechseln**.

5. Klicken Sie unter **Einstellungen** auf **Netzwerkschnittstellen** und dann auf **Zuordnen**.

6. Wählen Sie die in der vorherigen Aufgabe identifizierte Netzwerkschnittstelle aus. 

# <a name="task-3-configure-an-inbound-security-port-rule-to-allow-rdp"></a>Aufgabe 3: Konfigurieren einer Sicherheitsregel für eingehende Ports zum Zulassen von RDP

In dieser Aufgabe lassen Sie RDP-Datenverkehr für den virtuellen Computer zu, indem Sie eine eingehende Sicherheitsportregel konfigurieren. 

1. Navigieren Sie im Azure-Portal zum Blatt des virtuellen Computers **SimpleWinVM**. 

2. Klicken Sie im Bereich **Übersicht** auf **Verbinden**.

3. Attempt to connect to the virtual machine by selecting RDP and downloading an running the RDP file. By default the network security group does not allow RDP. Close the error window. 


    ![Screenshot der Fehlermeldung, die besagt, dass die Verbindung zum virtuellen Computer fehlgeschlagen ist.](../images/1201.png)

4. Scrollen Sie auf dem Blatt des virtuellen Computers nach unten zum Abschnitt **Einstellungen**, und klicken Sie auf **Netzwerk**. Beachten Sie, dass die Eingangsregeln für die Netzwerksicherheitsgruppe **myNSGSecure (angeschlossen an Netzwerkschnittstelle: myVMNic)** den gesamten eingehenden Datenverkehr mit Ausnahme des Datenverkehrs innerhalb des virtuellen Netzwerks und der Lastenausgleichstests verweigern.

5. On the <bpt id="p1">**</bpt>Inbound port rules<ept id="p1">**</ept> tab, click <bpt id="p2">**</bpt>Add inbound port rule<ept id="p2">**</ept> . Click <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> when you are done. 

    | Einstellung | Wert |
    | -- | -- |
    | `Source` | **Alle**|
    | Source port ranges | **\*** |
    | Destination | **Alle** |
    | Zielportbereiche | **3389** |
    | Protokoll | **TCP** |
    | Aktion | **Zulassen** |
    | Priorität | **300** |
    | Name | **AllowRDP** |

6. Select <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> and wait for the rule to be provisioned and then try again to RDP into the virtual machine by going back to <bpt id="p2">**</bpt>Connect<ept id="p2">**</ept> This time you should be successful. Remember the user is <bpt id="p1">**</bpt>azureuser<ept id="p1">**</ept> and the password is <bpt id="p2">**</bpt>Pa$$w0rd1234<ept id="p2">**</ept>.

# <a name="task-4-configure-an-outbound-security-port-rule-to-deny-internet-access"></a>Aufgabe 4: Konfigurieren einer Sicherheitsregel für ausgehende Ports zum Verweigern des Internetzugriffs

In dieser Aufgabe erstellen wir eine NSG-Regel für ausgehende Ports, die den Internetzugriff verweigert, und testen dann, ob die Regel funktioniert.

1. Fahren Sie in der RDP-Sitzung Ihres virtuellen Computers fort. 

2. Öffnen Sie nach dem Start des Computers den **Internet Explorer**-Browser. 

3. Verify that you can access <bpt id="p1">**</bpt><ph id="ph1">https://www.bing.com</ph><ept id="p1">**</ept> and then close Internet Explorer. You will need to work through the IE enhanced security pop-ups. 

    **Hinweis:** Wir konfigurieren nun eine Regel, um den ausgehenden Internetzugang zu verweigern. 

4. Kehren Sie zum Azure-Portal zurück, und navigieren Sie zum Blatt des virtuellen Computers **SimpleWinVM**. 

5. Klicken Sie unter **Einstellungen** auf **Netzwerk** und dann auf **Regeln für ausgehende Ports**.

6. Notice there is a rule, <bpt id="p1">**</bpt>AllowInternetOutbound<ept id="p1">**</ept>. This a default rule and cannot be removed. 

7. Click <bpt id="p1">**</bpt>Add outbound port rule<ept id="p1">**</ept> to the right of the <bpt id="p2">**</bpt>myNSGSecure  (attached to network interface: myVMNic)<ept id="p2">**</ept> network security group and configure a new outbound security rule with a higher priority that will deny internet traffic. Click <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> when you are finished. 

    | Einstellung | Wert |
    | -- | -- |
    | `Source` | **Alle**|
    | Source port ranges | **\*** |
    | Destination | **Diensttag** |
    | Zieldiensttag | **Internet** |
    | Zielportbereiche | **\*** |
    | Protocol | **TCP** |
    | Aktion | **Deny** (Verweigern) |
    | Priority | **4000** |
    | Name | **DenyInternet** |

8. Klicken Sie auf **Hinzufügen**. Kehren Sie zur VM zurück, mit der Sie per RDP verbunden sind. 

9. Browse to <bpt id="p1">**</bpt><ph id="ph1">https://www.microsoft.com</ph><ept id="p1">**</ept>. The page should not display. You may need to work through additional IE enhanced security pop-ups.  

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
