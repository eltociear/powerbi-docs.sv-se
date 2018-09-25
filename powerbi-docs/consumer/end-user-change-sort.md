---
title: Ändra hur ett diagram sorteras i en Power BI-rapport
description: Ändra hur ett diagram sorteras i en Power BI-rapport
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: dd8eeda3ba2bbc8da49a06199fa00dc3d731faaa
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565899"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändra hur ett diagram sorteras i en Power BI-rapport
I en Power BI-rapport kan du sortera de flesta visualiseringar alfabetiskt efter namnen på kategorierna i diagrammet eller efter de numeriska värdena i varje kategori. Det här diagrammet sorteras exempelvis på butiksnamn.

![](media/end-user-change-sort/pbi_chartsortcategory.png)

Det är enkelt att ändra sorteringen från en kategori (lagernamn) till ett värde (försäljning per kvadratmeter) i stället.

1. Välj ellipsen (...) och **Sortera efter försäljning per kvadratfot**.
2. Om det behövs väljer du sorteringsikonen ![](media/end-user-change-sort/sorticon.png) för att ändra till **Fallande**.

   ![](media/end-user-change-sort/sortby.gif)

   **Obs**! Det går inte att sortera alla visuella objekt.  Följande visuella objekt går inte att sortera: Trädkarta, Karta, Koropletkarta, Punkt, Mätare, Kort, Flerradskort, Vattenfall.

## <a name="saving-changes-you-make-to-sort-order"></a>Spara dina ändringar av sorteringsordningen
De filter, utsnitt, sorteringar och andra datavisningsändringar som du gör sparas i Power BI-rapporterna. Ändringarna finns alltså kvar om du lämnar rapporten och kommer tillbaka senare.  Om du vill återställa ändringarna till inställningarna som rapportförfattaren använde väljer du **Återställ till standard** från den översta menyraden. 

![beständig sortering](./media/end-user-change-sort/power-bi-reset-to-default.png)

Om knappen **Återställ till standard** är nedtonad betyder det att rapportförfattaren har inaktiverat möjligheten att spara ändringarna.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sortera med andra kriterier
Ibland kan du vilja sortera ditt visuella objekt på ett annat fält eller med andra kriterier.  Du kan t.ex. sortera efter månad (i stället för alfabetisk ordning), eller med heltal i stället för siffra (exempelvis 0, 1, 9, 20 och inte 0, 1, 20, 9).  

I vissa fall kan du sortera det visuella objektet som du vill, exempelvis på månad.  Om det inte går kan det bero på att datauppsättningen bakom rapporten behöver ändras. Här är några lösningar:

* I Power BI Desktop [använder du fliken Dataverktyg för modellering till att sortera efter en annan kolumn](../desktop-sort-by-column.md).
* I Excel, om du äger datauppsättningen, lägger du till en ny kolumn som slår ihop månadens namn och nummer. Uppdatera eller importera sedan datauppsättningen igen för att se den nya kolumnen i området Fält.
* I Excel kontrollerar du att dina numeriska kolumner är taggade som ”heltal” eller ”decimal” i stället för ”text”.

## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](../visuals/power-bi-report-visualizations.md).

[Power BI – Grundläggande begrepp](end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
