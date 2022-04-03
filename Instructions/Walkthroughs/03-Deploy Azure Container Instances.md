---
wts:
  title: 03 – Bereitstellen von Azure Container Instances (10 Min.)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 0616be96840b14f7580c7d2b16cb43b211c6e3a2
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908134"
---
# <a name="03---deploy-azure-container-instances-10-min"></a>03 – Bereitstellen von Azure Container Instances (10 Min.)

In dieser exemplarischen Vorgehensweise werden wir einen Container mit Azure Container Instances (ACI) im Azure Portal erstellen, konfigurieren und bereitstellen. Der Container ist eine Welcome to ACI-Webanwendung, die eine statische HTML-Seite anzeigt. 

# <a name="task-1-create-a-container-instance"></a>Aufgabe 1: Erstellen einer Containerinstanz 

In dieser Aufgabe erstellen wir eine neue Containerinstanz für die Webanwendung.  

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **Containerinstanzen**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen, + Neu**. 

3. Geben Sie die folgenden grundlegenden Details für die neue Containerinstanz an (lassen Sie die restlichen Standardeinstellungen unverändert): 

    | Einstellung| Wert|
    |----|----|
    | Subscription | ***Standarddaten verwenden*** |
    | Resource group | **Neue Ressourcengruppe erstellen** |
    | Containername| **mycontainer**|
    | Region | **(USA) USA, Osten** |
    | Imagequelle| **Docker Hub oder andere Registrierung**|
    | Imagetyp| **Public**|
    | Image| **mcr.microsoft.com/azuredocs/aci-helloworld**|
    | Betriebssystemtyp| **Linux** |
    | Size| ***Standard beibehalten***|


4. Konfigurieren Sie die Registerkarte „Netzwerk“ (ersetzen Sie **xxxxx** durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Behalten Sie für alle anderen Einstellungen die Standardwerte bei.

    | Einstellung| Wert|
    |--|--|
    | DNS-Namensbezeichnung| **mycontainerdnsxxxxx** |

    
    **Hinweis**: Ihr Container ist unter „dns-name-label.region.azurecontainer.io“ öffentlich erreichbar. Wenn nach der Bereitstellung die Fehlermeldung **DNS-Namensbezeichnung nicht verfügbar** angezeigt wird, geben Sie eine andere DNS-Namensbezeichnung (xxxxx ersetzen) an, und wiederholen Sie die Bereitstellung. 

5. Klicken Sie auf **Überprüfen + erstellen**, um die automatische Validierung zu starten.

6. Klicken Sie auf **Erstellen**, um die Containerinstanz zu erstellen. 

7. Überwachen Sie die Bereitstellungsseite und die Seite **Benachrichtigungen**. 


# <a name="task-2-verify-deployment-of-the-container-instance"></a>Aufgabe 2: Überprüfen der Bereitstellung der Containerinstanz

In dieser Aufgabe überprüfen wir, ob die Containerinstanz ausgeführt wird, indem wir sicherstellen, dass die Willkommensseite angezeigt wird.

1. Klicken Sie nach Abschluss der Bereitstellung auf **Zu Ressource wechseln**, verknüpfen Sie das Blatt „Bereitstellung“ oder die Verknüpfung mit der Ressource im Benachrichtigungsbereich.

2. Stellen Sie auf dem Blatt **Überblick** von **mycontainer** sicher, dass der **Status** Ihres Containers **Wird ausgeführt** lautet. 

3. Suchen Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN).

    ![Screenshot des Übersichtsbereichs für den neu erstellten Container im Azure-Portal mit hervorgehobenem FQDN. ](../images/0202.png)

2. Kopieren Sie den FQDN des Containers in eine neue Registerkarte in Ihrem Webbrowser, und drücken Sie die **Eingabetaste**. Die Willkommensseite sollte angezeigt werden. 

    ![Screenshot der ACI-Begrüßungsnachricht, die in einem Webbrowser angezeigt wird.](../images/0203.png)


**Glückwunsch!** Sie haben Azure Container Instances im Azure-Portal verwendet, um eine Anwendung in einem Container bereitzustellen.

**Hinweis:** Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe bei Bedarf entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
