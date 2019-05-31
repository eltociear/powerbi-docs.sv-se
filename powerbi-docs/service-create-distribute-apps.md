---
title: Publicera en app i Powerbi
description: Lär dig hur du publicerar de nya appar som är samlingar av instrumentpaneler och rapporter med inbyggda navigering.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941546"
---
# <a name="publish-an-app-in-power-bi"></a>Publicera en app i Powerbi

I Power BI kan du skapa officiella paketeras innehåll och sedan distribuera den till en bred publik som en *app*. Du skapar appar i *apparbetsytor* där du kan samarbeta på Power BI-innehåll med dina kollegor. Du kan sedan publicera de slutförda apparna till stora grupper i din organisation. 

![Power BI-appar](media/service-create-distribute-apps/power-bi-new-apps.png)

Dina företagsanvändare behöver ofta flera Power BI-instrumentpaneler och -rapporter för att göra sitt jobb. Med Power BI-appar kan du skapa samlingar av instrumentpaneler och rapporter, och publicera dessa appar till hela organisationen eller till vissa personer eller grupper. För dig som skapare eller administratör av rapporter gör apparna det enklare att hantera behörigheter för dessa samlingar.

Företagsanvändarna får dina appar på ett par olika sätt:

- Användarna kan söka efter och installera appen från Microsoft AppSource
- Du kan skicka dem en direktlänk.
- Du kan installera den automatiskt på dina medarbetares Power BI-konton om din Power BI-administratör ger dig behörighet.

