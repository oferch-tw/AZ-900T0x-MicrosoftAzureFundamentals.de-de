---
wts:
  title: 20 – Verwenden des Azure-Gesamtbetriebskostenrechners (10 Min.)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 – Verwenden des Azure-Gesamtbetriebskostenrechners (10 Min.)


In dieser exemplarischen Vorgehensweise verwenden Sie den Gesamtkostenrechner, um einen Kostenvergleichsbericht für eine lokale Umgebung zu erstellen.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This walkthrough provides example definitions of on-premises infrastructure and workloads for a typical datacenter. To create a TCO Calculator report, use the example definitions or provide details of your <bpt id="p1">*</bpt>actual<ept id="p1">*</ept> on-premises infrastructure and workloads.

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

    ![Screenshot of the report pane of the tco calculator in Azure. The highlighted and completed input fields indicates how set the tco calculator timeframe to three years and the region to north europe. A graph shows the cost of on-premises infrastructure and workloads off-set against the reduced cost of using Azure.](../images/2001.png)

Congratulations! You have used the TCO Calculator to generate a cost comparison report for an on-premises environment.
