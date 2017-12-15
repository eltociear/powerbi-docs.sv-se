---
title: "Kombinationsdiagram i Power BI (självstudier)"
description: "Den här dokumentationen innehåller självstudier (med video) som visar varför och hur du skapar ett kombinationsdiagram i Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: lnv66cTZ5ho
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: c00ba74501a411743036c4514750bccbbae3eb00
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="combo-chart-in-power--tutorial"></a>Kombinationsdiagram i Power BI (självstudier)
I Power BI är ett kombinationsdiagram en enskild visualisering som kombinerar ett linjediagram med ett stapeldiagram. Om du kombinerar de två diagrammen till ett kan du göra en snabbare jämförelse av dina data.

Kombinationsdiagram kan ha en eller två Y-axlar.

## <a name="when-to-use-a-combo-chart"></a>När du ska använda ett kombinationsdiagram
Kombinationsdiagram är ett bra alternativ:

* när du har ett linjediagram och ett stapeldiagram med samma X-axel,
* för att jämföra flera mått med olika värdeintervall,
* för att illustrera sambandet mellan två mätvärden i en visualisering,
* för att kontrollera om ett mätvärde uppfyller det mål som definieras av ett annat mätvärde,
* för att spara utrymme på arbetsytan.

## <a name="create-a-basic-single-axis-combo-chart"></a>Skapa ett grundläggande kombinationsdiagram med en axel
Se hur Will skapar ett kombinationsdiagram med exemplet på försäljning och marknadsföring.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Om du vill skapa ett eget kombinationsdiagram, loggar du in till Power BI och väljer **Hämta data \> Exempel \> Exempel på detaljhandelsanalys**. 

1. Välj **Totalt antal butiker** från instrumentpanelen ”Exempel på detaljhandelsanalys” för att öppna rapporten ”Exempel på detaljhandelsanalys”.
2. Välj **Redigera rapport** för att öppna rapporten i redigeringsvyn.
3. [Lägg till en ny rapportsida](power-bi-report-add-page.md).
4. Skapa ett stapeldiagram som visar årets försäljning och bruttomarginal per månad.
   
    a.  Välj **Försäljning** \> **This Year Sales (Årets försäljning)** > **Värde** i fönstret Fält.
   
    b.  Dra **Försäljning** \> **Gross Margin This Year (Årets bruttomarginal)** till området **Värde**.
   
    c.  Välj **Tid**\>**FiscalMonth (Räkenskapsmånad)** och lägg till det i området **Axel**. 
   
    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Välj ellipserna (...) i det övre högra hörnet av visualiseringen och välj **Sort by FiscalMonth (Sortera efter räkenskapsmånad)**.
6. Konvertera stapeldiagrammet till ett kombinationsdiagram. Välj **Linje- och grupperat stapeldiagram** i fönstret **Visualiseringar** med stapeldiagrammet markerat.
   
    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. Från panelen **Fält** drar du **Försäljning** \> **Last Years Sales (Förra årets försäljning)** till behållaren **Radvärden**.
   
   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)
   
   Kombinationsdiagrammet bör se ut ungefär så här:
   
   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Skapa ett kombinationsdiagram med två axlar
I det här steget ska vi jämföra bruttomarginal och försäljning.

1. Skapa ett nytt linjediagram som spårar bruttomarginal % förra året per månad.  I januari var bruttomarginal % 35 %, med en topp på 45 % i april som sjönk i juli och fick ytterligare en topp igen i augusti. Ser vi ett liknande mönster för försäljningen föregående år och det här året?
   
   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Lägg till **This Year Sales (Årets försäljning) > Värde** och **Last Years Sales (Förra årets försäljning)** till linjediagrammet. Skalan för **GM% Last Year (Bruttomarginal % förra året)** är mycket mindre än skalan för **Försäljning**, vilket gör det svårt att jämföra.      
   
   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Konvertera linjediagrammet till ett stående linje- och stapeldiagram om du vill göra det visuella objektet lättare att läsa och tolka.
   
   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Dra **Gross Margin% Last Year (Bruttomarginal % förra året)** från **Kolumnvärde** till **Radvärden**. Power BI skapar två axlar, vilket medför att datauppsättningarna kan skalas på olika sätt; den till vänster mäter dollar och den till höger procentandel.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-combochart.png)    

## <a name="add-titles-to-the-axes"></a>Lägga till rubriker på axlarna
1. Välj färgrollerikonen ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) för att öppna formateringsfönstret.
2. Välj nedpilen för att expandera alternativen för **y-axeln**.
3. För **Y-axel (kolumn)** anger du **Position** till **Vänster** och **Rubrik** till **På**,  **Format** till **Visa endast rubriken** och **Visa** som **Miljoner**.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-y-axis-column.png)
4. Under **Y-axeln (kolumn)** ska du också se till att **Visa sekundär** är **På**. Detta visar alternativ för att formatera linjediagramsdelen i kombinationsdiagrammet.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-show-secondary.png)
5. För **Y-axeln (rad)** lämnar du **Position** som **Höger**, ställer in **Rubrik** till **På** och ställer in **Format** på **Visa endast rubriken**.
   
   Kombinationsdiagrammet visar nu dubbla axlar, båda med rubriker.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

Härifrån kan du vilja:

* [lägga till kombinationsdiagrammet som en panel på instrumentpanelen](service-dashboard-tiles.md),
* [Spara rapporten](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Markering och korsfiltrering
Information om hur du använder fönstret Filter finns i [Lägga till ett filter i en rapport](power-bi-report-add-filter.md).

Om du markerar en kolumn eller linje i ett kombinationsdiagram korsfiltreras de övriga visualiseringarna på sidan, och vice versa.

## <a name="next-steps"></a>Nästa steg
[Lägga till en visualisering till en rapport](power-bi-report-add-visualizations-i.md)

[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

[Testa – det är kostnadsfritt!](https://powerbi.com/)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

