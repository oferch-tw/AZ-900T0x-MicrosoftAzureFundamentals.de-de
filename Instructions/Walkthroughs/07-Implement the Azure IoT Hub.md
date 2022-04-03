---
wts:
  title: 07 – Implementieren eines Azure IoT Hubs (10 Min.)
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: c2098875e07323c84eac8a405c8a59ad70eaabcd
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908047"
---
# <a name="07---implement-an-azure-iot-hub-10-min"></a>07 – Implementieren eines Azure IoT Hubs (10 Min.)

In dieser exemplarischen Vorgehensweise konfigurieren wir einen neuen Azure IoT Hub im Azure-Portal und authentifizieren dann eine Verbindung zu einem IoT-Gerät mithilfe des Raspberry Pi-Gerätesimulators. Sensordaten und Nachrichten werden vom Raspberry Pi-Simulator an Ihren Azure IoT Hub übergeben, und Sie sehen Metriken für die Meldungsaktivität im Azure-Portal.

# <a name="task-1-create-an-iot-hub"></a>Aufgabe 1: Erstellen eines IoT-Hubs 

In dieser Aufgabe erstellen wir einen IoT-Hub. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **IoT Hub**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**.

3. Auf der Registerkarte **Grundlagen** des Blatts **IoT-Hub** füllen Sie die Felder mit den folgenden Details aus (ersetzen Sie **xxxx** im Namen des Speicherkontos durch Buchstaben und Ziffern, sodass der Name global eindeutig ist):

    | Einstellungen | Wert |
    |--|--|
    | Subscription | **Standarddaten beibehalten** |
    | Ressourcengruppe | **Neue Ressourcengruppe erstellen** |
    | IoT Hub-Name | **my-hub-groupxxxxx** |
    | Region | **USA, Osten** |

    **Hinweis**: Denken Sie daran, **xxxxx** zu ändern, sodass sich ein eindeutiger **IoT Hub-Name** ergibt.

4. Wechseln Sie zur Registerkarte **Verwaltung**, und verwenden Sie das Dropdownfeld, um die **Preis- und Skalierungsebene** festzulegen auf **S1: Standard-Tarif**.

5. Klicken Sie auf **Überprüfen + erstellen**.

6. Klicken Sie auf die Schaltfläche **Erstellen**, um mit der Erstellung Ihrer neuen Azure IoT Hub-Instanz zu beginnen.

7. Warten Sie, bis die Azure IoT Hub-Instanz bereitgestellt ist. 

# <a name="task-2-add-an-iot-device"></a>Aufgabe 2: Hinzufügen eines IoT-Geräts

In dieser Aufgabe fügen wir dem IoT-Hub ein IoT-Gerät hinzu. 

1. Wenn die Bereitstellung abgeschlossen ist, klicken Sie auf dem Blatt „Bereitstellung“ auf **Zur Ressource wechseln**. Alternativ suchen Sie auf dem Blatt **Alle Dienste** nach **IoT Hub**, wählen diese Option aus und suchen Ihre neue IoT Hub-Instanz

    ![Screenshot der Benachrichtigungen „Die Bereitstellung wird ausgeführt“ und „Bereitstellung erfolgreich“ im Azure-Portal.](../images/0601.png)

2. Scrollen Sie zum Hinzufügen eines neuen IoT-Geräts nach unten zum Abschnitt **Geräteverwaltung**, und klicken Sie auf **Geräte**. Klicken Sie dann auf **+ Gerät hinzufügen**.

    ![Screenshot des Bereichs „IoT-Geräte“, der auf dem IoT Hub-Navigationsblatt im Azure-Portal hervorgehoben ist. Die Schaltfläche „Neu“ ist hervorgehoben, um zu veranschaulichen, wie dem IoT-Hub eine neue IoT-Geräteidentität hinzugefügt wird.](../images/0602.png)

3. Geben Sie einen Namen für Ihr neues IoT-Gerät ein ( **myRaspberryPi**), und klicken Sie auf die Schaltfläche **Speichern**. Dadurch wird eine neue IoT-Geräteidentität in Ihrem Azure IoT Hub erstellt.

4. Wenn Sie Ihr neues Gerät nicht sehen, **Aktualisieren** Sie die Seite „IoT-Geräte“. 

5. Wählen Sie **myRaspberryPi** aus, und kopieren Sie den Wert von **Primäre Verbindungszeichenfolge**. Mit diesem Schlüssel werden Sie in der nächsten Aufgabe eine Verbindung zum Raspberry Pi-Simulator authentifizieren.

    ![Screenshot der Seite „Primäre Verbindungszeichenfolge“ mit hervorgehobenem Kopiersymbol.](../images/0603.png)

# <a name="task-3-test-the-device-using-a-raspberry-pi-simulator"></a>Aufgabe 3: Testen Sie das Gerät mit einem Raspberry Pi-Simulator.

In dieser Aufgabe testen wir unser Gerät mit dem Raspberry Pi-Simulator. 

1. Öffnen Sie eine neue Registerkarte im Webbrowser, und öffnen Sie den folgenden Link: https://aka.ms/RaspPi. Daraufhin wird ein Raspberry Pi-Simulator geöffnet. Lesen Sie etwas mehr über den Raspberry Pi-Simulator, wenn Sie Zeit dafür haben. Wenn Sie fertig sind, wählen Sie „**X**“ aus, um das Popupfenster zu schließen.

2. Suchen Sie im Codebereich auf der rechten Seite die Zeile mit der Zeichenfolge „const connectionString =“. Ersetzen Sie diese Zeile durch die Verbindungszeichenfolge, die Sie im Azure-Portal kopiert haben. Beachten Sie, dass die Verbindungszeichenfolge Einträge für DeviceId (**myRaspberryPi**) und SharedAccessKey enthält.

    ![Screenshot des Codierungsbereichs im Raspberry Pi-Simulator.](../images/0604.png)

3. Klicken Sie auf **Ausführen** (unterhalb des Codebereichs), um die Anwendung auszuführen. Die Konsolenausgabe sollte die Sensordaten und Nachrichten anzeigen, die vom Raspberry Pi-Simulator an Ihren Azure IoT Hub gesendet werden. Daten und Nachrichten werden jedes Mal gesendet, wenn die Raspberry Pi-Simulator-LED blinkt. 

    ![Screenshot der Raspberry Pi.Simulator-Konsole.  Die Konsolenausgabe zeigt Sensordaten und Nachrichten an, die vom Raspberry Pi-Simulator an Azure IoT Hub gesendet wurden.](../images/0605.png)

5. Klicken Sie auf **Beenden**, um das Senden von Daten zu beenden.

6. Kehren Sie zum Azure-Portal zurück.

7. Wechseln Sie zum IoT Hub-Blatt **Überblick**, und scrollen Sie nach unten zur Information **IoT Hub-Nutzung**, um die Nutzung anzuzeigen. Ändern Sie den Zeitraum unter **Datenanzeige für die letzten:** , um die Daten aus der letzten Stunde anzuzeigen.

    ![Screenshot der Metriken im IoT-Hub-Nutzungsbereich des Azure-Portals.](../images/0606.png)


Glückwunsch! Sie haben Azure IoT Hub so eingerichtet, dass Sensordaten von einem IoT-Gerät erfasst werden.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
