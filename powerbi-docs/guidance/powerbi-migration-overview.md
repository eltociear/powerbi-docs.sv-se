---
title: Översikt över Power BI-migrering
description: Lär dig hur du planerar och utför en migrering från ett annat BI-verktyg från tredje part till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: aa17e6293a4bd946b1d6b7acad45623fa2393c57
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803514"
---
# <a name="power-bi-migration-overview"></a>Översikt över Power BI-migrering

Kunder standardiserar Power BI i allt högre utsträckning för att driva en datakultur. Det inbegriper möjliggörande av hanterad BI med självbetjäning, rationalisering av tillhandahållandet av Enterprise BI och åtgärder för ekonomiska belastningar. Syftet med den här serien med artiklar om Power BI-migrering är att ge vägledning om hur du planerar och utför en migrering från ett BI-verktyg från tredje part till Power BI.

Artiklarna i Power BI-migrationsserien är:

1. Översikt över Power BI-migrering (den här artikeln)
1. [Förbered för att migrera till Power BI](powerbi-migration-pre-migration-steps.md)
1. [Samla in krav för att migrera till Power BI (steg 1)](powerbi-migration-requirements.md)
1. [Planera distribution för att migrera till Power BI (steg 2)](powerbi-migration-planning.md)
1. [Utföra konceptbevis för att migrera till Power BI (steg 3)](powerbi-migration-proof-of-concept.md)
1. [Skapa innehåll för att migrera till Power BI (steg 4)](powerbi-migration-create-validate-content.md)
1. [Distribuera till Power BI (steg 5)](powerbi-migration-deploy-support-monitor.md)
1. [Lär dig av kunders Power BI-migreringar](powerbi-migration-learn-from-customers.md)

Det finns två antaganden: Din organisation har en äldre BI-plattform som för närvarande är på plats och beslutet har fattats om att migrera innehåll och användare till Power BI. Att migrera till Power BI-tjänsten är seriens primära fokus. Ytterligare överväganden kan tillkomma för nationella molnkunder utöver vad som diskuteras i den här artikelserien.

I följande diagram visas fyra viktiga faser för att distribuera Power BI i din organisation.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="Bild som visar de fyra faserna på hög nivå, som beskrivs i följande tabell.":::

|Fas|Beskrivning|
|--------|-----------|
|![Fas 1.](media/common/icon-01-red-30x30.png)|**Konfigurera och utvärdera Power BI.** I den första fasen måste du etablera den inledande Power BI-arkitekturen. Preliminär planering för distribution och styrning hanteras i detta läge, samt Power BI-utvärderingar, däribland avkastning på investeringar och/eller kostnads-nyttoanalys.|
|![Fas 2.](media/common/icon-02-red-30x30.png)|**Skapa nya lösningar snabbt i Power BI.** I den andra fasen kan självbetjänings-BI-författare börja använda och utvärdera Power BI efter sina behov, och värdet kan hämtas från Power BI snabbt. Aktiviteter i fas 2 är avgörande för flexibilitet och snabbt affärsvärde, vilket är viktigt för att få godkännande för valet av ett nytt BI-verktyg, till exempel Power BI. Av den anledningen illustrerar diagrammet aktiviteter i fas 2 sida vid sida med migreringen i fas 3.|
|![Fas 3.](media/common/icon-03-red-30x30.png)|**Migrera BI-tillgångar från en äldre plattform till Power BI.** Den tredje fasen hanterar migreringen till Power BI. Det är fokus för den här serien med Power BI-migreringsartiklar. Fem olika migreringssteg beskrivs i nästa avsnitt.|
|![Fas 4.](media/common/icon-04-red-30x30.png)|**Införa, styra och övervaka Power BI.** Den sista fasen omfattar pågående aktiviteter, till exempel vård av datakultur, kommunikation och utbildning. Dessa aktiviteter påverkar kraftigt en effektiv Power BI-implementering. Det är viktigt att ha styrnings- och säkerhetsprinciper och processer som är lämpliga för din organisation, samt granskning och övervakning som gör det möjligt att skala, växa och ständigt förbättra.|

> [!IMPORTANT]
> En formell migrering till Power BI sker nästan alltid parallellt med utvecklingen av en ny Power BI-lösning. _Power BI-lösning_ är en allmän term som omfattar användningen av både data och rapporter. En enda Power BI Desktop-fil (pbix) kan innehålla en datamodell eller rapport, eller båda. [Att separera datamodellen från rapporter](../guidance/report-separate-from-model.md) uppmuntras för dataanvändning, men är inte obligatoriskt.
>
> Använd Power BI för att skapa nya krav, medan du planerar och genomför den formella migreringen för att få hjälp med att satsa. Samtidiga faser ger innehållsskapare en praktisk och verklig upplevelse med Power BI.

## <a name="five-stages-of-a-power-bi-migration"></a>Fem steg i en Power BI-migrering

