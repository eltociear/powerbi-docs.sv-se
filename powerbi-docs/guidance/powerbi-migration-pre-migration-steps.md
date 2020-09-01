---
title: Förbereda för att migrera till Power BI
description: Vägledning om förberedelser före migrering till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 9a5ed3d2a4798332de2394e1ad5be6fdbdb6eeae
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803387"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Förbereda för att migrera till Power BI

I den här artikeln beskrivs åtgärder som du kan överväga innan du migrerar till Power BI.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Bild som visar stegen i en Power BI-migrering. Stegen före migreringen beskrivs i den här artikeln.":::

> [!NOTE]
> En fullständig förklaring av bilden ovan finns i [Översikt över Power BI-migrering](powerbi-migration-overview.md).

Stegen före migreringen betonar planeringen i förväg, vilket är viktigt innan du går igenom de fem stegen i migreringen. De flesta av stegen före migreringen sker endast en gång, men för större organisationer kan vissa delar upprepas för varje affärsenhet eller avdelning.

Resultatet av stegen före migreringen omfattar en initial styrningsmodell, en initial översiktlig distributionsplan, förutom en inventering av de rapporter och data som ska migreras. Ytterligare information från aktiviteter i steg 1, 2 och 3 är nödvändig för att helt kunna uppskatta arbetsinsatsen för att migrera enskilda lösningar.

> [!TIP]
> De flesta ämnena som diskuteras i den här artikeln gäller även för ett Power BI-projekt med standardimplementering.

## <a name="create-costbenefit-analysis-and-evaluation"></a>Skapa kostnad–fördels-analys och -utvärdering

Det finns många viktiga överväganden att göra vid den första utvärderingen:

- Tydlighet i affärsstudien och BI-strategin för att uppnå ett visst önskat framtida tillstånd.
- Tydlighet om vad framgång innebär och hur framsteg och framgång för migreringen ska mätas.
- Beräkningsresultat av kostnadsuppskattningar och räntabilitet.
- Lyckade resultat för flera produktiva Power BI-initiativ som är mindre till sin omfattning och komplexitetsnivå.

## <a name="identify-stakeholders-and-executive-support"></a>Identifiera intressenter och stöd från chefer

Det finns flera saker att tänka på när du identifierar intressenter:

- Se till att intressenterna är överens i fråga om affärsstudien och i BI-strategin.
- Ta med företrädare från alla affärsenheterna – även om deras innehåll inte ska migreras förrän vid ett senare tillfälle – för att förstå deras motivation och problem.
- Involvera Power BI-experter tidigt.
- Skapa och följ en kommunikationsplan med intressenterna.

> [!TIP]
> Om du känner att du börjar kommunicera för mycket är det förmodligen precis rätt nivå.

## <a name="generate-initial-governance-model"></a>Skapa initial styrningsmodell

Det finns flera viktiga punkter att ta itu med tidigt i en Power BI-implementering:

- Specifika mål för Power BI-introduktionen och var Power BI passar i den övergripande BI-strategin för organisationen.
- Hur Power BI-administratörsrollen ska hanteras, särskilt i decentraliserade organisationer.
- Principer för att uppnå betrodda data: användning av auktoritativa datakällor, åtgärdande av datakvalitetsproblem och användning av konsekvent terminologi och gemensamma definitioner.
- Strategi för säkerhet och datasekretess för datakällor, datamodeller, rapporter och innehållsleverans till interna och externa användare.
- Hur interna och externa krav på efterlevnad, reglering och granskning ska uppfyllas.

