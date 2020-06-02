---
title: Dela Power BI-instrumentpaneler och -rapporter med kollegor och andra
description: Hur du delar Power BI-instrumentpaneler och -rapporter med dina kollegor i och utanför din organisation, och vad du behöver veta om delning.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/26/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d094e3411bd5b8bef9b4a8f488412d903723a703
ms.sourcegitcommit: c1f05254eaf5adb563f8d4f33c299119134c7d1f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83733564"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Dela Power BI-instrumentpaneler och -rapporter med kollegor och andra
*Dela* är ett bra sätt att ge ett fåtal användare åtkomst till dina instrumentpaneler och rapporter. Power BI erbjuder också [flera andra sätt att samarbeta och distribuera instrumentpaneler och rapporter på](service-how-to-collaborate-distribute-dashboards-reports.md).

![Delningsikonen i en lista med instrumentpaneler](media/service-share-dashboards/power-bi-share-new-look.png)

Med delning, vare sig om du delar innehåll i eller utanför din organisation, behöver du en [Power BI Pro-licens](../fundamentals/service-features-license-type.md). Mottagarna behöver också Power BI Pro-licenser, såvida inte innehållet finns i en [Premium-kapacitet](../admin/service-premium-what-is.md). 

Du kan dela instrumentpaneler och rapporter från de flesta platser i Power BI-tjänsten: Favoriter, Senaste, Min arbetsyta och Delat med mig, om ägaren tillåter det. Du kan också dela från andra arbetsytor om du har rollen [administratör, medlem eller deltagare](service-new-workspaces.md#roles-in-the-new-workspaces) i arbetsytan. 

När du delar en instrumentpanel eller en rapport kan de som du delar med se den och interagera med den, men inte redigera den. De ser samma data som visas på instrumentpanelen eller i rapporterna, såvida inte [säkerhet på radnivå (RLS)](../admin/service-admin-rls.md) tillämpas. De medarbetare som du delar med kan också dela den med sina medarbetare, om du tillåter detta. Personerna utanför organisationen kan också visa och interagera med instrumentpanelen eller rapporten, men de kan inte dela den. 

Du kan inte *dela* direkt från Power BI Desktop. Du [publicerar rapporter från Power BI Desktop](../create-reports/desktop-upload-desktop-files.md) till Power BI-tjänsten. Du kan dock [dela en instrumentpanel från Power BI-mobilappar](../consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md).  

## <a name="video-share-a-dashboard"></a>Video: Dela en instrumentpanel
Se hur Amanda delar sin instrumentpanel med kollegor i och utanför företaget. Prova sedan själv genom att följa de stegvisa anvisningarna under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Dela en instrumentpanel eller en rapport

1. I en lista med instrumentpaneler och rapporter, eller i en öppen instrumentpanel eller rapport, väljer du **Dela** ![delningsikon](media/service-share-dashboards/power-bi-share-icon.png).

2. Ange fullständiga e-postadresser för enskilda användare, distributionsgrupper och säkerhetsgrupper i den översta rutan. Du kan inte dela med dynamiska distributionslistor. 
   
   Du kan dela med användare vars postadresser finns utanför organisationen, men en varning visas. Du kan läsa mer om [delning utanför organisationen](#share-a-dashboard-or-report-outside-your-organization) i den här artikeln.
   
   ![Varning om att dela externt](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >Textrutan för indata stöder högst 100 separata användare eller grupper. Om du vill veta hur du kan dela med fler personer kan du läsa [Dela med fler än 100 användare](#share-with-more-than-100-separate-users) i den här artikeln.

3. Lägg till ett meddelande om du vill. Det är valfritt.
4. Om du vill att dina medarbetare ska kunna dela innehåll med andra markerar du **Tillåt mottagarna att dela din instrumentpanel (eller rapport)** .
   
   Att låta andra dela kallas *dela om*. Om du låter dem göra det, kan de dela om från Power BI-tjänsten och de mobila apparna, eller vidarebefordra e-postinbjudan till andra i din organisation. Inbjudan upphör att gälla efter en månad. Personer utanför organisationen kan inte dela om. Som ägare av innehållet kan du inaktivera delning igen eller återkalla delning igen på individuell grund. Se [Avsluta eller ändra delning](#stop-or-change-sharing) i den här artikeln.

5. Om du väljer **Låt användare skapa nytt innehåll från de underliggande datauppsättningarna** kan de skapa egna rapporter i andra arbetsytor baserat på datamängden för instrumentpanelen. Läs mer om hur du [skapar rapporter baserat på datamängder från olika arbetsytor](../connect-data/service-datasets-discover-across-workspaces.md).

1. Välj **Dela.**
   
   ![Välj knappen Dela](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI skickar en e-postinbjudan till enskilda personer, men inte till grupper, med en länk till det delade innehållet. Du ser ett meddelande om att det **Lyckades**. 
   
   När mottagare i din organisation klickar på länken, så lägger Power BI till instrumentpanelen eller rapporten på sidan **Delat med mig**. De kan markera namnet för att se allt innehåll som du delar med dem. 
   
   ![Listsidan Delat med mig](media/service-share-dashboards/power-bi-shared-with-me-new-look.png)
   
   När mottagare utanför organisationen klickar på länken kan de se instrumentpanelen eller rapporten, men inte i den vanliga Power BI-portalen. Du kan läsa mer om [delning med personer utanför organisationen](#share-a-dashboard-or-report-outside-your-organization) i den här artikeln.

## <a name="see-who-has-access-to-a-dashboard-or-report"></a>Se vem som har tillgång till en instrumentpanel eller en rapport
Ibland kan du behöva se vilka personer du har delat med, och se vilka de har delat den med.

1. I listan med instrumentpaneler och rapporter, eller i själva instrumentpanelen eller rapporten, väljer du **Dela** ![delningsikon](media/service-share-dashboards/power-bi-share-icon.png). 
2. I dialogrutan **Dela instrumentpanel** eller **Dela rapport** väljer du **Åtkomst**.
   
    ![Dialogrutan Dela instrumentpanel, fliken Åtkomst](media/service-share-dashboards/power-bi-share-dialog-access.png)

    Personer utanför organisationen listas som **Gäst**.

    I den här vyn kan du [sluta dela eller ändra delningsbehörigheter](#stop-or-change-sharing). 

## <a name="share-a-dashboard-or-report-outside-your-organization"></a>Dela en instrumentpanel eller en rapport utanför din organisation
När du delar med personer utanför organisationen får de ett e-postmeddelande med en länk till den delade instrumentpanelen eller rapporten. De måste logga in på Power BI för att se vad du har delat. Om de inte har någon Power BI Pro-licens kan de registrera sig för en licens efter att ha klickat på länken.

När de har loggat in visas den delade instrumentpanelen eller rapporten i ett eget webbläsarfönster, inte i den vanliga Power BI-portalen. För att komma åt den här instrumentpanelen eller rapporten senare behöver de lägga till länken som bokmärke.

De kan inte redigera något innehåll i den här instrumentpanelen eller rapporten. De kan interagera med diagram och ändra filter eller utsnitt, men kan inte spara ändringarna. 

Endast dina direkta mottagare kan se den delade instrumentpanelen eller rapporten. Om du t.ex. skickade e-postmeddelandet till Vicki@contoso.com, så kan endast Vicki se instrumentpanelen. Ingen annan kan se instrumentpanelen, även om Vicki vidarebefordrar länken till dem. Vicki måste använda samma e-postadress för att komma åt den. Om Vicki loggar in med någon annan e-postadress får hon inte åtkomst till instrumentpanelen.

Personer utanför organisationen kan inte se några data alls om säkerhet på roll- eller radnivå har implementerats på lokala Analysis Services-tabellmodeller.

Använd en säkerhetsgrupp, inte en distributionsgrupp, när du ska dela med en grupp som innehåller personer med externa e-postadresser. Personer med externa e-postmeddelanden i en distributionsgrupp kan inte se innehållet du delar, såvida de inte är gästanvändare i Azure Active Directory (Azure AD) B2B. Läs mer om [gästanvändare i Azure AD B2B](../admin/service-admin-azure-ad-b2b.md).

Om du skickar en länk från en Power BI-mobilapp till personer utanför organisationen öppnas instrumentpanelen i en webbläsare, inte i Power BI-mobilappen, om de klickar på länken.

### <a name="allow-external-users-to-edit-content"></a>Tillåt att externa användare redigerar innehåll

Power BI-administratörer kan tillåta externa gästanvändare att redigera och hantera innehåll i organisationen. I så fall kommer dina externa användare inte att ha upplevelsen för enbart förbrukning. De kan redigera och hantera innehåll i din organisation. Läs mer om att [distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B](../admin/service-admin-azure-ad-b2b.md).

## <a name="stop-or-change-sharing"></a>Avsluta eller ändra delning
Endast en instrumentpanels eller rapports ägare kan aktivera eller inaktivera omdelning.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Om du inte har skickat delningsinbjudan ännu
* Avmarkera kryssrutan **Tillåt mottagare att dela min instrumentpanel (eller rapport)** längst ned i inbjudan innan du skickar den.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Om du redan har delat instrumentpanelen eller rapporten
1. I listan med instrumentpaneler och rapporter, eller i själva instrumentpanelen eller rapporten, väljer du **Dela** ![delningsikon](media/service-share-dashboards/power-bi-share-icon.png). 
2. I dialogrutan **Dela instrumentpanel** eller **Dela rapport** väljer du **Åtkomst**.
   
    ![Dialogrutan Dela instrumentpanel, fliken Åtkomst](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Markera ellipsen ( **...** ) intill **Läs och dela vidare** och välj:
   
   ![Läs och dela vidare](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Läs** om du vill förhindra den personen från att dela med någon annan.
   * **Ta bort åtkomst** om du vill förhindra personen från att se delat innehåll överhuvudtaget.

4. I dialogrutan **Ta bort åtkomst** bestämmer du om du även vill ta bort åtkomsten till relaterat innehåll, till exempel rapporter och datamängder. Om du tar bort objekt med en varningsikon ![Power BI-varningsikon](media/service-share-dashboards/power-bi-warning-icon.png), är det bäst att även ta bort relaterat innehåll. Annars visas det inte korrekt.

    ![Dialogruta med Power BI-delningsvarning](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Saker att tänka på när det gäller att dela instrumentpaneler och rapporter:

* Normalt ser du och dina kollegor samma data på instrumentpanelen eller rapporten. Så om du har behörighet att se mer data än vad de har, så kan de se alla dina data på instrumentpanelen eller rapporten. Men om [säkerhet på radnivå (RLS)](../admin/service-admin-rls.md) tillämpas på instrumentpanelens eller rapportens underliggande datauppsättning, då avgör varje enskild persons autentiseringsuppgifter vilka data de har åtkomst till.
* Alla som du delar din instrumentpanel med kan se den och interagera med relaterade rapporter i [läsvyn](../consumer/end-user-reading-view.md#reading-view). De kan i allmänhet inte skapa rapporter eller spara ändringar i befintliga rapporter. Men om du väljer **Låt användare skapa nytt innehåll från de underliggande datauppsättningarna** kan de skapa egna rapporter i andra arbetsytor baserat på datamängden för instrumentpanelen eller rapporten.
* Ingen kan se eller hämta datamängden, men de kan komma åt den direkt med hjälp av funktionen Analysera i Excel. En administratör kan begränsa möjligheten att använda Analysera i Excel för alla användare i en grupp. Begränsningen gäller dock för alla användare i gruppen och för varje arbetsyta som gruppen tillhör.
* Alla kan [uppdatera data](../connect-data/refresh-data.md) manuellt.
* Om du använder Microsoft 365 för e-post kan du dela med medlemmar i en distributionsgrupp genom att ange den e-postadress som är kopplad till distributionsgruppen.
* Medarbetare som har samma e-postdomän som du, och medarbetare med en annan domän men som är registrerade inom samma klientorganisation, kan dela instrumentpanelen med andra. Låt oss t.ex. anta att domänerna contoso.com och contoso2.com har registrerats i samma klientorganisation och din e-postadress är konrads@contoso.com. Både ravali@contoso.com och gustav@contoso2.com kan dela din instrumentpanel, så länge som du ger dem behörighet att dela.
* Om dina medarbetare redan har åtkomst till en specifik instrumentpanel eller rapport kan du skicka en direktlänk genom att kopiera URL:en när du är på instrumentpanelen eller i rapporten. Exempel: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`.
* Om dina medarbetare på motsvarande sätt redan har åtkomst till en specifik instrumentpanel kan du [skicka en direktlänk till den underliggande rapporten](service-share-reports.md). 

### <a name="share-with-more-than-100-separate-users"></a>Dela med fler än 100 separata användare

Du kan dela med högst 100 användare eller grupper i en enda delningsåtgärd. Du kan dock ge mer än 500 användare åtkomst till ett objekt. Här följer några förslag:

- Dela flera gånger genom att ange användarna individuellt.
- Dela med en användargrupp som innehåller alla användare. 
- Skapa rapporten eller instrumentpanelen i en arbetsyta och skapa sedan en app från arbetsytan. Du kan dela appen med många fler personer. Läs mer om att [publicera appar i Power BI](service-create-distribute-apps.md).

## <a name="troubleshoot-sharing"></a>Felsöka delning

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Mina instrumentpanelsmottagare ser en låsikon i en panel eller ett meddelande om ”Behörighet krävs”

De personer som du delar med kan se en låst panel på en instrumentpanel eller ett meddelande om att ”behörighet krävs” när de försöker visa en rapport.

![låst panel i Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

I så fall behöver ge dem behörighet till den underliggande datauppsättningen.

1. Gå till fliken **Datauppsättningar** i listan med innehåll.

1. Välj ellipsen ( **...** ) intill datamängden och välj sedan **Hantera behörigheter**.

    ![Hantera behörigheter](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Välj **Lägg till användare**.

    ![Välj Lägg till användare](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Ange fullständiga e-postadresser för enskilda användare, distributionsgrupper och säkerhetsgrupper. Du kan inte dela med dynamiska distributionslistor.

    ![Lägg till e-postadresser](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Välj **Lägg till**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Jag kan inte dela en instrumentpanel eller en rapport

Om du vill dela en instrumentpanel eller rapport behöver du behörighet att dela det underliggande innehållet, det vill säga relaterade rapporter och datamängder. Om du ser ett meddelande om att du inte kan dela ber du rapportskaparen att ge dig behörighet att dela vidare för dessa rapporter och datamängder.

![Meddelande om att det inte går att dela](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Nästa steg

* [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Dela en filtrerad Power BI-rapport](service-share-reports.md)
* Har du några frågor? [Prova Power BI Community](https://community.powerbi.com/)
