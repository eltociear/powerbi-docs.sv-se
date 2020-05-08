---
title: Interaktivitetsverktyg för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till markeringar i visuella Power BI-objekt med hjälp av interaktivitetsverktyg
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379270"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Interaktivitetsverktyg för visuella Power BI-objekt

Interaktivitetshjälpmedlen (`InteractivityUtils`) är en uppsättning funktioner och klasser som du kan använda för att förenkla implementeringen av korsmarkering och korsfiltrering.

> [!NOTE]
> Det finns bara stöd för de nya interaktivitetshjälpmedlen i den senaste verktygsversionen (3.x.x. och senare).

## <a name="installation"></a>Installation

1. Om du vill installera paketet så kör följande kommando i katalogen med ditt aktuella visuella Power BI-projekt.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Om du använder version 3.0 eller senare eller verktyget, så lös beroenden genom att installera `powerbi-models`.

    ```bash
    npm install powerbi-models --save
    ```

3. Importera den nödvändiga komponenten i det visuella Power BI-objektets källkod om du vill använda interaktivitetshjälpmedlen.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Inklusive CSS-filerna

Om du vill använda paketet med ditt visuella Power BI-objekt, så importera följande CSS-fil till din `.less`-fil.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importera CSS-filen som en `.less`-fil eftersom verktyget för visuella Power BI-objekt radbryter externa CSS-regler.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint-egenskaper

Datapunkter innehåller vanligtvis markeringar och värden. Gränssnittet utökar `SelectableDataPoint`-gränssnittet.

`SelectableDataPoint` innehåller redan egenskaper enligt beskrivningen nedan.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definiera ett gränssnitt för datapunkter

1. Skapa en instans av interaktivitetshjälpmedel och spara objektet som en egenskap för det visuella objektet

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

2. Utöka grundbeteendeklassen.

    > [!NOTE]
    > `BaseBehavior` introducerades i [5.6.x-versionen av interaktivitetshjälpmedlen](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Om du använder den äldre versionen kan du skapa en beteendeklass från exemplet nedan.

3. Definiera gränssnittet för beteendeklassalternativen.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Definiera en klass för `visual behavior`. Eller utöka `BaseBehavior`-klassen.

    **Definiera en klass för `visual behavior`**

    Klassen ansvarar för att hantera mushändelserna `click` och `contextmenu`.

    När användaren klickar på dataelement anropar det visuella objektet urvalshanteraren så att datapunkter kan väljas. Om användaren klickar på bakgrundselementet i det visuella objektet anropas hanteraren för att rensa urvalet.

    Klassen har följande motsvarande metoder:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **Utöka `BaseBehavior`-klassen**

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

5. Om du vill hantera klickande på element, så anropa *D3*-urvalsobjektets `on`-metod. Detta gäller även för `elementsSelection` och `clearCatcherSelection`.

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

6. Lägg till en liknande hanterare där `contextmenu`-händelsen, så att urvalshanterarens `showContextMenu`-metoden anropas.

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

7. Om du vill tilldela hanterare funktioner, så kan interaktivitetshjälpmedlen anropa `bindEvents`-metoden. Lägg till följande anrop i metoden `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. Metoden `renderSelection` ansvarar för att uppdatera diagramelementens visuella status. Detta är en exempelimplementering av `renderSelection`.

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

9. Det sista steget är att skapa en instans av `visual behavior` och anropa `bind`-metoden för interaktivitetsverktygsinstansen.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` är *d3*-urvalsobjektet som motsvarar alla valbara element i det visuella objektet.
    * `select(this.target)` är *d3*-urvalsobjektet som representerar det visuella objektets DOM-huvudelement.
    * `this.categories` är datapunkter med element där gränssnittet är `VisualDataPoint` eller `categories: VisualDataPoint[];`.
    * `this.behavior` är en ny instans av `visual behavior` som skapats i det visuella objektets konstruktor, så som visas nedan.

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
## <a name="next-steps"></a>Nästa steg

* [Läs om hur du hanterar markeringar när du växlar mellan bokmärken](bookmarks-support.md#visuals-with-selection)

* [Läs om hur du lägger till snabbmenyn för visuella datapunkter](context-menu.md)

* [Läs om hur du använder markeringshanteraren för att lägga till markeringar i visuella Power BI-objekt](selection-api.md)
