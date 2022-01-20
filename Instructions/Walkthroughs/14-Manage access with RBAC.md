---
wts:
    title: '14 - Verwalten des Zugriffs mit RBAC (5 Min.)'
    module: 'Modul 05: Beschreiben der Features für Identität, Governance, Datenschutz und Compliance'
---
# 14 – Zugriff mit RBAC verwalten (5 Min.)

In dieser exemplarischen Vorgehensweise weisen wir Berechtigungsrollen zu Ressourcen zu und sehen uns Protokolle an.

# Aufgabe 1: Anzeigen und Zuweisen von Rollen

In dieser Aufgabe weisen wir die Rolle „Mitwirkender für virtuelle Computer“ zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Ressourcengruppen**, wählen Sie ihn aus, und klicken Sie auf **+Hinzufügen, +Erstellen, +Neu**.

3. Erstellen einer neuen Ressourcengruppe Klicken Sie auf **Erstellen**, wenn Sie fertig sind. 

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **Standardwert verwenden** |
    | Ressourcengruppe | **myRGRBAC** |
    | Region | **(USA) USA, Osten** |
   

4. Erstellen Sie **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**.

5. **Aktualisieren** Sie die Seite „Ressourcengruppe“, und klicken Sie auf den Eintrag, der die neu erstellte Ressourcengruppe darstellt.

6. Klicken Sie auf das Blatt **Zugriffssteuerung (IAM)**, und wechseln Sie dann auf die Registerkarte **Rollen**. Blättern Sie durch die große Anzahl an Rollendefinitionen, die verfügbar sind. Verwenden Sie die Informationssymbole, um eine Vorstellung von den Berechtigungen der einzelnen Rollen zu erhalten. Beachten Sie, dass es auch Informationen zur Anzahl der Benutzer und Gruppen gibt, die jeder Rolle zugewiesen sind.

![Bild](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Wechseln Sie zur Registerkarte **Rollenzuweisungen** des Blatts **myRGRBAC - Zugriffssteuerung (IAM)**, klicken Sie auf **Hinzufügen** und dann auf **Rollenzuweisung hinzufügen**. Suchen Sie nach der Rolle „Mitwirkender für virtuelle Computer“, und wählen Sie diese Option aus. Wechseln Sie zur Registerkarte „Mitglieder“, und weisen Sie folgende Zugriffe zu: Auf Benutzer, Gruppe oder Dienstprinzipal. Klicken Sie dann auf „+ Mitglieder auswählen“, und geben Sie Ihren Namen in die Popup-Suchfunktion ein. Klicken Sie dann auf „Auswählen“. Wählen Sie anschließend „Überprüfen und zuweisen“.

    
    ![Bild](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **Hinweis:** Mit der Rolle „Mitwirkender für virtuelle Computer“ können Sie virtuelle Computer verwalten, jedoch nicht auf deren Betriebssystem zugreifen oder das virtuelle Netzwerk und das Speicherkonto verwalten, mit denen sie verbunden sind.

  

8. **Aktualisieren** Sie die Seite „Rollenzuweisungen“ und stellen Sie sicher, dass Sie jetzt als Mitwirkender eines virtuellen Computers aufgeführt sind. 

    **HINWEIS**: Diese Zuweisung gewährt Ihnen keine zusätzlichen Berechtigungen, da Ihr Konto bereits über die Besitzerrolle verfügt, die alle mit der Rolle „Mitwirkender“ verbundenen Berechtigungen enthält.

# Aufgabe 2: Überwachen von Rollenzuweisungen und Entfernen einer Rolle

In dieser Aufgabe werden wir anhand des Aktivitätsprotokolls die Rollenzuweisung überprüfen und anschließend die Rolle entfernen. 

1. Klicken Sie auf dem Blatt „myRGRBAC Ressourcengruppen“ auf **Aktivitätsprotokoll**.

2. Klicken Sie auf **Filter hinzufügen**, wählen Sie **Vorgang** und dann **Rollenzuweisung erstellen** aus.

    ![Screenshot der Aktivitätsprotokollseite mit konfiguriertem Filter.](../images/1503.png)

3. Überprüfen Sie, ob Ihre Rollenzuweisung im Aktivitätsprotokoll angezeigt wird. 

    **HINWEIS**: Wissen Sie, wie Sie Ihre Rollenzuweisung entfernen können?

Herzlichen Glückwunsch! Sie haben eine Ressourcengruppe erstellt, ihr eine Zugriffsrolle zugewiesen und sich Aktivitätsprotokolle angesehen. 

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.

