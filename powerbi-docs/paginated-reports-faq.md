---
title: 'Sidnumrerade rapporter i Power BI: Vanliga frågor och svar (förhandsversion)'
description: I den här artikeln finns svar på vanliga frågor om sidnumrerade rapporter. Dessa rapporter innehåller mycket formatering och utdatan har ett utseende som är optimerat för utskrift eller PDF-generering.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: d3fdf9b568aa13ba5a8437c684835e0fce803d19
ms.sourcegitcommit: bb4cf3469b44e451153c469725a9069dcd548809
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53649455"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Sidnumrerade rapporter i Power BI: Vanliga frågor och svar (förhandsversion)

I den här artikeln finns svar på vanliga frågor om sidnumrerade rapporter. Dessa rapporter innehåller mycket formatering och utdatan har ett utseende som är optimerat för utskrift eller PDF-generering. De kallas ”sidnumrerade” eftersom de är formaterade att passa för flersidiga dokument. Sidnumrerade rapporter baseras på tekniken för RDL-rapporter i SQL Server Reporting Services. 

I den här artikeln finns svar på vanliga frågor om sidnumrerade rapporter i Power BI Premium, samt om Report Builder som är ett fristående verktyg för redigering av sidnumrerade rapporter. Du måste ha en Power BI Pro-licens för att kunna publicera en rapport till tjänsten. Du kan publicera och dela sidnumrerade rapporter på Min arbetsyta eller på apparbetsytor, så länge arbetsytan finns i en Power BI Premium-kapacitet. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Hur stor Premium-kapacitet måste jag ha för sidnumrerade rapporter?

Arbetsbelastningen för sidnumrerade rapporter finns på SKU:erna P1–P3 som en förhandsversion.  Du kan också använda den för test-/utvecklingsscenarier med SKU:erna A4–A6.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Vilket tröskelvärde för maximalt minne kan jag ha för sidnumrerade rapporter i min kapacitet?

Du kan för närvarande bara reservera 50 % av minnet för den här arbetsbelastningen. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Hur fungerar användaråtkomst för sidnumrerade rapporter?

Användaråtkomsten till sidnumrerade rapporter är likadan som användaråtkomsten till allt innehåll i Power BI-tjänsten 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Hur aktiverar/inaktiverar jag arbetsbelastningens sidnumrerade rapporter?

Kapacitetsadministratören kan aktivera eller inaktivera arbetsbelastningen för sidnumrerade rapporter på kapacitetsadministratörens portalsida.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Hur övervakar jag användningen av sidnumrerade rapporter i min klientorganisation?

Office 365-spårningsloggarna visar användningen av den här rapporttypen vid följande händelser: 

- Visa Power BI-rapport
- Ta bort Power BI-rapport
- Skapa Power BI-rapport
- Power BI-rapport hämtades

Fältet ReportType har värdet ”PaginatedReport” för att identifiera sidnumrerade rapporter i stället för Power BI-rapporter.

Dessutom innehåller spårningsloggarna följande händelser för sidnumrerade rapporter:

- Power BI-datamängd har bundits till gateway
- Identifiera datakällan för Power BI
- TakeOverDataset

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Kan jag övervaka den här arbetsbelastningen med övervakningsappen för Premium-kapacitet?

Ja, övervakning är tillgängligt som en ny flik med samma relevanta uppgifter som du har för dina Power BI-datauppsättningar.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Måste jag ha en Pro-licens för att kunna skapa och publicera sidnumrerade rapporter?

Ja. Du kan inte ladda upp rapporter till arbetsytan utan en Pro-licens. Du kan ladda ned och prova Report Builder utan Pro-licens, men du kan inte publicera de sidnumrerade rapporter som du skapar. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Vad händer om jag har en sidnumrerad rapport i en arbetsyta och arbetsbelastningen för den sidnumrerade rapporten stängs av?

Du får ett felmeddelande och du kan inte se rapporten förrän arbetsbelastningen aktiveras igen. Du kan fortfarande ta bort rapporten från arbetsytan.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Vad är standardminnet för de olika Premium-SKU:er som stöds för sidnumrerade rapporter?

Standardminnet i varje Premium-SKU för sidnumrerade rapporter:

- **P1/A4**: 20 % standard, 10 % minimum
- **P2/A5**: 20 % standard, 5 % minimum
- **P3/A6**: 20 % standard, 2,5 % minimum

