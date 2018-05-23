---
title: Dela Power BI-instrumentpaneler och -rapporter med kollegor och andra
description: Hur du delar Power BI-instrumentpaneler och -rapporter med dina kollegor i och utanför din organisation, och vad du behöver veta om delning.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: e176f82e106c531410b8e9233b983c6e321bddf4
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="share-your-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Dela Power BI-instrumentpaneler och -rapporter med kollegor och andra
*Dela* är ett bra sätt att ge ett fåtal användare åtkomst till dina instrumentpaneler och rapporter. Power BI erbjuder också [flera andra sätt att samarbeta och distribuera instrumentpaneler och rapporter på](service-how-to-collaborate-distribute-dashboards-reports.md).

![Dela ikonen i en lista över favoritinstrumentpaneler](media/service-share-dashboards/power-bi-share-dash-report-favorites.png)

Med delning, vare sig om du delar innehåll i eller utanför din organisation, behöver du en [Power BI Pro-licens](service-free-vs-pro.md). Mottagarna behöver också Power BI Pro-licenser eller så måste innehållet finnas i en [Premium-kapacitet](service-premium.md). 

Du kan dela instrumentpaneler och rapporter från de flesta platser i Power BI-tjänsten: dina favoriter, senaste, delade med mig (om ägaren tillåter det), min arbetsyta eller andra arbetsytor. När du delar en instrumentpanel eller en rapport, kan de som du delar med se den och interagera med den, men inte redigera den. De ser samma data som visas på instrumentpanelen eller i rapporterna, såvida inte [säkerhet på radnivå (RLS)](service-admin-rls.md) tillämpas. De medarbetare som du delar med kan också dela den med sina medarbetare, om du tillåter detta. Personerna utanför organisationen kan också visa och interagera med instrumentpanelen eller rapporten, men de kan inte dela den. 

Du kan också [dela en instrumentpanel från vilken Power BI-mobilapp du vill](mobile-share-dashboard-from-the-mobile-apps.md). Du kan dela instrumentpaneler från Power BI-tjänsten och Power BI-appar, men inte från Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Video: Dela en instrumentpanel
Se hur Amanda delar sin instrumentpanel med dina kollegor i och utanför företaget. Prova sedan själv genom att följa de stegvisa anvisningarna under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Dela en instrumentpanel eller en rapport

1. Välj i en lista över instrumentpaneler och rapporter, eller i en öppen instrumentpanel eller rapport välj **Resurs** ![Resursikon](media/service-share-dashboards/power-bi-share-icon.png).

