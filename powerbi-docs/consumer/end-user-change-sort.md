---
title: Ändra hur ett diagram sorteras i en rapport
description: Ändra hur ett diagram sorteras i en Power BI-rapport
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302709"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändra hur ett diagram sorteras i en Power BI-rapport
I en Power BI-rapport kan du sortera de flesta visualiseringar alfabetiskt efter namnen på kategorierna i diagrammet eller efter de numeriska värdena i varje kategori. Det här diagrammet sorteras exempelvis på kategorin **butiksnamn**.

![liggande diagram sorterat alfa till X-axeln](media/end-user-change-sort/pbi_chartsortcategory.png)

Det är enkelt att ändra sorteringen från en kategori (lagernamn) till ett värde (försäljning per kvadratmeter) i stället.

1. Välj ellipsen (...) och **Sortera efter försäljning per kvadratfot**.
2. Om det behövs väljer du ellipsen igen och sedan **Sortera fallande**.

   ![video som visar att välja sortera efter och sedan stigande, fallande](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Det går inte att sortera alla visuella objekt. Till exempel går det inte att sortera följande visuella objekt: trädkarta, karta, koropletkarta, punktdiagram, mätare, kort och vattenfall.

## <a name="saving-changes-you-make-to-sort-order"></a>Spara dina ändringar av sorteringsordningen
De filter, utsnitt, sorteringar och andra datavisningsändringar som du gör sparas i Power BI-rapporterna. Ändringarna finns alltså kvar om du lämnar rapporten och kommer tillbaka senare.  Om du vill återställa ändringarna till rapportdesignerns inställningar väljer du **Återställ till standard** i det övre menyfältet. 

![beständig sortering](media/end-user-change-sort/power-bi-reset.png)

Om knappen **Återställ till standard** är nedtonad betyder det att rapportdesignern har inaktiverat möjligheten att spara ändringarna.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sortera med andra kriterier
Ibland kan du vilja sortera ditt visuella objekt på ett annat fält eller med andra kriterier.  Du kan t.ex. sortera efter månad (i stället för alfabetisk ordning), eller med heltal i stället för siffra (exempelvis 0, 1, 9, 20 och inte 0, 1, 20, 9).  

I vissa fall kan du sortera det visuella objektet som du vill, exempelvis på månad.  Om det inte går kan det bero på att datauppsättningen bakom rapporten behöver ändras. Be rapportdesignern att uppdatera datauppsättningen.

## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](end-user-visualizations.md).

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)
