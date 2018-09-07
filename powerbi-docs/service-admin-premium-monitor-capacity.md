---
title: Övervaka Power BI Premium-kapaciteter i din organisation
description: Använd Power BI-administratörsportalen och appen Power BI Premium Capacity Metrics
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/29/2018
LocalizationGroup: Premium
ms.openlocfilehash: 8e19bc596bef3862dca79ac92ffbd74954a9c756
ms.sourcegitcommit: 6be2c54f2703f307457360baef32aee16f338067
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43300171"
---
# <a name="monitor-power-bi-premium-capacities-in-your-organization"></a>Övervaka Power BI Premium-kapaciteter i din organisation

Den här artikeln innehåller en översikt över övervakning av mått för dina Power BI Premium-kapaciteter. Genom att övervaka kapacitetsförbrukningen kan du hantera din kapacitet på ett genomtänkt sätt. 

Du kan övervaka kapaciteten med appen Power BI Premium Capacity Metrics eller i administrationsportalen. Vi rekommenderar appen, eftersom det ger mycket mer detaljerad information, men den här artikeln beskriver båda alternativen.

## <a name="install-the-premium-capacity-metrics-app"></a>Installera appen Premium Capacity Metrics

Du kan gå direkt till [Premium Capacity Metrics-appen](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) eller installera den precis som andra appar i Power BI.

> [!IMPORTANT]
> Du måste vara kapacitetsadministratör för minst en kapacitet för att installera och använda den här appen. Det räcker inte att vara en Power BI-administratör. 

1. I Power BI klickar du på **Appar**.

    ![Gå till Appar](media/service-admin-premium-monitor-capacity/apps.png)

2. Till höger klickar du på **Hämta appar**.

3. I kategorin **Appar** söker du efter **Power BI Premium Capacity Metrics-appen**.

4. Prenumerera för att installera appen.

Nu när du har installerat appen kan du se mått som gäller kapaciteterna i din organisation. Låt oss ta en titt på några av de viktigaste måtten som är tillgängliga.

## <a name="use-the-metrics-app"></a>Använda måttappen 
När du öppnar appen visas först en instrumentpanel med en sammanfattning av alla kapaciteter som du har administratörsrättigheter till.

![Rapportöversikt över Premium](media/service-admin-premium-monitor-capacity/app-dashboard.png)

### <a name="filtering"></a>Filtrering

På fliken **Filter tillämpas på alla sidor** kan du välja en kapacitet, en datauppsättning och/eller ett datumintervall under de senaste sju dagarna. De här filtren tillämpar urvalet på alla relevanta sidor och paneler i den här rapporten. Om inget är markerat använder rapporten standardinställningarna för att visa den senaste veckan mått på varje kapacitet som du äger.

![Rapportöversikt över Premium](media/service-admin-premium-monitor-capacity/premium-report-overview.png)

### <a name="summary-tab"></a>Fliken Sammanfattning

Fliken **Sammanfattning** visar en vy av kapaciteten baserat på entiteter, system och datauppsättningar.

![Filter som gäller för alla sidor](media/service-admin-premium-monitor-capacity/premium-summary-report.png)

| **Område** | **Mått** |
| --- | --- |
| **Entiteter** | * Antalet kapaciteter som du äger<br> * Det exakta antalet datauppsättningar i din kapacitet<br> * Det exakta antalet arbetsytor i din kapacitet |
| **System** | * Den genomsnittliga minnesanvändningen i GB under de senaste sju dagarna<br> * Högsta minnesförbrukning i GB under de senaste sju dagarna och den lokala tid då det hände<br> * Antalet gånger som CPU har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa buckets<br> * De flesta gånger CPU överskred 80 % under de senaste sju dagarna, uppdelat på en timme långa buckets och den lokala tid då det hände<br> * Antalet gånger som DirectQuery- och Live-anslutningar har överskridit 80 % av tröskelvärdena under de senaste sju dagarna, uppdelat på tre minuter långa buckets<br> * De flesta gånger DirectQuery- och Live-anslutningar har överskridit 80 % under de senaste sju dagarna, uppdelat på en timme långa buckets och den lokala tid då det hände |
| **Arbetsbelastningar för datauppsättningar** | * Totalt antal uppdateringar under de senaste sju dagarna<br> * Totalt antal lyckade uppdateringar under de senaste sju dagarna<br> * Totalt antal misslyckade uppdateringar under de senaste sju dagarna<br> * Totalt antal misslyckade uppdateringar på grund av minnesbrist<br> * Genomsnittlig uppdateringstid mätt i minuter, den tid det tar att slutföra åtgärden<br> * Genomsnittlig väntetid för uppdatering mätt i minuter, genomsnittlig fördröjning mellan den schemalagda tiden och åtgärdsstart<br> * Totalt antal frågor som körts under de senaste sju dagarna<br> * Totalt antal lyckade frågor under de senaste sju dagarna<br> * Totalt antal misslyckade frågor under de senaste sju dagarna<br> * Genomsnittlig frågetid mätt i minuter, den tid det tar att slutföra åtgärden<br> * Totalt antal modeller som tagits bort på grund av minnestryck |
|  |  |

### <a name="refreshes-tab"></a>Fliken Uppdaterar

Fliken **Uppdaterar** anger slutförda uppdateringar, lyckade mätningar, genomsnittlig/maximal väntetid för uppdaterings och genomsnittlig/maximal uppdateringstid per datauppsättning under de senaste sju dagarna. De två diagrammen längst ner visar uppdateringarna jämfört med minnesförbrukning i GB och genomsnittliga väntetider uppdelade i en timme långa buckets, rapporterat i lokal tid. De översta stapeldiagrammen anger de fem främsta datauppsättningarna efter den totala maximala tid som det tog att uppdatera datauppsättningen (uppdateringstid) och maximal väntetid för uppdateringen. Om det förekommer många toppar för väntan på uppdatering tyder det på att kapaciteten körs för hårt.

![Uppdateringsrapport för Premium](media/service-admin-premium-monitor-capacity/premium-refresh-report.png)

### <a name="datasets-tab"></a>Fliken Datauppsättningar

Fliken **Datauppsättningar** visar slutförda datauppsättningar som du vill ta bort på grund av minnestryck per timme.

![Datauppsättningsrapport för Premium](media/service-admin-premium-monitor-capacity/premium-datasets-report.png)

### <a name="system-tab"></a>Fliken System

Fliken **System** visar hög CPU-användning (antalet gånger då 80% utnyttjande har överskridits), hög användning av DirectQuery- och Live-anslutningar och minnesförbrukning.

![Systemrapport för Premium](media/service-admin-premium-monitor-capacity/premium-system-report.png)

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
