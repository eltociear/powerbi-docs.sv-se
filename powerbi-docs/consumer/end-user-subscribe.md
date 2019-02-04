---
title: Prenumerera på rapporter och instrumentpaneler
description: Lär dig hur du ordnar en prenumeration åt dig och dina kollegor på en ögonblicksbild via e-post av en Power BI-rapport eller instrumentpanel.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2019
LocalizationGroup: Common tasks
ms.openlocfilehash: a35067af531f6da29edef7638fc9a743c948b8ce
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430267"
---
# <a name="subscribe-to-a-report-or-dashboard-in-power-bi-service"></a>Prenumerera på en rapport eller en instrumentpanel i Power BI-tjänsten 
Det har aldrig varit enklare att hålla sig uppdaterad när det gäller viktiga instrumentpaneler och rapporter. Prenumerera på de rapportsidor och instrumentpaneler som är viktigast för dig och Power BI skickar dig ett e-postmeddelande med en ögonblicksbild till din inkorg. Ange hur ofta du vill att Power BI ska skicka dig sådana e-postmeddelanden: varje dag, varje vecka eller när data uppdateras. Du kan även ange en specifik tid då Power BI skickar e-postmeddelanden.  

E-post och ögonblicksbild använder det språk som angetts i Power BI-inställningarna (se [språk och länder/regioner som stöds för Power BI](../supported-languages-countries-regions.md)). Om inget språk har definierats använder Power BI det språk som är inställt i de nationella inställningarna i din nuvarande webbläsare. Om du vill se eller ange din språkinställning klickar du på kugghjulsikonen ![kugghjulsikon](./media/end-user-subscribe/power-bi-settings-icon.png) > **Inställningar > Allmänt > Språk**. 

![Listruta för språk](./media/end-user-subscribe/power-bi-language.png)

När du får e-postmeddelandet innehåller det en länk med rubriken ”Gå till rapporten eller instrumentpanelen”. Om du väljer den här länken på mobila enheter med installerade Power BI-appar, så startas appen (istället för standardåtgärden att rapporten eller instrumentpanelen på webbplatsen Power BI öppnas).


## <a name="requirements"></a>Krav
**Skapa** en prenumeration är en funktion i Power BI Pro.   

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>Prenumerera på instrumentpanel eller en rapportsida
Oavsett om du prenumererar på en instrumentpanel eller en rapport är processerna lika. Du kan använda samma knapp för att prenumerera på Power BI-tjänstens instrumentpaneler och rapporter.
 
![välj ikonen Prenumerera](./media/end-user-subscribe/power-bi-subscribe-orientation.png).

1. Öppna instrumentpanelen eller rapporten.
2. Välj **Prenumerera** på den översta menyraden, eller välj kuvertikonen ![ikonen Prenumerera](./media/end-user-subscribe/power-bi-icon-envelope.png).
   
   ![Ikonen Prenumerera](./media/end-user-subscribe/power-bi-subscribe-icon.png)

   ![Prenumerationsfönster](./media/end-user-subscribe/power-bi-emails2.png)
    
    Fönstret till vänster när du är på en instrumentpanel och väljer **Prenumerera**. Fönstret till höger när du är på en rapportsida och väljer **Prenumerera**. Om du vill prenumerera på flera sidor i en rapport väljer du **Lägg till en till prenumeration** och väljer en annan sida. 

3. Aktivera eller inaktivera prenumerationen med det gula skjutreglaget.  Om du ställer in skjutreglaget på Av så tas inte prenumerationen bort. Om du vill ta bort prenumerationen så väljer du istället papperskorgen.

4. Lägg alternativt till e-postmeddelandeinformation. 

5. Välj en **frekvens** för prenumerationen.  Du kan välja Varje dag, Varje vecka och Efter datauppdatering (Varje dag).  Om du bara vill få e-post för prenumerationen på vissa dagar väljer du **Varje vecka** och vilka dagar du vill få den.  Om du till exempel bara vill ha e-post för prenumerationen på arbetsdagar väljer du **Varje vecka** som frekvens och avmarkerar rutorna Lör och Sön.   


