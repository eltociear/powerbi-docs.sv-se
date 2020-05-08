---
title: Optimeringsguide för Power BI
description: Optimeringsguide för Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d718c9c7f627d735c083a46c1483815e3744faca
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378879"
---
# <a name="optimization-guide-for-power-bi"></a>Optimeringsguide för Power BI

Den här artikeln innehåller riktlinjer som gör det möjligt för utvecklare och administratörer att skapa och underhålla optimerade Power BI-lösningar. Du kan optimera din lösning på olika arkitekturnivåer. Nivåerna inkluderar:

- Datakällorna
- Datamodellen
- Visualiseringar, inklusive instrumentpaneler, Power BI-rapporter och paginerade Power BI-rapporter
- Miljön, inklusive kapaciteter, datagatewayer och nätverket

## <a name="optimizing-the-data-model"></a>Optimera datamodellen

Datamodellen stöder hela visualiseringsupplevelsen. Datamodeller är antingen externt eller internt värdbaserade, och i Power BI kallas de för _datamängder_. Det är viktigt att du förstår dina alternativ och att du väljer rätt datamängdstyp för din lösning. De tre datamängdslägena är: Import, DirectQuery och Sammansatt. Mer information finns i [Datamängder i Power BI-tjänsten](../service-datasets-understand.md) och  [Datamängdslägen i Power BI-tjänsten](../service-dataset-modes-understand.md).

Mer specifik vägledning om datamängdslägen finns i:

