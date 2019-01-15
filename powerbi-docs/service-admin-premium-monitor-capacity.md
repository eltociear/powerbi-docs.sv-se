---
title: Övervaka Power BI Premium-kapaciteter i din organisation
description: Använd Power BI-administratörsportalen och appen Power BI Premium Capacity Metrics
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/13/2018
LocalizationGroup: Premium
ms.openlocfilehash: e8e69cdacb9ee54cdf19724c590f994f66c4dff7
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290646"
---
# <a name="monitor-power-bi-premium-and-power-bi-embedded-capacities"></a>Övervaka Power BI Premium- och Power BI Embedded-kapaciteter

Den här artikeln innehåller en översikt över övervakning av mått för dina Power BI Premium-kapaciteter. Genom att övervaka kapacitetsförbrukningen kan du hantera din kapacitet på ett genomtänkt sätt.

Du kan övervaka kapaciteten med appen Power BI Premium Capacity Metrics eller i administrationsportalen. Vi rekommenderar appen, eftersom det ger mycket mer detaljerad information, men den här artikeln beskriver båda alternativen.

**Den aktuella versionen av appen är 1.10 (släpptes den 13 december 2018).**

.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UgsjMbhi_Bk?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="install-the-premium-capacity-metrics-app"></a>Installera appen Premium Capacity Metrics

Du kan gå direkt till [Premium Capacity Metrics-appen](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) eller installera den precis som andra appar i Power BI.

1. I Power BI klickar du på **Appar**.

    ![Gå till Appar](media/service-admin-premium-monitor-capacity/apps.png)

1. Till höger klickar du på **Hämta appar**.

1. I kategorin **Appar** söker du efter **Power BI Premium Capacity Metrics-appen**.

1. Prenumerera för att installera appen.

Nu när du har installerat appen kan du se mått som gäller kapaciteterna i din organisation. Låt oss ta en titt på några av de viktigaste måtten som är tillgängliga.

## <a name="use-the-metrics-app"></a>Använda måttappen

### <a name="metrics-dashboard"></a>Instrumentpanelen med mätvärden

När du öppnar appen visas först en instrumentpanel med en sammanfattning av alla kapaciteter som du har administratörsrättigheter till.