> [!IMPORTANT]
> Den mest effektiva styrningsmodellen strävar efter att balansera användarbefogenheter med nödvändig kontrollnivå. Läs mer om [central disciplin](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) och [gränsflexibilitet](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="conduct-initial-deployment-planning"></a>Genomför initial distributionsplanering

Den första distributionsplaneringen handlar om att definiera standarder, principer och önskemål för organisationens Power BI-implementering.

Observera att i [steg 2](powerbi-migration-planning.md) hänvisas det till distributionsplanering på lösningsnivå. Aktiviteterna inom steg 2 bör respektera besluten på organisationsnivå så långt som möjligt.

Det finns några kritiska punkter att hantera tidigt i en Power BI-implementering:

- Beslut om [administratörsinställningen för Power BI-klientorganisationen](admin-tenant-settings.md), som bör dokumenteras.
- Beslut om [arbetsytehantering](../collaborate-share/service-new-workspaces.md), som bör dokumenteras.
- Överväganden och val i fråga om data och [metoder för innehållsdistribution](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md), till exempel appar, arbetsytor, delning, prenumerationer och inbäddning av innehåll.
- Val som rör [datamängdslägen](../connect-data/service-dataset-modes-understand.md), till exempel användning av importläge, DirectQuery-läge eller en kombination av de två lägena i en [sammansatt modell](composite-model-guidance.md).
- [Skydda data och åtkomst](../admin/service-admin-power-bi-security.md).
- Arbeta med [delade datamängder](../connect-data/service-datasets-share.md) för återanvändningsbarhet.
- Använda [datacertifiering](../connect-data/service-datasets-certify.md) för att främja användningen av auktoritativa och tillförlitliga data.
- Användning av olika [rapporttyper](../create-reports/index.yml), inklusive Power BI-rapporter, Excel-rapporter eller sidnumrerade rapporter för olika användningsscenarier eller affärsenheter.
- Metoder för ändringshantering för att hantera centraliserade BI-artefakter och affärshanterade BI-artefakter.
- Utbildningsplaner för konsumenter, datamodellerare, rapportförfattare och administratörer.
- Stöd till innehållsförfattare med [Power BI Desktop-mallar](../create-reports/desktop-templates.md), [anpassade visuella objekt](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/)och dokumenterade rapportdesignsstandarder.
- Procedurer och processer för att hantera användarkrav, till exempel att begära nya licenser, lägga till nya gateway-datakällor, få behörighet till gateway-datakällor, begära nya arbetsytor, ändra arbetsytans behörigheter och andra vanliga krav som kan uppstå regelbundet.

> [!IMPORTANT]
> Distributionsplanering är en iterativ process. Distributionsbeslut förfinas och utvidgas många gånger i takt med att organisationens erfarenhet av Power BI växer och Power BI utvecklas. Besluten som fattas under den här processen används under distributionsplaneringen på lösningsnivå som beskrivs i [steg 2](powerbi-migration-planning.md) av migreringsprocessen.

## <a name="establish-initial-architecture"></a>Upprätta initial arkitektur

Din [BI-lösningsarkitektur](center-of-excellence-business-intelligence-solution-architecture.md) utvecklas och mognar över tid. Uppgifter för Power BI-installationen som ska hanteras direkt omfattar följande:

- Skapa och integrera Power BI-klientorganisationen med Azure Active Directory.
- Definiera [Power BI-administratörer](../admin/service-admin-role.md).
- Införskaffa och tilldela initiala [användarlicenser](../admin/service-admin-licensing-organization.md).
- Konfigurera och granska [administratörsinställningar för Power BI-klientorganisationen](admin-tenant-settings.md).
- Konfigurera [arbetsyteroller](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) och tilldela åtkomst till Azure Active Directory-säkerhetsgrupper och -användare.
- Konfigurera ett första [datagateway](../connect-data/service-gateway-deployment-guidance.md)-kluster, med en plan för att uppdatera det regelbundet.
- Införskaffa initial [Premium-kapacitetslicens](../admin/service-admin-premium-purchase.md) (om tillämpligt).
- Konfigurera [arbetsbelastningar för Premium-kapacitet](../admin/service-admin-premium-workloads.md), med en plan för att hantera dem regelbundet.

## <a name="define-success-criteria-for-migration"></a>Definiera framgångskriterier för migreringen

Den första uppgiften är att förstå hur framgång ser ut vid migrering av en enskild lösning. Frågor som du kan ställa omfattar följande:

- **Vilka är de specifika motiven och målen för den här migreringen?** Mer information finns i [Översikt över Power BI-migrering (Ta hänsyn till migrationsorsaker)](powerbi-migration-overview.md#consider-migration-reasons). I den här artikeln beskrivs de vanligaste orsakerna till att migrera till Power BI. Målen bör absolut anges på organisationsnivå. Utöver detta kan migreringen av en äldre BI-lösning ge kostnadsbesparingar, medan migrering av en annan äldre BI-lösning kan fokusera på att optimera arbetsflöden.
- **Vilken förväntad kostnad–nytta eller räntabilitet har den här migreringen?** En tydlig förståelse av förväntningar i fråga om kostnader, ökade funktioner, minskad komplexitet eller ökad flexibilitet, är användbart för att mäta framgång. Den kan ligga till grund för vägledande principer som hjälper dig att fatta beslut under migreringsprocessen.
- **Vilka nyckeltal (KPI:er) ska användas för att mäta framgång?** I följande lista presenteras några exempel på KPI:er:
    - Antalet rapporter som renderas från en äldre BI-plattform, som minskar från månad till månad.
    - Antalet rapporter som renderas från Power BI, som ökar från månaden till månad.
    - Antalet konsumenter av Power BI-rapporter, som ökar från kvartal till kvartal.
    - Andelen rapporter som migrerats till produktion efter måldatum.
    - Kostnadsminskning för licenskostnader från år till år.

> [!TIP]
> [Power BI-aktivitetsloggen](../admin/service-admin-auditing.md) kan användas som källa för att mäta förändringen av KPI:erna.

## <a name="prepare-inventory-of-existing-reports"></a>Förbereda inventering av befintliga rapporter

Att förbereda en inventering av befintliga rapporter i en äldre BI-plattform är ett viktigt steg mot att förstå vad som redan finns. Resultatet av det här steget är ett underlag för att utvärdera hur stort arbete migreringen innebär. Aktiviteter som rör förberedelse av en inventering kan omfatta:

1. **Inventering av rapporter:** Sammanställ en lista över rapporter och instrumentpaneler som är kandidater för migrering.
2. **Inventering av datakällor:** Sammanställ en lista över alla datakällor som används av befintliga rapporter. Den bör omfatta både företagsdatakällor, avdelningsdatakällor och personliga datakällor. Den här processen kan blottlägga datakällor som inte tidigare var kända för IT-avdelningen, vilket kan kallas _skugg-IT_.
3. **Granskningslogg:** Hämta data från den äldre BI-plattformens granskningslogg för att förstå användningsmönster och som hjälp för prioritering. Viktig information som du kan hämta från granskningsloggen omfattar följande:
    - Genomsnittligt antal gånger som varje rapport kördes per vecka/månad/kvartal.
    - Genomsnittligt antal konsumenter per rapport per vecka/månad/kvartal.
    - Konsumenter för varje rapport, särskilt rapporter som används av chefer.
    - Senaste datum då varje rapport kördes.

> [!NOTE]
> I många fall migreras inte innehållet till Power BI exakt som det är. Migreringen utgör ett tillfälle att omforma dataarkitekturen och/eller förbättra rapportleveransen. Att kompilera en inventering av rapporter är viktigt för att förstå vad som finns för närvarande, så att du kan börja bedöma vad som behöver göras. Återstående artiklar i den här serien beskriver möjliga förbättringar i detalj.

## <a name="explore-automation-options"></a>Utforska automatiseringsalternativ

Det går inte att helt automatisera en Power BI-konvertering från början till slut.

En möjlig kandidat för automation är uppgiften att sammanställa den befintliga inventeringen av data och rapporter om du har ett befintligt verktyg som kan göra det åt dig. I vilken utsträckning automation kan användas för vissa delar av migreringsprocessen, till exempel att sammanställa inventeringen, beror främst på vilka verktyg du har.

## <a name="next-steps"></a>Nästa steg

I [nästa artikel i den här serien om Power BI-migrering](powerbi-migration-requirements.md) lär du dig mer om steg 1 som handlar om att samla in och prioritera kraven när du migrerar till Power BI.

Andra användbara resurser är:

- [Microsoft BI-omvandling](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

Våra erfarna Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
