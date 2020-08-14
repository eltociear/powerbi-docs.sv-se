---
title: Power BI-rapportdatakällor i Power BI-rapportserver
description: Power BI-rapporter kan ansluta till ett antal datakällor. Beroende på hur data används, finns olika datakällor tillgängliga.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 08/04/2020
ms.author: maggies
ms.openlocfilehash: 00c00ca7bbd7ad3f901c98f44a2900f332e3616a
ms.sourcegitcommit: 65822b51810a5239fea9d3d0af1fc286436c6cad
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87837622"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI-rapportdatakällor i Power BI-rapportserver
Power BI-rapporter kan ansluta till ett antal datakällor. Beroende på hur data används, finns olika datakällor tillgängliga. Data kan importeras eller så kan data frågas direkt med DirectQuery eller en live-anslutning till SQL Server Analysis Services. Vissa datakällor stöds i Power BI Desktop optimerat för Power BI-rapportserver, men är inte optimerade för Power BI-rapporter som publiceras till Power BI-rapportserver. Följande lista innehåller datakällor som stöds på båda platserna.

Dessa datakällor är specifika för Power BI-rapporter som används i Power BI-rapportserver. Information om datakällor som stöds med sidnumrerade rapporter (.rdl), finns i [Datakällor som stöds av Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Alla datakällor i en Power BI Desktop-rapport måste stödja konfigurering av schemalagd uppdatering.
>  

## <a name="list-of-supported-data-sources"></a>Lista med datakällor som stöds

| **Datakälla** | **Cachelagrade data** | **Schemalagd uppdatering** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server-databas |Ja |Ja |Ja |
| SQL Server Analysis Services |Ja |Ja |Ja |
| Azure SQL Database |Ja |Ja |Ja |
| Azure SQL Data Warehouse |Ja |Ja |Ja |
| Excel |Ja |Ja |Inga |
| Access-databas |Ja |Ja |Inga |
| Active Directory |Ja |Ja |Nej |
| Amazon Redshift |Ja |Nej |Nej |
| Azure Blob Storage |Ja |Ja |Inga |
| Azure Data Lake Store |Ja |Nej |Inga |
| Azure HDInsight (HDFS) |Ja |Nej |Inga |
| Azure HDInsight (Spark) |Ja |Nej |Nej |
| Azure Table Storage |Ja |Ja |Inga |
| Dynamics 365 (online) |Ja |Nej |Inga |
| Facebook |Ja |Nej |Inga |
| Mapp |Ja |Ja |Nej |
| Google Analytics |Ja |Nej |Nej |
| Hadoop-fil (HDFS) |Ja |Nej |Inga |
| IBM DB2-databas |Ja |Ja |Inga |
| Impala |Ja |Nej |Inga |
| JSON |Ja |Ja |Nej |
| Microsoft Exchange |Ja |Nej |Nej |
| Microsoft Exchange Online |Ja |Nej |Inga |
| MySQL-databas |Ja |Ja |Inga |
| OData-feed |Ja |Ja |Nej |
| ODBC |Ja |Ja |Inga |
| OLE DB |Ja |Ja |Inga |
| Oracle-databas |Ja |Ja |Ja |
| PostgreSQL-databas |Ja |Ja |Inga |
| Power BI-tjänst |Nej |Nej |Inga |
| R-skript |Ja |Nej |Nej |
| Salesforce-objekt |Ja |Nej |Nej |
| Salesforce-rapporter |Ja |Nej |Inga |
| SAP Business Warehouse-server |Ja |Ja |Ja |
| SAP HANA-databas |Ja |Ja |Ja |
| SharePoint-mapp (lokal) |Ja |Ja |Inga |
| SharePoint-lista (lokal) |Ja |Ja |Inga |
| SharePoint Online-lista |Ja |Nej |Nej |
| Snowflake |Ja |Nej |Inga |
| Sybase-databas |Ja |Ja |Nej |
| Teradata |Ja |Ja |Ja |
| Text/CSV |Ja |Ja |Inga |
| Webben |Ja |Ja |Nej |
| XML |Ja |Ja |Inga |
| appFigures (beta) |Ja |Nej |Inga |
| Azure Analysis Services-databas |Ja |Inga |Ja |
| Azure Cosmos DB (beta) |Ja |Nej |Inga |
| Azure HDInsight Spark (beta) |Ja |Nej |Inga |
| Common Data Service (beta) |Ja |Nej |Inga |
| comScore Digital Analytix (beta) |Ja |Nej |Inga |
| Dynamics 365 for Customer Insights (beta) |Ja |Nej |Inga |
| Dynamics 365 for Financials (beta) |Ja |Nej |Inga |
| GitHub (beta) |Ja |Nej |Inga |
| Google BigQuery (beta) |Ja |Nej |Inga |
| IBM Informix-databas (beta) |Ja |Nej |Inga |
| IBM Netezza (beta) |Ja |Nej |Inga |
| Kusto (beta) |Ja |Nej |Inga |
| MailChimp (beta) |Ja |Nej |Inga |
| Microsoft Azure Consumption Insights (beta) |Ja |Nej |Inga |
| Mixpanel (beta) |Ja |Nej |Inga |
| Planview Enterprise (beta) |Ja |Nej |Inga |
| Projectplace (beta) |Ja |Nej |Inga |
| QuickBooks Online (beta) |Ja |Nej |Nej |
| Smartsheet |Ja |Nej |Inga |
| Spark (beta) |Ja |Nej |Inga |
| SparkPost (beta) |Ja |Nej |Inga |
| SQL Sentry (beta) |Ja |Nej |Inga |
| Stripe (beta) |Ja |Nej |Inga |
| SweetIQ (beta) |Ja |Nej |Inga |
| Troux (beta) |Ja |Nej |Inga |
| Twilio (beta) |Ja |Nej |Inga |
| tyGraph (beta) |Ja |Nej |Inga |
| Vertica (beta) |Ja |Nej |Inga |
| Visual Studio Team Services (beta) |Ja |Nej |Inga |
| Webtrends (beta) |Ja |Nej |Inga |
| Zendesk (beta) |Ja |Nej |Inga |

> [!IMPORTANT]
> Säkerhet på radnivå som konfigurerats på datakällan ska fungera för vissa DirectQuery- (SQL Server, Azure SQL Database, Oracle och Teradata) och live-anslutningar förutsatt att Kerberos har konfigurerats korrekt i din miljö.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lista med autentiseringsmetoder som stöds för modelluppdatering

Power BI-rapportservern har inte stöd för OAuth-baserad autentisering för modelluppdatering. Vissa datakällor, till exempel Excel- eller Access-databaser, använder separata steg som Fil eller Webb för att ansluta till data.

| **Datakälla** | **Anonym autentisering** | **Nyckelautentisering** | **Användarnamn och lösenord** | **Windows-autentisering** |
| --- | --- | --- | --- | --- |
| SQL Server-databas |Nej |Inga |Ja |Ja |
| SQL Server Analysis Services |Nej |Inga |Ja |Ja |
| Webben |Ja |Inga |Ja |Ja |
| Azure SQL Database |Nej |Inga |Ja |Nej |
| Azure SQL Data Warehouse |Nej |Inga |Ja |Inga |
| Active Directory |Nej |Inga |Ja |Ja |
| Amazon Redshift |Nej |Nej |Nej |Nej |
| Azure Blob Storage |Ja |Ja |Nej |Inga |
| Azure Data Lake Store |Nej |Nej |Nej |Inga |
| Azure HDInsight (HDFS) |Nej |Nej |Nej |Inga |
| Azure HDInsight (Spark) |Nej |Nej |Nej |Nej |
| Azure Table Storage |Inga |Ja |Nej |Inga |
| Dynamics 365 (online) |Nej |Nej |Nej |Inga |
| Facebook |Nej |Nej |Nej |Inga |
| Mapp |Nej |Nej |Inga |Ja |
| Google Analytics |Nej |Nej |Nej |Nej |
| Hadoop-fil (HDFS) |Nej |Nej |Nej |Inga |
| IBM DB2-databas |Nej |Inga |Ja |Ja |
| Impala |Nej |Nej |Nej |Nej |
| Microsoft Exchange |Nej |Nej |Nej |Nej |
| Microsoft Exchange Online |Nej |Nej |Nej |Inga |
| MySQL-databas |Nej |Inga |Ja |Ja |
| OData-feed |Ja |Ja |Ja |Ja |
| ODBC |Ja |Inga |Ja |Ja |
| OLE DB |Ja |Inga |Ja |Ja |
| Oracle-databas |Nej |Inga |Ja |Ja |
| PostgreSQL-databas |Nej |Inga |Ja |Inga |
| Power BI-tjänst |Nej |Nej |Nej |Inga |
| R-skript |Nej |Nej |Nej |Nej |
| Salesforce-objekt |Nej |Nej |Nej |Nej |
| Salesforce-rapporter |Nej |Nej |Nej |Inga |
| SAP Business Warehouse-server |Nej |Inga |Ja |Inga |
| SAP HANA-databas |Nej |Inga |Ja |Ja |
| SharePoint-mapp (lokal) |Ja |Nej |Inga |Ja |
| SharePoint-lista (lokal) |Ja |Nej |Inga |Ja |
| SharePoint Online-lista |Nej |Nej |Nej |Nej |
| Snowflake |Nej |Nej |Nej |Inga |
| Sybase-databas |Nej |Inga |Ja |Ja |
| Teradata |Nej |Inga |Ja |Ja** |
| appFigures (beta) |Nej |Nej |Nej |Inga |
| Azure Analysis Services-databas (beta) |Nej |Nej |Nej |Inga |
| Azure Cosmos DB (beta) |Nej |Nej |Nej |Inga |
| Azure HDInsight Spark (beta) |Nej |Nej |Nej |Inga |
| Common Data Service (beta) |Nej |Nej |Nej |Inga |
| comScore Digital Analytix (beta) |Nej |Nej |Nej |Inga |
| Dynamics 365 for Customer Insights (beta) |Nej |Nej |Nej |Inga |
| Dynamics 365 for Financials (beta) |Nej |Nej |Nej |Inga |
| GitHub (beta) |Nej |Nej |Nej |Inga |
| Google BigQuery (beta) |Nej |Nej |Nej |Inga |
| IBM Informix-databas (beta) |Nej |Nej |Nej |Inga |
| IBM Netezza (beta) |Nej |Nej |Nej |Inga |
| Kusto (beta) |Nej |Nej |Nej |Inga |
| MailChimp (beta) |Nej |Nej |Nej |Inga |
| Microsoft Azure Consumption Insights (beta) |Nej |Nej |Nej |Inga |
| Mixpanel (beta) |Nej |Nej |Nej |Inga |
| Planview Enterprise (beta) |Nej |Nej |Nej |Inga |
| Projectplace (beta) |Nej |Nej |Nej |Inga |
| QuickBooks Online (beta) |Nej |Nej |Nej |Nej |
| Smartsheet |Nej |Nej |Nej |Inga |
| Spark (beta) |Nej |Nej |Nej |Inga |
| SparkPost (beta) |Nej |Nej |Nej |Inga |
| SQL Sentry (beta) |Nej |Nej |Nej |Inga |
| Stripe (beta) |Nej |Nej |Nej |Inga |
| SweetIQ (beta) |Nej |Nej |Nej |Inga |
| Troux (beta) |Nej |Nej |Nej |Inga |
| Twilio (beta) |Nej |Nej |Nej |Inga |
| tyGraph (beta) |Nej |Nej |Nej |Inga |
| Vertica (beta) |Nej |Nej |Nej |Inga |
| Visual Studio Team Services (beta) |Nej |Nej |Nej |Inga |
| Webtrends (beta) |Nej |Nej |Nej |Inga |
| Zendesk (beta) |Nej |Nej |Nej |Inga |

**Användning av LDAP-autentisering med Teradata (aktiveras i Power BI Desktop med kommandot ”setx PBI_EnableTeradataLdap true” i Kommandotolken) stöds inte för modelluppdatering.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista med autentiseringsmetoder som stöds för DirectQuery

Power BI-rapportservern har inte stöd för OAuth-baserad autentisering för DirectQuery.

| **Datakälla** | **Anonym autentisering** | **Nyckelautentisering** | **Användarnamn och lösenord** | **Windows-autentisering** | **Integrerad Windows-autentisering** |
| --- | --- | --- | --- | --- | --- |
| SQL Server-databas |Nej |Inga |Ja |Ja |Ja |
| SQL Server Analysis Services |Nej |Inga |Ja |Ja |Ja |
| Azure SQL Database |Nej |Inga |Ja |Nej |Nej |
| Azure SQL Data Warehouse |Nej |Inga |Ja |Nej |Inga |
| Oracle-databas |Nej |Inga |Ja |Ja |Ja |
| SAP Business Warehouse-server |Nej |Inga |Ja |Nej |Inga |
| SAP HANA-databas |Nej |Inga |Ja |Ja |Ja** |
| Teradata |Nej |Inga |Ja |Ja |Ja |

**SAP HANA stöder DirectQuery med integrerad Windows-autentisering endast när den används som relationsdatabas i den publicerade Power BI Desktop-filen (.pbix).

## <a name="next-steps"></a>Nästa steg

[Datakällor för Power BI-rapporter[(../connect-data/power-bi-data-sources.md) i Power BI-tjänsten. Nu när du har anslutit till din datakälla kan du [skapa en Power BI-rapport](quickstart-create-powerbi-report.md) med data från den datakällan.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
