---
title: Tips för färgformatering i Power BI
description: Tips för färgformatering i Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 3c91a6a70899a4a59c3d98cd9ab948284df5b662
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Tips för färgformatering i Power BI
Power BI erbjuder många olika sätt på vilka du kan anpassa dina instrumentpaneler och rapporter. Den här artikeln innehåller detaljerad information om en samling tips med vilkas hjälp du kan göra dina Power BI-visualiseringar mer intressanta och anpassade efter dina behov.

Följande tips tillhandahålls. Har du ytterligare något bra tips? Toppen! Skicka det till oss, så ska vi se till att lägga till det på listan.

* Ändra färg på en enskild datapunkt
* Basera färgerna i ett diagram på ett numeriskt värde
* Basera datapunkternas färg på ett fältvärde
* Anpassa färgerna som används i färgskalan
* Använda avvikande färgskalor
* Hur du ångrar i Power BI

Om du vill göra några ändringar måste du redigera en rapport: välj **rapporten** i fönstret **Min arbetsyta** och välj sedan **Redigera rapport** från menyområdet högst upp, så som visas i bilden nedan.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_1.png)

När fönstret **Visualiseringar** visas utmed den högra sidan av arbetsytan **Rapport** och du kan börja anpassa.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_2.png)

## <a name="change-the-color-of-a-single-data-point"></a>Ändra färg på en enskild datapunkt
Ibland vill du kanske markera en viss datapunkt. Kanske gäller det försäljningssiffrorna i samband med lanseringen av en ny produkt, eller förbättrade kvalitetsresultat när du startar ett nytt program. Med Power BI kan du markera en viss datapunkt genom att ändra dess färg.

Följande visualiseringen rangordnar stater efter levnadskostnader. 

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_3.png)

Anta att du snabbt och enkelt vill visa var i den rankningslistan Washington hamnar med hjälp av färgmarkering. Gör så här:

Utöka avsnittet **Datafärger**. Följande visas.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_4.png)

Ställ in **Visa alla** på värdet **På**. Då visas färgerna för varje dataelement i visualiseringen. När du hovrar över datapunkter är bläddring aktiverat, så kan du kan modifiera valfria datapunkter.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_5.png)

Låt oss ändra **Washington** till grönt. Vi rullar ned till **Washington** och väljer nedpilen i dess färgruta. Då visas fönstret för färgval.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_6.png)

När du är klar visas datapunkten **Washington** med en fin grön nyans som verkligen står ut.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_7.png)

Även om du ändrar visualiseringstyper, och sedan går tillbaka, så kommer Power BI ihåg ditt val och bevarar **Washington** grönt.

Du kan ändra färg på en datapunkt för mer än ett dataelement. I följande bild är **Arizona** rött, och **Washington** är fortfarande grönt.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_8.png)

Det finns olika typer av saker du kan göra med färger. I nästa avsnitt ta vi en titt på toningar.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basera färgerna i ett diagram på ett numeriskt värde
Diagram tjänar ofta på att man använder dynamisk färginställning som baseras på fältens numeriska värden. Med den här metoden kan du visa ett annat värde än vad som används för stapelns storlek, och visa två värden i ett enskilt diagram. Eller så kan du använda det för att markera datapunkter över (eller under) ett visst värde – t.ex. områden med låg lönsamhet.

I följande avsnitt visar vi olika sätt på vilka man kan basera färger på numeriska värden.

## <a name="base-the-color-of-data-points-on-a-value"></a>Basera datapunkternas färg på ett värde
Om du vill ändra färg utifrån ett värde, så dra det fält som du vill basera färgen på till fältet **Färgmättnad** i fönstret **Fält**. I följande bild har **Vinst före skatt** dragits till **Färgmättnad**. Även om **Velo** har högre **Bruttoförsäljning** (kolumnen är högre) så har **Amarilla** större **Vinst före skatt** (dess kolumn har högre färgmättnad).

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_9.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>Anpassa färgerna som används i färgskalan
Du kan även anpassa färgerna som används i färgskalan. Expandera **Datafärger**. Då visas en färgtoning som används för att visualisera dina data. Det lägsta värdet i dina data mappas som standard till den minst mättade färgen, och det högsta värdet mappas till den mest mättade färgen.

Färgintervallet visas i en toningsstapel som visar spektrumet mellan färgvärdena **lägsta** och **högsta**, med **lägsta** färgvärdet till vänster och **högsta** färgvärdet till höger.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_10.png)

Om du vill ändra skalan och använda en annan uppsättning färger, så välj färglistrutan bredvid **lägsta** eller **högsta** och välj en färg. Följande bild visar hur den **högsta** färgen ändrats till svart och toningsstapeln visar det nya spektrumet mellan **lägsta** och **högsta**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

Du kan också ändra hur värdena mappas till dessa färger. I följande bild har färgerna för **lägsta** och **högsta** ställts in på orange respektive grönt.

Notera hur diagramstaplarna i den första bilden reflekterar den toning som visas i stapeln. Det högsta värdet är grönt, det lägsta är orange, och varje mellanliggande stapel har en färgton som ligger i spektrumet någonstans mellan grönt och orange.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Nu ska vi se vad som händer om vi tillhandahåller numeriska värden i värderutorna **Lägsta** och **Högsta** som är lägre än värdena i färgväljarna **Lägsta** och **Högsta** (se följande bild). Låt oss ställa in **Lägsta** på 20 000 000 och **Högsta** på 20 000 000.

Om du anger dessa värden så tillämpas inte toningen längre på värden i diagrammet som är lägre än **Lägsta** eller högre än **Högsta**. Alla staplar med värden över **Högsta** färgas gröna, och alla staplar med värden under **Lägsta** färgas röda.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Använda avvikande färgskalor
Ibland kan dina data ha en naturligt avvikande skala. Ett temperaturintervall har ett naturligt centrum vid fryspunkten, och en lönsamhetsskala har en naturlig mittpunkt (noll).

Om du vill använda avvikande färgskalor så dra skjutreglaget **Avvikande** till **På**. När du har aktiverat **Avvikande** visas ytterligare en färgväljare och en värderuta, som båda kallas **Mitten**, så som visas på följande bild.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

När skjutreglaget **Avvikande** har aktiverats kan du ange färgerna för **Lägsta**, **Högsta** och **Mitten** separat. I följande bild har **Mitten** ställts in på ett, så staplar med värden över ett utgör olika toningar av grönt, och staplar med värden under ett utgör olika toningar av rött.

## <a name="how-to-undo-in-power-bi"></a>Hur du ångrar i Power BI
Precis som med många andra Microsoft-tjänster och program så erbjuder Power BI ett enkelt sätt på vilket du kan ångra ditt senaste kommando. Låt oss säga att du t.ex. ändrar färg på en datapunkt, eller en serie datapunkter, och du inte tycker om färgen när den visas i visualiseringen. Du kommer inte ihåg exakt vilken färg du hade tidigare, men du vill ha tillbaka den!

Om du vill **ångra** din senaste åtgärd, eller ett antal av dina senaste åtgärder, är allt du behöver göra följande:

- Skriv CTRL + Z

## <a name="feedback"></a>Feedback
Har du något tips som du vill dela? Skicka det till oss, så ska vi se till att lägga till det här.

>[!NOTE]
>Dessa färger, axlar och relaterade anpassningar är tillgängliga när ikonen **Format** är markerad, och de är också tillgängliga i Power BI Desktop.

## <a name="next-steps"></a>Nästa steg
[Komma igång med färgformatering och axelegenskaper](service-getting-started-with-color-formatting-and-axis-properties.md)

