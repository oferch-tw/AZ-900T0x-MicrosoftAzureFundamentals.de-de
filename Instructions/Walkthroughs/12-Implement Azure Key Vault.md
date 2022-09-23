---
wts:
  title: 12 – Implementieren von Azure Key Vault (5 Min.)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="12---implement-azure-key-vault-5-min"></a>12 – Implementieren von Azure Key Vault (5 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir einen Azure-Schlüsseltresor und erstellen dann ein Kennwortgeheimnis in diesem Schlüsseltresor. Dadurch wird ein sicher gespeichertes, zentral verwaltetes Kennwort für die Verwendung mit Anwendungen bereitgestellt.

# <a name="task-1-create-an-azure-key-vault"></a>Aufgabe 1: Erstellen einer Azure Key Vault-Instanz 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** die Option **Schlüsseltresore**, und wählen Sie sie aus. Wählen Sie dann **+ Hinzufügen +Neu +Erstellen** aus.

3. Configure the key vault (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the key vault with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | Einstellung | Wert | 
    | --- | --- |
    | Subscription | **Standarddaten verwenden** |
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Name des Schlüsseltresors | **keyvaulttestxxx** |
    | Location | **USA, Osten** |
    | Tarif | **Standard** |
    
    **Hinweis** Ersetzen Sie **xxxx** so, dass ein eindeutiger Name entsteht.
4. Klicken Sie auf **Überprüfen und erstellen** und dann auf **Erstellen**. 

5. Once the new key vault is provisioned, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept>. Or you can locate your new key vault by searching for it. 

6. Click on the key vault <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> tab and take note of the <bpt id="p2">**</bpt>Vault URI<ept id="p2">**</ept>. Applications that use your vault through the REST APIs will need this URI.

7. Take a moment to browse through some of the other key vault options. Under <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> review <bpt id="p2">**</bpt>Keys<ept id="p2">**</ept>, <bpt id="p3">**</bpt>Secrets<ept id="p3">**</ept>, <bpt id="p4">**</bpt>Certificates<ept id="p4">**</ept>, <bpt id="p5">**</bpt>Access Policies<ept id="p5">**</ept>, <bpt id="p6">**</bpt>Firewalls and virtual networks<ept id="p6">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your Azure account is the only one authorized to perform operations on this new vault. You can modify this if you wish in the <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> and then the <bpt id="p2">**</bpt>Access policies<ept id="p2">**</ept> section.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>Aufgabe 2: Hinzufügen eines Geheimnisses zum Schlüsseltresor
        
In dieser Aufgabe werden wir dem Schlüsseltresor ein Kennwort hinzufügen. 

1. Klicken Sie unter **Einstellungen** auf **Geheimnisse** und dann auf **Generieren/Importieren**.

2. Configure the secret. Leave the other values at their defaults. Notice you can set an activation and expiration date. Notice you can also disable the secret.

    | Einstellung | Wert | 
    | --- | --- |
    | Uploadoptionen | **Manuell** |
    | Name | **ExamplePassword** |
    | Wert | **hVFkk96** |

3. Klicken Sie auf **Erstellen**.

4. Sobald das Geheimnis erfolgreich erstellt wurde, klicken Sie auf **ExamplePassword**. Beachten Sie, dass der Status **Aktiviert** lautet.

5. Select the secret you just created, note the the <bpt id="p1">**</bpt>Secret Identifier<ept id="p1">**</ept>. This is the url value that you can now use with applications. It provides a centrally managed and securely stored password. 

6. Klicken Sie auf die Schaltfläche **Geheimniswert anzeigen**, um das zuvor angegebene Kennwort anzuzeigen.


Konfigurieren Sie den Schlüsseltresor (ersetzen Sie **xxxx** im Namen des Schlüsseltresors durch Buchstaben und Ziffern, sodass der Name global eindeutig ist).

Belassen Sie ansonsten die Standardeinstellungen.
