---
title: "Power BI-rapportdatakällor i Power BI-rapportserver"
description: "Power BI-rapporter kan ansluta till olika datakällor. Beroende på hur data används, finns olika datakällor tillgängliga."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: dfdb0aebfd86854e756003d188a5b92fd8370fc1
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI-rapportdatakällor i Power BI-rapportserver
Power BI-rapporter kan ansluta till olika datakällor. Beroende på hur data används, finns olika datakällor tillgängliga. Data kan importeras eller så kan data frågas direkt med DirectQuery eller en live-anslutning till SQL Server Analysis Services.

Dessa datakällor är specifika för Power BI-rapporter som används i Power BI-rapportserver. Information om datakällor som stöds med sidnumrerade rapporter finns i [datakällor som stöds av Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Alla datakällor i en Power BI Desktop-rapport måste stödjas för att konfigurera schemalagd uppdatering.
> 
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
| Azure HDInsight (HDFS) |Ja |Ja |Nej |
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
| Azure Analysis Services-databas (beta) |Ja |Nej |Nej |
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

## <a name="next-steps"></a>Nästa steg
Nu när du valt ut datakällan, kan du [skapa en rapport](quickstart-create-powerbi-report.md) med hjälp av data från datakällan.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

