---
title: Ange datavarningar i Power BI-tjänsten
description: Ställ in aviseringar som meddelar dig när data i dina instrumentpaneler har ändrats så att de överskrider de gränser du har angett i Microsoft Power BI-tjänsten.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: cc374da84e269abe18a52270c0d9fd15987cf666
ms.sourcegitcommit: fdb54145f9bc93b312409c15c603749f3a4a876e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52452624"
---
# <a name="data-alerts-in-power-bi-service"></a>Datavarningar i Power BI-tjänsten
Ställ in aviseringar som meddelar dig när data i dina instrumentpaneler har ändrats så att de överskrider de gränser du har angett. 

Du kan ställa in aviseringar på paneler om du har en Power BI Pro-licens, eller om någon har delat en instrumentpanel med dig från en [Premium-kapacitet](service-premium.md). Aviseringar kan endast ställas in på paneler som har fästs från rapportvisualiseringar och endast på mätare, KPI:er och kort. Aviseringar kan ställas in på visuella objekt som skapats från direktuppspelande datauppsättningar som har fästs från en rapport till en instrumentpanel, men kan inte anges för direktuppspelande paneler som skapas direkt på en instrumentpanel med hjälp av **Lägg till panel** > **Anpassade direktuppspelande data**. 

Du kan endast se aviseringar som du anger, även om du delar din instrumentpanel. Datavarningar är helt synkroniserade på plattformar. Ställ in och visa datavarningar [i Power BI-appar](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) och i Power BI-tjänsten. De finns inte för Power BI Desktop. Aviseringar kan även vara [automatiserade och integrerade med Microsoft Flow](https://flow.microsoft.com) - [Prova själv](service-flow-integration.md).

![paneler](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Datadrivna aviseringar ger information om dina data. Om du visar dina Power BI-data på en mobilenhet och den blir stulen, bör du använda Power BI-tjänsten för att inaktivera alla datadrivna aviseringar.
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Ange datavarningar i Power BI-tjänsten
Se när Amanda lägger till aviseringar i paneler på sin instrumentpanel. Prova sedan själv genom att följa de stegvisa anvisningarna under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

I det här exemplet används en kortpanel från exempelinstrumentpanelen detaljhandelsanalys.

1. Starta på en instrumentpanel. Välj ellipserna från en mätare, KPI eller kortpanel på instrumentpanelen.
   
   ![panelen Totalt antal butiker](media/service-set-data-alerts/powerbi-card.png)
2. Välj klockikonen ![aviseringsikon](media/service-set-data-alerts/power-bi-bell-icon.png) för att lägga till en eller flera aviseringar för **Totalt antal butiker**.
   
1. För att starta, väljer du **+ Lägg till aviseringsregel** kontroller att skjutreglaget är inställt till **På** och ge din avisering en rubrik. Namnet hjälper dig att identifiera aviseringarna.
   
   ![Fönstret Hantera aviseringar](media/service-set-data-alerts/powerbi-alert-title.png)
4. Bläddra nedåt och ange detaljerad information om aviseringen.  I det här exemplet ska vi skapa en avisering som meddelar oss en gång om dagen om antalet totala butiker går över 100. Aviseringar visas i meddelandecentret. Power BI kommer också att skicka ett e-postmeddelande.
   
   ![Fönstret Hantera aviseringar, ange tröskelvärde](media/service-set-data-alerts/power-bi-set-alert-details.png)
5. Välj **Spara**.

## <a name="receiving-alerts"></a>Ta emot aviseringar
När data som spåras når något av dina angivna tröskelvärden sker flera saker. Först kontrollerar Power BI om mer än en timme eller mer än 24 timmar har gått (beroende på vilket alternativ som du valde) sedan den senaste aviseringen skickades. Så länge data har passerat tröskelvärdet får du en avisering.

Därefter skickar Power BI en avisering till meddelandecentret och, om du vill, via e-post. Varje avisering innehåller en direktlänk till dina data. Klicka på länken om du vill se den berörda panelen där du kan utforska, dela och visa mer information.  

1. Om du har valt att skicka ett e-postmeddelande kommer du att se följande i din inkorg.
   
   ![Aviseringsmeddelande](media/service-set-data-alerts/powerbi-alerts-email.png)
2. Power BI lägger till ett meddelande i **meddelandecentret** och lägger till en ny aviseringsikon i den berörda panelen.
   
   ![Meddelandeikonen i Power BI-tjänsten](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. Öppna meddelandecentret om du vill se detaljerad information om aviseringen.
   
    ![läs aviseringen](media/service-set-data-alerts/powerbi-alert-notification.png)
   
   > [!NOTE]
   > Aviseringar fungerar bara på data som ska uppdateras. När data uppdateras söker Power BI för att se om en avisering har angetts för dessa data. Om data har uppnått ett tröskelvärde utlöses en avisering.
   > 
   > 

## <a name="managing-alerts"></a>Hantera aviseringar
Det finns flera sätt att hantera dina aviseringar: från paneler i instrumentpanelen, Power BI-inställningsmenyn och på en enskild panel i [Power BI-mobilappen på iPhone](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) eller i [Power BI-mobilappen för Windows 10](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Från själva panelen
1. Om du behöver ändra eller ta bort en avisering för en panel öppnar du fönstret **Hantera aviseringar** på nytt genom att välja klockikonen ![klockikon](media/service-set-data-alerts/power-bi-bell-icon.png). Alla aviseringar som du har angett för panelen visas.
   
    ![Fönstret Hantera aviseringar](media/service-set-data-alerts/powerbi-see-alerts.png).
2. Om du vill ändra en avisering, väljer du pilen till vänster om aviseringens namn.
   
    ![pilen bredvid aviseringsnamnet](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. Om du vill ta bort en avisering, väljer du papperskorgen till höger om aviseringens namn.
   
      ![papperskorgikonen har valts](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>På inställningsmenyn för Power BI
1. Välj kugghjulsikonen från menyfältet i Power BI.
   
    ![kugghjulsikonen](media/service-set-data-alerts/powerbi-gear-icon.png).
2. Välj **Aviseringar** under **Inställningar**.
   
    ![Fliken Aviseringar i fönstret Inställningar](media/service-set-data-alerts/powerbi-alert-settings.png)
3. Härifrån kan du aktivera och inaktivera aviseringar, öppna fönstret **Hantera aviseringar** för att ändra eller ta bort aviseringen.

## <a name="tips-and-troubleshooting"></a>Tips och felsökning
* Aviseringar stöds inte för närvarande för Bing paneler eller kortpaneler med datum-/tidsmått.
* Aviseringar fungerar bara med numeriska datatyper.
* Aviseringar fungerar bara på data som ska uppdateras. De fungerar inte på statiska data.
* Aviseringar fungerar bara på direktöverförda datauppsättningar om du bygger en mätare-KPI/kort för det visuella objektet och fäster det visuella objektet på instrumentpanelen.

## <a name="next-steps"></a>Nästa steg
[Skapa ett Microsoft-flöde som innehåller en datavarning](service-flow-integration.md)    
[Ställa in datavarningar på din mobilenhet](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)    
[Vad är Power BI?](power-bi-overview.md)    
Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

