---
title: Microsoft BI-omvandling
description: Se hur Microsoft har skapat en datakultur för företagets beslutsfattande. Artikeln beskriver deras strategi och vision för BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: v-pemyer
ms.openlocfilehash: 1b4f86a0e3316cc774b0f1562112f0d6e5b19a4f
ms.sourcegitcommit: f73ea4b9116ad186817ec5cc5d5f487d49cc0cb0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88638714"
---
# <a name="microsofts-bi-transformation"></a>Microsoft BI-omvandling

Den här artikeln vänder sig till IT-proffs och IT-chefer. Vi beskriver vår BI-strategi och vision som gör det möjligt för oss att kontinuerligt utnyttja våra data som en tillgång. Du får också se hur vi skapar en datakultur för affärsbeslut med Power BI.

Först lite bakgrundsinformation: I dag påverkar explosionen av datahantering både kunder och företag i en svindlande hastighet. För att lyckas i den här dataintensiva miljön måste analytiker och chefer kunna utvinna kortfattade insikter ur enorma mängder data. Den snabba utvecklingen inom Microsofts BI-verktyg har förändrat hur Microsoft självt utforskar sina data och får de insikter som krävs för att driva företaget framåt.

Så hur kan din organisation också revolutionera sin dataanvändning? Vi rekommenderar att du läser artikeln om vår BI-omvandling för att få en bättre förståelse för möjligheterna.

## <a name="microsoft-journey"></a>Microsofts resa

För flera år sedan på Microsoft uppmuntrade vår organisatoriska kultur individerna att ha ett fullständigt ägande av sina data och insikter. Vi hade även ett starkt inbyggt motstånd mot att göra saker på ett standardiserat sätt. Den organisatoriska kulturen ledde därför till utmaningar inom både rapportering och analys. Mer specifikt ledde det till:

- Inkonsekventa datadefinitioner, hierarkier, mått och nyckelindikatorer. Varje land hade till exempel sitt eget sätt att rapportera om nya intäkter. Det fanns ingen konsekvens, men mycket förvirring.
- Analytiker lägger 75 % av tiden på att samla in och kompilera data.
- 78 % av rapporterna skapas i en offlinemiljö.
- Det finns drygt 350 centraliserade finansverktyg och system.
- Cirka 30 miljoner USD läggs varje år på ”skuggprogram”.

Dessa utmaningar innebar att vi började fundera på hur vi skulle kunna göra detta bättre. Ekonomiavdelningen och andra interna team fick stöd från ledningen att omvandla affärsgranskningsprocessen, vilket ledde till att en enhetlig BI-plattform skapades som vår enda faktakälla. (Vi beskriver vår BI-plattform senare i den här artikeln.) Dessa innovationer ledde i slutänden till att affärsgranskningar gick från kompakta tabellvyer till enklare visualiseringar med fokus på företagets viktigaste delar.

Hur uppnådde vi detta lyckade resultat? Vi lyckades tack vare en centraliserad BI som hanteras av IT-avdelningen och en utökning med självservice-BI (SSBI). Vi kan beskriva det på två kreativa sätt: _central disciplin_ och _gränsflexibilitet_.

### <a name="discipline-at-the-core"></a>Central disciplin

Central disciplin innebär att IT-avdelningen behåller kontrollen genom att hantera en enda huvuddatakälla. Att leverera standardiserad företags-BI samt definiera konsekventa taxonomier och KPI-hierarkier ingår i denna disciplin. Det är viktigt att databehörigheter bara används centralt, för att säkerställa att våra användare bara kan läsa de data de behöver.

Från början insåg vi att vår BI-omvandling inte var något teknikproblem. För att lyckas lärde vi oss att först definiera framgång och sedan omvandla den till nyckeltal. Det går inte att nog understryka hur viktigt det var för oss att uppnå en enhetlig definition av våra data.

Vår omvandling inträffade inte över en natt. Vi prioriterade att ta fram ett styrkort för dotterbolagen som innehöll cirka 30 KPI:er. Under flera år utökades antalet och djupet i ämnesområdena gradvis och mer komplexa KPI-hierarkier skapades. I dag kan vi sammanställa KPI:er från kundnivå till företagsnivå. Vårt totala KPI-antal är drygt 2 000 stycken, där var och en är ett viktigt mått på framgång och justerat efter företagets mål. Alla rapporter och SSBI-lösningar inom företaget innehåller nu KPI:er som är väldefinierade, konsekventa och säkra.

### <a name="flexibility-at-the-edge"></a>Gränsflexibilitet

I utkanten av kärnan blev våra analytiker inom ekonomi, försäljning och marknadsföring mer flexibla. De drar nu nytta av möjligheten att kunna analysera data snabbare. Mer formellt kallas scenariot _hanterad självservice-BI (SSBI)_ . Vi förstår numera att hanterad SSBI ger _ömsesidiga fördelar_ för både IT-avdelningen och analytiker. Det viktigaste är att vi har kunnat optimera genom standardisering, kunskap och återanvändning av våra data- och BI-lösningar. Och som företag har vi fått synergieffekter eftersom vi har hittat balansen mellan centraliserad BI och hanterad SSBI.

