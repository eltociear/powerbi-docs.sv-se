---
title: "Skapa en stor sifferpanel från en Power BI-rapport"
description: "Skapa en stor sifferpanel från en Power BI-rapport"
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 9f748ed1d3a34c6c6aceb14337bbb780598a15f9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-big-number-tile-from-a-power-bi-report"></a>Skapa en stor sifferpanel från en Power BI-rapport
Ett enda tal kan ibland vara det viktigaste du vill spåra i Power BI-instrumentpanelen, till exempel total försäljning, marknadsandel år för år eller totala affärsmöjligheter. Du kan skapa en stor sifferpanel [genom att ställa en fråga i rutan Frågor och svar](power-bi-visualization-big-number.md) eller i en Power BI-rapport. Den här artikeln beskriver hur du skapar en i en rapport.

1. Skapa en [instrumentpanel](service-dashboards.md) och [hämta data](service-get-data.md).
   
   Om du vill få data att öva på kan du [hämta Exempel på detaljhandelsanalys](sample-retail-analysis.md). 
2. Öppna rapporten i [Redigeringsvy](service-reading-view-and-editing-view.md).
3. Hitta en sida med tomt utrymme i rapporten eller [lägg till en ny sida i rapporten](power-bi-report-add-page.md).
4. Välj det talfält som du vill visa i Fält-listan.
   
   I det här exemplet **Antal öppna butiker** i tabellen **Butik**. Power BI skapar ett stapeldiagram med ditt tal.
   
   ![](media/power-bi-visualization-big-number-report/pbi_rptnumbertilechart.png)
5. I fönstret Visualiseringar väljer du färgrollerikonen.
   
   ![](media/power-bi-visualization-big-number-report/pbi_changechartcard.png)
6. Hovra över kortet och välj fästikonen ![](media/power-bi-visualization-big-number-report/pbi_pintile.png) för att lägga till panelen på instrumentpanelen. 
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-icon.png)
7. Fäst panelen på en befintlig eller ny instrumentpanel. 
   
   * Befintlig instrumentpanel: välj instrumentpanelens namn i listrutan.
   * Ny instrumentpanel: Skriv instrumentpanelens namn.
8. Välj **Fäst**.
   
   Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-success-message.png)
9. Välj **Gå till instrumentpanelen**. Där kan du [redigera och flytta](service-dashboard-edit-tile.md) den fästa visualiseringen.

## <a name="next-steps"></a>Nästa steg
[Paneler på instrumentpanelen i Power BI](service-dashboard-tiles.md)

[Instrumentpaneler i Power BI](service-dashboards.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

