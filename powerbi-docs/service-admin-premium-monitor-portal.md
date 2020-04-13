---
title: Övervaka Power BI Premium-kapaciteter med hjälp av administratörsportalen
description: Använd Power BI-administratörsportalen för att övervaka dina Premium-kapaciteter.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/06/2020
LocalizationGroup: Premium
ms.openlocfilehash: 7f300cca6614f638f88886a913b30a93d0f52cfd
ms.sourcegitcommit: 2b93c1cc29aaf199ab7441a04c8e5ae49ffca5d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80813016"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Övervaka kapaciteter i administratörsportalen

Fliken **Hälsa** i **Kapacitetsinställningar** i administratörsportalen innehåller en sammanfattning av din kapacitet och aktiverade arbetsbelastningar.  

![Fliken Kapacitetshälsa i portalen](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Om du behöver mer omfattande mätningar använder du appen [Kapacitetsmått för Power BI Premium](service-admin-premium-monitor-capacity.md). Appen innehåller detaljerad information och filtrering, samt de mest detaljerade måtten för i princip varje del som påverkar kapacitetsprestandan. Läs mer i [Övervaka Premium-kapaciteter med appen](service-admin-premium-monitor-capacity.md).

> [!IMPORTANT]
> Om din Power BI Premium-kapacitet har hög resursanvändning, som medför prestanda- och tillförlitlighetsproblem, kan du få e-postmeddelanden för att identifiera och lösa problemet. Mer information finns i [meddelanden om kapacitet och tillförlitlighet](service-interruption-notifications.md#capacity-and-reliability-notifications).

## <a name="system-metrics"></a>Systemmått

På den högsta nivån på fliken **Hälsa** kan du med processor- och minnesanvändning få en snabb överblick över de viktigaste måtten för kapaciteten. Dessa mått är kumulativa och innefattar alla aktiverade arbetsbelastningar för kapaciteten.

| **Mått** | **Beskrivning** |
| --- | --- |
| PROCESSORANVÄNDNING | Genomsnittlig processoranvändning, som en procentandel av den totala tillgängliga processorkapaciteten. |
| MINNESANVÄNDNING | Genomsnittlig minnesanvändning i gigabyte (GB).|

## <a name="workload-metrics"></a>Arbetsbelastningsmått

För varje arbetsbelastning som är aktiverad för kapaciteten. Processoranvändning och minnesanvändning visas.

| **Mått** | **Beskrivning** |
| --- | --- |
| PROCESSORANVÄNDNING | Genomsnittlig processoranvändning, som en procentandel av den totala tillgängliga processorkapaciteten. |
| MINNESANVÄNDNING | Genomsnittlig minnesanvändning i gigabyte (GB).|

### <a name="detailed-workload-metrics"></a>Detaljerade arbetsbelastningsmått

Varje arbetsbelastning har ytterligare mått. Vilken typ av mått som visas beror på arbetsbelastningen. Klicka på expanderingspilen (nedåt) om du vill se detaljerade mått för en arbetsbelastning.

![Expandera hälsotillstånd för arbetsbelastning](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Dataflöden

##### <a name="dataflow-operations"></a>Dataflödesåtgärder

| **Mått** | **Beskrivning** |
| --- | --- |
| Totalt antal kärnor | Totalt antal uppdateringar för varje dataflöde. |
| Antal slutförda | Totalt antal lyckade uppdateringar för varje dataflöde.|
| Genomsnittlig varaktighet (min) | Genomsnittlig varaktighet för uppdatering för dataflödet, mätt i minuter |
| Maximal varaktighet (min) | Varaktigheten för den långvarigaste uppdateringen av dataflödet, i minuter. |
| Genomsnittlig väntetid (min) | Den genomsnittliga fördröjningen mellan schemalagd tid och start av en uppdatering av dataflödet, i minuter. |
| Maximal väntetid (min) | Maximal väntetid för dataflödet, i minuter.  |

#### <a name="datasets"></a>Datauppsättningar

##### <a name="refresh"></a>Uppdatera

| **Mått** | **Beskrivning** |
| --- | --- |
| Totalt antal kärnor | Totalt antal uppdateringar för varje datauppsättning. |
| Antal slutförda | Totalt antal lyckade uppdateringar för varje datamängd. |
| Antal misslyckade | Totalt antal misslyckade uppdateringar för varje datamängd. |
| Slutförandefrekvens  | Antal lyckade uppdateringar dividerat med det totala antalet uppdateringar som uppmätts. tillförlitlighet. |
| Genomsnittlig varaktighet (min) | Den genomsnittliga varaktigheten för uppdateringen för datauppsättningen, i minuter.  |
| Maximal varaktighet (min) | Varaktigheten för den långvarigaste uppdateringen av datauppsättningen, i minuter. |
| Genomsnittlig väntetid (min) | Den genomsnittliga fördröjningen mellan schemalagda tid och starttid för en uppdatering av datauppsättningen, i minuter. |
| Maximal väntetid (min) | Den maximala väntetiden för datauppsättningen, i minuter. |

##### <a name="query"></a>Fråga

| **Mått** | **Beskrivning** |
| --- | --- |
| Totalt antal kärnor | Det totala antal frågor som körts för datauppsättningen. |
| Genomsnittlig varaktighet (ms) |Den genomsnittliga frågevaraktigheten för datauppsättningen, mätt i millisekunder|
| Maximal varaktighet (ms) |Varaktigheten för den långvarigaste frågan i datauppsättningen, i millisekunder. |
| Snittväntetid (ms) |Den genomsnittliga frågeväntetiden för datauppsättningen, i millisekunder. |
| Maximal väntetid (ms) |Varaktigheten för den längst väntande frågan i datauppsättningen, i millisekunder. |

##### <a name="eviction"></a>Borttagning

| **Mått** | **Beskrivning** |
| --- | --- |
| Modellantal | Det totala antalet borttagna datamängder för denna kapacitet. När en kapacitet drabbas av minnesbelastning avlägsnar noden en eller flera datauppsättningar från minnet. Datamängder som är inaktiva (utan frågor/uppdateringsåtgärder som körs för tillfället) avlägsnas först. Avlägsnandeordern baseras sedan på ett mått på ”minst nyligen använd” (LRU, Least Recently Used). |

#### <a name="paginated-reports"></a>Sidnumrerade rapporter

##### <a name="report-execution"></a>Rapportkörning

| **Mått** | **Beskrivning** |
| --- | --- |
| Antal körningar  | Antalet gånger som rapporten har körts och visats av användarna.|

##### <a name="report-usage"></a>Rapportanvändning

| **Mått** | **Beskrivning** |
| --- | --- |
| Antal slutförda | Antalet gånger som rapporten har visats av en användare. |
| Antal misslyckade |Antalet gånger som rapporten har visats av en användare.|
| Radantal |Antalet rader data i rapporten. |
| Varaktighet för datahämtning (ms) |Den genomsnittliga tid det tar att hämta data för rapporten, uttryckt i millisekunder. Långa varaktigheter kan indikera långsamma frågor eller andra problem med datakällan.  |
| Bearbetningstid (ms) |Den genomsnittliga tid det tar att bearbeta data för en rapport, i millisekunder. |
| Renderingstid (ms) |Den genomsnittliga tid det tar att återge en rapport i webbläsaren, i millisekunder. |

> [!NOTE]
> Detaljerade mått för **AI-** arbetsbelastningen är ännu inte tillgängliga.

## <a name="next-steps"></a>Nästa steg

Nu när du vet hur du övervakar Power BI Premium-kapacitet kan du lära dig mer om hur du optimerar kapaciteter.

> [!div class="nextstepaction"]
> [Optimera Power BI Premium-kapaciteter](service-premium-capacity-optimize.md)
