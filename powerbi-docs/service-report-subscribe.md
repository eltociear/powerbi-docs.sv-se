---
title: Prenumerera på dig själv och andra rapporter och instrumentpaneler – Power BI
description: Lär dig hur du prenumererar en ögonblicksbild av en Power BI-rapportsida, en instrumentpanel eller en sidnumrerad rapport dig själv och andra.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: a344e3cdd93fbd237387b61fb4735b41f22625e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65991117"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>Skapa en prenumeration åt dig eller andra på rapporter och instrumentpaneler i Power BI-tjänsten

Du kan prenumerera på dig själv och dina kollegor till rapportsidor, instrumentpaneler och sidnumrerade rapporter som är viktigast för dig. Powerbi e-postmeddelanden en ögonblicksbild till din inkorg. Ange hur ofta du vill att Power BI ska skicka dig sådana e-postmeddelanden: varje dag, varje vecka eller efter den första datauppdateringen.  Om du väljer varje dag eller varje vecka, kan du välja tid vill du ha den prenumeration som kör.  Totalt kan du ange upp till 24 olika prenumerationer per dag, för varje rapportsida och instrumentpanel.

![e-postmeddelande med ögonblicksbild av instrumentpanel](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

Du kan bara skapa prenumerationer i Power BI-tjänsten. Du får ett e-postmeddelande med en ögonblicksbild av rapportsidan eller instrumentpanelen, med en länk till att öppna rapporten eller instrumentpanelen. Om du väljer den här länken på mobila enheter med installerade Power BI-appar, så startas Power BI-appen, i stället för att öppna rapporten eller instrumentpanelen på Power BI-webbplatsen.

## <a name="requirements"></a>Krav

- **Skapa** en prenumeration är en funktion i Power BI Pro.
- Du behöver inte redigera behörigheter för innehållet (instrumentpanel eller rapport) för att skapa en prenumeration åt dig själv men du måste ha redigeringsbehörigheter för att skapa en åt någon annan. 
- Från och med januari 2019 måste du inte längre ha uppdatering av datauppsättning för att köra en prenumeration.  Den körs oberoende av schemalagda uppdateringar du har ställt in.  

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>Prenumerera på en instrumentpanel, en rapportsida eller en sidnumrerad rapport

Om du prenumerera på en instrumentpanel, rapport, eller sidnumrerad rapport, processen påminner om. Du kan använda samma knapp för att prenumerera på Power BI-tjänstens instrumentpaneler och rapporter.

Prenumerera på sidnumrerade rapporter är lite annorlunda. Se [prenumerera en sidnumrerad rapport i Power BI-tjänsten dig själv och andra](paginated-reports-subscriptions.md) mer information.
 
![välj ikonen Prenumerera](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Öppna instrumentpanelen eller rapporten.
2. Välj **Prenumerera** på den översta menyraden, eller välj kuvertikonen ![ikonen Prenumerera](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Ikonen Prenumerera](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. Aktivera eller inaktivera prenumerationen med det gula skjutreglaget.  Om du ställer in skjutreglaget på **Av** så tas inte prenumerationen bort. Om du vill ta bort prenumerationen så väljer du istället papperskorgen.

4. Din e-postadress finns redan i rutan **Prenumerera**. Du kan också lägga till andra e-postadresser i prenumerationen men bara i samma domän. Om rapporten eller instrumentpanelen finns i [Premium-kapacitet](service-premium-what-is.md) kan du skapa prenumerationer för andra enskilda e-postadresser och gruppalias. Om rapporten eller instrumentpanelen inte finns i Premium-kapacitet kan du skapa prenumerationer för andra personer men de måste också ha Power BI Pro-licenser. Mer information finns i [Överväganden och felsökning](#considerations-and-troubleshooting) nedan. 

5. Fyll i information om **Ämne** och **Meddelande** för e-posten. 

5. Välj en **frekvens** för prenumerationen: **Varje dag**, **Varje vecka** och **Efter datauppdatering (Varje dag)** .  Om du bara vill få e-post för prenumerationen på vissa dagar väljer du **Varje vecka** och vilka dagar du vill få den.  Om du till exempel bara vill ha e-post för prenumerationen på vardagar väljer du **Varje vecka** och avmarkerar rutorna **Lör** och **Sön**.  

6. Om du väljer **Varje dag** eller **Varje vecka** kan du också välja en **Schemalagd tid** för prenumerationen.  Du kan köra den på heltimme eller 15, 30 eller 45 minuter över.  Välj morgon (AM) eller eftermiddag/kväll (PM). Du kan även ange tidszon.

7. Som standard är startdatum för prenumerationen det datum du skapar den. Du har möjlighet att välja ett slutdatum. Om du inte anger ett slutdatum är slutdatumet automatiskt ett år efter startdatumet. Du kan ändra det till vilket datum som helst i framtiden (upp till år 9999) när som helst innan prenumerationen avslutas. När en prenumeration når ett slutdatum stoppas den tills du aktiverar den igen. Du får ett eller flera meddelanden innan det schemalagda slutdatumet där du tillfrågas om du vill förlänga den.    

    I skärmbilderna nedan ser du att när du prenumererar på en rapport prenumererar du i själv verket på en rapport*sida*.  Om du vill prenumerera på flera sidor i en rapport väljer du **Lägg till en till prenumeration** och väljer en annan sida. 
      
   ![Fönstret Prenumerera](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. Välj **Spara och stäng**. Användare som prenumererar får ett e-postmeddelande och en ögonblicksbild eller rapportsida för den frekvens och tid du har valt. Totalt kan du skapa upp till 24 prenumerationer per rapport eller instrumentpanel och kan ange unika mottagare, tider och frekvenser för varje prenumeration.  Alla prenumerationer med frekvensen **Efter datauppdatering** inställd för din instrumentpanel eller rapport skickar fortfarande bara ett e-postmeddelande efter den första schemalagda uppdateringen.   
      
   > [!TIP]
   > Vill du skicka e-postmeddelandet från en prenumeration direkt eller på begäran vid valfri tidpunkt? Välj **Kör nu** för prenumerationerna för den instrumentpanel eller rapport som du vill skicka. Du får därmed ett meddelande om att ett e-postmeddelande skickas till alla för den specifika prenumerationen.  Du kan göra detta så ofta du vill. Den räknas inte mot din gräns på 24 schemalagda prenumerationskörningar per dag per rapport eller instrumentpanel. Den utlöser inte en datauppdatering av den underliggande datauppsättningen. 
   > 
   > 
   
## <a name="email-languages"></a>E-postspråk

E-post och ögonblicksbild använder det språk som angetts i Power BI-inställningarna (se [språk och länder/regioner som stöds för Power BI](supported-languages-countries-regions.md)). Om inget språk har definierats använder Power BI det språk som är inställt i de nationella inställningarna i din nuvarande webbläsare. Om du vill se eller ange din språkinställning klickar du på kugghjulsikonen ![kugghjulsikon](media/service-report-subscribe/power-bi-settings-icon.png) > **Inställningar > Allmänt > Språk**. 

![Listruta för språk](media/service-report-subscribe/power-bi-language.png)

## <a name="manage-your-subscriptions"></a>Hantera dina prenumerationer
Endast den person som skapade prenumerationen kan hantera den.  Det finns två vägar till skärmen för att hantera dina prenumerationer.  Den första är att välja **Hantera alla prenumerationer** i dialogrutan **Prenumerera på e-postmeddelanden** (se skärmbilderna nedanför steg 4 ovan). Den andra hittar du genom att välja kugghjulsikonen i Power BI ![kugghjulsikon](media/service-report-subscribe/power-bi-settings-icon.png) på den översta menyraden sedan välja **Inställningar**.

![välj Inställningar](media/service-report-subscribe/power-bi-subscribe-settings.png)

Vilka enskilda prenumerationer som visas beror på vilken arbetsyta som för närvarande är aktiv.  Om du vill se alla dina prenumerationer på en gång för alla arbetsytor, så kontrollera att **Min arbetsyta** är aktiv. Om du vill ha hjälp med att förstå hur arbetsytor fungerar, så gå till [Arbetsytor i Power BI](service-create-workspaces.md).

![se alla prenumerationer i Min arbetsyta](media/service-report-subscribe/power-bi-subscriptions.png)

En prenumeration går ut om Pro-licensen upphör att gälla, om ägaren tar bort instrumentpanelen eller om det användarkonto som använts för att skapa prenumerationen raderas.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

* Instrumentpaneler med fler än 25 fästa paneler, eller fyra fästa liverapportsidor, kanske inte återges till fullo i prenumerationsmeddelanden som skickas till användare via e-post.  Prenumerationer på instrumentpaneler i dessa antal paneler inte är blockerad. Men betraktas de som stöds inte om det uppstår problem. Överväg att ändra dem enlighet med detta för att ligga inom ett intervall som stöds.
* När du konfigurerar e-postprenumerationer, Kom ihåg det finns en fördröjning mellan när prenumerationen jobbet startar och den exakta tidpunkt som meddelandet skickas.  Ställ in en annan tid för din schemalagd datauppdatering än när din prenumeration för e-post är schemalagd att köras för att minimera fördröjningen mellan två.
* Om alla paneler har radnivå (RLS) tillämpas, för instrumentpanelen e-postprenumerationer visas dessa paneler.  
* För rapporten e-postprenumerationer om datauppsättningen använder RLS måste skapa du en prenumeration för dig själv. Du kan inte prenumerera andra i en rapport med radnivå (RLS) tillämpas.
* Rapportsideprenumerationer är knutna till namnet på rapportsidan. Om du prenumererar på en rapportsida och sedan byter namn på den, måste du återskapa din prenumeration.
* Din organisation kan konfigurera vissa inställningar i Azure Active Directory som begränsar möjligheten att använda e-postprenumerationer i Power BI.  Dessa begränsningar inkluderar, men begränsas inte till, att ha multifaktorautentisering eller begränsningar för IP-intervallet vid åtkomst till resurser.
* E-postprenumerationer för rapporter/instrumentpaneler som använder live-anslutningsdatauppsättningar stöds för närvarande inte när du andra användare än du prenumererar.
* E-postprenumerationer har inte stöd för så många [anpassade visuella objekt](power-bi-custom-visuals.md).  Det enda undantaget är de anpassade visuella objekt som har [certifierats](power-bi-custom-visuals-certified.md).  
* E-postprenumerationer har för närvarande inte stöd för R-baserade anpassade visuella objekt.  
* E-postprenumerationer skickas med rapportens standardfilter och utsnittstillstånd. Inga ändringar av standardinställningarna som du gör efter att du börjar prenumerera visas i e-postmeddelandet.    
* För prenumerationer på instrumentpaneler så saknar vissa typer av paneler fortfarande stöd.  Detta gäller: strömningspaneler, videopaneler och paneler för anpassat webbinnehåll.     
* Om du delar en instrumentpanel med en kollega utanför din klientorganisation kan du inte skapa en prenumeration till den kollegan. Om du till exempel är aaron@xyz.com kan du dela med anyone@ABC.com, men du kan ännu inte prenumerera anyone@ABC.com, och den personen kan inte prenumerera på delat innehåll.      
* Power BI pausar automatiskt uppdateringar för datauppsättningar som är associerade med instrumentpaneler och rapporter som inte har besökts på över två månader.  Men om du lägger till en prenumeration på en instrumentpanel eller en rapport, så pausas den inte, även om den förblir obesökt.    
* Om du inte får någon e-post angående prenumerationen, så kontrollera att ditt UPN (User Principal Name) kan ta emot e-postmeddelanden. [Power BI-teamet arbetar med att släppa på det här kravet](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163), så håll dig uppdaterad. 
* Om din instrumentpanel eller rapport finns i Premium-kapacitet kan du använda grupp-e-postalias för prenumerationer i stället för att prenumerera kollegor med en e-postadress i taget. Alias baseras på aktuell aktiv katalog. 

## <a name="next-steps"></a>Nästa steg

- [Prenumerera på dig själv och andra en sidnumrerad rapport i Power BI-tjänsten](paginated-reports-subscriptions.md)
- Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)    
- [Läs blogginlägget](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
