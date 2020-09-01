---
title: Samla in krav för att migrera till Power BI
description: Vägledning om att samla in och prioritera krav vid en migrering till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 29b821dc44f7eacb07f0df31100df2ff837c2189
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803390"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>Samla in krav för att migrera till Power BI

I den här artikeln beskrivs **steg 1**, som handlar om att samla in och prioritera kraven vid en migrering till Power BI.

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="Bild som visar stegen i en Power BI-migrering. Steg 1 framhävs för den här artikeln.":::

> [!NOTE]
> En fullständig förklaring av bilden ovan finns i [Översikt över Power BI-migrering](powerbi-migration-overview.md).

Tyngdpunkten för steg 1 ligger på att samla in information och planera för en enskild lösning som ska migreras till Power BI.

Resultatet från steg 1 innehåller detaljerade krav i prioritetsordning. Ytterligare aktiviteter i steg 2 och 3 måste slutföras för att helt kunna uppskatta nivån på ansträngningen.

> [!IMPORTANT]
> Steg 1–5 representerar aktiviteter för en specifik lösning. Det finns beslut och aktiviteter på organisations-/klientorganisationsnivå som påverkar processen på lösningsnivå. Några av de mer översiktliga planeringsaktiviteterna beskrivs i artikeln [Översikt över Power BI-migrering](powerbi-migration-overview.md). När det är lämpligt kan besluten skjutas upp till organisationsnivå besluten för effektivitet och konsekvens.

> [!TIP]
> De flesta ämnena som diskuteras i den här artikeln gäller även för ett Power BI-projekt med standardimplementering.

## <a name="compile-requirements"></a>Sammanställa krav

Inventeringen av befintliga BI-artefakter, som sammanställs i [stegen före migreringen](powerbi-migration-pre-migration-steps.md), blir indata för kraven för den nya lösningen som ska skapas i Power BI. Att samla in krav handlar om att förstå det aktuella läget, samt vilka punkter som användare skulle vilja ändra eller omstrukturera när rapporter återskapas i Power BI. Detaljerade krav är användbara för distributionsplanering för lösningen i [steg 2](powerbi-migration-planning.md), under skapandet av ett konceptbevis i [steg 3](powerbi-migration-proof-of-concept.md) och när du skapar den produktionsklara lösningen i [steg 4](powerbi-migration-create-validate-content.md).

### <a name="gather-report-requirements"></a>Samla in rapportkrav

Sammanställ grundlig och lättfattlig information om rapporter, till exempel:

- **Syfte, målgrupp och förväntad åtgärd:** Identifiera syftet och affärsprocessen för varje rapport, samt målgrupp, analytiskt arbetsflöde och förväntad åtgärd som ska vidtas av rapportkonsumenter.
- **Hur konsumenterna använder rapporten:** Det kan vara en bra idé att sätta sig ner med konsumenter av den befintliga rapporten och ta reda på exakt vad de gör med den. Du kanske får veta att vissa delar av rapporten kan strykas eller förbättras i den nya Power BI-versionen. Den här processen omfattar ytterligare tidsinvesteringar, men det är värdefullt för kritiska rapporter eller rapporter som används ofta.
- **Ägare och ämnesexpert:** Identifiera rapportägaren och eventuella ämnesexperter som är kopplade till rapporten eller datadomänen. De kan bli ägare till den nya Power BI-rapporten framöver. Ta med eventuella specifika krav för ändringshantering (som normalt skiljer sig mellan IT-hanterade och verksamhetshanterade lösningar) samt godkännanden och signeringar som krävs när ändringar görs i framtiden.
- **Metod för innehållsleverans:** Klargör rapportkonsumenternas förväntningar på innehållsleverans. Det kan vara på begäran, interaktiv körning, inbäddat i ett anpassat program eller enligt ett schema med hjälp av en e-postprenumeration. Det kan också finnas krav på att utlösa aviseringsmeddelanden.
- **Interaktivitetsbehov:** Ta reda på vilka interaktivitetskrav som är _nödvändiga_ och vilka som vore _trevliga_, till exempel filtrera eller öka detaljnivån.
- **Datakällor:** Se till att alla datakällor som krävs av rapporten identifieras och att behoven av datasvarstid (dataaktualitet) har förståtts. Identifiera krav på historiska data, trendande och ögonblicksbilder av data för varje rapport så att de kan samordnas med datakraven. Datakällans dokumentation kan också vara användbar senare när du utför datavalidering för en ny rapport med dess källdata.
- **Säkerhetskrav:** Klargör säkerhetskraven (till exempel tillåtna tittare, tillåtna redigerare och eventuella säkerhetsbehov på radnivå), inklusive eventuella undantag från normal organisationssäkerhet. Dokumentera eventuella behov av datakänslighetsnivåer, datasekretess eller regelefterlevnad.
- **Beräkningar, KPI:er och affärsregler:** Identifiera och dokumentera alla beräkningar, KPI:er och affärsregler som för närvarande är definierade i den befintliga rapporten så att de kan samordnas med datakraven.
- **Användbarhet, layout och kosmetiska krav:** Identifiera särskilda krav på användbarhet, layout och utseende som rör datavisualiseringar, gruppering och sorteringskrav och villkorlig synlighet. Ta med eventuella specifika överväganden som rör leverans till mobila enheter.
- **Utskrifts- och exportbehov:** Ta reda på om det finns några särskilda krav i fråga om utskrifter, exporter eller pixelperfekta layouter. De här behoven påverkar vilken typ av rapport som passar bäst (till exempel en Power BI- eller Excel-rapport eller en sidnumrerad rapport). Tänk på att rapportkonsumenter tenderar att lägga stor vikt vid hur de alltid har gjort, så dra dig inte för att utmana deras sätt att tänka. Kom ihåg att prata om _förbättringar_ i stället för _förändringar_.
- **Risker eller problem:** Ta reda på om det finns andra tekniska eller funktionella krav för rapporter, samt eventuella risker eller problem avseende den information som presenteras i dem.
- **Öppna ärenden och eftersläpning:** Identifiera eventuellt framtida underhåll, kända problem eller uppskjutna begäranden som ska sättas på väntelista för tillfället.

