---
title: "Ange datavarningar i Power BI-tjänsten"
description: "Ställ in aviseringar som meddelar dig när data i dina instrumentpaneler har ändrats så att de överskrider de gränser du har angett i Microsoft Power BI-tjänsten."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: JbL2-HJ8clE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/21/2017
ms.author: mihart
ms.openlocfilehash: 2a4134e1a06933927bd2c5453cd8e7a79394c384
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/21/2017
---
# <a name="data-alerts-in-power-bi-service"></a>Datavarningar i Power BI-tjänsten
Ställ in aviseringar som meddelar dig när data i dina instrumentpaneler har ändrats så att de överskrider de gränser du har angett. 

Aviseringar kan endast ställas in på paneler som har fästs från rapportvisualiseringar och endast på mätare, KPI:er och kort. Aviseringar kan ställas in på visuella objekt som skapats från direktuppspelande datauppsättningar som har fästs från en rapport till en instrumentpanel, men kan inte anges för direktuppspelande paneler som skapas direkt på en instrumentpanel med hjälp av **Lägg till panel** > **Anpassade direktuppspelande data**. 

Du kan endast se aviseringar som du anger, även om du delar din instrumentpanel. Datavarningar är helt synkroniserade på plattformar. Ställ in och visa datavarningar [i Power BI-appar](mobile-set-data-alerts-in-the-mobile-apps.md) och i Power BI-tjänsten. De finns inte för Power BI Desktop. Aviseringar kan även vara [automatiserade och integrerade med Microsoft Flow](https://flow.microsoft.com) - [Prova själv](service-flow-integration.md).

![](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Datadrivna aviseringar ger information om dina data. Om du visar dina Power BI-data på en mobilenhet och den blir stulen, bör du använda Power BI-tjänsten för att inaktivera alla datadrivna aviseringar.
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Ange datavarningar i Power BI-tjänsten
Se när Amanda lägger till aviseringar i paneler på sin instrumentpanel. Prova sedan själv genom att följa de stegvisa anvisningarna under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

I det här exemplet används en kortpanel från exempelinstrumentpanelen detaljhandelsanalys.

1. Starta på en instrumentpanel. Välj ellipserna från en mätare, KPI eller kortpanel på instrumentpanelen.
   
   ![](media/service-set-data-alerts/powerbi-card.png)
2. Välj på klockikonen ![](media/service-set-data-alerts/power-bi-bell-icon.png) för att lägga till en eller flera aviseringar för **Summa butiker**.
   
1. För att starta, väljer du **+ Lägg till aviseringsregel** kontroller att skjutreglaget är inställt till **På** och ge din avisering en rubrik. Namnet hjälper dig att identifiera aviseringarna.
   
   ![](media/service-set-data-alerts/powerbi-alert-title.png)
4. Bläddra nedåt och ange detaljerad information om aviseringen.  I det här exemplet ska vi skapa en avisering som meddelar oss en gång om dagen om antalet totala butiker går över 100. Aviseringar visas i meddelandecentret. Power BI kommer också att skicka ett e-postmeddelande.
   
   ![](media/service-set-data-alerts/power-bi-set-alert-details.png)
5. Välj **Spara**.

## <a name="receiving-alerts"></a>Ta emot aviseringar
När data som spåras når något av dina angivna tröskelvärden sker flera saker. Först kontrollerar Power BI om mer än en timme eller mer än 24 timmar har gått (beroende på vilket alternativ som du valde) sedan den senaste aviseringen skickades. Så länge data har passerat tröskelvärdet får du en avisering.

Därefter skickar Power BI en avisering till meddelandecentret och, om du vill, via e-post. Varje avisering innehåller en direktlänk till dina data. Klicka på länken om du vill se den berörda panelen där du kan utforska, dela och visa mer information.  

1. Om du har valt att skicka ett e-postmeddelande kommer du att se följande i din inkorg.
   
   ![](media/service-set-data-alerts/powerbi-alerts-email.png)
2. Power BI lägger till ett meddelande i **meddelandecentret** och lägger till en ny aviseringsikon i den berörda panelen.
   
   ![](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. Öppna meddelandecentret om du vill se detaljerad information om aviseringen.
   
    ![](media/service-set-data-alerts/powerbi-alert-notfication.png)
   
   > [!NOTE]
   > Aviseringar fungerar bara på data som ska uppdateras. När data uppdateras söker Power BI för att se om en avisering har angetts för dessa data. Om data har uppnått ett tröskelvärde utlöses en avisering.
   > 
   > 

## <a name="managing-alerts"></a>Hantera aviseringar
Det finns flera sätt att hantera dina aviseringar: från paneler i instrumentpanelen, Power BI-inställningsmenyn och på en enskild panel i [Power BI-mobilappen på iPhone](mobile-set-data-alerts-in-the-mobile-apps.md) eller i [Power BI-mobilappen för Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Från själva panelen
1. Om du behöver ändra eller ta bort en avisering för en panel, ska du öppna fönstret **Hantera aviseringar** på nytt genom att välja klockikonen ![](media/service-set-data-alerts/power-bi-bell-icon.png). Alla aviseringar som du har angett för panelen visas.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts.png).
2. Om du vill ändra en avisering, väljer du pilen till vänster om aviseringens namn.
   
    ![](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. Om du vill ta bort en avisering, väljer du papperskorgen till höger om aviseringens namn.
   
      ![](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>På inställningsmenyn för Power BI
1. Välj kugghjulsikonen från menyfältet i Power BI.
   
    ![](media/service-set-data-alerts/powerbi-gear-icon.png).
2. Välj **Aviseringar** under **Inställningar**.
   
    ![](media/service-set-data-alerts/powerbi-alert-settings.png)
3. Härifrån kan du aktivera och inaktivera aviseringar, öppna fönstret **Hantera aviseringar** för att ändra eller ta bort aviseringen.

## <a name="tips-and-troubleshooting"></a>Tips och felsökning
* Aviseringar stöds inte för närvarande för Bing paneler eller kortpaneler med datum-/tidsmått.
* Aviseringar fungerar bara med numeriska datatyper.
* Aviseringar fungerar bara på data som ska uppdateras. De fungerar inte på statiska data.
* Aviseringar fungerar bara på direktöverförda datauppsättningar om du bygger en mätare-KPI/kort för det visuella objektet och fäster det visuella objektet på instrumentpanelen.

## <a name="next-steps"></a>Nästa steg
[Skapa ett Microsoft-flöde som innehåller en datavarning](service-flow-integration.md)    
[Ställa in datavarningar på din mobilenhet](mobile-set-data-alerts-in-the-mobile-apps.md)    
[Kom igång med Power BI](service-get-started.md)    
Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

