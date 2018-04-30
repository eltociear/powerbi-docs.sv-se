---
title: Del 1, Lägga till visualiseringar i en Power BI-rapport (självstudie)
description: 'Självstudier: Del 1, Lägga till visualiseringar i en Power BI-rapport'
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
featuredvideoid: IkJda4O7oGs
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b6fdc11b19e130272cf715f4cff58721f46dd6e8
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="part-i-add-visualizations-to-a-power-bi-report-tutorial"></a>Del 1, Lägga till visualiseringar i en Power BI-rapport (självstudie)
Den här artikeln ger en snabb introduktion till att skapa en visualisering i en rapport med antingen Power BI-tjänsten eller Power BI Desktop.  För mer avancerat innehåll, se [del II](power-bi-report-add-visualizations-ii.md). Amanda visar ett par sätt att skapa, redigera och formatera visuella objekt på rapportarbetsytan. Prova sedan att skapa en egen rapport med hjälp av den [Försäljning- och marknadsföringsexempel](sample-datasets.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Öppna en rapport och lägg till en ny sida
1. Öppna en rapport i [redigeringsvyn](service-reading-view-and-editing-view.md). Den här kursen använder exemplet för [försäljning och marknadsföring](sample-datasets.md).
2. Om fönstret Fält inte visas, väljer du på pilikonen för att öppna den. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. [Lägg till en ny sida i rapporten](power-bi-report-add-page.md).

## <a name="add-visualizations-to-the-report"></a>Lägg till visuella objekt i rapporten
1. Skapa ett visuellt objekt genom att välja ett fält från fönstret **Fält**.  
   
   **Börja med ett numeriskt fält** som Försäljning > Försäljning $: Power BI skapar ett stapeldiagram med en enda kolumn.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **Börja med ett kategorifält**, till exempel namn eller produkt: Power BI skapar en tabell och lägger till fältet till brunnen **Värden**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **Börja med ett geografiskt fält**, till exempel Geo > Stad. Power BI och Bing Maps skapar en kartvisualisering.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Skapa en visualisering och ändra dess typ. Välj **Produkt > Antal produkter** och **Produkt > Kategori** för att lägga till dem i brunnen **Värden**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Ändra visualiseringen till ett stapeldiagram genom att välja ikonen stapeldiagram.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. När du skapar visualiseringar i rapporten kan du [fästa dem på din instrumentpanel](service-dashboard-pin-tile-from-report.md). Välj fästikonen ![](media/power-bi-report-add-visualizations-i/pinnooutline.png) för att fästa visualiseringen.
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
5. Nu kan du:
   
   Fortsätta till [Del 2, Lägga till visualiseringar i en Power BI-rapport](power-bi-report-add-visualizations-ii.md)
   
   [Interagera med visualiseringar](service-reading-view-and-editing-view.md) i rapporten.
   
   [Gör ännu mer med visualiseringar](power-bi-report-visualizations.md).
   
   [Spara rapporten](service-report-save.md).

## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md).

[Rapporter i Power BI](service-reports.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

