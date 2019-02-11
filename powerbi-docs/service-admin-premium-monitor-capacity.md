---
title: Övervaka Power BI Premium-kapaciteter med appen Premium Capacity Metrics.
description: Använd Power BI-administratörsportalen och appen Power BI Premium Capacity Metrics
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: c4e919de95c86051257ddc38b65c4dfda78dfc03
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794619"
---
# <a name="monitor-premium-capacities-with-the-app"></a>Övervaka Premium-funktioner med appen

Övervakning av dina kapaciteter är viktigt för att fatta välgrundade beslut om hur du bäst använder dina Premium-kapacitetsresurser. Du kan övervaka kapacitet med administratörsportalen eller med appen **Power BI Premium Capacity Metrics**. I den här artikeln beskrivs appen Premium Capacity Metrics. Appen ger den mest djupgående informationen om hur kapaciteterna fungerar. För en översikt på högre nivå över genomsnittliga användningsmått de senaste sju dagarna kan du använda administratörsportalen. Mer information om övervakning i portalen finns i [Övervaka Premium-kapaciteter i administratörsportalen](service-admin-premium-monitor-portal.md).

Appen uppdateras regelbundet med nya funktioner. Se till att du kör den senaste versionen.
**Den senaste versionen av appen är 1.10.1.1 (5 februari 2019)**.   
Om du redan har en tidigare version av appen installerad är det bäst att ta bort den från dina appar och sedan trycka på CTRL+F5 för att uppdatera. 

## <a name="install-the-app"></a>Installera appen

Du kan gå direkt till [Premium Capacity Metrics-appen](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) eller installera den precis som andra appar i Power BI.


1. I Power BI klickar du på **Appar**.   
    ![Gå till Appar](media/service-admin-premium-monitor-capacity/apps.png)

2. Till höger klickar du på **Hämta appar**.
3. I kategorin **Appar** söker du efter **Power BI Premium Capacity Metrics-appen**.
4. Prenumerera för att installera appen.

Ha tålamod. Det tar några minuter att installera och uppdatera mått. Om appen visar tomma mått trycker du på F5 för att uppdatera webbläsaren.


## <a name="get-app-refresh-history"></a>Hämta uppdateringshistorik för appen

Om du vill kontrollera den senaste tiden som Premium Capacity Metrics-appen uppdaterades klickar du på **Inställningar** > **Datauppsättningar** > **Power BI Premium Capacity Metrics** > **Uppdateringshistorik**. 

![Uppdateringshistorik i Inställningar](media/settings-refresh-history.png)

Den senaste uppdateringen visas. Du kan också klicka på **Uppdateringshistorik** för att se schemalagda och uppdateringar och på begäran-uppdateringar.

![Senaste uppdatering](media/service-admin-premium-monitor-capacity/settings-last-refresh.png)

## <a name="monitor-a-capacity-with-the-app"></a>Övervaka en kapacitet med appen

Nu när du har installerat appen kan du se mått för kapaciteterna i din organisation. Låt oss ta en titt på några av de viktigaste måtten som är tillgängliga.

### <a name="metrics-dashboard"></a>Instrumentpanelen med mätvärden

När du öppnar appen visas först en instrumentpanel med en sammanfattning av alla kapaciteter som du har administratörsrättigheter till.

