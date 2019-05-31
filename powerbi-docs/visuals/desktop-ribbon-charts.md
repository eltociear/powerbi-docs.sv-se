---
title: Använda banddiagram i Power BI
description: Skapa och använda banddiagram i Power BI-tjänsten och Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 08a2de32b092ba24b66ddd9f173be1eaea8819ab
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61394540"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Använda banddiagram i Power BI
Du kan använda banddiagram för att visualisera data och snabbt avgöra vilken datakategori som har högst rangordning (störst värde). Banddiagram är effektiva för att visa en rangordningsförändring med den högsta rangordningen (värdet) längst upp för varje tidsperiod. 

![banddiagram](media/desktop-ribbon-charts/ribbon-charts_01.png)

## <a name="create-a-ribbon-chart"></a>Skapa ett banddiagram
Om du vill följa med, kan du öppna [exempelrapporten över detaljhandelsanalys](../sample-retail-analysis.md). 

1. Skapa ett banddiagram genom att välja **Banddiagram** i fönstret **Visuella objekt**.

    ![visualiseringsmallar](media/desktop-ribbon-charts/ribbon-charts_02.png)

    Banddiagram jämför en datakategori under en tidsperiod med band, vilket innebär att du kan se vilken rangordning en viss kategori har under loppet av diagrammets x-axel (vanligtvis tidslinjen).

2. Välj fält för **Axel**, **Förklaring** och **Värde**.  I det här exemplet har vi valt: **Date** (Datum), **Category** (Kategori) och **This year sales** (Det här årets försäljning).  

    ![markerade fält](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Eftersom datauppsättningen bara innehåller data för ett år har vi tagit bort fältet **Year** (År) från **Axel**. 

3. Banddiagrammet visar rangordningen för varannan månad. Observera hur rangordningen ändras över tid.  Till exempel flyttar kategorin Home (Hem) från tredje till fjärde och tillbaka till tredje igen. Kategorin Juniors (Juniorsäljare) från tredje till femte i July (juli). 

    ![banddiagram](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Formatera ett banddiagram
När du skapar ett diagram i menyfliksområdet har du formateringsalternativ som är tillgängliga i området **Format** i fönstret **Visuella objekt**. Formateringsalternativen för banddiagram liknar dem för ett stående stapeldiagram med extra formateringsalternativ som är specifika för band.

![bandmall i visualiseringsfönstret](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Med formateringsalternativen för banddiagram kan du göra justeringar.

* **Med avstånd** kan du styra hur mycket utrymme som ska visas mellan banden. Numret är i procent av kolumnens maximala höjd.
* **Med matcha seriefärg** kan du matcha färg i menyfliksområdet med seriefärg. Banden är grå när detta är **avaktiverat**.
* **Genomskinlighet** anger hur genomskinligt menyfliksområdet är. Standardvärdet är 30.
* **Kantlinje** kan du placera en mörk kantlinje högst upp och längst ned på banden. Kantlinjer är inaktiverade som standard.

Eftersom banddiagrammet inte har några y-axeletiketter kan du vilja lägga till dataetiketter. Välj **Dataetiketter** i formateringsfönstret. 

![formateringsalternativ för dataetiketter](media/desktop-ribbon-charts/power-bi-labels.png)

Ange formateringsalternativ för dina dataetiketter.  I det här exemplet har vi ställt in textfärgen på vit, decimaler på noll och visningsenheter på tusental. 

![bandmall i visualiseringsfönstret](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Nästa steg

[Punktdiagram och bubbeldiagram i Power BI](power-bi-visualization-scatter.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)