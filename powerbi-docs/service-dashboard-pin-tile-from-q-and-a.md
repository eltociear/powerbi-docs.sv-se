---
title: "Fäst en panel på en Power BI-instrumentpanel från frågor och svar"
description: "Dokumentering om hur man fäster en panel på en Power BI-instrumentpanel från frågerutan i frågor och svar"
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
ms.date: 09/09/2017
ms.author: mihart
ms.openlocfilehash: f37c0f9e433f1ac8c6bb8f7f3fa4b513fb4b4652
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Fäst en panel till en instrumentpanel från frågor och svar
## <a name="how-to-pin-a-tile-from-qa"></a>Så här fäster du en panel från frågor och svar
Frågor och svar är Power BI:s verktyg för ad hoc-rapportering. Behöver du hitta en viss insikt? Ställ en fråga om dina data och ta emot ett svar i form av en visualisering.

> **Obs**: Om du vill följa med, kan du öppna [exemplet detaljhandelsanalys](sample-retail-analysis.md).
> 
> 

1. Öppna en [instrumentpanel](service-dashboards.md) som har minst en panel fäst från en rapport. När du skriver en fråga, letar Power BI efter svaret i alla datauppsättningar som har en panel fäst på den instrumentpanelen.  Läs mer i [hämta data](service-get-data.md).
2. Börja skriva vad du vill veta om dina data i frågerutan överst på instrumentpanelen.  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. När du till exempel skriver senaste årets försäljning per månad och område...  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)
   
   ger frågerutan dig förslag.
4. Om du vill lägga till diagrammet till din instrumentpanel, väljer du fäst ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) längst upp till höger i arbetsytan.
5. Fäst panelen på en befintlig eller ny instrumentpanel. 
   
   * Befintlig instrumentpanel: välj instrumentpanelens namn i listrutan. Dina val begränsas till instrumentpanelerna inom den aktuella arbetsytan.
   * Ny instrumentpanel: ange namnet på den nya instrumentpanelen så läggs den till din aktuella arbetsyta.
6. Välj **fäst**.
   
   Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.  
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Välj **gå till instrumentpanel** för att se den nya panelen. Där kan du [byta namn på, ändra storlek, lägga till en hyperlänk och flytta panelen och mer](service-dashboard-edit-tile.md) på din instrumentpanel. 
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* När du börjar skriva en fråga, börjar frågor och svar genast att söka efter det bästa svaret från alla datauppsättningar som är associerade med den aktuella instrumentpanelen.  Den aktuella instrumentpanelen är den instrumentpanel som listas i det övre navigeringsfältet. Den här frågan ställs till exempel i instrumentpanelen **exemplet detaljshandelsanalys** som är en del av **mihart**-apparbetsytan.
  
  ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **Hur vet frågor och svar vilka datauppsättningar som ska användas**?  Frågor och svar har åtkomst till alla datauppsättningar som har visualiseringar fästa på den instrumentpanelen.

## <a name="next-steps"></a>Nästa steg
[Byt namn på, ändra storlek, lägg till en hyperlänk, flytta panelen och mer](service-dashboard-edit-tile.md)    
[Visa din panel i instrumentpanelen i fokusläge](service-focus-mode.md)     
[Gå tillbaka till frågor och svar i Power BI](service-q-and-a.md)  
Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

