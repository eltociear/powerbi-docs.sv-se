---
title: Lägg till färger till dina visuella Power BI-objekt
description: Den här artikeln beskriver hur du lägger till färger i visuella Power BI-objekt och hur du hanterar datapunkter för ett visuellt objekt med färg.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141154"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Lägg till färger till dina visuella Power BI-objekt

Den här artikeln beskriver hur du lägger till färger i dina visuella objekt och hur du hanterar datapunkter för ett visuellt färgobjekt.

`IVisualHost` exponerar färg som en av sina tjänster.
Exempelkoden i den här artikeln ändrar det [visuella SampleBarChart-objektet](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
För källkoden, se [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Information om hur du kommer igång med att skapa visuella objekt finns i [Utveckla ett visuellt Power BI-objekt](custom-visual-develop-tutorial.md).

## <a name="add-color-to-data-points"></a>Lägg till färg till datapunkter

En annan färg representerar varje datapunkt.
Lägg till färgen i `BarChartDataPoint`-gränssnittet, som i följande exempel:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Använda färgpalettjänsten

Tjänsten `colorPalette` hanterar de färger som används i ditt visuella objekt.
En instans av tjänsten finns tillgänglig på `IVisualHost`.

Definiera det i `update`-metoden.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Tilldela färg till datapunkter

Ange därefter `dataPoints`.
I det här exemplet innehåller varje `dataPoints` värde, kategori och färg.
`dataPoints` kan även innehålla andra egenskaper.

I `SampleBarChart` sammanfattar `visualTransform`-metoden `dataPoints`-beräkningen.
Den metoden är en del av stapeldiagrammet ViewModel.
Eftersom metoden itererar genom `dataPoints`-beräkningen i `visualTransform`, är det den perfekta platsen att tilldela färger, som i följande kod:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Använd sedan data från `dataPoints` på [d3](https://d3js.org/)-markeringen `barSelection` inuti `update`-metoden:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Nästa steg

Mer information om visuella Power BI-objekt finns i [Funktioner och egenskaper för visuella Power BI-objekt](capabilities.md).

Mer information om hur du utvecklar visuella Power BI-objekt finns i [Så här felsöker du visuella Power BI-objekt](visuals-how-to-debug.md) och [Felsök visuella Power BI-objekt](power-bi-custom-visuals-troubleshoot.md).
