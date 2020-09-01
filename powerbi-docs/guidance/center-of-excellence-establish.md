---
title: Upprätta ett center för utmärkthet
description: Se hur ett center för utmärkthet hjälpte Microsoft att skapa en standardiserad analys- och dataplattform som låser upp insikter med rätt driftsmodell, med ett engagemang från intressenter, samt delade och dedikerade investeringar.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: v-pemyer
ms.openlocfilehash: 477b6a1e29fc05da3004a2dcf8466ef969df4531
ms.sourcegitcommit: f73ea4b9116ad186817ec5cc5d5f487d49cc0cb0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88638622"
---
# <a name="establish-a-center-of-excellence"></a>Upprätta ett center för utmärkthet

Den här artikeln vänder sig till IT-experter och IT-chefer. Du lär dig att konfigurera ett center för utmärkthet (COE) för BI och analys i din organisation, samt hur Microsoft har konfigurerat sina.

Det finns en felaktig uppfattning om att COE bara är en supporttjänst.

I allmänhet består ett COE för BI och analys av ett team med experter som ansvarar för att upprätta och underhålla en BI-plattform. De ansvarar också för att skapa en enda faktakälla och definiera en uppsättning konsekventa företagsmått som hittar och påskyndar insikter. Ett COE är trots detta ett brett begrepp. Det kan implementeras och hanteras på olika sätt och dess struktur och omfattning kan variera från organisation till organisation. I grunden finns det alltid en robust plattform som levererar rätt data och insikter till rätt personer vid rätt tidpunkt. Helst främjar det också spridning, utbildning och support. På Microsoft beskrivs det som _[central disciplin](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ och det levereras som vår BI-plattform och en enda faktakälla.

I större organisationer kan du hitta flera COE:er där grund-COE:et har _utökats_ med satellit-COE:er – ofta på avdelningsnivå. Det innebär att en satellit-COE består av en grupp experter som har kännedom om taxonomier och definitioner, samt som vet hur man kan omvandla kärndata till det som passar bäst _för deras avdelning_. Avdelningsanalytiker beviljas behörighet till kärndata och använder den i sina egna rapporter. De skapar lösningar som förlitar sig på noggrant förberedda kärndimensioner, fakta och affärslogik. Ibland kan de även utöka med mindre, avdelningsspecifika datamängder och affärslogik. Det är viktigt att satellit-COE:er aldrig kopplas bort och de kan heller inte fungera på egen hand. På Microsoft ger satellit-COE:er en _[gränsflexibilitet](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

För att det här utökade scenariot ska lyckas, måste avdelningarna _betala för att få vara med_. Med andra ord måste avdelningarna investera finansiellt i kärn-COE:et. De behöver därför aldrig oroa sig för att de inte får en ”rättvis del”, eller att deras krav prioriteras bort.

Som stöd för det här scenariot måste kärn-COE:et skalas för att uppfylla de finansierade avdelningsbehoven. När flera datamängder har registrerats blir ekonomin påtaglig. På Microsoft blev det snabbt uppenbart att ett centralt arbete är mer ekonomiskt och ger snabbare resultat. Vartefter nya ämnesområden registrerades fick vi ännu fler ekonomiska fördelar som kunde utnyttjas och bidra till hela plattformen, och därmed förstärka vår underliggande datakultur.

Vi tar ett exempel: Vår BI-plattform levererar kärndimensioner, fakta och affärslogik för ekonomi, försäljning och marknadsföring. Den definierar också hundratals nyckelindikatorer (KPI:er). Numera måste en analytiker i Power Platform-verksamheten förbereda en instrumentpanel för ledningen. Några av KPI:erna, till exempel intäkter och pipelines, hämtas direkt från BI-plattformen. Andra baseras på mer detaljerade behov i verksamheten. Ett sådant behov av en KPI är när användaren inför den Power BI-specifika funktionen för dataflöden. Därför skapar analytikern en [sammansatt modell](composite-model-guidance.md) i Power BI som integrerar grundläggande BI-plattformsdata med avdelningsdata. Analytikern lägger sedan till affärslogik som definierar avdelningens KPI:er. Slutligen skapas en instrumentpanel för ledningen som baseras på den nya modellen. Den använder företagets COE-resurser som har förstärkts med lokal kunskap och data.

En uppdelning av ansvaret mellan kärn- och satellit-COE:er gör det möjligt för avdelningsanalytiker att fokusera på att skapa nytt, i stället för att hantera en dataplattform. Ibland kan det även finnas en ömsesidigt fördelaktig relation mellan satellit-COE:er och kärn-COE:n. Till exempel kan en satellit-COE definiera nya mått som – när de har visat sig vara till nytta på deras avdelning – visar sig vara kärnmått som är användbara för hela företaget, tillgängliga från – och med stöd av – kärn-COE:n.

## <a name="bi-platform"></a>BI-plattform

I din organisation kan COE:er ha ett annat namn, t.ex. BI-teamet eller BI-gruppen. Det som COE:n faktiskt utför är viktigare än vad den heter. Om du inte har en formell grupp rekommenderar vi att du skapar ett team med dina BI-experter för att upprätta BI-plattformen.

På Microsoft kallas COE för BI-plattformen. Den består av många intressentgrupper som representerar olika avdelningar på företaget, till exempel ekonomi, försäljning och marknadsföring. Den är utformad för att köra [delade funktioner](#shared-capabilities) och [dedikerade leveranser](#dedicated-deliveries).

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="Diagrammet visar de delade funktioner och dedikerade leveranser som beskrivs i följande avsnitt.":::

### <a name="shared-capabilities"></a>Delade funktioner

Delade funktioner krävs för att kunna upprätta och driva BI-plattformen. De har stöd för alla intressentgrupper som finansierar plattformen. De består av följande team:

- **Teknik för kärnplattformen:** Vi har utformat BI-plattformen ur en teknisk synvinkel. Det är egentligen en uppsättning ramverk som har stöd för datainmatning, bearbetning för att utöka data, samt leverans av dessa data i BI-semantikmodeller för att kunna analysera förbrukningen. Teknikerna ansvarar för den tekniska utformningen och implementeringen av kärnfunktionerna i BI-plattformen. De kan till exempel utforma och implementera datapipelines.
- **Infrastruktur och värdtjänster:** IT-teknikerna ansvarar för etablering och hantering av alla Azure-tjänster.
- **Support och drift:** Det här teamet håller plattformen igång. Supporten tar hand om användarbehov som exempelvis databehörighet. Driften håller plattformen igång, säkerställer att serviceavtal är uppfyllda och kommunicerar vid förseningar eller fel.
- **Versionshantering:** Versionsändringar från tekniska programchefer. Ändringar kan variera från uppdateringar av plattformens ramverk till ändringsbegäranden för BI-semantikmodeller. De är den sista utposten som ser till att ändringar inte förstör något.

### <a name="dedicated-deliveries"></a>Dedikerade leveranser

Det finns ett dedikerat leveransteam för varje intressentgrupp. Det består vanligtvis av en datatekniker, en analystekniker och en teknisk programchef. Allt finansieras av deras intressentgrupp.

## <a name="bi-team-roles"></a>BI-teamroller

På Microsoft drivs vår BI-plattform av skalbara expertteam. Teamen anpassas efter dedikerade och delade resurser. Just nu har vi följande roller:

- **Programchefer:** Programchefer är en dedikerad resurs. De fungerar som den primära kontakten mellan BI-teamet och intressenterna. Det är deras jobb att översätta intressenternas affärskrav till en teknisk specifikation. De hanterar även prioriteringen av intressenternas slutprodukter.
- **Databasleads:** De är en dedikerad resurs som ansvarar för att registrera nya datamängder i det centraliserade informationslagret. Att registrera en datamängd kan omfatta konfiguration av fördefinierade dimensioner, lägga till affärslogik och anpassade attribut, samt standardnamn och formatering.
- **Analysleads:** De är en dedikerad resurs som ansvarar för utformningen och utvecklingen av BI-semantikmodeller. De strävar efter att tillämpa en konsekvent arkitektur med standardnamn och formatering. Prestandaoptimering är en viktig del av deras roll.
- **Drift och infrastruktur:** De är en delad resurs som ansvarar för att hantera jobb och datapipelines. De är också ansvariga för att hantera Azure-prenumerationer, Power BI-kapaciteter, virtuella datorer och datagatewayer.
- **Support:** De är en delad resurs som ansvarar för att skriva dokumentation, organisera utbildning, kommunicera ändringar i BI-semantikmodeller och besvara användarfrågor.

## <a name="governance-and-compliance"></a>Styrning och efterlevnad

För varje intressentgrupp erbjuder programcheferna styrning och tillsyn över olika program. Det övergripande målet är att säkerställa att investeringar i IT genererar affärsvärde och minimerar risker. Styrningskommitténs möten hålls regelbundet i syfte att granska framsteg och godkänna större initiativ.

## <a name="grow-your-own-community"></a>Bygg upp en egen community

Upprätta och främja en community i organisationen genom att göra följande:

- Ordna evenemang på ordinarie arbetstid där BI-teamet deltar och användare kan ställa frågor, komma med förslag, dela med sig av idéer och framföra klagomål.
- Skapa en egen supportkanal i Teams och uppmuntra alla att ställa och svara på publicerade frågor.
- Genomför och främja informella användargrupper och uppmuntra medarbetare att närvara och delta.
- Genomför mer formella utbildningstillfällen om vissa produkter och själva BI-plattformen. Överväg att genomföra [Power BI-instrumentpanelen på en dag](https://powerbi.microsoft.com/diad/), som är tillgänglig som kostnadsfritt kurspaket och som är ett bra sätt att introducera medarbetarna till Power BI för första gången.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [BI-lösningsarkitektur i COE](center-of-excellence-business-intelligence-solution-architecture.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)

I [nästa artikeln i den här serien](center-of-excellence-business-intelligence-solution-architecture.md) lär du dig mer om BI-lösningsarkitekturen i COE och de olika tekniker som används.

### <a name="professional-services"></a>Professionella tjänster

Certifierade Power BI-partners finns där och kan hjälpa din organisation att starta ett COE. De kan erbjuda kostnadseffektiv utbildning eller en granskning av dina data. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).

Du kan också kontakta erfarna konsultpartners. De kan hjälpa dig att [bedöma](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [utvärdera](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) eller [implementera](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
