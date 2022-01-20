---
wts:
    title: '05 - Erstellen von Blob-Speicher (5 Min.)'
    module: 'Modul 02 - Azure-Kerndienste (Workloads)'
---
# 05 – Blob-Speicher erstellen (5 Min.)

In dieser exemplarischen Vorgehensweise erstellen wir ein Speicherkonto und arbeiten dann mit Blob Storage-Dateien.

# Aufgabe 1: Speicherkonto erstellen 

In dieser Aufgabe erstellen wir ein neues Speicherkonto. 

1. Melden Sie sich beim Azure-Portal an unter: <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Speicherkonten**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**. 

3. Geben Sie auf dem Blatt **Speicherkonto erstellen** auf der Registerkarte **Grundlagen** die folgenden Informationen ein (ersetzen Sie **xxxx** im Speicherkontonamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Standardwert beibehalten** |
    | Ressourcengruppe | **Erstellen einer neuen Ressourcengruppe** |
    | Speicherkontoname | **storageaccountxxxxx** |
    | Standort | **(USA) USA, Osten**  |
    | Leistung | **Standard** |
    | Redundanz | **Lokal redundanter Speicher (LRS)** |
    
    **Hinweis** - Denken Sie daran, **xxxxx** so zu ändern, dass sich ein eindeutiger **Speicherkontoname** ergibt

5. Klicken Sie auf **Überprüfen + erstellen**, um die Einstellungen Ihres Speicherkontos zu überprüfen und Azure die Validierung der Konfiguration zu ermöglichen. 

6. Klicken Sie nach der Validierung auf **Erstellen**. Warten Sie auf die Benachrichtigung, dass das Konto erfolgreich erstellt wurde. 

7. Suchen Sie auf der Homepage die Option **Speicherkonten**, und wählen Sie sie aus. Stellen Sie sicher, dass Ihr neues Speicherkonto aufgeführt ist.

    ![Screenshot des neu erstellten Speicherkontos im Azure-Portal.](../images/0401.png)

# Aufgabe 2: Arbeiten mit Blob-Speicher

In dieser Aufgabe erstellen wir einen Blob-Container und laden eine Blob-Datei hoch. 

1. Klicken Sie auf den Namen des neuen Speicherkontos, scrollen Sie zum Abschnitt **Datenspeicherung** im linken Menü, und klicken Sie auf **Container**.

2. Klicken Sie auf **+ Container**, und vervollständigen Sie die Informationen. Über das Informationssymbol erhalten Sie weitere Informationen. Klicken Sie abschließend auf **Erstellen**.


    | Einstellung | Wert |
    | --- | --- |
    | Name | **container1**  |
    | Öffentliche Zugriffsebene| **Privat (kein anonymer Zugang)** |
  

    ![Screenshot des neu erstellten Blob-Containers im Speicherkonto im Azure-Portal.](../images/0402.png)

4. Öffnen Sie ein neues Browserfenster, und suchen Sie mit **Bing** nach einem Bild von einer Blume. Klicken Sie mit der rechten Maustaste auf das Bild, und speichern Sie es auf Ihrer VM. 

6. Wechseln Sie zurück zum Portal, klicken Sie auf **container1**, und wählen Sie **Hochladen** aus.

5. Suchen Sie nach der Bilddatei, die Sie soeben auf Ihrem lokalen Computer gespeichert haben. Wählen Sie die Datei aus, und wählen Sie „Hochladen“ aus.

   
6. Klicken Sie auf den Pfeil **Erweitert**, übernehmen Sie die Standardwerte, überprüfen Sie die verfügbaren Optionen, und klicken Sie dann auf **Hochladen**.

    **HINWEIS**: Auf diese Weise können Sie beliebig viele Blobs hochladen. Neue Blobs werden im Container aufgelistet.

7. Klicken Sie nach dem Hochladen der Datei mit der rechten Maustaste auf die Datei und beachten Sie die Optionen „Anzeigen/Bearbeiten“, „Herunterladen“, „Eigenschaften“ und „Löschen“. 

8. Falls Sie Zeit dafür haben, sehen Sie sich die Optionen für Dateien, Tabellen und Warteschlangen an.

# Aufgabe 3: Überwachen des Speicherkontos

1. Kehren Sie zum Blatt „Speicherkonto“ zurück, und klicken Sie auf **Diagnose und Problembehandlung**. 

2. Machen Sie sich mit einigen der häufigsten Speicherprobleme vertraut. Beachten Sie, dass hier mehrere Problembehandlungen angezeigt werden.

3. Scrollen Sie auf dem Blatt „Speicherkonten“ nach unten zum Abschnitt **Überwachung**, und klicken Sie auf **Insights**. Beachten Sie, dass Informationen zu Fehlern, Leistung, Verfügbarkeit und Kapazität vorhanden sind. Ihre Informationen werden davon abweichen.

    ![Screenshot der Seite „Insights“ des Speicherkontos.](../images/0403.png)

Herzlichen Glückwunsch! Sie haben ein Speicherkonto erstellt und dann mit Speicherblobs gearbeitet.

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
