---
title: Lär dig av kunders Power BI migreringar
description: Lär dig av kunder vid migrering till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a725d2763d7d044220785c2f9727ee30f14bfd5d
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803491"
---
# <a name="learn-from-customer-power-bi-migrations"></a>Lär dig av kunders Power BI migreringar

Den här artikeln, som avslutar serien om att migrera till Power BI, delar viktiga lektioner från två kunder som har uppgraderat till Power BI.

## <a name="international-consumer-goods-company"></a>Internationellt konsumentvarubolag

Ett internationellt konsumentvarubolag, som säljer hundratals produkter, fattar beslutet i 2017 att de ska uppnå en molnbaserad strategi. En av de viktigaste faktorerna för att välja Power BI som dess Business Intelligence-plattform (BI) är dess djupgående integrering med Azure och Microsoft 365.

### <a name="conduct-a-phased-migration"></a>Utföra en stegvis migrering

2017 började företaget använda Power BI. Det första organisatoriska målet var att introducera Power BI som ett extra BI-verktyg. Beslutet gav innehållsförfattare, konsumenter och IT tid att anpassa sig till nya sätt att leverera BI. Det har också gett dem möjlighet att utveckla expertis i Power BI.

Under den andra hälften av 2018 gjordes ett formellt tillkännagivande om att Power BI var det godkända BI-verktyget för organisationen. Och därför bör allt nytt BI-utvecklingsarbete äga rum i Power BI. Tillgängligheten för Power BI Premium var en viktig faktor för att fatta detta beslut. För närvarande rekommenderar organisationen inte användning av den tidigare BI-plattformen och planera för den påbörjade övergången.

Mot slutet av 2019 startade arbetet med att migrera befintligt innehåll från den äldre BI-plattformen till Power BI. Några tidiga efterföljare migrerade sitt innehåll snabbt. Det hjälpte till att bygga ännu fler moment med Power BI runt om i organisationen. Innehållsägare och författare uppmanades sedan att påbörja förberedelser för att fullständigt migrera till Power BI i slutet av 2020. Organisationen står fortfarande inför utmaningar som rör färdigheter, tid och finansiering – även om ingen av deras utmaningar är relaterade till själva teknikplattformen.

> [!IMPORTANT]
> Power BI hade redan lyckats och rotat sig inom organisationen innan affärsenheterna uppmanades att genomgå en formell migrering från den tidigare BI-plattformen.

### <a name="prepare-to-handle-varying-responses"></a>Förbered för att hantera varierande svar

I den här stora decentraliserade organisationen fanns det varierande nivåer av mottaglighet och vilja att flytta till Power BI. Förutom bekymmer kring tid och budget har det funnits personal som hade gjort betydande investeringar i att skapa sig kunskaper i den tidigare BI-plattformen. Det innebar att meddelandet om standardiserad Power BI inte välkomnades av alla. Eftersom varje affärsenhet har sin egen budget kan enskilda affärsenheter utmana beslut som detta. När beslut fattades på central nivå ledde det till några utmaningar att hantera för den ansvariga sponsorn och BI-ledarna.

> [!IMPORTANT]
> Kommunikationen med ledarskapsteam i affärsenheterna var avgörande för att se till att alla förstod organisationsförmånerna med att standardisera Power BI. Effektiv kommunikation blev ännu mer viktig när migreringen fortskred och inaktiveringsdatumet för den äldre BI-plattformen närmade sig.

### <a name="focus-on-the-bigger-picture"></a>Fokusera på helheten

Företaget upptäckte att även om vissa migrerade rapporter skulle kunna replikera den ursprungliga designen kunde inte alla enskilda rapporter replikeras fullständigt i Power BI. Även om det var förväntat, eftersom alla BI-plattformar skiljer sig åt. Det gjorde att ett annan tänkesätt kring design krävdes.

Vägledning tillhandahölls för innehållsförfattare: fokus på att skapa anpassningsrapporter i Power BI, i stället för att försöka skapa en exakt replik av den äldre rapporten. Därför måste ämnesexperterna vara aktivt tillgängliga under migreringsprocessen för samråd och verifiering. Vi har vidtagit åtgärder för att beakta rapportdesignsyftet och förbättra det när det är lämpligt.

