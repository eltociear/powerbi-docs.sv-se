---
title: Ange geografiska filter i Power BI Desktop för mobilapparna
description: När du ställer in geografisk filtrering i din modell i Power BI Desktop, kan du filtrera data för din plats automatiskt i Power BI-mobilapparna.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: ed8a0990c9da2da877c32a0ef44c676f91e0f493
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34291407"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Ange geografiska filter i Power BI Desktop för mobilapparna
Du kan i Power BI Desktop [kategorisera geografiska data](desktop-data-categorization.md) för en kolumn, så att Power BI Desktop vet hur värden ska hanteras i visuella objekt i en rapport. En fördel när du och dina kolleger ser rapporten i Power BI-mobilapparna är att Power BI automatiskt anger geografiska filter baserat på var ni befinner er. 

Anta exempelvis att du är en försäljningschef som reser för att träffa kunder och du snabbt vill filtrera försäljning och intäkter för en viss kund som du planerar att besöka. Du vill filtrera ut data för din aktuella plats, oavsett om det gäller region, stad eller en faktisk adress. Senare, om du har tid, tänker du besöka andra kunder i närheten. Du kan [filtrera rapporten efter din plats för att söka efter dessa kunder](mobile-apps-geographic-filtering.md).

> [!NOTE]
> Du kan bara filtrera efter plats i mobilappen om geografiska namn i rapporten är på engelska &#150; till exempel ”New York City” eller ”Germany”.
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Identifiera geografiska data i rapporten
1. Växla till Datavy i Power BI Desktop ![Ikonen Datavy](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Välj en kolumn med geografiska data &#151; till exempel kolumnen Stad.
   
    ![Kolumnen Stad](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. På fliken **Modellering** väljer du **Datakategori** och sedan rätt kategori &#151; i det här exemplet **Stad**.
   
    ![Rutan Datakategori](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Fortsätt konfigurera geografiska datakategorier för andra fält i modellen. 
   
   > [!NOTE]
   > Du kan ange flera kolumner för varje datakategori i en modell, men om du gör det kan modellen inte filtrera efter geografi i Power BI-mobilappen. Om du vill använda geografisk filtrering i mobilappar, anger du endast en kolumn för varje datakategori &#151; till exempel bara en kolumn för **Stad**, en kolumn för **Region** och en kolumn för **Land**. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Skapa visuella objekt med geografiska data
1. Växla till Rapportvy ![Ikonen Rapportvy](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png), och skapa visuella objekt som använder de geografiska fälten i dina data. 
   
    ![Rapport med karta](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    I det här exemplet innehåller modellen också en beräknad kolumn där både staden och regionen finns tillsammans i en kolumn. Läs mer om [att skapa beräknade kolumner i Power BI Desktop](desktop-calculated-columns.md).
   
    ![Fältet Stad + Region](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Publicera rapporten i Power BI-tjänsten.

## <a name="view-the-report-in-power-bi-mobile-app"></a>Visa rapporten i Power BI-mobilappen
1. Öppna rapporten i någon av [Power BI-mobilapparna](mobile-apps-for-mobile-devices.md).
2. Om du använder en geografisk plats med data i rapporten kan du filtrera den automatiskt till din plats.
   
    ![Geografiskt filter i mobilappen](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

Läs mer om att [filtrera en rapport efter plats i Power BI-mobilapparna](mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>Nästa steg
* [Datakategorisering i Power BI Desktop](desktop-data-categorization.md)  
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

