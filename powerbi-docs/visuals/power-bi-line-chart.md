---
title: Linjediagram i Power BI
description: Linjediagram i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0654dccf55b1e13f26d8ecaabee0349f0e56afc6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65535800"
---
# <a name="line-charts-in-power-bi"></a>Linjediagram i Power BI
Ett linjediagram är en serie datapunkter som representeras av punkter och anslutna via raka linjer. Ett linjediagram kan innehålla en eller flera rader. Linjediagram har ett X och Y-axeln. 

![enkelt linjediagram](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Skapa ett linjediagram
Dessa anvisningar används på försäljning och marknadsföring appen att skapa ett linjediagram som visar årets försäljning efter kategori. Om du vill följa med kan du hämta exempelappen från appsource.com.

1. Börja med en tom rapportsida. Om du inte använder Power BI-tjänsten, se till att du öppnar rapporten i [Redigeringsvyn](../service-interact-with-a-report-in-editing-view.md).

2. Från fönstret fält, Välj **salesfact (säljfakta)** \> **Totalt antal enheter**, och välj **datum** > **månad**.  Powerbi skapar ett stapeldiagram på rapportarbetsytan.

    ![Välj från fönstret fält](media/power-bi-line-charts/power-bi-step1.png)

4. Konvertera till ett linjediagram genom att välja diagrammall rad från fönstret visualiseringar. 

    ![Konvertera till linjediagram](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtrera din linjediagram för att visa data i flera år 2012 2014. Om din filterfönstret är komprimerat expanderar du den nu. Från fönstret fält, Välj **datum** \> **år** och dra den till fönstret filter. Släpp den under rubriken **filter på det här visuella objektet**. 
     
    ![rad bredvid fönstret fält](media/power-bi-line-charts/power-bi-year-filter.png)

    Ändra **avancerade filter** till **grundläggande filter** och välj **2012**, **2013** och **2014**.

    ![Filter för år](media/power-bi-line-charts/power-bi-filter-year.png)

6. Du kan också [justera storlek och färg för diagramtexten](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Öka teckenstorlek och ändra Y axisfont](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Lägga till ytterligare rader i diagrammet
Linjediagram kan ha många olika rader. Och i vissa fall kan värdena på raderna kanske avvikande så att de inte visas tillsammans. Låt oss titta på att lägga till ytterligare rader till våra aktuella diagram och lär dig sedan att formatera diagrammet när de värden som representeras av raderna är mycket olika. 

### <a name="add-additional-lines"></a>Lägg till ytterligare rader
I stället för att titta på totalt antal enheter för alla regioner som en enda rad i diagrammet, vi dela upp till totalt antal enheter per region. Lägg till ytterligare rader genom att dra **Geo** > **Region** till brunnen förklaring.

   ![En rad för varje region](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Använd två Y-axlar
Vad händer om du vill titta på total försäljning och Totalt antal enheter i samma schema? Försäljningssiffrorna är mycket högre än enhetsnummer, vilket gör linjediagrammet inte kan användas. Den röda linjen för totalt antal enheter visas i själva verket ska vara noll.

   ![mycket avviker värden](media/power-bi-line-charts/power-bi-diverging.png)

Visa mycket avvikande värden i ett diagram genom att använda ett kombinationsdiagram. Du kan lära dig allt om kombinationsdiagram genom att läsa [kombinationsdiagram i Power BI](power-bi-visualization-combo-chart.md). I vårt exempel nedan har kan vi Visa försäljnings- och Totalt antal enheter tillsammans i ett diagram genom att lägga till en andra Y-axel. 

   ![mycket avviker värden](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* Ett linjediagram kan inte ha dubbla Y-axlar.  Du måste använda ett kombinationsdiagram i stället.
* I exemplen ovan har diagrammen formaterade för att öka teckenstorlek, ändra teckenfärg, lägga till axelrubriker, diagramrubrik och förklaring center, starta båda axlarna på noll och mycket mer. Formateringsfönstret (färgrollerikonen) har en till synes ändlösa uppsättning med alternativ för att göra dina diagram ser på sätt som du vill. Det bästa sättet att lära dig är att öppna formateringsfönstret och utforska.

## <a name="next-steps"></a>Nästa steg

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


