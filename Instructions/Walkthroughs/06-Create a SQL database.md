---
wts:
  title: 06 – Erstellen einer SQL-Datenbank (5 Min.)
  module: Module 02 - Core Azure Services (Workloads)
---

# <a name="06---create-a-sql-database-5-min"></a>06 – Erstellen einer SQL-Datenbank (5 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir eine SQL-Datenbank in Azure und fragen dann die Daten in dieser Datenbank ab.

# <a name="task-1-create-the-database"></a>Aufgabe 1: Erstellen der Datenbank 

In dieser Aufgabe erstellen Sie eine SQL-Datenbank, die auf der Beispieldatenbank AdventureWorksLT basiert. 

1. Melden Sie sich unter [ **https://portal.azure.com** ](https://portal.azure.com) beim Azure-Portal an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **SQL-Datenbanken**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**. 

3. Geben Sie auf der Registerkarte **Grundlagen** diese Informationen ein.  

    | Einstellung | Wert | 
    | --- | --- |
    | Subscription | **Standarddaten verwenden** |
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Datenbankname| **db1** | 
    | Server | Wählen Sie **Neu erstellen** aus (rechts wird eine neue Seitenleiste geöffnet).|
    | Servername | **sqlserverxxxx** (muss eindeutig sein) | 
    | Standort | **(USA) USA, Osten** |
    | Authentifizierungsmethode | **SQL-Authentifizierung verwenden** |
    | Serveradministratoranmeldung | **sqluser** |
    | Kennwort | **Pa$$w0rd1234** |
    | Klicken Sie auf  | **OK** |

   ![Screenshot der Bereiche „Server“ und „Neuer Server“ mit den Feldern, die gemäß der Tabelle ausgefüllt sind, und den hervorgehobenen Schaltflächen „Überprüfen + speichern“ und „OK“](../images/0501.png)

4. Konfigurieren Sie auf der Registerkarte **Netzwerk** die folgenden Einstellungen (behalten Sie bei den anderen Optionen die Standardeinstellungen bei). 

    | Einstellung | Wert | 
    | --- | --- |
    | Konnektivitätsmethode | **Öffentlicher Endpunkt** |    
    | Azure-Diensten und -Ressourcen den Zugriff auf diesen Server erlauben | **Ja** |
    | Aktuelle Client-IP-Adresse hinzufügen | **Nein** |
    
   ![Screenshot der Registerkarte „Netzwerk“ des Blatts „SQL-Datenbank erstellen“ mit den in der Tabelle gewählten Einstellungen und hervorgehobener Schaltfläche „Überprüfen + erstellen“.](../images/0501b.png)

5. Wechseln Sie zur Registerkarte **Sicherheit**. 

    | Einstellung | Wert | 
    | --- | --- |
    | Microsoft Defender für SQL| **Jetzt nicht** |
    
6. Wechseln Sie in die Registerkarte **Zusätzliche Einstellungen**. Wir werden die AdventureWorksLT-Beispieldatenbank verwenden.

    | Einstellung | Wert | 
    | --- | --- |
    | Vorhandene Daten verwenden | **Beispiel** |

    ![Screenshot der Registerkarte „Zusätzliche Einstellungen“ des Blatts „SQL-Datenbank erstellen“, wobei die Einstellungen gemäß der Tabelle ausgewählt und die Schaltfläche „Überprüfen + erstellen“ hervorgehoben ist.](../images/0501c.png)

7. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> and then click <bpt id="p2">**</bpt>Create<ept id="p2">**</ept> to deploy and provision the resource group, server, and database. It can take approx. 2 to 5 minutes to deploy.


# <a name="task-2-test-the-database"></a>Aufgabe 2: Testen Sie die Datenbank.

In dieser Aufgabe konfigurieren Sie den SQL-Server und führen eine SQL-Abfrage aus. 

1. When the deployment has completed, click Go to resource from the deployment blade. Alternatively, from the <bpt id="p1">**</bpt>All Resources<ept id="p1">**</ept> blade, search and select <bpt id="p2">**</bpt>Databases<ept id="p2">**</ept>, then <bpt id="p3">**</bpt>SQL databases<ept id="p3">**</ept> ensure your new database was created. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

    ![Screenshot der soeben bereitgestellten SQL-Datenbank und des Servers](../images/0502.png)

2. Click the <bpt id="p1">**</bpt>db1<ept id="p1">**</ept> entry representing the SQL database you created. On the db1 blade click <bpt id="p1">**</bpt>Query editor (preview)<ept id="p1">**</ept>.

3. Melden Sie sich als **sqluser** mit dem Kennwort **Pa$$w0rd1234** an.

4. You will not be able to login. Read the error closely and make note of the IP address that needs to be allowed through the firewall. 

    ![Screenshot der Anmeldeseite des Abfrage-Editors mit dem IP-Adressfehler](../images/0503.png)

5. Wechseln Sie zurück zum Blatt **db1**, und klicken Sie auf **Überblick**. 

    ![Screenshot der Seite „SQL-Server“.](../images/0504.png)

6. Klicken Sie auf dem Blatt **Übersicht** für „db1“ auf **Serverfirewall festlegen** oben in der Mitte des Übersichtsbildschirms.

7. Click <bpt id="p1">**</bpt>+ Add client IP<ept id="p1">**</ept> (top menu bar) to add the IP address referenced in the error. (it may have autofilled for you - if not paste it into the IP address fields). Be sure to <bpt id="p1">**</bpt>Save<ept id="p1">**</ept> your changes. 

    ![Screenshot der Seite mit den SQL Server-Firewalleinstellungen, auf der die neue IP-Adressregel hervorgehoben ist](../images/0506.png)

8. Return to your SQL database (slide the bottom toggle bar to the left) and click on <bpt id="p1">**</bpt>Query Editor (Preview)<ept id="p1">**</ept>. Try to login again as <bpt id="p1">**</bpt>sqluser<ept id="p1">**</ept> with the password <bpt id="p2">**</bpt>Pa$$w0rd1234<ept id="p2">**</ept>. This time you should succeed. Note that it may take a couple of minutes for the new firewall rule to be deployed. 

9. Once you log in successfully, the query pane appears. Enter the following query into the editor pane. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Screenshot des Abfrage-Editors mit dem Abfragebereich und der erfolgreichen Befehlsausführung](../images/0507.png)

10. Click <bpt id="p1">**</bpt>Run<ept id="p1">**</ept>, and then review the query results in the <bpt id="p2">**</bpt>Results<ept id="p2">**</ept> pane. The query should run successfully.

    ![Screenshot des Datenbankbereichs im Abfrage-Editor mit dem erfolgreich ausgeführten SQL-Code und der im Ergebnisbereich angezeigten Ausgabe](../images/0508.png)

Congratulations! You have created a SQL database in Azure and successfully queried the data in that database.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
