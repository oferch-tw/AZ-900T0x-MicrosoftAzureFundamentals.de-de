---
wts:
    title: '03 - Bereitstellen von Azure Container Instances (10 Min.)'
    module: 'Modul 02 - Azure-Kerndienste (Workloads)'
---

# 03 – Bereitstellen von Azure Container Instances (10 Min.)

In dieser exemplarischen Vorgehensweise erstellen, konfigurieren und implementieren wir einen Container mit Azure Container Instances (ACI) im Azure-Portal. Der Container ist eine „Welcome to ACI“-Webanwendung, die eine statische HTML-Seite anzeigt. 

# Aufgabe 1: Containerinstanz erstellen 

In dieser Aufgabe erstellen wir eine neue Containerinstanz für die Webanwendung. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Containerinstanzen**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**. 

3. Geben Sie die folgenden grundlegenden Details für die neue Containerinstanz an (belassen Sie die Standardeinstellungen für alles andere so, wie sie sind): 

	| Einstellung| Wert|
	|----|----|
	| Abonnement | ***Standardwert verwenden*** |
	| Ressourcengruppe | **Erstellen einer neuen Ressourcengruppe** |
	| Containername| **mycontainer**|
	| Region | **(USA) USA, Osten** |
	| Imagequelle| **Docker Hub oder andere Registrierung**|
	| Imagetyp| **Öffentlich**|
	| Bild| **mcr.microsoft.com/azuredocs/aci-helloworld**|
	| Betriebssystemtyp| **Linux** |
	| Größe| ***Belassen Sie die Standardeinstellung***|


4. Konfigurieren Sie die Registerkarte „Netzwerk“ (ersetzen Sie **xxxx** durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Behalten Sie für andere Einstellungen die Standardwerte bei.

	| Einstellung| Wert|
	|--|--|
	| DNS-Namensbezeichnung| **mycontainerdnsxxxxx** |

	
	**HINWEIS**: Ihr Container ist unter „dns-name-label.region.azurecontainer.io“ öffentlich erreichbar. Falls nach der Bereitstellung die Fehlermeldung **DNS-Namensbezeichnung nicht verfügbar** angezeigt wird, geben Sie eine andere DNS-Namensbezeichnung an (ersetzen Sie den Teil „xxxxx“), und wiederholen Sie die Bereitstellung. 

5. Klicken Sie auf **Überprüfen + Erstellen**, um die automatische Validierung zu starten.

6. Klicken Sie auf **Erstellen**, um die Containerinstanz zu erstellen. 

7. Überwachen Sie die Bereitstellungsseite und die Seite **Benachrichtigungen**. 


# Aufgabe 2: Überprüfen der Bereitstellung der Containerinstanz

In dieser Aufgabe überprüfen wir, ob die Containerinstanz ausgeführt wird, indem wir sicherstellen, dass die Willkommensseite angezeigt wird.

1. Klicken Sie nach Abschluss der Bereitstellung auf **Zu Ressource wechseln**, verknüpfen Sie das Blatt „Bereitstellung“ oder die Verknüpfung mit der Ressource im Benachrichtigungsbereich.

2. Stellen Sie auf dem Blatt **Überblick** von **mycontainer** sicher, dass der **Status** Ihres Containers **Wird ausgeführt** lautet. 

3. Suchen Sie den vollqualifizierten Domänennamen (FQDN).

	![Screenshot des Übersichtsbereichs für den neu erstellten Container im Azure-Portal mit hervorgehobenem FQDN. ](../images/0202.png)

2. Kopieren Sie den vollqualifizierten Domänennamen des Containers in eine neue Registerkarte im Webbrowser, und drücken Sie die **Eingabetaste**. Die Startseite sollte angezeigt werden. 

	![Screenshot der ACI-Begrüßungsnachricht, die in einem Webbrowser angezeigt wird.](../images/0203.png)


**Herzlichen Glückwunsch!** Sie haben das Azure-Portal verwendet, um eine Anwendung in einem Container in Azure Container Instances bereitzustellen.

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
