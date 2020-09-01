---
title: Planera distribution för att migrera till Power BI
description: Vägledning om hur du planerar distribution när du migrerar till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 590e28c727cab88b008d7a05e7df22244e8dabf0
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803368"
---
# <a name="plandeploymenttomigratetopowerbi"></a>Planera distribution för att migrera till Power BI

I den här artikeln beskrivs **steg 2**, som handlar om att planera migreringen för en enskild Power BI-lösning.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Bild som visar stegen i en Power BI-migrering. Steg 2 framhävs för den här artikeln.":::

> [!NOTE]
> En fullständig förklaring av bilden ovan finns i [Översikt över Power BI-migrering](powerbi-migration-overview.md).

Fokus för steg 2 är att definiera hur de krav som definierades i steg 1 används för att migrera en lösning till Power BI.

Resultatet från steg 2 innehåller så många specifika beslut som möjligt för att vägleda distributions processen.

Beslutsfattande av den här typen är en iterativ och icke-linjär process. En del planering har redan gjorts i [stegen före migreringen](powerbi-migration-pre-migration-steps.md). Insikter från ett konceptbevis (Proof of Concept, POC) (beskrivs i [steg 3](powerbi-migration-proof-of-concept.md)) kan komma parallellt med distributionsplaneringen. Även när du skapar lösningen (beskrivs i [steg 4](powerbi-migration-create-validate-content.md)) kan ytterligare information komma fram som påverkar beslut kring distributionen.

> [!IMPORTANT]
> Steg 1–5 representerar aktiviteter för en specifik lösning. Det finns beslut och aktiviteter på organisations-/klientorganisationsnivå som påverkar processen på lösningsnivå. Några av de mer översiktliga planeringsaktiviteterna beskrivs i artikeln [Översikt över Power BI-migrering](powerbi-migration-overview.md). När det är lämpligt kan besluten skjutas upp till organisationsnivå besluten för effektivitet och konsekvens.

> [!TIP]
> Ämnena som diskuteras i den här artikeln gäller även för ett Power BI-projekt med standardimplementering.

## <a name="choose-power-bi-product"></a>Välja Power BI-produkt

Ett av de första besluten är att välja Power BI-produkt. Valet står mellan [Power BI-tjänsten](../fundamentals/power-bi-service-overview.md) eller [Power BI-rapportservern](../report-server/get-started.md). När innehållet har publicerats blir många andra alternativ tillgängliga, till exempel inbäddning, mobil leverans och e-postprenumerationer.

Mer information om saker att tänka på angående arkitekturen finns i **avsnitt 3** i [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP).

> [!CAUTION]
> Om du lutar mot att förlita dig på Power BI Desktop-filer lagrade i ett filsystem, ska du vara medveten om att det inte är någon optimal lösning. Att använda Power BI-tjänsten (eller Power BI-rapportservern) har avsevärda fördelar vad gäller säkerhet, innehållsdistribution och samarbete. Möjligheten att granska och övervaka aktiviteter öppnas också med Power BI-tjänsten.

## <a name="decide-on-workspace-management-approach"></a>Bestämma metod för hantering av arbetsytor

[Arbetsytor](../collaborate-share/service-new-workspaces.md) är ett centralt begrepp för Power BI-tjänsten, vilket gör att hantering av arbetsytor är en viktig aspekt av planeringen. Frågor du behöver ställa dig är bland annat:

