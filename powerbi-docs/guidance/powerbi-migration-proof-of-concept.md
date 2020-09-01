---
title: Utföra konceptbevis för att migrera till Power BI
description: Vägledning för att utföra ett konceptbevis vid migrering till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a7b7a848aafc3a581c1a19cf34366d61ba891f86
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803365"
---
# <a name="conductproofofconcepttomigratetopowerbi"></a>Utföra konceptbevis för att migrera till Power BI

I den här artikeln beskrivs **steg 3**, som handlar om att utföra ett koncepttest (POC) för att minimera risker och åtgärda dem så tidigt som möjligt vid migrering till Power BI.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Bild som visar stegen i en Power BI-migrering. Steg 3 framhävs för den här artikeln.":::

> [!NOTE]
> En fullständig förklaring av bilden ovan finns i [Översikt över Power BI-migrering](powerbi-migration-overview.md).

Fokus i steg 3 är att åtgärda och minimera risker så tidigt som möjligt. En teknisk POC är användbar för att validera antaganden. Det kan göras iterativt tillsammans med planering av lösningsdistribution (beskrivs i [steg 2](powerbi-migration-planning.md)).

Resultatet av det här steget är en Power BI-lösning som har ett smalt omfång, åtgärdar de första öppna frågorna och är redo för ytterligare arbete i [steg 4](powerbi-migration-create-validate-content.md) för att göra den produktionsklar.

> [!IMPORTANT]
> Vi avser inte att POC ska vara ett disponibelt arbete. I stället förväntar vi oss att det ska vara en tidig iteration av produktionsklara lösningar. I din organisation kan du referera till den här aktiviteten som en prototyp, pilot, modell, snabbstart eller MVP (minsta fungerande produkt). Att utföra en POC är inte alltid nödvändigt och det kan till och med ske informellt.

> [!TIP]
> De flesta ämnena som diskuteras i den här artikeln gäller även för ett Power BI-projekt med standardimplementering. I takt med att din organisation får mer erfarenhet av Power BI minskar behovet av att utföra POC. På grund av den snabba frisläppningstakten med Power BI och den kontinuerliga introduktionen av nya funktioner kan du dock regelbundet göra tekniska POC i inlärningssyfte.

## <a name="set-poc-goals-and-scope"></a>Ange mål för POC och omfång

Fokusera på följande mål när du utför en POC:

- Verifiera dina antaganden om hur en funktion fungerar.
- Lär dig mer om skillnader i hur Power BI fungerar jämfört med den äldre BI-plattformen.
- Verifiera inledande förståelse för vissa krav med ämnesexperter.
- Skapa en liten datauppsättning med verkliga data för att förstå och identifiera eventuella problem med datastrukturen, relationer, datatyper eller datavärden.
- Experimentera med, och validera, [DAX-syntaxuttryck](/dax/) som används av modellberäkningar.
- Testa datakällans anslutning med en gateway (om det är en gatewaykälla).
- Testa datauppdateringen med en gateway (om det är en gatewaykälla).
- Verifiera säkerhetskonfigurationer, inklusive säkerhet på radnivå om det är tillämpligt.
- Experimentera med layout och kosmetiska beslut.
- Kontrollera att alla funktioner i Power BI-tjänsten fungerar som förväntat.

POC-omfånget är beroende av vilka riskerna är eller vilka mål som måste verifieras med kollegor. För att minska komplexiteten bör du ha en POC som är så smal som möjligt i termer av omfång.

Oftast med en migrering är kraven välkända eftersom det finns en befintlig lösning att börja med. Beroende på omfattningen av förbättringarna eller befintliga Power BI-kunskaper skapar en POC dock fortfarande betydande värde. Dessutom kan snabba prototyper med konsumentfeedback vara lämpliga för att snabbt klargöra krav, särskilt om förbättringar görs.

> [!IMPORTANT]
> Även om en POC bara innehåller en delmängd av data eller bara innehåller begränsade visuella objekt är det ofta viktigt att göra den från början till slut. Det vill säga från utveckling i Power BI Desktop till distribution till en arbetsyta för utveckling i Power BI-tjänsten. Det är det enda sättet att fullständigt uppnå POC-målen. Det är särskilt sant när Power BI-tjänsten måste leverera kritiska funktioner som du inte har använt tidigare, t. ex. en DirectQuery-datauppsättning med enkel inloggning. Under POC kan du fokusera dina åtgärder på aspekter som du är osäker på eller behöver verifiera med andra.

