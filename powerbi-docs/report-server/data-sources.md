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
ms.openlocfilehash: 08294e1320e603131beb0ca332b0f85ee51ea8bb
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937572"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI-rapportdatakällor i Power BI-rapportserver
Power BI-rapporter kan ansluta till ett antal datakällor. Beroende på hur data används, finns olika datakällor tillgängliga. Data kan importeras eller så kan data frågas direkt med DirectQuery eller en live-anslutning till SQL Server Analysis Services. Vissa datakällor som finns i Power BI Desktop är optimerade för Power BI-rapportservern, men de stöds inte när de publiceras till Power BI-rapportservern.

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
| Amazon Redshift |Ja |Inga |Nej |
| Azure Blob Storage |Ja |Ja |Inga |
| Azure Data Lake Store |Ja |Inga |Nej |
| Azure HDInsight (HDFS) |Ja |Inga |Nej |
| Azure HDInsight (Spark) |Ja |Inga |Nej |
| Azure Table Storage |Ja |Ja |Inga |
| Dynamics 365 (online) |Ja |Inga |Nej |
| Facebook |Ja |Inga |Nej |
| Mapp |Ja |Ja |Nej |
| Google Analytics |Ja |Inga |Nej |
| Hadoop-fil (HDFS) |Ja |Inga |Nej |
| IBM DB2-databas |Ja |Ja |Inga |
| Impala |Ja |Inga |Nej |
| JSON |Ja |Ja |Nej |
| Microsoft Exchange |Ja |Inga |Nej |
| Microsoft Exchange Online |Ja |Inga |Nej |
| MySQL-databas |Ja |Ja |Inga |
| OData-feed |Ja |Ja |Nej |
| ODBC |Ja |Ja |Inga |
| OLE DB |Ja |Ja |Inga |
| Oracle-databas |Ja |Ja |Ja |
| PostgreSQL-databas |Ja |Ja |Inga |
| Power BI-tjänst |Nej |Nej |Nej |
| R-skript |Ja |Inga |Nej |
| Salesforce-objekt |Ja |Inga |Nej |
| Salesforce-rapporter |Ja |Inga |Nej |
| SAP Business Warehouse-server |Ja |Ja |Ja |
| SAP HANA-databas |Ja |Ja |Ja |
| SharePoint-mapp (lokal) |Ja |Ja |Inga |
| SharePoint-lista (lokal) |Ja |Ja |Inga |
| SharePoint Online-lista |Ja |Inga |Nej |
| Snowflake |Ja |Inga |Nej |
| Sybase-databas |Ja |Ja |Nej |
| Teradata |Ja |Ja |Ja |
| Text/CSV |Ja |Ja |Inga |
| Webben |Ja |Ja |Nej |
| XML |Ja |Ja |Inga |
| appFigures (beta) |Ja |Inga |Nej |
| Azure Analysis Services-databas |Ja |Inga |Ja |
| Azure Cosmos DB (beta) |Ja |Inga |Nej |
| Azure HDInsight Spark (beta) |Ja |Inga |Nej |
| Common Data Service (beta) |Ja |Inga |Nej |
| comScore Digital Analytix (beta) |Ja |Inga |Nej |
| Dynamics 365 for Customer Insights (beta) |Ja |Inga |Nej |
| Dynamics 365 for Financials (beta) |Ja |Inga |Nej |
| GitHub (beta) |Ja |Inga |Nej |
| Google BigQuery (beta) |Ja |Inga |Nej |
| IBM Informix-databas (beta) |Ja |Inga |Nej |
| IBM Netezza (beta) |Ja |Inga |Nej |
| Kusto (beta) |Ja |Inga |Nej |
| MailChimp (beta) |Ja |Inga |Nej |
| Microsoft Azure Consumption Insights (beta) |Ja |Inga |Nej |
| Mixpanel (beta) |Ja |Inga |Nej |
| Planview Enterprise (beta) |Ja |Inga |Nej |
| Projectplace (beta) |Ja |Inga |Nej |
| QuickBooks Online (beta) |Ja |Inga |Nej |
| Smartsheet |Ja |Inga |Nej |
| Spark (beta) |Ja |Inga |Nej |
| SparkPost (beta) |Ja |Inga |Nej |
| SQL Sentry (beta) |Ja |Inga |Nej |
| Stripe (beta) |Ja |Inga |Nej |
| SweetIQ (beta) |Ja |Inga |Nej |
| Troux (beta) |Ja |Inga |Nej |
| Twilio (beta) |Ja |Inga |Nej |
| tyGraph (beta) |Ja |Inga |Nej |
| Vertica (beta) |Ja |Inga |Nej |
| Visual Studio Team Services (beta) |Ja |Inga |Nej |
| Webtrends (beta) |Ja |Inga |Nej |
| Zendesk (beta) |Ja |Inga |Nej |

