---
title: Hämta mer data
description: Aktivera segmenthämtning av stora datamängder för visuella Power BI-objekt
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425078"
---
# <a name="fetch-more-data-from-power-bi"></a>Hämta flera data från Power BI

Inläsning av flera data-API:er för att lösa den hårdkodade gränsen på 30 000 datapunkter. Detta hämtar data i segment. Segmentstorleken kan konfigureras för att förbättra prestanda enligt användningsfallet.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Aktivera segmenthämtning av stora datamängder

För `dataview`-segmentläge definierar du en "window"-dataReductionAlgorithm i det visuella objektets `capabilities.json` för nödvändig dataViewMapping.
`count` bestämmer fönstrets storlek, vilket begränsar det antal nya datarader som läggs till i `dataview` i varje uppdatering.

Ska läggas till i capabilities.json

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Nya segment läggs till i befintlig `dataview` och anges till det visuella objektet som ett `update`-anrop.

## <a name="usage-in-the-custom-visual"></a>Användning i det anpassade visuella objektet

Indikationen på huruvida data finns eller inte kan fastställas genom att existensen av `dataView.metadata.segment` kontrolleras:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Det är även möjligt att kontrollera om det är den första eller efterföljande uppdateringen genom att kontrollera `options.operationKind`.

`VisualDataChangeOperationKind.Create` innebär det första segmentet och `VisualDataChangeOperationKind.Append` innebär efterföljande segment.

Se kodfragmentet nedan för en exempelimplementering:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Metoden `fetchMoreData` kan också anropas från en händelsehanterare för användargränssnitt

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI anropar metoden `update` för det visuella objektet med det nya datasegmentet som svar på anropet av metoden `this.host.fetchMoreData`.

> [!NOTE]
> Power BI begränsar för närvarande hämtade data till **100 MB** för att undvika klientbegränsningar för minne. Du kan identifiera att den här gränsen nås när fetchMoreData() returnerar "false".*
