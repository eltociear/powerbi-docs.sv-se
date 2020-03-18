---
title: 'Sidnumrerade rapporter i Power BI: Vanliga frågor och svar'
description: I den här artikeln finns svar på vanliga frågor om sidnumrerade rapporter. Dessa rapporter innehåller mycket formatering och utdatan har ett utseende som är optimerat för utskrift eller PDF-generering.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/28/2020
ms.openlocfilehash: d9d97715853ab87ac507ff41117ab176b8620e2e
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79205261"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Sidnumrerade rapporter i Power BI: Vanliga frågor och svar 

I den här artikeln finns svar på vanliga frågor om sidnumrerade rapporter. Dessa rapporter innehåller mycket formatering och utdatan har ett utseende som är optimerat för utskrift eller PDF-generering. De kallas ”sidnumrerade” eftersom de är formaterade att passa för flersidiga dokument. Sidnumrerade rapporter baseras på tekniken för RDL-rapporter i SQL Server Reporting Services. 

I den här artikeln finns svar på vanliga frågor om sidnumrerade rapporter i Power BI Premium, samt om Report Builder som är ett fristående verktyg för redigering av sidnumrerade rapporter. Du måste ha en Power BI Pro-licens för att kunna publicera en rapport i tjänsten. Du kan publicera och dela sidnumrerade rapporter på Min arbetsyta eller på arbetsytor så länge arbetsytan ligger i en Power BI Premium-kapacitet. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Hur stor Premium-kapacitet måste jag ha för sidnumrerade rapporter?

Arbetsbelastningen för sidnumrerade rapporter finns på SKU:erna P1–P3.  Du kan även använda med SKU:erna A4–A6 för inbäddnings- eller test-/utvecklingsscenarier.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Vilket tröskelvärde för maximalt minne kan jag ha för sidnumrerade rapporter i min kapacitet?

Du kan använda upp till 100 % av minnet för den här arbetsbelastningen.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Hur fungerar användaråtkomst för sidnumrerade rapporter?

Användaråtkomsten till sidnumrerade rapporter är likadan som användaråtkomsten till allt innehåll i Power BI-tjänsten 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Hur aktiverar/inaktiverar jag arbetsbelastningens sidnumrerade rapporter?

Kapacitetsadministratören kan aktivera eller inaktivera arbetsbelastningen för sidnumrerade rapporter på kapacitetsadministratörens portalsida.  Som standard är arbetsbelastningen för alla nya kapaciteter som du skapar, men den kommer inte att förbruka minne förrän du har laddat upp din första sidnumrerade rapport.  

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

Du kan ladda upp sidnumrerade rapporter till din Min arbetsyta utan en Pro-licens, förutsatt att det är i en Premium-kapacitet.  För andra arbetsytor måste du ha en Pro-licens för att skapa och publicera innehåll till dem. Vi rekommenderar att du hämtar och använder Power BI Report Builder även utan Pro-licens, men du kan inte publicera de sidnumrerade rapporter som du skapar utan licens. 

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

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>Enligt dokumentationen är Power BI Report Builder det prioriterade redigeringsverktyget. Kan jag skapa sidnumrerade rapporter i SQL Server Data Tools för Power BI?

Ja, men med Power BI-tjänsten kan du bara ladda upp ett enskilt objekt i taget, så många av de scenarier som författare använder med SQL Server Data Tools (SSDT) stöds inte än. Se en fullständig [lista med funktioner som inte stöds](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) senare i dessa vanliga frågor och svar.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Vilka versioner av Report Builder stöder ni?

