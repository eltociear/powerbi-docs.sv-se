---
title: Sortera efter kolumn i Power BI Desktop
description: Du kan ändra utseendet för ett visuellt objekt i Power BI genom att sortera det enligt olika datafält.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 0cbba86bd77debda9ab2162b8f9b190e1846b99c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464699"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Sortera efter kolumn i Power BI Desktop
I Power BI Desktop och Power BI-tjänsten kan du ändra utseendet på ett visuellt objekt genom att sortera det enligt olika datafält. Genom att ändra sorteringen för ett visuellt objekt kan du framhäva den information som du vill förmedla och se till att det visuella objektet speglar trenden på rätt sätt.

Om du använder numeriska data (till exempel försäljningssiffror) eller textdata (till exempel namn på delstater) kan du sortera dina visuella objekt och utforma dem som du vill. Du har stor flexibilitet gällande sortering i Power BI och du kan använda olika snabbmenyer. Välj **Fler alternativ** (...) för valfritt visuellt objekt, välj **Sortera efter** och sedan det fält du vill sortera efter.

![Menyn Fler alternativ](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>Sorteringsexempel
Låt oss ta ett mer ingående exempel och se hur det fungerar i Power BI Desktop.

Följande visualisering visar kostnader, antal och belopp efter tillverkare. Så här ser det visuella objektet ut innan vi sorterar ytterligare:

![Ursprunglig visualisering](media/desktop-sort-by-column/sortbycolumn_1.png)

Det visuella objektet sorteras för närvarande efter kolumnen **SalesQuantity**. Vi kan bestämma sorteringskolumnen genom att matcha färgen på staplarna mot förklaringen, men det finns ett bättre sätt: menyn **Fler alternativ** som du öppnar genom att välja ellipsen (...).

![Menyn Fler alternativ](media/desktop-sort-by-column/sortbycolumn_2.png)

Du har följande sorteringsalternativ:

* Det nuvarande sorteringsfältet är **SalesQuantity**, vilket visas med **SalesQuantity** i fetstil och en gul markering. 

* Den nuvarande sorteringsriktningen är stigande, vilket visas med **Sortera stigande** i fetstil och ett gult fält.

Vi ska titta närmare på sorteringsfältet och riktningen i följande två avsnitt.

## <a name="select-which-column-to-use-for-sorting"></a>Välj vilken kolumn som ska användas för sortering
Du såg den gula markeringen innan **SalesQuantity** på menyn **Fler alternativ**, vilket innebär att det visuella objektet sorteras baserat på kolumnen **SalesQuantity**. Det är enkelt att sortera efter en annan kolumn: välj ellipserna (...) för att öppna menyn **Fler alternativ**, välj **Sortera efter** och välj sedan en annan kolumn.

I den här bilden har vi valt **DiscountAmount** som kolumn att sortera efter. Den här kolumnen visas som en av linjerna i det visuella objektet snarare än en stapel. 

![Sortera efter DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Observera hur den visuella informationen har ändrats. Nu sorteras värdena från det högsta **DiscountAmount**-värdet, i detta fall Fabrikam Inc., och nedåt till det lägsta värdet som är Northwind Traders. 

Men vad händer om vi vill sortera stigande i stället för fallande? I nästa avsnitt visar vi hur enkelt det är.

## <a name="select-the-sort-order"></a>Välj sorteringsordning
Om vi tittar närmare på menyn **Fler alternativ** i föregående bild ser vi att **Sortera fallande** är fetstilt och föregås av ett gult fält.

![Sortera efter största till minsta](media/desktop-sort-by-column/sortbycolumn_4.png)

När du väljer **Sortera fallande** innebär det att det visuella objektet sorteras efter den markerade kolumnen från det största till det minsta värdet. Vill du ändra det? Inga problem, välj bara **Sortera stigande** så ändras sorteringsordningen för den valda kolumnen från det minsta till det största värdet.

Här är samma visuella objekt när ordningen för **DiscountAmount** har ändrats. Observera att Northwind Traders nu är den tillverkare som visas först medan Fabrikam, Inc. visas sist, alltså den motsatta sorteringsordningen.

![Sortera efter minsta till största](media/desktop-sort-by-column/sortbycolumn_5.png)

Du kan sortera efter valfri kolumn i det visuella objektet. Vi kan till exempel enkelt välja **SalesQuantity** som sorteringskolumn om vi vill visa tillverkarna med störst försäljning först, och bevara övriga kolumner i det visuella objektet baserat på deras relation till tillverkaren i fråga. Så här ser det visuella objektet ut med dessa inställningar:

![Sortera efter SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Sortera med knappen Sortera efter kolumn
Det finns ett annat sätt att sortera data, och det är med hjälp av knappen **Sortera efter kolumn** i menyfliksområdet **Modellering**.

![Knappen Sortera efter kolumn](media/desktop-sort-by-column/sortbycolumn_8.png)

Den här sorteringsmetoden kräver att du först väljer kolumnen (fältet) från fönstret **Fält** och sedan väljer **Modellering** > **Sortera efter kolumn** för att sortera ditt visuella objekt. Om du inte väljer någon kolumn är knappen **Sortera efter kolumn** inaktiv.

Låt oss titta på ett vanligt exempel. Du har data från varje månad under året och vill sortera dem i kronologisk ordning. Så här gör du:

1. Observera att knappen är inaktiv (nedtonad) när det visuella objektet har valts men ingen kolumn har valts i rutan **Fält** i **Sortera efter kolumn**.
   
   ![Knappen Sortera efter kolumn är inaktiv](media/desktop-sort-by-column/sortbycolumn_9.png)

2. När vi väljer den kolumn som vi vill sortera i rutan **fält** i **Sortera efter kolumn** blir knappen aktiv.
   
   ![Knappen Sortera efter kolumn är aktiv](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Nu när det visuella objektet är valt kan vi välja **MonthOfYear** i stället för standardinställningen **MonthName**, så sorteras det visuella objektet i den ordning vi villa ha: efter månaden på året.
   
   ![Menyn Sortera efter kolumn](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använd visning av detaljerad information mellan rapporter i Power BI Desktop](desktop-cross-report-drill-through.md)
* [Utsnitt i Power BI](visuals/power-bi-visualization-slicers.md)

