---
title: Ange datavarningar i Power BI-tjänsten
description: Ställ in aviseringar som meddelar dig när data i dina instrumentpaneler har ändrats så att de överskrider de gränser du har angett i Microsoft Power BI-tjänsten.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 8f5d11b53526c5d266b96a8f21c42fecc66d3795
ms.sourcegitcommit: c839ef7437bc8fb8f7eeda23e59d05c7192a7fe8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163764"
---
# <a name="data-alerts-in-the-power-bi-service"></a>Datavarningar i Power BI-tjänsten

Ställ in aviseringar som meddelar dig när data i dina instrumentpaneler har ändrats så att de överskrider de gränser du har angett.

Du kan konfigurera aviseringar på paneler om du har en Power BI Pro-licens. Du kan även konfigurera aviseringar om någon delar en instrumentpanel som finns i en [Premium](service-premium-what-is.md)-kapacitet. Aviseringar kan endast konfigureras på paneler som har fästs från visuella objekt i rapporter och endast på mätare, KPI:er och kort. Aviseringar kan konfigureras för visuella objekt som skapats från direktuppspelande datamängder som du fäster från en rapport på en instrumentpanel. Aviseringar kan inte konfigureras på direktuppspelande paneler som skapats direkt på instrumentpanelen med hjälp av **Lägg till panel** > **Anpassade direktuppspelande data**.

Du kan endast se aviseringar som du anger, även om du delar din instrumentpanel. Inte ens instrumentpanelens ägare kan se de aviseringar du anger i din vy av instrumentpanelen. Datavarningar är helt synkroniserade på plattformar. Ställ in och visa datavarningar [i Power BI-appar](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) och i Power BI-tjänsten. De är inte tillgängliga för Power BI Desktop. Du kan till och med automatisera och integrera aviseringar med Power Automate. Du kan prova själv i den här artikeln om [Power Automate och Power BI](service-flow-integration.md).

![paneler](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Datadrivna aviseringar ger information om dina data. Om du visar dina Power BI-data på en mobil enhet och den tappas bort eller blir stulen bör du använda Power BI-tjänsten för att inaktivera alla datagenererade aviseringar.

## <a name="set-data-alerts-in-the-power-bi-service"></a>Ange datavarningar i Power BI-tjänsten

Se när Amanda lägger till aviseringar i rutor på instrumentpanelen. Prova sedan själv genom att följa de stegvisa anvisningarna under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

I det här exemplet används en kortpanel från exempelinstrumentpanelen detaljhandelsanalys. Om du vill följa med kan du [hämta Exempel på detaljhandelsanalys](sample-retail-analysis.md#get-the-content-pack-for-this-sample).

1. Starta på en instrumentpanel. Från panelen **Totalt antal butiker** väljer du ellipsen.

   ![panelen Totalt antal butiker](media/service-set-data-alerts/powerbi-card.png)

1. Välj klockikonen ![aviseringsikon](media/service-set-data-alerts/power-bi-bell-icon.png) för att lägga till en eller flera aviseringar för **Totalt antal butiker**.

1. För att starta väljer du **+ Lägg till varningsregel**, kontrollerar att skjutreglaget **Aktiv** är inställt till **På** och ge aviseringen en rubrik. Namnet hjälper dig att identifiera aviseringarna.

   ![Fönstret Hantera aviseringar](media/service-set-data-alerts/powerbi-alert-title.png)

1. Bläddra nedåt och ange detaljerad information om aviseringen.  I det här exemplet skapar du en avisering som meddelar dig en gång om dagen om det totala antalet butiker överstiger 100.

   ![Fönstret Hantera aviseringar, ange tröskelvärde](media/service-set-data-alerts/power-bi-set-alert-details.png)

    Aviseringar visas i **Meddelandecenter**. Power BI skickar även ett e-postmeddelande om aviseringen om du markerar kryssrutan.

1. Välj **Spara och stäng**.

## <a name="receiving-alerts"></a>Ta emot aviseringar

När spårade data når något av dina angivna tröskelvärden sker flera saker. Först kontrollerar Power BI om mer än en timme eller mer än 24 timmar (beroende på vilket alternativ du valde) har gått sedan den senaste aviseringen. Om data överskrider tröskelvärdet får du en avisering.

Därefter skickar Power BI en avisering till **Meddelandecenter** och, om du vill, via e-post. Varje avisering innehåller en direktlänk till dina data. Klicka på länken om du vill se den berörda panelen där du kan utforska, dela och visa mer information.  

* Om du har valt att skicka ett e-postmeddelande kommer du att se följande i din inkorg.

   ![Aviseringsmeddelande](media/service-set-data-alerts/powerbi-alerts-email.png)

* Power BI lägger till ett meddelande i **meddelandecentret** och lägger till en ny aviseringsikon i den berörda panelen.

   ![Meddelandeikonen i Power BI-tjänsten](media/service-set-data-alerts/powerbi-alert-notifications.png)

* **Meddelandecenter** visar information om aviseringen.

    ![läs aviseringen](media/service-set-data-alerts/powerbi-alert-notification.png)

   > [!NOTE]
   > Aviseringar fungerar endast på uppdaterade data. När data uppdateras söker Power BI för att se om en avisering har angetts för dessa data. Om data har uppnått ett aviseringströskelvärde utlöser Power BI en avisering.

## <a name="managing-alerts"></a>Hantera aviseringar

Det finns många sätt att hantera dina aviseringar:

* På instrumentpanelen.

* På inställningsmenyn för Power BI.

* På en panel i [Power BI-mobilapparna](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-dashboard-tile"></a>På instrumentpanelen

1. Om du behöver ändra eller ta bort en avisering för en panel öppnar du fönstret **Hantera aviseringar** på nytt genom att välja klockikonen ![klockikon](media/service-set-data-alerts/power-bi-bell-icon.png).

    Power BI visar alla aviseringar som du har angett för den panelen.

    ![Fönstret Hantera aviseringar](media/service-set-data-alerts/powerbi-see-alerts.png)

1. Om du vill ändra en avisering, väljer du pilen till vänster om aviseringens namn.

    ![pilen bredvid aviseringsnamnet](media/service-set-data-alerts/powerbi-see-alerts-arrow.png)

1. Om du vill ta bort en avisering, väljer du papperskorgen till höger om aviseringens namn.

      ![papperskorgikonen har valts](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>På inställningsmenyn för Power BI

1. Välj kugghjulsikonen från menyfältet i Power BI och välj **Inställningar**.

    ![kugghjulsikonen](media/service-set-data-alerts/powerbi-gear-icon.png).

1. Välj **Aviseringar** under **Inställningar**.

    ![Fliken Aviseringar i fönstret Inställningar](media/service-set-data-alerts/powerbi-alert-settings.png)

1. Härifrån kan du aktivera och inaktivera aviseringar, öppna fönstret **Hantera aviseringar** för att ändra eller ta bort aviseringen.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

* Aviseringar stöds inte för kortpaneler med datum-/tidsmått.
* Aviseringar fungerar bara med numeriska datatyper.
* Aviseringar fungerar endast på uppdaterade data. De fungerar inte på statiska data.
* Aviseringar fungerar endast på direktuppspelade datamängder om du bygger ett visuellt objekt för KPI, kort eller mätare och sedan fäster det visuella objektet på instrumentpanelen.


## <a name="next-steps"></a>Nästa steg

* [Skapa ett Power Automate som innehåller en datavarning](service-flow-integration.md).

* [Konfigurera datavarningar på din mobila enhet](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

* [Vad är Power BI?](fundamentals/power-bi-overview.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
