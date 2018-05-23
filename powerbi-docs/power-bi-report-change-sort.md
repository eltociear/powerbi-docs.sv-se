---
title: Ändra hur ett diagram sorteras i en Power BI-rapport
description: Ändra hur ett diagram sorteras i en Power BI-rapport
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6b70a9ef7774d1ba49bc5bf825a5c1cde47197f2
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändra hur ett diagram sorteras i en Power BI-rapport
I en Power BI-rapport kan du sortera de flesta visualiseringar alfabetiskt efter namnen på kategorierna i diagrammet eller efter de numeriska värdena i varje kategori. Det här diagrammet sorteras exempelvis på butiksnamn.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

Det är enkelt att ändra sorteringen från en kategori (lagernamn) till ett värde (försäljning per kvadratmeter) i stället.

1. Välj ellipsen (...) och **Sortera efter försäljning per kvadratfot**.
2. Om det behövs väljer du sorteringsikonen ![](media/power-bi-report-change-sort/sorticon.png) för att ändra till **Fallande**.

   ![](media/power-bi-report-change-sort/sortby.gif)

   **Obs**! Det går inte att sortera alla visuella objekt.  Följande visuella objekt går inte att sortera: Trädkarta, Karta, Koropletkarta, Punkt, Mätare, Kort, Flerradskort, Vattenfall.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sortera med andra kriterier
Ibland kan du vilja sortera ditt visuella objekt på ett annat fält eller med andra kriterier.  Du kan t.ex. sortera efter månad (i stället för alfabetisk ordning), eller med heltal i stället för siffra (exempelvis 0, 1, 9, 20 och inte 0, 1, 20, 9).  

I vissa fall kan du sortera det visuella objektet som du vill, exempelvis på månad.  Om det inte går kan det bero på att datauppsättningen bakom rapporten behöver ändras. Här är några lösningar:

* I Power BI Desktop [använder du fliken Dataverktyg för modellering till att sortera efter en annan kolumn](desktop-sort-by-column.md).
* I Excel, om du äger datauppsättningen, lägger du till en ny kolumn som slår ihop månadens namn och nummer. Uppdatera eller importera sedan datauppsättningen igen för att se den nya kolumnen i området Fält.
* I Excel kontrollerar du att dina numeriska kolumner är taggade som ”heltal” eller ”decimal” i stället för ”text”.

## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md).

[Power BI – Grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
