---
title: Power BI-tjänsten – grundläggande begrepp för användare
description: Power BI-tjänstens appar, arbetsytor, instrumentpaneler, rapporter, datamängder och arbetsböcker.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.custom: seodec18
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 2e41a3f5b1d1bd945e1ab4566abed1589b20c148
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264919"
---
# <a name="basic-concepts-for-the-power-bi-service-consumers"></a>Grundläggande begrepp för användare av Power BI-tjänsten

Den här artikeln förutsätter att du redan har läst [översikten över Power BI](../power-bi-overview.md) och har identifierat dig själv som ***användare*** av Power BI. Användare får Power BI-innehåll såsom instrumentpaneler och rapporter från kollegor. Användare använder Power BI-tjänsten, som är den webbplatsbaserade versionen av Power BI.

Du kommer utan tvekan att höra talas om ”Power BI Desktop” eller bara ”Desktop”. Det är det fristående verktyget som används av *designers* som skapar och delar instrumentpaneler och rapporter med dig. Det är viktigt att veta att det även finns andra Power BI-verktyg. Om du är användare kommer du bara att arbeta med Power BI-tjänsten. Den här artikeln gäller endast för Power BI-tjänsten.

## <a name="terminology-and-concepts"></a>Termer och begrepp

Den här artikeln är inte en visuell genomgång av Power BI eller en praktisk självstudie. I stället är den en översiktsartikel som kommer att göra dig bekant med termer och begrepp i Power BI. Här kommer du att lära dig jargongen och hur det ser ut i allmänhet. Gå till [Snabbstart – Navigera i Power BI-tjänsten](end-user-experience.md) för en genomgång av Power BI-tjänsten och dess navigering.

## <a name="open-the-power-bi-service-for-the-first-time"></a>Öppna Power BI-tjänsten för första gången

De flesta Power BI-användare skaffar Power BI-tjänsten eftersom 1) deras företag köper licenser och 2) en administratör tilldelar licenserna till medarbetare som du.

För att komma igång öppnar du en webbläsare och anger **app.powerbi.com**. Första gången du öppnar Power BI-tjänsten ser det ut ungefär så här:

![En skärmbild av Power BI-tjänstens välkomstskärm.](media/end-user-basic-concepts/power-bi-open.png)

När du använder Power BI anpassar du det som visas när du öppnar webbplatsen varje gång. Till exempel föredrar vissa att Power BI öppnas på **startsidan**, medan andra har en favoritinstrumentpanel som de vill se först. Oroa dig inte, i den här artikeln får du lära dig hur du kan anpassa din upplevelse.

