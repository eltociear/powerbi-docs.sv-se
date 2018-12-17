---
title: Ändra hur ett diagram sorteras i en Power BI-rapport
description: Ändra hur ett diagram sorteras i en Power BI-rapport
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: Conceptual
ms.date: 09/20/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: f4ca6633eb401e7df8041ea385284210c14995ad
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2018
ms.locfileid: "52979354"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändra hur ett diagram sorteras i en Power BI-rapport
I en Power BI-rapport kan du sortera de flesta visualiseringar alfabetiskt efter namnen på kategorierna i diagrammet eller efter de numeriska värdena i varje kategori. Det här diagrammet sorteras exempelvis på kategorin **butiksnamn**.

![](media/end-user-change-sort/pbi_chartsortcategory.png)

Det är enkelt att ändra sorteringen från en kategori (lagernamn) till ett värde (försäljning per kvadratmeter) i stället.

1. Välj ellipsen (...) och **Sortera efter försäljning per kvadratfot**.
2. Om det behövs väljer du ellipsen igen och sedan **Sortera fallande**.

   ![](media/end-user-change-sort/sort.gif)

   **Obs!** Det går inte att sortera alla visuella objekt.  Till exempel går inte följande visuella objekt att sortera: trädkarta, karta, koropletkarta, punktdiagram, mätare, kort, flerradskort, vattenfall.

## <a name="saving-changes-you-make-to-sort-order"></a>Spara dina ändringar av sorteringsordningen
De filter, utsnitt, sorteringar och andra datavisningsändringar som du gör sparas i Power BI-rapporterna. Ändringarna finns alltså kvar om du lämnar rapporten och kommer tillbaka senare.  Om du vill återställa ändringarna till inställningarna som rapportskaparen använde väljer du **Återställ till standard** från den översta menyraden. 

![beständig sortering](media/end-user-change-sort/power-bi-reset-to-default.png)

Om knappen **Återställ till standard** är nedtonad betyder det att rapportskaparen har inaktiverat möjligheten att spara ändringarna.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sortera med andra kriterier
Ibland kan du vilja sortera ditt visuella objekt på ett annat fält eller med andra kriterier.  Du kan t.ex. sortera efter månad (i stället för alfabetisk ordning), eller med heltal i stället för siffra (exempelvis 0, 1, 9, 20 och inte 0, 1, 20, 9).  

I vissa fall kan du sortera det visuella objektet som du vill, exempelvis på månad.  Om det inte går kan det bero på att datauppsättningen bakom rapporten behöver ändras. Be rapportskaparen att uppdatera datauppsättningen.

## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](end-user-visualizations.md).

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)