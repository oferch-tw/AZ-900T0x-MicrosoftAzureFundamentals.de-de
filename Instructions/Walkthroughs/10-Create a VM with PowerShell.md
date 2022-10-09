---
wts:
  title: 10 – Erstellen eines virtuellen Computers mithilfe von PowerShell (10 Min.)
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="10---create-a-vm-with-powershell-10-min"></a>10 – Erstellen eines virtuellen Computers mithilfe von PowerShell (10 Min.)

In dieser exemplarischen Vorgehensweise konfigurieren wir die Cloud Shell, erstellen mithilfe des Azure PowerShell-Moduls eine Ressourcengruppe und einen virtuellen Computer und überprüfen die Empfehlungen von Azure Advisor. 

# <a name="task-1-configure-the-cloud-shell"></a>Aufgabe 1: Konfigurieren der Cloud Shell 

In dieser Aufgabe konfigurieren wir Cloud Shell. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. ** Sie finden Ihre Anmeldeinformationen in der Registerkarte „Ressourcen“ (direkt neben dieser Registerkarte „Anweisungen“). **
2. Öffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

    ![Screenshot des Azure Cloud Shell-Symbols im Azure-Portal.](../images/1002.png)

3. Wenn Sie aufgefordert werden, entweder **Bash** oder **PowerShell** auszuwählen, wählen Sie **PowerShell** aus.

4. Wählen Sie auf dem Bildschirm **Für Sie wurde kein Speicher bereitgestellt** die Option **Erweiterte Einstellungen anzeigen** aus, und geben Sie die folgenden Informationen ein.

    | Einstellungen | Werte |
    |  -- | -- |
    | Ressourcengruppe | **Neue Ressourcengruppe erstellen** |
    | Speicherkonto (Erstellen Sie ein neues Konto mit einem global eindeutigen Namen, z. B. cloudshellstoragemystorage) | **cloudshellxxxxxxx** |
    | Dateifreigabe (neu erstellen) | **shellstorage** |

5. Wählen Sie **Speicher erstellen** aus.

# <a name="task-2-create-a-resource-group-and-virtual-machine"></a>Aufgabe 2: Erstellen einer Ressourcengruppe und eines virtuellen Computers

In dieser Aufgabe erstellen Sie mithilfe von PowerShell eine Ressourcengruppe und einen virtuellen Computer.  

1. Stellen Sie sicher, dass im Dropdownmenü oben links im Cloud Shell-Bereich der Eintrag **PowerShell** ausgewählt ist.

2. Überprüfen Sie Ihre neue Ressourcengruppe, indem Sie den folgenden Befehl im PowerShell-Fenster ausführen. Drücken Sie die **Eingabetaste**, um den Befehl auszuführen.

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

3. Erstellen Sie einen virtuellen Computer, indem Sie den folgenden Befehl im Terminalfenster einfügen. 

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```
    
4. Wenn Sie dazu aufgefordert werden, geben Sie den Benutzernamen (**azureuser**) und das Kennwort (**Pa$$w0rd1234**) an, die als lokales Administratorkonto auf diesen virtuellen Computern konfiguriert werden.

5. Warten Sie, bis die VM erstellt wurde, und schließen Sie den Cloud Shell-Bereich der PowerShell-Sitzung.

6. Suchen Sie im Azure-Portal nach **Virtuelle Computer**, und überprüfen Sie, ob **myVMPS** ausgeführt wird. Dies kann einige Minuten dauern.

    ![Screenshot der Seite „Virtuelle Computer“, wobei myVMPS ausgeführt wird.](../images/1001.png)

7. Greifen Sie auf den neuen virtuellen Computer zu, und überprüfen Sie die Einstellungen für „Übersicht“ und „Netzwerk“, um sicherzustellen, dass Ihre Informationen korrekt bereitgestellt wurden. 

# <a name="task-3-execute-commands-in-the-cloud-shell"></a>Aufgabe 3: Ausführen von Befehlen in Cloud Shell

In dieser Aufgabe üben wir das Ausführen von PowerShell-Befehlen aus der Cloud Shell. 

1. Öffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

2. Stellen Sie sicher, dass im Dropdownmenü oben links im Cloud Shell-Bereich der Eintrag **PowerShell** ausgewählt ist.

3. Rufen Sie Informationen zu Ihrem virtuellen Computer ab, einschließlich Name, Ressourcengruppe, Standort und Status. Beachten Sie, dass der Energiestatus **Wird ausgeführt** lautet.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. Beenden Sie den virtuellen Computer mit dem folgenden Befehl. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. Wenn Sie dazu aufgefordert werden, bestätigen Sie die Aktion (Ja). Warten Sie, bis der Status **Erfolgreich** angezeigt wird.

6. Überprüfen Sie den Status Ihres virtuellen Computers. Der Energiestatus sollte jetzt **Zuweisung aufgehoben** lauten. Sie können den Status des virtuellen Computers auch im Portal überprüfen. Schließen Sie Cloudshell.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# <a name="task-4-review-azure-advisor-recommendations"></a>Aufgabe 4: Überprüfen von Azure Advisor-Empfehlungen

**Hinweis:** Diese Aufgabe finden Sie im Lab „Erstellen eines virtuellen Computers mit der Azure CLI“. 

In dieser Aufgabe überprüfen wir die Azure Advisor-Empfehlungen für unseren virtuellen Computer. 

1. Suchen Sie auf Blatt **Alle Dienste** nach **Advisor**, und wählen Sie diese Option aus. 

2. Wählen Sie auf dem Blatt **Advisor** den Eintrag **Überblick** aus. Beachten Sie, dass Empfehlungen nach Zuverlässigkeit, Sicherheit, Leistung und Kosten gruppiert sind. 

    ![Screenshot der Seite „Advisor-Übersicht“. ](../images/1003.png)

3. Wählen Sie **Alle Empfehlungen** aus und Sie sich Zeit, um die einzelnen Empfehlungen und vorgeschlagenen Maßnahmen anzuzeigen. 

    **Hinweis:** Die Empfehlungen sind je nach Ihren Ressourcen unterschiedlich. 

    ![Screenshot der Advisor-Seite „Alle Empfehlungen“. ](../images/1004.png)

4. Beachten Sie, dass Sie die Empfehlungen als CSV- oder PDF-Datei herunterladen können. 

5. Beachten Sie, dass Sie Warnungen erstellen können. 

6. Wenn Sie Zeit haben, experimentieren Sie weiter mit Azure PowerShell. 

Glückwunsch! Sie haben Cloud Shell konfiguriert, mithilfe von PowerShell einen virtuellen Computer erstellt, PowerShell-Befehle geübt und Advisor-Empfehlungen angesehen.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
