---
title: Skapa och publicera appar med instrumentpaneler och rapporter i Power BI
description: "Här kan du lära dig hur du skapar och publicerar appar som är samlingar av instrumentpaneler och rapporter som skapats för att förse din organisation med statistik."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/16/2018
ms.author: maggies
ms.openlocfilehash: 89c376451199aec0a6f464f3298df44d468f37d2
ms.sourcegitcommit: 259d7689bcb1683d4d63a245a9b02becea072139
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="create-and-publish-apps-with-dashboards-and-reports-in-power-bi"></a>Skapa och publicera appar med instrumentpaneler och rapporter i Power BI

I Power BI kan du skapa *appar* för att samordna relaterade instrumentpaneler och rapporter på en enda plats och sedan publicera dem för stora grupper i organisationen. Du kan också ansluta till [Power BI-appar för externa tjänster](service-connect-to-services.md), som Google Analytics och Microsoft Dynamics CRM.

![Power BI-appar](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Dina företagsanvändare behöver ofta flera Power BI-instrumentpaneler och -rapporter för att göra sitt jobb. Appar samordnar delarna så att de inte behöver komma ihåg namn och platser för alla dessa instrumentpaneler.  

Med Power BI-appar, än så länge i en förhandsversion, kan du skapa samlingar av instrumentpaneler och rapporter och publicera dessa appar till hela organisationen eller till särskilda personer eller grupper. För dig som skapare eller administratör av rapporter gör apparna det enklare att hantera behörigheter för samlingar av instrumentpaneler.

Företagsanvändare installerar de här apparna från Microsoft AppSource, eller så kan du skicka dem en direktlänk. De kan enkelt hitta och gå tillbaka till ditt innehåll eftersom allt finns på samma plats. De får uppdateringar automatiskt och du kan styra hur ofta dina data ska uppdateras. Läs mer om [app-upplevelsen för företagsanvändare](service-install-use-apps.md).

### <a name="apps-and-organizational-content-packs"></a>Appar- och organisationsinnehållspaket
Appar är utvecklingen av organisationsinnehållspaket. Om du redan har organisationsinnehållspaket, fortsätter de att fungera sida vid sida med appar.

Nu när du har en översikt över appar ska vi prata mer om *app-arbetsytor*, platsen där du skapar appar. 

## <a name="video-apps-and-app-workspaces"></a>Video: Appar och app-arbetsytor
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licenser för appar
För att skapa appar måste du ha en licens för Power BI Pro. Det finns två alternativ för dina app-användare.

* Alternativ 1: Alla företagsanvändare behöver **Power BI Pro**-licenser för att kunna visa din app. 
* Alternativ 2: Kostnadsfria användare i din organisation kan visa app-innehåll om din app finns i en Power BI Premium-kapacitet. Läs [Vad är Power BI Premium?](service-premium.md) för mer information.

## <a name="app-workspaces"></a>App-arbetsytor
*App-arbetsytor* är de platser där du skapar appar, så du måste börja med att skapa en app-arbetsyta innan du skapar appen. Om du tidigare har arbetat i en grupparbetsyta i Power BI, kommer app-arbetsytor att kännas bekanta. De är en utveckling av grupparbetsytor – mellanlagringsområden och behållare för innehållet i appen. 

Du kan lägga till kollegor till dessa arbetsytor som medlemmar eller administratörer. Alla medlemmar och administratörer av app-arbetsytan behöver Power BI Pro-licenser. På arbetsytan kan ni samarbeta kring instrumentpaneler, rapporter och annat innehåll som du planerar att publicera till en bredare publik eller hela organisationen. 

När innehållet är färdigt kan du välja vilka instrumentpaneler och rapporter som du vill publicera, och sedan publicerar du appen. Du kan skicka en direktlänk till den bredare målgruppen eller så kan de hitta din app på fliken Appar genom att gå till **Ladda ned och utforska fler appar från AppSource**. Dessa personer kan inte ändra innehållet i appen, men de kan interagera med det i antingen Power BI-tjänsten eller i någon av mobilapparna och kan filtrera, markera och sortera data på egen hand. 

## <a name="create-an-app-workspace"></a>Skapa en app-arbetsyta
[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Den är tom, så nu lägger du till innehåll på den. Observera att du efter att du har skapat arbetsytan, kan behöva vänta i ungefär en timme för att den ska spridas till Office 365. 

Att lägga till innehåll går till precis som att lägga till innehåll på Min arbetsyta, förutom att även andra på arbetsytan kan se och arbeta med det. En stor skillnad är att när du är klar, kan du publicera innehållet som en app. När du befinner dig på app-arbetsytan kan du ladda upp eller ansluta till filer eller ansluta till tjänster från tredje part, precis som på Min arbetsyta. Till exempel:

* [Anslut till tjänster](service-connect-to-services.md) som Microsoft Dynamics CRM, Salesforce eller Google Analytics.
* [Hämta data från filer](service-get-data-from-files.md), till exempel Excel, CSV eller Power BI Desktop-filer (PBIX).

## <a name="add-an-image-to-your-app-optional"></a>Lägga till en bild i appen (valfritt)
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

## <a name="publish-your-app"></a>Publicera appen
När instrumentpanelerna och rapporterna på din app-arbetsyta är klara, publicerar du dem som en app. Kom ihåg att du inte behöver publicera alla rapporter och instrumentpaneler på arbetsytan. Du kan välja att bara publicera de som är klara. 

1. Bestäm vilka instrumentpaneler och rapporter som du vill ska ingå i appen i arbetsytans listvy.

     ![Välja instrumentpanelen för publicering](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Om du väljer att inte publicera en rapport, visas en varning bredvid rapporten och dess relaterade instrumentpanel. Du kan fortfarande publicera appen, men den relaterade instrumentpanelen kommer att sakna panelerna från rapporten.

     ![Varning om relaterad instrumentpanel](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

1. Välj knappen **Publicera app** i det övre högra hörnet för att starta processen med att dela allt innehåll på arbetsytan.
   
     ![Publicera app](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

2. Börja med att fylla i en beskrivning under **Information** som hjälper användare att hitta appen. Du kan ange en bakgrundsfärg för att göra den lite personlig.
   
     ![Information om appar](media/service-create-distribute-apps/power-bi-apps-details.png)

3. Därefter går du till **Innehåll** och tittar på det innehåll som ska publiceras som en del av appen – allt som du har valt på arbetsytan. Du kan också ange en landningssida för appen – den instrumentpanel eller rapport som först visas när någon använder din app. Du kan välja **Ingen**. Då landar de i en lista över allt innehåll i appen. 
   
     ![Appens innehåll](media/service-create-distribute-apps/power-bi-apps-content.png)

4. Till sist bestämmer du under **Åtkomst** vem som ska ha åtkomst till appen: antingen alla i din organisation, specifika personer eller Active Directory-säkerhetsgrupper. 

5. När du väljer **Slutför**, visas ett meddelande som bekräftar att appen är redo för publicering. I dialogrutan som bekräftar slutförandet kan du kopiera URL:en som är en direktlänk till appen och skicka den till dem som du ska dela den med.
   
     ![Slutföra appen](media/service-create-distribute-apps/power-bi-apps-success.png)

De företagsanvändare som du har publicerat appen åt, kan hitta den på olika sätt. Du kan skicka dem en direktlänk till appen eller så kan de söka efter den i Microsoft AppSource, där de kan se alla appar som de kan komma åt. När de därefter går till Appar, kan de se den här appen i listan.

Läs mer om [app-upplevelsen för företagsanvändare](service-install-use-apps.md).

## <a name="change-your-published-app"></a>Ändra en publicerad app
När du har publicerat en app kan du vilja ändra eller uppdatera den. Det är enkelt att uppdatera den om du är administratör eller medlem på app-arbetsytan. 

1. Öppna den app-arbetsyta som motsvarar appen. 
   
     ![Öppna arbetsyta](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Öppna instrumentpanelen eller rapporten. Du ser att du kan göra alla ändringar som du önskar.
   
     App-arbetsytan är ditt mellanlagringsområde så att ändringarna inte skickas i realtid till appen förrän du gör en ny publicering. På så sätt kan du göra ändringar utan att påverka de publicerade apparna.  
 
1. Gå tillbaka till app-arbetsytans lista över innehåll och markera **Uppdatera app**.
   
     ![Uppdatera app-knappen](media/service-create-distribute-apps/power-bi-app-update-button.png)
4. Uppdatera **Information**, **Innehåll** och **Åtkomst** om du behöver och välj sedan **Uppdatera app**.
   
     ![Uppdatera app-knappen](media/service-create-distribute-apps/power-bi-app-update-complete.png)

De personer som du har publicerat appen för ser automatiskt den uppdaterade versionen av appen. 

## <a name="unpublish-an-app"></a>Ta bort en app
Alla medlemmar i en app-arbetsyta kan ta bort appen.

* I en app-arbetsyta väljer du ellipsen (**...** ) i det övre högra hörnet > **Ta bort appen**.
  
     ![Ta bort appen](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Den här åtgärden avinstallerar appen för alla som du har publicerat den till och de har inte längre åtkomst till den. Varken app-arbetsytan eller dess innehåll tas bort.

## <a name="power-bi-apps-faq"></a>Vanliga frågor och svar om Power BI-appar
### <a name="how-are-app-workspaces-different-from-group-workspaces"></a>Hur skiljer sig app-arbetsytor åt från grupparbetsytor?
Med den här versionen har vi döpt om alla grupparbetsytor till app-arbetsytor. Du kan publicera en app från vilken som helst av dessa arbetsytor. Funktionaliteten förblir oftast likvärdig med den hos grupparbetsytor. De kommande månaderna planerar vi följande förbättringar av app-arbetsytor: 

* Att skapa app-arbetsytor kommer inte att skapa motsvarande entiteter i Office 365, på samma sätt som för grupparbetsytor. Därför kan du skapa valfritt antal app-arbetsytor utan att oroa dig för att olika Office 365-grupper skapas i bakgrunden (du kan fortfarande använda en Office 365-grupps OneDrive för företag för att lagra dina filer). 
* Idag kan du bara lägga till enskilda personer till medlems- och administratörslistor. Snart kommer du att kunna lägga till flera AD-säkerhetsgrupper eller moderna grupper i listorna för enklare hantering.  

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Hur skiljer sig appar åt från organisationsinnehållspaket?
Appar är en utveckling och förenkling av innehållspaket med några viktiga skillnader. 

* När företagsanvändare har installerat ett innehållspaket, förlorar det sin grupperade identitet: det är bara en lista över instrumentpaneler och rapporter bland andra instrumentpaneler och rapporter. Appar, å andra sidan, bevarar sin gruppering och identitet även efter installationen. Det gör det lätt för företagsanvändare att fortsätta att gå tillbaka till dem över tid.  
* Du kan skapa flera innehållspaket från en arbetsyta, men en app har ett 1:1-förhållande med sin arbetsyta. Vi tror att detta medför att appar blir lättare att förstå och hantera på lång sikt. Mer information om hur vi planerar att förbättra det här området finns i översiktsavsnittet i Power BI-bloggen. 
* Med tiden planerar vi att avveckla användningen av organisationsinnehållspaket, så vi rekommenderar att du skapar appar hädanefter.  

### <a name="what-about-read-only-members-in-groups"></a>Hur fungerar det med skrivskyddade medlemmar i grupper?
Du kan lägga till skrivskyddade medlemmar i grupper som bara kan visa innehållet. Det huvudsakliga problemet med den här metoden är att du inte kan lägga till säkerhetsgrupper som medlemmar. Med appar kan man publicera en skrivskyddad version av app-arbetsytan för stora målgrupper, inklusive säkerhetsgrupper. Du kan mellanlagra ändringar till instrumentpaneler och rapporter i appen utan att påverka slutanvändarna. Vi rekommenderar användning av appar på det här sättet i framtiden. Vi planerar att även avveckla användningen av skrivskyddade medlemmar för arbetsytor på längre sikt.  

## <a name="next-steps"></a>Nästa steg
* [Installera och använda appar i Power BI](service-install-use-apps.md)
* [Power BI-appar för externa tjänster](service-connect-to-services.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

