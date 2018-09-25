---
title: Ringdiagram i Power BI
description: Ringdiagram i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/23/2017
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3bf0aa516f50d363b53d2ed91b86d999e7855c30
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46545046"
---
# <a name="doughnut-charts-in-power-bi"></a>Ringdiagram i Power BI
Ett ringdiagram liknar ett cirkeldiagram så till vida att det visar förhållandet mellan delarna och helheten. Den enda skillnaden är att mitten är tom och har utrymme för en etikett eller ikon.

## <a name="create-a-doughnut-chart"></a>Skapa ett ringdiagram
De här anvisningarna använder exemplet på detaljhandelsanalys för att skapa ett cirkeldiagram som visar försäljning detta år efter kategori. Om du vill följa med kan du [hämta exemplet](../sample-datasets.md) för Power BI-tjänsten (app.powerbi.com) eller Power BI Desktop.

1. Starta på en [tom rapportsida ](../power-bi-report-add-page.md) och välj fältet **SalesStage** \> **Försäljningssteg**. Om du inte använder Power BI-tjänsten, se till att du öppnar rapporten i [Redigeringsvyn](../service-interact-with-a-report-in-editing-view.md).

2. I Fält-panelen, väljer du **Försäljning** \> **Senaste årets försäljning**.  
   
3. I fönstret visualiseringar, väljer du ikonen för cirkeldiagrammet ![cirkeldiagramsikonen]() för att konvertera ditt stapeldiagram till ett cirkeldiagram. Om **Fjolårets försäljning** inte är i **Värden**-området, drar du det dit.
     
   ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Välj **Objekt** \> **Kategori** för att lägga till den i området **Förklaring**. 
     
    ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Du kan också [justera storlek och färg för diagramtexten](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* Summan av ringdiagrammets värden måste uppgå till 100 %.
* För många kategorier gör det svårt att läsa och tolka översikten.
* Ringdiagram är bättre för att jämföra en särskild sektion med helheten än för att jämföra enskilda sektioner med varandra. 

## <a name="next-steps"></a>Nästa steg
[Rapporter i Power BI](../consumer/end-user-reports.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

[Power BI – grundläggande begrepp](../consumer/end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

