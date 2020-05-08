---
title: Introduktion till användning av verktyg för knappbeskrivningar för visuella Power BI-objekt
description: Den här artikeln beskriver hur du använder verktyg för knappbeskrivningar för att förenkla anpassningen av knappbeskrivningar för visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 67470ec405806f44fdb483e857d222ad4ff05a45
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379178"
---
# <a name="tooltip-utils"></a>Verktyg för knappbeskrivningar
I den här artikeln får du hjälp att installera, importera och använda verktyg för knappbeskrivningar. Detta verktyg är användbart för alla anpassningar av knappverktyg i visuella Power BI-objekt.

## <a name="requirements"></a>Krav
Om du vill använda paketet bör du ha följande saker:
* [node.js](https://nodejs.org) (vi rekommenderar den senaste LTS-versionen)
* [npm](https://www.npmjs.com/) (den lägsta versionen som stöds är 3.0.0)
* Det anpassade visuella objektet som skapats med [verktyg för visuella PowerBI-objekt](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installation

Om du vill installera paketet kör du följande kommando i katalogen med ditt nuvarande visuella objekt:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Det här kommandot installerar paketet och lägger till ett paket som ett beroende till ```package.json```

## <a name="usage"></a>Användning

> I användarguiden beskrivs ett offentligt API för paketet. Du hittar en beskrivning och några exempel för varje offentligt gränssnitt i paketet.

Det här paketetinnehållet ger dig möjlighet att skapa `TooltipServiceWrapper` och metoder som hjälper dig att hantera knappbeskrivningsåtgärder. Det använder gränssnitt för knappbeskrivning – `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Det har också vissa metoder (hanterare av touchhändelser) som gäller mobil utveckling: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` är det enklaste sättet för att ändra knappbeskrivningar.

Denna modul har följande funktioner och gränssnitt:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [dölj](#itooltipservicewrapperhide)

* [Gränssnitt](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Touchhändelser](#touch-events)

### `createTooltipServiceWrapper`
Den här funktionen skapar en instans av ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService``` finns i [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Exempel**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Du kan se exempelkoden för det anpassade visuella objektet [här](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391).

### `ITooltipServiceWrapper`
Det här gränssnittet beskriver offentliga metoder för TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Den här metoden lägger till knappbeskrivningar i det aktuella valet.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Exempel**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Du kan se exempelkoden för det anpassade visuella objektet [här](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931).

Du bör också beakta följande exempel för anpassning av knappbeskrivningar i anpassade visuella Gantt-objekt [här](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Den här metoden döljer knappbeskrivningen.

```typescript
hide(): void;
```

**Exempel**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
De här gränssnitten används när TooltipServiceWrapper skapas och används. De nämndes även i exemplen från föregående avsnitt [här](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Nu kan verktyg för knappbeskrivningar hantera flera touchhändelser som är användbara för mobil utveckling.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Den här metoden returnerar touch start-händelsens namn.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Den här metoden returnerar touch start-händelsens namn.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Den här metoden returnerar aktuell touchStart-händelse relaterad till pekare eller inte.
