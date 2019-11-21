---
title: Interaktivitetsverktyg för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till markeringar i visuella Power BI-objekt med hjälp av interaktivitetsverktyg
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8a9218085b0da655d1ce4b3ece0b2666c4826c86
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061878"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Interaktivitetsverktyg för visuella Microsoft Power BI-objekt

InteractivityUtils är en uppsättning funktioner och klasser som förenklar implementeringen av korsmarkering och korsfiltrering i anpassade visuella Power BI-objekt.

## <a name="installation"></a>Installation

> [!NOTE]
> Om du fortsätter använda den gamla versionen av powerbi-visuals-tools (versionsnummer som är mindre än 3.x), installerar du den nya versionen av verktygen (3.x.x).

> [!IMPORTANT]
> De nya uppdateringarna av interaktivitetsverktygen stöder bara den senaste verktygsversionen. [Läs mer om hur du uppdaterar koden till de visuella objekten, som ska användas med de senaste verktygen](migrate-to-new-tools.md)

Om du vill installera paketet kör du följande kommando i katalogen med ditt nuvarande anpassade visuella objekt:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

Från version 3.0 eller senare måste du också installera ```powerbi-models``` för att lösa beroenden.

```bash
npm install powerbi-models --save
```

Du måste importera den komponent som krävs i det visuella objektets källkod för att kunna använda interaktivitetsverktygen.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Inkludera CSS-artefakter i det anpassade visuella objektet

Om du vill använda paketet med dina anpassade visuella objekt, bör du importera följande CSS-fil till `your.less`-filen:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Du får då följande filstruktur:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Du bör importera .css-filen som en .less-fil eftersom Power BI:s verktyg för visuella objekt omsluter de externa CSS-reglerna.

## <a name="usage"></a>Användning

### <a name="define-interface-for-data-points"></a>Definiera gränssnittet för datapunkter

Datapunkter innehåller vanligtvis markeringar och värden. Gränssnittet utökar `SelectableDataPoint`-gränssnittet. `SelectableDataPoint` innehåller redan egenskaper:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

Det första steget när interaktivitetsverktyg ska användas är att skapa en instans av interaktivitetsverktyg och spara objekt som en egenskap för det visuella objektet

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

Det andra steget är att utöka BaseBehavior-klassen:

> [!NOTE]
> BaseBehavior introducerades i [5.6.x-versionen för interaktivitetsverktygen](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Om du använder en tidigare version kan du skapa beteendeklassen från exemplet nedan (`BaseBehavior`-klassen är densamma):

Definiera gränssnittet för alternativen i beteendeklassen:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Definiera en klass för `visual behaviour`. Den klass som ansvarar för att hantera `click`, `contextmenu`-mushändelser.
När du klickar på dataelement anropar det visuella objektet markeringshanteraren för att välja datapunkter. Markeringen rensas om användaren klickar på bakgrundselementet i det visuella objektet. Klassen har motsvarande metoder: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

eller så kan du utöka `BaseBehavior`-klassen:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

För att hantera klick på element anropas `on`-metoden för D3-markeringsobjektet (även för elementsSelection och clearCatcherSelection):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Lägg till en liknande hanterare där `contextmenu`-händelsen anropar `showContextMenu`-metoden i markeringshanteraren:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Interaktivitetsverktygen anropar `bindEvents`-metoder som tilldelar funktioner till hanterare, samt lägger till anrop för `bindClick`, `bindClearCatcher` och `bindContextMenu` i `bindEvents`-metoden:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

`renderSelection`-metoden är ansvarig för att uppdatera elementens status i visuella objekt i diagrammet.

Exempel på implementering av `renderSelection`-metoden:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

Det sista steget är att skapa en instans av `visual behavior` och anropa en `bind`-metod för en interaktivitetsverktygsinstans:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` är D3-markeringsobjektet, vilket motsvarar alla valbara element i det visuella objektet.

* `select(this.target)` är D3-markeringsobjektet, vilket motsvarar DOm-huvudelement i det visuella objektet.

* `this.categories`-datapunkter med element, där gränssnittet är `VisualDataPoint` (eller `categories: VisualDataPoint[];`)

* `this.behavior` är en ny instans av `visual behavior`

  skapades i konstruktorn för det visuella objektet:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Nu är ditt visuella objekt redo att hantera markeringar.

## <a name="next-steps"></a>Nästa steg

* [Läs om hur du hanterar markeringar när du växlar mellan bokmärken](bookmarks-support.md#visuals-with-selection)

* [Läs om hur du lägger till snabbmenyn för datapunkter till visuella objekt](context-menu.md)

* [Läs om hur du använder markeringshanteraren för att lägga till markeringar i visuella Power BI-objekt](selection-api.md)
