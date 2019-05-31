---
title: Skapa klassiska arbetsytor i Power BI
description: Lär dig mer om att skapa arbetsytor, samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter som skapats för att leverera nyckelvärden för din organisation.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: dcf9b8befabfec98fcae154e6276f8e698b3ddc2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61151047"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Skapa klassiska arbetsytor i Power BI

I Power BI, kan du skapa *arbetsytor*, placerar för att samarbeta med kollegor för att skapa och förfina samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter. Och sedan samlingen kan slå samman i *appar* som du kan distribuera till hela organisationen eller till specifika personer eller grupper. 

**Visste du att?** Powerbi erbjuder en ny arbetsyta-upplevelse, som nu är standard. Läs [organisera arbete i nya arbetsyteförhandsversionen](service-new-workspaces.md) mer information om nya arbetsytor. 

När du skapar en klassiska arbetsyta, skapar du en underliggande, associerade Office 365-grupp. All administration för arbetsytor sker i Office 365. Du kan lägga till kollegor till dessa arbetsytor som medlemmar eller administratörer. På arbetsytan kan ni samarbeta kring instrumentpaneler, rapporter och annat innehåll som du planerar att distribuera till en bredare publik. Alla som du lägger till i en apparbetsyta behöver en Power BI Pro-licens. 

## <a name="video-apps-and-app-workspaces"></a>Video: Appar och apparbetsytor
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Skapa en klassisk app-arbetsyta som är baserat på en Office 365-grupp

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

     Avbildningar kan vara .png, .jpg eller BMP-filer. Bildernas storlek kan vara stora, upp till 3 MB. 

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

Om du vill distribuera officiella innehåll till en stor publik i din organisation kan du publicera en app från din arbetsyta.  När innehållet är klar kan du välja vilka instrumentpaneler och rapporter som du vill publicera och sedan publicera den som en *app*. Du kan skapa en app från varje arbetsyta.

Listan över appar i det vänstra navigeringsfönstret visar alla appar som du har installerat. Dina medarbetare kan få appen på ett par olika sätt. 
- Användarna kan söka efter och installera appen från Microsoft AppSource
- Du kan skicka dem en direktlänk. 
- Du kan installera den automatiskt på dina medarbetares Power BI-konton om din Power BI-administratör ger dig behörighet. 

Användarna ser uppdaterade appen innehåll automatiskt när du har publicerat en uppdatering från din arbetsyta. Du kan styra hur ofta data uppdateras genom att ange uppdateringsschemat i de datauppsättningar som används av appinnehåll i din arbetsyta. Se [publicera en app från de nya arbetsytorna i Power BI](service-create-distribute-apps.md) mer information.

## <a name="power-bi-classic-apps-faq"></a>Power BI-klassiska appar vanliga frågor och svar

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