![Instrumentpanelen med mätvärden för app](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Instrumentpanelen innehåller följande mått:

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Systemöversikt** |  Programmets version<br>  Antal kapaciteter du är administratör för<br>  Antal arbetsytor i dina kapaciteter som rapporterar mått<br>  Genomsnittlig minnesförbrukning i GB under de senaste sju dagarna<br>  Maximal minnesförbrukning i GB under de senaste sju dagarna<br>  Lokal tid då den maximala minnesförbrukningen inträffade<br>  Antal gånger som CPU har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa bucketar<br>  De flesta gånger CPU överskred 80 % under de senaste sju dagarna, uppdelat på en timme långa bucketar<br>  Lokal tid då CPU överskred 80 % flest gånger under en timme |
| **Översikt över datauppsättning** |  Totalt antal datauppsättningar för alla arbetsytor i dina kapaciteter<br>  Antal gånger som Direct Query/Live-anslutningar har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa bucketar<br>  De flesta gånger Direct Query/Live-anslutningar har överskridit 80 % under de senaste sju dagarna, uppdelat på en timme långa bucketar<br>  Lokal tid då Direct Query/Live-anslutningar överskred 80 % flest gånger i timmen<br>  Totalt antal uppdateringar under de senaste sju dagarna<br>  Genomsnittlig väntetid för uppdatering – den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och uppdateringens start<br>  Genomsnittlig uppdateringstid – den tid, mätt i minuter, det tar att slutföra uppdateringen<br>  Totalt antal frågor som körts under de senaste sju dagarna<br>  Genomsnittlig väntetid för fråga – den tid, mätt i millisekunder, som en fråga väntade på systemresurser innan körningen startades<br>  Genomsnittlig frågevaraktighet – den tid, mätt i millisekunder, det tar att slutföra frågan<br>  Totalt antal modeller som tagits bort på grund av minnestryck<br>  Genomsnittlig storlek på datauppsättningar <br>  Genomsnittligt antal datauppsättningar som läses in i minnet |
| **Översikt över dataflöde** |  Totalt antal dataflöden för alla arbetsytor i dina kapaciteter<br>  Totalt antal uppdateringar under de senaste sju dagarna<br>  Genomsnittlig väntetid för uppdatering – den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och uppdateringens start<br>  Genomsnittlig uppdateringstid – den tid, mätt i minuter, det tar att slutföra uppdateringen |
| **Översikt över sidnumrerade rapporter** |  Totalt antal sidnumrerade rapporter för alla arbetsytor i dina kapaciteter<br>  Totalt antal gånger som alla rapporter har setts av användare<br>  Totalt antal rader med data i alla rapporter<br>  Total tid det tar för alla faser (datahämtning, bearbetning och återgivning) för alla rapporter, i millisekunder |
|  |  |

### <a name="metrics-report"></a>Måttrapport

Gå till den underliggande rapporten genom att klicka på instrumentpanelen. Längst ned i rapporten finns det fem flikar:

* [**Datauppsättningar**](#datasets) – Innehåller detaljerade mätvärden om hälsotillståndet för Power BI-datamängderna i dina kapaciteter.

* [**Sidnumrerade rapporter**](#paginated-reports) – Innehåller detaljerade mätvärden om hälsotillståndet för sidnumrerade rapporter i dina kapaciteter.

* [**Dataflöden**](#dataflows) – Innehåller detaljerade uppdateringsmätvärden för dataflöden i dina kapaciteter.

* [**Resursförbrukning**](#resource-consumption) – Innehåller mätvärden för den totala kapaciteten, inklusive minne och hög CPU-användning.

* [**ID:n och info**](#ids-and-info) – Namn, ID:n och ägare för kapaciteter, arbetsytor och arbetsbelastningar.

Du kan filtrera mått efter kapacitet och datumintervall på varje flik. Om inga filter har markerats använder rapporten standardinställningarna för att visa den senaste veckans mått för alla kapaciteter som rapporterar mått. 

#### <a name="datasets"></a>Datauppsättningar

Navigera till olika områden genom att använda knapparna överst på fliken **Datauppsättningar**: **Uppdateringar**, **Frågevaraktigheter**, **Frågeväntan** och **Datauppsättningar**.

##### <a name="refreshes-area"></a>Området Uppdaterar

Området **Uppdateringar** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Uppdateringstillförlitlighet** |  Totalt antal: Totalt antal uppdateringar för varje datauppsättning<br>  Tillförlitlighet: Procentandelen uppdateringar som har slutförts för varje datauppsättning<br>  Genomsnittlig väntetid: Den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och starten av en uppdatering av datauppsättningen<br>  Maximal väntetid: Maximal väntetid för datauppsättningen, mätt i minuter <br>  Genomsnittlig varaktighet: Genomsnittlig varaktighet för uppdatering för datauppsättningen, mätt i minuter<br>  Maximal varaktighet: Varaktigheten för den långvarigaste uppdateringen av datauppsättningen, mätt i minuter |
| **De 5 främsta datauppsättningarna efter genomsnittlig uppdateringsvaraktighet** |  De fem datauppsättningarna med den längsta genomsnittliga uppdateringsvaraktigheten, mätt i minuter |
| **De 5 främsta datauppsättningarna efter genomsnittlig väntetid** |  De fem datauppsättningarna med den längsta genomsnittliga uppdateringsväntetiden, mätt i minuter |
| **Genomsnittlig uppdateringsväntetid uppdelad i timmar** |  Den genomsnittliga uppdateringsväntetiden, uppdelad i timbucketar, rapporterad i lokal tid. Många toppar med långa uppdateringsväntetider tyder på att kapaciteten körs för hårt. |
| **Antal uppdateringar och minnesförbrukning per timma** |  Lyckade och misslyckade åtgärder och minnesförbrukning, uppdelade i timbucketar, rapportede i lokal tid |
|  |  |

##### <a name="query-durations-area"></a>Frågevaraktighetsområde

Området **Frågevaraktighet** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Frågevaraktighet** |  Data i det här avsnittet är indelade i datauppsättningar, arbetsytor och timbucketar under de senaste sju dagarna<br>  Totalt: Det totala antal frågor som körs för datauppsättningen<br>  Genomsnitt: Den genomsnittliga frågevaraktigheten för datauppsättningen, mätt i millisekunder<br>  Max: Varaktigheten för den långvarigaste frågan i datauppsättningen, mätt i millisekunder|
| **Frågevaraktighetsfördelning** |  Frågevaraktighetens histogram bucketeras efter frågevaraktighet (i millisekunder) i följande kategorier: intervall på < = 30 ms, 30-100 ms, 100-300 ms, 300 ms-1 sek, 1-3 sek, 3-10 sek, 10-30 sek och > 30 sek. Lång frågevaraktighet och långa väntetider är en tydlig indikation på kapaciteten utsätts för mycket hög belastning. Det kan också innebära att en enskild datauppsättning orsakar problem och ytterligare utredning krävs. |
| **De 5 främsta datauppsättningarna efter genomsnittlig varaktighet** |  De fem datauppsättningarna med den längsta genomsnittliga frågevaraktigheten, mätt i millisekunder |
| **Direct Query/Live-anslutningar (> 80 % utnyttjande)** |  De tider som en direktfråga eller live-anslutning har överskridit 80 % CPU-belastning, uppdelat i timbucketar, rapporterat i lokal tid |
| **Frågevaraktighetsfördelning per timma** |  Antal frågor och genomsnittlig varaktighet (i millisekunder) jämfört med minnesanvändningen i GB, uppdelat i timbucketar uttryckta i lokal tid |
|  |  |

##### <a name="query-waits-area"></a>Frågeväntansområde

Området **Frågeväntan** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Fråga väntetider** |  Data i det här avsnittet är indelade i datauppsättningar, arbetsytor och timbucketar under de senaste sju dagarna<br>  Totalt: Det totala antal frågor som körs för datauppsättningen<br>  Antal väntande: Det antal frågor i den datauppsättning som väntade på systemresurser innan körningen startades <br>  Genomsnitt: Den genomsnittliga frågeväntetiden för datauppsättningen, mätt i millisekunder<br>  Max: Varaktigheten för den längst väntande frågan i datauppsättningen, mätt i millisekunder|
| **Väntetidsfördelning** |  Frågevaraktighetens histogram bucketeras efter frågevaraktigheter (i millisekunder) i följande kategorier: intervall på <= 50 ms , 50-100 ms , 100-200 ms , 200-400 ms 400 ms-1 sek, 1-5 sek och > 5 sek |
| **De 5 främsta datauppsättningarna efter genomsnittlig väntetid** |  De fem datauppsättningarna med den längsta genomsnittliga väntetiden för att börja köra en fråga, mätt i millisekunder |
| **Antal väntande frågor och väntetid per timma** |  Antal väntande frågor och genomsnittlig väntetid (i millisekunder) jämfört med minnesanvändningen i GB, uppdelat i timbucketar uttryckta i lokal tid |
|  |  |

##### <a name="datasets-area"></a>Området Datamängder

Området **Datauppsättningar** innehåller följande mått.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Antal borttagna datauppsättningar** |  Totalt: Det totala antalet *avlägsnade* datauppsättningar för respektive kapacitet. När en kapacitet drabbas av minnesbelastning avlägsnar noden en eller flera datauppsättningar från minnet. Datamängder som är inaktiva (utan frågor/uppdateringsåtgärder som körs för tillfället) avlägsnas först. Avlägsnandeordern baseras sedan på ett mått på ”minst nyligen använd” (LRU, Least Recently Used).|
| **Antal borttagna datauppsättningar och minnesförbrukning per timma** |  Borttagna datauppsättningar jämfört med minnesförbrukning i GB, uppdelat i timbucketar, uttryckt i lokal tid |
| **Inlästa datauppsättningar per timme** |  Antal datauppsättningar som läses in i minnet jämfört med minnesförbrukning i GB, uppdelat i timbucketar, uttryckt i lokal tid |
| **Procent för använt minne** |  Det totala antalet aktiva datauppsättningar i minnet som procent av det totala minnet. Delta mellan aktiva och alla definierade datauppsättningar som kan avlägsnas. Visas per timme, för de sju föregående dagarna. |
| **Datastorlekar**  |  Maxstorlek: Maxstorleken för datauppsättningen i MB för perioden som visas |
|  |  |

#### <a name="paginated-reports"></a>Sidnumrerade rapporter

Fliken **Sidnumrerade rapporter** innehåller detaljerade mätvärden om hälsotillståndet för sidnumrerade rapporter i dina kapaciteter.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Total användning** |  Totalt antal visningar: Det antal gånger som rapporten har setts av användare<br>  Radantal: Antalet rader med data i rapporten<br>  Hämtning (medelvärde): Den genomsnittliga tid det tar att hämta data för rapporten, uttryckt i millisekunder. Långa varaktigheter kan indikera långsamma frågor eller andra problem med datakällan. <br>  Bearbetning (medelvärde): Den genomsnittliga tid det tar att bearbeta data för en rapport, uttryckt i millisekunder<br> Återgivning (medelvärde): Den genomsnittliga tid det tar att återge en rapport i webbläsaren, uttryckt i millisekunder<br>  Total tid: Den tid det tar för alla faser i en rapport, uttryckt i millisekunder|
| **De 5 främsta rapporterna efter genomsnittlig datahämtningstid** |  De fem rapporterna med den längsta genomsnittliga datahämtningstiden, uttryckt i millisekunder |
| **De 5 främsta rapporterna efter genomsnittlig rapportbearbetningstid** |  De fem rapporterna med den längsta genomsnittliga rapportbearbetningstiden, uttryckt i millisekunder |
| **Varaktighet per timma** |  Datahämtning jämfört med tiden för bearbetning och återgivning, uppdelat i entimmasbucketar, utryckt i lokal tid |
| **Resultat per timma** |  Lyckade och misslyckade åtgärder och minnesförbrukning, uppdelade i timbucketar, rapportede i lokal tid |
|  |  |

#### <a name="dataflows"></a>Dataflöden

Fliken **Dataflöden** innehåller detaljerade uppdateringsmätvärden för dataflöden i dina kapaciteter.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **Uppdatera** |  Totalt: Totalt antal uppdateringar för varje dataflöde<br>  Tillförlitlighet: Procentandelen uppdateringar som har slutförts för respektive dataflöde<br>  Genomsnittlig väntetid: Den genomsnittliga fördröjningen, mätt i minuter, mellan den schemalagda tiden och starten av en uppdatering av dataflödet<br>  Maximal väntetid: Maximal väntetid för dataflödet, mätt i minuter <br>  Genomsnittlig varaktighet: Genomsnittlig varaktighet för uppdatering för dataflödet, mätt i minuter<br>  Maximal varaktighet: Varaktigheten för den långvarigaste uppdateringen av dataflödet, mätt i minuter |
| **De 5 främsta dataflödena efter genomsnittlig uppdateringsvaraktighet** |  De fem dataflöden med den längsta genomsnittliga uppdateringsvaraktigheten, mätt i minuter |
| **De 5 främsta dataflödena efter genomsnittlig väntetid** |  De fem dataflödena med den längsta genomsnittliga uppdateringsväntetiden, mätt i minuter |
| **Genomsnittlig uppdateringsväntetid uppdelad i timmar** |  Den genomsnittliga uppdateringsväntetiden, uppdelad i timbucketar, rapporterad i lokal tid. Många toppar med långa uppdateringsväntetider tyder på att kapaciteten körs för hårt. |
| **Antal uppdateringar och minnesförbrukning per timma** |  Lyckade och misslyckade åtgärder och minnesförbrukning, uppdelade i timbucketar, rapportede i lokal tid |
|  |  |

#### <a name="resource-consumption"></a>Resursförbrukning

Fliken **Resursförbrukning** visar CPU-användning och minnesförbrukning för alla kapaciteter och arbetsbelastningar.

| **Rapportavsnitt** | **Mått** |
| --- | --- |
| **CPU-förbrukning** |  Förbrukning av arbetsbelastning som procentandel av total CPU-kapacitet. Visas per timme, för de sju föregående dagarna. |
| **Minnesförbrukning** |  Minnesförbrukning i GB per arbetsbelastning (heldragna linjer), med arbetsbelastningsbelastningar (streckad linje) ovanpå. Visas per timme, för de sju föregående dagarna. |
|  |  |

#### <a name="ids-and-info"></a>ID:n och info

Fliken **ID:n and info** innehåller namn, ID:n och ägare för kapaciteter, arbetsytor och arbetsbelastningar.


## <a name="monitor-power-bi-embedded-capacity"></a>Övervaka Power BI Embedded-kapacitet

Du kan använda appen Power BI Premium Capacity Metrics för att övervaka *A SKU*-kapaciteter i Power BI Embedded. De kapaciteterna visas i rapporten så länge du är administratör för kapaciteten. Uppdatering av rapporten misslyckas dock såvida inte du ger vissa behörigheter till Power BI för dina A-SKU:

1. Öppna kapaciteten i Azure Portal.

1. Klicka på **Åtkomstkontroll (IAM)**, och Lägg till ”Power BI Premium”-appen till läsarrollen. Om det inte går att hitta appen genom att ange namnet kan du också lägga till den med hjälp av dess klient-ID: cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Behörigheter för Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Du kan övervaka kapacitetsförbrukningen för Power BI Embedded i appen eller Azure Portal, men inte i Power BI-administratörsportalen.


## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Resurshantering och -optimering av Power BI Premium-kapacitet](service-premium-understand-how-it-works.md)
