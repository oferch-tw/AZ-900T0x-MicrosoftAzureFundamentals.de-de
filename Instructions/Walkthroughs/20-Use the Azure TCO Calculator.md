---
wts:
  title: 20 – Verwenden des Azure-Gesamtbetriebskostenrechners (10 Min.)
  module: 'Module 06: Describe Azure cost management and service level agreements'
ms.openlocfilehash: 8044b922cef99fae814fb6418a33ed7334eb506b
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908166"
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 – Verwenden des Azure-Gesamtbetriebskostenrechners (10 Min.)


In dieser exemplarischen Vorgehensweise verwenden Sie den Gesamtkostenrechner, um einen Kostenvergleichsbericht für eine lokale Umgebung zu erstellen.

**Hinweis:** Diese exemplarische Vorgehensweise enthält Beispieldefinitionen der lokalen Infrastruktur und Workloads für ein typisches Rechenzentrum. Verwenden Sie zum Erstellen eines Gesamtkostenrechner-Berichts die Beispieldefinitionen, oder geben Sie Details Ihrer *tatsächlich* lokalen Infrastruktur und Workloads an.

# <a name="task-1-configure-the-tco-calculator"></a>Aufgabe 1: Konfigurieren des Gesamtbetriebskostenrechners

In dieser Aufgabe fügen wir dem Rechner Infrastrukturinformationen hinzu. 

1. Navigieren Sie in einem Browser zur Seite [Gesamtkostenrechner](https://azure.microsoft.com/en-us/pricing/tco/calculator/).

2. Um Details zu Ihrer lokalen Serverinfrastruktur hinzuzufügen, klicken Sie im Bereich **Workloads definieren** auf **+ Serverworkload hinzufügen**.

    | Einstellungen | Wert |
    | -- | -- |
    | Name | **Server: Windows-VMs** |
    | Workload | **Windows-/Linux-Server** |
    | Umgebung | **Virtuelle Computer** |
    | Betriebssystem | **Windows** |  
    | VMs | **50** |
    | Virtualisierung | **Hyper-V** |
    | Kern(e) | **8**|
    | RAM (GB) | **16** |
    | Optimieren für | **CPU** |
    | Windows Server 2008/2008 R2 | **Deaktiviert** |

3. Wählen Sie **+ Serverworkload hinzufügen** aus, um eine Zeile für eine neue Definition der Serverworkloads zu erstellen. 

    | Einstellungen | Wert |
    | -- | -- |
    | Name | **Server: Linux-VMs** |
    | Workload | **Windows-/Linux-Server** |
    | Umgebung | **Virtuelle Computer** |
    | Betriebssystem | **Linux** |  
    | VMs | **50** |
    | Virtualisierung | **VMware** |
    | Kern(e) | **8**|
    | RAM (GB) | **16** |
    | Optimieren für | **CPU** |
    | Windows Server 2008/2008 R2 | **Deaktiviert** |

4. Klicken Sie im Bereich **Speicher** auf **Speicher hinzufügen**.

    | Einstellungen | Wert |
    | -- | -- |
    | Name | **Serverspeicher** |
    | Speichertyp | **Lokaler Datenträger/SAN** |
    | Datenträgertyp | **Festplattenlaufwerk** |
    | Capacity | **60 TB** |  
    | Backup | **120 TB** |
    | Archivieren | **0 TB** |

5. Fügen Sie im Bereich **Netzwerk** Bandbreite hinzu. 

    | Einstellungen | Wert |
    | -- | -- |
    | Ausgehende Bandbreite | 15 TB|

6. Klicken Sie auf **Weiter**.

7. Prüfen Sie die Optionen, und nehmen Sie erforderliche Anpassungen vor. 

    | Einstellungen | Wert |
    | -- | -- |
    | Währung | **Euro** |

8. Klicken Sie auf **Weiter**.

# <a name="task-2-review-the-results-and-save-a-copy"></a>Aufgabe 2: Überprüfen der Ergebnisse und Speichern einer Kopie

In dieser Aufgabe werden wir die Empfehlungen zur Kosteneinsparung überprüfen und einen Bericht herunterladen. 

1. Lesen Sie die Azure-Empfehlungen und -Visualisierungen zur Kosteneinsparung.

    | Einstellungen | Wert |
    | -- | -- |
    | Zeitraum| **3 Jahre** |
    | Region | **Europa, Norden** |

2. Um die von Ihnen angegebenen Informationen zu ändern, gehen Sie zum Ende der Seite, und klicken Sie auf **Zurück**. 

3. Um eine PDF-Kopie des Berichts zu speichern oder zu drucken, klicken Sie auf **Herunterladen**.

    ![Screenshot des Berichtsbereichs des Gesamtkostenrechners in Azure. Die hervorgehobenen und ausgefüllten Eingabefelder geben an, wie der Zeitraum des Gesamtkostenrechners auf drei Jahre und die Region auf Nordeuropa festgelegt wird. Ein Diagramm zeigt die Kosten für lokale Infrastruktur und Workloads im Vergleich zu den durch die Verwendung von Azure reduzierten Kosten.](../images/2001.png)

Glückwunsch! Sie haben den Gesamtkostenrechner verwendet, um einen Kostenvergleichsbericht für eine lokale Umgebung zu erstellen.
