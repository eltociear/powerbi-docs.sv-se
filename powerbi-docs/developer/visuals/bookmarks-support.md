---
title: Lägga till stöd för bokmärken för visuella Power BI-objekt
description: Visuella Power BI-objekt kan hantera bokmärkesväxling
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 5bf1c79aa411788fdb3275b938e7eaad7d6014a1
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380535"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Lägga till stöd för bokmärken för visuella Power BI-objekt

Med Power BI-rapportbokmärken kan du samla en konfigurerad vy av en rapportsida, urvalstillståndet samt filtreringstillståndet för det visuella objektet. Men det krävs ytterligare åtgärder från det visuella Power BI-objekten för att stödja bokmärket och reagera korrekt på ändringar.

Mer information om bokmärken finns i [Använda bokmärken för att dela insikter och skapa artiklar i Power BI](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Stöd för rapportbokmärken i ditt visuella objekt

Om ditt visuella objekt interagerar med andra visuella objekt, väljer datapunkter eller filtrerar andra visuella objekt behöver du återställa tillståndet från egenskaper.

## <a name="add-report-bookmarks-support"></a>Lägga till stöd för rapportbokmärken

1. Installera (eller uppdatera) det verktyg som krävs, [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) version 3.0.0 eller senare. Det innehåller ytterligare klasser som kan manipuleras med tillståndsurvalet eller filter. Det krävs för visuella filterobjekt och alla visuella objekt som använder `InteractivityService`.

2. Uppdatera API:et för visuella objekt till version 1.11.0 för att använda `registerOnSelectCallback` i en instans av `SelectionManager`. Det krävs för icke-filtrerande visuella objekt som använder det vanliga `SelectionManager` i stället för `InteractivityService`.

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Så interagerar visuella Power BI-objekt med Power BI i rapportbokmärken

Vi tänker oss följande scenario: Du vill skapa flera bokmärken på rapportsidan med olika urvalstillstånd i varje bokmärke.

Först väljer du en datapunkt i ditt visuella objekt. Det visuella objektet interagerar med Power BI och andra visuella objekt genom att skicka val till värden. Sedan väljer du **Lägg till** i fönstret **Bokmärke**, så sparar Power BI de aktuella valen för det nya bokmärket.

Det inträffar flera gånger allt eftersom du ändrar valet och lägger till nya bokmärken. När du har skapat bokmärkena kan du växla mellan dem.

När du väljer ett bokmärke återställer Power BI det sparade filtret eller urvalstillståndet och skickar det till de visuella objekten. Andra visuella objekt markeras eller filtreras enligt det tillstånd som lagras i bokmärket. Power BI-värden ansvarar för åtgärderna. Ditt visuella objekt ansvarar för korrekt visning av det nya urvalstillståndet (till exempel ändring av färg på renderade datapunkter).

Det nya urvalstillståndet förmedlas till det visuella objektet via metoden `update`. Argumentet `options` innehåller en särskild egenskap, `options.jsonFilters`. Dess JSONFilter-egenskap kan innehålla `Advanced Filter` och `Tuple Filter`.

Det visuella objektet bör återställa filtervärdena till att visa det visuella objektets motsvarande tillstånd för det valda bokmärket. Om det visuella objektet endast använder urval kan du även använda den särskilda metoden `registerOnSelectCallback` för registrerad motringningsfunktion i ISelectionManager.

### <a name="visuals-with-selection"></a>Visuella objekt med urval

Om ditt visuella objekt interagerar med andra visuella objekt med hjälp av [Val](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md) kan du lägga till bokmärken på endera av de följande två sätten:

* Om det visuella objektet inte redan har använt [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) kan du använda metoden `FilterManager.restoreSelectionIds`.

* Om det visuella objektet redan använder [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) för att hantera val bör du använda metoden `applySelectionFromFilter` i instansen av `InteractivityService`.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>Använda ISelectionManager.registerOnSelectCallback

När du väljer ett bokmärke anropar Power BI metoden `callback` för det visuella objektet med motsvarande urval. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Vi antar att du har en datapunkt i det visuella objektet som skapades i metoden [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

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

Nu har du `visualDataPoints` som dina datapunkter och matrisen `ids` som skickats till funktionen `callback`.

I det här läget bör det visuella objektet jämföra matrisen `ISelectionId[]` med valen i matrisen `visualDataPoints` och markera motsvarande datapunkter som valda.

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

När du har uppdaterat datapunkterna speglar de det aktuella urvalstillstånd som lagras i `filter`-objektet. När datapunkterna sedan renderas kommer det anpassade visuella objektets urvalstillstånd att matcha bokmärkets tillstånd.

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>Använda InteractivityService för kontrollval i det visuella objektet

Om ditt visuella objekt använder `InteractivityService` behöver du inte några ytterligare åtgärder för att stödja bokmärken i ditt visuella objekt.

När du väljer bokmärken hanterar verktyget det visuella objektets urvalstillstånd.

### <a name="visuals-with-a-filter"></a>Visuella objekt med ett filter

Vi antar att det visuella objektet skapar ett filter för data efter datumintervall. Du har `startDate` och `endDate` som startdatum och slutdatum för intervallet.

Det visuella objektet skapar ett avancerat filter och anropar värdmetoden `applyJsonFilter` för att filtrera data efter relevanta villkor.

Målet är den tabell som används för filtrering.

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

Varje gång du väljer ett bokmärke får det anpassade visuella objektet ett `update`-anrop.

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

Därefter bör det visuella objektet ändra sitt intern tillstånd så att det återspeglar de aktuella villkoren. Det interna tillståndet omfattar datapunkterna och visualiseringsobjekten (linjer, rektanglar och så vidare).

> [!IMPORTANT]
> I scenariot för rapportbokmärken ska det visuella objektet inte anropa `applyJsonFilter` för att filtrera de andra visuella objekten. De kommer redan att filtreras av Power BI.

Det visuella objektet Tidslinjeutsnitt ändrar intervallväljaren till motsvarande dataintervall.

Mer information finns i [datalagret för Tidslinjeutsnitt](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Filtrera tillståndet för att spara egenskaper för visuella objekt i bokmärken

Egenskapen `filterState` gör en egenskap till en del av filtreringen. Det visuella objektet kan lagra ett flertal olika värden i bokmärken.

Om du vill spara egenskapsvärdet som ett filtertillstånd markerar du objektegenskapen som `"filterState": true` i filen *capabilities.json*.

Till exempel lagrar tidslinjeutsnittet `Granularity`-egenskapsvärden i ett filter. Det gör att den aktuella kornigheten kan ändras när du ändrar bokmärkena.

Mer information finns i [datalagret för Tidslinjeutsnitt](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
