---
title: API för visuella filter i visuella Power BI-objekt
description: I den här artikeln beskrivs hur visuella Power BI-objekt kan filtrera andra visuella objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ee4ac2db9d27129172797db9743790b5175dcd89
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880064"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>API för visuella filter i visuella Power BI-objekt

Med API:et för visuella filter kan du filtrera data i visuella Power BI-objekt. Den största skillnaden jämfört med andra val är att andra visuella objekt filtreras på något sätt trots markeringsstöd från andra visuella objekt.

För att filtrering ska aktiveras för det visuella objektet ska det innehålla ett `filter`-objekt i avsnittet `general` i koden för *capabilities.json*.

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

Gränssnitt för API:et för visuella filter finns i paketet [powerbi-models](https://www.npmjs.com/package/powerbi-models). Paketet innehåller även klasser för skapande av filterinstanser.

```cmd
npm install powerbi-models --save
```

Om du använder en äldre version av verktygen (tidigare än 3.x.x) bör du ta med `powerbi-models` i paketet med visuella objekt. Mer information finns i den korta guiden [Add the Advanced Filter API to the custom visual](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md) (Lägga till API:et för avancerat filter i det anpassade visuella objektet).

Alla filter utökar `IFilter`-gränssnittet enligt följande kod:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Där:
* `target` är tabellkolumnen i datakällan.

## <a name="the-basic-filter-api"></a>API:et för grundläggande filter

Gränssnittet för grundläggande filter visas i följande kod:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Där:
* `operator` är en uppräkning med värdena *In*, *NotIn* och *All*.
* `values` är värden för villkoret.

Exempel på ett grundläggande filter:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Filtret innebär ”Ge mig alla rader där `col1` är lika med värdet 1, 2 eller 3”.

SQL-motsvarigheten är:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Om du vill skapa ett filter kan du använda klassen BasicFilter i `powerbi-models`.

Om du använder en äldre version av verktyget bör du hämta en instans av modellerna i window-objektet med hjälp av `window['powerbi-models']` enligt följande kod:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

Det visuella objektet anropar filtret med hjälp av metoden applyJsonFilter() i värdgränssnittet, IVisualHost, som tillhandahålls till det visuella objektet i konstruktorn.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>API:et för avancerat filter

[API:et för avancerat filter](https://github.com/Microsoft/powerbi-models) möjliggör komplexa frågor för val och filtrering av korsvisuella datapunkter som baseras på flera kriterier, till exempel *LessThan*, *Contains*, *Is*, *IsBlank* och så vidare).

Filtret introducerades i visualiserings-API 1.7.0.

API:et för avancerat filter kräver även `target` med ett `table`- och `column`-namn. Operatorerna för API:et för avancerat filter är dock *And* och *Or*. 

Dessutom använder filtret villkor i stället för värden med gränssnittet:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Villkorsoperatorer för parametern `operator` är *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* och ”IsNotBlank”.

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

SQL-motsvarigheten är:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Den fullständiga exempelkoden för användning av API:et för avancerat filter finns på [lagringsplatsen för det visuella objektet Sampleslicer](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="the-tuple-filter-api-multi-column-filter"></a>API:et för tuppelfilter (flerkolumnsfilter)

API:et för tuppelfilter-introducerades i API:et för visuella objekt 2.3.0. Det liknar API:et för grundläggande filter men gör det möjligt att definiera villkor för flera kolumner och tabeller.

Filtergränssnittet visas i följande kod: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Där:
* `target` är en matris med kolumner med tabellnamn:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  Filtret kan hänvisa till kolumner från flera olika tabeller.

* `$schema` är https://powerbi.com/product/schema#tuple.

* `filterType` är *FilterType.Tuple*.

* `operator` tillåter endast användning i operatorn *In*.

* `values` är en matris med värdetupplar, och varje tuppel representerar en tillåten kombination av målkolumnvärdena. 

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
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "https://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> Ordningen på kolumnnamnen och villkorsvärden är känslig.

SQL-motsvarigheten är:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Återställa JSON-filtret från datavyn

Från och med API-version 2.2 kan du återställa JSON-filtret från *VisualUpdateOptions* enligt följande kod:

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

När du växlar bokmärken anropar Power BI metoden `update` för det visuella objektet, och det visuella objektet hämtar motsvarande `filter`-objekt. Mer information finns i [Lägga till stöd för bokmärken för visuella Power BI-objekt](bookmarks-support.md).

### <a name="sample-json-filter"></a>JSON-exempelfilter

Viss kod för JSON-exempelfilter visas i följande bild:

![Kod för JSON-filter](./media/json-filter.png)

### <a name="clear-the-json-filter"></a>Rensa JSON-filtret

Filter-API:et accepterar värdet `null` för filtret såsom *reset* (återställ) eller *clear* (rensa).

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
