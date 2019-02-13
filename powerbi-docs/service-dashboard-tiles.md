---
title: Introduktion till paneler på instrumentpanelen för Power BI-designers
description: Allt om paneler på instrumentpanelen i Power BI. Detta inkluderar paneler som skapas från SQL Server Reporting Services-rapporter (SSRS).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: c8b5728c951bc1a25e71da8885997814c5485cd4
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56215997"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introduktion till paneler på instrumentpanelen för Power BI-designers

En panel är en ögonblicksbild av dina data, fäst på instrumentpanelen. En panel kan skapas från en rapport, datamängd, instrumentpanel, Frågor och svar-rutan, Excel samt SQL Server Reporting Services-rapporter (SSRS) med mera.  Den här skärmbilden visar många olika paneler fästa på en instrumentpanel.

![Power BI-instrumentpanel](media/service-dashboard-tiles/power-bi-dashboard.png)

Instrumentpaneler och paneler på instrumentpanelen är en funktion i Power BI-tjänsten, inte Power BI Desktop. Du kan inte skapa instrumentpaneler på mobila enheter, men du kan [visa och dela](mobile-apps-view-dashboard.md) dem.

Förutom att fästa kan du skapa fristående paneler direkt på en instrumentpanel med hjälp av [Lägg till panel](service-dashboard-add-widget.md). Fristående paneler innehåller: textrutor, bilder, videor, strömmande data och webbinnehåll.

Behöver du hjälp att förstå de olika byggstenarna i Power BI?  Mer information finns i [Power BI – grundläggande begrepp](service-basic-concepts.md).

> [!NOTE]
> Om den ursprungliga visualiseringen som användes för att skapa panelen ändras, ändras inte panelen.  Om du till exempel har fäst ett linjediagram från en rapport och sedan ändrar linjediagrammet till ett stapeldiagram, fortsätter panelen på instrumentpanelen att visa ett linjediagram. Data uppdateras, men visualiseringstypen gör det inte.
> 
> 

## <a name="pin-a-tile-from"></a>Fästa en panel från ...
Det finns många olika sätt att lägga till (fästa) en panel till en instrumentpanel. Paneler kan fästas från:

* [Power BI frågor och svar](service-dashboard-pin-tile-from-q-and-a.md)
* [en rapport](service-dashboard-pin-tile-from-report.md)
* [en annan instrumentpanel](service-pin-tile-to-another-dashboard.md)
* [Excel-arbetsbok på OneDrive för företag](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher för Excel](publisher-for-excel.md)
* [Quick Insights](service-insights.md)
* [Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Fristående paneler för bilder, textrutor, videor, strömning av data och webbinnehåll kan skapas direkt på en instrumentpanel med hjälp av [Lägg till panel](service-dashboard-add-widget.md).

  ![Ikonen Lägg till panel](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>Interaktion med paneler på en instrumentpanel
### <a name="move-and-resize-a-tile"></a>Flytta och ändra storlek på en panel
Hämta en panel och [flytta runt den på instrumentpanelen](service-dashboard-edit-tile.md). Hovra och välj referens ![referens](media/service-dashboard-tiles/resize-handle.jpg) för att ändra storlek på panelen.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Hovra över en panel för att ändra utseendet och beteendet
1. Hovra över panelen för att visa ellipserna.
   
    ![panelellips](media/service-dashboard-tiles/ellipses_new.png)
2. Välj ellipserna för att öppna åtgärdsmenyn i panelen.
   
    ![ellipsikon](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Här kan göra du följande:
   
   * [Öppna rapporten som användes för att skapa den här panelen ](service-reports.md) ![rapportikon](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [Öppna kalkylbladet som användes för att skapa den här panelen ](service-reports.md) ![kalkylbladsikon](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
    * [Visa i fokusläge ](service-focus-mode.md) ![fokusikon](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [Exportera data som användes i panelen](visuals/power-bi-visualization-export-data.md) ![ikonen Exportera data](media/service-dashboard-tiles/export-icon.png)
     * [Redigera rubrik och underrubrik, lägg till en hyperlänk](service-dashboard-edit-tile.md)![redigeringsikon](media/service-dashboard-tiles/pencil-icon.jpg)
     * [Köra insikter ](service-insights.md) ![ikonen Insikter](media/service-dashboard-tiles/power-bi-insights.png)
     * [Fästa panelen till en annan instrumentpanel ](service-pin-tile-to-another-dashboard.md)
       ![fästikon](media/service-dashboard-tiles/pin-icon.jpg)
     * [Ta bort panelen](service-dashboard-edit-tile.md)
     ![borttagningsikon](media/service-dashboard-tiles/trash-icon.png)
3. Om du vill stänga åtgärdsmenyn, välj ett tomt område på arbetsytan.

### <a name="select-click-a-tile"></a>Välj (klicka på) en panel
När du väljer en panel beror händelseförloppet på hur du skapade panelen. Och om den har en [anpassad länk](service-dashboard-edit-tile.md) kommer du till denna länk om du väljer panelen. I annat fall kommer du, om du väljer panelen, till rapporten, arbetsboken i Excel Online, den lokala Reporting Services-rapporten eller frågor och svar som användes för att skapa panelen.

> [!NOTE]
> Undantag för detta är videopaneler som skapats direkt på en instrumentpanel med hjälp av **Lägg till panel**. Att välja en videopanel (som har skapats på detta sätt) gör så att videon spelas upp direkt på instrumentpanelen.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

* Om den rapport som användes för att skapa visualiseringen inte sparades kommer inget att hända om du väljer panelen.
* Om panelen skapades från en arbetsbok i Excel Online behöver du minst läsbehörighet för arbetsboken. I annat fall öppnas inte arbetsboken i Excel Online när du väljer panelen.
* Anta att du skapar en panel direkt på en instrumentpanel med hjälp av **Lägg till panel** och anger en anpassad hyperlänk för den. I så fall öppnas webbadressen när du väljer rubriken, underrubriken eller panelen. I annat fall händer som standard ingenting om du väljer en panel som skapats direkt på instrumentpanelen för en bild, webbkod eller textruta.
* Om du inte har behörighet för rapporten i Reporting Services kommer val av en panel som skapats från Reporting Services-rapporten att dirigera dig till en sida som anger att du inte har åtkomst (rsAccessDenied).
* Om du inte har åtkomst till nätverket där Reporting Services -servern finns kommer val av en panel som skapats från Reporting Services dirigera dig till en sida som anger att det inte går att hitta servern (HTTP 404). Enheten måste ha nätverksåtkomst till rapportservern för att visa rapporten.
* Om den ursprungliga visualiseringen som användes för att skapa panelen ändras, ändras inte panelen.  Om du till exempel fäster ett linjediagram från en rapport och sedan ändrar linjediagrammet till ett stapeldiagram, fortsätter panelen på instrumentpanelen att visa ett linjediagram. Data uppdateras, men visualiseringstypen gör det inte.

## <a name="next-steps"></a>Nästa steg
[Skapa ett kort (stor sifferpanel) för din instrumentpanel](power-bi-visualization-card.md)

[Instrumentpaneler i Power BI](service-dashboards.md)  

[Datauppdatering](refresh-data.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

[Exportera en panel till Power Point](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[Fäst Reporting Services-objekt till Power BI-instrumentpaneler](https://msdn.microsoft.com/library/mt604784.aspx)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