> [!IMPORTANT]
> Ibland är det bättre att genomföra förbättringar under migreringen. Vid andra tillfällen är det bättre att leverera exakt samma värde som tidigare, utan avsevärda förbättringar, så att du man inte äventyrar migreringens tidslinje.

### <a name="cautiously-assess-priorities"></a>Utvärdera prioriteringar försiktigt

En analys av den tidigare BI-plattformen genomfördes för att fullständigt förstå användningen. Den tidigare BI-plattformen hade tusentals publicerade rapporter, varav cirka hälften hade varit tillgängliga under föregående år. Antalet kunde minska med hälften igen vid bedömningen av vilka rapporter som ansågs leverera ett betydande värde till organisationen. Dessa rapporter prioriterades först för migreringen.

> [!IMPORTANT]
> Det är mycket enkelt att överskatta hur viktig en rapport faktiskt är. För rapporter som inte används ofta kan du utvärdera om de kan tas ur bruk helt och hållet. Ibland är billigast och enklast att inte göra något.

### <a name="cautiously-assess-complexity"></a>Utvärdera komplexitet försiktigt

I de första prioriterade rapporterna kompilerades tidsuppskattningarna baserat på uppskattade nivåer av arbete: enkel, medel eller komplex. Även om det låter som en relativt enkel process ska du inte förvänta dig att tidsuppskattningarna är korrekta i en enskild rapport. Du kan få en uppskattning som är felaktig. Företaget hade till exempel en rapport som bedömdes vara mycket komplex. Den fick en konverteringsuppskattning på 50 dagar av konsulterna. Den omdesignade rapporten i Power BI slutfördes dock inom cirka 50 timmar.

> [!IMPORTANT]
> Även om tidsuppskattningar ofta är nödvändiga för att få finansiering och personaltilldelningar är de förmodligen mest värdefulla i mängd.

### <a name="decide-how-change-management-is-handled"></a>Bestäm hur ändringshantering ska utföras

Med en sådan stor mängd BI-tillgångar har ändringshantering för de affärsägda rapporterna utgjort en utmaning. IT-hanterade rapporter hanterades enligt standardmetoder för ändringshantering. Men på grund av den stora volymen var det inte möjligt att köra ändringar centralt för företagsägt innehåll.

> [!IMPORTANT]
> Ytterligare ansvarsområden läggs på affärsenheterna när det är opraktiskt att hantera förändringar från ett centralt team.

### <a name="create-an-internal-community"></a>Skapa en intern community

Företaget upprättade ett Center för utmärkthet (COE) för att tillhandahålla interna utbildningsklasser och resurser. COE fungerar också som en intern konsultgrupp som är redo att hjälpa innehållsförfattare med tekniska problem, lösning av hinder och riktlinjer för bästa praxis.

Det finns också en intern Power BI-community, som har varit en enorm framgång med över 1 600 medlemmar. Communityn hanteras i Yammer. Medlemmar kan ställa interna relevanta frågor och få svar som följer bästa praxis och inramas i organisatoriska begränsningar. Den här typen av interaktion mellan användare minskar mycket av supportbördan från COE. COE övervakar dock frågorna och svaren och deltar i konversationer när det är lämpligt.

En förlängning av den interna communityn är det nyare Power BI-expertnätverket. Det innehåller ett litet antal förvalda Power BI-experter inifrån organisationen. De är kunniga Power BI-användare från affärsenheterna, som är entusiastiska experter och som aktivt vill lösa utmaningar inom verksamheten. Medlemmar i Power BI-expertnätverket förväntas följa bästa praxis och riktlinjer som upprättats av COE, och hjälpa till att få den bredare interna Power BI-communityn att förstå och implementera dem. Även om Power BI-expertnätverket samarbetar med COE och kan få särskild utbildning kan Power BI-experter arbeta oberoende av COE. Varje Power BI-expert kan definiera parametrar för hur de fungerar, med hänsyn till att de har andra ansvarsområden och prioriteringar i sin officiella roll.

> [!IMPORTANT]
> Ha en mycket väldefinierad omfattning för vad COE gör, till exempel: implementering, styrning, vägledning, metodtips, utbildning, support och kanske även praktisk utveckling. Även om en COE är otroligt värdefull kan det vara svårt att mäta avkastningen på investeringar.

