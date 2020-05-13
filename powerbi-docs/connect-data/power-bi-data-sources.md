---
title: Power BI-datakällor
description: Den här artikeln innehåller de datakällor som Power BI stöder, inklusive information om DirectQuery och den lokala datagatewayen.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: kfollis
ms.openlocfilehash: a29dcd8c89d064678e558d5ebfee7ccb3cc8a8e0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83330116"
---
# <a name="power-bi-data-sources"></a>Power BI-datakällor

I följande tabell visas de datakällor som Power BI stöder för datauppsättningar, inklusive information om DirectQuery och den lokala datagatewayen. Information om dataflöden finns i [Ansluta till datakällor för Power BI-dataflöden](../transform-model/service-dataflows-data-sources.md).

> [!NOTE]
> Det finns många dataanslutningar för Power BI Desktop som kräver Internet Explorer 10 (eller senare) för autentisering. 


| Datakälla | Ansluta från skrivbordet | Anslut och uppdatera från tjänst | DirectQuery/Live-anslutning | Gateway (stöds) | Gateway (krävs) |
|---|---|---|---|---|---|---|---|
| Access-databas | Ja | Ja | Nej | Ja <sup>1</sup> | Ja |
| ActiveDirectory | Ja | Ja | Nej | Ja | Ja |
| Adobe Analytics | Ja | Ja | Nej | Nej | Nej |
| Amazon Redshift | Ja | Ja | Ja | Ja | Nej |
| appFigures | Ja | Ja | Nej | Nej | Nej |
| AtScale-kuber | Ja | Ja | Ja | Ja | Nej |
| Azure Analysis Services | Ja | Ja | Ja | Ja <sup>2</sup> | Nej |
| Azure Blob Storage | Ja | Ja | Nej | Ja | Nej |
| Azure Cosmos DB | Ja | Ja | Nej | Nej | Nej |
| Azure Cost Management | Ja | Ja | Nej | Nej | Nej |
| Azure Data Explorer (Kusto) | Ja | Ja | Ja | Nej | Nej |
| Azure Data Lake Storage Gen1 | Ja | Ja | Nej | Nej | Nej |
| Azure Data Lake Storage Gen2 | Ja | Ja | Nej | Ja | Nej |
| Azure DevOps | Ja | Ja | Nej | Nej | Nej |
| Azure DevOps Server | Ja | Ja | Nej | Ja | Ja |
| Azure HDInsight (HDFS) | Ja | Ja | Nej | Nej | Nej |
| Azure HDInsight Spark | Ja | Ja | Ja | Nej | Nej |
| Azure SQL Database | Ja | Ja | Ja | Ja <sup>2</sup> | Nej |
| Azure SQL Data Warehouse | Ja | Ja | Ja | Ja <sup>2</sup> | Nej |
| Azure Table Storage | Ja | Ja | Nej | Ja | Nej |
| BI-anslutningsapp | Ja | Ja | Ja | Ja | Ja |
| BI360 – Budgeting & Financial Reporting | Ja | Ja | Nej | Nej | Nej |
| Common Data Service | Ja | Ja | Nej | Nej | Nej |
| Data.World – Hämta datamängd | Ja | Ja | Nej | Nej | Nej |
| Denodo | Ja | Ja | Ja | Ja | Ja |
| Dremio | Ja | Ja | Ja | Ja | Ja |
| Dynamics 365 (online) | Ja | Ja | Nej | Nej | Nej |
| Dynamics 365 Business Central | Ja | Ja | Nej | Nej | Nej |
| Dynamics 365 Business Central (lokal) | Ja | Ja | Nej | Nej | Nej |
| Dynamics 365 Customer Insights | Ja | Ja | Nej | Nej | Nej |
| Dynamics NAV | Ja | Ja | Nej | Nej | Nej |
| Emigo Data Source | Ja | Ja | Nej | Nej | Nej |
| Entersoft Business Suite | Ja | Ja | Nej | Nej | Nej |
| Essbase | Ja | Ja | Ja | Ja | Ja |
| Exasol | Ja | Ja | Ja | Ja | Ja |
| Excel | Ja <sup>3</sup> | Ja <sup>3</sup> | Nej | Ja <sup>3</sup> | Nej <sup>4</sup> |
| Facebook | Ja | Ja | Nej | Nej | Nej |
| Arkiv | Ja | Ja | Nej | Ja | Ja |
| Mapp | Ja | Ja | Nej | Ja | Ja |
| GitHub | Ja | Ja | Nej | Nej | Nej |
| Google Analytics | Ja | Ja | Nej | Nej | Nej |
| Google BigQuery | Ja | Ja | Nej | Nej | Nej |
| Hadoop-fil (HDFS) | Ja | Nej | Nej | Nej | Nej |
| HDInsight Interactive-fråga | Ja | Ja | Ja | Nej | Nej |
| IBM DB2 | Ja | Ja | Ja | Ja | Nej |
| IBM Informix-databas | Ja | Ja | Nej | Ja | Nej |
| IBM Netezza | Ja | Ja | Ja | Ja | Ja |
| Impala | Ja | Ja | Ja | Ja | Ja |
| Indexima | Ja | Ja | Ja | Ja | Ja |
| Industrial App Store | Ja | Ja | Nej | Nej | Nej |
| Information Grid | Ja | Ja | Nej | Nej | Nej |
| Intersystems IRIS | Ja | Ja | Ja | Ja | Ja |
| Intune Data Warehouse | Ja | Ja | Nej | Nej | Nej |
| Jethro ODBC | Ja | Ja | Ja | Ja | Ja |
| JSON | Ja | Ja | Nej | Ja** | Nej <sup>4</sup> |
| Kyligence Enterprise | Ja | Ja | Ja | Ja | Ja |
| MailChimp | Ja | Ja | Nej | Nej | Nej |
| Marketo | Ja | Ja | Nej | Nej | Nej |
| MarkLogic ODBC | Ja | Ja | Ja | Ja | Ja |
| Microsoft Azure Consumption Insights | Ja | Ja | Nej | Nej | Nej |
| Microsoft Exchange | Ja | Ja | Nej | Ja | Nej |
| Microsoft Exchange Online | Ja | Ja | Nej | Nej | Nej |
| Microsoft Graph Security | Ja | Ja | Nej | Ja | Nej |
| Mixpanel | Ja | Ja | Nej | Nej | Nej |
| MySQL | Ja | Ja | Nej | Ja | Ja |
| OData | Ja | Ja | Nej | Ja | Nej |
| ODBC | Ja | Ja | Nej | Ja | Ja |
| OleDb | Ja | Ja | Nej | Ja | Ja |
| Oracle | Ja | Ja | Ja | Ja | Ja |
| Paxata | Ja | Ja | Nej | Ja | Nej |
| PDF | Ja | Ja | Nej | Ja | Nej <sup>4</sup> |
| Planview Enterprise One – CTM | Ja | Ja | Nej | Nej | Nej |
| Planview Enterprise One – PRM | Ja | Ja | Nej | Nej | Nej |
| Planview Projectplace | Ja | Ja | Nej | Nej | Nej |
| PostgreSQL | Ja | Ja | Ja | Ja | Nej |
| Power BI-dataflöden | Ja | Ja | Nej | Nej | Nej |
| Power BI-datauppsättningar | Ja | Ja | Ja | Nej | Nej |
| Power Platform-dataflöden | Ja | Ja | Nej | Nej | Nej |
| Python-skript | Ja | Ja <sup>5</sup> | Nej | Ja <sup>5</sup> | Ja |
| QubolePresto | Ja | Ja | Ja | Ja | Ja |
| Quick Base | Ja | Ja | Nej | Ja | Ja |
| QuickBooks Online | Ja | Ja | Nej | Nej | Nej |
| R-skript | Ja | Ja <sup>5</sup> | Nej | Ja <sup>5</sup> | Nej |
| Roamler | Ja | Ja | Nej | Ja | Nej |
| Salesforce-objekt | Ja | Ja | Nej | Nej | Nej |
| Salesforce-rapporter | Ja | Ja | Nej | Nej | Nej |
| SAP Business Warehouse Message Server | Ja | Ja | Ja | Ja | Ja |
| SAP Business Warehouse Server | Ja | Ja | Ja | Ja | Ja |
| SAP HANA | Ja | Ja | Ja | Ja | Ja |
| SharePoint-mapp | Ja | Ja | Nej | Ja | Nej <sup>4</sup> |
| SharePoint-lista | Ja | Ja | Nej | Ja | Nej <sup>4</sup> |
| SharePoint Online-lista | Ja | Ja | Nej | Ja <sup>2</sup> | Nej |
| Smartsheet | Ja | Ja | Nej | Nej | Nej |
| Snowflake | Ja | Ja | Ja | Ja | Nej |
| Spark | Ja | Ja | Ja | Ja | Nej |
| SparkPost | Ja | Ja | Nej | Nej | Nej |
| SQL Server | Ja | Ja | Ja | Ja | Ja |
| SQL Server Analysis Services | Ja | Ja | Ja | Ja | Ja |
| Stripe | Ja | Ja | Nej | Nej | Nej |
| SurveyMonkey | Ja | Ja | Nej | Ja | Nej |
| SweetIQ | Ja | Ja | Nej | Nej | Nej |
| Sybase | Ja | Ja | Nej | Ja | Ja |
| TeamDesk | Ja | Ja | Nej | Ja | Nej |
| Tenforce | Ja | Ja | Nej | Nej | Nej |
| Teradata | Ja | Ja | Ja | Ja | Ja |
| Text/CSV | Ja | Ja | Nej | Ja | Nej <sup>4</sup> |
| Twilio | Ja | Ja | Nej | Nej | Nej |
| tyGraph | Ja | Ja | Nej | Nej | Nej |
| Vertica | Ja | Ja | Ja | Ja | Ja |
| Webb | Ja | Ja | Nej | Ja | Ja <sup>6</sup> |
| Webtrends | Ja | Ja | Nej | Nej | Nej |
| Workforce Dimensions | Ja | Ja | Nej | Ja | Nej |
| XML | Ja | Ja | Nej | Ja | Nej <sup>4</sup> |
| Zendesk | Ja | Ja | Nej | Nej | Nej |
| | | | | | | | |