Vi har lanserat Power BI Report Builder som det primära redigeringsverktyget för sidnumrerade rapporter i Power BI-tjänsten. Installera [Power BI Report Builder från Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Hur gör jag för att flytta befintliga rapporter som jag har sparat i SQL Server Reporting Services till Power BI?

Ett projekt på GitHub har nu stöd för migrering av innehåll från SQL Server Reporting Services till Power BI.  Visa information och ladda ned verktyget här: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Kan jag öppna rapporter och publicera dem direkt till tjänsten?

Ja. Vi har lagt till stöd för att öppna rapporter och publicera dem direkt till tjänsten från Power BI Report Builder.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Vilka sidnumrerade rapportfunktioner i SSRS stöds inte ännu i Power BI?

Sidnumrerade rapporter stöder för närvarande inte följande objekt:

- Delade datakällor
- Delade datauppsättningar
- Underrapporter
- Visning av detaljerad information och klickbaserad funktion för åtkomst till andra rapporter
- Länkade rapporter
- Bing-kartskikt
- Anpassade teckensnitt

Du får ett felmeddelande om du försöker ladda upp en fil som har en funktion som inte stöds i Power BI-tjänsten, förutom växla/sortera.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Vilka datakällor stöds för närvarande för sidnumrerade rapporter?

Du hittar en lista med datakällor i artikeln [Datakällor som stöds för sidnumrerade Power BI-rapporter](paginated-reports-data-sources.md). 

### <a name="what-authentication-methods-do-you-support"></a>Vilka autentiseringsmetoder stöder ni?

Vi stöder enkel inloggning för Azure Analysis Services, Azure SQL Database och Power BI-datakällor.  Vi stöder även OAuth för Azure SQL Database och Azure Analysis Services.  För andra datakällor måste du för närvarande lagra ett användarnamn och ett lösenord med datakällan i portalen eller gatewayen.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Kan jag använda en Power BI-datamängder som en datakälla för min sidnumrerade rapport?

Ja, vi stöder Power BI-datamängder som datakällor för sidnumrerade rapporter.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Kan jag använda lagrade procedurer via gatewayen?

Ja, lagrade procedurer via gatewayen stöds för SQL Server-datakällor, inklusive de som använder parametrar.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Vilka exportformat är tillgängliga för min rapport i Power BI-tjänsten?

Du kan exportera till Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF., .CSV, XML och MHTML.

### <a name="can-i-print-paginated-reports"></a>Kan jag skriva ut sidnumrerade rapporter?

Ja, utskrift är tillgängligt för sidnumrerade rapporter, med en ny och förbättrad förhandsgranskningsmiljö. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>Är e-postprenumerationer tillgängliga för sidnumrerade rapporter?

Ja, e-postprenumerationer stöds fullt ut för sidnumrerade rapporter och har stöd för sex olika filformat och parametervärden.

### <a name="can-i-run-custom-code-in-my-report"></a>Kan jag köra anpassad kod i min rapport?

Ja, vi har stöd för möjligheten att köra kod i dina rapporter som i SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Kan jag använda inbäddad Power BI för att bädda in min sidnumrerade rapporter i en app som jag värd för?

SaaS-inbäddning, inklusive stöd för säker inbäddning, är redan tillgängligt. Om det gäller inbäddning av PaaS kan du gå igenom självstudien [Bädda in sidnumrerade Power BI-rapporter i en app för dina kunder](../developer/embed-paginated-reports-customers.md).

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Kan jag få detaljerad information från en Power BI-rapport till en sidnumrerad rapport?

Ja, detta kan utföras med hjälp av URL-parametrar med dina sidnumrerade rapporter.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Kan jag dela mitt sidnumrerade rapportinnehåll via en Power BI-app?

Ja, sidnumrerade rapporter har stöd för att distribueras med appar från både v1- och v2-arbetsytor. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Kommer andra rapportspecifika funktioner i Power BI, t.ex. fästa rapportpaneler på instrumentpaneler, fungera med sidnumrerade rapporter?

Vi planerar att rapporterna ska ha stöd för samma större scenarier i tjänsten så mycket som möjligt.  Även om verktyget för att skapa dem skiljer sig, är det ur ett konsumentperspektiv bara en annan rapport i listan i portalen. De spelar ingen roll hur den skapades, den kan göra vad de behöver.  Ett bra exempel på den här funktionspariteten är det planerade kommentarsstödet. Även om själva funktionen fungerar lite annorlunda för varje rapporttyp, kommer du att kunna använda kommentarer för båda.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Finns det en rapportvisningskontroll för sidnumrerade rapporter i Power BI-tjänsten?

Nej, en rapportvisningskontrollen är inte tillgängligt för tillfället.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kan man söka efter sidnumrerade rapporter från den nya startupplevelsen i Power BI-tjänsten?

Ja, du kan nu söka efter dina sidnumrerade rapporter från startsidan.  De visas också i andra delar av den nya startupplevelsen.

## <a name="next-steps"></a>Nästa steg

- [Installera Power BI Report Builder från Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Självstudie: Skapa en sidnumrerad rapport](paginated-reports-quickstart-aw.md)
