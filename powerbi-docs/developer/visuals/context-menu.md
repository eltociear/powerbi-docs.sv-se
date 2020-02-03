---
title: Funktioner och egenskaper för visuella Power BI-objekt
description: I den här artikeln beskrivs funktioner och egenskaper för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819202"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Lägga till en snabbmeny i ett visuellt Power BI-objekt

Du kan använda `selectionManager.showContextMenu()` med `selectionId`-parametrar och en position (som ett `{x:, y:}`-objekt) om du vill att Power BI ska visa en snabbmeny för ditt visuella objekt.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` introducerades i visualiserings-API 2.2.0.

Vanligtvis läggs den till som en högerklickningsåtgärd (eller en lång tryckning för pekenheter). Snabbmenyn lades till i exemplets BarChart som referens:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
