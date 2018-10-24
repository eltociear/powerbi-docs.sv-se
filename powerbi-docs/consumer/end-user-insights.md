---
title: Skapa automatiskt datainsikter med Power BI
description: Lär dig mer om att få insikter om dina datauppsättningar och instrumentpanelers paneler.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/10/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: f68e962eacf04005d83ec0def10cf8e0e24f6e10
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112048"
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Skapa automatiskt datainsikter med Power BI
Varje visualiseringspanel på instrumentpanelen är en dörr in till datagranskning. När du väljer en panel öppnas en rapport där du kan filtrera och sortera och fördjupa dig i datauppsättningen bakom rapporten. Och när du kör insikter, gör Power BI datagranskningen åt dig.

Kör Quick Insights om du vill generera intressanta interaktiva visualiseringar utifrån dina data. Quick Insights kan köras på en specifik panel på instrumentpanelen och du kan till och med köra insikter på en insikt!

Funktionen insikter bygger på en växande [uppsättning avancerade analytiska algoritmer](end-user-insight-types.md) utvecklade tillsammans med Microsoft Research som vi kommer att fortsätta att använda så att flera användare kan söka efter insikter i sina data på nya och intuitiv sätt.

## <a name="run-insights-on-a-dashboard-tile"></a>Kör insikter på en panel på instrumentpanelen
När du kör insikter på en panel på instrumentpanelen, söker Power BI exakt de data som används för att skapa denna enskilda panel. 

1. [Öppna en instrumentpanel](end-user-dashboards.md).
2. Hovra över en panel. välj ellipserna (...) och välj **Visa insikter**. 

    ![läget ellips-menyn](./media/end-user-insights/power-bi-hover.png)


3. Panelen öppnas i [Fokusläge](end-user-focus.md) med detta insiktskort visat längst till höger.    
   
    ![Fokusläge](./media/end-user-insights/pbi-insights-tile.png)    
4. Fångar ett insiktskort ditt intresse? Välj insiktskortet för att gå djupare. Vald insikt visas till vänster och nya insiktskort som endast baseras på data i denna enda insikt visas till höger.    

 ## <a name="interact-with-the-insight-cards"></a>Interagera med Insight-korten
   * Filtrera visualiseringarna.  Välj pilen i det övre högra hörnet för att expandera filterfönstret om du vill visa filtren.

     ![insikter med utökad filtermeny](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * Kör insikter på själva insiktskortet. Detta kallas ofta **relaterade insikter**. I det övre högra hörnet väljer du ikonen med glödlampan ![ikonen Hämta insikter](./media/end-user-insights/power-bi-bulb-icon.png) eller **Hämta insikter**.
     
     ![menyrad med ikonen Hämta insikter](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     Insikten visas till vänster och nya kort som endast baseras på data i denna enda insikt visas till höger.
     
     ![insikt med insikter](./media/end-user-insights/power-bi-insights-on-insights-new.png)

Om du vill återgå till den ursprungliga arbetsytan för insikter väljer du **Avsluta Fokusläge** i det övre vänstra hörnet.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- **Visa insikter** fungerar inte med DirectQuery – det fungerar bara med data som överförs till Power BI.
- **Visa insikter** fungerar inte med alla typer av paneler på instrumentpanelen. Det är till exempel inte tillgänglig för anpassade visuella objekt.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Nästa steg
Lär dig mer om [tillgängliga typer av Quick Insights](end-user-insight-types.md)