> [!TIP]
> Överväg att rangordna kraven genom att klassificera dem som _nödvändiga_ eller _trevliga_. Ofta ber konsumenter till en början om allt de någonsin kan tänkas behöva eftersom de tror att det är den enda chansen att komma med begäranden. När du tar upp prioriteringar i flera iterationer ska du också göra väntelistan tillgänglig för intressenter. Det bidrar till kommunikation, beslutsfattande och uppföljning av väntande åtaganden.

### <a name="gather-data-requirements"></a>Samla in datakrav

Sammanställ detaljerad information om data, till exempel:

- **Befintliga frågor:** Identifiera om det finns befintliga rapportfrågor eller lagrade procedurer som kan användas av en [DirectQuery-modell](../connect-data/desktop-use-directquery.md) eller en [sammansatt modell](../transform-model/desktop-composite-models.md) eller som kan konverteras till en importmodell.
- **Olika typer av datakällor:** Sammanställ vilka typer av datakällor som behövs, inklusive centraliserade datakällor (till exempel ett informationslager för företag) och datakällor som inte är standard (till exempel flata filer eller Excel-filer som utökar företagsdatakällor för rapporteringssyften). Det är också viktigt att ta reda på var datakällor finns för [datagateway](../connect-data/service-gateway-onprem.md)-anslutningar.
- **Datastruktur och rengöringsbehov:** Bestäm datastrukturen för varje nödvändig datakälla och i vilken utsträckning [datarengöring](../transform-model/desktop-query-overview.md) krävs.
- **Dataintegrering**: Utvärdera hur dataintegreringen ska hanteras när det finns flera datakällor och hur [relationer](../transform-model/desktop-create-and-manage-relationships.md) kan definieras mellan varje modelltabell. Identifiera de enskilda dataelement som behövs för att förenkla modellen och [minska storleken](import-modeling-data-reduction.md).
- **Godtagbar datasvarstid:** Fastställ behoven av datasvarstider för varje datakälla. Det påverkar beslut om vilket [datalagringsläge](../transform-model/desktop-storage-mode.md) som ska användas. Frekvensen för datauppdateringar för importmodellstabeller är viktig att känna till.
- **Datavolym och skalbarhet:** Utvärdera förväntningar på datavolymer, vilket kommer att påverka beslut om [stormodellsstöd](/admin/service-premium-large-models.md) och utformning av DirectQuery-modeller eller [sammansatta modeller](../transform-model/desktop-composite-models.md). Överväganden om behov av historiska data är också nödvändiga att känna till. För större datamängder är det också nödvändigt att fastställa reglerna för [stegvis uppdatering](../admin/service-premium-incremental-refresh.md).
- **Mått, KPI:er och affärsregler:** Utvärdera behovet av mått, KPI: er och affärsregler. De påverkar beslut om var logiken ska tillämpas: i datamängden eller i dataintegreringsprocessen.
- **Huvuddata och datakatalog:** Fundera över om det finns några problem med huvuddata som behöver åtgärdas. Kontrollera om integreringen med en företagsdatakatalog är lämplig för att förbättra identifieringsmöjligheterna, komma åt definitioner eller skapa konsekvent terminologi som godkänts av organisationen.
- **Säkerhet och datasekretess:** Ta reda på om det finns några särskilda överväganden angående säkerhet och datasekretess för datamängder, inklusive [krav på säkerhet på radnivå](../admin/service-admin-rls.md).
- **Öppna ärenden och eftersläpning:** Lägg till eventuella kända problem, kända defekter i datakvaliteten, framtida underhåll eller uppskjutna begäranden på väntelista för tillfället.

