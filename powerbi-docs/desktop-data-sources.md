---
title: Datakällor i Power BI Desktop
description: Datakällor i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f5fc52df86faa69683fa1e76f8893fb1d1a09ab9
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281170"
---
# <a name="data-sources-in-power-bi-desktop"></a>Datakällor i Power BI Desktop
Med Power BI Desktop kan du ansluta till data från många olika källor. En fullständig lista med tillgängliga datakällor finns längst ned på den här sidan.

Anslut till data genom att välja **Hämta data** från menyfliksområdet **Start**. Om du väljer nedåtpilen eller texten **Hämta data** på knappen, visas menyn **Mest vanliga** datatyper, enligt följande bild:

![Hämta data i Power BI Desktop](media/desktop-data-sources/data-sources_01.png)

Om du väljer **Mer...** från menyn **Mest vanliga** visas fönstret **Hämta data**. Du kan också öppna fönstret **Hämta data** (och kringgå menyn **Mest vanliga**) genom att välja **Hämta data**-**ikonen** direkt.

![Knappen Hämta data](media/desktop-data-sources/data-sources_02.png)

> [!NOTE]
> Power BI-teamet utökar kontinuerligt de datakällor som är tillgängliga för **Power BI Desktop** och **Power BI-tjänsten**. Därför visas ofta tidiga versioner av pågående datakällor markerade med *beta* eller *förhandsversion*. Alla datakällor som har markerats som *beta* eller *förhandsversion* har begränsad support och funktionalitet och ska inte användas i produktionsmiljöer.

## <a name="data-sources"></a>Datakällor
Datatyperna ordnas i följande kategorier:

* Alla
* Fil
* Databas
* Power BI
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
* PDF (Beta)
* SharePoint-mapp

Följande bild visar fönstret **Hämta data** för **Fil**.

![Hämta data > Fil](media/desktop-data-sources/data-sources_03.png)

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
* SAP Business Warehouse Message Server
* Amazon Redshift
* Impala
* Google BigQuery
* Snowflake
* Essbase (Beta)
* BI-anslutningsapp
* Exasol
* Dremio (Beta)
* Jethro (Beta)
* Kyligence Enterprise (Beta)

> [!NOTE]
> Vissa databaskopplingar kräver att du aktiverar dem genom att välja **Arkiv > Alternativ och inställningar > Alternativ** sedan välja **Förhandsversionsfunktioner** och aktivera kopplingen. Om du inte ser några av de kopplingar som nämns ovan och vill använda dem, kontrollerar du dina inställningar för **Förhandsversionsfunktioner**. Observera att alla datakällor som har markerats som *beta* eller *förhandsversion* har begränsad support och funktionalitet och ska inte användas i produktionsmiljöer.

Följande bild visar fönstret **Hämta data** för **Databas**.

![Hämta Data > Databaser](media/desktop-data-sources/data-sources_04.png)

I **Power BI**-kategorin finns följande dataanslutningar:

* Power BI-datauppsättningar
* Power BI-dataflöden (Beta)

Följande bild visar fönstret **Hämta data** för **Power BI**.

![Hämta data > Power BI](media/desktop-data-sources/data-sources_05.png)

Kategorin **Azure** innehåller följande dataanslutningar:

* Azure SQL Database
* Azure SQL Data Warehouse
* Azure Analysis Services-databas
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB (beta)
* Azure Data Lake Storage
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive-fråga
* Azure Data Explorer (Beta)

Följande bild visar fönstret **Hämta data** för **Azure**.

![Hämta data > Azure](media/desktop-data-sources/data-sources_06.png)

Kategorin **Onlinetjänster** innehåller följande dataanslutningar:

* SharePoint Online-lista
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (lokal)
* Common Data Service för appar (beta)
* Microsoft Azure Consumption Insights (beta)
* Azure DevOps (Beta)
* Azure DevOps Server (Beta)
* Salesforce-objekt
* Salesforce-rapporter
* Google Analytics
* Adobe Analytics
* appFigures (beta)
* comScore Digital Analytix (beta)
* Dynamics 365 for Customer Insights (beta)
* Data.World – Hämta datauppsättning (beta)
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
* TeamDesk (beta)

Följande bild visar fönstret **Hämta data** för **Onlinetjänster**.

![Hämta data > Onlinetjänster](media/desktop-data-sources/data-sources_07.png)

Kategorin **Övrigt** innehåller följande dataanslutningar:

* Vertica
* Webb
* SharePoint-lista
* OData-feed
* Active Directory
* Microsoft Exchange
* Hadoop-fil (HDFS)
* Spark
* R-skript
* Python-skript
* ODBC
* OLE DB
* Denado
* Paxata (Beta)
* Tom fråga

Följande bild visar fönstret **Hämta data** för **Övrigt**.

![Hämta data > Övrigt](media/desktop-data-sources/data-sources_08.png)

> [!NOTE]
> För tillfället går det inte att ansluta till anpassade datakällor som skyddas med Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Ansluta till en datakälla
Anslut till en datakälla genom att välja datakällan i fönstret **Hämta data** och välja **Anslut**. I följande bild har **Webb** valts från dataanslutningskategorin **Övrigt**.

![Anslut till webben](media/desktop-data-sources/data-sources_08a.png)

Ett fönster för anslutningen visas, specifik för dataanslutningstypen. Om det krävs autentiseringsuppgifter uppmanas du att ange dem. Följande bild visar en URL som anges för att ansluta till en webbdatakälla.

![Ange webbadress](media/desktop-data-sources/datasources_fromwebbox.png)

När URL:en eller anslutningsinformationen för resursen har angetts, väljer du **OK**. Power BI Desktop ansluter till datakällan och visar tillgängliga datakällor i **navigatören**.

![Navigatörsskärmen](media/desktop-data-sources/datasources_fromnavigatordialog.png)

Du kan antingen läsa in data genom att välja knappen **Läs in** längst ned i **navigatören**, eller redigera frågan innan du läser in data genom att välja knappen **Redigera**.

Det är allt du behöver veta om att ansluta till datakällor i Power BI Desktop! Försök att ansluta till data från våra växande lista med datakällor och kom tillbaka ofta – vi fyller på listan hela tiden.

## <a name="next-steps"></a>Nästa steg
Det finns olika typer av saker som du kan göra med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datatyper i Power BI Desktop](desktop-data-types.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)    
