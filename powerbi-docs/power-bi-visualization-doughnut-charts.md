---
title: "Ringdiagram i Power BI (självstudier)"
description: "Självstudier: Ringdiagram i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 2f428095eb57c5358770f1d6d8572316d2b84c37
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Ringdiagram i Power BI (självstudier)
Ett ringdiagram liknar ett cirkeldiagram så till vida att det visar förhållandet mellan delarna och helheten. Den enda skillnaden är att mitten är tom och har utrymme för en etikett eller ikon.

## <a name="create-a-doughnut-chart"></a>Skapa ett ringdiagram
Om du vill hänga på loggar du in i Power BI och väljer **Hämta data** \> **Exempel** \> **Exempel på detaljhandelsanalys**\>**Anslut**. 

1. Välj panelen **Totalt antal butiker** från instrumentpanelen för att öppna rapporten ”Exempel på detaljhandelsanalys”.
2. Välj **Redigera rapport** för att öppna rapporten i redigeringsvyn.
3. [Lägg till en ny rapportsida](power-bi-report-add-page.md).
4. Skapa ett ringdiagram som visar årets försäljning efter kategori.
   
   * Välj **Försäljning** \> **Last Year Sales (Förra årets försäljning)** på panelen **Fält**.
   * Konvertera till ett ringdiagram. Om Last Year Sales (Förra årets försäljning) inte befinner sig i området **Värden** dra du den dit.
     
       ![](media/power-bi-visualization-doughnut-charts/convertdonut.png)
   * Välj **Objekt** \> **Kategori** för att lägga till den i området **Förklaring**. 
     
       ![](media/power-bi-visualization-doughnut-charts/doughnuttutorial.png)

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

