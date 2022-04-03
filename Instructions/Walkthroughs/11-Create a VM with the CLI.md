---
wts:
  title: 11 – Erstellen eines virtuellen Computers mithilfe der CLI (10 Min.)
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: 6e88e520011ccf4f1d02fd14038a457226492082
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907999"
---
# <a name="11---create-a-vm-with-the-cli-10-min"></a>11 – Erstellen eines virtuellen Computers mithilfe der CLI (10 Min.)

In dieser exemplarischen Vorgehensweise konfigurieren wir die Cloud Shell, erstellen mithilfe von Azure CLI eine Ressourcengruppe und einen virtuellen Computer und überprüfen die Empfehlungen von Azure Advisor. 

# <a name="task-1-configure-the-cloud-shell"></a>Aufgabe 1: Konfigurieren der Cloud Shell 

In dieser Aufgabe konfigurieren wir Cloud Shell und verwenden Azure CLI, um eine Ressourcengruppe und einen virtuellen Computer zu erstellen.  

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Öffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

    ![Screenshot des Azure Cloud Shell-Symbols im Azure-Portal.](../images/1002.png)
   
3. Wenn Sie im Willkommensdialog für Azure Cloud Shell dazu aufgefordert werden, entweder **Bash** oder **PowerShell** auszuwählen, wählen Sie **Bash** aus. 

4. Ein neues Fenster mit der Meldung **Cloudshell** wird geöffnet. Wählen Sie **Erweiterte Einstellungen** aus.

5. Füllen Sie in den erweiterten Einstellungen die folgenden Felder aus, und klicken Sie auf „Speicher erstellen“:
    - Ressourcengruppe: **Neue Ressourcengruppe erstellen**
    - Speicherkonto: Erstellen Sie ein neues Konto mit einem global eindeutigen Namen, z. B. cloudshellxyzstorage.
    - Dateifreigabe: Erstellen Sie eine neue Kampagne mit dem Namen cloudshellfileshare.


# <a name="task-2-use-cli-to-create-a-virtual-machine"></a>Aufgabe 2: Erstellen eines virtuellen Computers per CLI

In dieser Aufgabe verwenden wir Azure CLI, um eine Ressourcengruppe und einen virtuellen Computer zu erstellen.

1. Stellen Sie sicher, dass **Bash** im Dropdownmenü oben links im Cloud Shell-Bereich ausgewählt ist (wählen Sie andernfalls diese Option aus).

    ![Screenshot der Azure-Portal Azure Cloud Shell mit hervorgehobenem Bash-Dropdown.](../images/1002a.png)


2. Überprüfen Sie mit dem folgenden Befehl, in welcher Ressourcengruppe Sie sich befinden.

    ```cli
    az group list --output table
    ```

4. Geben Sie in Cloud Shell den folgenden Befehl ein, und stellen Sie sicher, dass auf jede Zeile mit Ausnahme der letzten Zeile ein umgekehrter Schrägstrich (`\`) folgt. Wenn Sie den gesamten Befehl in derselben Zeile eingeben, verwenden Sie keine umgekehrten Schrägstriche. 

    ```cli
    az vm create \
    --name myVMCLI \
    --resource-group myRGCLI \
    --image UbuntuLTS \
    --location EastUS2 \
    --admin-username azureuser \
    --admin-password Pa$$w0rd1234
    ```

    >**Hinweis:** Wenn Sie die Befehlszeile auf einem Windows-Computer verwenden, ersetzen Sie den umgekehrten Schrägstrich (`\`) durch das Caretzeichen (`^`).

    **Hinweis:** Die Ausführung des Befehls dauert 2 bis 3 Minuten. Der Befehl erstellt einen virtuellen Computer und verschiedene damit verbundene Ressourcen wie Speicher-, Netzwerk- und Sicherheitsressourcen. Fahren Sie mit dem nächsten Schritt erst dann fort, wenn die Bereitstellung des virtuellen Computers abgeschlossen ist. 

5. Wenn der Befehl ausgeführt wurde, schließen Sie im Browserfenster den Cloud Shell-Bereich.

6. Suchen Sie im Azure-Portal nach **Virtuelle Computer**, und überprüfen Sie, ob **myVMCLI** ausgeführt wird.

    ![Screenshot der Seite „Virtuelle Computer“, wobei myVMPS ausgeführt wird.](../images/1101.png)


# <a name="task-3-execute-commands-in-the-cloud-shell"></a>Aufgabe 3: Ausführen von Befehlen in Cloud Shell

In dieser Aufgabe üben wir das Ausführen von CLI-Befehlen über Cloud Shell. 

1. Öffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

2. Stellen Sie sicher, dass **Bash** im Dropdownmenü oben links im Cloud Shell-Bereich ausgewählt ist.

3. Rufen Sie Informationen zu dem von Ihnen bereitgestellten virtuellen Computer ab, einschließlich Name, Ressourcengruppe, Ort und Status. Beachten Sie, dass der Energiestatus **Wird ausgeführt** lautet.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

4. Beenden Sie den virtuellen Computer. Beachten Sie die Meldung, dass die Abrechnung weiterläuft, bis die Zuordnung des virtuellen Computers aufgehoben wird. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

5. Überprüfen Sie den Status Ihres virtuellen Computers. Der Energiestatus sollte jetzt **Beendet** lauten.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

# <a name="task-4-review-azure-advisor-recommendations"></a>Aufgabe 4: Überprüfen von Azure Advisor-Empfehlungen

In dieser Aufgabe überprüfen wir die Empfehlungen von Azure Advisor.

   **Hinweis:** Wenn Sie das vorherige Lab (Erstellen eines virtuellen Computers mithilfe von PowerShell) abgeschlossen haben, haben Sie diese Aufgabe bereits ausgeführt. 

1. Suchen Sie auf Blatt **Alle Dienste** nach **Advisor**, und wählen Sie diese Option aus. 

2. Wählen Sie auf dem Blatt **Advisor** den Eintrag **Überblick** aus. Beachten Sie, dass Empfehlungen nach Zuverlässigkeit, Sicherheit, Leistung und Kosten gruppiert sind. 

    ![Screenshot der Seite „Advisor-Übersicht“. ](../images/1103.png)

3. Wählen Sie **Alle Empfehlungen** aus und Sie sich Zeit, um die einzelnen Empfehlungen und vorgeschlagenen Maßnahmen anzuzeigen. 

    **Hinweis:** Die Empfehlungen sind je nach Ihren Ressourcen unterschiedlich. 

    ![Screenshot der Advisor-Seite „Alle Empfehlungen“. ](../images/1104.png)

4. Beachten Sie, dass Sie die Empfehlungen als CSV- oder PDF-Datei herunterladen können. 

5. Beachten Sie, dass Sie Warnungen erstellen können. 

6. Wenn Sie Zeit haben, experimentieren Sie weiter mit Azure CLI. 

Glückwunsch! Sie haben Cloud Shell konfiguriert, einen virtuellen Computer mit Azure CLI erstellt, Azure CLI-Befehle geübt und Advisor-Empfehlungen angesehen.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
