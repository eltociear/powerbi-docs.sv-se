---
title: Objekt och egenskaper
description: Anpassningsbara egenskaper för visuella Power BI-objekt
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424618"
---
# <a name="object-and-properties"></a>Objekt och egenskaper

Objekt beskriver anpassningsbara egenskaper som är associerade med det visuella objektet.
Varje objekt kan ha flera egenskaper och varje egenskap kan associeras med en typ.
Typer refererar till vad egenskapen ska vara. Nedan finns mer information om typer.

`myCustomObject` är det interna namn som används för att referera till objektet i `dataView` och `enumerateObjectInstances`

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

`properties` är en karta över egenskaper som definierats av utvecklaren.

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

Det finns två typer av egenskapstyper: `ValueTypeDescriptor` och `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Deskriptor för värdetyp

`ValueTypeDescriptor` är mestadels primitiva typer och används vanligtvis som ett statiskt objekt.
Här följer några vanliga `ValueTypeDescriptor`

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Deskriptor för strukturell typ

`StructuralTypeDescriptor` används främst för databundna objekt.
Fyllning är den vanligaste `StructuralTypeDescriptor`

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Toningsegenskap

Toningsegenskapen är en egenskap som inte kan anges som en standardegenskap. I stället behöver du ange en regel för ersättning av färgväljaregenskapen (fyllningstyp).
Se exemplet nedan:

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

Var uppmärksam på egenskaperna `"fill"` och `"fillRule"`. Den första är färgväljaren, och den andra är ersättningsregeln för toning som ersätter ”fyllningsegenskapen” `visually` när regelvillkoren är uppfyllda.

Den här länken mellan fyllningsegenskapen och ersättningsregeln anges i avsnittet `"rule"`->`"output"` i egenskapen `"fillRule"`.

`"Rule"`->`"InputRole"` anger vilken dataroll som utlöser regeln (villkoret). I det här exemplet gäller att om datarollen `"Gradient"` innehåller data så används regeln för egenskapen `"fill"`.

Nedan visas ett exempel på den dataroll som utlöser fyllningsregeln (`the last item`).

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

## <a name="enumerateobjectinstances-method"></a>Metoden `enumerateObjectInstances`

För att kunna använda objekt effektivt behöver du en funktion i ditt anpassade visuella objekt som kallas `enumerateObjectInstances`. Den här funktionen fyller i egenskapsfönstret med objekt och bestämmer även var objekten ska bindas i datavyn.  

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

Egenskaperna i `enumerateObjectInstances` speglar de egenskaper som du definierade i dina funktioner. Se exemplet längst ned på sidan.

### <a name="objects-selector"></a>Objektväljare

Väljaren i `enumerateObjectInstances` bestämmer var varje objekt ska bindas i datavyn. Det finns fyra olika alternativ.

#### <a name="static"></a>statiskt

Det här objektet kommer att bindas till metadata `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>kolumner

Det här objektet kommer att bindas till kolumner med matchande `QueryName`.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>väljare

Det här objektet kommer att bindas till det element som vi har skapat ett `selectionID` för. I det här exemplet antar vi att vi har skapat `selectionID` för vissa datapunkter, och vi loopar genom dem.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Omfångsidentitet

Det här objektet kommer att bindas till vissa värden i skärningspunkten för grupper. Om jag till exempel har kategorierna `["Jan", "Feb", "March", ...]` och serierna `["Small", "Medium", "Large"]` vill jag kanske ha ett objekt i skärningspunkten för värden som matchar `Feb` och `Large`. För att åstadkomma detta kan jag hämta `DataViewScopeIdentity` för båda kolumnerna, skicka dem till variabeln `identities` och använda den här syntaxen med väljaren.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exempel

I det här exemplet visar vi hur en objectEnumeration skulle se ut för ett customColor-objekt med en `fill`-egenskap. Vi vill att det här objektet ska bindas statiskt till `dataViews[index].metadata.objects`

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
