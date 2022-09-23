---
wts:
  title: 21 – Berechnen zusammengesetzter SLAs (5 Min.)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="21---calculate-composite-slas-5-min"></a>21 – Berechnen zusammengesetzter SLAs (5 Min.)

In dieser exemplarischen Vorgehensweise ermitteln wir das Verfügbarkeits-SLA von Azure-Diensten und berechnen dann die SLA-basierte erwartete Verfügbarkeit auf Anwendungsbasis.

Our example application consists of these Azure services. We will not go in to deep architectural configuration and considerations, the intention here is to give an high level example.

+ **App Service**: So hosten Sie die Anwendung.
+ **Azure AD B2C**: Zum Authentifizieren von Benutzeranmeldungen und Verwalten von Profilen.
+ **Application Gateway**: So verwalten Sie den Anwendungszugriff und die Skalierung. 
+ **Azure SQL-Datenbank**: So speichern Sie Anwendungsdaten. 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>Aufgabe 1: Bestimmen der prozentualen SLA-Verfügbarkeitswerte für unsere Anwendung

1. Navigieren Sie in einem Browser zur Seite [DLV-Übersicht für Azure-Dienste](https://azure.microsoft.com/en-us/support/legal/sla/summary/).

2. Locate the <bpt id="p1">**</bpt>App Service<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.95%<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>View full details<ept id="p1">**</ept>, and then expand <bpt id="p2">**</bpt>SLA details<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Monthly uptime percentages<ept id="p1">**</ept> and <bpt id="p2">**</bpt>Service Credits<ept id="p2">**</ept>.

3. Kehren Sie zur SLA-Webseite zurück, suchen Sie den **Azure Active Directory B2C**-Dienst, und bestimmen Sie den SLA-Betriebszeitwert, in diesem Fall **99,9%** . 

4. Suchen Sie den SLA-Verfügbarkeitswert des **Application Gateway**, **99,95 %** . 

5. The Azure SQL database uses Premium tiers but is not configured for Zone Redundant Deployments. Locate the <bpt id="p1">**</bpt>Azure SQL Database<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.99%<ept id="p2">**</ept>. 

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: There are different uptime values for different configurations and deployments of Azure SQL Database. It is important you are clear on your required uptime values, when planning and costing your deployment and configuration. Small changes in uptime can have impact on service costs as well as potentially increase complexity in configuration. Some other services that may be of interest on the Azure SLA summary web page would include <bpt id="p1">**</bpt>Virtual Machines<ept id="p1">**</ept>, <bpt id="p2">**</bpt>Storage Accounts<ept id="p2">**</ept> and <bpt id="p3">**</bpt>Cosmos DB<ept id="p3">**</ept>.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>Aufgabe 2: Berechnen der prozentualen Verfügbarkeit der zusammengesetzten Anwendungs-SLA

1. Unsere Beispielanwendung besteht aus diesen Azure-Diensten.

    **App Service-Betriebszeit in %** X **Azure AD B2C-Betriebszeit in %** X **Azure Application Gateway-Betriebszeit in %** X **Azure SQL-Datenbank--Betriebszeit in %**  =  **Gesamtbetriebszeit in %**

    was in Prozent wie folgt aussieht:

    **99,95 %** X **99,9 %** X **99,95 %** X **99,99 %**  = **99,79 %**

    Dies ist die SLA-basierte erwartete Verfügbarkeit unserer Anwendung mit den aktuellen Diensten und der aktuellen Architektur.

Wir wollen hier nicht auf tiefgreifende architektonische Konfigurationen und Überlegungen eingehen, sondern ein allgemeines Beispiel geben.