- Krävs det en ny arbetsyta för den här nya lösningen?
- Behövs det separata arbetsytor för utveckling, testning och produktion?
- Kommer separata arbetsytor att användas för data och rapporter, eller räcker det med en enda arbetsyta? Separata arbetsytor har flera fördelar, särskilt för att skydda datamängder. Vid behov kan de hanteras separat från de användare som publicerar rapporter.
- Vilka är säkerhetskraven för arbetsytan? Det påverkar planeringen av [arbetsyteroller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Om en app ska användas av innehållskonsumenter, hanteras [behörigheter för appen](../collaborate-share/service-create-distribute-apps.md#publish-your-app) separat från arbetsytan. Särskilda behörigheter för tittare i appen ger ytterligare flexibilitet i att uppfylla säkerhetskrav för användare med skrivskyddad åtkomst till rapporter eller instrumentpaneler.
- Kan befintliga grupper användas för att skydda det nya innehållet? Både Azure Active Directory- och Microsoft 365-grupper kan användas. När de överensstämmer med befintliga processer gör användningen av grupper det enklare hantera behörigheter än tilldelningar till enskilda användare.
- Är det något särskilt man ska tänka på angående säkerhet och externa gästanvändare? Du kan behöva arbeta med Azure Active Directory-administratören och Power BI-administratören för att konfigurera [åtkomst för gästanvändare](../admin/service-admin-azure-ad-b2b.md).

> [!TIP]
> Överväg att skapa en arbetsyta för en viss affärsaktivitet eller ett visst projekt. Du kanske är frestad att börja strukturera arbetsytorna utifrån organisationens struktur (till exempel en arbetsyta per avdelning), men den här metoden visar sig ofta vara för bred.

## <a name="determine-how-content-will-be-consumed"></a>Bestämma hur innehåll ska konsumeras

Det är bra att förstå hur konsumenter av en lösning föredrar att visa rapporter och instrumentpaneler. Frågor du behöver ställa dig är bland annat:

- Är en [Power BI-app](../consumer/end-user-apps.md) (som innehåller rapporter och instrumentpaneler från en enda arbetsyta) det bästa sättet att leverera innehåll till konsumenter eller räcker det med direkt åtkomst till en arbetsyta för innehållstittare?
- Ska vissa rapporter och instrumentpaneler bäddas in någon annanstans, till exempel i [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), [SharePoint Online](../collaborate-share/service-embed-report-spo.md) eller en [säker portal eller webbplats](../collaborate-share/service-embed-secure.md)?
- Ska konsumenter komma åt innehåll med [mobila enheter](../consumer/mobile/mobile-apps-for-mobile-devices.md)? Krav för att leverera rapporter till små enheter påverkar vissa [beslut om rapportdesign](../create-reports/desktop-create-phone-report.md).

## <a name="decide-if-other-content-may-be-created"></a>Bestämma om annat innehåll kan skapas

Det finns flera viktiga beslut att fatta om att huruvida konsumenterna ska tillåtas att skapa nytt innehåll, till exempel:

- Ska konsumenter tillåtas att skapa nya rapporter från den publicerade datamängden? Den här funktionen kan aktiveras genom att tilldela [versionsbehörighet](../connect-data/service-datasets-build-permissions.md) för en datamängd till en användare.
- Om konsumenterna vill anpassa en rapport, kan de [spara en kopia](../connect-data/service-datasets-copy-reports.md) av den och anpassa den efter sina behov?

> [!CAUTION]
> Även om funktionen _Spara en kopia_ är en bra funktion, bör den användas med försiktighet när rapporten innehåller viss grafik eller sidhuvuds-/sidfotsmeddelanden. Eftersom logotyper, ikoner och textmeddelanden ofta kan hänföras till varumärkeskrav krav eller regelefterlevnad, är det viktigt att noggrant kontrollera hur de levereras och distribueras. Om _Spara en kopia_ används, men ursprunglig grafik eller sidhuvuds-/sidfotsmeddelanden förblir oförändrade av den nya författaren, kan det leda till förvirring om vem som faktiskt skapade rapporten. Det kan också minska varumärkesanpassningens betydelse.

## <a name="evaluate-needs-for-premium-capacity"></a>Utvärdera behov av Premium-kapacitet

Ytterligare funktioner är tillgängliga när en arbetsyta lagras i [Premium-kapacitet](../admin/service-premium-what-is.md). Här följer flera orsaker till varför arbetsytor i Premium-kapacitet kan vara fördelaktiga:

- Innehåll kan nås av konsumenter som inte har någon Power BI Pro-licens.
- Stöd för stora datamängder.
- Stöd för mer frekventa datauppdateringar.
- Stöd för att använda fullständiga funktioner i dataflöden.
- Enterprise-funktioner, inklusive distributionspipelines och XMLA-slutpunkten.
- Stöd för sidnumrerade rapporter (när arbetsbelastningen är aktiverad).

## <a name="determine-data-acquisition-method"></a>Bestämma metod för datainsamling

Vilka data som krävs av en rapport kan påverka flera beslut. Frågor du behöver ställa dig är bland annat:

- Kan en befintlig [delad Power BI-datamängd](../connect-data/service-datasets-share.md) användas eller är det bättre att skapa en ny Power BI-datamängd för den här lösningen?
- Måste en befintlig delad datamängd utökas med nya data eller mått för att uppfylla ytterligare behov?
- Vilket [datalagringsläge](../transform-model/desktop-storage-mode.md) är lämpligast? Alternativen omfattar Import, DirectQuery, Sammansatt eller Live-anslutning.
- Ska [aggregeringar](../transform-model/desktop-aggregations.md) användas för att förbättra prestanda för frågor?
- Är det användbart att skapa ett [dataflöde](../transform-model/service-dataflows-overview.md) och kan det fungera som en källa för flera datamängder?
- Behöver en ny [gatewaydatakälla](../connect-data/service-gateway-data-sources.md) registreras?

## <a name="decide-where-original-content-will-be-stored"></a>Bestäm var originalinnehållet ska lagras

Förutom att planera distributionsmålet är det också viktigt att planera var originalet – eller källan – till innehållet ska lagras, till exempel:

- Ange en godkänd plats för lagring av Power BI Desktop-originalfiler (.pbix). Vi rekommenderar att den här platsen endast är tillgänglig för personer som redigerar innehållet. Det bör överensstämma med hur säkerheten konfigureras i Power BI-tjänsten.
- Använd en plats för ursprungliga Power BI Desktop-filer som innehåller versionshistorik eller källkontroll. Versionshantering gör det möjligt för innehållsförfattaren att återgå till en tidigare filversion, om det behövs. OneDrive för företag eller SharePoint fungerar bra för det här ändamålet.
- Ange en godkänd plats för lagring av icke-centraliserade källdata, till exempel flata filer eller Excel-filer. Det bör vara en sökväg som alla datamängdsredigerare kan nå utan fel och som säkerhetskopieras regelbundet.
- Ange en godkänd plats för innehåll som exporteras från Power BI-tjänsten. Målet är att säkerställa att säkerhet som definierats i Power BI-tjänsten inte oavsiktligt kringgås.

> [!IMPORTANT]
> Att ange en skyddad plats för ursprungliga Power BI Desktop-filer är särskilt viktigt när de innehåller importerade data.

## <a name="assess-the-level-of-effort"></a>Utvärdera nivå för arbetsinsatsen

När tillräckligt mycket information är tillgänglig från kraven (som beskrivs i [steg 1](powerbi-migration-requirements.md)) och distributionsplaneringsprocessen för lösningen, är det nu möjligt att utvärdera nivån för arbetsinsatsen. Därefter kan du formulera en projektplan med uppgifter, tidslinje och ansvarsområden.

> [!TIP]
> Arbetskostnader – löner – är vanligtvis bland de högsta utgifterna i de flesta organisationer. Även om det kan vara svårt att göra en exakt uppskattning har produktivitetsförbättringarna en utmärkt räntabilitet (ROI).

## <a name="next-steps"></a>Nästa steg

I [nästa artikel i den här serien om Power BI-migrering](powerbi-migration-proof-of-concept.md) lär du dig mer om steg 3, som handlar om att utföra ett koncepttest för att minimera risker och åtgärda dem så tidigt som möjligt vid migrering till Power BI.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
