---
title: Funktioner
description: Funktioner och egenskaper för visuella Power BI-objekt
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425469"
---
# <a name="power-bi-visual-capabilities"></a>Funktioner för visuella Power BI-objekt

Funktioner ger värden information om ditt visuella objekt. Alla egenskaper för funktionsmodellen är `optional`

Rotobjekten för det visuella objektets funktioner är `dataRoles`, `dataViewMappings` och så vidare.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>Definiera de datafält som förväntas av det visuella objektet – `dataRoles`

För att definiera fält som kan bindas till data använder vi `dataRoles` som tar en matris med `DataViewRole`-objekt, som definierar alla egenskaper som behövs.

### <a name="properties"></a>Egenskaper

* **name** – det interna namnet för det här datafältet (måste vara unikt)
* **kind** – fältets typ:
    * `Grouping` – diskreta värden som används för att gruppera måttfält
    * `Measure` – numeriska datavärden
    * `GroupingOrMeasure` – kan användas som antingen en gruppering eller ett mått
* **displayName** – namnet som visas för användaren i fönstret Egenskaper
* **description** – en kort beskrivning av fältet (valfritt)
* **requiredTypes** – den datatyp som krävs för den här datarollen. Alla värden som inte matchar anges till null (valfritt)
* **preferredTypes** – den önskade datatypen för den här datarollen (valfritt)

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Giltiga datatyper i requiredTypes och preferredTypes

* **bool** – ett booleskt värde
* **integer** – ett heltalsvärde
* **numeric** – ett numeriskt värde
* **text** – ett textvärde
* **geography** – geografiska data

### <a name="example"></a>Exempel

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

Datarollerna ovan skapar följande fält

![Dataroll som visas](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>Definiera hur du vill att data ska mappas – `dataViewMappings`

DataViewMapping beskriver hur datarollerna är relaterade till varandra och gör att du kan ange villkorskrav för dem.

De flesta visuella objekt har en enda mappning, men du kan ange flera dataViewMappings. Varje giltig mappning genererar en DataView. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[Läs mer om DataViewMappings](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>Definiera alternativ för egenskapsfönster – `objects`

Objekt beskriver anpassningsbara egenskaper som är associerade med det visuella objektet.
Varje objekt kan ha flera egenskaper och varje egenskap kan associeras med en typ.
Typer refererar till vad egenskapen ska vara. Nedan finns mer information om typer.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[Läs mer om objekt](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>Hantera partiell markering – `supportsHighlight`

Som standard är det här värdet inställt på false, vilket innebär att dina "values" (värden) filtreras automatiskt när något på sidan väljs, vilket i sin tur uppdaterar ditt visuella objekt så att det bara visar det valda värdet. Om du vill visa fullständiga data, men bara markera de valda objekten, måste du ange `supportsHighlight` till true i capabilities.json.

[Läs mer om markering](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>Hantera Avancerat redigeringsläge – `advancedEditModeSupport`

Ett visuellt objekt kan deklarera stöd för Avancerat redigeringsläge.
Som standard har ett visuellt objekt inte stöd för Avancerat redigeringsläge, om inget annat anges i capabilities.json.

[Läs mer om advancedEditModeSupport](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>Datasorteringsalternativ för visuellt objekt – `sorting`

Ett visuellt objekt kan definiera dess sorteringsbeteende via dess funktioner.
Som standard har ett visuellt objekt inte stöd för ändring av sorteringsordning, om inget annat anges i capabilities.json.

[Läs mer om sortering](sort-options.md)