> [!IMPORTANT]
> Säkerhet på radnivå som konfigurerats på datakällan ska fungera för vissa DirectQuery- (SQL Server, Azure SQL Database, Oracle och Teradata) och live-anslutningar förutsatt att Kerberos har konfigurerats korrekt i din miljö.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lista med autentiseringsmetoder som stöds för modelluppdatering

Power BI-rapportservern har inte stöd för OAuth-baserad autentisering för modelluppdatering. Vissa datakällor, till exempel Excel- eller Access-databaser, använder separata steg som Fil eller Webb för att ansluta till data.

| **Datakälla** | **Anonym autentisering** | **Nyckelautentisering** | **Användarnamn och lösenord** | **Windows-autentisering** |
| --- | --- | --- | --- | --- |
| SQL Server-databas |Nej |Nej |Ja |Ja |
| SQL Server Analysis Services |Nej |Nej |Ja |Ja |
| Webben |Ja |Inga |Ja |Ja |
| Azure SQL Database |Nej |Nej |Ja |Nej |
| Azure SQL Data Warehouse |Nej |Nej |Ja |Inga |
| Active Directory |Nej |Nej |Ja |Ja |
| Amazon Redshift |Nej |Nej |Nej |Nej |
| Azure Blob Storage |Ja |Ja |Inga |Nej |
| Azure Data Lake Store |Nej |Nej |Nej |Nej |
| Azure HDInsight (HDFS) |Nej |Nej |Nej |Nej |
| Azure HDInsight (Spark) |Nej |Nej |Nej |Nej |
| Azure Table Storage |Inga |Ja |Inga |Nej |
| Dynamics 365 (online) |Nej |Nej |Nej |Nej |
| Facebook |Nej |Nej |Nej |Nej |
| Mapp |Nej |Nej |Nej |Ja |
| Google Analytics |Nej |Nej |Nej |Nej |
| Hadoop-fil (HDFS) |Nej |Nej |Nej |Nej |
| IBM DB2-databas |Nej |Nej |Ja |Ja |
| Impala |Nej |Nej |Nej |Nej |
| Microsoft Exchange |Nej |Nej |Nej |Nej |
| Microsoft Exchange Online |Nej |Nej |Nej |Nej |
| MySQL-databas |Nej |Nej |Ja |Ja |
| OData-feed |Ja |Ja |Ja |Ja |
| ODBC |Ja |Inga |Ja |Ja |
| OLE DB |Ja |Inga |Ja |Ja |
| Oracle-databas |Nej |Nej |Ja |Ja |
| PostgreSQL-databas |Nej |Nej |Ja |Inga |
| Power BI-tjänst |Nej |Nej |Nej |Nej |
| R-skript |Nej |Nej |Nej |Nej |
| Salesforce-objekt |Nej |Nej |Nej |Nej |
| Salesforce-rapporter |Nej |Nej |Nej |Nej |
| SAP Business Warehouse-server |Nej |Nej |Ja |Inga |
| SAP HANA-databas |Nej |Nej |Ja |Ja |
| SharePoint-mapp (lokal) |Ja |Inga |Nej |Ja |
| SharePoint-lista (lokal) |Ja |Inga |Nej |Ja |
| SharePoint Online-lista |Nej |Nej |Nej |Nej |
| Snowflake |Nej |Nej |Nej |Nej |
| Sybase-databas |Nej |Nej |Ja |Ja |
| Teradata |Nej |Nej |Ja |Ja** |
| appFigures (beta) |Nej |Nej |Nej |Nej |
| Azure Analysis Services-databas (beta) |Nej |Nej |Nej |Nej |
| Azure Cosmos DB (beta) |Nej |Nej |Nej |Nej |
| Azure HDInsight Spark (beta) |Nej |Nej |Nej |Nej |
| Common Data Service (beta) |Nej |Nej |Nej |Nej |
| comScore Digital Analytix (beta) |Nej |Nej |Nej |Nej |
| Dynamics 365 for Customer Insights (beta) |Nej |Nej |Nej |Nej |
| Dynamics 365 for Financials (beta) |Nej |Nej |Nej |Nej |
| GitHub (beta) |Nej |Nej |Nej |Nej |
| Google BigQuery (beta) |Nej |Nej |Nej |Nej |
| IBM Informix-databas (beta) |Nej |Nej |Nej |Nej |
| IBM Netezza (beta) |Nej |Nej |Nej |Nej |
| Kusto (beta) |Nej |Nej |Nej |Nej |
| MailChimp (beta) |Nej |Nej |Nej |Nej |
| Microsoft Azure Consumption Insights (beta) |Nej |Nej |Nej |Nej |
| Mixpanel (beta) |Nej |Nej |Nej |Nej |
| Planview Enterprise (beta) |Nej |Nej |Nej |Nej |
| Projectplace (beta) |Nej |Nej |Nej |Nej |
| QuickBooks Online (beta) |Nej |Nej |Nej |Nej |
| Smartsheet |Nej |Nej |Nej |Nej |
| Spark (beta) |Nej |Nej |Nej |Nej |
| SparkPost (beta) |Nej |Nej |Nej |Nej |
| SQL Sentry (beta) |Nej |Nej |Nej |Nej |
| Stripe (beta) |Nej |Nej |Nej |Nej |
| SweetIQ (beta) |Nej |Nej |Nej |Nej |
| Troux (beta) |Nej |Nej |Nej |Nej |
| Twilio (beta) |Nej |Nej |Nej |Nej |
| tyGraph (beta) |Nej |Nej |Nej |Nej |
| Vertica (beta) |Nej |Nej |Nej |Nej |
| Visual Studio Team Services (beta) |Nej |Nej |Nej |Nej |
| Webtrends (beta) |Nej |Nej |Nej |Nej |
| Zendesk (beta) |Nej |Nej |Nej |Nej |

