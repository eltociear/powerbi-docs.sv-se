---
title: Stöd för högkontrastläge
description: Så lägger du till stöd för högkontrastläge för visuella Power BI-objekt
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cb77ea012fdfdbd5be62c58c6f9b94a0355db1a9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424940"
---
# <a name="high-contrast-mode-support"></a>Stöd för högkontrastläge

Windows-inställningen *Högkontrast* gör text och appar lättare att se genom att använda mer distinkta färger.
Läs mer om [stöd för högkontrast i Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Följande krävs för att lägga till stöd för högkontrast för ditt visuella objekt:

1. Vid initiering: Identifiera om Power BI är i högkontrastläge och hämta i så fall aktuella högkontrastfärger.
2. Varje uppdatering: Ändra det sätt på vilket det visuella objektet renderas för att göra det lättare att se.

Visuella PowerBI-objekt – det visuella objektet sampleBarChart har implementering av stöd för högkontrast.

Mer information finns på [lagringsplatsen PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6)

## <a name="on-init"></a>Vid initiering

colorPalette-medlemmen `options.host` har flera egenskaper för högkontrastläge. Använd dessa egenskaper för att avgöra huruvida högkontrastläge är aktivt och i så fall vilka färger som ska användas.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Identifiera om Power BI är i högkontrastläge

Om `host.colorPalette.isHighContrast` är `true` så är högkontrastläget aktivt, och det visuella objektet bör rita sig självt därefter.

### <a name="get-high-contrast-colors"></a>Få högkontrastfärger

I högkontrastläge bör ditt visuella objekt begränsas till följande färger:

* **Förgrundsfärg** används för att rita linjer, ikoner, text och konturer eller fyllningsformer.
* **Bakgrundsfärg** används för bakgrunden samt som fyllningsfärg för konturformer.
* **Förgrund – vald** färg används för att ange ett markerat eller aktivt element.
* **Hyperlänkfärg** används endast för hyperlänktext.

> [!NOTE]
> Om en sekundär färg behövs kan förgrundsfärgen användas med viss opacitet (inbyggda visuella Power BI-objekt använder 40 % opacitet). Använd det här sparsamt så att visuell information är enkel att se.

Du kan lagra dessa värden under initieringen:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

Eller så kan du lagra `host`-objektet under initieringen och komma åt relevanta `colorPalette`-egenskaper under uppdateringen.

## <a name="on-update"></a>Vid uppdatering

De specifika implementeringarna av stöd för högkontrast skiljer sig mellan olika visuella objekt och är beroende av hur den grafiska designen ter sig. Vanligtvis kräver högkontrastläge en något annorlunda design än den vanliga, så att viktig information lätt kan särskiljas med de begränsade färgerna.

Här är några riktlinjer som följs av inbyggda visuella Power BI-objekt:

* Alla datapunkter använder samma färg (förgrund).
* All text och alla axlar, pilar, rader och så vidare. använd förgrundsfärg.
* Tjocka former ritas som konturer, med tjocka streck (minst två bildpunkter) och bakgrundsfärgfyllning.
* När det är relevant särskiljs datapunkter av olika markörformer, och datalinjer särskiljs med olika streck.
* När ett dataelement markeras ändrar alla andra element sin opacitet till 40 %.
* För utsnitt använder aktiva filterelement färgen förgrund – vald.

I exempelstapeldiagrammet ritas till exempel alla staplar med förgrundskontur och bakgrundsfyllning som är två bildpunkter tjocka. Jämför hur det ser ut med standardfärger och med några högkontrastteman:

![Exempelstapeldiagram med standardfärger](./media/hc-samplebarchart-standard.png)
![Exempelstapeldiagram med färgtemat *Mörk #2*](./media/hc-samplebarchart-dark2.png)
![Exempelstapeldiagram med färgtemat *Vitt*](./media/hc-samplebarchart-white.png)

Här är en plats i funktionen `visualTransform` som har ändrats till att stödja högkontrast. Den anropas även som en del av renderingen under `update`:

### <a name="before"></a>Före

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Efter

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
