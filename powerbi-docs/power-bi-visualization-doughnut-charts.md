---
title: Ringdiagram i Power BI
description: Ringdiagram i Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/23/2017
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5d8be3d160e8ea37ba9814c7bd78c3ad5a751d3b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34294206"
---
# <a name="doughnut-charts-in-power-bi"></a>Ringdiagram i Power BI
Ett ringdiagram liknar ett cirkeldiagram så till vida att det visar förhållandet mellan delarna och helheten. Den enda skillnaden är att mitten är tom och har utrymme för en etikett eller ikon.

## <a name="create-a-doughnut-chart"></a>Skapa ett ringdiagram
De här anvisningarna använder exemplet på detaljhandelsanalys för att skapa ett cirkeldiagram som visar försäljning detta år efter kategori. Om du vill följa med kan du [hämta exemplet](sample-datasets.md) för Power BI-tjänsten (app.powerbi.com) eller Power BI Desktop.

1. Starta på en [tom rapportsida ](power-bi-report-add-page.md) och välj fältet **SalesStage** \> **Försäljningssteg**. Om du inte använder Power BI-tjänsten, se till att du öppnar rapporten i [Redigeringsvyn](service-interact-with-a-report-in-editing-view.md).

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
[Rapporter i Power BI](service-reports.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

