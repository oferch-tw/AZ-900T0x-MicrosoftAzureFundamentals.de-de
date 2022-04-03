---
wts:
  title: 12 – Implementieren von Azure Key Vault (5 Min.)
  module: 'Module 04: Describe general security and network security features'
ms.openlocfilehash: 1381900fc934ddbc092faf42f0b0a366364a9872
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907741"
---
# <a name="12---implement-azure-key-vault-5-min"></a>12 – Implementieren von Azure Key Vault (5 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir einen Azure-Schlüsseltresor und erstellen dann ein Kennwortgeheimnis in diesem Schlüsseltresor. Dadurch wird ein sicher gespeichertes, zentral verwaltetes Kennwort für die Verwendung mit Anwendungen bereitgestellt.

# <a name="task-1-create-an-azure-key-vault"></a>Aufgabe 1: Erstellen einer Azure Key Vault-Instanz 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** die Option **Schlüsseltresore**, und wählen Sie sie aus. Wählen Sie dann **+ Hinzufügen +Neu +Erstellen** aus.

3. Konfigurieren Sie den Schlüsseltresor (ersetzen Sie **xxxx** im Namen des Schlüsseltresors durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Subscription | **Standarddaten verwenden** |
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Name des Schlüsseltresors | **keyvaulttestxxx** |
    | Location | **USA, Osten** |
    | Tarif | **Standard** |
    
    **Hinweis** Ersetzen Sie **xxxx** so, dass ein eindeutiger Name entsteht.
4. Klicken Sie auf **Überprüfen und erstellen** und dann auf **Erstellen**. 

5. Wenn der neue Schlüsseltresor bereitgestellt ist, klicken Sie auf **Zu Ressource wechseln**. Sie können aber auch nach Ihrem neuen Schlüsseltresor suchen. 

6. Klicken Sie auf die Registerkarte **Übersicht** für den Schlüsseltresor, und notieren Sie sich den **Tresor-URI**. Anwendungen, die Ihren Tresor über die REST-APIs verwenden, benötigen diesen URI.

7. Nehmen Sie sich einen Moment Zeit, um einige der anderen wichtigen Schlüsseltresoroptionen zu durchsuchen. Prüfen Sie unter **Einstellungen** die Einträge **Schlüssel**, **Geheimnisse**, **Zertifikate**, **Zugriffsrichtlinien** und **Firewalls und virtuelle Netzwerke**.

    **Hinweis:** Ihr Azure-Konto ist das einzige, das berechtigt ist, Vorgänge für diesen neuen Tresor auszuführen. Wenn Sie wünschen, können Sie dies im Abschnitt **Einstellungen** unter **Zugriffsrichtlinien** ändern.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>Aufgabe 2: Hinzufügen eines Geheimnisses zum Schlüsseltresor
        
In dieser Aufgabe werden wir dem Schlüsseltresor ein Kennwort hinzufügen. 

1. Klicken Sie unter **Einstellungen** auf **Geheimnisse** und dann auf **Generieren/Importieren**.

2. Konfigurieren Sie das Geheimnis. Belassen Sie für die anderen Werte die Standardeinstellungen. Beachten Sie, dass Sie ein Aktivierungs- und Ablaufdatum festlegen können. Beachten Sie, dass Sie das Geheimnis auch deaktivieren können.

    | Einstellung | Wert | 
    | --- | --- |
    | Uploadoptionen | **Manuell** |
    | Name | **ExamplePassword** |
    | Wert | **hVFkk96** |

3. Klicken Sie auf **Erstellen**.

4. Sobald das Geheimnis erfolgreich erstellt wurde, klicken Sie auf **ExamplePassword**. Beachten Sie, dass der Status **Aktiviert** lautet.

5. Wählen Sie den soeben erstellten geheimen Schlüssel aus, und notieren Sie sich die **Geheimnis-ID**. Dies ist der URL-Wert, den Sie jetzt mit Anwendungen verwenden können. Er bietet ein zentral verwaltetes und sicher gespeichertes Kennwort. 

6. Klicken Sie auf die Schaltfläche **Geheimniswert anzeigen**, um das zuvor angegebene Kennwort anzuzeigen.


Glückwunsch! Sie haben einen Azure-Schlüsseltresor erstellt und anschließend in diesem Schlüsseltresor ein Kennwortgeheimnis erstellt. Damit steht ein sicher gespeichertes, zentral verwaltetes Kennwort für die Nutzung mit Anwendungen zur Verfügung.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