- [Metoder för dataminskning för importmodellering](import-modeling-data-reduction.md)
- [Vägledning för DirectQuery-modeller i Power BI Desktop](directquery-model-guidance.md)
- [Vägledning för sammansatta modeller i Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Optimera visualiseringar

Power BI-visualiseringar kan vara instrumentpaneler, Power BI-rapporter eller paginerade Power BI-rapporter. Var och en har olika arkitekturer, och har därför sin egen vägledning. 

### <a name="dashboards"></a>Instrumentpaneler

Det är viktigt att du förstår att Power BI upprätthåller ett cacheminne för dina instrumentpaneler, med undantag för rapportpaneler i realtid och direktuppspelningspaneler. Mer information finns i [Datauppdatering i Power BI (paneluppdatering)](../refresh-data.md#tile-refresh). Om din datamängd framtvingar dynamisk [säkerhet på radnivå (RLS)](../service-admin-rls.md), så är det viktigt att du förstår prestandaimplikationerna eftersom panelerna cachelagras per användare.

När du fäster live-rapportpaneler på en instrumentpanel, så betjänas de inte från frågans cacheminne. De fungerar i stället som rapporter och gör frågor till backend-kärnor i farten.

Som namnet antyder får du bättre och mer konsekvent prestanda om du hämtar data från cachen än om du förlitar dig på datakällan. Ett sätt att dra nytta av den här funktionen är att låta instrumentpaneler vara första landningssidan för dina användare. Fäst visuella objekt som används och begärs ofta till instrumentpanelerna. På så sätt blir instrumentpanelerna en värdefull ”första försvarslinje” vilket ger kontinuerlig prestanda med mindre belastning på kapaciteten. Användare kan fortfarande klicka sig fram genom en rapport om de vill analysera informationen.

För DirectQuery och live-anslutningsdatamängder kan frågecachen uppdateras regelbundet genom att fråga datakällan. Detta sker, som standard, varje timma, men du kan konfigurera en annan frekvens i datamängdsinställningarna. Varje cacheuppdatering uppdaterar cachen genom att skicka frågor till den underliggande datakällan. Antalet frågor som genereras beror på hur många visuella objekt som har fästs på de instrumentpaneler som förlitar sig på datakällan. Observera att frågor genereras för varje säkerhetskontext om säkerhet på radnivå är aktiverad. Tänk t.ex. att det finns två olika roller som kategoriserar dina användare, och de har två olika datavyer. Under uppdateringen av frågecache genererar Power BI två uppsättningar med frågor.

### <a name="power-bi-reports"></a>Power BI-rapporter

Det finns flera rekommendationer när det gäller optimering av Power BI-rapportdesigner.

> [!NOTE]
> När rapporter baseras på en DirectQuery-datamängd, så finns det information om ytterligare rapportdesignsoptimering i [DirectQuery-modellvägledning i Power BI Desktop (optimera rapportdesigner)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Använd de mest restriktiva filtren

Ju mer data som ett visuellt objekt måste visa, desto längre tid kommer det att ta att läsa in det visuella objektet. Även om denna princip verkar uppenbar, är den lätt att glömma. Exempel: anta att du har en stor datauppsättning. Förutom denna datamängd, så skapar du en rapport med hjälp av en tabell. Slutanvändare använder utsnitt på sidan för att komma åt de rader som de vill – vanligtvis är de bara intresserade av några dussin rader.

Ett vanligt fel är att lämna standardvyn för tabellen ofiltrerad – dvs alla över 100M rader. Data för dessa rader läses in i minnet och dekomprimeras vid varje uppdatering. Den här bearbetningen skapar enorma krav på minnet. Lösning: minska det maximala antalet objekt som visas i tabellen genom att använda filtret ”Top N”. Du kan ange det maximala antalet objekt till ett högre antal än användarna behöver, till exempel 10 000. Upplevelsen ändras inte för slutanvändarna, men minnesanvändningen minskar markant. Och viktigast av allt är att prestanda förbättras.

Ett tillvägagångssätt liknande det ovanstående kan användas för alla visuella objekt i dina rapporter. Fråga dig själv, behövs alla data i den här visuella informationen? Finns det sätt att filtrera mängden data som visas i det visuella objektet med minimal påverkan på slutanvändarens upplevelse? Tänk på att i synnerhet tabeller kan vara väldigt kostsamma.

#### <a name="limit-visuals-on-report-pages"></a>Begränsa visuell information på rapportsidorna

Principen ovan gäller likvärdigt för all visuell information som läggs till på en rapportsida. Vi rekommenderar att du begränsar den visuella informationen på en rapportsida till endast det som är nödvändigt. [Detaljerade sidor](report-drillthrough.md) och [knappbeskrivningar för rapportsidor](report-page-tooltips.md) är bra sätt att ge mer information på utan att belasta rapporten med mer visuell information.

#### <a name="evaluate-custom-visual-performance"></a>Utvärdera anpassade visuella prestanda

Se till att placera varje anpassad visuell information inom dess tempo för att försäkra hög prestanda. Visuella Power BI-objekt som är dåligt optimerade kan påverka hela rapportens prestanda.

### <a name="power-bi-paginated-reports"></a>Sidnumrerade rapporter i Power BI

Du kan optimera sidnumrerade rapporter i Power BI genom att använda metodtips när det gäller rapportens datahämtning. Mer information finns i [Guide till datahämtning för sidnumrerade rapporter](report-paginated-data-retrieval.md).

Se dessutom till att din kapacitet har tillräckligt med allokerat minne för den [paginerade rapportens arbetsbelastning](../service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Optimera miljön

Du kan optimera Power BI-miljön genom att konfigurera kapacitetsinställningar, storleksanpassa datagatewayar och minska nätverkssvarstider.

### <a name="capacity-settings"></a>Kapacitetsinställningar

När du använder dedikerade kapaciteter – tillgängliga med Power BI Premium (P SKUs) eller Power BI Embedded (A SKUs, A4-A6) – så kan du hantera kapacitetsinställningarna. Mer information finns i [Hantera Premium-kapaciteter](../service-premium-capacity-manage.md). Mer information om hur du kan optimera din kapacitet finns i [Optimera Premium-kapaciteter](../service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Gateway-storleksändring

Det krävs en gateway när Power BI behöver få åtkomst till data som inte är direkt tillgängliga via Internet. Du kan installera den [lokala datagatewayen](../service-gateway-onprem.md) på en lokal server eller en VM-baserad infrastruktur som en tjänst (IaaS).

Mer information om gateway-arbetsbelastningar och storleksrekommendationer finns i [Storleksändring av lokal datagateway](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Svarstid för nätverk

Nätverksfördröjningen kan påverka rapportprestandan genom att öka den tid som krävs för begäranden att nå Power BI-tjänsten och för svar som ska levereras. En specifik region tilldelas klienter i Power BI.

> [!TIP]
> Om du vill ta reda på var din klientorganisation finns kan du läsa [Var finns min Power BI-klientorganisation?](../service-admin-where-is-my-tenant-located.md)

När användare från en klient ansluter till Power BI-tjänsten, dirigeras deras begäranden alltid till den här regionen. När begäranden når Power BI-tjänsten kan tjänsten sedan skicka ytterligare begäranden, till exempel till den underliggande datakällan eller en gateway, som också påverkas av nätverkssvarstiden.

Verktyg som [Azure-hastighetstest](https://azurespeedtest.azurewebsites.net/) ger en indikation om nätverksfördröjningen mellan klienten och Azure-regionen. Sträva generellt mot att hålla datakällor, gatewayer och Power BI-klustret så nära som möjligt för att minimera effekten av nätverksfördröjningen. Helst finns de i samma region. Om nätverksfördröjning är ett problem, så försök hitta gatewayer och datakällor som är närmare Power BI-klustret genom att placera dem på molnbaserade virtuella datorer.

## <a name="monitoring-performance"></a>Övervaka prestanda

Du kan identifiera flaskhalsar genom att övervaka prestanda. Fokusera på långsamma frågor eller visuella rapportobjekt i den fortsatta optimeringen. Övervakningen kan göras under designtid i Power BI Desktop, eller på produktionsarbetsbelastningar i Power BI Premium-kapaciteter. Mer information finns i [Övervaka rapportprestanda i Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Power BI-vägledning](index.yml)
- [Övervaka rapportprestanda](monitor-report-performance.md)
- Whitepaper: [Planera en företagsdistribution för Power BI](https://go.microsoft.com/fwlink/?linkid=2057861)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
