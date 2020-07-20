---
title: Optimera en instrumentpanel för mobiltelefoner – Power BI
description: Läs hur du skapar en anpassad vy av en instrumentpanel i Power BI-tjänsten för visning på mobiltelefoner.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: bc1c9987205e86ee9a123bf8ba9afd567c59ff52
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264714"
---
# <a name="optimize-a-dashboard-for-mobile-phones---power-bi"></a>Optimera en instrumentpanel för mobiltelefoner – Power BI 
När du visar instrumentpaneler i stående läge på en telefon märker du att instrumentpanelens paneler placeras ut en i taget, alla i samma storlek. I Power BI-tjänsten kan du skapa en anpassad vy av en instrumentpanel särskilt för stående läge på mobiltelefoner. Även om du skapar en telefonvy ser du instrumentpanelen som den ser ut i tjänsten när du vänder telefonen i sidled.

Letar du efter information om visning av instrumentpaneler på en mobil enhet? Prova den här snabbstarten [Utforska instrumentpaneler och rapporter i Power BI-mobilappar](../consumer/mobile/mobile-apps-quickstart-view-dashboard-report.md) i stället.

> [!NOTE]
> När du redigerar telefonvyn kan alla som ser instrumentpanelen på en telefon se de ändringar du gör i realtid. Om du till exempel plockar bort alla paneler i instrumentpanelens telefonvy, kommer instrumentpanelen på telefonen plötsligt inte ha några paneler. 
> 
> 

## <a name="create-a-phone-view-of-a-dashboard"></a>Skapa en telefonvy av en instrumentpanel
1. Öppna en instrumentpanel i Power BI-tjänsten.
2. Välj pilen bredvid **webbvy** i det övre högra hörnet > välj **telefonvy**.

    ![Skärmbild av listrutan Webbvy och en pekare till Telefonvy.](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-dashboard.png)

    Om du inte äger instrumentpanelen visas inte det här alternativet.

    ![Skärmbild av en telefoninstrumentpanel och redigeringsalternativ för att ta bort, ändra storlek på och ordna om paneler så att de passar i telefonvyn.](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-canvas.png)

    Telefonredigeringsvyn för instrumentpanelen öppnas. Här kan du ta bort, ändra storlek på och flytta paneler för att passa telefonvyn. Webbversionen av instrumentpanelen ändras inte.


1. Välj en panel för att dra, ändra storlek på eller tas bort. Du ser hur panelerna flyttar undan när du drar en panel.
   
    ![Skärmbild av telefonpaneler och panelalternativ för att dra, ändra storlek på eller ta bort paneler.](media/service-create-dashboard-mobile-phone-view/power-bi-unpin-tile-phone-dashboard.png)
   
    De borttagna panelerna åker till fönstret borttagna paneler där de blir kvar om du inte lägger till dem igen.
   
    ![Skärmbild av en telefoninstrumentpanel med paneler i fönstret Ej fästa paneler.](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-post-edit.png)
2. Om du ändrar dig, väljer du **återställ paneler** för att få tillbaks dem med den storlek och placering som de hade innan.
   
    ![Skärmbild av fönstret Ej fästa paneler med en pekare till Återställ paneler.](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-reset-tiles.png)
   
    Bara att öppna telefonredigeringsvyn i Power BI-tjänsten ändrar storleken och formen på panelerna lite på en telefon. Om du vill återställa instrumentpanelen till exakt samma tillstånd som innan du öppnade telefonredigeringsvyn, väljer du **återställ paneler**.
3. När du är nöjd med telefonens instrumentpanelslayout, väljer du pilen bredvid **telefonvy** i det övre högra hörnet > väljer **webbvy**.
   
    Power BI sparar telefonlayouten automatiskt.

## <a name="next-steps"></a>Nästa steg
* [Skapa rapporter som är optimerade för Power BI-telefonapopar](desktop-create-phone-report.md)
* [Skapa dynamiska visuella objekt som optimerats för alla storlekar](../visuals/power-bi-report-visualizations.md)
* Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