> [!IMPORTANT]
> Återanvändningsbara data kan uppnås med [delade datamängder](../connect-data/service-datasets-share.md), som om så önskas kan [certifieras](../connect-data/service-datasets-certify.md) för att påvisa trovärdighet och förbättra identifieringen. Återanvändningsbar dataförberedelse kan uppnås med [dataflöden](../transform-model/service-dataflows-overview.md) för att minska den repetitiva logiken i flera datamängder. Dataflöden kan också avsevärt minska belastningen på källsystemen eftersom data hämtas mindre ofta – flera datamängder kan sedan importera data från dataflödet.

## <a name="identify-improvement-opportunities"></a>Identifiera förbättringsmöjligheter

I de flesta situationer görs vissa ändringar och förbättringar. Det är ovanligt med en direkt ett-till-ett-migrering utan någon omstrukturering eller förbättring. Tre typer av förbättringar kan vara:

- **Konsolidering av rapporter:** Liknande rapporter kan konsolideras med hjälp av tekniker som filter, bokmärken eller anpassning. Att ha färre men mer flexibla rapporter kan avsevärt förbättra upplevelsen för rapportkonsumenter. Överväg att optimera datamängder för [Frågor och svar (frågor på naturligt språk)](../natural-language/q-and-a-best-practices.md) för att ge rapportkonsumenter ännu större flexibilitet, så att de kan skapa egna visualiseringar.
- **Effektivitetsförbättringar:** Under kravinsamlingen kan förbättringar ofta identifieras. När till exempel analytiker sammanställer siffror manuellt eller när ett arbetsflöde kan effektiviseras. [Power Query](../transform-model/desktop-query-overview.md) kan spela upp en viktig roll för att ersätta manuella aktiviteter som utförs för närvarande. Om affärsanalytikerna upptäcker att de regelbundet utför samma aktiviteter för att rensa och förbereda data, kan repeterbara dataförberedelsesteg i Power Query ge avsevärda tidsbesparingar och minska fel.
- **Centralisering av datamodell:** En auktoritativ och certifierad datamängd fungerar som ryggraden för hanterad självbetjänings-BI. I det här fallet hanteras data en gång, och analytikerna har sedan flexibiliteten att använda och utöka dessa data så att de uppfyller deras rapporterings- och analysbehov.

> [!NOTE]
> Om du vill ha mer information om centralisering av datamodeller kan du läsa om [central disciplin](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) och [gränsflexibilitet](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="prioritize-and-assess-complexity"></a>Prioritera och utvärdera komplexitet

I det här läget är den första inventeringen tillgänglig och kan innehålla specifika krav. När du prioriterar den första uppsättningen BI-artefakter som är klara för migrering bör rapporter och data betraktas som både kollektivt och oberoende av varandra.

Identifiera rapporter med hög prioritet, vilket kan omfatta rapporter som:

- har betydande värde för verksamheten.
- körs ofta.
- krävs av ledningen eller chefer.
- innebär en rimlig komplexitetsnivå (för att förbättra chanserna att lyckas under den första migreringen).

Identifiera data med hög prioritet, vilket kan omfatta data som:

- innehåller kritiska dataelement.
- är vanliga organisationsdata som används i många scenarier.
- kan användas för att skapa en delad datamängd för återanvändning av rapporter och flera olika rapportförfattare.
- innebär en rimlig komplexitetsnivå (för att förbättra chanserna att lyckas under den första migreringen).

## <a name="next-steps"></a>Nästa steg

I [nästa artikel i den här serien om Power BI-migrering](powerbi-migration-planning.md) lär du dig mer om steg 2 som handlar om att planera migreringen för en enskild Power BI-lösning.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
