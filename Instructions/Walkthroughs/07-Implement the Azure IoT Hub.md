---
wts:
  title: 07 – Implementieren eines Azure IoT Hubs (10 Min.)
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="07---implement-an-azure-iot-hub-10-min"></a>07 – Implementieren eines Azure IoT Hubs (10 Min.)

In this walkthrough, we will configure a new Azure IoT Hub in Azure Portal, and then authenticate a connection to an IoT device using the online Raspberry Pi device simulator. Sensor data and messages are passed from the Raspberry Pi simulator to your Azure IoT Hub, and you view metrics for the messaging activity in Azure Portal.

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

1. When the deployment has completed, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept> from the deployment blade. Alternatively, from the <bpt id="p1">**</bpt>All services<ept id="p1">**</ept> blade, search for and select <bpt id="p2">**</bpt>IoT Hub<ept id="p2">**</ept> and locate your new IoT Hub instance

    ![Screenshot der Benachrichtigungen „Die Bereitstellung wird ausgeführt“ und „Bereitstellung erfolgreich“ im Azure-Portal.](../images/0601.png)

2. To add a new IoT device, scroll down to the <bpt id="p1">**</bpt>Device management<ept id="p1">**</ept> section and click <bpt id="p2">**</bpt>Devices<ept id="p2">**</ept>. Then, click <bpt id="p1">**</bpt>+ Add Device<ept id="p1">**</ept>.

    ![In dieser exemplarischen Vorgehensweise konfigurieren wir einen neuen Azure IoT Hub im Azure-Portal und authentifizieren dann eine Verbindung zu einem IoT-Gerät mithilfe des Raspberry Pi-Gerätesimulators.](../images/0602.png)

3. Sensordaten und Nachrichten werden vom Raspberry Pi-Simulator an Ihren Azure IoT Hub übergeben, und Sie sehen Metriken für die Meldungsaktivität im Azure-Portal.

4. Wenn Sie Ihr neues Gerät nicht sehen, **Aktualisieren** Sie die Seite „IoT-Geräte“. 

5. Select <bpt id="p1">**</bpt>myRaspberryPi<ept id="p1">**</ept> and copy the <bpt id="p2">**</bpt>Primary Connection String<ept id="p2">**</ept> value. You will use this key in the next task to authenticate a connection to the Raspberry Pi simulator.

    ![Screenshot der Seite „Primäre Verbindungszeichenfolge“ mit hervorgehobenem Kopiersymbol.](../images/0603.png)

# <a name="task-3-test-the-device-using-a-raspberry-pi-simulator"></a>Aufgabe 3: Testen Sie das Gerät mit einem Raspberry Pi-Simulator.

In dieser Aufgabe testen wir unser Gerät mit dem Raspberry Pi-Simulator. 

1. Open a new tab in the web browser and type this shortcut link <ph id="ph1">https://aka.ms/RaspPi</ph>. It will take you to a Raspberry Pi Simulator site. If you have time, read about the Raspberry Pi simulator. When done select "<bpt id="p1">**</bpt>X<ept id="p1">**</ept>" to close the pop-up window.

2. In the code area on the right side, locate the line with 'const connectionString ='. Replace it with the connection string you copied from the Azure portal. Note that the connection sting includes the DeviceId (<bpt id="p1">**</bpt>myRaspberryPi<ept id="p1">**</ept>) and SharedAccessKey entries.

    ![Screenshot des Codierungsbereichs im Raspberry Pi-Simulator.](../images/0604.png)

3. Click <bpt id="p1">**</bpt>Run<ept id="p1">**</ept> (below the code area) to run the application. The console output should show the sensor data and messages that are sent from the Raspberry Pi simulator to your Azure IoT Hub. Data and messages are sent each time the Raspberry Pi simulator LED flashes. 

    ![Screenshot of the Raspberry Pi simulator console.  The console output shows sensor data and messages sent from the Raspberry Pi simulator to Azure IoT Hub.](../images/0605.png)

5. Klicken Sie auf **Beenden**, um das Senden von Daten zu beenden.

6. Kehren Sie zum Azure-Portal zurück.

7. Switch the IoT Hub <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> blade and scroll down to the <bpt id="p2">**</bpt>IoT Hub Usage<ept id="p2">**</ept> information to view usage. Change your timeframe in the <bpt id="p1">**</bpt>show data for last<ept id="p1">**</ept> to see data in the last hour.

    ![Screenshot der Metriken im IoT-Hub-Nutzungsbereich des Azure-Portals.](../images/0606.png)


Congratulations! You have set up Azure IoT Hub to collect sensor data from an IoT device.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
