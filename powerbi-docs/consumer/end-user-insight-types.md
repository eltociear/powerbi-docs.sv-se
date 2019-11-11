---
title: Typer av insikter som stöds av Power BI
description: Quick Insights och Visa insikter med Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 75462c2414854d0848254a36b89bcdd1de365ec5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863493"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Typer av insikter som stöds av Power BI

Power BI-tjänst kan automatiskt söka efter insikter i dina instrumentpaneler eller rapporter.

## <a name="how-does-insights-work"></a>Hur fungerar insikter?
Power BI söker snabbt igenom delmängder av din datauppsättning. Under sökningen används en uppsättning sofistikerade algoritmer för att identifiera potentiellt intressanta insikter. Power BI söker igenom så mycket av en datauppsättning som möjligt inom tilldelad tid.

Du kan köra insikter mot en datauppsättning eller en panel på en instrumentpanel.   

## <a name="what-types-of-insights-can-we-find"></a>Vilka typer av insikter kan vi hitta?
Det här är några av de algoritmer som vi använder:

## <a name="category-outliers-topbottom"></a>Kategoriavvikare (upp/ned)
Visar fall, för ett mått i modellen, där en eller två medlemmar i en dimension har mycket större värden än andra medlemmar i dimensionen.  

![Exempel på kategoriavvikare](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

## <a name="change-points-in-a-time-series"></a>Ändra punkterna i en tidsserie
Visar om det finns betydande förändringar i trender i en tidsserie med data.

![Exempel på ändrade punkter i en tidsserie](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

## <a name="correlation"></a>Korrelation
Identifierar fall där flera mått visar ett förhållande mellan varandra när de ritas mot en dimension i datauppsättningen.

![Exempel på korrelation](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

## <a name="low-variance"></a>Låg varians
Identifierar fall där datapunkter ligger nära medelvärdet.

![Exempel på låg varians](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Majoritet (viktiga faktorer)
Söker efter fall där en majoritet av ett totalt värde kan bero på en enda faktor vid uppdelat efter en annan dimension.  

![Exempel på viktiga faktorer](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

## <a name="overall-trends-in-time-series"></a>Övergripande trender i tidsserier
Identifierar trender uppåt eller nedåt i tidsseriedata.

![Exempel på övergripande trender i tidsserier](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

## <a name="seasonality-in-time-series"></a>Säsongsberoende i tidsserier
Söker efter periodiska mönster i tidsseriedata, till exempel säsongsvärdet för varje vecka, månad eller år.

![Exempel på säsongsvärde](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

## <a name="steady-share"></a>Stadig resurs
Visar fall där det finns en överordnad-underordnad korrelation mellan andelen av det underordnade värdet i förhållande till det övergripande värdet för det överordnade över en kontinuerlig variabel.

![Exempel på stadig resurs](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

## <a name="time-series-outliers"></a>Extremvärden för tidsserier
För data över en tidsserie, identifierar när det finns specifika datum- och tidsvärden som skiljer sig från andra datum-/tidsvärden.

![Exempel på extremvärden för tidsserier](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>Nästa steg
[Power BI-insikter](end-user-insights.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

