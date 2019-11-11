---
title: Tips för färgformatering i Power BI
description: Tips för färgformatering i Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3865647a056e28735894e40f71045305518642c6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880644"
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

Om du vill göra några ändringar måste du redigera en rapport. Öppna rapporten och välj **Redigera rapport** från menyområdet, enligt följande bild.

![här hittar du menyn Redigera](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-report.png)

När du ser fönstren **Filter** och **Visualiseringar** till höger på rapportarbetsytan kan du börja anpassa rapporten. Om fönstret inte visas klickar du på pilen i det övre högra hörnet att öppna det.

![rapportarbetsyta i redigeringsvyn](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

## <a name="change-the-color-of-a-single-data-point"></a>Ändra färg på en enskild datapunkt
Ibland vill du kanske markera en viss datapunkt. Kanske gäller det försäljningssiffrorna i samband med lanseringen av en ny produkt, eller förbättrade kvalitetsresultat när du startar ett nytt program. Med Power BI kan du markera en viss datapunkt genom att ändra dess färg.

Följande visualisering rangordnar enheter sålda per produktsegment. 

![Ändra till grå färg för data](media/service-tips-and-tricks-for-color-formatting/power-bi-data.png)

Anta nu att du vill att anropa segmentet **Bekvämlighet** för att visa hur väl den här helt nya segmentet fungerar, genom att använda färg. Gör så här:

Expandera avsnittet **Datafärger** och aktivera skjutreglaget för **Visa alla**. Då visas färgerna för varje dataelement i visualiseringen. När du hovrar över datapunkter är bläddring aktiverat, så kan du kan modifiera valfria datapunkter.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show.png)

Ställ in **Bekvämlighet** på orange. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

När du är klar visas datapunkten **Bekvämlighet** med en fin orange nyans som verkligen står ut.

Även om du ändrar visualiseringstyper, och sedan går tillbaka, så kommer Power BI ihåg ditt val och bevarar **Bekvämlighet** orange.

Du kan ändra färg på en datapunkt för ett, flera eller alla dataelement i visualiseringen. Kanske vill du att ditt visuella objekt ska efterlikna företagets färger. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Det finns olika typer av saker du kan göra med färger. I nästa avsnitt ta vi en titt på toningar.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basera färgerna i ett diagram på ett numeriskt värde
Diagram tjänar ofta på att man använder dynamisk färginställning som baseras på fältens numeriska värden. Med den här metoden kan du visa ett annat värde än vad som används för stapelns storlek, och visa två värden i ett enskilt diagram. Eller så kan du använda det för att markera datapunkter över (eller under) ett visst värde – t.ex. områden med låg lönsamhet.

I följande avsnitt visar vi olika sätt på vilka man kan basera färger på numeriska värden.

## <a name="base-the-color-of-data-points-on-a-value"></a>Basera datapunkternas färg på ett värde
Om du vill ändra färg baserat på ett värde öppnar du formateringsfönstret och väljer alternativet **Villkorsstyrd formatering**.  

![välj alternativet för villkorsstyrd formatering genom att klicka på de tre lodräta punkterna](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting.png)

Använd listrutorna i fönstret Standardfärger till att identifiera vilka fält som villkorsstyrd formatering ska användas för. I det här exemplet har vi valt fältet **Sales fact** > **Total Units** och valt ljusblå färg för **Lowest value** samt mörkblå färg för **Highest value**. 

![inställningar för villkorsstyrd formatering av datafärg](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![stapeldiagram med standardfärger](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

Du kan också formatera färgen för det visuella objektet med hjälp av ett fält som inte ingår i det visuella objektet. I följande bild används **%Market Share SPLY YTD**. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Här kan vi se att även om vi har sålt fler enheter av både **Productivity** och **Extreme** (deras kolumner är högre) så har **Moderation** större **%Market Share SPLY YTD** (dess kolumn har högre färgmättnad).

## <a name="customize-the-colors-used-in-the-color-scale"></a>Anpassa färgerna som används i färgskalan
Du kan också ändra hur värdena mappas till dessa färger. I följande bild har färgerna för **lägsta** och **högsta** ställts in på orange respektive grönt.

Notera hur diagramstaplarna i den första bilden reflekterar den toning som visas i stapeln. Det högsta värdet är grönt, det lägsta är orange, och varje mellanliggande stapel har en färgton som ligger i spektrumet någonstans mellan grönt och orange.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Nu ska vi se vad som händer om vi tillhandahåller numeriska värden i värdefälten **Minimum** och **Maximum**. Vi ställer in **Minimum** på 3 500 och **Maximum** på 6 000.

Om du anger dessa värden så tillämpas inte toningen längre på värden i diagrammet som är lägre än **Lägsta** eller högre än **Högsta**. Alla staplar med värden över **Högsta** färgas gröna, och alla staplar med värden under **Lägsta** färgas röda.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

## <a name="use-diverging-color-scales"></a>Använda avvikande färgskalor
Ibland kan dina data ha en naturligt avvikande skala. Ett temperaturintervall har ett naturligt centrum vid fryspunkten, och en lönsamhetsskala har en naturlig mittpunkt (noll).

Om du vill använda avvikande färgskalor väljer du alternativet **Divergerande**. När du har aktiverat **Divergerande** visas ytterligare en färgväljare som kallas **Mitten**, som du ser i följande bild.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging2.png)

När skjutreglaget **Avvikande** har aktiverats kan du ange färgerna för **Lägsta**, **Högsta** och **Mitten** separat. I följande bild är **Center** (Mitten) inställt på .2 för **% Market Share SPLY YTD**, så staplar med värden över .2 har olika toningar av grönt medan staplar med värden under har olika toningar av rött.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

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

