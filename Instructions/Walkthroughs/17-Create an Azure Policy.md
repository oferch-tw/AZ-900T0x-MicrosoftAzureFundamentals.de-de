---
wts:
  title: 17 – Erstellen einer Azure-Richtlinie (10 Min.)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="17---create-an-azure-policy-10-min"></a>17 – Erstellen einer Azure-Richtlinie (10 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir eine Azure-Richtlinie, um die Bereitstellung von Azure-Ressourcen auf einen bestimmten Standort zu beschränken.

# <a name="task-1-create-a-policy-assignment"></a>Aufgabe 1: Erstellen einer Richtlinienzuweisung 

In dieser Aufgabe konfigurieren wir die zulässige Standortrichtlinie und weisen sie unserem Abonnement zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. From the <bpt id="p1">**</bpt>All services<ept id="p1">**</ept> blade, search for and select <bpt id="p2">**</bpt>Policy<ept id="p2">**</ept>, under the <bpt id="p3">**</bpt>Authoring<ept id="p3">**</ept> section click <bpt id="p4">**</bpt>Definitions<ept id="p4">**</ept>.  Take a moment to review the list of built-in policy definitions. For example, in the <bpt id="p1">**</bpt>Category<ept id="p1">**</ept> drop-down select only <bpt id="p2">**</bpt>Compute<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Allowed virtual machine size SKUs<ept id="p1">**</ept> definition enables you to specify a set of virtual machine SKUs that your organization can deploy.

3. Return to the <bpt id="p1">**</bpt>Policy<ept id="p1">**</ept> page, under the <bpt id="p2">**</bpt>Authoring<ept id="p2">**</ept> section click <bpt id="p3">**</bpt>Assignments<ept id="p3">**</ept>. An assignment is a policy that has been assigned to take place within a specific scope. For example, a definition could be assigned to the subscription scope. 

4. Klicken Sie auf **Richtlinie zuweisen** im oberen Bereich der Seite **Richtlinie - Aufgaben**.

5. Behalten Sie auf der Seite **Richtlinie zuweisen** den Standardbereich bei.

      | Einstellung | Wert | 
    | --- | --- |
    | Bereich| **Standarddaten verwenden**|
    | Richtliniendefinition | Klicken Sie auf die Auslassungspunkte, suchen Sie nach **Zulässige Standorte**, und **wählen Sie die Option aus**. |
    | Zuweisungsname | **Zulässige Standorte** |
    
    ![Screenshot des Bereichs „Bereich“ mit ausgefüllten Feldwerten und hervorgehobener Schaltfläche „Auswählen“. ](../images/1402.png)
6. On the <bpt id="p1">**</bpt>Parameters<ept id="p1">**</ept> tab, select <bpt id="p2">**</bpt>Japan West<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>, and then <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: A scope determines what resources or grouping of resources the policy assignment applies to. In our case we could assign this policy to a specific resource group, however we chose to assign the policy at subscription level. Be aware that resources can be excluded based on the scope configuration. Exclusions are optional.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This <bpt id="p2">**</bpt>Allowed Locations<ept id="p2">**</ept> policy definition will specify a location into which all resources must be deployed. If a different location is chosen, deployment will not be allowed. For more information view the <bpt id="p1">[</bpt>Azure Policy Samples<ept id="p1">](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index)</ept> page.

   ![Screenshot des Bereichs „Verfügbare Definitionen“ mit verschiedenen hervorgehobenen Feldern und ausgewählter Option „Überwachungs-VMs, die keine verwalteten Datenträger verwenden“.](../images/1403.png)

9. Die Richtlinienzuweisung **Zulässige Standorte** ist jetzt auf der Liste **Richtlinie - Aufgaben** aufgeführt und in Kraft getreten und setzt die Richtlinie auf der von uns angegebenen Bereichsebene (Abonnementebene) durch.

# <a name="task-2-test-allowed-location-policy"></a>Aufgabe 2: Testen der Richtlinie für zulässige Standorte

In dieser Aufgabe testen wir die Richtlinie für zulässige Standorte. 

1. Suchen Sie im Azure-Portal auf dem Blatt **Alle Dienste** nach **Speicherkonten**, und wählen Sie diese Option aus. Klicken Sie anschließend auf **+ Erstellen**.

2. Configure the storage account (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the storage account with letters and digits such that the name is globally unique). Leave the defaults for everything else. 

    | Einstellung | Wert | 
    | --- | --- |
    | Subscription | **Standarddaten verwenden** |
    | Resource group | **myRGPolicy** (neu erstellen) |
    | Speicherkontoname | **storageaccountxxxx** |
    | Standort | **(USA) USA, Osten** |

3. Klicken Sie auf **Überprüfen + erstellen** und dann auf **Erstellen**. 

4. Sie erhalten die Fehlermeldung **Bereitstellung fehlgeschlagen**, die besagt, dass die Ressource von der Richtlinie nicht zugelassen wurde, einschließlich des Richtliniennamens **Zulässige Standorte**.

# <a name="task-3-delete-the-policy-assignment"></a>Aufgabe 3: Löschen der Richtlinienzuweisung

In dieser Aufgabe entfernen wir die Richtlinienzuweisung für zulässige Standorte und testen dies. 

Wir werden die Richtlinienzuweisung löschen, um sicherzustellen, dass wir bei zukünftigen Arbeiten, die wir ausführen möchten, nicht blockiert werden.

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und wählen Sie diese Option aus. Klicken Sie anschließend auf Ihre Richtlinie **Zulässige Standorte**.

    **Hinweis:** Auf dem Blatt **Richtlinie** können Sie den Konformitätszustand der verschiedenen Richtlinien anzeigen, die Sie zugewiesen haben.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The Allowed location policy may show non-compliant resources. If so, these are resources created prior to the policy assignment.
 
2. Klicken Sie auf **Zulässige Standorte**. Daraufhin wird Fenster für die Richtlinieneinhaltung der zulässigen Standorte geöffnet.

3. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und wählen Sie sie diese Option aus. Klicken Sie im Abschnitt **Dokumenterstellung** auf **Definitionen**.

   ![Screenshot des Menüelements „Zuweisung löschen“.](../images/1407.png)

4. Versuchen Sie, ein anderes Speicherkonto zu erstellen, um sicherzustellen, dass die Richtlinie nicht mehr gültig ist.

    **Hinweis:** Häufige Szenarien, in denen die Richtlinie **Zulässige Standorte** nützlich sein kann, wären: 
    - Nehmen Sie sich einen Moment Zeit, um die Liste der integrierten Richtliniendefinitionen zu überprüfen. 
    - *Compliance mit Datenresidenz- und Sicherheitsanforderungen*: Sie können auch Anforderungen an die Datenresidenz haben und Abonnements pro Kunde oder bestimmten Workloads erstellen und festlegen, dass alle Ressourcen in einem bestimmten Rechenzentrum bereitgestellt werden müssen, um die Complianceanforderungen bezüglich Daten und Sicherheit zu erfüllen.

Wählen Sie zum Beispiel in der Dropdownliste **Kategorie** nur **Compute** aus.

Mit der Definition **Zulässige SKUs für virtuelle Computer** können Sie eine Reihe von SKUs für virtuelle Computer angeben, die Ihre Organisation bereitstellen kann.
