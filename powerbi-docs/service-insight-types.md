---
title: "Typer av Quick Insights som stöds av Power BI"
description: Quick Insights med Power BI.
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
ms.date: 09/03/2017
ms.author: mihart
ms.openlocfilehash: 13f5614cf121b17d8ae4dff9653f5789372f7f49
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="types-of-quick-insights-supported-by-power-bi"></a>Typer av Quick Insights som stöds av Power BI
## <a name="how-does-quick-insights-work"></a>Hur fungerar Quick Insights?
Power BI söker snabbt olika delmängder av din datauppsättning samtidigt som en uppsättning avancerade algoritmer används för att identifiera potentiellt intressanta insikter. Power BI söker igenom så mycket av en datauppsättning som möjligt inom tilldelad tid.

Du kan köra Quick Insights mot en datauppsättning eller en panel (relaterade insikter).   

## <a name="what-types-of-quick-insights-can-we-find"></a>Vilka typer av Quick Insights kan vi hitta?
Det här är några av de algoritmer som vi använder:

## <a name="category-outliers-topbottom"></a>Kategoriavvikare (upp/ned)
Visar fall, för ett mått i modellen, där en eller två medlemmar i en dimension har mycket större värden än andra medlemmar i dimensionen.  

![](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Ändra punkterna i en tidsserie
Visar om det finns betydande förändringar i trender i en tidsserie med data.

![](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Korrelation
Identifierar fall där flera mått visar ett förhållande mellan varandra när de ritas mot en dimension i datauppsättningen.

![](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Låg varians
Identifierar fall där datapunkter inte är långt från medelvärdet.

![](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Majoritet (viktiga faktorer)
Söker efter fall där en majoritet av ett totalt värde kan bero på en enda faktor vid uppdelat efter en annan dimension.  

![](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Övergripande trender i tidsserier
Identifierar trender uppåt eller nedåt i tidsseriedata.

![](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Säsongsberoende i tidsserier
Söker efter periodiska mönster i tidsseriedata, till exempel säsongsvärdet för varje vecka, månad eller år.

![](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Stadig resurs
Visar fall där det finns en överordnad-underordnad korrelation mellan andelen av det underordnade värdet i förhållande till det övergripande värdet för det överordnade över en kontinuerlig variabel.

![](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Extremvärden för tidsserier
För data över en tidsserie, identifierar när det finns specifika datum- och tidsvärden som skiljer sig från andra datum-/tidsvärden.

![](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Nästa steg
[Power BI Quick Insights](service-insights.md)

Om du äger en datauppsättning, [optimera den för Quick Insights](service-insights-optimize.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

