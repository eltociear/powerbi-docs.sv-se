---
title: "Kom igång med Power BI-tjänsten"
description: "Kom igång med Power BI-tjänsten"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/31/2017
ms.author: mihart
ms.openlocfilehash: 6714283ea4590ac9c2f3728121e05d03d4aa646e
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-power-bi-service"></a>Kom igång med Power BI-tjänsten
Dessa självstudier hjälper dig att komma igång med ***Power BI-tjänsten***. Om du vill förstå hur Power BI-tjänsten passar ihop med andra Power BI-erbjudanden, så rekommenderar vi starkt att du börjar med att läsa [Vad är Power BI](guided-learning/gettingstarted.yml#step-1).

![](media/service-get-started/power-bi-components.png)

Power BI-tjänsten finns i en kostnadsfri version och en Pro-version. Oavsett vilken version du använder, så börja med att öppna webbläsaren och skriva www.powerbi.com. Om du redan har registrerat dig väljer du länken **Logga in** som visas i det övre högra hörnet. Om du inte har registrerat dig för Power BI-tjänsten ännu, så välj istället länken **Registrera dig gratis**.

![](media/service-get-started/power-bi-sign-up.png)

Om du behöver hjälp med Power BI Desktop, så läs [Kom igång med Desktop](desktop-getting-started.md). Om du behöver hjälp med Power BI Mobile, så läs [Power BI-appar för mobila enheter](mobile-apps-for-mobile-devices.md).

> [!TIP]
> Föredrar du en kostnadsfri självstudiekurs istället? [Registrera dig för vår kurs Analysera och visualisera data på EdX](http://aka.ms/edxpbi).

Besök vår [spelningslista på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). En bra video är att börja med är Introduktion till Power BI-tjänsten:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 
> 
> 

Microsoft Power BI hjälper dig att hålla dig uppdaterad med den information som är viktig för dig.  Tack vare Power BI-tjänsten hjälper ***instrumentpanelerna*** dig att ha koll på verksamhetens puls.  Instrumentpanelerna visar ***paneler*** i vilka du kan öppna ***rapporter*** genom att klicka, för att sedan utforska vidare.  Anslut till flera ***datauppsättningar*** så att alla relevanta data samlas på samma plats. Behöver du hjälp att förstå de olika byggstenarna i Power BI?  Mer information finns i [Power BI – grundläggande begrepp](service-basic-concepts.md).

Om du har viktiga data i Excel- eller CSV-filer, så kan du skapa en Power BI-instrumentpanel så att du kan hålla dig informerad var du än befinner dig och dela information med andra.  Prenumererar du på ett SaaS-program som Salesforce?  Kom igång direkt genom att [ansluta till Salesforce](service-connect-to-salesforce.md) och automatiskt skapa en instrumentpanel från dessa data, eller [ta en närmare titt på alla andra SaaS-appar](service-get-data.md) som du kan ansluta till. Om du arbetar för en organisation kan du kontrollera om några [appar](service-create-distribute-apps.md) har publicerats för dig.

Läs mer om alla andra sätt att [hämta data på för Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Steg 1: Hämta data
Här är ett exempel på hämtning av data från en CSV-fil. Vill du följa den här självstudien? [Hämta den här CSV-exempelfilen](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Logga in till Power BI](http://www.powerbi.com/). Har du inte något konto? Inga problem, du kan registrera dig kostnadsfritt.
2. Power BI öppnas i webbläsaren. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-get-started/getdata3.png)
3. Välj **Filer**. 
   
   ![](media/service-get-started/gs1.png)
4. Välj **Lokal fil**, bläddra till filen på datorn och välj **Öppna**.
   
   ![](media/service-get-started/gs2.png)
5. I den här självstudien väljer vi **Importera** så att vi kan lägga till Excel-filen som en datauppsättning som vi sedan kan använda för att skapa rapporter och instrumentpaneler.  
   
   > [!NOTE]
   > Om du väljer **Ladda upp** överförs hela Excel-arbetsboken till Power BI, där du kan öppna och redigera den i Excel Online.
   > 
   > 
   
   ![](media/service-get-started/power-bi-import.png)
6. När din datauppsättning är klar öppnar du den i rapportredigeraren genom att välja **Visa datauppsättning**. ![](media/service-get-started/power-bi-gs.png).
   
   > [!TIP]
   > Ett bra sätt för dig att bekanta dig med rapportredigeraren är att [ta en rundtur](service-the-report-editor-take-a-tour.md)
   > 
   > 

## <a name="step-2-start-exploring-your-dataset"></a>Steg 2: Börja utforska din datauppsättning
Nu när du har anslutit till dina data kan du börja utforska dem och få insikter.  När du har hittat något som du vill övervaka, kan du skapa en instrumentpanel som håller dig uppdaterad om ändringar.

1. Välj datauppsättningsavbildningen på instrumentpanelen så att du kan utforska de data som du just anslutit till, eller öppna den genom att markera datauppsättningens namn under rubriken **Datauppsättningar**. Datauppsättningen öppnas som en tom rapport.
   
   ![](media/service-get-started/power-bi-report-editor.png)
   
   > [!NOTE]
> Ett annat sätt att utforska dina data är genom **Quick Insights**.  Mer information finns i [Introduktion till Quick Insights](service-insights.md)
   > 
   > 
2. Skapa en visualisering genom att välja fält i listan **Fält** till höger på sidan.  Markera kryssrutan intill **Bruttoförsäljning** och **Datum**.
   
   ![](media/service-get-started/fields.png)
3. Power BI analyserar informationen och skapar ett visuellt objekt.  Om du markerade **Datum** först, så visas en tabell.  Om du markerade **Bruttoförsäljning** först, så visas ett diagram. Växla till ett annat sätt att visa dina data. Försök att ändra till ett linjediagram genom att välja diagramalternativet.
   
   ![](media/service-get-started/gettingstart5new.png)
4. När du har en visualisering som du vill ha på din instrumentpanel, så hovra över visualiseringen och välj ikonen **Fäst**.  När du har fäst visualiseringen sparas den på din instrumentpanel så att du kan spåra det senaste värdet direkt.
   
   ![](media/service-get-started/pinnew.png)
5. Eftersom detta är en ny rapport måste du spara det innan du kan fästa en visualisering från den på instrumentpanelen. Ge rapporten ett namn (t.ex. *Försäljning över tid*) och välj **Spara och fortsätt**. 
   
   ![](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
   Den nya rapporten visas i navigeringsfönstret under rubriken **Rapporter**.
6. Fäst panelen på en befintlig eller ny instrumentpanel. 
   
   ![](media/service-get-started/power-bi-pin.png)
   
   * **Befintlig instrumentpanel**: Markera instrumentpanelens namn i listrutan.
   * **Ny instrumentpanel**: Skriv instrumentpanelens namn.
7. Välj **Fäst**.
   
   Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.
   
   ![](media/service-get-started/power-bi-pin-success.png)
8. Välj **Gå till instrumentpanelen** om du vill se din nya instrumentpanel med det fästa fönstret. Linjediagrammet fästs, som en panel, på instrumentpanelen. Kontrollera instrumentpanelen ännu bättre genom att [byta namn på, ändra storlek på, länka och positionera om panelerna](service-dashboard-edit-tile.md).
   
   ![](media/service-get-started/power-bi-new-dashboard.png)
   
   Välj den nya panelen på instrumentpanelen och gå tillbaka till rapporten.

## <a name="step-3-continue-exploring-with-qa-natural-language-querying"></a>Steg 3: Fortsätt att utforska med frågor och svar (frågor på naturligt språk)
1. Om du vill utforska dina data snabbt, så försök med att ställa en fråga i rutan Frågor och svar. Frågerutan finns högst upp på instrumentpanelen. Försök t.ex. att skriva ”**vilket segment hade mest intäkter**”.
   
   ![](media/service-get-started/powerbi-qna.png)
2. Välj fästikonen ![](media/service-get-started/pbi_pinicon.png) om du även vill visa den här visualiseringen på instrumentpanelen.
3. Fäst visualiseringen på instrumentpanelen Ekonomiskt exempel.
   
    ![](media/service-get-started/power-bi-pin2.png)
4. Markera bakåtpilen för **Avsluta frågor och svar** ![](media/service-get-started/pbi_qabackarrow.png) och gå tillbaka till instrumentpanelen, där du ser den nya panelen.

## <a name="next-steps"></a>Nästa steg
Är du redo att testa mer?  Här följer några bra sätt du kan utforska Power BI på.

* [Ansluta till en annan datauppsättning](service-get-data.md).
* [Dela instrumentpanelen](service-share-dashboards.md) med dina kollegor.
* Läs [Tips om att utforma instrumentpaneler](service-dashboards-design-tips.md).
* Visa dina instrumentpaneler med en [Power BI-app på en mobil enhet](mobile-apps-for-mobile-devices.md)

Är du inte riktigt redo än? Börja med dessa ämnen som hjälper dig att känna dig bekväm med Power BI.

* [Lär dig hur rapporter, datauppsättningar, instrumentpaneler och fönster fungerar ihop](service-basic-concepts.md)
* [Power BI-videor](videos.md)
* [Se vilka tillgängliga exempel som du kan använda](sample-datasets.md)

### <a name="stay-in-touch-with-power-bi"></a>Hålla kontakten med Power BI
* Följ [@MSPowerBI på Twitter](https://twitter.com/mspowerbi)
* Prenumerera på vår [YouTube-video-kanal](https://www.youtube.com/channel/UCy--PYvwBwAeuYaR8JLmrfg)
* Titta på våra på begäran-webbseminarier [Power BI Komma igång](webinars.md)
* Vet du inte var du hittar hjälp? Läs sidan [10 tips om att få hjälp](service-tips-for-finding-help.md)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

