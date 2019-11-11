---
title: Hämta flera data från Power BI
description: I den här artikeln diskuteras hur du aktiverar segmenterad hämtning av stora datamängder för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 6c79673e9d4b7edc95bdfe0373bb8a47d9fe587b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880100"
---
# <a name="fetch-more-data-from-power-bi"></a>Hämta flera data från Power BI

I den här artikeln beskrivs hur du läser in flera data för att kringgå den hårda gränsen på en 30 KB-datapunkt. Den här metoden tillhandahåller data i segment. För att förbättra prestanda kan du konfigurera segmentstorleken så att den passar ditt användningsfall.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Aktivera segmenterad hämtning av stora datamängder

För `dataview`-segmentläget definierar du en fönsterstorlek för dataReductionAlgorithm i det visuella objektets *capabilities.json*-fil för den dataViewMapping som krävs. `count` bestämmer fönsterstorleken, vilket begränsar det antal nya datarader som kan läggas till i `dataview` i varje uppdatering.

Lägg till följande kod i filen *capabilities.json*:

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

## <a name="usage-in-the-power-bi-visual"></a>Användning i det visuella Power BI-objektet

Du kan fastställa huruvida data finns genom att kontrollera existensen av `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Du kan även kontrollera om det är den första uppdateringen eller en efterföljande uppdatering genom att kontrollera `options.operationKind`. I följande kod refererar `VisualDataChangeOperationKind.Create` till det första segmentet och `VisualDataChangeOperationKind.Append` till efterföljande segment.

En exempelimplementering finns i följande kodfragment:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Du kan även anropa metoden `fetchMoreData` från en UI-händelsehanterare såsom det visas här:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Som ett svar på anrop av metoden `this.host.fetchMoreData` anropar Power BI metoden `update` för det visuella objektet med ett nytt datasegment.

> [!NOTE]
> För att undvika klientminnesbegränsningar begränsar Power BI för närvarande totala hämtade data till 100 MB. Du kan se att gränsen har nåtts när fetchMoreData() returnerar `false`.