6. Schemalägg tiden som e-postmeddelandet skickas genom att välja Varje dag eller Varje vecka som frekvens och ange en **Schemalagd** **tid** för prenumerationen.   

7. Schemalägg start- och slutdatum genom att ange datum i datumfälten. Som standard blir starttiden för prenumerationen det datum du skapade den och slutdatumet blir ett år senare. När en prenumeration når ett slutdatum stoppas den tills du aktiverar den igen.  Du får ett eller flera meddelanden innan det schemalagda slutdatumet där du tillfrågas om du vill förlänga den.     


5. Spara prenumerationen genom att välja **Spara och stäng**. Du får ett e-postmeddelande och en ögonblicksbild av instrumentpanelen eller rapporten enligt det schema du anger. Alla prenumerationer med frekvensen **Efter datauppdatering** inställd skickar bara ett e-postmeddelande efter den första schemalagda uppdateringen på den dagen.
   
   ![e-postmeddelande med ögonblicksbild av instrumentpanel](media/end-user-subscribe/power-bi-subscribe-email.png)
   
    Att uppdatera rapportsidan uppdaterar inte datauppsättningen. Endast datauppsättningens ägare kan uppdatera en datauppsättning manuellt. Om du vill söka efter namnet på den underliggande datauppsättningen, välj **Visa relaterade** på den översta menyraden.
   
    ![Relaterade datauppsättningar](./media/end-user-subscribe/power-bi-view-related-screen.png)


## <a name="manage-your-subscriptions"></a>Hantera dina prenumerationer
Endast du kan hantera dina prenumerationer. Välj **prenumerera** igen och välj **Hantera alla prenumerationer** längst ned i det nedre vänstra hörnet (se skärmbilder ovan). 

![se alla prenumerationer i Min arbetsyta](./media/end-user-subscribe/power-bi-manage.png)

En prenumeration går ut om Pro-licensen upphör att gälla, om instrumentpanelen eller rapporten tas bort av ägaren eller om det användarkonto som använts för att skapa prenumerationen raderas.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* För e-postprenumerationer på instrumentpaneler visas inte paneler som har säkerhet på radnivå (RLS) tillämpat.  För e-postprenumerationer på rapporter går det inte att skapa en prenumeration om datauppsättningen använder RLS.
* Rapportsideprenumerationer är knutna till namnet på rapportsidan. Om du prenumererar på en rapportsida och den byter namn, måste du återskapa din prenumeration
* Kontakta systemadministratören om du inte använder prenumerationsfunktionen. Din organisation kan ha inaktiverat den här funktionen för autentisering eller av andra orsaker.  
* E-postprenumerationer har inte stöd för så många [anpassade visuella objekt](../power-bi-custom-visuals.md).  Undantaget är de anpassade visuella objekt som har [certifierats](../power-bi-custom-visuals-certified.md).  
* E-postprenumerationer har för närvarande inte stöd för R-baserade anpassade visuella objekt.  
* För prenumerationer på instrumentpaneler så saknar vissa typer av paneler fortfarande stöd.  Detta gäller: strömningspaneler, videopaneler och paneler för anpassat webbinnehåll.     
* På grund av storleksbegränsningar i e-posten kan prenumerationer på instrumentpaneler och rapporter som innehåller extremt stora bilder misslyckas.    
* Power BI pausar automatiskt uppdateringar för datauppsättningar som är associerade med instrumentpaneler och rapporter som inte har besökts på över två månader.  Men om du lägger till en prenumeration på en instrumentpanel eller en rapport, så pausas den inte, även om den förblir obesökt.    

## <a name="next-steps"></a>Nästa steg
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)    
* [Läs blogginlägget](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

