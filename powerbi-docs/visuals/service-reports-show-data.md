---
title: Visa data som används för att skapa visualiseringen Power BI
description: Det här dokumentet förklarar hur du visar data som används för att skapa en visualisering i Power BI och hur du exporterar dessa data till en .csv-fil.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5417511b12c85cb467c3613671a1e101541c9609
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "73880623"
---
# <a name="show-the-data-that-was-used-to-create-the-visualization"></a>Visa data som används för att skapa visualiseringen
## <a name="show-data"></a>Visa data
En Power BI-visualisering konstrueras med data från dina datauppsättningar. Om du är intresserad av att se vad som pågår i bakgrunden, Power BI kan *visa* de data som används för att skapa visualiseringen. När du väljer **Visa data** visar Power BI dessa data under (eller bredvid) visualiseringen.

Du kan också exportera de data som används för att skapa visualiseringen som en .xlsx- eller .csv-fil och visa dem i Excel. Mer information finns i [Exportera data från visualiseringar i Power BI](power-bi-visualization-export-data.md).

> [!NOTE]
> *Visa Data* och *Exportera data* finns både i Power BI-tjänsten och Power BI Desktop. Dock ger Power BI Desktop ett ytterligare lager med information: [*Visa poster* visar de faktiska raderna i datauppsättningen](../desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Använda *Visa data* 
1. I Power BI Desktop väljer du en visualisering för att aktivera den.

2. Välj **Fler åtgärder** (...) och **Visa data**. 
    ![visningsalternativ för Visa data](media/service-reports-show-data/power-bi-more-action.png)


3. Som standard visas data under visualiseringen.
   
   ![visning av visuellt objekt och lodräta data](media/service-reports-show-data/power-bi-show-data-below.png)

4. För att välja orientering väljer du lodrät layout ![liten skärmbild av ikonen som används för att ändra till lodrät layout](media/service-reports-show-data/power-bi-vertical-icon-new.png) uppe i det högra hörnet på visualiseringen.
   
   ![visning av visuellt objekt och vågräta data](media/service-reports-show-data/power-bi-show-data-side.png)
5. Om du vill exportera data till en .csv-fil väljer du ellipserna och sedan **Exportera data**.
   
    ![välj Exportera data](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Mer information om att exportera data till Excel finns i [Exportera data från visualiseringar i Power BI](power-bi-visualization-export-data.md).
6. Om du vill dölja data avmarkerar du **Utforska** > **Visa data**.

## <a name="using-show-records"></a>Använda Visa poster
Du kan också fokusera på en datapost i en visualisering och gå in på detaljnivå på bakomliggande data. 

1. Välj en visualisering för att aktivera den och använda **Visa poster**. 

2. I menyfliksområdet Desktop väljer du fliken för **Visuella verktyg** > **Data/detaljgranska** > **Visa poster**. 

    ![Skärmbild där Visa poster har valts.](media/service-reports-show-data/power-bi-see-record.png)

3. Välj en datapunkt eller en rad i visualiseringen. I det här exemplet har vi valt den fjärde kolumnen från vänster. Power BI visar datamängdsposten för datapunkten.

    ![Skärmbild av enskild post från datamängd.](media/service-reports-show-data/power-bi-row.png)

4. Välj **Tillbaka till rapporten** för att återgå till Desktop-rapportens arbetsyta. 

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

- Om knappen **Visa poster** i menyfliksområdet är inaktiverad och nedtonad, betyder det att den valda visualiseringen inte stöder Visa poster.
- Du kan inte ändra data i vyn Visa poster och sedan spara dem i rapporten igen.
- Du kan inte använda Visa poster när ditt visuella objekt använder ett beräknat mått.
- Du kan inte använda Visa poster när du är ansluten till en flerdimensionell livemodell.  

## <a name="next-steps"></a>Nästa steg
[Exportera data från Power BI-visualiseringar](power-bi-visualization-export-data.md)    

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

