---
title: Vad är Power BI?
description: Översikt över Power BI och hur de olika delarna fungerar ihop – Power BI Desktop i Power BI-tjänsten, Power BI mobile, rapportservern och Power BI embedded.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7236caba1c7a8eb07e93c6f2af7068141b8ac3a7
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413038"
---
# <a name="what-is-power-bi"></a>Vad är Power BI?
**Power BI** är en samling programvarutjänster, appar och kopplingar som arbetar tillsammans för att förvandla dina orelaterade datakällor till sammanhängande, visuellt fördjupande och interaktiva insikter. Dina data kan finnas i ett Excel-kalkylblad eller i en samling molnbaserade och lokala hybridinformationslager. Powerbi kan du enkelt ansluta till dina datakällor, visualisera och Upptäck vad som är viktigt och dela det med någon eller alla du vill.

![diagram som visar indatakällor för Power BI](media/power-bi-overview/power-bi-input-new.png)

Powerbi kan vara enkla och snabba, kan skapa snabba insikter från ett Excel-kalkylblad eller en lokal databas. Men Power BI är också robust och i företagsklass redo för möjliggör omfattande modellering och analys i realtid samt anpassad utveckling. Det kan vara ditt personliga visualiseringsverktyg för rapportering och och även fungera som analys- och för grupprojekt, avdelningar eller hela bolag.

## <a name="the-parts-of-power-bi"></a>Power BI:s delar
Powerbi består av: 
- Ett Windows-skrivbordsprogram kallas **Power BI Desktop**
- En online SaaS (*programvara som en tjänst*) tjänst som kallas den **Power BI-tjänsten** 
- Power BI **mobilappar** för Windows, iOS och Android-enheter

![Power BI Desktop, service, mobile](media/power-bi-overview/power-bi-blocks.png)

Dessa tre delar&mdash;Power BI Desktop och tjänsten mobilapparna&mdash;är utformade för att låta användare skapa, dela och använda affärsinsikter på det sätt som passar dem eller deras roll så effektivt som möjligt.

Med hjälp av en fjärde del som kallas **Power BI-rapportserver** kan du publicera Power BI-rapporter som du har skapat i Power BI Desktop till en lokal rapportserver. Läs mer om [Power BI-rapportservern](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Hur Power BI matchar din roll
Hur du använder Power BI kan bero på vilken roll du har i ett projekt eller i ett team. Andra personer kan i andra roller använda Power BI på olika sätt.

Till exempel använder du kanske själv främst **Power BI-tjänsten**. Men din siffertokiga kollega som är mer intresserad av affärsrapporter kanske i större utsträckning använder sig av **Power BI Desktop** för att skapa rapporter och sedan publicera dem till Power BI-tjänsten, där du läser dem. En annan kollega på FÖRSÄLJNINGSSIDAN kanske främst använder sin **Power BI-mobilapp** att övervaka sina försäljningskvoter och för att visa detaljer nya försäljningstillfälle.

Om du är utvecklare kan du använda Power BI:s API:er för att skicka data till datauppsättningar eller för att bädda in instrumentpaneler och rapporter i dina egna anpassade program. Har du en idé till ett nytt visuellt objekt? Skapa det själv och dela det med andra.  

Du kan också använda delarna i Power BI vid olika tidpunkter, beroende på vad du försöker åstadkomma eller din roll för ett visst projekt.

Hur du använder Power BI kan ändra enligt vilken funktion eller tjänst i Power BI som är det bästa verktyget för din aktuella situation. Exempel: du kan använda Power BI Desktop för att skapa rapporter för ditt team om kundengagemangsstatistik och du kan visa lager och tillverkning i en realtidsinstrumentpanel i Power BI-tjänsten. Varje del av Power BI finns tillgänglig för dig, vilket också är orsaken till att det är så flexibelt och attraktivt.

Utforska dokument som hör till din roll:
- Power BI för [***designers***](desktop-what-is-desktop.md)
- Power BI för [***konsumenter***](consumer/end-user-consumer.md)
- Power BI för [***utvecklare***](developer/what-can-you-do.md)
- Power BI för [***administratörer***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>Arbetsflödet i Power BI
Ett vanligt arbetsflöde i Power BI börjar genom att ansluta till datakällor och skapa en rapport i Power BI Desktop. Sedan publicera rapporten från Power BI Desktop till Power BI-tjänsten och dela den så att slutanvändare i Power BI-tjänsten och mobila enheter kan visa och interagera med rapporten.
Det här är det vanliga arbetsflödet, som visar hur de tre huvuddelarna i Power BI kompletterar varandra.

Här är en detaljerad [jämförelse av Power BI Desktop och Power BI-tjänsten](service-service-vs-desktop.md).

Men vad händer om du inte är redo att flytta till molnet och vill behålla dina rapporter bakom en företagsbrandvägg?  Då läser du vidare.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Lokal rapportering med Power BI-rapportservern
Skapa, distribuera och hantera Power BI mobila och sidnumrerade rapporter lokalt med utbud av färdiga att använda verktyg och tjänster som Power BI Report Server tillhandahåller.

![diagram för lokal rapportering](media/power-bi-overview/power-bi-report-server2.png)

Power BI-rapportservern är en lösning som du distribuerar bakom brandväggen och som skickar dina rapporter till rätt användare på olika sätt, oavsett om de som får dem ska visa dem i en webbläsare, på en mobil enhet eller som ett e-postmeddelande. Och eftersom Power BI-rapportservern är kompatibel med Power BI i molnet, kan du flytta över till molnet när du är redo. 

Läs mer om [Power BI-rapportservern](report-server/get-started.md).

## <a name="next-steps"></a>Nästa steg
- [Snabbstart: Lär dig grunderna i Power BI-tjänsten](service-the-new-power-bi-experience.md)   
- [Självstudier: Kom igång med Power BI-tjänsten](service-get-started.md)
- [Snabbstart: Ansluta till data i Power BI Desktop](desktop-quickstart-connect-to-data.md)
