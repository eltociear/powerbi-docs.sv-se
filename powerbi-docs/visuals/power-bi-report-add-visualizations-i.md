---
title: Del 1, lägg till visualiseringar i en Power BI-rapport
description: Del 1, lägg till visualiseringar i en Power BI-rapport
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: df53cf238a52502cecb4d1f77482b7b1a09c6b7a
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46545278"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>Del 1, lägg till visualiseringar i en Power BI-rapport
Den här artikeln ger en snabb introduktion till att skapa en visualisering i en rapport med antingen Power BI-tjänsten eller Power BI Desktop.  För mer avancerat innehåll, se [del II](power-bi-report-add-visualizations-ii.md). Amanda visar ett par sätt att skapa, redigera och formatera visuella objekt på rapportarbetsytan. Prova sedan att skapa en egen rapport med hjälp av den [Försäljning- och marknadsföringsexempel](../sample-datasets.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Öppna en rapport och lägg till en ny sida
1. Öppna en rapport i [redigeringsvyn](../consumer/end-user-reading-view.md). Den här kursen använder exemplet för [försäljning och marknadsföring](../sample-datasets.md).
2. Om fönstret Fält inte visas, väljer du på pilikonen för att öppna den. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. [Lägg till en ny sida i rapporten](../power-bi-report-add-page.md).

## <a name="add-visualizations-to-the-report"></a>Lägg till visuella objekt i rapporten
1. Skapa ett visuellt objekt genom att välja ett fält från fönstret **Fält**.  
   
   **Börja med ett numeriskt fält** som SalesFact > Sales $. Power BI skapar ett stapeldiagram med en enda kolumn.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **Eller börja med ett kategorifält**, till exempel namn eller produkt: Power BI skapar en tabell och lägger till fältet till **Värden**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **Eller börja med ett geografiskt fält**, till exempel Geo > Stad. Power BI och Bing Maps skapar en kartvisualisering.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Skapa en visualisering och ändra dess typ. Välj **Produkt > Kategori**, sedan **Produkt > Antal produkter** för att lägga till dem i **Värden**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Ändra visualiseringen till ett stapeldiagram genom att välja ikonen stapeldiagram.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. När du skapar visualiseringar i rapporten kan du [fästa dem på din instrumentpanel](../service-dashboard-pin-tile-from-report.md). Välj fästikonen ![](media/power-bi-report-add-visualizations-i/pinnooutline.png) för att fästa visualiseringen.
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>Nästa steg
 Fortsätta till [Del 2, Lägga till visualiseringar i en Power BI-rapport](power-bi-report-add-visualizations-ii.md)
   
   [Interagera med visualiseringar](../consumer/end-user-reading-view.md) i rapporten.
   
   [Gör ännu mer med visualiseringar](power-bi-report-visualizations.md).
   
   [Spara rapporten](../service-report-save.md).
