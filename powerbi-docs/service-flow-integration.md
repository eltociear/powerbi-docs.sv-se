---
title: "Självstudier: Power BI-integrering med Microsoft Flow"
description: "Lär dig mer om att skapa flöden som utlösts av Power BI-datavarningar."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: YhmNstC39Mw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/30/2017
ms.author: mihart
ms.openlocfilehash: efab2e6be1d376a0da70c13bb66144ba34afa58c
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2017
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow och Power BI

[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) är ett SaaS-erbjudande för automatisering av arbetsflöden i det växande antalet program och SaaS-tjänster som användare i verksamheten förlitar sig på. Du kan använda Flow för att automatisera uppgifter genom att integrera dina favorit-appar och -tjänster (inklusive Power BI) om du vill få meddelanden, synkronisera filer, samla in data med mera. Återkommande uppgifter blir enkelt med automatisering av arbetsflödet.

[Kom igång med Flow nu.](https://flow.microsoft.com/documentation/getting-started)

Titta på när Sirui skapar ett flöde som skickar ett detaljerat e-postmeddelande till kollegor när en Power BI-avisering utlöses. Prova sedan själv genom att följa de stegvisa anvisningarna under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Skapa ett flöde som utlöses av en avisering för Power BI-data
Den här kursen visar hur du skapar två olika flöden; ett från en mall och ett från grunden. För att följa instruktionerna, [skapa en datavarning i Power BI](service-set-data-alerts.md) och [registrera dig för Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup) (det är gratis!).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Skapa ett flöde som använder Power BI – från en mall
I den här uppgiften använder vi en mall för att skapa ett enkelt flöde som utlöses av en Power BI-datavarning (meddelande).

1. Logga in på Microsoft Flow (flow.microsoft.com).
2. Välj **Mina flöden**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Välj **Skapa från mall**.
   
    ![](media/service-flow-integration/power-bi-template.png)
4. Använd sökrutan för att hitta Power BI-mallar och välj **Skicka ett meddelande till en Slack-kanal när en Power BI-datavarning utlöses**.
   
    ![](media/service-flow-integration/power-bi-template2.png)
5. Välj **Använd den här mallen**.
   
   ![](media/service-flow-integration/power-bi-use-template.png)
6. Om du uppmanas, anslut till Slack och Power BI genom att välja **Logga in** och följ sedan anvisningarna. En grön bockmarkering visar att du har loggat in.  När du har bekräftat dina anslutningar, välj **Fortsätt**.
   
   ![](media/service-flow-integration/power-bi-flow-signin.png)

### <a name="build-the-flow"></a>Skapa flödet
Den här mallen har en utlösare (Power BI-datavarning för nya OS-medaljer för Irland) och en åtgärd (skicka ett meddelande till Slack). När du markerar ett fält visar flödet dynamiskt innehåll som ska inkluderas.  I det här exemplet har vi inkluderat panelvärdet och panelens URL i meddelandekroppen.

![](media/service-flow-integration/power-bi-flow-template.png)

1. Välj Power BI-datavarning från listrutan med utlösare. Välj **Ny medalj för Irland**. Information om hur du skapar en avisering finns i [Datavarningar i Power BI](service-set-data-alerts.md).
   
   ![](media/service-flow-integration/power-bi-trigger-flow.png)
2. För att skicka till Slack, ange ett kanalnamn och en meddelandetext (du kan också välja det standardmeddelande som Flow skapar). Lägg märke till det dynamiska innehåll som vi har inkluderat i meddelandets textfält.
   
   > [!NOTE]
   > Inkludera ”@” i början av kanalnamnet.  Till exempel om Slack-kanalen heter ”channelA”, anger du ”@channelA” i Flow.
   > 
   > 
   
   ![](media/service-flow-integration/power-bi-flow-slacker.png)
3. När du är klar väljer du **Skapa flödet** eller **Spara flöde**.  Flödet skapas och utvärderas.  Flödet meddelar om några fel påträffas.
4. Om fel hittas, välj **Redigera flödet** åtgärda dem, välj annars **Klar** för att köra det nya flödet.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
5. Öppna ditt Slack-konto om du vill visa meddelandet.  
   
   ![](media/service-flow-integration/power-bi-slack-message.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Skapa ett flöde som använder Power BI – från början (tomt)
I den här uppgiften skapar vi ett enkelt flöde från början som utlöses av en Power BI-datavarning (meddelande).

1. Logga in på Microsoft Flow.
2. Välj **Mina flöden** > **Skapa från början**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Använd sökrutan för att hitta en Power BI-utlösare och välj **Utlös ett flöde med en Power BI-datadriven varning**.

### <a name="build-your-flow"></a>Skapa ditt flöde
1. Välj namnet på aviseringen i listrutan.  Information om hur du skapar en avisering finns i [Datavarningar i Power BI](service-set-data-alerts.md).
   
    ![](media/service-flow-integration/power-bi-totalstores.png)
2. Välj **Nytt steg** > **Lägg till en åtgärd**.
   
   ![](media/service-flow-integration/power-bi-new-step.png)
3. Sök efter **Outlook** och välj **Skapa en händelse**.
   
   ![](media/service-flow-integration/power-bi-create-event.png)
4. Fyll i händelsefälten. När du markerar ett fält visar flödet dynamiskt innehåll som ska inkluderas.
   
   ![](media/service-flow-integration/power-bi-flow-event.png)
5. Välj **Skapa flöde** när du är klar.  Flow sparar och utvärderar flödet. Om det inte finns några fel, välj **Klar** för att köra detta flöde.  Det nya flödet har lagts till på din sida **Mina flöden**.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
6. När flödet utlöses av Power BI-datavarningen, får du ett Outlook-händelsemeddelande som liknar det här.
   
    ![](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Nästa steg
* [Kom igång med Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [Ange datavarningar i Power BI-tjänsten](service-set-data-alerts.md)
* [Ange datavarningar på din iPhone](mobile-set-data-alerts-in-the-mobile-apps.md)
* [Ställ in dataaviseringar i Power BI-mobilappen för Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md)
* Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

