---
title: Introduktion till paneler på instrumentpanelen för Power BI-designers
description: I den här artikeln beskrivs instrumentpaneler i Power BI, vilket omfattar paneler som skapas från SSRS-rapporter (SQL Server Reporting Services).
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: efa5acbe70ea4541c2f9819d5260cb662ca0adac
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81637886"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introduktion till paneler på instrumentpanelen för Power BI-designers

En panel är en ögonblicksbild av dina data, fäst på instrumentpanelen. En panel kan skapas från en rapport, datamängd, instrumentpanel, Frågor och svar-rutan, Excel samt SQL Server Reporting Services-rapporter (SSRS) med mera.  Den här skärmbilden visar många olika paneler fästa på en instrumentpanel.

![Power BI-instrumentpanel](media/service-dashboard-tiles/power-bi-dashboard.png)

Instrumentpaneler och paneler på instrumentpanelen är en funktion i Power BI-tjänsten, inte Power BI Desktop. Du kan inte skapa instrumentpaneler på mobila enheter, men du kan [visa och dela](mobile-apps-view-dashboard.md) dem.

Utöver att fästa paneler kan du även skapa fristående paneler direkt på instrumentpanelen med hjälp av kontrollen [Lägg till panel](service-dashboard-add-widget.md). Fristående paneler innehåller: textrutor, bilder, videor, strömmande data och webbinnehåll.

Behöver du hjälp med att förstå de olika byggstenarna som utgör Power BI? Se [Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md).

> [!NOTE]
> Om den ursprungliga visualiseringen som användes för att skapa panelen ändras, ändras inte panelen.  Om du till exempel har fäst ett linjediagram från en rapport och sedan ändrar linjediagrammet till ett stapeldiagram, fortsätter panelen på instrumentpanelen att visa ett linjediagram. Data uppdateras, men visualiseringstypen gör det inte.
> 
> 

## <a name="pin-a-tile"></a>Fästa en panel
Det finns många olika sätt att lägga till (fästa) en panel till en instrumentpanel. Du kan fästa paneler från:

* [Power BI frågor och svar](service-dashboard-pin-tile-from-q-and-a.md)
* [En rapport](service-dashboard-pin-tile-from-report.md)
* [En annan instrumentpanel](service-pin-tile-to-another-dashboard.md)
* [Excel-arbetsbok på OneDrive för företag](service-dashboard-pin-tile-from-excel.md)
* [Quick Insights](service-insights.md)
* [En lokal sidnumrerad rapport i Power BI-rapportserver eller SQL Server Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Du skapar fristående paneler för bilder, textrutor, videor, strömmande data och webbinnehåll direkt på instrumentpanelen med hjälp av kontrollen [Lägg till panel](service-dashboard-add-widget.md).

  ![Ikonen Lägg till panel](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>Interagera med paneler på en instrumentpanel
När du har lagt till en panel på en instrumentpanel kan du flytta och ändra storlek på den eller ändra dess utseende och beteende.

### <a name="move-and-resize-a-tile"></a>Flytta och ändra storlek på en panel
Hämta en panel och [flytta runt den på instrumentpanelen](service-dashboard-edit-tile.md). Hovra och välj handtaget ![Panelhandtag](media/service-dashboard-tiles/resize-handle.jpg) för att ändra storlek på panelen.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Hovra över en panel för att ändra utseendet och beteendet
1. Hovra över panelen för att visa ellipsen.
   
    ![Panelellips](media/service-dashboard-tiles/ellipses_new.png)
2. Välj ellipsen för att öppna menyn för panelåtgärder.
   
    ![Ellipsikon](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Här kan göra du följande:
   
     * [Lägga till kommentarer på instrumentpanelen](consumer/end-user-comment.md).
     * [Öppna den rapport som användes för att skapa den här panelen](service-reports.md).  
     * [Visa i fokusläge](service-focus-mode.md).   
     * [Exportera de data som används i panelen](visuals/power-bi-visualization-export-data.md).
     * [Redigera rubriken och lägga till en hyperlänk](service-dashboard-edit-tile.md). 
     * [Köra insikter](service-insights.md). 
     * [Fästa panelen till en annan instrumentpanel](service-pin-tile-to-another-dashboard.md).
     * [Ta bort panelen](service-dashboard-edit-tile.md).

3. Om du vill stänga åtgärdsmenyn väljer du ett tomt område på instrumentpanelen.

### <a name="select-a-tile"></a>Välja en panel
När du väljer en panel beror händelseförloppet på hur du skapade panelen. I annat fall kommer du, om du väljer panelen, till rapporten, arbetsboken i Excel Online, den lokala Reporting Services-rapporten eller frågor och svar som användes för att skapa panelen. Eller om den har en [anpassad länk](service-dashboard-edit-tile.md) kommer du till den länken om du väljer panelen.

> [!NOTE]
> Ett undantag för detta är videopaneler som skapats direkt på instrumentpanelen med hjälp av **Lägg till panel**. Om en videopanel (som skapades på det här sättet) väljs så spelas videon upp direkt på instrumentpanelen.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

* Om den rapport som användes för att skapa visualiseringen inte sparades kommer inget att hända om panelen väljs.
* Om panelen skapades från en arbetsbok i Excel Online behöver du minst läsbehörighet för arbetsboken. I annat fall öppnas inte arbetsboken i Excel Online när du väljer panelen.
* Anta att du skapar en panel direkt på instrumentpanelen med hjälp av **Lägg till panel** och anger en anpassad hyperlänk för den. I så fall öppnas den webbadressen när du väljer rubriken, underrubriken eller panelen. I annat fall händer som standard ingenting om du väljer en panel som skapats direkt på instrumentpanelen för en bild, webbkod eller textruta.
* Paneler kan skapas från lokala sidnumrerade rapporter i Power BI-rapportserver eller SQL Server Reporting Services. Om du väljer panelen och inte har behörighet att komma åt den lokala rapporten kommer du till en sida där det står att du inte har åtkomst (rsAccessDenied).
* Anta att du väljer en panel som skapats från en lokal sidnumrerad rapport i Power BI-rapportserver eller SQL Server Reporting Services. Om du inte har åtkomst till det nätverk där rapportservern finns kommer val av en panel som skapats från den sidnumrerade rapporten att dirigera dig till en sida som anger att den inte kan hitta servern (HTTP 404). Enheten måste ha nätverksåtkomst till rapportservern för att visa rapporten.
* Om den ursprungliga visualiseringen som användes för att skapa panelen ändras så ändras inte panelen. Om du till exempel fäster ett linjediagram från en rapport och sedan ändrar linjediagrammet till ett stapeldiagram, fortsätter panelen på instrumentpanelen att visa ett linjediagram. Data uppdateras, men visualiseringstypen gör det inte.

## <a name="next-steps"></a>Nästa steg
- [Skapa ett kort (stor sifferpanel) för din instrumentpanel](power-bi-visualization-card.md)
- [Introduktion till instrumentpaneler för Power BI-designers](service-dashboards.md)  
- [Datauppdatering i Power BI](refresh-data.md)
- [Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)
- [Integrera Power BI-paneler i Office-dokument](https://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)
- [Fästa Reporting Services-objekt till Power BI-instrumentpaneler](https://msdn.microsoft.com/library/mt604784.aspx)

Fler frågor? [Testa Power BI Community](https://community.powerbi.com/).

