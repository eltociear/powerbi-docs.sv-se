---
title: "Datakällor i Power BI Desktop"
description: "Datakällor i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 04/29/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ff28f5d43b065ae798e2e9f275c8e8b59e9ee1ce
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/09/2018
---
# <a name="data-sources-in-power-bi-desktop"></a>Datakällor i Power BI Desktop
Med Power BI Desktop kan du ansluta till data från många olika källor. En fullständig lista med tillgängliga datakällor finns längst ned på den här sidan.

Anslut till data genom att välja **Hämta data** från menyfliksområdet **Start**. Om du väljer nedåtpilen eller texten **Hämta data** på knappen, visas menyn **Mest vanliga** datatyper, enligt följande bild.

![](media/desktop-data-sources/data-sources_1.png)

Om du väljer **Mer...** från menyn **Mest vanliga** visas fönstret **Hämta data**. Du kan också öppna fönstret **Hämta data** (och kringgå menyn **Mest vanliga**) genom att välja **Hämta data**-**ikonen** direkt.

![](media/desktop-data-sources/data-sources_2.png)

> [!NOTE]
> Power BI-teamet utökar kontinuerligt de datakällor som är tillgängliga för **Power BI Desktop** och **Power BI-tjänsten**. Därför visas ofta tidiga versioner av pågående datakällor markerade med *beta* eller *förhandsversion*. Alla datakällor som har markerats som *beta* eller *förhandsversion* har begränsad support och funktionalitet och ska inte användas i produktionsmiljöer.
> 
> 

## <a name="data-sources"></a>Datakällor
Datatyperna ordnas i följande kategorier:

* Alla
* Fil
* Databas
* Azure
* Onlinetjänster
* Övrigt

I kategorin **Alla** finns alla dataanslutningstyper från alla kategorier.

I kategorin **Fil** finns följande dataanslutningar:

* Excel
* Text/CSV
* XML
* JSON
* Mapp
* SharePoint-mapp

Följande bild visar fönstret **Hämta data** för **Fil**.

![](media/desktop-data-sources/data-sources_3.png)

> [!NOTE]
> I tidigare versioner av Power BI Desktop var **CSV** och **Text** olika dataanslutningstyper. Dessa datakopplingar har nu kombinerats till **CSV/text**.
> 
> 

Kategorin **Databas** innehåller följande dataanslutningar:

* SQL Server-databas
* Access-databas
* SQL Server Analysis Services-databas
* Oracle-databas
* IBM DB2-databas
* IBM Informix-databas (beta)
* IBM Netezza
* MySQL-databas
* PostgreSQL-databas
* Sybase-databas
* Teradata-databas
* SAP HANA-databas
* SAP Business Warehouse Application Server
* SAP Business Warehouse Message Server (beta)
* Amazon Redshift
* Impala
* Google BigQuery (beta)
* Snowflake

> [!NOTE]
> Vissa databaskopplingar kräver att du aktiverar dem genom att välja **Arkiv > Alternativ och inställningar > Alternativ** sedan välja **Förhandsversionsfunktioner** och aktivera kopplingen. Om du inte ser några av de kopplingar som nämns ovan och vill använda dem, kontrollerar du dina inställningar för **Förhandsversionsfunktioner**. Observera att alla datakällor som har markerats som *beta* eller *förhandsversion* har begränsad support och funktionalitet och ska inte användas i produktionsmiljöer.
> 
> 

Följande bild visar fönstret **Hämta data** för **Databas**.

![](media/desktop-data-sources/data-sources_4.png)

Kategorin **Azure** innehåller följande dataanslutningar:

* Azure SQL Database
* Azure SQL Data Warehouse
* Azure Analysis Services-databas
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB (beta)
* Azure Data Lake Store
* Azure HDInsight (HDFS)
* Azure HDInsight Spark (beta)
* Interaktiv HDInsight-fråga (beta)

Följande bild visar fönstret **Hämta data** för **Azure**.

![](media/desktop-data-sources/data-sources_5.png)

Kategorin **Onlinetjänster** innehåller följande dataanslutningar:

* Power BI-tjänsten
* SharePoint Online-lista
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV (beta)
* Dynamics 365 for Financials (beta)
* Common Data Service (beta)
* Microsoft Azure Consumption Insights (beta)
* Visual Studio Team Services (beta)
* Salesforce-objekt
* Salesforce-rapporter
* Google Analytics
* Adobe Analytics
* appFigures (beta)
* comScore Digital Analytix (beta)
* Dynamics 365 for Customer Insights (beta)
* Data.World – Hämta datamängd (beta)
* Facebook
* GitHub (beta)
* MailChimp (beta)
* Marketo (beta)
* Mixpanel (beta)
* Planview Enterprise One – PRM (beta)
* Planview Projectplace (beta)
* QuickBooks Online (beta)
* Smartsheet
* SparkPost (beta)
* Stripe (beta)
* SweetIQ (beta)
* Planview Enterprise One – CMT (beta)
* Twilio (beta)
* tyGraph (beta)
* Webtrends (beta)
* Zendesk (beta)

Följande bild visar fönstret **Hämta data** för **Onlinetjänster**.

![](media/desktop-data-sources/data-sources_6b.png)

Kategorin **Övrigt** innehåller följande dataanslutningar:

* Vertica (beta)
* Kusto (beta)
* Webb
* SharePoint-lista
* OData-feed
* Active Directory
* Microsoft Exchange
* Hadoop-fil (HDFS)
* Spark (beta)
* R-skript
* ODBC
* OLE DB
* Tom fråga

Följande bild visar fönstret **Hämta data** för **Övrigt**.

![](media/desktop-data-sources/data-sources_7a.png)

> [!NOTE]
> För tillfället går det inte att ansluta till anpassade datakällor som skyddas med Azure Active Directory.
> 
> 

## <a name="connecting-to-a-data-source"></a>Ansluta till en datakälla
Anslut till en datakälla genom att välja datakällan i fönstret **Hämta data** och välja **Anslut**. I följande bild har **Webb** valts från dataanslutningskategorin **Övrigt**.

![](media/desktop-data-sources/data-sources_7b.png)

Ett fönster för anslutningen visas, specifik för dataanslutningstypen. Om det krävs autentiseringsuppgifter uppmanas du att ange dem. Följande bild visar en URL som anges för att ansluta till en webbdatakälla.

![](media/desktop-data-sources/datasources_fromwebbox.png)

När URL:en eller anslutningsinformationen för resursen har angetts, väljer du **OK**. Power BI Desktop ansluter till datakällan och visar tillgängliga datakällor i **navigatören**.

![](media/desktop-data-sources/datasources_fromnavigatordialog.png)

Du kan antingen läsa in data genom att välja knappen **Läs in** längst ned i **navigatören**, eller redigera frågan innan du läser in data genom att välja knappen **Redigera**.

Det är allt du behöver veta om att ansluta till datakällor i Power BI Desktop! Försök att ansluta till data från våra växande lista med datakällor och kom tillbaka ofta – vi fyller på listan hela tiden.

## <a name="next-steps"></a>Nästa steg
Det finns olika typer av saker som du kan göra med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datatyper i Power BI Desktop](desktop-data-types.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)    