- [Introduktion till Power BI-start och global sökning](https://powerbi.microsoft.com/blog/introducing-power-bi-home-and-global-search)

- [Aktuella instrumentpaneler i Power BI-tjänsten](end-user-featured.md)

![En skärmbild som visar startsidevyn och instrumentpanelsvyn.](media/end-user-basic-concepts/power-bi-first.png)

Men innan vi fortsätter ska vi gå tillbaka lite och prata om de byggstenar som utgör Power BI-tjänsten.

_______________________________________________________

## <a name="power-bi-content"></a>Power BI-innehåll

### <a name="introduction-to-building-blocks"></a>Introduktion till byggstenar

För Power BI-användare är de fem byggblocken: ***visualiseringar***, ***instrumentpaneler***, ***rapporter***, ***appar*** och ***datamängder***. Dessa kallas ibland *Power BI*-***innehåll***. *Innehåll* finns i ***arbetsytor***. Ett vanligt arbetsflöde inbegriper alla dessa byggstenar: En *Power BI-designer* (gul i diagrammet nedan) samlar in data från *datamängder*, hämtar in dem till Power BI för analys, skapar *rapporter* med *visualiseringar* som visar intressanta fakta och insikter, fäster visualiseringar från rapporter på en instrumentpanel och delar rapporterna och instrumentpanelerna med *användare* som du (svarta i diagrammet nedan). *Designern* delar dem i form av *appar* eller andra typer av delat innehåll.

![Ett grundläggande arbetsflödesdiagram i Power BI.](media/end-user-basic-concepts/power-bi-workflow.png)

I dess mest grundläggande form:

- ![En skärmbild av visualiseringsikonen.](media/end-user-basic-concepts/visual.png) En ***visualisering*** (eller ett *visuellt objekt*) är en typ av diagram som skapats av *Power BI-designers*. De visuella objekten visar data från *rapporter* och *datamängder*. Normalt skapar *designers* visuella objekt i Power BI Desktop.

    Mer information finns i [Interagera med visuella objekt i rapporter, instrumentpaneler och appar](end-user-visualizations.md).

- ![En skärmbild av databasikonen.](media/end-user-basic-concepts/power-bi-dataset-icon.png) En *datamängd* är en container med data. Det kan till exempel vara en Excel-fil från Världshälsoorganisationen. Det kan också vara en företagsägd databas över kunder eller en Salesforce-fil.  

- ![En skärmbild av instrumentpanelsikonen.](media/end-user-basic-concepts/dashboard.png) En *instrumentpanel* är en enskild skärm med interaktiva visuella objekt, texter och bilder. En instrumentpanel samlar in dina viktigaste mått på en skärm för att ge en bild över något eller besvara en fråga. Innehållet på instrumentpanelen kommer från en eller flera rapporter och en eller flera datamängder.

    Mer information finns i [Instrumentpaneler för Power BI-tjänstens användare](end-user-dashboards.md).

- ![En skärmbild av rapportikonen.](media/end-user-basic-concepts/report.png) En *rapport* är en eller flera sidor med interaktiva visuella objekt, text och grafik som tillsammans utgör en enskild rapport. Power BI baserar en rapport på en enda datamängd. Ofta organiserar tjänsten rapportsidorna för att handla om ett viktigt intresseområde eller för att besvara en enskild fråga.

    Mer information finns i [Rapporter i Power BI](end-user-reports.md).

- ![En skärmbild av appikonen.](media/end-user-basic-concepts/app.png) En *app* är en metod för *designers* att paketera och dela relaterade instrumentpaneler och rapporter tillsammans. *Användare* får vissa appar automatiskt men kan söka efter andra appar som skapats av kollegor eller av communityn. Till exempel erbjuder externa tjänster som du kanske redan använder, t.ex. Google Analytics och Microsoft Dynamics CRM, också Power BI-appar.

Bara för tydlighetens skull: om du är en ny användare och loggar in i Power BI för första gången, visas inte instrumentpaneler, appar eller rapporter ännu.

_______________________________________________________

## <a name="datasets"></a>Datauppsättningar

En *datamängd* är en samling data som *designers* importerar eller ansluter till och sedan använder för att skapa rapporter och instrumentpaneler. Som användare kommer du inte att interagera direkt med datamängder, men det är fortfarande bra att förstå syftet med dem.  

Varje datamängd representerar en enskild datakälla. Källan kan exempelvis vara en Excel-arbetsbok på OneDrive, en lokal SQL Server Analysis Services-datamängd i tabellformat eller en Salesforce-datamängd. Power BI har stöd för många olika datakällor.

När en designer delar en app med dig, kan du se vilka datamängder som designern har inkluderat i appen.

![Skärmbild av Power BI:s användargränssnitt som visar valda appar och en pil som pekar på avsnittet Datamängder på arbetsytan.](media/end-user-basic-concepts/power-bi-dataset-list.png)

Om datamängd ...

- Kan användas och om igen av en rapportdesigner för att skapa instrumentpaneler och rapporter

- Kan användas för att skapa många olika rapporter

- Visuella objekt från en datamängd kan visas på många olika instrumentpaneler

  ![En graf som visar en datamängd med många-till-en-relationer](media/end-user-basic-concepts/drawing2.png)

Designers kan dessutom använda datamängder från andra arbetsytor för att skapa innehåll (rapporter, instrumentpaneler) på sin arbetsyta. Power BI visar dessa datamängder med hjälp av ikonen för refererade datamängder:

![En skärmbild av en databas med länkikon.](media/end-user-basic-concepts/power-bi-dataset-reference-icon.png)

Nu går vi vidare till nästa byggsten – visualiseringar.

_______________________________________________________

## <a name="visualizations"></a>Visualiseringar

Visualiseringar (även kända som visuella objekt) visar insikter som Power BI har upptäckt i aktuella data. Visualiseringar gör det lättare att tolka insikter eftersom hjärnan förstår en bild snabbare än ett kalkylblad med siffror.

Några exempel på de visualiseringar som du stöter på i Power BI är: vattenfallsdiagram, trädkartor, cirkeldiagram, trattdiagram, kort, punktdiagram och mätare:

   ![En skärmbild med åtta exempel på visuella objekt.](media/end-user-basic-concepts/power-bi-visuals.png)

Se den [fullständiga listan över visualiseringar som ingår i Power BI](../power-bi-visualization-types-for-reports-and-q-and-a.md).

Visualiseringar, som även kallas *anpassade visuella objekt*, finns också tillgängliga från communityt. Om du får en rapport med ett visuellt objekt som du inte känner igen är det sannolikt ett anpassat visuellt objekt. Om du behöver hjälp med att tolka det anpassade visuella objektet, letar du upp namnet på *designern* av rapporten eller instrumentpanelen och kontaktar denne.

En visualisering i en rapport ...

- Kan förekomma flera gånger i samma rapport

- Kan användas på många olika instrumentpaneler

_______________________________________________________

## <a name="reports"></a>Rapporter

En Power BI-rapport är en eller flera sidor med visualiseringar, grafik och text. Alla visualiseringar i en rapport kommer från en enda datauppsättning. *Designers* delar rapporter med *användare* som [interagerar med rapporterna i *läsvyn*](end-user-reading-view.md).

![Skärmbild av en rapport med flikar.](media/end-user-basic-concepts/power-bi-report2.png)

En rapport ...

- Kan associeras med flera instrumentpaneler (paneler fästa från en rapport kan visas på flera instrumentpaneler)

- Kan skapas med hjälp av data från endast en datamängd  

- Kan ingå i flera appar

  ![En graf som visar relationerna för en rapport.](media/end-user-basic-concepts/drawing5.png)

_______________________________________________________

## <a name="dashboards"></a>Instrumentpaneler

En instrumentpanel representerar en anpassad vy av någon delmängd av de underliggande datamängderna. *Designers* skapar instrumentpaneler och delar dem med *användare*, antingen enskilt eller som en del av en app. En instrumentpanel är en enskild arbetsyta som innehåller *paneler*, grafik och text.

  ![Skärmbild av ett exempel på en instrumentpanel](media/end-user-basic-concepts/power-bi-dashboard.png)

En panel är en rendering av ett visuellt objekt som en *designer* *fäster* till exempel från en rapport till en instrumentpanel. Varje fäst panel visar en [visualisering](end-user-visualizations.md) som Power BI har skapat från en datamängd och fästs på den instrumentpanelen. En panel kan även innehålla en hel rapportsida och kan innehålla liveuppspelningsdata eller en video. Det finns många sätt som *designers* kan använda för att lägga till paneler på instrumentpaneler. Det finns för många för att vi ska kunna ta upp dem i den här översikten. Läs mer i [Paneler på instrumentpanelen i Power BI](end-user-tiles.md).

Användare kan inte redigera instrumentpaneler. Du kan dock lägga till kommentarer, visa relaterade data, ange en instrumentpanel som favorit, prenumerera med mera.

Vad är syftet med instrumentpaneler?  Här följer några:

- få en överblick över all information som behövs för att fatta beslut

- övervaka den viktigaste informationen om verksamheten

- se till att alla kollegor är på samma sida och ser och använder samma information

- övervaka hälsotillståndet för ett företag, en produkt, en affärsenhet, en marknadsföringskampanj osv.

- för att skapa en anpassad vy av en större instrumentpanel – alla mått som är viktiga för dig

**EN** instrumentpanel ...

- kan visa visualiseringar från många olika datauppsättningar

- kan visa visualiseringar från många olika rapporter

- kan visa visualiseringar som fästs från andra verktyg (t.ex. Excel)

  ![En graf över relationer för en instrumentpanel.](media/end-user-basic-concepts/drawing1.png)

_______________________________________________________

## <a name="apps"></a>Appar

Dessa samlingar av instrumentpaneler och rapporter organiserar relaterat innehåll tillsammans i ett enda paket. Power BI-*designers* skapar och delar dem med enskilda användare, grupper, en hel organisation eller allmänheten. Som användare kan du vara säker på att du och dina kolleger arbetar med samma data, en enskild betrodd version av sanningen.

![Skärmbild av appar har valts i det vänstra fönstret i Power BI.](media/end-user-basic-concepts/power-bi-app.png)

Apparna är enkla att hitta och installera i [Power BI-tjänsten](https://powerbi.com) och på din mobila enhet. När du installerar en app behöver du inte komma ihåg namnen på flera olika instrumentpaneler. De har samlats i en app, i webbläsaren eller på din mobila enhet.

Den här appen har tre relaterade instrumentpaneler och tre relaterade rapporter som utgör en enda app.

![Skärmbild av relaterat innehåll för den valda appen.](media/end-user-basic-concepts/power-bi-app-list.png)

Och när appförfattare släpper uppdateringar, så ser du dem automatiskt. Författaren också styr schemat för hur ofta data uppdateras i Power BI. Du behöver inte oroa dig för att hålla den uppdaterad.

Du kan hämta appar på några olika sätt:

- Appdesignern kan installera appen automatiskt på ditt Power BI-konto.

- Appdesignern kan skicka dig en direktlänk till en app.

- Du kan söka efter den i [Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi), där du hittar alla appar som du kan använda.

I Power BI på din mobila enhet kan du bara installera appar från en direktlänk och inte från AppSource. Om appdesignern installerar appen automatiskt visas den i din lista över appar.

När du har installerat appen behöver du bara välja den i applistan och välja vilken instrumentpanel eller rapport som du vill öppna och utforska först.

Jag hoppas att den här artikeln gav nyttig information om de byggstenar som utgör Power BI-tjänsten för användare.

## <a name="next-steps"></a>Nästa steg

- Granska och bokmärk [ordlistan](end-user-glossary.md)

- Få en [genomgång av Power BI-tjänsten](end-user-experience.md)

- Läs [översikten över Power BI som skrivits särskilt för användare](end-user-consumer.md)

- Titta på en video där Will går igenom de grundläggande begreppen och håller en genomgång av Power BI-tjänsten.

    <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
