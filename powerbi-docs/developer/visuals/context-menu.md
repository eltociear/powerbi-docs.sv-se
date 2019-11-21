---
title: Funktioner och egenskaper för visuella Power BI-objekt
description: I den här artikeln beskrivs funktioner och egenskaper för visuella Power BI-objekt.
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206f1aec7c76b00b6f725d8469eb3e483a01c653
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061786"
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
