---
title: Skapa arbetsytor med dina kollegor i Power BI
description: Lär dig hur du skapar arbetsytor, samlingar av instrumentpaneler och rapporter som skapats för att förse din organisation med statistik.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 55f592101954ae5c0724fb5b48fb2571a1bdfc51
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983702"
---
# <a name="create-workspaces-with-your-colleagues-in-power-bi"></a>Skapa arbetsytor med dina kollegor i Power BI

I Power BI kan du skapa *arbetsytor*, platser där du kan samarbeta med kollegor för att skapa och förfina samlingar av instrumentpaneler och rapporter. Sedan paketerar du samlingen tillsammans i *appar* som du kan distribuera till hela organisationen eller till specifika personer eller grupper. 

![Power BI-appar](media/service-create-workspaces/power-bi-apps-left-nav.png)

När du skapar en arbetsyta skapar du en underliggande, associerad Office 365-grupp. All administration för arbetsytor sker i Office 365. Du kan lägga till kollegor till dessa arbetsytor som medlemmar eller administratörer. På arbetsytan kan ni samarbeta kring instrumentpaneler, rapporter och annat innehåll som du planerar att distribuera till en bredare publik. Alla som du lägger till i en apparbetsyta behöver en Power BI Pro-licens. 

**Visste du att?** Power BI har en ny arbetsyta i förhandsversion. I [Organisera arbete i de nya arbetsytorna (förhandsversion)](service-new-workspaces.md) finns information om de nya arbetsytorna. 

## <a name="video-apps-and-app-workspaces"></a>Video: Appar och apparbetsytor
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-an-app-workspace-based-on-an-office-365-group"></a>Skapa en apparbetsyta baserat på en Office 365-grupp

När du skapar en apparbetsyta byggs den på en Office 365-grupp.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

När du först skapar arbetsytan kan du behöva vänta i ungefär en timme för att den ska spridas till Office 365. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Lägga till en bild i din Office 365-apparbetsyta (valfritt)
Som standard skapar Power BI en liten färgad cirkel för din app med appens initialer. Men du kan också anpassa den med en bild. Om du vill lägga till en bild måste du ha en Exchange Online-licens.

1. Välj **Arbetsytor**, välj ellipsen (...) bredvid namnet på arbetsytan och sedan **Medlemmar**. 
   
     ![Välja medlemmar till arbetsytan](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    Office 365 Outlook-kontot för arbetsytan öppnas i ett nytt webbläsarfönster.
2. När du hovrar över den färgade cirkeln i det övre vänstra hörnet omvandlas den till en pennikon. Välj den.
   
     ![Office 365-pennikon](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Välj pennikonen igen och leta reda på den bild som du vill använda.
   
     ![Välj pennan igen](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

4. Välj **Spara**.
   
     ![Välja Spara](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    Bilden ersätter den färgade cirkeln i Outlook-fönstret i Office 365. 
   
     ![Anpassad bild](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    Om några minuter visas den även i appen i Power BI.
   
     ![Anpassad bild](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Lägga till innehåll i din apparbetsyta

När du har skapat en apparbetsyta är det dags att lägga till innehåll. Det går till precis som att lägga till innehåll på Min arbetsyta, förutom att även andra på arbetsytan kan se och arbeta med det. En stor skillnad är att när du är klar, kan du publicera innehållet som en app. När du visar innehåll i innehållslistan på en apparbetsyta visas apparbetsytans namn som ägare.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Ansluta till tjänster från tredje part på apparbetsytor

Appar tillhandahålls för alla tredjepartstjänster som Power BI stödjer, vilket gör det enkelt att hämta data från de tjänster du använder, till exempel Microsoft Dynamics CRM, Salesforce eller Google Analytics. Du kan publicera organisationsappar för att ge användarna de data de behöver.

I de aktuella arbetsytorna kan du även ansluta med hjälp av organisationsinnehållspaket och innehållspaket från tredje part såsom Microsoft Dynamics CRM, Salesforce eller Google Analytics. Överväg att migrera organisationens innehållspaket till appar.

## <a name="distribute-an-app"></a>Distribuera en app

När innehållet är färdigt kan du välja vilka instrumentpaneler och rapporter som du vill publicera, och sedan publicerar du det som en *app*. Dina medarbetare kan få apparna på ett par olika sätt. Du kan installera dem automatiskt på dina medarbetares Power BI-konton om din Power BI-administratör ger dig behörighet. I annat fall kan de hitta och installera dina appar från Microsoft AppSource, eller så kan du skicka dem en direktlänk. De får uppdateringar automatiskt och du kan styra hur ofta dina data ska uppdateras. Information finns i [Publicera appar med instrumentpaneler och rapporter i Power BI](service-create-distribute-apps.md).

## <a name="power-bi-apps-faq"></a>Vanliga frågor och svar om Power BI-appar

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Hur skiljer sig appar åt från organisationsinnehållspaket?
Appar är utvecklingen av organisationsinnehållspaket. Om du redan har organisationsinnehållspaket, fortsätter de att fungera sida vid sida med appar. Det finns några viktiga skillnader mellan appar och innehållspaket. 

* När företagsanvändare har installerat ett innehållspaket, förlorar det sin grupperade identitet: det är bara en lista över instrumentpaneler och rapporter bland andra instrumentpaneler och rapporter. Appar, å andra sidan, bevarar sin gruppering och identitet även efter installationen. Den här grupperingen gör det lätt för företagsanvändare att fortsätta att gå tillbaka till dem över tid.
* Du kan skapa flera innehållspaket från en arbetsyta, men en app har ett 1:1-förhållande med sin arbetsyta. 
* Med tiden planerar vi att avveckla användningen av organisationsinnehållspaket, så vi rekommenderar att du skapar appar hädanefter.  
* Med den nya förhandsversionen av arbetsytan tar vi de första stegen mot att avveckla innehållspaket för organisationer. Du kan inte använda eller skapa dem i arbetsytor som är i förhandsversion.

Du kan jämföra de två i [Hur skiljer sig de nya apparbetsytorna åt från befintliga apparbetsytor?](service-new-workspaces.md#how-are-the-new-workspaces-different-from-current-workspaces). 

## <a name="next-steps"></a>Nästa steg
* [Installera och använda appar i Power BI](service-create-distribute-apps.md)
- [Skapa de nya arbetsytorna (förhandsversion)](service-create-the-new-workspaces.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
