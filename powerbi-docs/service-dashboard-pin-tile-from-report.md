---
title: Fäst en panel på en Power BI-instrumentpanel från en rapport
description: Fäst en panel på en Power BI-instrumentpanel från en rapport.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: lJKgWnvl6bQ
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 968cf7e573a298c2a82adaf2092a9d35ffa397e5
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-a-report"></a>Fäst en panel på en Power BI-instrumentpanel från en rapport
## <a name="pinning-tiles-from-a-report"></a>Fästa paneler från en rapport
Ett sätt att lägga till en ny [instrumentpanel](service-dashboard-tiles.md) är från en [Power BI-rapport](service-reports.md). Du kan lägga till flera nya paneler från en rapport.  Var och en av dem är en länk tillbaka till rapporten när du klickar på dem.

Och hela rapportsidor kan fästas på en instrumentpanel.  Det kallas även att fästa en *live*-panel.  *Live* eftersom du kan interagera med panelen på instrumentpanelen och, till skillnad från enskilda visualiseringspaneler, synkroniseras ändringar i rapporten med instrumentpanelen. Läs mer om det här nedan.

Du kan inte fästa paneler från rapporter som har delats med dig eller från Power BI Desktop. 

> **Tips**: vissa visualiseringar använder bakgrundsbilder. Fästning kanske inte fungerar om bakgrundsbilden är för stor.  Försök att minska bildstorleken eller använd bildkomprimering.  
> 
> 

## <a name="pin-a-tile-from-a-report"></a>Fäst en panel från en rapport
Titta när Amanda skapar en instrumentpanel genom att fästa visuella objekt och bilder från en Power BI-rapport.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

Nu kan du skapa din egen instrumentpanel med en av Power BI-exempelrapporterna.

1. Hovra över den visualisering som du vill fästa och välj fästikonen ![](media/service-dashboard-pin-tile-from-report/pbi_pintile_small.png). Power BI öppnar skärmen **fäst på instrumentpanelen**.
   
     ![Fönstret Fäst på instrumentpanelen](media/service-dashboard-pin-tile-from-report/pbi_themes2.png)
2. Välj om du ska fästa panelen på en befintlig instrumentpanel eller em ny.
   
   * Befintlig instrumentpanel: välj instrumentpanelens namn i listrutan. Instrumentpaneler som har delats med dig visas inte i listrutan.
   * Ny instrumentpanel: skriv instrumentpanelens namn.
3. I vissa fall kan objektet du vill fästa ha ett redan tillämpat *tema*.  Visuella objekt som fästs från en Excel-arbetsbok till exempel. I så fall, väljer du vilket tema som ska tillämpas på panelen.
4. Välj **fäst**.
   
   Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.
   
   ![meddelande om slutförande](media/service-dashboard-pin-tile-from-report/pinsuccess.png)
5. Från navigeringsfönstret, väljer du instrumentpanelen med den nya panelen. Markera panelen för att hoppa tillbaka till rapporten. Eller, [redigera panelens visning och beteende](service-dashboard-edit-tile.md).

## <a name="pin-an-entire-report-page"></a>Fäst en hel rapportsida
Ett annat alternativ är att fästa en hel rapportsida till en instrumentpanel. Detta är ett enkelt sätt att fästa flera visualiseringar åt gången.  När du fäster en hel sida är panelerna dessutom *live*. Du kan interagera med dem direkt på instrumentpanelen. Ändringar du gör i någon av visualiseringarna i rapportredigeraren, om du till exempel lägger till ett filter eller ändrar fälten som används i diagrammet, visas då även på instrumentpanelen.  

Mer information finns i [fäst en hel rapportsida](service-dashboard-pin-live-tile-from-report.md)

## <a name="next-steps"></a>Nästa steg
[Instrumentpaneler i Power BI](service-dashboards.md)

[Paneler på instrumentpanelen i Power BI](service-dashboard-tiles.md)

[Rapporter i Power BI](service-reports.md)

[Datauppdatering i Power BI](refresh-data.md)

[Grundläggande begrepp i Power BI](service-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