### <a name="our-solution"></a>Vår lösning

**Starlight** är namnet på vår interna samlade analysplattform, som stöder ekonomi, försäljning, marknadsföring och teknik. Uppdraget är att leverera en robust, delad och skalbar dataplattform. Plattformen har skapats helt och hållet av ekonomiavdelningen och används i dag med de senaste Microsoft-produkterna.

**KPI Lake** är inte Azure Data Lake. I stället är det en Starlight-driven, tabellformad BI-semantikmodell som finns i Azure IaaS och används med Microsoft SQL Server Analysis Services. BI-semantikmodellen levererar data från ett hundratal interna källor och definierar många hierarkier och KPI:er. Uppdraget är att teamen inom ekonomi, marknadsföring och försäljning ska kunna utföra prestandarapportering och analyser. De får korrekta insikter i rätt tid med hjälp av enhetliga, BI-semantikmodeller från relevanta källor.

Den första distributionen var spännande eftersom den tabellformade BI-semantikmodellen resulterade i omedelbara och mätbara fördelar. Den första versionen centraliserade plattformarna C+E Finance och Marketing BI. Under de senaste sex åren har den utökats till att konsolidera fler lösningar för affärsinsikter. Den fortsätter att utvecklas och förser våra globala och kommersiella företag med granskningar, standardrapportering och SSBI. Införandet har femdubblats sedan lanseringen och överträffar våra inledande förväntningar.

Här är en sammanfattning av viktiga fördelar:

- Våra dotterbolag får styrkort och globala affärsgranskningar av ekonomi, marknadsföring, försäljningsrapporter och analyser.
- Självbetjäningsanalys stöds, vilket gör det möjligt för analytiker att upptäcka insikter som är dolda i data.
- Den hanterar rapporter och analyser av incitamentskompensation, marknadsförings- och driftanalys, prestandamått för försäljning, ledningsöversyn och den årliga planeringsprocessen.
- Den tillhandahåller automatiserad och dynamisk rapportering och analys från en _enskild källa till sanningen_.

**KPI Lake** är en fantastisk framgångsberättelse. Den presenteras ofta för våra kunder som ett exempel på hur man effektivt använder våra senaste tekniker. Föga förvånande blir många kunder mycket intresserade.

#### <a name="how-it-works"></a>Så här fungerar det

Starlight-plattformen hanterar dataflödet från förvärv, till bearbetning och sedan hela vägen till publiceringen:

1. Den robusta och smidiga dataintegreringen utförs regelbundet och konsoliderar data från drygt 100 olika obearbetade källor. Källdatasystemen är bl.a. relationsdatabaser, Azure Data Lake Storage och Azure Synapse-databaser. Ämnesområdena är ekonomi, marknadsföring, försäljning och teknik.
2. När datan har mellanlagrats, fördefinieras och formateras den med hjälp av huvuddata och affärslogik. Den läses sedan in i informationslagertabeller. Sedan uppdateras den tabellformade BI-semantikmodellen.
3. Analytiker i företaget använder Excel och Power BI till att leverera insikter och analyser från den tabellformade BI-semantikmodellen. Dessutom kan företagsägare få måttdefinitioner för sin egen verksamhet. Vid behov uppnås skalning med hjälp av Azure IaaS med belastningsutjämning.

## <a name="deliver-success"></a>Bli framgångsrik

Det är märkligt att alla vill ha en version av sanningen ... så länge det är deras. Men för vissa organisationer är det deras verklighet. De har flera versioner av sanningen eftersom enskilda personer har fullständig äganderätt till data och insikter. För dessa organisationer är den här ohanterade metoden förmodligen inte vägen mot företagets framgångar.

Vi tror att du behöver ett _Center för utmärkthet (COE)_ . Ett COE är ett centralt team som ansvarar för att bl.a. definiera företagets mått och definitioner. Det är också en affärsfunktion som organiserar personer, processer och teknikkomponenter i en omfattande uppsättning affärskompetenser och funktioner.

Vi ser många bevis för att ett omfattande och robust COE är avgörande för att få mervärden och maximera företagets framgångar. Det kan handla om ändringsinitiativ, standardprocesser, roller, riktlinjer, metodtips, support, utbildning och mycket mer.

Läs gärna artiklarna i denna COE-serie för mer information. Vi hjälper dig att se hur din organisation kan förändra sig för framgång.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Upprätta ett center för utmärkthet](center-of-excellence-establish.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

I [nästa artikel i serien](center-of-excellence-establish.md) visar vi hur ett COE hjälpte oss på Microsoft att skapa en standardiserad analys- och dataplattform som utvinner insikter från våra data.

### <a name="professional-services"></a>Professionella tjänster

Certifierade Power BI-partners finns där och kan hjälpa din organisation att starta ett COE. De kan erbjuda kostnadseffektiv utbildning eller en granskning av dina data. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).

Du kan också kontakta erfarna konsultpartners. De kan hjälpa dig att [bedöma](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [utvärdera](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) eller [implementera](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