Du kan skapa appen med en egen inbyggd navigering, så att användarna lätt kan hitta vägen runt ditt innehåll. De kan inte ändra innehållet i appen. De kan interagera med den i Power BI-tjänsten eller någon av de mobila apparna- – filtrera, markera och sortera data på egen hand. De får uppdateringar automatiskt och du kan styra hur ofta dina data ska uppdateras. Läs mer om [app-upplevelsen för företagsanvändare](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licenser för appar
Om du vill skapa eller uppdatera en app, behöver du en Power BI Pro-licens. För app *konsumenter*, det finns två alternativ.

* Alternativ 1: Alla företagsanvändare behöver **Power BI Pro**-licenser för att kunna visa din app. 
* Alternativ 2: Om din app-arbetsyta finns i en Power BI Premium-kapacitet, kan kostnadsfria användare i din organisation visa appinnehåll. Läs [Vad är Power BI Premium?](service-premium.md) för mer information.

## <a name="publish-your-app"></a>Publicera appen
När instrumentpanelerna och rapporterna på din arbetsyta är redo kan du välja vilka instrumentpaneler och rapporter som du vill publicera, och sedan publicerar du dem som en app. 

1. Bestäm vilka instrumentpaneler och rapporter som du vill i arbetsytans listvy **ingår i appen**.

     ![Välja instrumentpanelen för publicering](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Om du väljer att inte inkludera en rapport som har en relaterad instrumentpanel, visas en varning bredvid rapporten. Du kan fortfarande publicera appen, men den relaterade instrumentpanelen kommer inte ha panelerna från rapporten.

     ![Varning om relaterad instrumentpanel](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Välj den **publicera app** knappen i det övre högra hörnet att starta processen med att skapa och publicera en app från arbetsytan.
   
     ![Publicera app](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. På **installationsprogrammet**, Fyll i namn och beskrivning som hjälper användare att hitta appen. Du kan ange en Temafärg du anpassar den. Du kan också lägga till en länk till en supportwebbplats.
   
     ![Skapa din app](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. På **navigering**, väljer du innehållet som ska publiceras som en del av appen. Därefter lägger du till app-navigering, för att organisera innehållet i avsnitt. Se [utforma navigeringsupplevelsen för din app](#design-the-navigation-experience-for-your-app) i den här artikeln för information.
   
     ![App-navigering](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. På **åtkomst**, bestämma vem som har åtkomst till appen. 
    - I [klassiska arbetsytor](service-create-workspaces.md): alla i din organisation, specifika personer eller säkerhetsgrupper i Azure Active Directory (AAD).
    - I den [nya upplevelse arbetsytor](service-create-the-new-workspaces.md): specifika personer, AAD-säkerhetsgrupper och distributionslistor och Office 365-grupper.

6. Om du har behörighet kan du installera appen automatiskt för mottagarna. En Power BI-administratör kan aktivera den här inställningen i Power BI-administratörsportalen. Läs mer om [automatiskt installera en app](#automatically-install-apps-for-end-users) i den här artikeln.

     ![App-behörigheter](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. När du väljer **publicera app**, visas ett meddelande som bekräftar att den är redo att publicera. I den **dela den här appen** dialogrutan kan du kopiera den URL som är en direktlänk till den här appen.
   
     ![Slutföra appen](media/service-create-distribute-apps/power-bi-apps-success.png)

Du kan skicka en direktlänk till personerna som du har delat den med, eller de kan hitta din app på fliken appar genom att gå till **ladda ned och utforska fler appar från AppSource**. Läs mer om [app-upplevelsen för företagsanvändare](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Ändra en publicerad app
När du har publicerat en app kan du vilja ändra eller uppdatera den. Det är enkelt att uppdatera den om du är administratör eller medlem i den nya apparbetsytan. 

1. Öppna den app-arbetsyta som motsvarar appen. 
   
     ![Öppna arbetsyta](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Ändra instrumentpaneler eller rapporter.
 
     Apparbetsytan är ditt mellanlagringsområde så att ändringarna inte börjar gälla i appen förrän du gör en ny publicering. På så sätt kan du göra ändringar utan att påverka de publicerade apparna.  
 
    > [!IMPORTANT]
    > Om du tar bort en rapport och uppdatera appen, även om du lägger till rapporten tillbaka till appen, förlorar dina appkonsumenter alla anpassningar bokmärken, kommentarer, t.ex.  
 
3. Gå tillbaka till app-arbetsytans lista över innehåll och markera **uppdatera app** i det övre högra hörnet.
   
1. Uppdatera **installationsprogrammet**, **navigering**, och **behörigheter**, om du behöver och välj sedan **uppdatera app**.
   
De personer som du har publicerat appen för ser automatiskt den uppdaterade versionen av appen. 

## <a name="design-the-navigation-experience-for-your-app"></a>Utforma navigeringsupplevelsen för din app
Den **ny navigering builder** alternativet kan du skapa en anpassad navigeringen för din app. Anpassad navigering gör det enklare för användarna att hitta och använda innehåll i appen. Befintliga appar har det här alternativet inaktiverat och alternativet för den nya appar som standard.

När alternativet är inaktiverat, kan du välja den **applandningssida** antingen vara **specifikt innehåll**, till exempel en instrumentpanel eller rapport eller välj **ingen** att visa en grundläggande lista över innehåll för användaren.

När du aktiverar **ny navigering builder**, du kan utforma en anpassad navigering. Som standard visas alla rapporter, instrumentpaneler och Excel-arbetsböcker som du inkluderade i din app som en platt lista. 

![App-navigering](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Du kan anpassa app-navigering av ytterligare:
* Ändra ordningen på elementen genom att använda / nedåtpilarna. 
* Byta namn på objekt i den **rapportera information om**, **instrumentpanelen information**, och **arbetsboksinformation**.
* Dölja vissa objekt från navigeringen.
* Med hjälp av den **New** möjlighet att lägga till **avsnitt** till gruppen relaterat innehåll.
* Med hjälp av den **New** möjlighet att lägga till en **länk** till en extern resurs till det vänstra navigeringsfönstret. 

När du lägger till en **länk**i **information om** du där länken öppnas. Som standard länkar öppnas i den **aktuella fliken**, men du kan välja **ny flik**, eller **innehållsområde**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Att tänka på när det nya navigering builder alternativet
Här följer allmänna saker att tänka på när du använder den nya navigeringen builder:
* Rapportsidor visas som ett expanderbart avsnitt i området för app-navigering
* Om du stänga av den nya navigeringen builder och sedan publicera eller uppdatera din app kan förlora du anpassningar som du har gjort. Till exempel försvinner avsnitt, ordning, länkar och anpassade namn för navigeringsobjekt alla.

När du lägger till länkar till din app-navigering och välja alternativet innehållsområde:
* Se till att länken kan bäddas in. Vissa tjänster blockera inbäddning för sitt innehåll i tredje parters webbplatser som Power BI.
* Bädda in Power BI-tjänsts innehåll som rapporter eller instrumentpaneler i andra arbetsytor stöds inte. 
* Bädda in Power BI Report Server innehållet via dess ursprungliga bädda in URL: en innehåll från en on premises-distribution. Följ stegen i [skapar Power BI-Rapportserver](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) att hämta Webbadress. Tänk på att tillämpa regler för vanlig autentisering, så ser innehållet kräver en VPN-anslutning till en lokal server. 
* En säkerhetsvarning visas överst i det inbäddade innehållet att visa innehållet finns inte i Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Installera appar automatiskt för slutanvändare
Om en administratör ger dig behörighet, kan du installera appar automatiskt, *push-överföra* dem till slutanvändare. Den här push-funktionen gör det enklare att distribuera rätt appar till rätt personer eller grupper. Appen visas automatiskt i innehållslistan för appar för dina slutanvändare. De har inte att hitta det från Microsoft AppSource eller följa en installationslänk. Se hur administratörer aktivera [pusha appar till slutanvändare](service-admin-portal.md#push-apps-to-end-users) i Power BI admin portal artikeln.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Så här skickar du en app automatiskt för slutanvändare
När administratören har tilldelat dig behörigheter får du ett nytt alternativ för att **installera appen automatiskt**. När du markera kryssrutan och välj **publicera app** (eller **uppdatera app**), pushas appen till alla användare eller grupper som angetts i den **behörigheter** i appen på **Åtkomst** fliken.

![Aktivera funktionen för att pusha appar](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Hur användare får de appar som du har överfört till dem.
När du har överfört en app, visas den i listan över sina appar automatiskt. På så sätt kan bestämma du vilka appar den specifika användare eller arbetsroller i din organisation behöver ha åtkomst till.

![Aktivera funktionen för att pusha appar](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Överväganden för att installera appar automatiskt
Här är saker som du bör ha i åtanke när du pushar appar till slutanvändare:

* Det kan ta tid att installera en app automatiskt till användare. De flesta appar installeras omedelbart för användare, men skicka appar kan ta tid.  Det beror på antalet objekt i appen och hur många personer som tilldelas åtkomst. Vi rekommenderar att pusha appar efter arbetstid, när det finns gott om tid innan användarna behöver dem. Verifiera med flera användare innan du meddelar många om apparnas tillgänglighet.

* Uppdatera webbläsaren. Innan den pushade appen visas i applistan kan det hända att användarna måste uppdatera, eller stänga och öppna webbläsaren igen.

* Om användarna inte omedelbart ser appen i listan över appar, bör de uppdatera eller stänga och öppna webbläsaren igen.

* Försök att inte överväldiga användarna. Pusha inte för många appar så att användarna uppfattar det som att de förinstallerade apparna är användbara för dem. Det är bäst att kontrollera vem som kan pusha appar till slutanvändarna så att tidsaspekten kan samordnas. Upprätta en kontaktpunkt för att hämta appar i din organisation som pushats till slutanvändarna.

* Gästanvändare som inte har godkänt en inbjudan hämta inte appar som installeras automatiskt för dessa.  

## <a name="unpublish-an-app"></a>Ta bort en app
Alla medlemmar i en app-arbetsyta kan ta bort appen.

>[!IMPORTANT]
>När du ta bort en app, förlorar app-användare sina anpassningar. De förlora alla personliga bokmärken, kommentarer eller prenumerationer som är associerad med innehållet i appen. Ta endast bort en app om du behöver ta bort den.
> 
> 

* I en app-arbetsyta väljer du ellipsen ( **...** ) i det övre högra hörnet > **Ta bort appen**.
  
     ![Ta bort appen](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Den här åtgärden avinstallerar appen för alla som du har publicerat den till och de har inte längre åtkomst till den. Varken app-arbetsytan eller dess innehåll tas bort.

## <a name="view-your-published-app"></a>Visa din publicerade app

När dina appkonsumenter öppnar din app, visas det navigeringsfönstret som du skapade i stället för standard Power BI vänstra navigeringsfönstret. App-navigering visar en lista över rapporter och instrumentpaneler i avsnitten som du har definierat. Dessutom visas de olika sidorna i varje rapport snarare som precis rapportens namn.

![App med navigering](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Nästa steg
* [Skapa en apparbetsyta](service-create-workspaces.md)
* [Installera och använda appar i Power BI](consumer/end-user-apps.md)
* [Power BI-appar för externa tjänster](service-connect-to-services.md)
* [Power BI-administratörsportalen](https://docs.microsoft.com/power-bi/service-admin-portal)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
