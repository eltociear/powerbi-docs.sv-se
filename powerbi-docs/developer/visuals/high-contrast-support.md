---
title: Stöd för högkontrastläge i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till stöd för högkontrastläge för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f5e6d205a26648f8e157663ed7afd58e33b4b328
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194001"
---
# <a name="high-contrast-mode-support-in-power-bi-visuals"></a>Stöd för högkontrastläge i visuella Power BI-objekt

Windows-inställningen *Högkontrast* gör text och appar lättare att se genom att visa mer distinkta färger. I den här artikeln diskuteras hur du lägger till stöd för högkontrastläge för visuella Power BI-objekt. Mer information finns i [stöd för högkontrast i Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Du kan se en implementering av stöd för högkontrast genom att gå till [lagringsplatsen för det visuella objektet PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6).

## <a name="on-initialization"></a>Vid initiering

colorPalette-medlemmen `options.host` har flera egenskaper för högkontrastläge. Använd dessa egenskaper för att avgöra huruvida högkontrastläge är aktivt och i så fall vilka färger som ska användas.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Identifiera om Power BI är i högkontrastläge

Om `host.colorPalette.isHighContrast` är `true` så är högkontrastläget aktivt, och det visuella objektet bör rita sig självt därefter.

### <a name="get-high-contrast-colors"></a>Få högkontrastfärger

I högkontrastläge bör ditt visuella objekt begränsas till följande inställningar:

* **Förgrundsfärg** används för att rita linjer, ikoner, text och konturer eller fyllningsformer.
* **Bakgrundsfärg** används för bakgrunden samt som fyllningsfärg för konturformer.
* **Förgrund – vald** färg används för att ange ett markerat eller aktivt element.
* **Hyperlänkfärg** används endast för hyperlänktext.

> [!NOTE]
> Om en sekundär färg behövs kan förgrundsfärgen användas med viss opacitet (inbyggda visuella Power BI-objekt använder 40 % opacitet). Använd det här sparsamt så att visuell information är enkel att se.

Vid initiering kan du lagra följande värden:

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

De specifika implementeringarna av stöd för högkontrast skiljer sig mellan olika visuella objekt och är beroende av hur den grafiska designen ter sig. Vanligtvis kräver högkontrastläge en något annorlunda design än standardläget, så att viktig information lätt kan särskiljas med de begränsade färgerna.

Inbyggda visuella Power BI-objekt följer dessa riktlinjer:

* Alla datapunkter använder samma färg (förgrund).
* All text och alla axlar, pilar, linjer och så vidare använder förgrundsfärgen.
* Tjocka former ritas som konturer, med tjocka streck (minst två bildpunkter) och bakgrundsfärgfyllning.
* När datapunkter är relevanta särskiljs de av olika markörformer, och datalinjer särskiljs med olika streck.
* När ett dataelement markeras ändrar alla andra element sin opacitet till 40 %.
* För utsnitt använder aktiva filterelement färgen förgrund – vald.

I följande exempelstapeldiagram ritas till exempel alla staplar med förgrundskontur och bakgrundsfyllning som är två bildpunkter tjocka. Jämför hur det ser ut med standardfärger och med några högkontrastteman:

![Exempelstapeldiagram med standardfärger](./media/hc-samplebarchart-standard.png)
![Exempelstapeldiagram med färgtemat *Mörk #2*](./media/hc-samplebarchart-dark2.png)
![Exempelstapeldiagram med färgtemat *Vitt*](./media/hc-samplebarchart-white.png)

I nästa avsnitt visas ett ställe i funktionen `visualTransform` som ändrades för att stödja högkontrast. Det anropas som en del av renderingen under uppdateringen.

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