### <a name="monitor-migration-progress-and-success"></a>Övervaka förloppet för migrering och framgång

KPI:er (Key Performance Indicators) övervakas kontinuerligt under migreringen till Power BI. De hjälper företaget att förstå trender för mått, till exempel antal rapportbesök, antal aktiva rapporter och distinkta användare per månad. Ökad användning av Power BI mäts tillsammans med minskad användning av den tidigare BI-plattformen, med målet att uppnå en inverterad relation. Målen uppdateras varje månad för att anpassas till ändringar. Om användningen inte sker i önskad takt identifieras flaskhalsar så att lämpliga åtgärder kan vidtas.

> [!IMPORTANT]
> Skapa ett styrkort med åtgärdsbar Business Intelligence för att övervaka att migreringen lyckades.

## <a name="large-transportation-and-logistics-company"></a>Stort transport- och logistikföretag

Ett stort nordamerikanskt transport- och logistikföretag investerar aktivt i modernisering av datainfrastrukturen och analyssystemen.

### <a name="allow-a-period-of-gradual-growth"></a>Tillåt en gradvis tillväxtperiod

Företaget kom igång med att använda Power BI 2018. Efter mitten av 2019 blev Power BI den föredragna plattformen för alla nya BI-användningsfall. Sedan, 2020, fokuserade företaget på att fasa ut sin befintliga BI-plattform, förutom en mängd olika anpassade ASP.NET BI-lösningar.

> [!IMPORTANT]
> Power BI hade många aktiva användare i organisationen innan de började fasa ut den äldre BI-plattformen och -lösningarna.

### <a name="balance-centralized-and-distributed-groups"></a>Balansera centraliserade och distribuerade grupper

I företaget finns det två typer av BI-team: ett centralt BI-team och analysgrupper som distribueras i hela organisationen. Det centrala BI-teamet har ansvaret för Power BI som en plattform, men det äger inte något av innehållet. På så sätt är det centrala BI-teamet ett nav för teknisk aktivering som stöder de distribuerade analysgrupperna.

Var och en av analysgrupperna är dedikerad till en särskild affärsenhet eller en delad tjänstfunktion. En liten grupp kan innehålla en enda analytiker, medan en större grupp kan ha 10–15 analytiker.

> [!IMPORTANT]
> De distribuerade analysgrupperna utgörs av ämnesexperter som känner till de dagliga affärsbehoven. Den här separationen gör det möjligt för det centrala BI-teamet att fokusera primärt på teknisk aktivering och stöd för BI-tjänster och -verktyg.

### <a name="focus-on-dataset-reusability"></a>Fokus på återanvändningsbarhet av datauppsättningar

Att förlita sig på anpassade ASP.NET BI-lösningar var ett hinder för att utveckla nya BI-lösningar. De nödvändiga kunskaperna innebar att antalet självbetjäningsinnehållsförfattare var litet. Eftersom Power BI är ett mycket mer användarvänligt verktyg, som är särskilt utformat för självbetjänings-BI, så spreds det snabbt i hela organisationen när det släpptes.

Upprättandet av dataanalytiker i företaget ledde till omedelbara positiva resultat. Det inledande fokuset med Power BI-utveckling var emellertid på visualisering. Även om det resulterade i värdefulla BI-lösningar så ledde det till ett stort antal Power BI Desktop-filer, var och en med en en-till-en-relation mellan rapporten och dess datauppsättning. Det resulterade i flera datauppsättningar och dubbletter av data och affärslogik. För att minska dubbleringen av data, logik och arbete, har företaget erbjudit utbildning och gett support till innehållsförfattare.

> [!IMPORTANT]
> Ta med information om vikten av data återanvändning i dina interna utbildningsinsatser. Åtgärda viktiga begrepp så tidigt som möjligt.

### <a name="test-data-access-multiple-ways"></a>Testa dataåtkomst på flera sätt

Företagets informationslagerplattform är DB2. Baserat på den aktuella designen av datalager upptäckte företaget att DirectQuery-modeller fungerade bäst för deras krav – i stället för Import-modeller.