**Användning av LDAP-autentisering med Teradata (aktiveras i Power BI Desktop med kommandot ”setx PBI_EnableTeradataLdap true” i Kommandotolken) stöds inte för modelluppdatering.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista med autentiseringsmetoder som stöds för DirectQuery

Power BI-rapportservern har inte stöd för OAuth-baserad autentisering för DirectQuery.

| **Datakälla** | **Anonym autentisering** | **Nyckelautentisering** | **Användarnamn och lösenord** | **Windows-autentisering** | **Integrerad Windows-autentisering** |
| --- | --- | --- | --- | --- | --- |
| SQL Server-databas |Nej |Nej |Ja |Ja |Ja |
| SQL Server Analysis Services |Nej |Nej |Ja |Ja |Ja |
| Azure SQL Database |Nej |Nej |Ja |Inga |Nej |
| Azure SQL Data Warehouse |Nej |Nej |Ja |Inga |Nej |
| Oracle-databas |Nej |Nej |Ja |Ja |Ja |
| SAP Business Warehouse-server |Nej |Nej |Ja |Inga |Nej |
| SAP HANA-databas |Nej |Nej |Ja |Ja |Ja** |
| Teradata |Nej |Nej |Ja |Ja |Ja |

**SAP HANA stöder DirectQuery med integrerad Windows-autentisering endast när den används som relationsdatabas i den publicerade Power BI Desktop-filen (.pbix).

## <a name="next-steps"></a>Nästa steg

[Datakällor för Power BI-rapporter](../connect-data/power-bi-data-sources.md) i Power BI-tjänsten

Nu när du har anslutit till din datakällan, [skapar du en Power BI-rapport](quickstart-create-powerbi-report.md) med hjälp av data från den datakällan.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
