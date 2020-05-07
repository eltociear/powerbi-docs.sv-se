---
title: Använda banddiagram i Power BI
description: Skapa och använda banddiagram i Power BI Desktop
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1cee814b5013ece3a847aeb3660f1257c69be125
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73871147"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Använda banddiagram i Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Du kan använda banddiagram för att visualisera data och snabbt avgöra vilken datakategori som har högst rangordning (störst värde). Banddiagram är effektiva för att visa en rangordningsförändring med den högsta rangordningen (värdet) längst upp för varje tidsperiod. 

![banddiagram](media/desktop-ribbon-charts/ribbon-charts-01.png)

## <a name="prerequisites"></a>Förutsättningar

De här självstudierna använder sig av [PBIX-filen Exempel på detaljhandelsanalys](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Välj **Arkiv** > **Öppna** uppe till vänster på menyraden
   
2. Leta reda på kopian av **PBIX-filen Exempel för detaljhandelsanalys**

1. Öppna **PBIX-filen Exempel för detaljhandelsanalys** i rapportvyn ![Skärmbild av rapportvisningsikonen.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Välj ![Skärmbild av den gula fliken.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) för att lägga till en ny sida.

## <a name="create-a-ribbon-chart"></a>Skapa ett banddiagram

1. Skapa ett banddiagram genom att välja **Banddiagram** i fönstret **Visuella objekt**.

    ![visualiseringsmallar](media/desktop-ribbon-charts/power-bi-template.png)

    Banddiagram jämför en datakategori under en tidsperiod med band, vilket innebär att du kan se vilken rangordning en viss kategori har under loppet av diagrammets x-axel (vanligtvis tidslinjen).

2. Välj fält för **Axel**, **Förklaring** och **Värde**.  I det här exemplet har vi valt: **Lagra** > **OpenDate**, **Artikel** > **Kategori** och **Försäljning** > **Årets försäljning** > **Värde**.  

    ![markerade fält](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Eftersom datauppsättningen bara innehåller data för ett år har vi tagit bort fältet **År** och **Kvartal** från**Axel**.

3. Banddiagrammet visar rangordningen för varje månad. Observera hur rangordningen ändras över tid. Kategorin Home (Hem) flyttas till exempel från andra till femte från februari till mars.

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

Ange formateringsalternativ för dina dataetiketter. I det här exemplet har vi ställt in textfärgen på vit och visningsenheter på tusental.

![bandmall i visualiseringsfönstret](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Nästa steg

[Punktdiagram och bubbeldiagram i Power BI](power-bi-visualization-scatter.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