1. Ange fullständiga e-postadresser för enskilda användare, distributionsgrupper och säkerhetsgrupper i den översta rutan. Du kan inte dela med dynamiska distributionslistor. 
   
   Du kan dela med användare vars postadresser finns utanför organisationen, men en varning visas.
   
   ![Varning om att dela externt](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
3. Lägg till ett meddelande om du vill. Det är valfritt.
4. Om du vill att dina medarbetare ska kunna dela innehåll med andra, så markera **Tillåt mottagarna att dela din instrumentpanel/rapport**.
   
   Att låta andra dela kallas *dela om*. Om du låter dem göra det, kan de dela om från Power BI-tjänsten och de mobila apparna, eller vidarebefordra e-postinbjudan till andra i din organisation. Inbjudan upphör att gälla efter en månad. Personer utanför organisationen kan inte dela om. Som ägare av innehållet kan du inaktivera delning igen eller återkalla delning igen på individuell grund. Se [Sluta dela eller hindra andra från att dela](service-share-dashboards.md#stop-sharing-or-stop-others-from-sharing), nedan.

5. Välj **Dela.**
   
   ![Välj knappen Dela](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI skickar en e-postinbjudan till enskilda individer, men inte till grupper, med en länk till det delade innehållet. Du ser ett meddelande om att det **Lyckades**. 
   
   När mottagare i din organisation klickar på länken, så lägger Power BI till instrumentpanelen eller rapporten på sidan **Delat med mig**. De kan markera namnet för att se allt innehåll som du delar med dem. 
   
   ![Listsidan Delat med mig](media/service-share-dashboards/power-bi-shared-with-me-dashboards-reports.png)
   
   När mottagare utanför organisationen klickar på länken kan de se instrumentpanelen eller rapporten, men inte i den vanliga Power BI-portalen. Mer information finns i [Dela med personer utanför din organisation](service-share-dashboards.md#share-a-dashboard-with-people-outside-your-organization) nedan.

## <a name="who-has-access-to-a-dashboard-or-report-you-shared"></a>Vem har tillgång till en instrumentpanel eller rapport som du delat?
Ibland kan du behöva se vilka personer du har delat med, och se vilka de har delat den med.

1. I listan över instrumentpaneler och rapporter, eller i själva instrumentpanelen eller rapporten, välj **Resurs** ![Resursikon](media/service-share-dashboards/power-bi-share-icon.png). 
2. Välj **Åtkomst** i dialogrutan **Dela instrumentpanel/rapport**.
   
    ![Dialogrutan Dela instrumentpanel, fliken Åtkomst](media/service-share-dashboards/power-bi-share-dialog-access.png)
   
    Personer utanför organisationen listas som **Gäst**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Sluta dela eller hindra andra från att dela
Endast en instrumentpanels eller rapports ägare kan aktivera eller inaktivera omdelning.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Om du inte har skickat delningsinbjudan ännu
* Avmarkera kryssrutan **Tillåt mottagare att dela min instrumentpanel/rapport** längst ned i inbjudan innan du skickar den.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Om du redan har delat instrumentpanelen eller rapporten
1. I listan över instrumentpaneler och rapporter, eller i själva instrumentpanelen eller rapporten, välj **Resurs** ![Resursikon](media/service-share-dashboards/power-bi-share-icon.png). 
2. Välj **Åtkomst** i dialogrutan **Dela instrumentpanel/rapport**.
   
    ![Dialogrutan Dela instrumentpanel, fliken Åtkomst](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Markera ellipsen (**...** ) intill **Läs och dela vidare** och välj:
   
   ![Läs och dela vidare](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Läs** om du vill förhindra den personen från att dela med någon annan.
   * **Ta bort åtkomst** om du vill förhindra personen från att se delat innehåll överhuvudtaget.

4. I dialogrutan **Ta bort åtkomst** bestämmer du om du vill ta bort åtkomsten till relaterat innehåll, till exempel rapporter och datauppsättningar. Om du tar bort objekt med en varningsikon ![Power BI-varningsikon](media/service-share-dashboards/power-bi-warning-icon.png), är det bäst att ta bort relaterat innehåll eftersom det inte kommer att visas korrekt.

## <a name="share-a-dashboard-or-report-with-people-outside-your-organization"></a>Dela en instrumentpanel eller rapport med personer utanför din organisation
När du delar med personer utanför organisationen, får de ett e-postmeddelande med en länk till den delade instrumentpanelen eller rapporten, och de måste logga in till Power BI för att kunna se den. Om de inte har någon Power BI Pro-licens kan de registrera sig för en licens efter att ha klickat på länken.

När de har loggat in visas den delade instrumentpanelen eller rapporten i ett eget webbläsarfönster utan det vänstra navigeringsfönstret, och inte i den vanliga Power BI-portalen. De måste bokmärka länken om du vill ha åtkomst till den här instrumentpanelen eller rapporten i framtiden.

De kan inte redigera något innehåll i den här instrumentpanelen eller rapporten. De kan interagera med diagram och ändra filter eller utsnitt i rapporten, men det går inte att spara ändringarna.

Endast dina direkta mottagare kan se den delade instrumentpanelen eller rapporten. Om du t.ex. skickade e-postmeddelandet till Vicki@contoso.com, så kan endast Vicki se instrumentpanelen. Ingen annan kan se instrumentpanelen, även om de har tillgång till länken, och Vicki måste använda samma e-postadress för att få åtkomst till instrumentpanelen. Om hon loggar med någon annan e-postadress har inte heller hon någon åtkomst till instrumentpanelen.

Personer utanför organisationen kan inte se några data alls om säkerhet på roll- eller radnivå har implementerats på lokala Analysis Services-tabellmodeller.

Om du skickar en länk från en Power BI-mobilapp till personer utanför organisationen, och mottagarna klickar på länken, så öppnas instrumentpanelen i en webbläsare, inte i Power BI-mobilappen.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Saker att tänka på när det gäller att dela instrumentpaneler och rapporter:

* Normalt ser du och dina kollegor samma data på instrumentpanelen eller rapporten. Så om du har behörighet att se mer data än vad de har, så kan de se alla dina data på instrumentpanelen eller rapporten. Men om [säkerhet på radnivå (RLS)](service-admin-rls.md) tillämpas på instrumentpanelens eller rapportens underliggande datauppsättning, då avgör de enskilda användarnas autentiseringsuppgifter vilka data de har åtkomst till.
* Alla som du delar din instrumentpanel med kan se den och interagera med relaterade rapporter i [läsvy](service-reading-view-and-editing-view.md). De kan inte skapa rapporter eller spara ändringar i befintliga rapporter.
* Ingen kan se eller hämta datauppsättningen.
* Alla kan [uppdatera data](refresh-data.md) manuellt.
* Om du använder Office 365 för e-post kan du dela med medlemmar i en distributionsgrupp genom att ange den e-postadress som är kopplad till distributionsgruppen.
* Medarbetare som har samma e-postdomän som du och medarbetare vars domäner är olika men registrerade inom samma klientorganisation kan dela instrumentpanelen med andra. Låt oss t.ex. anta att domänerna contoso.com och contoso2.com har registrerats i samma klientorganisation. Om din e-postadress är konrads@contoso.com, så kan både ravali@contoso.com och gustav@contoso2.com dela, så länge som du har gett dem behörighet att dela.
* Om dina medarbetare redan har åtkomst till en specifik instrumentpanel eller rapport, kan du skicka en direktlänk genom att kopiera webbadressen när du är i instrumentpanelen eller rapporten. Exempel: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* Om dina medarbetare på motsvarande sätt redan har åtkomst till en specifik instrumentpanel, kan du [skicka en direktlänk till den underliggande rapporten](service-share-reports.md). 

## <a name="troubleshoot-sharing"></a>Felsöka delning

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Mina instrumentpanelsmottagare ser en låsikon i en panel eller ett meddelande om ”Behörighet krävs”

De personer som du delar med kan se en låst panel på en instrumentpanel eller ett meddelande om att ”behörighet krävs” när de försöker visa en rapport.

![låst panel i Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

I så fall behöver ge dem behörighet till den underliggande datauppsättningen. Gör så här.

1. Gå till fliken **Datauppsättningar** i listan med innehåll.

1. Välj de tre punkterna (**...** ) bredvid datauppsättningen > **Hantera behörigheter**.

    ![Hantera behörigheter](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

3. Välj **Lägg till användare**.

    ![Välj Lägg till användare](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Ange fullständiga e-postadresser för enskilda användare, distributionsgrupper och säkerhetsgrupper. Du kan inte dela med dynamiska distributionslistor.

    ![Lägg till e-postadresser](media/service-share-dashboards/power-bi-add-user-dataset.png)

5. Välj **Lägg till**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Jag kan inte dela en instrumentpanel eller en rapport

Om du vill dela en instrumentpanel eller rapport, behöver du behörighet att dela det underliggande innehållet – relaterade rapporter och datauppsättningar. Om du ser ett meddelande om att du inte kan dela be rapportskaparen att ge dig behörighet att dela för dessa rapporter och datauppsättningar.


## <a name="next-steps"></a>Nästa steg
* Har du feedback till oss? Gå till [Power BI Community-webbplatsen](https://community.powerbi.com/) med dina förslag.
* [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Dela en filtrerad Power BI-rapport](service-share-reports.md)
* Har du några frågor? [Testa Power BI Community](http://community.powerbi.com/).

