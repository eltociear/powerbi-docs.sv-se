---
title: "Ändra hur ett diagram sorteras i en Power BI-rapport"
description: "Ändra hur ett diagram sorteras i en Power BI-rapport"
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
ms.date: 09/08/2017
ms.author: mihart
ms.openlocfilehash: 37161fab1e19e6ce00eb0f02c96b6e5cbdd60f18
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändra hur ett diagram sorteras i en Power BI-rapport
I Power BI kan du sortera diagram alfabetiskt efter namnen på kategorierna, eller efter de numeriska värdena i varje kategori. Det här diagrammet sorteras exempelvis på butiksnamn.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

Det är enkelt att sortera från högsta till lägsta försäljning per kvadratfot i stället.

1. Välj ellipsen (...) och **Sortera efter försäljning per kvadratfot**.
2. Om det behövs väljer du sorteringsikonen ![](media/power-bi-report-change-sort/sorticon.png) för att ändra till **Fallande**.
   
   ![](media/power-bi-report-change-sort/sortby.gif)
   
   **Obs**! Det går inte att sortera alla visuella objekt.  Följande visuella objekt går inte att sortera: Trädkarta, Karta, Koropletkarta, Punkt, Mätare, Kort, Flerradskort, Vattenfall.

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

