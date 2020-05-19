---
title: Exempel på visuella objekt i Power BI
description: Den här artikeln innehåller exempel på visuella objekt i Power BI, t.ex. utsnitt, mer än 20 diagramtyper, WebGL, visuella R-objekt och skript.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132948"
---
# <a name="samples-of-power-bi-visuals"></a>Exempel på Power BI-visualiseringar

Du kan ladda ned, använda och ändra dessa visuella Power BI-objekt från GitHub. Dessa exempel illustrerar hur du kan hantera vanliga situationer när du bedriver utvecklingsarbete i Power BI.

## <a name="slicers"></a>Utsnitt

Ett utsnitt begränsar den del av datamängden som visas i andra visuella objekt i en rapport. Utsnitt är en av flera metoder som används för att filtrera data i Power BI.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Chiclet-utsnitt](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Visa bild- eller textknappar som fungerar som filter på arbetsytan för andra visuella objekt | [Tidslinje-utsnitt](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Datumintervallsväljare för grafik som filtrerar efter datum | [Utsnittsexempel](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Visar användningen av API:et för avancerad filtrering

## <a name="charts"></a>Diagram

Bli inspirerad med vårt galleri, med bl.a. stapeldiagram, cirkeldiagram, ordmoln och annat.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Aster-punktdiagram](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>En variant på ett vanligt ringdiagram som använder ett andra värde för att driva en svepvinkel | [Jämförande stapeldiagram](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Ett stapeldiagram med extra visuella element som ger ytterligare kontext, som är användbart vid målspårning | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>En grafisk metod som visar relationerna mellan data i en matris
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Punktritning](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Visa frekvensfördelning på ett snyggt sätt | [Dubbel KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Visualiserar effektivt två mått över tid, vilket visar deras trend på en gemensam tidslinje | [Förbättrat punktdiagram](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Förbättringar i det befintliga punktdiagrammet
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Tvingat diagram](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Tvinga layoutdiagram med en böjd linje, vilket är användbart när du vill visa anslutningar mellan entiteter | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Ett stapeldiagram som illustrerar ett projekts tidslinje eller ett schema med resurser | [Termisk tabellkarta](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Jämför data enkelt och intuitivt med färger i en tabell
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Histogramdiagram](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualiserar distributionen av data över ett kontinuerligt intervall eller en viss tidsperiod | [LineDot-diagram](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Ett animerat linjediagram med roliga animerade punkter som fångar publikens intresse med data | [Mekko-diagram](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>En blandning av ett 100 % stående stapeldiagram och 100 % liggande stapeldiagram kombinerat i en vy
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Multi-KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> En kraftfull visualisering av flera KPI: er med en nyckel-KPI tillsammans med flera miniatyrdiagram med stöddata | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>En kraftfull KPI-indikator med flera linjediagram och etiketter för aktuellt datum, värde och avvikelser. | [Power KPI-matris](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Övervaka balanserade styrkort och obegränsat antal mått och KPI:er i en komprimerad lättläst lista
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Pulsdiagram](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Det här linjediagrammet som är kommenterat med nyckelhändelser passar perfekt när du ska berätta en historia med data| [Polärdiagram](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Presenterar flera mått som ritats på en kategorisk axel, vilket är användbart när du ska jämföra attribut | [Sankey-diagram](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Flödesdiagram där bredden på serien är proportionell mot flödets mängd
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Stream-diagram](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Ett staplat ytdiagram med utjämnad interpolering, vilket ofta används för att visa värden över tid | [Soldiagram](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Ett ringdiagram med flera nivåer som effektivt visualiserar hierarkiska data| [Storm-diagram](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Jämför den relativa vikten för variabler mellan två grupper
 | <img src="media/samples/word-cloud.png" width="200">
 | [Ordmoln](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Skapa ett roligt visuellt objekt från frekvent text i dina data

## <a name="webgl"></a>WebGL

Med WebGL kan webbinnehåll använda ett API som baseras på OpenGL ES 2.0 i samband med 2D-och 3D-återgivning på en HTML-arbetsyta.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Världskarta](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Rita platser på en interaktiv 3D-karta

## <a name="r-visuals"></a>R-visualiseringar

Dessa exempel visar hur du kan dra nytta av de visuella R-objektens och R-skriptens analytiska och visuella kraft.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Association Rules](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Avslöja relationer mellan tillsynes orelaterade data med hjälp av if...then-instruktioner | [Klustring](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Sök efter liknande grupper i dina data med hjälp av K-means-algoritmer | [Klustring med extremvärden](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Hitta likhetsgrupper och extremvärden i dina data
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Korrelationsrityta](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Markera de mest korrelerade variablerna i en datatabell | [Beslutsträdsdiagram](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Ett schematiskt trädformat diagram som används för att fastställa statistisk sannolikhet med hjälp av rekursiv partitionering | [Prognosticering av TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Tidsserieprognoser för serier som har flera säsonger med hjäp av TBATS-modellen
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Prognosticering med ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Förutsäg framtida värden baserat på historiska data med ARIMA (Autoregressive Integrated Moving Avg) | [Trattritning](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Hitta extremvärden i dina data med hjälp av en trattritning | [Identifiering av extremvärden](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Hitta extremvärden i dina data med den lämligaste metoden och ritytan
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Spline-diagram](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Visualisera och förstå datastörningar | [Tidsseriefördelningsdiagram](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Förstå tidsseriekomponenter med "Säsongs- och trendnedbrytning med Loess" | [Prognostiseringsdiagram för tidsserier](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Använda en modell för exponentiell utjämning för att förutsäga framtida värden baserat på tidigare observerade värden

## <a name="next-steps"></a>Nästa steg

Om du vill testa att skapa visuella Power BI-objekt, kan du studera [-självstudien: Utveckla ett visuellt Power BI-objekt](custom-visual-develop-tutorial.md).
