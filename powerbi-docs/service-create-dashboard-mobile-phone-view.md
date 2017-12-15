---
title: "Skapa en vy av en Power BI-instrumentpanel för mobiltelefoner"
description: "Läs hur du skapar en anpassad vy av en instrumentpanel i Power BI-tjänsten för visning på mobiltelefoner."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/12/2017
ms.author: maggies
ms.openlocfilehash: fca163588801633ad3eac227ceea84be17089713
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-view-of-a-power-bi-dashboard-optimized-for-mobile-phones"></a>Skapa en vy av en Power BI-instrumentpanel optimerad för mobiltelefoner
När du visar instrumentpaneler i Power BI-mobilappen på en telefon, märker du att instrumentpanelens paneler placeras ut en i taget, alla i samma storlek. I Power BI-tjänsten, kan du skapa en anpassad vy av valfri instrumentpanel som du äger, specifikt för mobiltelefoner.

När du vänder telefonen på sidan, ser du instrumentpanelen som den ser ut i tjänsten, inte som du designade den för telefonen.

> [!NOTE]
> När du redigerar telefonvyn kan alla som ser instrumentpanelen på en telefon se de ändringar du gör i realtid. Om du till exempel plockar bort alla paneler i instrumentpanelens telefonvy, kommer instrumentpanelen på telefonen plötsligt inte ha några paneler. 
> 
> 

## <a name="create-a-phone-view-of-a-dashboard"></a>Skapa en telefonvy av en instrumentpanel
1. Öppna en instrumentpanel i Power BI-tjänsten.
2. Välj pilen bredvid **webbvy** i det övre högra hörnet > välj **telefonvy**.

    ![](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-dashboard.png)

    Om du inte äger instrumentpanelen visas inte det här alternativet.

    ![](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-canvas.png)

    Telefonredigeringsvyn för instrumentpanelen öppnas. Här kan du ta bort, ändra storlek på och flytta paneler för att passa telefonvyn. Webbversionen av instrumentpanelen ändras inte.


1. Välj en panel för att dra, ändra storlek på eller tas bort. Du ser hur panelerna flyttar undan när du drar en panel.
   
    ![](media/service-create-dashboard-mobile-phone-view/power-bi-unpin-tile-phone-dashboard.png)
   
    De borttagna panelerna åker till fönstret borttagna paneler där de blir kvar om du inte lägger till dem igen.
   
    ![](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-post-edit.png)
2. Om du ändrar dig, väljer du **återställ paneler** för att få tillbaks dem med den storlek och placering som de hade innan.
   
    ![](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-reset-tiles.png)
   
    Bara att öppna telefonredigeringsvyn i Power BI-tjänsten ändrar storleken och formen på panelerna lite på en telefon. Om du vill återställa instrumentpanelen till exakt samma tillstånd som innan du öppnade telefonredigeringsvyn, väljer du **återställ paneler**.
3. När du är nöjd med telefonens instrumentpanelslayout, väljer du pilen bredvid **telefonvy** i det övre högra hörnet > väljer **webbvy**.
   
    Power BI sparar telefonlayouten automatiskt.

## <a name="next-steps"></a>Nästa steg
* [Skapa rapporter som är optimerade för Power BI-telefonapopar](desktop-create-phone-report.md)
* [Skapa dynamiska visuella objekt som optimerats för alla storlekar](desktop-create-responsive-visuals.md)
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

