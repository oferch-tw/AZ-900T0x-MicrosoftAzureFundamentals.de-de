---
wts:
    title: '12 - Implementieren von Azure Key Vault (5 Min.)'
    module: 'Modul 04: Beschreiben der Features für allgemeine Sicherheit und Netzwerksicherheit'
---
# 12 – Implementieren von Azure Key Vault (5 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir einen Azure-Schlüsseltresor und erstellen dann ein Kennwortgeheimnis in diesem Schlüsseltresor. Dadurch wird ein sicher gespeichertes, zentral verwaltetes Kennwort für die Verwendung mit Anwendungen bereitgestellt.

# Aufgabe 1: Einen Azure Key Vault erstellen 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Schlüsseltresore**, wählen Sie ihn aus, und wählen Sie dann **+Hinzufügen, +Erstellen, +Neu** aus.

3. Konfigurieren Sie den Schlüsseltresor (ersetzen Sie **xxxx** im Namen des Schlüsseltresors durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Standardwert verwenden** |
    | Ressourcengruppe | **Erstellen einer neuen Ressourcengruppe** |
    | Schlüsseltresorname | **keyvaulttestxxx** |
    | Standort | **USA, Osten** |
    | Tarif | **Standard** |
    
    **Hinweis** Ersetzen Sie **xxxx**, um einen eindeutigen Namen zu erhalten.
4. Klicken Sie auf **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**. 

5. Wenn der neue Schlüsseltresor bereitgestellt ist, klicken Sie auf **Zu Ressource wechseln**. Sie können aber auch nach Ihrem neuen Schlüsseltresor suchen. 

6. Klicken Sie auf die Registerkarte **Übersicht** für den Schlüsseltresor, und notieren Sie sich den **Vault-URI**. Anwendungen, die Ihren Tresor über die REST-APIs nutzen, müssen diesen URI verwenden.

7. Nehmen Sie sich einen Moment Zeit, um einige der anderen wichtigen Schlüsseltresoroptionen zu durchsuchen. Prüfen Sie unter **Einstellungen** die Einträge **Schlüssel**, **Geheimnisse**, **Zertifikate**, **Zugriffsrichtlinien** und **Firewalls und virtuelle Netzwerke**.

    **HINWEIS**: Ihr Azure-Konto ist das einzige, das berechtigt ist, Vorgänge für diesen neuen Tresor auszuführen. Wenn Sie wünschen, können Sie dies im Abschnitt **Einstellungen** unter **Zugriffsrichtlinien** ändern.

# Aufgabe 2: Hinzufügen eines Geheimnisses zum Schlüsseltresor
        
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

5. Wählen Sie das soeben erstellte Geheimnis aus, und notieren Sie sich die **Geheimnis-ID**. Dies ist der URL-Wert, den Sie jetzt mit Anwendungen verwenden können. Er bietet ein zentral verwaltetes und sicher gespeichertes Kennwort. 

6. Klicken Sie auf die Schaltfläche **Geheimniswert anzeigen**, um das zuvor angegebene Kennwort anzuzeigen.


Herzlichen Glückwunsch! Sie haben einen Azure-Schlüsseltresor erstellt und anschließend in diesem Schlüsseltresor ein Kennwortgeheimnis erstellt. Damit steht ein sicher gespeichertes, zentral verwaltetes Kennwort für die Nutzung mit Anwendungen zur Verfügung.

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
