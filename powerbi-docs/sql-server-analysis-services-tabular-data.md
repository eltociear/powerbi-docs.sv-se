---
title: SQL Server Analysis Services-realtidsdata i Power BI
description: "SQL Server Analysis Services realtidsdata i Power BI. Detta görs via en datakälla som har konfigurerats för en företagsgateway."
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
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 6925dc9bcf3e500af18cf63c62f6cb33c297392b
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2017
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>SQL Server Analysis Services-realtidsdata i Power BI
Det finns två sätt att ansluta till en SQL Server Analysis Services-realtidsserver i Power BI. I **hämta data**, kan du ansluta till en SQL Server Analysis Services-server, eller så kan du ansluta till en [Power BI Desktop-fil](service-desktop-files.md), eller [Excel-arbetsbok](service-excel-workbook-files.md) som redan ansluter till en Analysis Services-server.

 >[!IMPORTANT]
 >* Om du vill ansluta till en Analysis Services-realtidsserver, måste en lokal datagateway installeras och konfigureras av en administratör. Mer information finns i [lokal datagateway](service-gateway-onprem.md).
 >* När du använder gatewayen, blir dina data kvar lokalt.  Alla rapporter du skapar baserat på dessa data, sparas i Power BI-tjänsten. 
 >* [Frågor och svar frågor med naturligt språk](service-q-and-a-direct-query.md) är i förhandsvisning för Analysis Services-realtidsanslutningar.

## <a name="to-connect-to-a-model-from-get-data"></a>Om du vill ansluta till en modell från hämta data
1. I **min arbetsyta** väljer du **hämta data**. Du kan också ändra till en grupparbetsyta om det finns en.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)
2. Välj **databaser och mer**.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)
3. Välj **SQL Server Analysis Services** > **anslut**. 
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)
4. Välj en server. Om du inte ser några servrar listade här, betyder det antingen att ingen gateway och datakälla har konfigurerats, eller att ditt konto inte listas i fliken **användare** för datakällan i gatewayen. Kontrollera med din administratör.
5. Välj den modell du vill ansluta till. Det kan antingen vara tabell eller flerdimensionell.

När du ansluter till modellen, visas den i din Power BI-plats i **min arbetsyta/datauppsättningar**. Om du växlades till en grupparbetsyta, visas datauppsättningen i gruppen.

![](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Paneler på instrumentpanelen
Om du fäster visuella objekt från en rapport på instrumentpanelen, uppdateras de fästa panelerna automatiskt var tionde minut. Om data i din lokala Analysis Services-server uppdateras, blir panelerna automatiskt uppdaterade efter 10 minuter.

## <a name="next-steps"></a>Nästa steg
[Lokal datagateway](service-gateway-onprem.md)  
[Hantera Analys Services-datakällor](service-gateway-enterprise-manage-ssas.md)  
[Felsökning av den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