![Instrumentpanelen med mätvärden för app](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Instrumentpanelen innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Systemöversikt** | * Programmets version<br> * Antal kapaciteter du är administratör för<br> * Antal arbetsytor i dina kapaciteter som rapporterar mått<br> * Genomsnittlig minnesförbrukning i GB under de senaste sju dagarna<br> * Maximal minnesförbrukning i GB under de senaste sju dagarna<br> * Lokal tid då den maximala minnesförbrukningen inträffade<br> * Antal gånger som CPU har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa buckets<br> * De flesta gånger CPU överskred 80 % under de senaste sju dagarna, uppdelat på en timme långa buckets<br> * Lokal tid då CPU överskred 80 % flest gånger under en timme |
| **Översikt över datauppsättning** | * Totalt antal datauppsättningar för alla arbetsytor i dina kapaciteter<br> * Antal gånger som Direct Query/Live-anslutningar har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa buckets<br> * De flesta gånger Direct Query/Live-anslutningar har överskridit 80 % under de senaste sju dagarna, uppdelat på en timme långa buckets<br> * Lokal tid då Direct Query/Live-anslutningar överskred 80 % flest gånger i timmen<br> * Totalt antal uppdateringar under de senaste sju dagarna<br> * Genomsnittlig väntetid för uppdatering – den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och uppdateringens start<br> * Genomsnittlig uppdateringstid – den tid, mätt i minuter, det tar att slutföra uppdateringen<br> * Totalt antal frågor som körts under de senaste sju dagarna<br> * Genomsnittlig väntetid för fråga – den tid, mätt i millisekunder, som en fråga väntade på systemresurser innan körningen startades<br> * Genomsnittlig frågevaraktighet – den tid, mätt i millisekunder, det tar att slutföra frågan<br> * Totalt antal modeller som tagits bort på grund av minnestryck<br> * Genomsnittlig storlek på datauppsättningar <br> * Genomsnittligt antal datauppsättningar som läses in i minnet |
| **Översikt över dataflöde** | * Totalt antal dataflöden för alla arbetsytor i dina kapaciteter<br> * Totalt antal uppdateringar under de senaste sju dagarna<br> * Genomsnittlig väntetid för uppdatering – den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och uppdateringens start<br> * Genomsnittlig uppdateringstid – den tid, mätt i minuter, det tar att slutföra uppdateringen |
| **Översikt över sidnumrerade rapporter** | * Totalt antal sidnumrerade rapporter för alla arbetsytor i dina kapaciteter<br> * Totalt antal gånger som alla rapporter har setts av användare<br> * Totalt antal rader med data i alla rapporter<br> * Total tid det tar för alla faser (datahämtning, bearbetning och återgivning) för alla rapporter, i millisekunder |
|  |  |

### <a name="metrics-report"></a>Måttrapport

Gå till den underliggande rapporten genom att klicka på instrumentpanelen. Rapporten har fem flikar som vi beskriver i detalj i följande avsnitt.

* **Dataumängder**: Innehåller detaljerade mätvärden om hälsotillståndet för Power BI-datamängderna i dina kapaciteter.

* **Sidnumrerade rapporter**: Innehåller detaljerade mätvärden om hälsotillståndet för sidnumrerade rapporter i dina kapaciteter.

* **Dataflöden**: Innehåller detaljerade uppdateringsmätvärden för dataflöden i dina kapaciteter.

* **Resursförbrukning**: Innehåller mätvärden för den totala kapaciteten, inklusive minne och hög CPU-användning.

* **ID:n och info**: Namn, ID:n och ägare för kapaciteter, arbetsytor och arbetsbelastningar.

Du kan filtrera mått efter kapacitet och datumintervall på varje flik. Om inga filter har markerats använder rapporten standardinställningarna för att visa den senaste veckans mått för alla kapaciteter som rapporterar mått.

#### <a name="datasets-tab"></a>Fliken Datauppsättningar

Navigera till olika områden genom att använda knapparna överst på fliken **Datauppsättningar**: **Sammanfattning**, **Uppdateringar**, **Frågevaraktigheter**, **Frågeväntan** och **Datauppsättningar**.

![Fliken Datauppsättningar](media/service-admin-premium-monitor-capacity/datasets-tab.png)

##### <a name="refreshes-area"></a>Området Uppdaterar

Området **Uppdateringar** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Uppdateringstillförlitlighet** | * Totalt antal: Totalt antal uppdateringar för varje datauppsättning<br> * Tillförlitlighet: Procentandelen uppdateringar som har slutförts för varje datauppsättning<br> * Genomsnittlig väntetid: Den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och starten av en uppdatering av datauppsättningen<br> * Maximal väntetid: Maximal väntetid för datauppsättningen, mätt i minuter <br> * Genomsnittlig varaktighet: Genomsnittlig varaktighet för uppdatering för datauppsättningen, mätt i minuter<br> * Maximal varaktighet: Varaktigheten för den långvarigaste uppdateringen av datauppsättningen, mätt i minuter |
| **De 5 främsta datauppsättningarna efter genomsnittlig uppdateringsvaraktighet** | * De fem datauppsättningarna med den längsta genomsnittliga uppdateringsvaraktigheten, mätt i minuter |
| **De 5 främsta datauppsättningarna efter genomsnittlig väntetid** | * De fem datauppsättningarna med den längsta genomsnittliga uppdateringsväntetiden, mätt i minuter |
| **Genomsnittlig uppdateringsväntetid uppdelad i timmar** | * Den genomsnittliga uppdateringsväntetiden, uppdelad i timbucketar, rapporterad i lokal tid. Många toppar med långa uppdateringsväntetider tyder på att kapaciteten körs för hårt. |
| **Antal uppdateringar och minnesförbrukning per timma** | * Lyckade och misslyckade åtgärder och minnesförbrukning, uppdelade i timbucketar, rapportede i lokal tid |
|  |  |

##### <a name="query-durations-area"></a>Frågevaraktighetsområde

Området **Frågevaraktighet** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Frågevaraktighet** | * Data i det här avsnittet är indelade i datauppsättningar, arbetsytor och timbucketar under de senaste sju dagarna<br> * Totalt: Det totala antal frågor som körs för datauppsättningen<br> * Medelvärde: Den genomsnittliga frågevaraktigheten för datauppsättningen, mätt i millisekunder<br> * Max: Varaktigheten för den långvarigaste frågan i datauppsättningen, mätt i millisekunder|
| **Frågevaraktighetsfördelning** | * Frågevaraktighetens histogram bucketeras efter frågevaraktighet (i millisekunder) i följande kategorier: intervall på < = 30 ms, 30-100 ms, 100-300 ms, 300 ms-1 sek, 1-3 sek, 3-10 sek, 10-30 sek och > 30 sek. Lång frågevaraktighet och långa väntetider är en tydlig indikation på kapaciteten utsätts för mycket hög belastning. Det kan också innebära att en enskild datauppsättning orsakar problem och ytterligare utredning krävs. |
| **De 5 främsta datauppsättningarna efter genomsnittlig varaktighet** | * De fem datauppsättningarna med den längsta genomsnittliga frågevaraktigheten, mätt i millisekunder |
| **Direct Query/Live-anslutningar (> 80 % utnyttjande)** | * De tider som en direktfråga eller live-anslutning har överskridit 80 % CPU-belastning, uppdelat i timbucketar, rapporterat i lokal tid |
| **Frågevaraktighetsfördelning per timma** | * Antal frågor och genomsnittlig varaktighet (i millisekunder) jämfört med minnesanvändningen i GB, uppdelat i timbucketar uttryckta i lokal tid |
|  |  |

##### <a name="query-waits-area"></a>Frågeväntansområde

Området **Frågeväntan** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Fråga väntetider** | * Data i det här avsnittet är indelade i datauppsättningar, arbetsytor och timbucketar under de senaste sju dagarna<br> * Totalt: Det totala antal frågor som körs för datauppsättningen<br> * Antal väntande: Det antal frågor i den datauppsättning som väntade på systemresurser innan körningen startades <br> * Medelvärde: Den genomsnittliga frågeväntetiden för datauppsättningen, mätt i millisekunder<br> * Max: Varaktigheten för den längst väntande frågan i datauppsättningen, mätt i millisekunder|
| **Väntetidsfördelning** | * Frågevaraktighetens histogram bucketeras efter frågevaraktigheter (i millisekunder) i följande kategorier: intervall på <= 50 ms , 50-100 ms , 100-200 ms , 200-400 ms 400 ms-1 sek, 1-5 sek och > 5 sek |
| **De 5 främsta datauppsättningarna efter genomsnittlig väntetid** | * De fem datauppsättningarna med den längsta genomsnittliga väntetiden för att börja köra en fråga, mätt i millisekunder |
| **Antal väntande frågor och väntetid per timma** | * Antal väntande frågor och genomsnittlig väntetid (i millisekunder) jämfört med minnesanvändningen i GB, uppdelat i timbucketar uttryckta i lokal tid |
|  |  |

##### <a name="datasets-area"></a>Området Datamängder

Området **Datauppsättningar** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Antal borttagna datauppsättningar** | * Totalt: Det totala antalet *avlägsnade* datauppsättningar för respektive kapacitet. När en kapacitet drabbas av minnesbelastning avlägsnar noden en eller flera datauppsättningar från minnet. Datamängder som är inaktiva (utan frågor/uppdateringsåtgärder som körs för tillfället) avlägsnas först. Avlägsnandeordern baseras sedan på ett mått på ”minst nyligen använd” (LRU, Least Recently Used).|
| **Antal borttagna datauppsättningar och minnesförbrukning per timma** | * Borttagna datauppsättningar jämfört med minnesförbrukning i GB, uppdelat i timbucketar, uttryckt i lokal tid |
| **Inlästa datauppsättningar per timme** | * Antal datauppsättningar som läses in i minnet jämfört med minnesförbrukning i GB, uppdelat i timbucketar, uttryckt i lokal tid |
| **Datastorlekar**  | * Maxstorlek: Maxstorleken för datauppsättningen i MB för perioden som visas |
|  |  |

#### <a name="paginated-reports-tab"></a>Fliken Sidnumrerade rapporter

Fliken **Sidnumrerade rapporter** innehåller detaljerade mätvärden om hälsotillståndet för sidnumrerade rapporter i dina kapaciteter.

![Fliken Sidnumrerade rapporter](media/service-admin-premium-monitor-capacity/paginated-reports-tab.png)

Fliken **Sidnumrerade rapporter** fliken innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Total användning** | * Totalt antal visningar: Det antal gånger som rapporten har setts av användare<br> * Radantal: Antalet rader med data i rapporten<br> * Hämtning (medelvärde): Den genomsnittliga tid det tar att hämta data för rapporten, uttryckt i millisekunder. Långa varaktigheter kan indikera långsamma frågor eller andra problem med datakällan. <br> * Bearbetning (medelvärde): Den genomsnittliga tid det tar att bearbeta data för en rapport, uttryckt i millisekunder<br>* Återgivning (medelvärde): Den genomsnittliga tid det tar att återge en rapport i webbläsaren, uttryckt i millisekunder<br> * Total tid: Den tid det tar för alla faser i en rapport, uttryckt i millisekunder|
| **De 5 främsta rapporterna efter genomsnittlig datahämtningstid** | * De fem rapporterna med den längsta genomsnittliga datahämtningstiden, uttryckt i millisekunder |
| **De 5 främsta rapporterna efter genomsnittlig rapportbearbetningstid** | * De fem rapporterna med den längsta genomsnittliga rapportbearbetningstiden, uttryckt i millisekunder |
| **Varaktighet per timma** | * Datahämtning jämfört med tiden för bearbetning och återgivning, uppdelat i entimmasbucketar, utryckt i lokal tid |
| **Resultat per timma** | * Lyckade och misslyckade åtgärder och minnesförbrukning, uppdelade i timbucketar, rapportede i lokal tid |
|  |  |

#### <a name="dataflows-tab"></a>Fliken Dataflöden

Fliken **Dataflöden** innehåller detaljerade uppdateringsmätvärden för dataflöden i dina kapaciteter.

![Fliken Dataflöden](media/service-admin-premium-monitor-capacity/dataflows-tab.png)

Fliken **Dataflöden** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Uppdatera** | * Totalt: Totalt antal uppdateringar för varje dataflöde<br> * Tillförlitlighet: Procentandelen uppdateringar som har slutförts för respektive dataflöde<br> * Genomsnittlig väntetid: Den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och starten av en uppdatering av dataflödet<br> * Maximal väntetid: Maximal väntetid för dataflödet, mätt i minuter <br> * Genomsnittlig varaktighet: Genomsnittlig varaktighet för uppdatering för dataflödet, mätt i minuter<br> * Maximal varaktighet: Varaktigheten för den långvarigaste uppdateringen av dataflödet, mätt i minuter |
| **De 5 främsta dataflödena efter genomsnittlig uppdateringsvaraktighet** | * De fem dataflöden med den längsta genomsnittliga uppdateringsvaraktigheten, mätt i minuter |
| **De 5 främsta dataflödena efter genomsnittlig väntetid** | * De fem dataflödena med den längsta genomsnittliga uppdateringsväntetiden, mätt i minuter |
| **Genomsnittlig uppdateringsväntetid uppdelad i timmar** | * Den genomsnittliga uppdateringsväntetiden, uppdelad i timbucketar, rapporterad i lokal tid. Många toppar med långa uppdateringsväntetider tyder på att kapaciteten körs för hårt. |
| **Antal uppdateringar och minnesförbrukning per timma** | * Lyckade och misslyckade åtgärder och minnesförbrukning, uppdelade i timbucketar, rapportede i lokal tid |
|  |  |

#### <a name="resource-consumption-tab"></a>Fliken Resursförbrukning

Fliken **Resursförbrukning** visar CPU-användning och minnesförbrukning för alla kapaciteter och arbetsbelastningar.

![Fliken Resursförbrukning](media/service-admin-premium-monitor-capacity/resource-consumption-tab.png)

Fliken **Resursförbrukning** innehåller följande mätvärden.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **CPU-förbrukning** | * Antalet gånger som CPU har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa buckets |
| **Minnesförbrukning** | * Minnesförbrukning under de senaste sju dagarna, uppdelad i bucketar på tre minuter |
|  |  |

#### <a name="ids-and-info-tab"></a>Fliken ID:n och info

Fliken **ID:n and info** innehåller namn, ID:n och ägare för kapaciteter, arbetsytor och arbetsbelastningar.

![Fliken ID:n och info](media/service-admin-premium-monitor-capacity/info-tab.png)

## <a name="monitor-power-bi-embedded-capacity"></a>Övervaka Power BI Embedded-kapacitet

Du kan också använda appen Power BI Premium Capacity Metrics för att övervaka *A SKU*-kapaciteter i Power BI Embedded. De kapaciteterna visas i rapporten så länge du är administratör för kapaciteten. Uppdatering av rapporten misslyckas dock såvida inte du ger vissa behörigheter till Power BI för dina A-SKU:

1. Öppna kapaciteten i Azure Portal.

1. Klicka på **Åtkomstkontroll (IAM)**, och Lägg till ”Power BI Premium”-appen till läsarrollen. Om det inte går att hitta appen genom att ange namnet kan du också lägga till den med hjälp av dess klient-ID: cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Behörigheter för Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Du kan övervaka kapacitetsförbrukningen för Power BI Embedded i appen eller Azure Portal, men inte i Power BI-administratörsportalen.

## <a name="basic-monitoring-in-the-admin-portal"></a>Grundläggande övervakning i adminportalen

Området **Kapacitetsinställningar** i adminportalen innehåller fyra mätare som anger belastningen på och de resurser som använts av din kapacitet under de senaste sju dagarna. Dessa fyra paneler har tidsfönster på en timme som anger hur många timmar under de senaste sju dagarna då motsvarande mått översteg 80 %. Det här måttet anger en potentiell försämring av slutanvändarens upplevelse.

![Användning under 7 dagar](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Mått** | **Beskrivning** |
| --- | --- |
| Processor |Antalet gånger processorn överskridit 80 % användning. |
| Minnesförslöing |Representerar minnesbelastningen på dina serverkärnor. Mer specifikt är detta ett mått på hur många gånger datauppsättningar avlägsnas från minnet på grund av minnesbelastning från användningen av flera datauppsättningar. |
| Minnesanvändning |Genomsnittlig minnesanvändning, representerat i gigabyte (GB). |
| DQ/s | Antalet gånger som Direct Query och Live-anslutningar överskridit 80 % av gränsvärdet. <br> * Vi begränsar det totala antalet DirectQuery- och Live-anslutningsfrågor per sekund.* Gänserna är 30/s för P1, 60/s för P2 och 120/s för P3. * Antalet frågor för Direct Query och Live-anslutningar räknas in mot ovanstående begränsning. Om du till exempel har 15 DirectQueries och 15 Live-anslutningar på en sekund når du begränsningen.<br>* Detta gäller lika för både lokala anslutningar och molnanslutningar. |
|  |  |

Måtten återspeglar användningen under den senaste veckan.  Om du vill visa en mer detaljerad vy över måtten kan du göra det genom att klicka på någon av sammanfattningspanelerna.  När du gör det öppnas detaljerade diagram för varje mått för din Premium-kapacitet. Följande diagram visar information om CPU-mått.

![Detaljerat användningsdiagram – processor](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Dessa diagram visar timbaserade sammanfattningar för den senaste veckan och kan hjälpa dig att isolera tidpunkter med specifika prestandarelaterade händelser i din Premium-kapacitet.

Du kan också exportera underliggande data för valfria mätvärdena till en CSV-fil.  Den här exporten ger detaljerad information i 3-minutersintervall för varje dag den senaste veckan.

## <a name="next-steps"></a>Nästa steg

Nu när du vet hur du övervakar Power BI Premium-kapacitet kan du lära dig mer om hur du optimerar kapaciteter.

> [!div class="nextstepaction"]
> [Resurshantering och -optimering av Power BI Premium-kapacitet](service-premium-understand-how-it-works.md)