> [!IMPORTANT]
> Genomför ett tekniskt konceptbevis för att utvärdera det modelllagringsläge som fungerar bäst. Du kan också lära datamodellerare om modelllagringslägen och hur de kan välja ett lämpligt läge för projektet.

### <a name="educate-authors-about-premium-licensing"></a>Utbilda författare om Premium-licensiering

Eftersom det var enklare att komma igång med Power BI (jämfört med deras äldre BI-plattform) var många av de tidiga anhängarna personer som inte hade någon licens till det tidigare BI-verktyget. Som förväntat ökade antalet innehållsförfattare mycket kraftigt. Dessa innehållsförfattare ville kunna dela sitt innehåll med andra, vilket resulterade i ett ständigt behov av ytterligare Power BI Pro-licenser.

Företaget gjorde en stor investering i Premium-arbetsytor, främst för att distribuera Power BI-innehåll till många användare med kostnadsfria Power BI-licenser. Supportteamet arbetar med innehållsförfattare för att se till att de använder Premium-arbetsytor vid behov. Det undviker att allokera Power BI Pro-licenser i onödan när en användare bara behöver använda innehåll.

> [!IMPORTANT]
> Licensieringsfrågor uppstår ofta. Var beredd på att utbilda och hjälpa innehållsförfattare att lösa licensieringsfrågor. Verifiera att användarbegäranden av Power BI Pro-licenser är berättigade.

### <a name="understand-the-data-gateways"></a>Förstå datagatewayer

Företaget hade tidigt många personliga gatewayer. Genom att använda ett lokalt datagatewaykluster flyttas arbetet med hantering till det centrala BI-teamet, vilket gör att innehållsförfattaren kan fokusera på att skapa innehåll. Det centrala BI-teamet arbetade med den interna Power BI-användarcommunityn för att minska antalet personliga gatewayer.

> [!IMPORTANT]
> Ha en plan för att skapa och hantera lokala datagatewayer. Bestäm vem som tillåts att installera och använda en personlig gateway och tillämpa med gatewayprinciper.

### <a name="formalize-your-support-plan"></a>Formalisera din supportplan

I takt med att Power BI växte inom organisationen påträffade företaget att en supportmetod för flera nivåer fungerade bra:

- **Skikt 1: Intra-team:** Folk lär sig av, och lär ut till varandra på daglig basis.
- **Skikt 2: Power BI Community:** Användare ställer frågor till interna teamcommunityn för att lära sig om varandra och förmedla viktig information.
- **Skikt 3: Centralt BI-team och COE:** Personer skickar e-postbegäran om hjälp. _Kontorssessioner_ hålls två gånger per vecka för att diskutera problem och dela idéer.

> [!IMPORTANT]
> Även om de två första skikten är mindre formella är de lika viktiga som det tredje skiktet med support. Erfarna användare brukar förlita sig på personer de känner, medan nyare användare (eller personer som är den enda dataanalytikern på en affärsenhet eller delad tjänst) ofta förlitar sig på formell support.

### <a name="invest-in-training-and-governance"></a>Investera i utbildning och styrning

Under det senaste året förbättrade företaget sina interna utbildningserbjudanden och förbättrade sitt datastyrningsprogram. Styrningskommittén har viktiga medlemmar från var och en av de distribuerade analysgrupperna, plus COE.

Det finns nu sex interna Power BI-kurser i den interna katalogen. Kursen [En instrumentpanel på en dag](https://powerbi.microsoft.com/diad/) är fortfarande en populär kurs för nybörjare. För att hjälpa användarna att fördjupa sina kunskaper levererar de en serie med tre Power BI-kurser och två DAX-kurser.

Ett av de viktigaste datastyrningsbeslutet rör hantering av Premium-kapaciteter. Företaget har valt att justera sin dedikerade kapacitet med nyckelanalysområden i affärsenheter och delade tjänster. Om det finns ineffektivitet påverkas bara detta enda område, och de decentraliserade kapacitetsadministratörerna kan hantera kapaciteten som de anser är bäst.

> [!IMPORTANT]
> Var uppmärksam på hur Premium-kapacitet används och hur arbetsytorna tilldelas till dem.

## <a name="next-steps"></a>Nästa steg

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- [En instrumentpanel på en dag](https://powerbi.microsoft.com/diad/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
