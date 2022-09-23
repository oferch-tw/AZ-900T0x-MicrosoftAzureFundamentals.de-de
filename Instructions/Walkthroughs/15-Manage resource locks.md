---
wts:
  title: 15 – Verwalten von Ressourcensperren (5 Min.)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="15---manage-resource-locks-5-min"></a>15 – Verwalten von Ressourcensperren (5 Min.)

In this walkthrough, we will add a lock to the resource group and test deleting the resource group. Locks can be applied in a subscription to resource groups, or individual resources to prevent accidental deletion or modification of critical resources.  


# <a name="task-1--add-a-lock-to-the-resource-group-and-test-deletion"></a>Aufgabe 1:  Hinzufügen einer Sperre zur Ressourcengruppe und Testen des Löschvorgangs

In dieser Aufgabe fügen wir der Ressourcengruppe eine Ressourcensperre hinzu und testen das Löschen der Ressourcengruppe. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie im Azure-Portal zur Ressourcengruppe **myRGLocks**.

3. Sie können eine Sperre auf ein Abonnement, eine Ressourcengruppe oder eine einzelne Ressource anwenden, um ein versehentliches Löschen oder Ändern kritischer Ressourcen zu verhindern. 

4. Klicken Sie im Abschnitt **Einstellungen** auf **Sperren** und dann auf **+ Hinzufügen**. 

    ![Screenshot der Ressourcengruppe „myRGLocks“ mit dem angezeigten Bereich „Sperren“.](../images/1601.png)

5. Configure the new lock. When you are done click <bpt id="p1">**</bpt>OK<ept id="p1">**</ept>. 

    | Einstellung | Wert |
    | -- | -- |
    | Sperrenname | RGLock |
    | Sperrentyp | **Löschen** |
    | | |

6. Click <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> and click <bpt id="p2">**</bpt>Delete resource group<ept id="p2">**</ept>. Type the name of the resource group and click <bpt id="p1">**</bpt>OK<ept id="p1">**</ept>. You receive an error message stating the resource group is locked and can't be deleted.

    ![Screenshot der fehlgeschlagenen Löschsperren.](../images/1602.png)

# <a name="task-2-test-deleting-a-member-of-the-resource-group"></a>Aufgabe 2: Testen des Löschens eines Mitglieds der Ressourcengruppe

In dieser Aufgabe testen wir, ob die Ressourcensperre ein Speicherkonto in der Ressourcengruppe schützt. 

1. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Speicherkonten**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen oder auf + Neu**. 

2. In dieser exemplarischen Vorgehensweise fügen wir der Ressourcengruppe eine Sperre hinzu und testen das Löschen der Ressourcengruppe.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Wählen Sie Ihr Abonnement aus** |
    | Resource group | **myRGLocks** |
    | Speicherkontoname | **storageaccountxxxx** |
    | Standort | **(USA) USA, Osten**  |
    | Leistung | **Standard** |
    | Kontoart | **StorageV2 (allgemein, Version 2)** |
    | Replikation | **Lokal redundanter Speicher (LRS)** |
    | Zugriffsebene (Standard) | **Heiße Ebene** |
   

3. Klicken Sie auf **Überprüfen + erstellen**, um die Einstellungen Ihres Speicherkontos zu überprüfen und Azure die Validierung der Konfiguration zu ermöglichen. 

4. Sperren können in einem Abonnement auf Ressourcengruppen oder einzelne Ressourcen angewendet werden, um ein versehentliches Löschen oder Ändern kritischer Ressourcen zu verhindern. 

5.  Warten Sie auf die Benachrichtigung, dass das Speicherkonto erfolgreich erstellt wurde. 

6. Access your new storage account and from the <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> pane, click <bpt id="p2">**</bpt>Delete<ept id="p2">**</ept>. You receive an error message stating the resource or its parent has a delete lock. 

    ![Screenshot der Meldung bezüglich eines Fehlers beim Löschen des Speicherkontos.](../images/1603.png)

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Although we did not create a lock specifically for the storage account, we did create a lock at the resource group level, which contains the storage account. As such, this <bpt id="p1">*</bpt>parent<ept id="p1">*</ept> level lock prevents us from deleting the resource and the storage account inherits the lock from the parent.

# <a name="task-3-remove-the-resource-lock"></a>Aufgabe 3: Entfernen der Ressourcensperre

In dieser Aufgabe entfernen wir die Ressourcensperre und testen. 

1. Wechseln Sie wieder zum Ressourcengruppen-Blatt **myRGLocks-XXXXXXXX**, und klicken Sie im Abschnitt **Einstellungen** auf **Sperren**.
    
2. Klicken Sie auf den Link **Löschen** ganz rechts neben dem Eintrag **myRGLocks-XXXXXXXX**, rechts von **Bearbeiten**.

    ![Screenshot der Sperre mit hervorgehobenem Link zum Löschen.](../images/1604.png)

3. Kehren Sie in das Blatt „Speicherkonto“ zurück und bestätigen Sie, dass Sie die Ressource jetzt löschen können.

Congratulations! You created a resource group, added a lock to resource group and tested deletion, tested deleting a resource in the resource group, and removed the resource lock. 

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
