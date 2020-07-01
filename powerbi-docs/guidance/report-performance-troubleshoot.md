---
title: Felsöka rapportprestanda i Power BI
description: Felsökningsguide för diagnostisering av långsamma rapportprestanda i Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: 2c7ba0ce8e41281e89e2bb31f9bc6db751b95dad
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485977"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Felsöka rapportprestanda i Power BI

Den här artikeln innehåller vägledning som gör att utvecklare och administratörer kan felsöka långsamma rapportprestanda. Den gäller för Power BI-rapporter och även sidnumrerade Power BI-rapporter.

Långsamma rapporter kan identifieras av rapportanvändare som upplever att rapporter läses in långsamt eller uppdateras långsamt när de använder utsnitt eller andra funktioner. När rapporter hanteras i en Premium-kapacitet kan långsamma rapporter även identifieras genom övervakning av [Power BI Premium-måttappen](../admin/service-admin-premium-monitor-capacity.md). Den här appen hjälper dig att övervaka hälsan och kapaciteten hos din Power BI Premium-prenumeration.

## <a name="follow-flowchart-steps"></a>Följ stegen i flödesdiagrammet

Använd följande flödesdiagram för att ta reda på orsaken till långsamma prestanda och fastställa vilka åtgärder som ska vidtas.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Bilden visar flödesdiagrammet, som beskrivs fullständigt i artikeltexten." border="true":::

Det finns sex slutnoder i flödesdiagrammet som var och en beskriver åtgärder som ska vidtas:

|Slutnod|Åtgärd(er)|
|---------|---------|
|![Flödesdiagrammets slutnod 1.](media/common/icon-01-red-30x30.png)|Hantera kapacitet<br />Skala kapacitet |
|![Flödesdiagrammets slutnod 2.](media/common/icon-02-red-30x30.png)|Undersök kapacitetsaktivitet vid normal rapportanvändning|
|![Flödesdiagrammets slutnod 3.](media/common/icon-03-red-30x30.png)|Arkitekturändring<br />Överväg Azure Analysis Services<br />Kontrollera lokal gateway|
|![Flödesdiagrammets slutnod 4.](media/common/icon-04-red-30x30.png)|Överväg Azure Analysis Services<br />Överväg Power BI Premium|
|![Flödesdiagrammets slutnod 5.](media/common/icon-05-red-30x30.png)|Använda prestandaanalyseraren i Power BI Desktop<br />Optimera rapport, modell eller DAX|
|![Flödesdiagrammets slutnod 6.](media/common/icon-06-red-30x30.png)|Skapa supportbegäran|

## <a name="take-action"></a>Vidta åtgärd

Det första övervägandet är att ta reda på om den långsamma rapporten hanteras i en Premium-kapacitet.

### <a name="premium-capacity"></a>Premiumkapacitet

När rapporten hanteras i en Premium-kapacitet använder du appen **Power BI Premium-måttappen** för att fastställa om kapaciteten för rapporthantering överskrider kapacitetsresurserna. Det är fallet för CPU:n när den ofta överskrider 80 %. För minnet sker det [måttet för aktivt minne](../admin/service-premium-metrics-app.md#the-active-memory-metric) överskrider 50. När resurser belastas högt kan det vara dags att [hantera eller skala kapaciteten](../admin/service-admin-premium-manage.md) (flödesdiagrammets slutnod 1). När det finns tillräckligt med resurser bör du undersöka kapacitetsaktiviteten vid normal rapportanvändning (flödesdiagrammets slutnod 2).

### <a name="shared-capacity"></a>Delad kapacitet

När rapporten hanteras i en delad kapacitet går det inte att övervaka kapacitetshälsan. Du måste då använda en annan undersökningsmetod.

Kontrollera först om långsamma prestanda inträffar vid vissa tider under dagen eller månaden. Om det gör det – och om många användare öppnar rapporten vid dessa tidpunkter – bör du överväga två alternativ:

- Öka frågedataflödet genom att migrera datamängden till [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) eller en Premium-kapacitet (flödesdiagrammets slutnod 4).
- Använd [Prestandaanalys](../create-reports/desktop-performance-analyzer.md) i Power BI Desktop för att ta reda på hur dina olika rapportelement, däribland visuella objekt och DAX-formler, presterar. Det är särskilt användbart att fastställa huruvida det är frågan eller den visuella renderingen som orsakar prestandaproblem (flödesdiagrammets slutnod 5).

Om du kommer fram till att det inte finns något tidsmönster kan du därefter ta reda på om långsamma prestanda är isolerade till ett specifik geografiskt område eller en region. Om så är fallet är det troligt att datakällan är avlägsen och att nätverkskommunikationen är långsam. I det fallet bör du överväga följande:

- Ändra arkitekturen med hjälp av [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (flödesdiagrammets slutnod 3).
- Optimera [prestanda för lokal datagateway](/data-integration/gateway/service-gateway-performance) (flödesdiagrammets slutnod 3).

Om du slutligen kommer fram till att det inte finns något tidsmönster _och_ att långsamma prestanda inträffar i alla regioner bör du undersöka om långsamma prestanda inträffar på specifika enheter, klienter eller webbläsare. Om så inte är fallet använder du [Prestandaanalys](../create-reports/desktop-performance-analyzer.md) i Power BI Desktop enligt beskrivningen ovan för att optimera rapporten eller modellen (flödesdiagrammets slutnod 5).

När du fastställer att specifika enheter, klienter eller webbläsare bidrar till långsamma prestanda rekommenderar vi att du skapar en supportbegäran via [Power BI-supportsidan](https://powerbi.microsoft.com/support/) (flödesdiagrammets slutnod 6).

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Power BI-vägledning](index.yml)
- [Övervaka rapportprestanda](monitor-report-performance.md)
- [Prestandaanalys](../create-reports/desktop-performance-analyzer.md)
- Whitepaper: [Planera en företagsdistribution för Power BI](https://go.microsoft.com/fwlink/?linkid=2057861)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
