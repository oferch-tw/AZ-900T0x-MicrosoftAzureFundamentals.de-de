---
wts:
  title: 09 – Erstellen eines virtuellen Computers mit Hilfe einer Vorlage (10 Min.)
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="09---create-a-vm-with-a-template-10-min"></a>09 – Erstellen eines virtuellen Computers mit Hilfe einer Vorlage (10 Min.)

In dieser exemplarischen Vorgehensweise stellen wir einen virtuellen Computer mit einer Schnellstartvorlage bereit und untersuchen Überwachungsfunktionen.

# <a name="task-1-explore-the-quickstart-gallery-and-locate-a-template"></a>Aufgabe 1: Schnellstartkatalog durchsuchen und Sie eine Vorlage finden 

In dieser Aufgabe durchsuchen wir den Azure-Schnellstartkatalog und stellen eine Vorlage bereit, mit der ein virtueller Computer erstellt wird. 

1. Within the lab environment, open a new browser window, and enter T <ph id="ph1">https://azure.microsoft.com/en-us/resources/templates/?azure-portal=true</ph>. In the gallery you will find a number of popular and recently updated templates. These templates automate deployment of Azure resources, including installation of popular software packages. Browse through the many different types of templates that are available.

3. Wählen Sie **Bereitstellen einer einfachen Windows-VM** aus.

4. Click the <bpt id="p1">**</bpt>Deploy to Azure<ept id="p1">**</ept> button. Your browser session will be automatically redirected to the <bpt id="p1">[</bpt>Azure portal<ept id="p1">](http://portal.azure.com/)</ept>.

  <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The <bpt id="p2">**</bpt>Deploy to Azure<ept id="p2">**</ept> button enables you to deploy the template via the Azure portal. During such deployment, you will be prompted only for small set of configuration parameters. 

5. Melden Sie sich mit den zuvor in den Anweisungen angegebenen Anmeldeinformationen bei Ihrem Azure-Abonnement an, wenn Sie dazu aufgefordert werden.

6. Click <bpt id="p1">**</bpt>Edit template<ept id="p1">**</ept>. The Resource Manager template format uses the JSON format. Review the parameters and variables.  Then locate the parameter for virtual machine name. Change the name to <bpt id="p1">**</bpt>myVMTemplate<ept id="p1">**</ept>. <bpt id="p1">**</bpt>Save<ept id="p1">**</ept> your changes. 

    ![Screenshot der Vorlage mit der hervorgehobenen Änderung des VM-Namens.](../images/0901.png)

7. Now configure the parameters required by the template (replace <bpt id="p1">***</bpt>xxxx<ept id="p1">***</ept> in the DNS label prefix with letters and digits such that the label is globally unique). Leave the defaults for everything else. 

    | Einstellung| Wert|
    |----|----|
    | Subscription | **Standarddaten beibehalten**|
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Region | Standard beibehalten |
    | Administratorbenutzername | **azureuser** |
    | Administratorkennwort | **Pa$$w0rd1234** |
    | Präfix der DNS-Bezeichnung | **myvmtemplatexxxx** |
    | Betriebssystemversion | **2019-Datacenter** |


9. Klicken Sie auf **Überprüfen + erstellen**.

10. Überwachen Sie Ihre Bereitstellung. 

# <a name="task-2-verify-and-monitor-your-virtual-machine-deployment"></a>Aufgabe 2: Überprüfen und Überwachen der Bereitstellung Ihres virtuellen Computers

In dieser Aufgabe überprüfen wir, ob der virtuelle Computer ordnungsgemäß bereitgestellt wurde. 

1. Auf dem Blatt **Alle Dienste** suchen und wählen Sie **Virtuelle Computer** aus.

2. Stellen Sie sicher, dass Ihr neuer virtueller Computer erstellt wurde. 

    ![Screenshot of the virtual machines page. The new VM is shown and running.](../images/0902.png)

3. Wählen Sie Ihren virtuellen Computer aus, wählen Sie im Bereich **Übersicht** die Registerkarte **Überwachung** aus, und scrollen Sie nach unten zu den Überwachungsdaten.

    **Hinweis:** Der Überwachungszeitraum kann von einer Stunde bis zu 30 Tagen angepasst werden.

4. Überprüfen Sie verschiedene Diagramme, einschließlich **CPU (Durchschnitt)** , **Netzwerk (gesamt)** , und **Festplattenbytes (gesamt)** . 

    ![Screenshot der Überwachungsdiagramme zum virtuellen Computer.](../images/0903.png)

5. Öffnen Sie in der Laborumgebung ein neues Browserfenster, und geben Sie https://azure.microsoft.com/en-us/resources/templates/?azure-portal=true ein.

6. Im Katalog finden Sie eine Reihe beliebter und kürzlich aktualisierter Vorlagen.
7. Diese Vorlagen automatisieren die Bereitstellung von Azure-Ressourcen, einschließlich der Installation gängiger Softwarepakete. 

8. Klicken Sie auf **Filter hinzufügen**, und experimentieren Sie mit der Suche nach verschiedenen Ereignistypen und Operationen. 

    ![Screenshot der Seite „Filter hinzufügen“ mit ausgewähltem Ereignistyp.](../images/0904.png)

Durchsuchen Sie die vielen verschiedenen Arten von Vorlagen, die verfügbar sind.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
