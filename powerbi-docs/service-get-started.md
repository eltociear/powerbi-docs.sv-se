---
title: Kom igång med Power BI-tjänsten (Power BI online)
description: Kom igång med Power BI online (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 6de9427a11ae5aa43563ce9e21371d231a1dd3a9
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900561"
---
# <a name="tutorial-get-started-with-power-bi-service-apppowerbicom"></a>Självstudie: Kom igång med Power BI-tjänsten (app.powerbi.com)
Dessa självstudier hjälper dig att komma igång med ***Power BI-tjänsten***. Om du vill förstå hur Power BI-tjänsten passar ihop med andra Power BI-erbjudanden, så rekommenderar vi starkt att du börjar med att läsa [Vad är Power BI](power-bi-overview.md).

![Bild på relationen mellan Power BI Desktop, Power BI Mobile och Power BI-tjänsten](media/service-get-started/power-bi-components.png)

I den här självstudien går du igenom följande steg:

> [!div class="checklist"]
> * Hitta annat kom igång-innehåll för Power BI-tjänsten
> * Logga in på ditt Power BI-onlinekonto eller registrera dig om du inte har ett konto
> * Öppna Power BI-tjänsten
> * Hämta information och öppna den i rapportvyn
> * Använd informationen för att skapa visualiseringar och spara som en rapport
> * Skapa en instrumentpanel genom att fästa paneler från rapporten
> * Lägg till ytterligare visualisering på instrumentpanelen med verktyget för frågor och svar på naturligt språk
> * Rensa resurser genom att ta bort datauppsättningen, rapporten och instrumentpanelen

## <a name="sign-up-for-power-bi-service"></a>Registrera dig för Power BI-tjänsten
Om du inte har registrerat dig för Power BI, [registrerar du dig för en kostnadsfri Power BI Pro-utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

Om du redan har ett konto öppnar du en webbläsare och skriver in app.powerbi.com för att öppna Power BI-tjänsten. 

![Logga in eller Registrera dig kostnadsfritt](media/service-get-started/power-bi-sign-up.png)

Om du behöver hjälp med Power BI Desktop, så läs [Kom igång med Desktop](desktop-getting-started.md). Om du behöver hjälp med Power BI Mobile, så läs [Power BI-appar för mobila enheter](consumer/mobile/mobile-apps-for-mobile-devices.md).

> [!TIP]
> Föredrar du en kostnadsfri självstudiekurs istället? [Registrera dig för vår kurs Analysera och visualisera data på EdX](http://aka.ms/edxpbi).

Besök vår [spelningslista på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). En bra video är att börja med är Introduktion till Power BI-tjänsten:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-power-bi-service"></a>Vad är Power BI-tjänsten?
Microsofts Power BI-tjänst kallas ibland för Power BI online eller app.powerbi.com. Power BI hjälper dig att hålla dig uppdaterad med den information som är viktig för dig.  Tack vare Power BI-tjänsten hjälper ***instrumentpanelerna*** dig att ha koll på verksamhetens puls.  Instrumentpanelerna visar ***paneler*** i vilka du kan öppna ***rapporter*** genom att klicka, för att sedan utforska vidare.  Anslut till flera ***datauppsättningar*** så att alla relevanta data samlas på samma plats. Behöver du hjälp att förstå de olika byggstenarna i Power BI?  Mer information finns i [Power BI – grundläggande begrepp](consumer/end-user-basic-concepts.md).

Om du har viktiga data i Excel- eller CSV-filer, så kan du skapa en Power BI-instrumentpanel så att du kan hålla dig informerad var du än befinner dig och dela information med andra.  Prenumererar du på ett SaaS-program som Salesforce?  Kom igång direkt genom att ansluta till Salesforce och automatiskt skapa en instrumentpanel från dessa data, eller [ta en närmare titt på alla andra SaaS-appar](service-get-data.md) som du kan ansluta till. Om du arbetar för en organisation kan du kontrollera om några [appar](service-create-distribute-apps.md) har publicerats för dig.

Läs mer om alla andra sätt att [hämta data på för Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Steg 1: Hämta data
Här är ett exempel på hämtning av data från en CSV-fil. Vill du följa den här självstudien? [Hämta den här CSV-exempelfilen](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Logga in till Power BI](http://www.powerbi.com/). Har du inte något konto? Inga problem, du kan registrera dig för en kostnadsfri utvärderingsversion.
2. Power BI öppnas i webbläsaren. Välj **Hämta data** längst ned i det vänstra navigeringsfältet.
   
   ![hämta data](media/service-get-started/getdata3.png)
3. Välj **Filer**. 
   
   ![hämta filer](media/service-get-started/gs1.png)
4. Bläddra till filen på datorn och välj **Öppna**. Om du har sparat den i OneDrive för företag, väljer du det alternativet. Om du har sparat den lokalt, väljer du **Lokal fil**. 
   
   ![Skärmen Hämta Data > Filer](media/service-get-started/gs2.png)
5. I den här självstudien väljer vi **Importera** så att vi kan lägga till Excel-filen som en datauppsättning som vi sedan kan använda för att skapa rapporter och instrumentpaneler. Om du väljer **Ladda upp** överförs hela Excel-arbetsboken till Power BI, där du kan öppna och redigera den i Excel Online.
   
   ![välj Importera](media/service-get-started/power-bi-import.png)
6. När din datauppsättning är klar öppnar du den i rapportredigeraren genom att välja **Visa datauppsättning**. 

    ![Dialogrutan Din datauppsättning är klar](media/service-get-started/power-bi-gs.png)

    Eftersom vi inte har skapat några visualiseringar än är rapportarbetsytan tom.

    ![tom rapportarbetsyta](media/service-get-started/power-bi-report-editor.png)

6. Ta en titt på den översta menyraden och lägg märke till att det finns ett alternativ som heter **Läsvy**. Eftersom alternativet Läsvy visas, innebär det att du för närvarande befinner dig i **redigeringsvyn**. 

    ![Alternativet Läsvy](media/service-get-started/power-bi-editing-view.png)

    I redigeringsvyn kan du skapa och ändra dina rapporter eftersom du är *ägare* till rapporterna. Det är du som är *skaparen*. När du delar din rapport med kollegor kan de bara interagera med rapporten i läsvyn. De är *konsumenter*. Lär dig mer om [Läsvy och Redigeringsvy](consumer/end-user-reading-view.md).
    
    Ett bra sätt för dig att bekanta dig med rapportredigeraren är att [ta en rundtur](service-the-report-editor-take-a-tour.md)
   > 
 

## <a name="step-2-start-exploring-your-dataset"></a>Steg 2: Börja utforska din datauppsättning
Nu när du har anslutit till dina data kan du börja utforska omgivningarna.  När du har hittat något intressant, kan du skapa en instrumentpanel för att övervaka det och se hur det ändras med tiden. Nu ska vi se hur det fungerar.
    
1. I rapportredigeraren använder vi fönstret **Fält** till höger på sidan för att skapa en visualisering.  Markera kryssrutan intill **Bruttoförsäljning** och **Datum**.
   
   ![Fältlista](media/service-get-started/fields.png)

2. Power BI analyserar informationen och skapar en visualisering.  Om du markerade **Datum** först, så visas en tabell.  Om du markerade **Bruttoförsäljning** först, så visas ett diagram. Växla till ett annat sätt att visa dina data. Nu visar vi dessa data som ett linjediagram. Välj linjediagramsikonen (kallas även mall) från **visualiseringsfönstret**.
   
   ![rapportredigeraren med vald ikon](media/service-get-started/gettingstart5new.png)

3. Det ser intressant ut så vi *fäster* det på en instrumentpanel. Hovra över visualiseringen och välj **stiftikonen**.  När du har fäst visualiseringen sparas den på instrumentpanelen och hålls uppdaterad så att du kan spåra det senaste värdet direkt.
   
   ![fästikon](media/service-get-started/pinnew.png)

4. Eftersom detta är en ny rapport uppmanas du att spara den innan du kan fästa en visualisering på instrumentpanelen. Ge rapporten ett namn (till exempel *Försäljning över tid*) och välj **Spara och fortsätt**. 
   
   ![Dialogrutan Spara rapport](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. Vi fäster linjediagrammet på en ny instrumentpanel och ger det namnet ”Ekonomiskt exempel för självstudier”. 
   
   ![namnge rapporten](media/service-get-started/power-bi-pin.png)
   
1. Välj **fäst**.
   
    Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.
   
    ![Dialogrutan Fäst på instrumentpanelen](media/service-get-started/power-bi-pin-success.png)

6. Välj **Gå till instrumentpanelen** för att se linjediagrammet fäst, som en panel, på din helt nya instrumentpanel. Du kan göra instrumentpanelen ännu bättre genom att lägga till fler visualiseringspaneler och [byta namn och storlek på dem, länka till dem och placera om dem](service-dashboard-edit-tile.md).
   
   ![Instrumentpanel med fäst visualisering](media/service-get-started/power-bi-new-dashboard.png)
   
   Välj den nya panelen på instrumentpanelen och gå tillbaka till rapporten. Power BI för dig tillbaka till rapportredigeraren i läsvyn. Om du vill växla tillbaka till redigeringsvyn, väljer du **Redigera rapporten** från den översta menyraden. När du befinner dig i redigeringsvyn igen kan du fortsätta att utforska och fästa paneler. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Steg 3: Fortsätt att utforska med Frågor och svar (frågor på naturligt språk)
1. Om du vill utforska dina data snabbt, så försök med att ställa en fråga i rutan Frågor och svar. Frågerutan för Frågor och svar är placerad längst upp på instrumentpanelen (**Ställ en fråga om dina data**) och i menyraden överst i rapporten (**Ställ en fråga**). Försök till exempel att skriva ”vilket segment hade mest intäkter”.
   
   ![Frågor och svar-arbetsyta](media/service-get-started/powerbi-qna.png)

2. Frågor och svar söker efter svar och visar dem i form av en visualisering. Välj fästikonen ![fästikon](media/service-get-started/pbi_pinicon.png) om du även vill visa den här visualiseringen på instrumentpanelen.
3. Fäst visualiseringen på instrumentpanelen ”Ekonomiskt exempel för självstudier”.
   
    ![Dialogrutan Fäst på instrumentpanelen](media/service-get-started/power-bi-pin2.png)

4. Gå tillbaka till instrumentpanelen där du ser den nya panelen.

   ![instrumentpanel med fäst diagram](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>Rensa resurser
Nu när du är klar med självstudien kan du ta bort datauppsättningen, rapporten och instrumentpanelen. 

1. Välj **Min arbetsyta** i det vänstra navigeringsfältet.
2. Välj fliken **Datauppsättningar** och hitta datauppsättningen du importerade för den här självstudien.  
3. Välj ellipsen (...) > **Ta bort**.

    ![Ta bort datauppsättningen](media/service-get-started/power-bi-delete.jpg)

    När du tar bort datauppsättningen tas även rapporten och instrumentpanelen bort. 


## <a name="next-steps"></a>Nästa steg
Är du redo att testa mer?  Här följer några bra exempel på hur du kan utforska Power BI.

> [!div class="nextstepaction"]
> [Ansluta till onlinetjänster som du använder](service-connect-to-services.md)

