---
title: Power BI-rapportdatakällor i Power BI-rapportserver
description: Power BI-rapporter kan ansluta till ett antal datakällor. Beroende på hur data används, finns olika datakällor tillgängliga.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: fe8ad0b951fedb17a97007e48808d2bfd7467e88
ms.sourcegitcommit: 6c2c7a090b0826e3cfc3a897566e802857bbacc8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68808212"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI-rapportdatakällor i Power BI-rapportserver
Power BI-rapporter kan ansluta till ett antal datakällor. Beroende på hur data används, finns olika datakällor tillgängliga. Data kan importeras eller så kan data frågas direkt med DirectQuery eller en live-anslutning till SQL Server Analysis Services.

Dessa datakällor är specifika för Power BI-rapporter som används i Power BI-rapportserver. Information om datakällor som stöds med sidnumrerade rapporter (.rdl), finns i [Datakällor som stöds av Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Alla datakällor i en Power BI Desktop-rapport måste stödja konfigurering av schemalagd uppdatering.
>  

## <a name="list-of-supported-data-sources"></a>Lista med datakällor som stöds

Andra datakällor kan fungera även om de inte finns med på listan.

| **Datakälla** | **Cachelagrade data** | **Schemalagd uppdatering** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server-databas |Ja |Ja |Ja |
| SQL Server Analysis Services |Ja |Ja |Ja |
| Azure SQL Database |Ja |Ja |Ja |
| Azure SQL Data Warehouse |Ja |Ja |Ja |
| Excel |Ja |Ja |Nej |
| Access-databas |Ja |Ja |Nej |
| Active Directory |Ja |Ja |Nej |
| Amazon Redshift |Ja |Nej |Nej |
| Azure Blob Storage |Ja |Ja |Nej |
| Azure Data Lake Store |Ja |Nej |Nej |
| Azure HDInsight (HDFS) |Ja |Nej |Nej |
| Azure HDInsight (Spark) |Ja |Ja |Nej |
| Azure Table Storage |Ja |Ja |Nej |
| Dynamics 365 (online) |Ja |Nej |Nej |
| Facebook |Ja |Nej |Nej |
| Mapp |Ja |Ja |Nej |
| Google Analytics |Ja |Nej |Nej |
| Hadoop-fil (HDFS) |Ja |Nej |Nej |
| IBM DB2-databas |Ja |Ja |Nej |
| Impala |Ja |Nej |Nej |
| JSON |Ja |Ja |Nej |
| Microsoft Exchange |Ja |Nej |Nej |
| Microsoft Exchange Online |Ja |Nej |Nej |
| MySQL-databas |Ja |Ja |Nej |
| OData-flöde |Ja |Ja |Nej |
| ODBC |Ja |Ja |Nej |
| OLE DB |Ja |Ja |Nej |
| Oracle-databas |Ja |Ja |Ja |
| PostgreSQL-databas |Ja |Ja |Nej |
| Power BI-tjänst |Nej |Nej |Nej |
| R -skript |Ja |Nej |Nej |
| Salesforce-objekt |Ja |Nej |Nej |
| Salesforce-rapporter |Ja |Nej |Nej |
| SAP Business Warehouse-server |Ja |Ja |Ja |
| SAP HANA-databas |Ja |Ja |Ja |
| SharePoint-mapp (lokal) |Ja |Ja |Nej |
| SharePoint-lista (lokal) |Ja |Ja |Nej |
| SharePoint Online-lista |Ja |Nej |Nej |
| Snowflake |Ja |Nej |Nej |
| Sybase-databas |Ja |Ja |Nej |
| Teradata-databas |Ja |Ja |Ja |
| Text/CSV |Ja |Ja |Nej |
| Webb |Ja |Ja |Nej |
| XML |Ja |Ja |Nej |
| appFigures (beta) |Ja |Nej |Nej |
| Azure Analysis Services-databas |Ja |Nej |Ja |
| Azure Cosmos DB (beta) |Ja |Nej |Nej |
| Azure HDInsight Spark (beta) |Ja |Nej |Nej |
| Common Data Service (beta) |Ja |Nej |Nej |
| comScore Digital Analytix (beta) |Ja |Nej |Nej |
| Dynamics 365 for Customer Insights (beta) |Ja |Nej |Nej |
| Dynamics 365 for Financials (beta) |Ja |Nej |Nej |
| GitHub (beta) |Ja |Nej |Nej |
| Google BigQuery (beta) |Ja |Nej |Nej |
| IBM Informix-databas (beta) |Ja |Nej |Nej |
| IBM Netezza (beta) |Ja |Nej |Nej |
| Kusto (beta) |Ja |Nej |Nej |
| MailChimp (beta) |Ja |Nej |Nej |
| Microsoft Azure Consumption Insights (beta) |Ja |Nej |Nej |
| Mixpanel (beta) |Ja |Nej |Nej |
| Planview Enterprise (beta) |Ja |Nej |Nej |
| Projectplace (beta) |Ja |Nej |Nej |
| QuickBooks Online (beta) |Ja |Nej |Nej |
| Smartsheet |Ja |Nej |Nej |
| Spark (beta) |Ja |Nej |Nej |
| SparkPost (beta) |Ja |Nej |Nej |
| SQL Sentry (beta) |Ja |Nej |Nej |
| Stripe (Beta) |Ja |Nej |Nej |
| SweetIQ (beta) |Ja |Nej |Nej |
| Troux (beta) |Ja |Nej |Nej |
| Twilio (beta) |Ja |Nej |Nej |
| tyGraph (beta) |Ja |Nej |Nej |
| Vertika (beta) |Ja |Nej |Nej |
| Visual Studio Team Services (beta) |Ja |Nej |Nej |
| Webtrends (beta) |Ja |Nej |Nej |
| Zendesk (beta) |Ja |Nej |Nej |

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
| Webb |Ja |Nej |Ja |Ja |
| Azure SQL Database |Nej |Nej |Ja |Nej |
| Azure SQL Data Warehouse |Nej |Nej |Ja |Nej |
| Active Directory |Nej |Nej |Ja |Ja |
| Amazon Redshift |Nej |Nej |Nej |Nej |
| Azure Blob Storage |Ja |Ja |Nej |Nej |
| Azure Data Lake Store |Nej |Nej |Nej |Nej |
| Azure HDInsight (HDFS) |Nej |Nej |Nej |Nej |
| Azure HDInsight (Spark) |Ja |Ja |Nej |Nej |
| Azure Table Storage |Nej |Ja |Nej |Nej |
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
| ODBC |Ja |Nej |Ja |Ja |
| OLE DB |Ja |Nej |Ja |Ja |
| Oracle-databas |Nej |Nej |Ja |Ja |
| PostgreSQL-databas |Nej |Nej |Ja |Nej |
| Power BI-tjänst |Nej |Nej |Nej |Nej |
| R-skript |Nej |Nej |Nej |Nej |
| Salesforce-objekt |Nej |Nej |Nej |Nej |
| Salesforce-rapporter |Nej |Nej |Nej |Nej |
| SAP Business Warehouse-server |Nej |Nej |Ja |Nej |
| SAP HANA-databas |Nej |Nej |Ja |Ja |
| SharePoint-mapp (lokal) |Ja |Nej |Nej |Ja |
| SharePoint-lista (lokal) |Ja |Nej |Nej |Ja |
| SharePoint Online-lista |Nej |Nej |Nej |Nej |
| Snowflake |Nej |Nej |Nej |Nej |
| Sybase-databas |Nej |Nej |Ja |Ja |
| Teradata-databas |Nej |Nej |Ja |Ja |
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

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista med autentiseringsmetoder som stöds för DirectQuery

Power BI-rapportservern har inte stöd för OAuth-baserad autentisering för DirectQuery.

| **Datakälla** | **Anonym autentisering** | **Nyckelautentisering** | **Användarnamn och lösenord** | **Windows-autentisering** | **Integrerad Windows-autentisering** |
| --- | --- | --- | --- | --- | --- |
| SQL Server-databas |Nej |Nej |Ja |Ja |Ja |
| SQL Server Analysis Services |Nej |Nej |Ja |Ja |Ja |
| Azure SQL Database |Nej |Nej |Ja |Nej |Nej |
| Azure SQL Data Warehouse |Nej |Nej |Ja |Nej |Nej |
| Oracle-databas |Nej |Nej |Ja |Ja |Ja |
| SAP Business Warehouse-server |Nej |Nej |Ja |Nej |Nej |
| SAP HANA-databas |Nej |Nej |Ja |Ja |Nej |
| Teradata-databas |Nej |Nej |Ja |Ja |Ja |


## <a name="next-steps"></a>Nästa steg
Nu när du har anslutit till din datakällan, [skapar du en Power BI-rapport](quickstart-create-powerbi-report.md) med hjälp av data från den datakällan.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

