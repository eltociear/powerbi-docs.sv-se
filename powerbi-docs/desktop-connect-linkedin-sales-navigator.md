---
title: Ansluta till LinkedIn Sales Navigator i Power BI Desktop
description: Anslut enkelt till och använd data från LinkedIn i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/11/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: cd952dfa690d079d662f09e1e01c34dadf129b7b
ms.sourcegitcommit: a21f7f9de32203e3a4057292a24ef9b5ac6ce94b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74565649"
---
# <a name="connect-to-linkedin-sales-navigator-in-power-bi-desktop"></a>Ansluta till LinkedIn Sales Navigator i Power BI Desktop

I **Power BI Desktop** kan du ansluta till **LinkedIn Sales Navigator** för att hitta och skapa relationer, på samma sätt som i andra datakällor i Power BI Desktop samt skapa färdiga rapporter för dina resultat.

![Användningsflik för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-01.png)


Om du vill ansluta till LinkedIn-data med **LinkedIn Sales Navigator**, måste du ha ett LinkedIn Sales Navigator Enterprise-abonnemang och antingen vara administratörsanvändare eller rapporterande användare i Sales Navigator-kontraktet.

Följande video innehåller en guidad rundtur och självstudie om hur du använder mallappen för **LinkedIn Sales Navigator**, vilken beskrivs mer detaljerat [längre fram i den här artikeln](#using-the-linkedin-sales-navigator-template-app). 

> [!VIDEO https://www.youtube.com/embed/ZqhmaiORLw0]

## <a name="connect-to-linkedin-sales-navigator"></a>Ansluta till LinkedIn Sales Navigator

Om du vill ansluta till **LinkedIn Sales Navigator**-data väljer du **Hämta data** i menyfliksområdet **Start** i Power BI Desktop. Välj **Onlinetjänster** i kategorierna till vänster och bläddra tills du ser **LinkedIn Sales Navigator (Beta)** .

![Hämta data i Power BI Desktop](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-02.png)

Ett meddelande visas om att du ansluter till en tredjepartsanslutning som fortfarande är under utveckling. 

![Tredjepartsvarning](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-03.png)

När du väljer **Fortsätt** uppmanas du ange vilka data du önskar.

![Fråga om vilken information som ska tillhandahållas](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-04.png)


I fönstret **LinkedIn Sales Navigator** som visas väljer du vilka data du vill returnera, antingen *Alla kontakter* eller *Valda kontakter* i den första listrutan. Du kan sedan ange start- och slutdatum för att begränsa vilka data som hämtas.

När du har angett informationen ansluter Power BI Desktop till de data som är kopplade till ditt LinkedIn Sales Navigator-kontrakt. Använd samma e-postadress som du använder för att logga in på LinkedIn Sales Navigator via webbplatsen. 

![Logga in på LinkedIn](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-05.png)

När du har anslutit uppmanas du att välja data från ditt LinkedIn Sales Navigator-kontrakt från ett **Navigator**-fönster.

![Välja data med Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-09.png)

Du kan skapa vilka rapporter du vill med dina LinkedIn Sales Navigator-data. För att göra det enklare finns det också en .PBIX-fil för LinkedIn Sales Navigator som du kan ladda ned. Den innehåller redan dataexempel för att du ska kunna bekanta dig med data och rapporter, utan att behöva starta från början.

Du kan ladda ned PBIX-filen från följande plats:
* [PBIX för LinkedIn Sales Navigator](service-template-apps-samples.md)

Förutom PBIX-filen innehåller LinkedIn Sales Navigator också en mallapp som du kan ladda ned och använda. I nästa avsnitt beskrivs mallappen mer detaljerat.


## <a name="using-the-linkedin-sales-navigator-template-app"></a>Använda mallappen i LinkedIn Sales Navigator

För att kunna använda **LinkedIn Sales Navigator** så enkelt som möjligt, kan du använda [mallappen](service-template-apps-overview.md) som automatiskt skapar en färdig rapport från dina LinkedIn Sales Navigator-data.

![Mallapp för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-10.png)

När du laddar ner appen kan du välja om du vill ansluta till dina data eller utforska appen med exempeldata. Du kan alltid gå tillbaka och ansluta till dina egna LinkedIn Sales Navigator-data när du har utforskat exempeldatan. 

![Ansluta till data för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-11.png)



Du kan hämta mallappen för **LinkedIn Sales Navigator** från följande länk:
* [Mallapp för LinkedIn Sales Navigator](https://appsource.microsoft.com/product/power-bi/pbi-contentpacks.linkedin_navigator-preview?flightCodes=17ad4c68-fbc5-4925-a351-139fd384ec33)

I mallappen finns fyra flikar som hjälper dig att analysera och dela din information:

* Användning
* Sök
* InMail
* SSI

På fliken **Användning** visas dina övergripande LinkedIn Sales Navigator-data.

![Fliken Användning för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-12.png)

På fliken **Sök** kan du söka mer detaljerat i dina sökresultat:

![Fliken Sök för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-13.png)

I **InMail** visas din InMail-användning, inklusive antal skickade InMail-meddelanden, godkännandefrekvenser och annan användbar information:

![Fliken InMail för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-14.png)

På fliken **SSI** finns ytterligare information om ditt SSI (Social Selling Index):

![Fliken SSI för LinkedIn Sales Navigator](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-15.png)

Om du vill gå från exempeldata till dina egna data väljer du **Redigera app** i det övre högra hörnet (pennikonen) och sedan **Anslut dina data** på skärmen som visas.

![Anslut dina egna data](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-16.png)

Därifrån kan du ansluta dina egna data och välja hur många dagars data som ska läsas in. Du kan läsa in upp till 365 dagars data. Du måste logga in med samma e-postadress som du använder för att logga in på LinkedIn Sales Navigator via webbplatsen. 

![Logga in](media/desktop-connect-linkedin-sales-navigator/linkedin-sales-navigator-17.png)

mallappen uppdaterar sedan datan i appen med dina data. Du kan också konfigurera en schemalagd uppdatering för att datan i din app ska vara lika aktuell som din uppdateringsfrekvens anger. 

När datan har uppdaterats kan du se att appen är ifylld med dina egna data.

## <a name="getting-help"></a>Få hjälp

Om du stöter på problem när du ansluter till dina data kan du kontakta LinkedIn Sales Navigator-supporten på https://www.linkedin.com/help/sales-navigator. 

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

