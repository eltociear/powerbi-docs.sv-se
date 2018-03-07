---
title: "Utsnitt i Power BI (självstudie)"
description: "Självstudie: Utsnitt i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/30/2017
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 619f694e6e3ed167a14262994c1c978d5b4ea2e0
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="slicers-in-power-bi-service-tutorial"></a>Utsnitt i Power BI-tjänsten (självstudie)
Din säljchef vill kunna titta på ett antal mått för hela divisionen och för varje enskild distriktschef. Hon skulle kunna skapa en separat rapportsida för varje chef eller använda ett utsnitt. Ett utsnitt begränsar den del av datauppsättningen som visas i andra visualiseringar på sidan.  Utsnitt är ett annat sätt att filtrera.

![](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>När ska du använda ett utsnitt
Utsnitt är ett bra val i följande situationer.

* Om du vill visa vanliga eller viktiga filter på rapportarbetsytan för enklare åtkomst.
* För att göra det lättare att se det aktuella filtrerade tillståndet utan att öppna listrutan för att få information om filtreringen.
* När du vill dölja kolumner som du inte behöver men fortfarande kunna använda dem för att filtrera – det här ger smalare, tydligare tabeller.
* För att skapa mer fokuserade rapporter – eftersom utsnitt är flytande objekt, kan du placera dem bredvid den intressanta delen av rapporten som du vill att användarna ska fokusera på.

## <a name="create-a-slicer"></a>Skapa ett utsnitt
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>


1. Öppna [Exemplet detaljhandelsanalys](sample-retail-analysis.md) i [redigeringsvyn](service-interact-with-a-report-in-editing-view.md) och [lägg till en ny rapportsida](power-bi-report-add-page.md).
2. I fältpanalen, väljer du **distrikt > distriktschef**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_chartfirst.png)
3. Konvertera visualiseringen till ett utsnitt. I visualiseringspanelen väljer du utsnittsikonen.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_select.png)

## <a name="format-the-slicer"></a>Formatera utsnittet
1. När utsnitt har valts, i visualiseringspanelen, väljer du färgrollerikonen ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) för att visa formateringsalternativen.
2. Välj **allmänt > konturfärg** och välj mörkblå och ändra **tjockleken** till **6**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_outline2.png)
3. Under **markeringskontroller**, som standard är **markera allt** **av** och **enskild markering** är **på**. Det innebär att jag måste använda CTRL-tangenten för att markera flera namn samtidigt. Sätt **markera alla** till **på** och **enskild markering** till **av**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_selectioncontrols2.png)
   
   * Observera att utsnittet nu har ett **markera alla**-alternativ överst i listan. Aktivera **markera alla** för att välja alla namn eller inga.
   * Du kan nu också välja flera namn utan att använda CTRL-tangenten.
4. Under **objekt**, ökar du textstorleken till 14 punkter.  Vi vill vara säkra på att våra kollegor kan se det här utsnittet.
5. Slutligen så anger vi **teckenfärg** som mörkröd.  Det kommer att skilja ut de markerade namnen från de omarkerade vårt utsnitt.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_font2.png)
6. Ha det kul med att utforska de andra alternativen för utsnitt.

## <a name="use-the-slicer-in-a-report"></a>Använd utsnitt i en rapport
1. Lägg till vissa ytterligare visualiseringar till rapportsidan eller öppna [Exempelrapporten detaljhandelsanalys](sample-retail-analysis.md) och välj fliken **distriktets månatliga försäljning**.
   
    ![](media/power-bi-visualization-slicers/power-bi-retail-sample.png)
2. Ta ett utsnitt på sidan för Carlos. Observera hur andra visualiseringar uppdateras för att återspegla valen.
   
    ![](media/power-bi-visualization-slicers/slicer2.gif)
3. Sortera utsnitt i alfabetisk ordning efter efternamn på distriktchefer.  Välj ellipserna (...) i det övre högra hörnet av utsnittet och välj **distriktschef**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sort2.png)
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sorted.png)

## <a name="control-what-effect-the-slicer-has-on-other-visuals-on-the-page"></a>Kontrollera vilken effekt utsnittet har på andra visuella objekt på sidan
Vill du att utsnitt bara filtrerar några av visualiseringarna på sidan?  Använd kontrollen **visuella interaktioner** för att kunna ställa in det.

**Obs**: Om du inte ser **visuella interaktioner**, leta efter ikonen istället ![](media/power-bi-visualization-slicers/power-bi-slicer-visual-interactions.png). Om du inte ser något, kontrollera att du är i rapportens [redigeringsvy](service-reading-view-and-editing-view.md).

1. Välj utsnitt för att göra den aktiv och, från menyfältet, väljer du**visuella interaktioner**.
   
    ![](media/power-bi-visualization-slicers/pbi-slicer-interactions.png)
2. Filterkontroller visas över alla andra visualiseringar på sidan. Om utsnittet ska filtrera ett visuellt objekt, väljer du **Filter**-ikonen.  Om utsnitt inte har någon effekt på visualiseringen, väljer du ikenen **ingen**.
   
    ![](media/power-bi-visualization-slicers/filter-controls.png)

Mer information finns i [visuella interaktioner i en Power BI-rapport](service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting-slicers-in-power-bi"></a>Överväganden och felsökning av utsnitt i Power BI
Det finns några begränsningar med att använda utsnitt i Power BI, vilka är följande:

1. Utsnitt stöder inte indatafält.
2. Ett enda utsnitt kan inte användas i hela rapporten. Ett utsnitt påverkar endast den aktuella sidan.
3. Utsnitt går inte att fästa på en instrumentpanel.
4. Det stöds inte att gå in på detaljnivå för utsnitt.    
5. Utsnitt stöder inte filter på visualiseringsnivå.

Har du förslag på hur vi kan förbättra Power BI? [Skicka in en idé](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

## <a name="next-steps"></a>Nästa steg
 [Lägg till en visualisering till en rapport](power-bi-report-add-visualizations-i.md)

 [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

 [Power BI – grundläggande begrepp](service-basic-concepts.md)

[Testa – det är kostnadsfritt!](https://powerbi.com/)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

