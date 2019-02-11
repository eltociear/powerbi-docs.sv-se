---
title: Övervaka Power BI Premium-kapaciteter med hjälp av administratörsportalen
description: Använd Power BI-administratörsportalen för att övervaka dina Premium-kapaciteter.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794108"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Övervaka kapaciteter i administratörsportalen

I den här artikeln beskrivs hur du kan använda området Kapacitetsinställningen i administratörsportalen för att få en snabb överblick över kapacitetens prestanda.  För de mest djupgående måtten om din kapacitet är det bäst att använda appen [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md).

## <a name="capacity-metrics"></a>Kapacitetsmått

Området **Kapacitetsinställningar** i adminportalen innehåller fyra mätare som anger belastningen på och de resurser som använts av din kapacitet under de senaste sju dagarna. Dessa fyra paneler har tidsfönster på en timme som anger hur många timmar under de senaste sju dagarna då motsvarande mått översteg 80 %. Det här måttet anger en potentiell försämring av slutanvändarens upplevelse.

![Användning under 7 dagar](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Mått** | **Beskrivning** |
| --- | --- |
| Processor |Antalet gånger processorn överskridit 80 % användning. |
| Minnesförslöing |Representerar minnesbelastningen på dina serverkärnor. Mer specifikt är detta ett mått på hur många gånger datauppsättningar avlägsnas från minnet på grund av minnesbelastning från användningen av flera datauppsättningar. |
| Minnesanvändning |Genomsnittlig minnesanvändning, representerat i gigabyte (GB). |
| DQ/s | Antalet gånger som Direct Query och Live-anslutningar överskridit 80 % av gränsvärdet. <br>  Det totala antalet DirectQuery- och realtidsanslutningsfrågor per sekund är begränsat. Gränserna är 30/s för P1, 60/s för P2 och 120/s för P3.  Antalet frågor för Direct Query och Live-anslutningar räknas in mot ovanstående begränsning. Om du till exempel har 15 DirectQueries och 15 Live-anslutningar på en sekund når du begränsningen.<br> Detta gäller lika för både lokala anslutningar och molnanslutningar. |
|  |  |

Måtten återspeglar användningen under den senaste veckan.  Om du vill visa en mer detaljerad vy över måtten kan du göra det genom att klicka på någon av sammanfattningspanelerna.  När du gör det öppnas detaljerade diagram för varje mått för din Premium-kapacitet. Följande diagram visar information om CPU-mått.

![Detaljerat användningsdiagram – processor](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Dessa diagram visar timbaserade sammanfattningar för den senaste veckan och kan hjälpa dig att isolera tidpunkter med specifika prestandarelaterade händelser i din Premium-kapacitet.

Du kan också exportera underliggande data för valfria mätvärdena till en CSV-fil.  Den här exporten ger detaljerad information i 3-minutersintervall för varje dag den senaste veckan.

## <a name="next-steps"></a>Nästa steg

Nu när du vet hur du övervakar Power BI Premium-kapacitet kan du lära dig mer om hur du optimerar kapaciteter.

> [!div class="nextstepaction"]
> [Resurshantering och -optimering av Power BI Premium-kapacitet](service-premium-understand-how-it-works.md)
