---
title: Översikt över rapportvisualiseringar i Power BI-tjänsten och Desktop
description: Översikt över rapportvisualiseringar (visuella objekt) i Microsoft Power BI.
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: SYk_gWrtKvM
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/28/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: d470a262bd8a5e6590746fb07889b1230f5cfc25
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375648"
---
# <a name="visualizations-in-power-bi-reports"></a>Visualiseringar i Power BI-rapporter

Visualiseringar (även kända som visuella objekt) visar insikter som har upptäckts i data. En Power BI-rapport kan ha en enda sida med ett visuellt objekt eller en mängd sidor med visuella objekt. I Power BI-tjänsten, kan visuella objekt [fästas från rapporter till instrumentpaneler](../service-dashboard-pin-tile-from-report.md).

Det är viktigt att skilja mellan rapport *designers* och rapportera *konsumenter* om du är den person som skapar eller ändrar rapporten så är du en designer.  Designers har redigeringsbehörighet till rapporten och dess underliggande datauppsättning. I Power BI Desktop, innebär det att du kan öppna datauppsättningen i Datavyn och skapa visuella objekt i Rapportvyn. I Power BI-tjänsten innebär detta att du kan öppna datauppsättningen eller rapporten i rapportredigeraren i [redigeringsvyn](../consumer/end-user-reading-view.md). Om en rapport eller instrumentpanel har [delats med dig](../consumer/end-user-shared-with-me.md) är du en rapport**konsument**. Du kommer att kunna visa och interagera med rapporten och dess visuella objekt, men du kan inte spara större ändringar.

Det finns många olika typer av visuella objekt tillgängliga direkt från Power BI-fönstret Visualiseringar.

![](media/power-bi-report-visualizations/power-bi-templates.png)

Om du vill ha ännu fler alternativ kan du besöka [Microsoft AppSource community-webbplatsen](https://appsource.microsoft.com) och söka efter och [ladda ned](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) [anpassade visuella objekt](../developer/custom-visual-develop-tutorial.md) från Microsoft och communityn.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SYk_gWrtKvM?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


  Om du inte har arbetat med Power BI tidigare eller behöver en uppfräschning, kan du använda länkarna nedan för att läsa om grunderna i Power BI-visualiseringar.  Alternativt, kan du använda vår innehållsförteckning (till vänster om den här artikeln) för att hitta ännu mer användbar information.

## <a name="add-a-visualization-in-power-bi"></a>Lägg till en visualisering i Power BI

[Skapa visualiseringar](power-bi-report-add-visualizations-i.md) på sidorna i dina rapporter. Bläddra igenom [listan över tillgängliga visualiseringar och tillgängliga visualiseringssjälvstudier.](power-bi-visualization-types-for-reports-and-q-and-a.md) 

## <a name="upload-a-custom-visualization-and-use-it-in-power-bi"></a>Ladda upp en anpassad visualisering och använd den i Power BI

Lägg till en anpassad visualisering som du har skapat själv eller som du hittat på [Microsoft AppSource community-webbplatsen](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Känner du dig kreativ? Ta en närmare titt på vår källkod och använd våra [utvecklarverktyg](../developer/custom-visual-develop-tutorial.md) om du vill skapa nya visualiseringstyper och [dela dem med communityn](../developer/office-store.md). Om du vill veta mer om hur man utvecklar anpassade visuella objekt kan du läsa [Utveckla ett anpassat visuellt objekt i Power BI](../developer/custom-visual-develop-tutorial.md).

## <a name="change-the-visualization-type"></a>Ändra visualiseringstyp

Försök att [ändra visualiseringstypen](power-bi-report-change-visualization-type.md) för att se vilken som fungerar bäst med dina data.

## <a name="pin-the-visualization"></a>Fäst visualiseringen

När du har fått till visualiseringen som du vill ha den i Power BI-tjänsten, kan du [fästa den på en instrumentpanel](../service-dashboard-pin-tile-from-report.md) som en panel. Om du ändrar den visualisering som används i rapporten efter att du fäster den, ändras inte panelen på instrumentpanelen. Om den var ett linjediagram förblir den ett linjediagram, även om du har ändrat till ett ringdiagram i rapporten.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
- Beroende på datakällan och antalet fält (mått eller kolumner), ett visuellt objekt kan läsa in långsamt.  Vi rekommenderar att begränsa visuell information till totalt 10-20-fält, både för läsbarhet och prestandaskäl. 

- Den övre gränsen för visuella objekt är 100 fält (mått eller kolumner). Om det inte går att läsa in ditt visuella objekt, kan du minska antalet fält.   

## <a name="next-steps"></a>Nästa steg

* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Anpassade visuella objekt](../power-bi-custom-visuals.md)