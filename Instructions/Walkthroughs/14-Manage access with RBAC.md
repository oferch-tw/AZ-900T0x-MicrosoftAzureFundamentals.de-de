---
wts:
  title: 14 – Zugriff mit RBAC verwalten (5 Min.)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="14---manage-access-with-rbac-5-min"></a>14 – Zugriff mit RBAC verwalten (5 Min.)

In dieser exemplarischen Vorgehensweise werden wir Berechtigungsrollen zu Ressourcen zuweisen und Protokolle anzeigen.

# <a name="task-1-view-and-assign-roles"></a>Aufgabe 1: Anzeigen und Zuweisen von Rollen

In dieser Aufgabe weisen wir die Rolle „Mitwirkender für virtuelle Computer“ zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Ressourcengruppen**, und wählen Sie diese Option aus. Klicken Sie anschließend auf **+ Hinzufügen +Neu +Erstellen**.

3. Create a new resource group. Click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> when you are finished. 

    | Einstellung | Wert |
    | -- | -- |
    | Subscription | **Standardeinstellung verwenden** |
    | Resource group | **myRGRBAC** |
    | Region | **(USA) USA, Osten** |
   

4. Erstellen Sie **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**.

5. **Aktualisieren** Sie die Seite „Ressourcengruppe“, und klicken Sie auf den Eintrag, der die neu erstellte Ressourcengruppe darstellt.

6. Click on the <bpt id="p1">**</bpt>Access control (IAM)<ept id="p1">**</ept> blade, and then switch to the <bpt id="p2">**</bpt>Roles<ept id="p2">**</ept> tab. Scroll through the large number of roles definitions that are available. Use the Informational icons to get an idea of each role's permissions. Notice there is also information on the number of users and groups that are assigned to each role.
7. 
![image](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Switch to the <bpt id="p1">**</bpt>Role assignments<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>myRGRBAC - Access control (IAM)<ept id="p2">**</ept> blade, click <bpt id="p3">**</bpt>+ Add<ept id="p3">**</ept> and then click <bpt id="p4">**</bpt>Add role assignment<ept id="p4">**</ept>. Search for the Virtual Machine Contributor role and select. Switch to the "Members" tab and Assign access to: User, group, or service principal. Then click + Select members and type in your name to the popup search function and hit 'select.' Then hit 'Review and Assign'

    
    ![image](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **Hinweis:** Mit der Rolle „Mitwirkender für virtuelle Computer“ können Sie virtuelle Computer verwalten, jedoch nicht auf deren Betriebssystem zugreifen oder das virtuelle Netzwerk und das Speicherkonto verwalten, mit denen sie verbunden sind.

  

8. **Aktualisieren** Sie die Seite „Rollenzuweisungen“ und stellen Sie sicher, dass Sie jetzt als Mitwirkender eines virtuellen Computers aufgeführt sind. 

    **Hinweis:** Diese Zuweisung gewährt Ihnen keine zusätzlichen Berechtigungen, da Ihr Konto bereits über die Besitzerrolle verfügt, die alle mit der Rolle „Mitwirkender“ verbundenen Berechtigungen enthält.

# <a name="task-2-monitor-role-assignments-and-remove-a-role"></a>Aufgabe 2: Überwachen von Rollenzuweisungen und Entfernen einer Rolle

In dieser Aufgabe werden wir anhand des Aktivitätsprotokolls die Rollenzuweisung überprüfen und anschließend die Rolle entfernen. 

1. Klicken Sie auf dem Blatt „myRGRBAC Ressourcengruppen“ auf **Aktivitätsprotokoll**.

2. Klicken Sie auf **Filter hinzufügen**, wählen Sie **Vorgang** und dann **Rollenzuweisung erstellen** aus.

    ![Screenshot der Aktivitätsprotokollseite mit konfiguriertem Filter.](../images/1503.png)

3. Überprüfen Sie, ob Ihre Rollenzuweisung im Aktivitätsprotokoll angezeigt wird. 

    **Hinweis:** Wissen Sie, wie Sie Ihre Rollenzuweisung entfernen können?

Congratulations! You created a resource group, assigned an access role to it and viewed activity logs. 

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.

