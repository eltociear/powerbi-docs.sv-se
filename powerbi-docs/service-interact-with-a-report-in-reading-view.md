---
title: "Interagera med en rapport i läsläget i Power BI"
description: "Interagera med en rapport i läsläget i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/15/2017
ms.author: mihart
ms.openlocfilehash: 54de712e0743801b3e8c565ca997bbc56e254c69
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="interact-with-a-report-in-reading-view-in-power-bi"></a>Interagera med en rapport i läsläget i Power BI
## <a name="reading-view"></a>Läsläge
Läsläge är inte interaktiv som [redigeringsvyn](service-interact-with-a-report-in-editing-view.md), men det finns fortfarande många alternativ för att utforska dina data. Detta är praktiskt när du visar rapporter som [delas med dig](service-share-dashboards.md) och som endast kan öppnas i läsläge.

Läsläge är ett roligt och säkert sätt att experimentera med och bekanta dig med dina data. I läsläget kan du korsmarkera och korsfiltrera visuella objekt på en sida.  Det är bara att markera eller välja ett värde i ett visuellt objekt så ser du direkt hur det påverkar andra visuella objekt. Använd filterfönstret för att lägga till och ändra filter på en rapportsida och ändra hur värden sorteras i en visualisering. Dina filtreringar eller markeringar sparas inte med rapporten.

## <a name="cross-highlight-the-related-visualizations-on-a-page"></a>Korsmarkera flera relaterade visualiseringar på en sida
Visualiseringar på en enstaka rapportsida är alla ”kopplade” till varandra.  Det innebär att om du väljer ett eller flera värden i en visualisering kommer andra visualiseringar som använder samma värde att ändras baserat på det valet.

![](media/service-interact-with-a-report-in-reading-view/pagefilter3b.gif)

> [!NOTE]
> Håll ned CTRL-tangenten för att välja fler än ett element i en visualisering.
> 
> 

## <a name="hover-over-visual-elements-to-see-the-details"></a>Håll muspekaren över visuella element för att visa detaljer
![](media/service-interact-with-a-report-in-reading-view/amarillachart.png)

## <a name="sort-the-data-in-a-visualization"></a>Sortera data i en visualisering
Välj ellipserna (...) för att öppna **Sortera efter**. Välj den nedrullningsbara pilen för att välja vilka fält som du vill sortera efter eller klicka på ikonen AZ för att växla mellan stigande och fallande. 

![](media/service-interact-with-a-report-in-reading-view/pbi_changechartsort.gif) 

## <a name="interact-with-filters"></a>Interagera med filter
Om rapportskaparen har lagt till filter på en sida i en rapport kan du interagera med dem i läsläget. Ändringarna sparas inte i rapporten.

1. Välj på filterikonen i det övre högra hörnet.
   
   ![](media/service-interact-with-a-report-in-reading-view/filters.png)  
2. Du ser alla filter som har kopplats till det visuella objektet du har valt (filter på visuell nivå), över hela sidan (filter på sidonivå) och i hela rapporten (filter på rapportnivå).
   
   ![](media/service-interact-with-a-report-in-reading-view/power-bi-reading-filters.png)
3. Håll muspekaren över ett filter och expandera det genom att välja nedpilen.
   
   ![](media/service-interact-with-a-report-in-reading-view/power-bi-expan-filter.png)
4. Göra ändringar i dina filter och se hur det visuella objektet påverkas.  
   
   * I det här exemplet har vi en filter på sidonivå för **Kedja**. Ändra det till **Fashions Direct** i stället för **Lindseys** genom att ta bort markeringen från den första och markera den andra.
     
     ![](media/service-interact-with-a-report-in-reading-view/power-bi-filter-chain.png)
   * Eller ta bort filtret helt från **kedjan** genom att välja raderingsikonen ![](media/service-interact-with-a-report-in-reading-view/power-bi-eraser-icon.png) eller genom att välja båda butiker.
   * Välj filtret på sidonivå **distrikt** och växla till **Avancerad filtrering**. Filter för att visa endast distrikt som börjar med **FD** och som inte får innehålla siffran 4.
     
     ![](media/service-interact-with-a-report-in-reading-view/power-bi-advanced-filter.png)

Mer information finns i [Lägga till ett filter i en rapport](power-bi-report-add-filter.md) och [Om filtrering och markering i rapporter](power-bi-reports-filters-and-highlighting.md).

## <a name="zoom-in-on-individual-visuals"></a>Zooma in på enskilda visuella objekt
Håll muspekaren över visualiseringen och välj ikonen **Fokusläge** ![](media/service-interact-with-a-report-in-reading-view/pbi_popouticon.jpg). När du visar en visualisering i fokusläge expanderas den så att den fyller hela rapportarbetsytan enligt nedan.

![](media/service-interact-with-a-report-in-reading-view/powerbi-focus-mode.png)

Om du vill visa att samma visualiseringen utan att störas av menyfält, filterfönstret och annan krom kan du välja ikonen **Helskärm** från den översta menyraden ![](media/service-interact-with-a-report-in-reading-view/power-bi-focus-icon.png) .

![](media/service-interact-with-a-report-in-reading-view/power-bi-full-screen.png)

Läs mer i [Fokusläge för rapporter](service-focus-mode.md) och [Helskärmsläge för rapporter](service-fullscreen-mode.md)

## <a name="adjust-the-display-dimensions"></a>Justera dimensionerna för visning
Rapporterna granskas på många olika enheter med olika skärmstorlekar och proportioner.  Standardåtergivningen är kanske inte vad du vill se på enheten.  Om du vill ändra detta, välj **visa** och sedan:

* Anpassa till sida: skalanpassa innehållet så att det passar på sidan
* Anpassa till bredd: skalanpassa innehållet så att det passar på sidans bredd
* Faktisk storlek: Visa innehåll i full storlek  

![](media/service-interact-with-a-report-in-reading-view/power-bi-view.png)

  I läsläget är visningsalternativet tillfälligt och sparas inte när du stänger rapporten.

  Läs mer i [Självstudier: Ändra visningsinställningarna för en rapport](power-bi-change-report-display-settings.md).

## <a name="next-steps"></a>Nästa steg
[Rapporter i Power BI](service-reports.md)

[Öppna redigeringsvy](service-reading-view-and-editing-view.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