## <a name="handle-differences-in-power-bi"></a>Hantera skillnader i Power BI

Power BI kan användas som ett _modellbaserat verktyg_ eller som ett _rapportbaserat verktyg_. En modellbaserad lösning innebär att utveckla en datamodell, medan en rapportbaserad lösning ansluter till en redan distribuerad datamodell.

På grund av den extrema flexibiliteten finns det några aspekter av Power BI som kan vara mycket annorlunda än den äldre BI-plattform som du migrerar från.

### <a name="consider-redesigning-the-data-architecture"></a>Överväg att utforma om dataarkitekturen

Om du migrerar från en äldre BI-plattform som har ett eget semantiskt lager är det troligt att skapandet av en Import-datauppsättning är ett lämpligt alternativ. Power BI fungerar bäst med ett [star-schema](star-schema.md)-tabelldesign. Om det äldre semantiska lagret inte är ett star-schema är det därför möjligt att viss omdesign kan krävas för att helt dra nytta av Power BI. Att definiera ett semantiskt lager som följer star-schemats designprinciper (inklusive relationer, vanliga åtgärder och egen organisationsterminologi) fungerar som en utmärkt startpunkt för självbetjäningsrapportens författare.

Om du migrerar från en äldre BI-plattform där rapporter refererar till relationsdatakällor med hjälp av SQL-frågor eller lagrade procedurer, och om du planerar att använda Power BI i [DirectQuery-läge](../connect-data/desktop-use-directquery.md), kan du nästan få en en-till-en-migrering av datamodellen.

> [!CAUTION]
> Om du ser att det skapas många Power BI Desktop-filer som består av en enda importerad tabell är det vanligtvis en indikator på att designen inte är optimal. Om du upptäcker den här situationen bör du undersöka om användningen av [delade datauppsättningar](../connect-data/service-datasets-across-workspaces.md) som skapats med ett [star-schema](star-schema.md)-design skulle få ett bättre resultat.

### <a name="decide-how-to-handle-dashboard-conversions"></a>Bestäm hur instrumentpanelskonverteringar ska hanteras

I BI-branschen är en instrumentpanel en samling visuella objekt som visar viktiga mått på en enda sida. Men i Power BI representerar en instrumentpanel en speciell visualiseringsfunktion som bara kan skapas i Power BI-tjänsten. När du migrerar en instrumentpanel från en äldre BI-plattform har du två alternativ:

1. Den äldre instrumentpanelen kan återskapas som en Power BI-_rapport_. De flesta rapporter skapas med Power BI Desktop. Sidnumrerade rapporter och Excel-rapporter är också alternativ.
2. Den äldre instrumentpanelen kan återskapas som en Power BI-_instrumentpanel_. [Instrumentpaneler](../fundamentals/service-basic-concepts.md#dashboards) är en visualiseringsfunktion som ingår i Power BI-tjänsten. Visuella instrumentpaneler skapas ofta genom att man fäster visuella objekt från en eller flera rapporter, vanliga frågor och svar eller Snabbinsikter.

> [!TIP]
> Eftersom instrumentpaneler är en Power BI-innehållstyp bör du avstå från att använda ordet _instrumentpanel_ i rapporten eller instrumentpanelens namn.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>Fokusera på helhetsbilden när du återskapar visuella objekt

Alla BI-verktyg har sina styrkor och fokusområden. Av den anledningen är den exakta rapporten som du är beroende av i en äldre BI-plattform kanske inte en nära motsvarighet i Power BI.

När du återskapar visuella rapportobjekt kan du fokusera mer på de stora företagsfrågorna som behandlas i rapporten. Det tar bort pressen på att replikera utformningen av varje visuellt objekt på exakt samma sätt. Även om innehållskonsumenter kan uppskatta konsekvens när de använder migrerade rapporter är det viktigt att inte fastna i tidskrävande diskussioner om små detaljer.

## <a name="next-steps"></a>Nästa steg

I [nästa artikel i den här serien om Power BI-migrering](powerbi-migration-create-validate-content.md) lär du dig mer om steg 4 som handlar om att skapa och validera innehåll när du migrerar till Power BI.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