Fas 3 i diagrammet ägnar sig åt migrering till Power BI. Under den här fasen finns det fem vanliga steg.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="Bild som visar stegen i en Power BI-migrering, som beskrivs nedan.":::

Följande steg som visas i föregående diagram är:

- [Steg före migrering](#pre-migration-steps)
- [Steg 1: Samla in krav och prioritera](#stage-1-gather-requirements-and-prioritize)
- [Steg 2: Planera för distribution](#stage-2-plan-for-deployment)
- [Steg 3: Utföra konceptbevis](#stage-3-conduct-proof-of-concept)
- [Steg 4: Skapa och verifiera innehåll](#stage-4-create-and-validate-content)
- [Steg 5: Distribuera, stödja och övervaka](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>Steg före migrering

I stegen före migreringen ingår åtgärder som du kan tänka på innan du påbörjar ett projekt för att migrera innehåll från en äldre BI-plattform till Power BI. Den innehåller vanligtvis den ursprungliga distributionsplaneringen på klientnivå. Mer information om dessa aktiviteter finns i [Förbered för att migrera till Power BI](powerbi-migration-pre-migration-steps.md).

### <a name="stage-1-gather-requirements-and-prioritize"></a>Steg 1: Samla in krav och prioritera

Fokus i steg 1 är att samla in information och planera för migreringen av en enskild lösning. Den här processen bör vara iterativ och begränsad till en rimlig storlek. Resultatet från steg 1 innehåller en prioriterad inventering av rapporter och data som ska migreras. Ytterligare aktiviteter i steg 2 och 3 är nödvändiga för att helt kunna uppskatta nivån på ansträngningen. Mer information om aktiviteter i steg 1 finns [Samla in krav för att migrera till Power BI](powerbi-migration-requirements.md).

### <a name="stage-2-plan-for-deployment"></a>Steg 2: Planera för distribution

I steg 2 ligger fokus på hur de krav som definieras i steg 1 kan uppfyllas för varje enskild lösning. Resultatet från steg 2 innehåller så mycket information som möjligt för att vägleda processen, även om det är en iterativ, icke-linjär process. Att skapa ett konceptbevis (i steg 3) kan göras parallellt med det här steget. Även när du skapar lösningen (i steg 4) kan ytterligare information komma fram som påverkar beslut kring distributionsplanering. Den här typen av distributionsplanering i steg 2 fokuserar på lösningsnivån, samtidigt som de beslut som redan har fattats på organisationsnivå respekteras. Mer information om aktiviteter i steg 2 finns [Planera distribution för att migrera till Power BI](powerbi-migration-planning.md).

### <a name="stage-3-conduct-proof-of-concept"></a>Steg 3: Utföra konceptbevis

Fokus i steg 3 är att åtgärda och minimera risker så tidigt som möjligt. Ett tekniskt konceptbevis (POC) är användbart för att validera antaganden och kan utföras iterativt tillsammans med distributionsplaneringen (steg 2). Resultatet från det här steget är en Power BI-lösning som är smal i omfånget. Observera att vi inte avser att POC ska vara ett disponibelt arbete. Det kräver dock troligen ytterligare arbete i steg 4 för att det ska bli produktionsklart. I det här avseendet kan du i din organisation referera till den här aktiviteten som en prototyp, pilot, modell, snabbstart eller MVP (minsta fungerande produkt). Att utföra en POC är inte alltid nödvändigt och det kan göras informellt. Mer information om aktiviteter i steg 3 finns [Utföra konceptbevis för att migrera till Power BI](powerbi-migration-proof-of-concept.md).

### <a name="stage-4-create-and-validate-content"></a>Steg 4: Skapa och verifiera innehåll

Steg 4 sker när det faktiska arbetet med att omvandla POC till en produktionsklar lösning är färdigt. Resultatet från det här steget är en slutförd Power BI-lösning som har verifierats i en utvecklingsmiljö. Det bör vara klart för distribution i steg 5. Mer information om aktiviteter i steg 4 finns [Skapa innehåll för att migrera till Power BI](powerbi-migration-create-validate-content.md).

### <a name="stage-5-deploy-support-and-monitor"></a>Steg 5: Distribuera, stödja och övervaka

Det primära fokuset i steg 5 är att distribuera den nya Power BI-lösningen till produktion. Resultatet från det här steget är en produktionslösning som används aktivt av företagsanvändare. När du använder en flexibel metod kan det vara bra att ha vissa planerade förbättringar som ska levereras i en framtida iteration. Beroende på din bekvämlighetsnivå med Power BI, till exempel minimera risk- och användaravbrott, kan du välja att utföra en mellanlagrad distribution. Eller så kan du börja med att distribuera till en mindre grupp pilotanvändare. Support och övervakning är också viktigt i det här skedet, och det bör ske regelbundet. Mer information om aktiviteter i steg 5 finns i [Migrera till Power BI](powerbi-migration-deploy-support-monitor.md).

> [!TIP]
> De flesta av de begrepp som diskuteras i den här serien med Power BI-migreringsartiklar gäller även för ett standardprojekt för Power BI-implementering.

## <a name="consider-migration-reasons"></a>Ta hänsyn till migrationsorsaker

Att möjliggöra en produktiv och frisk datakultur är ett huvudmål för många organisationer. Power BI är ett utmärkt verktyg för att underlätta detta mål. Tre vanliga anledningar till att du kan överväga att migrera till Power BI kan brytas ned till:

- **Möjliggöra hanterad självservice-BI** genom att introducera nya funktioner som hjälper användargruppen för självbetjäning i BI. Power BI ger tillgång till information och beslutsfattande som är allmänt tillgänglig, samtidigt som du förlitar dig mindre på specialistkunskaper som kan vara svåra att hitta.
- **Rationalisera tillhandahållandet av Enterprise BI** för att uppfylla kraven som inte åtgärdas av befintliga BI-verktyg, samtidigt som du minskar komplexitetsnivån, minskar ägandekostnaden och/eller standardiserar från flera BI-verktyg som används för närvarande.
- **Åtgärda ekonomiska belastningar** för ökad produktivitet med färre resurser, tid och personal.

## <a name="achieve-power-bi-migration-success"></a>Få en lyckad Power BI-migrering

Varje migrering skiljer sig något åt. Det kan bero på organisationens struktur, datastrategier, datahanteringsmognad och organisatoriska mål. Det finns dock vissa metoder som vi ser konsekvent med våra kunder som uppnår en framgångsrik Power BI-migrering.

- **Sponsring från ansvarig:** Identifiera en ansvarig sponsor tidigt i processen. Den här personen bör vara någon som aktivt stöder BI i organisationen och personligen har investerat i att uppnå ett positivt resultat för migreringen. Vi rekommenderar att sponsorn har den slutliga befogenheten och ansvarar för resultaten från Power BI.
- **Utbildning, support och kommunikation:** Inse att det är mer än bara ett teknikinitiativ. Alla BI- eller analysprojekt är också ett initiativ som rör personer, så överväg att investera tidigt i användarutbildning och support. Skapa också en kommunikationsplan som transparent förklarar för alla intressenter vad som inträffar, varför och ställer realistiska förväntningar. Se till att ta med en feedbackloop i kommunikationsplanen för att samla in input från intressenter.
- **Snabba vinster:** Prioritera inledningsvis objekt med högt värde som har ett stort affärsvärde och trycker på. I stället för att enbart försöka att alltid migrera rapporter exakt som de visas på den äldre BI-plattformen fokuserar du på den affärsfråga som rapporten försöker svara på, inklusive åtgärder som ska vidtas – när du ska hantera den omdesignade rapporten.
- **Modernisering och förbättringar:** Var beredd på att tänka på hur saker alltid har gjorts. En migrering kan ge en möjlighet att leverera förbättringar. Det kan till exempel eliminera manuell förberedelse av data eller flytta affärsregler som är begränsade till en enda rapport. Överväg att omstrukturera, modernisera och konsolidera befintliga lösningar när ansträngningen kan motiveras. Den kan omfatta att konsolidera flera rapporter till en eller eliminera äldre artefakter som inte har använts under en viss tid.
- **Kontinuerlig inlärning:** Var beredd på att använda en stegvis metod och få en löpande inlärning och anpassning. Arbeta med korta, iterativa cykler för att snabbt få fram ett värde. Gör en regelbunden övning för att slutföra små POC för att minimera risker, validera antaganden och lära dig mer om nya funktioner. Eftersom Power BI är en molntjänst som uppdateras varje månad är det viktigt att hålla jämna steg med utvecklingen och justera kursen när det är lämpligt.
- **Motstånd mot förändring:** Det kan finnas varierande motstånd att ändra. Vissa användare kommer att kämpa mot att lära sig ett nytt verktyg. Dessutom kan en del av personalen som har lagt n ed mycket tid och ansträngning för att få expertkunskaper med ett annat BI-verktyg känna sig hotade av att de tas ur drift. Var beredd, för det kan leda till interna politiska problem, särskilt i mycket decentraliserade organisationer.
- **Villkor:** Var realistisk med migreringsplaner, inklusive finansiering, tidsuppskattningar samt roller och ansvarsområden för alla som är inblandade.

## <a name="acknowledgments"></a>Tack till

Den här serien med artiklar har skrivits av Melissa Coates, Data Platform MVP och ägare till [Coates Data Strategies](https://www.coatesdatastrategies.com/). Deltagare och granskare innefattar Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger och Peter Myers.

## <a name="next-steps"></a>Nästa steg

I [nästa artikel i den här Power BI-migreringsserien](powerbi-migration-pre-migration-steps.md) kan du läsa om stegen före migreringen när du ska migrera till Power BI.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Migrera SSRS-rapporter till Power BI](migrate-ssrs-reports-to-power-bi.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
