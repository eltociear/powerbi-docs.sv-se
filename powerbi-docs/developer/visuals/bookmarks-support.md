---
title: Bokmärken
description: Visuella Power BI-objekt kan hantera bokmärkesväxling
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425515"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Lägga till stöd för bokmärken för visuella Power BI-objekt

Med Power BI-rapportbokmärken kan du få en konfigurerad vy av en rapportsida, ett urvalstillstånd och ett filtreringstillstånd för det visuella objektet. Men det krävs ytterligare åtgärder från anpassade visuella objekt för att stödja bokmärket och reagera korrekt på ändringar.

Läs mer om bokmärken i [dokumentationen](https://docs.microsoft.com/power-bi/desktop-bookmarks)

## <a name="report-bookmarks-support-in-your-visual"></a>Stöd för rapportbokmärken i ditt visuella objekt

Om ditt visuella objekt interagerar med andra visuella objekt, väljer datapunkter eller filtrerar andra visuella objekt behöver du återställa tillstånd från egenskaper.

## <a name="how-to-add-report-bookmarks-support"></a>Så lägger du till stöd för rapportbokmärken

1. Installera (eller uppdatera) det verktyg som krävs: `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) version 3.0.0 eller senare. Det innehåller ytterligare klasser som kan manipuleras med tillståndsurval eller filter. Det krävs för visuella filterobjekt och alla visuella objekt som använder `InteractivityService`.

2. Uppdatera API för visuella objekt till 1.11.0 för att använda `registerOnSelectCallback` i stället för `SelectionManager`. Det krävs för icke-filtrerande visuella objekt med det vanliga `SelectionManager` i stället för `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Så interagerar visuella objekt med Power BI i scenariot för rapportbokmärken

Vi tittar på följande exempel: En användare skapar flera bokmärken på rapportsidan med olika urvalstillstånd i varje bokmärke.

Först väljer användaren en datapunkt i ditt visuella objekt. Det visuella objektet interagerar med Power BI och andra visuella objekt genom att skicka val till värden. Sedan väljer användaren ”Lägg till” i `Bookmark panel`, och Power BI sparar de aktuella valen för det nya bokmärket.

Det inträffar flera gånger allt eftersom användaren ändrar valet och lägger till nya bokmärken.
När bokmärken har skapats kan användaren växla mellan dem.

När användare väljer ett bokmärke återställer Power BI det sparade filtret eller urvalstillståndet och skickar det till de visuella objekten. Andra visuella objekt markeras eller filtreras enligt det tillstånd som lagras i bokmärket. Power BI-värden ansvarar för åtgärder. Ditt visuella objekt ansvarar för korrekt visning av det nya urvalstillståndet (till exempel ändra färg på renderade datapunkter).

Det nya urvalstillståndet förmedlas till det visuella objektet via metoden `update`. Argumentet `options` innehåller en särskild egenskap: `options.jsonFilters`. Dess JSONFilter-egenskap kan innehålla `Advanced Filter` och `Tuple Filter`.

Det visuella objektet bör återställa filtervärden till att visa det visuella objektets motsvarande tillstånd för det valda bokmärket.

Du kan även använda den särskilda metoden `registerOnSelectCallback` för registrerad motringningsfunktion i ISelectionManager om det visuella objektet endast använder urval.

### <a name="visuals-with-selections"></a>Visuella objekt med urval

Om dina visuella objekt interagerar med andra visuella objekt med hjälp av [urval](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md) finns det två sätt att lägga till bokmärken.

* Du kan använda metoden `FilterManager.restoreSelectionIds` om du **inte har använt [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** förut i det visuella objektet.

* Om ditt visuella objekt redan använder **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** för att hantera urval bör du använda metoden `applySelectionFromFilter` i stället för `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Använda `ISelectionManager.registerOnSelectCallback`

När en användare klickar på bokmärken anropar Power BI metoden `callback` för det visuella objektet med motsvarande urval. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Vi antar att du har en datapunkt i ditt visuella objekt som skapats i metoden [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

Och `datapoints` ser ut så här:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Du har alltså `visualDataPoints` datapunkter och matrisen `ids` skickas till funktionen `callback`.

I det här läget bör det visuella objektet jämföra matrisen `ISelectionId[]` med markeringarna i matrisen `visualDataPoints` och markera motsvarande datapunkter som valda.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

När datapunkterna har uppdaterats speglar de det aktuella urvalstillstånd som lagras i `filter`-objektet. När datapunkterna renderas kommer det anpassade visuella objektets urvalstillstånd att matcha bokmärkets tillstånd.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Använda `InteractivityService` för kontrollval i det visuella objektet

Om ditt visuella objekt använder `InteractivityService` behöver du inte några ytterligare åtgärder för att stödja bokmärken i ditt visuella objekt.

Verktyget hanterar det visuella objektets urvalstillstånd när användaren väljer bokmärken.

### <a name="visuals-with-filter"></a>Visuella objekt med filter

Vi antar att det visuella objektet skapar ett filter för data efter datumintervall. Vi har då `startDate` och `endDate` som början och slutet av intervallet.
Det visuella objektet skapar ett avancerat filter och anropar värdmetoden `applyJsonFilter` för att filtrera data efter relevanta villkor.
`target` är tabellen för filtrering.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Varje gång en användare klickar på ett bokmärke får det anpassade visuella objektet ett `update`-anrop.

Det anpassade visuella objektet bör kontrollera filtret i objektet:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Om `filter`-objektet inte är null bör det visuella objektet återställa filtervillkoren från objektet:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Därefter bör det visuella objektet ändra sitt interna tillstånd – datapunkter och visualiseringsobjekt (linjer, rektanglar och så vidare) – till att spegla de aktuella villkoren.

> [!IMPORTANT]
> I scenariot för rapportbokmärken ska det visuella objektet inte anropa `applyJsonFilter` för att filtrera andra visuella objekt – de kommer redan att filtreras av Power BI.

Det visuella objektet Tidslinjeutsnitt ändrar intervallväljaren till att motsvara dataintervallen.

Mer information finns i [datalagret för Tidslinjeutsnitt](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Filtrera tillstånd för att spara egenskaper för visuella objekt i bokmärken

Egenskapen `filterState` gör en egenskap till en del av filtreringen. Det visuella objektet kan lagra olika värden i bokmärken.

För att spara egenskapsvärdet som filtreringstillstånd ska objektegenskapen markeras som `"filterState": true` i `capabilities.json`.

Exempel: `Timeline Slicer` lagrar egenskapsvärden för `Granularity` i filtret. Och det gör att du kan ändra aktuell kornighet när användare ändrar bokmärken.

Mer information finns i [datalagret för Tidslinjeutsnitt](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
