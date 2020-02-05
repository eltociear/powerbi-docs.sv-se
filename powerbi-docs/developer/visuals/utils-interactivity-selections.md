---
title: Interaktivitetsverktyg för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till markeringar i visuella Power BI-objekt med hjälp av interaktivitetsverktyg
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818696"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Interaktivitetsverktyg för visuella Microsoft Power BI-objekt

InteractivityUtils är en uppsättning funktioner och klasser som förenklar implementeringen av korsmarkering och korsfiltrering i anpassade visuella Power BI-objekt.

## <a name="installation"></a>Installation

> [!NOTE]
> Om du fortsätter att använda den gamla versionen av powerbi-visuals-tools (versionsnummer tidigare än 3.x.x) installerar du den nya versionen av verktygen (3.x.x).

> [!IMPORTANT]
> Det finns bara stöd för de nya interaktivitetsverktygen i den senaste verktygsversionen. [Läs mer om hur du uppdaterar koden för visuella objekt så att de använder de senaste verktygen](migrate-to-new-tools.md)

Om du vill installera paketet kör du följande kommando i katalogen med ditt nuvarande anpassade visuella objekt:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

Från version 3.0 eller senare måste du också installera ```powerbi-models``` för att lösa beroenden.

```bash
npm install powerbi-models --save
```

Du måste importera den komponent som används i det visuella objektets källkod för att kunna använda interaktivitetsverktygen.

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

Det första steget när du använder interaktivitetsverktyg är att skapa en instans av interaktivitetsverktyget och spara objektet som en egenskap hos det visuella objektet

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
> BaseBehavior introducerades i [5.6.x-versionen för interaktivitetsverktygen](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Om du använder den äldre versionen kan du skapa beteendeklassen från exemplet nedan (klassen `BaseBehavior` är densamma):

Definiera gränssnittet för beteendeklassens alternativ:

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

Definiera en klass för `visual behavior`. Klassen ansvarar för att hantera mushändelserna `click` och `contextmenu`.
När användaren klickar på dataelement anropar det visuella objektet urvalshanteraren för att välja datapunkter. Om användaren klickar på bakgrundselementet i det visuella objektet anropas hanteraren för att rensa urvalet. Klassen har motsvarande metoder: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

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

Interaktivitetsverktygen anropar `bindEvents`-metoder som tilldelar funktioner till hanterare och lägger till anrop av `bindClick`, `bindClearCatcher` och `bindContextMenu` i metoden `bindEvents`:

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

Metoden `renderSelection` ansvarar för att uppdatera diagramelementens visuella status.

Exempel på implementering av metoden `renderSelection`:

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

Det sista steget är att skapa en instans av `visual behavior` och ett anrop av metoden `bind` för instansen av interaktivitetsverktyget:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` är D3-urvalsobjektet som motsvarar alla valbara element i det visuella objektet.

* `select(this.target)` är D3-urvalsobjektet som motsvarar DOM-huvudelementen i det visuella objektet.

* `this.categories` är datapunkter med element där gränssnittet är `VisualDataPoint` (eller `categories: VisualDataPoint[];`)

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

Nu är ditt visuella objekt redo att hantera urval.

## <a name="next-steps"></a>Nästa steg

* [Läs om hur du hanterar markeringar när du växlar mellan bokmärken](bookmarks-support.md#visuals-with-selection)

* [Läs om hur du lägger till snabbmenyn för datapunkter till visuella objekt](context-menu.md)

* [Läs om hur du använder markeringshanteraren för att lägga till markeringar i visuella Power BI-objekt](selection-api.md)
