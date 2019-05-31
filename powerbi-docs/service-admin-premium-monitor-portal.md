---
title: Övervaka Power BI Premium-kapaciteter med hjälp av administratörsportalen
description: Använd Power BI-administratörsportalen för att övervaka dina Premium-kapaciteter.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564900"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Övervaka kapaciteter i administratörsportalen

Den **hälsotillstånd** fliken i den **kapacitetsinställningarna** område i Admin portal innehåller en sammanfattning om din kapacitet och aktiverade arbetsbelastningar.  

![Kapacitet på fliken hälsa i portalen](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Om du behöver mer omfattande mått kan använda den [Power BI Premium-kapacitet](service-admin-premium-monitor-capacity.md) app. Appen ger nedåt och filtrering och de mest detaljerade mätvärden för nästan alla aspekter som påverkar prestanda för kapacitet. Mer information finns i [övervakaren Premium-kapaciteter med appen](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Systemmått

På den **hälsotillstånd** på den högsta nivån, fliken processoranvändning och minnesanvändning ge en snabb överblick över de viktigaste mått för kapaciteten. De här måtten är kumulativa, inklusive alla aktiverade arbetsbelastningar för kapaciteten.

| **Mått** | **Beskrivning** |
| --- | --- |
| CPU-ANVÄNDNING | Genomsnittlig CPU-belastning, som en procentandel av total tillgänglig CPU. |
| MINNESANVÄNDNING | Genomsnittlig användning av minne i gigabyte (GB).|

## <a name="workload-metrics"></a>Nyckelmått för arbetsbelastningen

För varje arbetsbelastning har aktiverats för kapaciteten. Processoranvändning och minnesanvändning visas.

| **Mått** | **Beskrivning** |
| --- | --- |
| CPU-ANVÄNDNING | Genomsnittlig CPU-belastning, som en procentandel av total tillgänglig CPU. |
| MINNESANVÄNDNING | Genomsnittlig användning av minne i gigabyte (GB).|

### <a name="detailed-workload-metrics"></a>Detaljerad arbetsbelastning

Varje arbetsbelastning har ytterligare mått. Vilken typ av mått som visas beror på arbetsbelastningen. Klicka på Expandera (nedåtpilen) om du vill visa detaljerade mätvärden för en arbetsbelastning.

![Expandera arbetsbelastning hälsotillstånd](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Dataflöden

##### <a name="dataflow-operations"></a>Dataflöde åtgärder

| **Mått** | **Beskrivning** |
| --- | --- |
| Totalt antal kärnor | Totalt antal uppdateringar för varje dataflöde. |
| Antal slutförda | Totalt antal lyckade uppdateringar för varje dataflöde.|
| Genomsnittlig varaktighet (min) | Genomsnittlig varaktighet för uppdatering för dataflödet, mätt i minuter |
| Maximal varaktighet (min) | Varaktigheten för den långvarigaste uppdateringen av dataflödet, i minuter. |
| Snittväntetid (min) | Den genomsnittliga fördröjningen mellan schemalagd tid och start av en uppdatering av dataflödet, i minuter. |
| Maximal väntetid (min) | Maximal väntetid för dataflödet, i minuter.  |

#### <a name="datasets"></a>Datauppsättningar

##### <a name="refresh"></a>Uppdatera

| **Mått** | **Beskrivning** |
| --- | --- |
| Totalt antal kärnor | Totalt antal uppdateringar för varje datauppsättning. |
| Antal slutförda | Totalt antal lyckade uppdateringar för varje datauppsättning. |
| Antal misslyckade | Totalt antal misslyckade uppdateringar för varje datauppsättning. |
| Slutförandefrekvens  | Antal lyckade uppdateringar dividerat med Totalt antal uppdateringar ska mätas. Tillförlitlighet. |
| Genomsnittlig varaktighet (min) | Den genomsnittliga varaktigheten för uppdateringen för datauppsättningen, i minuter.  |
| Maximal varaktighet (min) | Varaktigheten för den långvarigaste uppdateringen av datauppsättningen, i minuter. |
| Snittväntetid (min) | Den genomsnittliga fördröjningen mellan schemalagda tid och starttid för en uppdatering av datauppsättningen, i minuter. |
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
| Modell-antal | Totalt antal borttagna datauppsättningen för den här kapaciteten. När en kapacitet drabbas av minnesbelastning avlägsnar noden en eller flera datauppsättningar från minnet. Datamängder som är inaktiva (utan frågor/uppdateringsåtgärder som körs för tillfället) avlägsnas först. Avlägsnandeordern baseras sedan på ett mått på ”minst nyligen använd” (LRU, Least Recently Used). |

#### <a name="paginated-reports"></a>Sidnumrerade rapporter

##### <a name="report-execution"></a>Köra en hälsorapport

| **Mått** | **Beskrivning** |
| --- | --- |
| Antal körningar  | Hur många gånger som rapporten har körts och visas för användare.|

##### <a name="report-usage"></a>Rapportera användning

| **Mått** | **Beskrivning** |
| --- | --- |
| Antal slutförda | Antal gånger som rapporten har setts av en användare. |
| Antal misslyckade |Antal gånger som rapporten har setts av en användare.|
| Radantal |Antalet rader data i rapporten. |
| Varaktighet för hämtning (ms) |Den genomsnittliga tid det tar att hämta data för rapporten, uttryckt i millisekunder. Långa varaktigheter kan indikera långsamma frågor eller andra problem med datakällan.  |
| Bearbetning av varaktighet (ms) |Den genomsnittliga tid det tar att bearbeta data för en rapport, i millisekunder. |
| Rendering varaktighet (ms) |Den genomsnittliga tid det tar att återge en rapport i webbläsaren, i millisekunder. |

> [!NOTE]
> Detaljerad mått för den **AI** arbetsbelastning är inte tillgängliga ännu.

## <a name="next-steps"></a>Nästa steg

Nu när du vet hur du övervakar Power BI Premium-kapacitet kan du lära dig mer om hur du optimerar kapaciteter.

> [!div class="nextstepaction"]
> [Optimera Power BI Premium-kapaciteter](service-premium-capacity-optimize.md)
