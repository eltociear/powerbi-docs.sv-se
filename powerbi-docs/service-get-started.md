---
title: Kom igång med Power BI-tjänsten
description: Kom igång med Power BI-tjänsten online (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 007819ead82f558efa8179a49dfba9454558dfbb
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995173"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>Självstudie: Kom igång med Power BI-tjänsten (app.powerbi.com)
Den här självstudien hjälper dig att komma igång med *Power BI-tjänsten*. Om du vill förstå hur Power BI-tjänsten passar ihop med andra Power BI-erbjudanden rekommenderar vi att du börjar med att läsa [Vad är Power BI](power-bi-overview.md).

![Relation mellan Power BI Desktop, tjänst, mobil](media/service-get-started/power-bi-components.png)

I den här självstudien går du igenom följande steg:

> [!div class="checklist"]
> * Hitta innehåll som hjälper dig att komma igång med Power BI-tjänsten.
> * Logga in på ditt Power BI-onlinekonto eller registrera dig om du inte har ett konto.
> * Öppna Power BI-tjänsten.
> * Hämta några data och öppna dem i rapportvyn.
> * Använd dessa data för att skapa visualiseringar och spara dem som en rapport.
> * Skapa en instrumentpanel genom att fästa paneler från rapporten.
> * Lägg till ytterligare en visualisering på instrumentpanelen med verktyget för frågor och svar på naturligt språk.
> * Rensa resurser genom att ta bort datamängden, rapporten och instrumentpanelen.

## <a name="sign-up-for-the-power-bi-service"></a>Registrera dig för Power BI-tjänsten
Om du inte har något Power BI-konto [registrerar du dig för en kostnadsfri Power BI Pro-utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

När du har ett konto anger du *app.powerbi.com* i webbläsaren för att öppna Power BI-tjänsten. 

Läs igenom informationen om att [komma igång med Power BI Desktop](desktop-getting-started.md) om du behöver hjälp med Power BI Desktop. Om du behöver hjälp med Power BI Mobile, så läs [Power BI-appar för mobila enheter](consumer/mobile/mobile-apps-for-mobile-devices.md).

> [!TIP]
> Föredrar du en kostnadsfri självstudiekurs istället? [Registrera dig för vår kurs Analysera och visualisera data på EdX](http://aka.ms/edxpbi).

Besök vår [spelningslista på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). En bra video att börja med är *Introduktion till Power BI-tjänsten*:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>Vad är Power BI-tjänsten?
Microsofts Power BI-tjänst kallas ibland för Power BI online eller app.powerbi.com. Power BI hjälper dig att hålla dig uppdaterad med den information som är viktig för dig. *Instrumentpanelerna* i Power BI-tjänsten kan hjälpa dig att hålla dig uppdaterad om din verksamhet. Instrumentpanelerna visar *paneler* som du kan välja för att öppna *rapporter* för vidare utforskning. Anslut till flera *datauppsättningar* så att alla relevanta data samlas på samma plats. Behöver du hjälp med att förstå de olika byggstenarna som utgör Power BI? Se [Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md).

Om du har viktiga data i Excel- eller CSV-filer, så kan du skapa en Power BI-instrumentpanel så att du kan hålla dig informerad var du än befinner dig och dela information med andra.  Prenumererar du på ett SaaS-program som Salesforce?  Kom igång direkt genom att ansluta till Salesforce och automatiskt skapa en instrumentpanel från dessa data, eller [ta en närmare titt på alla andra SaaS-appar](service-get-data.md) som du kan ansluta till. Om du ingår i en organisation kan du kontrollera om några [appar](service-create-distribute-apps.md) har publicerats för dig.

Läs mer om alla andra sätt att [hämta data på för Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Steg 1: Hämta data
Här är ett exempel på hämtning av data från en CSV-fil. Vill du följa den här självstudien? [Ladda ned CSV-filen med finansiella exempel](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Logga in till Power BI](http://www.powerbi.com/). Har du inte något konto? Inga problem, du kan registrera dig för en kostnadsfri utvärderingsversion.
2. Power BI öppnas i webbläsaren. Välj **Hämta data** längst ned i det vänstra navigeringsfältet.

    Sidan **Hämta data** öppnas.   

3. Under avsnittet **Skapa nytt innehåll** väljer du **Filer**. 
   
   ![Hämta filer](media/service-get-started/gs1.png)
4.  Välj **Lokal fil**.
   
     ![Skärmen Hämta Data > Filer](media/service-get-started/gs2.png)

5. Bläddra till filen på datorn och välj **Öppna**.

5. I den här självstudien väljer vi **Importera** för att lägga till Excel-filen som en datamängd som vi sedan kan använda för att skapa rapporter och instrumentpaneler. Om du väljer **Ladda upp** laddas hela Excel-arbetsboken upp till Power BI, där du kan öppna och redigera den i Excel Online.
   
   ![Välja importera](media/service-get-started/power-bi-import.png)
6. När din datauppsättning är klar öppnar du den i rapportredigeraren genom att välja **Visa datauppsättning**. 

    ![Dialogrutan Din datauppsättning är klar](media/service-get-started/power-bi-gs.png)

    Eftersom vi inte har skapat några visualiseringar ännu är rapportarbetsytan tom.

    ![Tom rapportarbetsyta](media/service-get-started/power-bi-report-editor.png)

7. Observera att det finns ett alternativ för **Läsvy** i det övre navigeringsfältet. Eftersom du har det här alternativet innebär det att du för närvarande är i Redigeringsvy. 

    ![Alternativet Läsvy](media/service-get-started/power-bi-editing-view.png)

    I redigeringsvyn kan du skapa och ändra dina rapporter eftersom du är *ägare* till rapporten. Det innebär att du är *skapare*. När du delar din rapport med kollegor kan de bara interagera med rapporten i läsvyn. Kollegorna är alltså *konsumenter*. Lär dig mer om [Läsvy och Redigeringsvy](consumer/end-user-reading-view.md).
    
    Ett bra sätt för dig att bekanta dig med rapportredigeraren är att [ta en rundtur](service-the-report-editor-take-a-tour.md).
 

## <a name="step-2-start-exploring-your-dataset"></a>Steg 2: Börja utforska din datauppsättning
Nu när du har anslutit till dina data kan du börja utforska omgivningarna.  När du har hittat något intressant, kan du skapa en instrumentpanel för att övervaka det och se hur det ändras med tiden. Nu ska vi se hur det fungerar.
    
1. I rapportredigeraren använder vi fönstret **Fält** till höger på sidan för att skapa en visualisering. Markera kryssrutorna **Bruttoförsäljning** och **Datum**.
   
   ![Fältlista](media/service-get-started/fields.png)

    Power BI analyserar informationen och skapar en visualisering. Om du markerade **Datum** först visas en tabell. Om du markerade **Bruttoförsäljning** först visas ett diagram. 

2. Växla till ett annat sätt att visa dina data. Nu visar vi dessa data som ett linjediagram. Välj ikonen för linjediagram i fönstret **Visualiseringar**.
   
   ![Rapportredigeraren med linjediagram valt](media/service-get-started/gettingstart5new.png)

3. Det här diagrammet ser intressant ut så vi *fäster* det på en instrumentpanel. Hovra över visualiseringen och välj fästikonen. När du fäster visualiseringen sparas den på instrumentpanelen och hålls uppdaterad så att du kan se det senaste värdet direkt.
   
   ![Fästikon](media/service-get-started/pinnew.png)

4. Eftersom den här rapporten är ny uppmanas du att spara den innan du kan fästa en visualisering på instrumentpanelen. Ge rapporten ett namn (till exempel *Försäljning över tid*) och välj sedan **Spara och fortsätt**. 
   
   ![Dialogrutan Spara rapport](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. Fäst linjediagrammet på en ny instrumentpanel och ger det namnet *Finansiellt exempel för självstudie*. 
   
   ![Namnge rapporten](media/service-get-started/power-bi-pin.png)
   
6. Välj **fäst**.
   
    Ett meddelande (nära det övre högra hörnet) anger att visualiseringen har lagts till som en panel på instrumentpanelen.
   
    ![Dialogrutan Fäst på instrumentpanelen](media/service-get-started/power-bi-pin-success.png)

7. Välj **Gå till instrumentpanelen** för att se det linjediagram som du fäste som en panel på din nya instrumentpanel. Du kan göra instrumentpanelen ännu bättre genom att lägga till fler visualiseringspaneler och [byta namn och storlek på paneler, länka till dem och placera om dem](service-dashboard-edit-tile.md).
   
   ![Instrumentpanel med fäst visualisering](media/service-get-started/power-bi-new-dashboard.png)
   
8. Välj den nya panelen på instrumentpanelen för att gå tillbaka till rapporten. Power BI för dig tillbaka till rapportredigeraren i läsvyn. Om du vill växla tillbaka till redigeringsvyn väljer du **Redigera rapport** från det översta navigeringsfältet. När du är i redigeringsvyn kan du fortsätta att utforska och fästa paneler. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Steg 3:  Fortsätt att utforska med Frågor och svar (frågor på naturligt språk)
1. Om du vill utforska dina data snabbt kan du ställa en fråga i rutan Frågor och svar. Frågerutan för Frågor och svar är placerad längst upp på instrumentpanelen (**Ställ en fråga om dina data**) och i det översta navigeringsfältet i rapporten (**Ställ en fråga**). Prova till exempel att skriva *vilket segment hade mest intäkter* i rutan Frågor och svar.
   
   ![Frågor och svar-arbetsyta](media/service-get-started/powerbi-qna.png)

2. Frågor och svar söker efter svar och visar dem i form av en visualisering. Välj fästikonen ![Fästikon](media/service-get-started/pbi_pinicon.png) om du vill visa den här visualiseringen på instrumentpanelen.
3. Fäst visualiseringen på instrumentpanelen **Finansiellt exempel för självstudie**.
   
    ![Dialogrutan Fäst på instrumentpanelen](media/service-get-started/power-bi-pin2.png)

4. Gå tillbaka till instrumentpanelen, där du ser den nya panelen.

   ![Instrumentpanel med fäst diagram](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>Rensa resurser
Nu när du är klar med självstudien kan du ta bort datauppsättningen, rapporten och instrumentpanelen. 

1. Välj **Min arbetsyta** i det vänstra navigeringsfältet.
2. Välj fliken **Datauppsättningar** och hitta datauppsättningen du importerade för den här självstudien.  
3. Välj ellipsen (…) > **Ta bort**.

    ![Ta bort datauppsättningen](media/service-get-started/power-bi-delete.jpg)

    När du tar bort datamängden tar Power BI även bort rapporten och instrumentpanelen. 


## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Ansluta till de onlinetjänster som du använder med Power BI](service-connect-to-services.md)

