---
title: API för visuella filter
description: Så kan visuella Power BI-objekt filtrera andra visuella objekt
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425055"
---
# <a name="power-bi-visual-filters-api"></a>API för visuella filter för Power BI

Visuella filterobjekt möjliggör filterdata. Den största skillnaden jämfört med val är att andra visuella objekt filtreras på något sätt trots markeringsstöd från andra visuella objekt.

För att aktivera filtrering för det visuella objektet ska det visuella objektet innehålla `filter`-objekt i avsnittet `general` i capabilities.json-innehåll.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Filter-API-gränssnitt är tillgängliga i paketet [`powerbi-models`](https://www.npmjs.com/package/powerbi-models). Paketet innehåller även klasser för skapande av filterinstanser.

```cmd
npm install powerbi-models --save
```

Om du använder gamla versioner av verktyg (version som är äldre än 3.x.x) bör du inkludera `powerbi-models` i paketet med visuella objekt. [Kort guide om hur du inkluderar paketet](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Alla filter utökar `IFilter`-gränssnittet.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` – är tabellkolumnen i datakällan.

## <a name="basic-filter-api"></a>Grundläggande filter-API

Grundläggande filtergränssnitt är

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` – är uppräkning med värdena "In", "NotIn" och "All"

`values` – är värden för villkor

Exempel på grundläggande filter:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Filtret innebär "ge mig alla rader där `col1` är lika med ett av värdena 1, 2 eller 3".

SQL-motsvarigheten är

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Om du vill skapa ett filter kan du använda BasicFilter-klassen i `powerbi-models`.

Om du använder den gamla versionen av verktyg bör du hämta en instans av modeller i fönsterobjekt genom att `window['powerbi-models']`:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

Det visuella objektet anropar filtret med hjälp av metoden applyJsonFilter() på värdgränssnittet IVisualHost som tillhandahålls till det visuella objektet i konstruktorn.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>Avancerad filter-API

[Avancerad filter-API](https://github.com/Microsoft/powerbi-models) möjliggör komplexa frågor för val/filtrering av korsvisuella datapunkter baserat på flera kriterier (till exempel "LessThan", "Contains", "Is", "IsBlank" och så vidare).

Filtret introducerades i visualiserings-API 1.7.0.

Avancerat filter-API kräver även `target` med `table` och `column`-namn. Operatorerna för Avancerat filter-API är dock `"And" | "Or"`. 

Dessutom använder filtret villkor i stället för värden med gränssnittet:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Villkorsoperatorer för `operator`-parametern är `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

SQL-motsvarigheten är

```sql
SELECT * FROM table WHERE col1 < 0;
```

Fullständig exempelkod för användning av Avancerat filter-API finns på [`Sampleslicer visual`lagringsplatsen](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>API för tuppelfilter (flerkolumnsfilter)

API för tuppelfilter introducerades i visualiserings-API 2.3.0.

API för tuppelfilter liknar det grundläggande filtret men det gör det möjligt att definiera villkor för flera kolumner och tabeller.

Och ett filter har gränssnitt: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` är en matris med kolumner med tabellnamn:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  Filtret kan hänvisa till kolumner från olika tabeller.

`$schema` är "http://powerbi.com/product/schema#tuple"

`filterType` är `FilterType.Tuple`

`operator` tillåter endast användning av operatorn `"In"`

`values` är en matris med värdetupplar där varje tuppel representerar en tillåten kombination av målkolumnvärdena 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Fullständigt exempel:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**Ordningen på kolumnnamn och värden för villkor är känsliga.**

SQL-motsvarigheten är

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Återställa JSON-filter från datavyn

Från och med API 2.2 kan **JSON-filter** återställas från **VisualUpdateOptions**

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Power BI anropar metoden `update` för det visuella objektet vid användning av switch-bokmärken, och det visuella objektet hämtar motsvarande `filter`-objekt.
[Läs mer om stöd för bokmärken](bookmarks-support.md)

### <a name="sample-json-filter"></a>JSON-exempelfilter

![Skärmbild på JSON-filter](./media/json-filter.png)

### <a name="clear-json-filter"></a>Rensa JSON-filter

Filter-API accepterar `null`-värde för filter som återställning eller rensning.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
