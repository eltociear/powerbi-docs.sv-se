---
title: Exportera data från ett visuellt Power BI-objekt
description: Exportera data från en rapportvisualisering och instrumentpanelvisualisering och visa dem i Excel.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 3ab3b7a96fb629b303263b1ccf5c2f31603300b4
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71073158"
---
# <a name="export-data-from-a-visual"></a>Exportera data från ett visuellt objekt
Om du vill se de data som används i en visualisering [kan du visa dessa data i Power BI](end-user-show-data.md) eller exportera data till Excel. Alternativet att exportera data kräver en viss typ av licens- och redigeringsbehörigheter till innehållet. Kontakta din Power BI-administratör om du inte kan exportera. 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Från en visualisering på en Power BI-instrumentpanel

1. Starta på en Power BI-instrumentpanel. Här ska vi använda instrumentpanelen från exempelappen ***Marknadsföring och försäljning***. Du kan [hämta den här appen frånAppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282).

    ![Appinstrumentpanel](media/end-user-export/power-bi-dashboards.png)

2. Hovra över en visualisering för att visa ellipserna (...) och klicka för att visa åtgärdsmenyn.

    ![Meny som visas när du väljer ellipserna](media/end-user-export/power-bi-action-menu.png)

3. Välj **Exportera till Excel**.

4. Vad som händer härnäst beror på vilken webbläsare du använder. Du kan uppmanas att spara filen eller så kan en länk till den exporterade filen visas längst ned i webbläsaren. 

    ![Chrome-webbläsare som visar exporterad fillänk](media/end-user-export/power-bi-dashboard-exports.png)

5. Öppna filen i Excel.  

    ![Summa enheter hittils i år i Excel](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>Från en visualisering i en rapport
Du kan exportera data från en visualisering i en rapport som .csv- eller .xlsx-format (Excel). 

1. Välj en panel på instrumentpanelen för att öppna den underliggande rapporten.  I det här exemplet väljer vi samma visualisering som ovan, *totalt antal enheter hittills i år var %.* 

    ![Markerad instrumentpanel](media/end-user-export/power-bi-export-reports.png)

    Eftersom den här panelen skapades från exempelrapporten *Försäljning och marknadsföring* öppnas den rapporten. Och den öppnas på sidan som innehåller den valda visualiseringen. 

2. Välj panelen i rapporten. Expandera fönstret **Filter** till höger. Den här visualiseringen har tillämpade filter. Mer information om filter finns i [Använda filter i en rapport.](end-user-report-filter.md)

    ![Filterfönstret har valts](media/end-user-export/power-bi-export-filter.png)


3. Välj ellipserna i det övre högra hörnet i visualiseringen. Välj **Exportera data**.

    ![Markerade exporterade data från listrutan](media/end-user-export/power-bi-export-report.png)

4. Du ser alternativ för att exportera sammanfattade data eller underliggande data. Om du använder exempelappen *Försäljning och marknadsföring* inaktiveras **Underliggande data**. Men du kan stöta på rapporter där båda alternativen är aktiverade. Här förklaras skillnaden.

    **Sammanfattade data**: Välj det här alternativet om du vill exportera data för det som visas i visualiseringen.  Den här typen av export visar bara de data som använts för att skapa visualiseringen. Om visualiseringen har filter tillämpat kommer även de data du exporterar att filtreras. Till exempel, i den här visualiseringen kommer din export endast att innehålla data för 2014 och den centrala regionen, och endast data för fyra av tillverkarna: VanArsdel, Natura, Aliqui och Pirum.
  

    **Underliggande data**: Välj det här alternativet om du vill exportera data för det du ser i visualiseringen **plus** ytterligare data från den underliggande datauppsättningen.  Detta kan omfatta data som finns i datauppsättningen men som inte används i visualiseringen. 

    ![Meny där du väljer underliggande eller sammanfattade](media/end-user-export/power-bi-export-option.png)

5. Vad som händer härnäst beror på vilken webbläsare du använder. Du kan uppmanas att spara filen eller så kan en länk till den exporterade filen visas längst ned i webbläsaren. 

    ![Exporterad fil visas i webbläsaren Microsoft Edge](media/end-user-export/power-bi-export-edge-browser.png)


6. Öppna filen i Excel. Jämför mängden data som exporteras med de data som vi exporterade från samma visualiseringen på instrumentpanelen. Skillnaden är att denna export inkluderar **underliggande data**. 

    ![Excel-exempel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Nästa steg

[Visa de data som används för att skapa ett visuellt objekt](end-user-show-data.md)