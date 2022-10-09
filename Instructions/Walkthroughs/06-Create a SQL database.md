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

7. Klicken Sie auf **Überprüfen + erstellen** und dann auf **Erstellen**, um die Ressourcengruppe, den Server und die Datenbank bereitzustellen. Die Bereitstellung kann etwa 2 bis 5 Minuten dauern.


# <a name="task-2-test-the-database"></a>Aufgabe 2: Testen Sie die Datenbank.

In dieser Aufgabe konfigurieren Sie den SQL-Server und führen eine SQL-Abfrage aus. 

1. Klicken Sie nach Abschluss der Bereitstellung auf dem Blatt „Bereitstellung“ auf „Zur Ressource wechseln“. Wählen Sie alternativ auf dem Blatt **Alle Ressourcen** die Option **Datenbanken** und dann **SQL-Datenbanken** aus. Vergewissern Sie sich, dass Ihre neue Datenbank erstellt wurde. Möglicherweise müssen Sie die Seite **aktualisieren**.

    ![Screenshot der soeben bereitgestellten SQL-Datenbank und des Servers](../images/0502.png)

2. Klicken Sie auf den Eintrag **db1** für die soeben erstellte SQL-Datenbank. Klicken Sie auf dem Blatt „db1“ auf **Abfrage-Editor (Vorschau)** .

3. Melden Sie sich als **sqluser** mit dem Kennwort **Pa$$w0rd1234** an.

4. Sie können sich nicht anmelden. Lesen Sie die Fehlermeldung genau durch, und notieren Sie sich die IP-Adresse, die in der Firewall zugelassen werden muss. 

    ![Screenshot der Anmeldeseite des Abfrage-Editors mit dem IP-Adressfehler](../images/0503.png)

5. Wechseln Sie zurück zum Blatt **db1**, und klicken Sie auf **Überblick**. 

    ![Screenshot der Seite „SQL-Server“.](../images/0504.png)

6. Klicken Sie auf dem Blatt **Übersicht** für „db1“ auf **Serverfirewall festlegen** oben in der Mitte des Übersichtsbildschirms.

7. Klicken Sie auf **+ Client-IP hinzufügen** (obere Menüleiste), um die IP-Adresse hinzuzufügen, auf die in der Fehlermeldung verwiesen wird. (Möglicherweise wurde der Wert bereits für Sie ausgefüllt. Fügen Sie ihn andernfalls in die IP-Adressfelder ein). Klicken Sie auf **Speichern**, um die Änderungen zu speichern. 

    ![Screenshot der Seite mit den SQL Server-Firewalleinstellungen, auf der die neue IP-Adressregel hervorgehoben ist](../images/0506.png)

8. Kehren Sie zu Ihrer SQL-Datenbank zurück (schieben Sie den unteren Umschalter nach links), und klicken Sie auf **Abfrage-Editor (Vorschau)** . Melden Sie sich erneut als **sqluser** mit dem Kennwort **Pa$$w0rd1234** an. Dieses Mal sollten Sie erfolgreich sein. Beachten Sie, dass es einige Minuten dauern kann, bis die neue Firewallregel bereitgestellt wird. 

9. Nachdem Sie sich erfolgreich angemeldet haben, wird der Abfragebereich angezeigt. Geben Sie die folgende Abfrage in den Editor-Bereich ein. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Screenshot des Abfrage-Editors mit dem Abfragebereich und der erfolgreichen Befehlsausführung](../images/0507.png)

10. Klicken Sie auf **Ausführen**, und überprüfen Sie dann die Abfrageergebnisse im **Ergebnisbereich**. Die Abfrage sollte erfolgreich ausgeführt werden.

    ![Screenshot des Datenbankbereichs im Abfrage-Editor mit dem erfolgreich ausgeführten SQL-Code und der im Ergebnisbereich angezeigten Ausgabe](../images/0508.png)

Herzlichen Glückwunsch! Sie haben eine SQL-Datenbank in Azure erstellt und die Daten in dieser Datenbank erfolgreich abgefragt.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