<sup>1</sup> Stöds med [ACE OLEDB-providern](https://www.microsoft.com/download/details.aspx?id=54920), installerad på samma dator som gatewayen.

<sup>2</sup> Stöds med samma M-funktion som den lokala versionen, vilket orsakar begränsade autentiseringsalternativ (Gateway stöder inte OAuth).

<sup>3</sup> Excel 1997–2003-filer (.xls) kräver [ACE OLEDB-providern](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Krävs för den lokala versionen av tekniken.

<sup>5</sup> Stöds endast med [personlig gateway](service-gateway-personal-mode.md).

<sup>6</sup> Krävs för .html-, .xls- och Access-databaser

## <a name="single-sign-on-sso-for-directquery-sources"></a>Enkel inloggning (SSO) för DirectQuery-källor

När alternativet för enkel inloggning är aktiverat och dina användares åtkomstrapporter har skapats ovanpå datakällan skickar Power BI deras autentiserade Azure AD-autentiseringsuppgifter i frågorna till den underliggande datakällan. Detta möjliggör för Power BI att respektera säkerhetsinställningarna som är konfigurerade på datakällsnivå.
Alternativet för enkel inloggning börjar fungera för alla datauppsättningar som använder den här datakällan. Autentiseringsmetoden som används för importscenarier påverkas inte. Följande datakällor stöder enkel inloggning för anslutningar via DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW Message Server
- Snowflake
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) stöds inte. Användare som vill använda enkel inloggning med DirectQuery måste undantas från MFA.

## <a name="next-steps"></a>Nästa steg

[Ansluta till data i Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Använd DirectQuery i Power BI](desktop-directquery-about.md)  
[SQL Server Analysis Services-realtidsdata i Power BI](sql-server-analysis-services-tabular-data.md)  
[Vad är en lokal datagateway?](service-gateway-onprem.md)  
