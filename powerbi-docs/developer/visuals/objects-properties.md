---
title: Objekt och egenskaper för visuella Power BI-objekt
description: I den här artikeln beskrivs anpassningsbara egenskaper för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ae548abd0d579414a69b0d970213ff9d69ff2f08
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79205882"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Objekt och egenskaper för visuella Power BI-objekt

Objekt beskriver anpassningsbara egenskaper som är associerade med ett visuellt objekt. Ett objekt kan ha flera egenskaper, och varje egenskap har en associerad typ som beskriver vad egenskapen ska vara. Den här artikeln innehåller information om objekt och egenskapstyper.

`myCustomObject` är det interna namn som används för att referera till objektet i `dataView` och `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Visningsnamn

`displayName` är det namn som visas i egenskapsfönstret.

## <a name="properties"></a>Egenskaper

`properties` är en karta över egenskaper som definieras av utvecklaren.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` är en särskild egenskap som aktiverar en växel för objektet.

Exempel:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Egenskapstyper

Det finns två egenskapstyper: `ValueTypeDescriptor` och `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Deskriptor för värdetyp

`ValueTypeDescriptor`-typer är mestadels primitiva och används vanligtvis som ett statiskt objekt.

Här följer några vanliga `ValueTypeDescriptor`-element:

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Deskriptor för strukturell typ

`StructuralTypeDescriptor`-typer används främst för databundna objekt.
Den vanligaste `StructuralTypeDescriptor`-typen är *fill*.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Toningsegenskap

Toningsegenskapen är en egenskap som inte kan anges som en standardegenskap. I stället behöver du ange en regel för ersättning av färgväljaregenskapen (*fill*-typ).

Ett exempel visas i följande kod:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Var uppmärksam på egenskaperna *fill* och *fillRule*. Den första är färgväljaren, och den andra är ersättningsregeln för toning som ersätter *fill-egenskapen*, `visually`, när regelvillkoren är uppfyllda.

Den här länken mellan *fill*-egenskapen och ersättningsregeln anges i avsnittet `"rule"`>`"output"` i egenskapen *fillRule*.

Egenskapen `"Rule"`>`"InputRole"` anger vilken dataroll som utlöser regeln (villkoret). I det här exemplet gäller att om datarollen `"Gradient"` innehåller data så används regeln för egenskapen `"fill"`.

Ett exempel på den dataroll som utlöser fill-regeln (`the last item`) visas i följande kod:

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>Metoden enumerateObjectInstances

För att kunna använda objekt effektivt behöver du en funktion i ditt anpassade visuella objekt som heter `enumerateObjectInstances`. Den här funktionen fyller i egenskapsfönstret med objekt och bestämmer även var objekten ska bindas i dataView.  

Så här ser en typisk konfiguration ut:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Egenskaper

Egenskaperna i `enumerateObjectInstances` speglar de egenskaper som du definierade i dina funktioner. Ett exempel finns i slutet av den här artikeln.

### <a name="objects-selector"></a>Objektväljare

Väljaren i `enumerateObjectInstances` bestämmer var varje objekt binds i dataView. Det finns fyra olika alternativ.

#### <a name="static"></a>statiskt

Det här objektet binds till metadata `dataviews[index].metadata.objects` enligt det som visas här.

```typescript
selector: null
```

#### <a name="columns"></a>kolumner

Det här objektet binds till kolumner med matchande `QueryName`.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>väljare

Det här objektet binds till det element som du skapade ett `selectionID` för. I det här exemplet antar vi att vi har skapat `selectionID` för vissa datapunkter samt vi loopar genom dem.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Omfångsidentitet

Det här objektet binds till vissa värden i skärningspunkten för grupper. Om du till exempel har kategorierna `["Jan", "Feb", "March", ...]` och serierna `["Small", "Medium", "Large"]` vill du kanske ha ett objekt i skärningspunkten för värden som matchar `Feb` och `Large`. För att åstadkomma detta kan du hämta `DataViewScopeIdentity` för båda kolumnerna, skicka dem till variabeln `identities` och använda den här syntaxen med väljaren.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exempel

Följande exempel visar hur objectEnumeration skulle se ut för ett customColor-objekt med en egenskap, *fill*. Vi vill att det här objektet ska bindas statiskt till `dataViews[index].metadata.objects` enligt följande:

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