## <a name="general"></a>Allmänt

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>När ska jag använda en sidnumrerad rapport jämfört med en Power BI-rapport?

Sidnumrerade rapporter är bäst vid scenarier som kräver mycket formaterade och har ett bra utseende på utdatan som är optimerad för utskrift eller PDF-generering.  En resultaträkning är ett bra exempel på typ av rapport som du förmodligen vill skapa som en sidnumrerad rapport.  

Power BI-rapporter är optimerade för utforskning och interaktivitet.  En försäljningsrapport där olika säljare vill dela upp data i samma rapport för deras specifika region/bransch/kund och se hur ändringen siffror som skulle vara bäst hanteras av en Power BI-rapport.

### <a name="the-documentation-says-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>Dokumentationen säger att Report Builder är det prioriterade redigeringsverktyget. Kan jag skapa sidnumrerade rapporter i SQL Server Data Tools för Power BI?

Ja, men med Power BI-tjänsten kan du bara ladda upp ett enskilt objekt i taget, så många av de scenarier som författare använder med SQL Server Data Tools (SSDT) stöds inte än. Se en fullständig [lista med funktioner som inte stöds](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) senare i dessa vanliga frågor och svar.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Vilka versioner av Report Builder stöder ni?

Använd den senaste versionen av SQL Server 2016 Report Builder för att skapa och publicera dina rapporter till Power BI-tjänsten. Installera [Report Builder från Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Hur gör jag för att flytta befintliga rapporter som jag har sparat i SQL Server Reporting Services till Power BI?

Du måste ladda ned rapporten från servern och sedan överföra den till Power BI via portalen.  Det finns inget migreringsverktyg tillgängligt just nu, men vi kommer kanske skapa ett sådant när vi har slutfört den offentliga förhandsversionen och fått lämplig funktionsparitet mellan produkterna.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Kan jag öppna rapporter och publicera dem direkt till tjänsten?

Just nu kan du inte det. Vi lägger till stöd för att öppna rapporter och publicera dem direkt till tjänsten från Report Builder framöver, på samma sätt som du kan göra med Power BI Desktop.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Vilka sidnumrerade rapportfunktioner i SSRS stöds inte ännu i Power BI?

Sidnumrerade rapporter stöder för närvarande inte följande objekt:

- Delade datakällor
- Delade datauppsättningar
- Underrapporter
- Klicka igenom och detaljerade åtgärder
- Länkade rapporter
- Bokmärken
- Bing-kartskikt
- Anpassade teckensnitt

Du får ett felmeddelande om du försöker ladda upp en fil som har en funktion som inte stöds i Power BI-tjänsten, förutom växla/sortera.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Vilka datakällor stöds för närvarande för sidnumrerade rapporter?

Vi stöder Azure SQL Database, SQL Server och både tabellmodeller (DAX) och flerdimensionella modeller (MDX) i SQL Server Analysis Services (SSAS) med hjälp av en lokal gateway.

När SSAS nås via gatewayen, lagras den användare vars autentiseringsuppgifter är lagrade behov med förhöjd behörighet i SSAS som arbetar via gatewayen.

### <a name="what-authentication-methods-do-you-support"></a>Vilka autentiseringsmetoder stöder ni?

För närvarande måste du lagra ett användarnamn och ett lösenord med datakällan i portalen eller gatewayen.  Ytterligare autentiseringsmetoder för exempelvis säkerhet på radnivå kommer senare i förhandsversionen.

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Kan jag använda en Power BI-datamängder som en datakälla för min sidnumrerade rapport?

Inte ännu, men detta stöd planeras snart.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Kan jag använda lagrade procedurer via gatewayen?

Du kan använda en lagrad procedur via gatewayen, men du kan få problem i vissa scenarier om den lagrade proceduren har parametrar.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Vilka exportformat är tillgängliga för min rapport i Power BI-tjänsten?

Du kan exportera till Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF., .CSV, XML och MHTML.

### <a name="can-i-print-paginated-reports"></a>Kan jag skriva ut sidnumrerade rapporter?

Ja, utskrift är tillgängligt för sidnumrerade rapporter, med en ny och förbättrad förhandsgranskningsmiljö. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>Är e-postprenumerationer tillgängliga än för sidnumrerade rapporter?

Nej, men e-postprenumerationer kommer snart.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Vilka funktioner från SSRS kommer att stödjas i Power BI-tjänsten?

Vår plan är att tillhandahålla funktionsparitet för de flesta fall. I vissa fall är det ändå möjligt att det inte är särskilt meningsfullt att försöka ändra saker i SSRS och Power BI så att de passar befintliga SSRS-mönster.  Till exempel kan inte de olika behörighetsmodellerna i Power BI mappas tillbaka till SSRS.  Vi kommer att lyssna på feedbacken från kunder och partner när vi tar sådana här sorts beslut.

### <a name="can-i-run-custom-code-in-my-report"></a>Kan jag köra anpassad kod i min rapport?

Ja, vi har stöd för möjligheten att köra kod i dina rapporter som i SSRS.

### <a name="does-this-mean-ssrs-is-going-away"></a>Innebär detta att SSRS kommer att försvinna?

Inte alls.  Med det här nya erbjudandet får kunder ett molnbaserat alternativ för sina sidnumrerade rapporter.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Kan jag använda inbäddad Power BI för att bädda in min sidnumrerade rapporter i en app som jag värd för?

Vi planerar att stödja det här scenariot med befintliga API:er för Power BI, men vi har inte ännu någon tidsram för när det här scenariot är tillgängligt.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Kan jag få detaljerad information från en Power BI-rapport till en sidnumrerad rapport?

Inte ännu, men vi planerar absolut att stödja det här scenariot.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Kan jag dela mitt sidnumrerade rapportinnehåll via en Power BI-app?

För närvarande kan du dela individuella sidnumrerade rapporter med andra användare via delningsåtgärden i portalen eller via verktygsfältet. Vi har ännu inte stöd för delning i en app, men förväntar att ha detta snart. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Kommer andra rapportspecifika funktioner i Power BI, t.ex. fästa rapportpaneler på instrumentpaneler, fungera med sidnumrerade rapporter?

Vi planerar att rapporterna ska ha stöd för samma större scenarier i tjänsten så mycket som möjligt.  Även om verktyget för att skapa dem skiljer sig, är det ur ett konsumentperspektiv bara en annan rapport i listan i portalen. De spelar ingen roll hur den skapades, den kan göra vad de behöver.  Ett bra exempel på den här funktionspariteten är det planerade kommentarsstödet. Även om själva funktionen fungerar lite annorlunda för varje rapporttyp, kommer du att kunna använda kommentarer för båda.

### <a name="are-you-planning-to-create-a-new-authoring-tool-for-paginated-reports-in-the-power-bi-service--we-cant-do-everything-we-need-to-with-report-builder-today"></a>Planerar du att skapa ett nytt redigeringsverktyg för sidnumrerade rapporter i Power BI-tjänsten?  Vi kan inte göra allt vi behöver med Report Builder i dag.

Vi överväger fortfarande olika alternativ här för de bästa verktygsfunktionerna för sidnumrerade rapporter i Power BI. 

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Planeras ett migreringsverktyg så att SSRS-kunder kan flytta sina befintliga rapporter och tillgångar till Power BI?

Vi utvärderar alternativ för att möjliggöra att innehåll flyttas till Power BI på ett automatiserat sätt, men det här kommer inte att bli tillgängligt förrän efter GA (allmän tillgänglighet).

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>Kommer jag någonsin att skapa både sidnumrerade rapporter och Power BI-rapporter i ett enda redigeringsverktyg?

Möjligtvis.  Vi undersöker för närvarande sätt för hur det här scenariot kunde möjliggöras, eller överväger sätt för att helt enkelt distribuera redigeringsverktygen tillsammans som en enda BI-svit jämfört med att ha enskilda nedladdningar/anpassningar.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Finns det en rapportvisningskontroll för sidnumrerade rapporter i Power BI-tjänsten?

Nej, en rapportvisningskontrollen är inte tillgängligt för tillfället.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kan man söka efter sidnumrerade rapporter från den nya startupplevelsen i Power BI-tjänsten?

Nej, det går inte att för närvarande söka efter dina sidnumrerade rapporter från startsidan.  Du visas dock i andra delar av den nya startupplevelsen.

## <a name="next-steps"></a>Nästa steg

- [Installera Report Builder från Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613)
- [Självstudie: Skapa en sidnumrerad rapport](paginated-reports-quickstart-aw.md)
