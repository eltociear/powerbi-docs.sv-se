---
title: Ändra hur ett diagram sorteras i en rapport
description: Ändra hur ett diagram sorteras i en Power BI-rapport
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/01/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fdd43320fec2b96aa708cb5bb1a21e269a117d2a
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830645"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändra hur ett diagram sorteras i en Power BI-rapport

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]


> [!IMPORTANT]
> **Den här artikeln är avsedd för Power BI-användare som inte har redigeringsbehörighet för rapporten eller datamängden. Du kan läsa mer om sortering i [Sortera efter kolumn i Power BI Desktop](../desktop-sort-by-column.md)**.

I Power BI-tjänsten kan du ändra utseendet för ett visuellt objekt genom att sortera det enligt olika datafält. Genom att ändra sorteringen för ett visuellt objekt kan du framhäva den information du vill förmedla.

Du kan inte sortera visuella objekt på en instrumentpanel, men i en Power BI-rapport kan du sortera de flesta visualiseringar 

Oavsett om du använder numeriska data (som försäljningssiffror) eller textdata (som namn på delstater) kan du sortera dina visuella objekt som det passar dig. Power BI ger stor flexibilitet gällande sortering och du kan använda olika snabbmenyer. 

## <a name="get-started"></a>Kom igång

Kom igång genom att välja valfritt visuellt objekt och sedan **Fler åtgärder**.  Det finns tre sorteringsalternativ: **Sortera fallande**, **Sortera stigande** och **Sortera efter**. 
    

![liggande diagram sorterat alfa till X-axeln](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Sortera alfabetiskt eller numeriskt

Du kan sortera visuella objekt alfabetiskt efter namnen på kategorierna i objektet, eller efter de numeriska värdena i varje kategori. Det här diagrammet är till exempel sorterat efter kategorin för **butiksnamn** längs X-axeln.

![liggande diagram sorterat alfa till X-axeln](media/end-user-change-sort/powerbi-sort-category.png)

Det är enkelt att ändra sorteringen från en kategori (lagernamn) till ett värde (försäljning per kvadratmeter) i stället. Välj **Fler åtgärder** (...) och sedan **Sortera efter**. Välj ett numeriskt värde som används i det visuella objektet.  I det här exemplet har vi valt **Sales Per Sq Ft**.

![Skärmbild som visar valet Sortera efter och sedan ett värde](media/end-user-change-sort/power-bi-sort-value.png)

Om det behövs kan du ändra sorteringsordningen mellan stigande och fallande.  Välj **Fler åtgärder** (...) igen och välj **Sortera fallande** eller **Sortera stigande**. Fältet som används för sortering visas i fetstil och med ett gult fält.

   ![video som visar att välja sortera efter och sedan stigande, fallande](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Det går inte att sortera alla visuella objekt. Till exempel går det inte att sortera följande visuella objekt: trädkarta, karta, koropletkarta, punktdiagram, mätare, kort och vattenfall.

## <a name="saving-changes-you-make-to-sort-order"></a>Spara dina ändringar av sorteringsordningen
De filter, utsnitt, sorteringar och andra datavisningsändringar som du gör sparas i Power BI-rapporterna. Om du navigerar bort från en rapport och sedan kommer tillbaka så har dina sorteringsändringar sparats.  Om du vill återställa ändringarna till rapportdesignerns inställningar väljer du **Återställ till standard** i det övre menyfältet. 

![beständig sortering](media/end-user-change-sort/power-bi-reset.png)

Om knappen **Återställ till standard** däremot är nedtonad innebär det att *rapportdesignern* har inaktiverat möjligheten att spara dina ändringar.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

### <a name="sorting-using-other-criteria"></a>Sortera med andra kriterier
Ibland kan du vilja sortera ditt visuella objekt efter ett annat fält (som inte ingår i det visuella objektet) eller något annat villkor.  Du kan till exempel sortera efter månad i sekvens (i stället för alfabetiskt), eller efter heltal snarare än siffror (så att det blir 0, 1, 9, 20 och inte 0, 1, 20, 9).  Det är bara den som designat rapporten som kan göra de här ändringarna åt dig. Du hittar kontaktuppgifter till *designern* genom att välja rapportnamnet i rubrikfältet.

![Listruta som visar kontaktuppgifter](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](end-user-visualizations.md).

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)
