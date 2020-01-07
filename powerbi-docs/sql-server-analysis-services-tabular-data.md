---
title: SQL Server Analysis Services-realtidsdata i Power BI
description: SQL Server Analysis Services realtidsdata i Power BI. Detta görs via en datakälla som har konfigurerats för en företagsgateway.
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: Minewiskan
ms.author: owend
ms.reviewer: ''
ms.custom: ''
ms.date: 08/10/2017
LocalizationGroup: Data from databases
ms.openlocfilehash: 00b7c98236f37505fbb0ddec81a45b65bf3e3ee6
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "73871196"
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>SQL Server Analysis Services-realtidsdata i Power BI

Det finns två sätt att ansluta till en SQL Server Analysis Services-realtidsserver i Power BI. I **hämta data**, kan du ansluta till en SQL Server Analysis Services-server, eller så kan du ansluta till en [Power BI Desktop-fil](service-desktop-files.md), eller [Excel-arbetsbok](service-excel-workbook-files.md) som redan ansluter till en Analysis Services-server. Som bästa praxis rekommenderar Microsoft användning av Power BI Desktop på grund av den kompletta verktygsuppsättningens och möjligheten att upprätthålla en säkerhetskopia av Power BI Desktop-filen lokalt.

>[!IMPORTANT]
> * Om du vill ansluta till en Analysis Services-realtidsserver, måste en lokal datagateway installeras och konfigureras av en administratör. Mer information finns i [lokal datagateway](service-gateway-onprem.md).
> * När du använder gatewayen, blir dina data kvar lokalt.  Alla rapporter du skapar baserat på dessa data, sparas i Power BI-tjänsten. 
> * [Frågor och svar frågor med naturligt språk](service-q-and-a-direct-query.md) är i förhandsvisning för Analysis Services-realtidsanslutningar.

## <a name="to-connect-to-a-model-from-get-data"></a>Om du vill ansluta till en modell från hämta data

1. I **min arbetsyta** väljer du **hämta data**. Du kan också ändra till en grupparbetsyta om det finns en.

   ![Knappen Anslut för att hämta data](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)

2. Välj **Databaser och mer**.

   ![Anslut för att hämta data 1](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)

3. Välj **SQL Server Analysis Services** > **Anslut**.

   ![Anslut för att hämta data 2](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)

4. Välj en server. Om du inte ser några servrar listade här, betyder det antingen att ingen gateway och datakälla har konfigurerats, eller att ditt konto inte listas i fliken **användare** för datakällan i gatewayen. Kontrollera med din administratör.

5. Välj den modell du vill ansluta till. Det kan antingen vara tabell eller flerdimensionell.

När du ansluter till modellen, visas den i din Power BI-plats i **min arbetsyta/datauppsättningar**. Om du växlades till en grupparbetsyta, visas datauppsättningen i gruppen.

![Ansluta till datamängd](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Paneler på instrumentpanelen

Om du fäster visuella objekt från en rapport på instrumentpanelen, uppdateras de fästa panelerna automatiskt var tionde minut. Om data i din lokala Analysis Services-server uppdateras, blir panelerna automatiskt uppdaterade efter 10 minuter.

## <a name="common-issues"></a>Vanliga problem

* Det går inte att läsa in modellschemat – det här felet inträffar när användaren som ansluter till SSAS inte har åtkomst till SSAS-databasen, SSAS-kuben eller SSAS-modellen.

## <a name="next-steps"></a>Nästa steg

* [On-premises data gateway (Lokal datagateway)](service-gateway-onprem.md)  
* [Hantera Analys Services-datakällor](service-gateway-enterprise-manage-ssas.md)  
* [Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)