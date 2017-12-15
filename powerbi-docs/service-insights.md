---
title: "Hämta Quick Insights i Power BI"
description: "Dokumentation för att köra och arbeta med Quick Insights med Power BI-tjänsten."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: et_MLSL2sA8
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/01/2017
ms.author: mihart
ms.openlocfilehash: 8b069f29737992817d20396007864cc8c005ca99
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="quick-insights-with-power-bi"></a>Quick Insights med Power BI
Har du en ny datauppsättning och vet inte riktigt var du ska börja?  Behöver du skapa en instrumentpanel snabbt?  Vill du snabbt leta efter insikter som du kan ha missat?

Kör Quick Insights om du vill generera intressanta interaktiva visualiseringar utifrån dina data. Quick Insights kan köras på en hel datauppsättning (Quick Insights) eller på en specifik instrumentpanel (Scoped Insights). Du kan även köra Quick Insights på en insikt!

> **Obs**! Quick Insights fungerar inte med DirectQuery – det fungerar bara med data som överförs till Power BI.
> 
> 

Funktionen Quick Insights bygger på en växande [uppsättning avancerade analytiska algoritmer](service-insight-types.md) utvecklade tillsammans med Microsoft Research som vi kommer att fortsätta att använda så att flera användare kan söka efter insikter i sina data på nya och intuitiv sätt.

## <a name="run-quick-insights-on-a-dataset"></a>Kör Quick Insights på en datauppsättning
Titta på när Amanda kör Quick Insights på en datauppsättning, öppnar en insikt i Fokusläge, fäster en av dessa snabba insikter som en panel på sin instrumentpanel och sedan får Quick Insights om ett visuellt objekt.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Nu är din tur. Utforska Quick Insights med [exemplet för analys av leverantörskvalitet](sample-supplier-quality.md).

1. Från fliken **Datauppsättningar**, välj ellipserna (...) och välj **Hämta insikter**.
   
    ![](media/service-insights/power-bi-ellipses.png)
   
    ![](media/service-insights/power-bi-tab.png)
2. Power BI använder [olika algoritmer](service-insight-types.md) för att söka efter trender i datauppsättningen.
   
    ![](media/service-insights/pbi_autoinsightssearching.png)
3. Dina insikter är klara inom några sekunder.  Välj **Visa insikter** för att visa visualiseringar.
   
    ![](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **Obs**! Vissa datauppsättningar kan inte generera Quick Insights eftersom data inte är statistiskt signifikanta.  Läs mer i [Optimera dina data för Quick Insights](service-insights-optimize.md).
   > 
   > 
4. Visualiseringar visas i en särskild arbetsyta för **Quick Insights** med upp till 32 separata insiktskort. Varje kort har ett diagram eller graf samt en kort beskrivning.
   
    ![](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-quick-insight-cards"></a>Interagera med Quick Insight-korten
  ![](media/service-insights/pbi_hover.png)

1. Hovra över ett kort och välj stiftikonen för att lägga till visualiseringen på en instrumentpanel.
2. Hovra över ett kort och välj ikonen för Fokusläge för att visa kortet i helskärmsläge.
   
    ![](media/service-insights/power-bi-insight-focus.png)
3. I Fokusläge kan du:
   
   * [filtrera](service-interact-with-a-report-in-reading-view.md) visualiseringarna.  Välj pilen i det övre högra hörnet för att expandera filterfönstret om du vill visa filtren.
     
        ![](media/service-insights/power-bi-insights-filter-new.png)
   * Fäst insiktskortet på en instrumentpanel genom att välja stiftikonen ![](media/service-insights/power-bi-pin-icon.png) eller **Fäst visualiseringar**.
   * Kör Quick Insights på själva kortet. Detta kallas **Scoped Quick Insights**. I det övre högra hörnet väljer du ikonen med en glödlampa ![](media/service-insights/power-bi-bulb-icon.png) eller **Hämta insikter**.
     
       ![](media/service-insights/pbi-autoinsights-tile.png)
     
     Quick Insight visas till vänster och nya kort som endast baseras på data i denna enda snabbinsikt visas till höger.
     
       ![](media/service-insights/power-bi-insights-on-insights-new.png)
4. Om du vill återgå till den ursprungliga arbetsytan för Quick Insights väljer du **Avsluta Fokusläge** i det övre vänstra hörnet.

## <a name="run-quick-insights-on-a-dashboard-tile"></a>Kör Quick Insights på en panel på instrumentpanelen
Begränsa sökningen till de data som används för att skapa en enda panel på instrumentpanelen i stället för att söka efter insikter mot en hel datauppsättning. Detta kallas **Scoped Quick Insights**.

1. Öppna en instrumentpanel.
2. Välj en panel och [öppna panelen i Fokusläge](service-focus-mode.md).
3. I det övre högra hörnet väljer du **Hämta insikter**.
   
    ![](media/service-insights/pbi-autoinsights-tile.png)
4. Power BI visar insiktskorten längs höger sida av panelen.
   
    ![](media/service-insights/pbi-insights-tile.png)
5. Fångar ett insiktskort ditt intresse? Välj insiktskortet för att gå djupare. Vald Quick Insight visas till vänster och nya insiktskort som endast baseras på data i denna enda Quick Insight visas till höger.
6. Fortsätt utforska dina data och när du har hittat en intressant Quick Insight fäster du dess visuella objekt på instrumentpanelen genom att välja **Fäst visualisering** från det övre högra hörnet. Du kan också skicka feedback så att datauppsättningens ägare vet om en viss snabbinsikt var till hjälp eller inte.
   
    ![](media/service-insights/useful.png)

## <a name="next-steps"></a>Nästa steg
Om du äger en datauppsättning, [optimera den för Quick Insights](service-insights-optimize.md)

Lär dig mer om [tillgängliga typer av Quick Insights](service-insight-types.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

