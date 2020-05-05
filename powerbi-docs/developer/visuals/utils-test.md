---
title: Introduktion till användning av testverktyg i visuella Power BI-objekt
description: Den här artikeln beskriver hur du använder testverktyg för att förenkla användning av simuleringar och specifika metoder i enhetstestning för visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196616"
---
# <a name="power-bi-visuals-test-utils"></a>Testverktyg för visuella Power BI-objekt

Den här artikeln hjälper dig att installera, importera och använda visuella Power BI-objekt. Dessa testverktyg kan användas för enhetstestning och innehåller simuleringar och metoder för element som datavyer, markeringar och färgscheman.

## <a name="requirements"></a>Krav

Om du vill använda det här paketet måste du installera följande:

* [node.js](https://nodejs.org), vi rekommenderar att du använder LTS-versionen
* [npm](https://www.npmjs.com/), version 3.0.0 eller senare
* Paketet [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## <a name="installation"></a>Installation

Om du vill installera testverktyg och lägga till dess beroende i *package.json* kör du följande kommando från katalogen för visuella Power BI-objekt:

```bash
npm install powerbi-visuals-utils-testutils --save
```

I följande avsnitt finns beskrivningar och exempel på testverktygets offentliga API.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Används av **VisualBuilder** i enhetstest med de metoder som används oftast, `build`, `update` och `updateRenderTimeout`. 

Metoden `build` returnerar en skapad instans av det visuella objektet.

Metoderna `enumerateObjectInstances` och `updateEnumerateObjectInstancesRenderTimeout` krävs för att kontrollera ändringar i bucket- och formateringsalternativen.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Fler exempel finns i avsnittet om [att skriva VisualBuilderBase-enhetstester](./unit-tests-introduction.md#create-a-visual-instance-builder) och om ett [verkligt VisualBuilderBase-användningsscenario](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Den här modulen används av **TestDataViewBuilder** och tillhandahåller en **CategoricalDataViewBuilder**-klass som används i `createCategoricalDataViewBuilder`-metoden. Den anger också gränssnitt och metoder som krävs för att arbeta med en simulerad **DataView** i enhetstest.

* `withValues` lägger till kolumner med statiska serier och `withGroupedValues` lägger till kolumner med dynamiska serier

  Använd inte både dynamiska serier och statiska serier i ett visuellt **DataViewCategorical**. Du kan bara använda båda i **DataViewCategorical**-frågan, där **DataViewTransform** förväntas dela upp dem i separata visuella **DataViewCategorical**-objekt.

* `build` returnerar DataView med metadata och DataViewCategorical

  `build` returnerar **odefinierad** om kombinationen av parametrar är ogiltig, till exempel både dynamisk och statisk serie när du skapar det visuella **DataView**-objektet.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Används för att skapa **VisualData** i enhetstest. När data placeras i datafältsbuckets skapar Power BI ett kategoriskt **DataView**-objekt baserat på dessa data. **TestDataViewBuilder** hjälper till att simulera skapande av kategoriska **DataView**-objekt.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Nedan visas de vanligaste gränssnitten när du skapar ett `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Fler exempel finns i avsnittet om [att skriva TestDataViewBuilder-enhetstester](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) och om ett [verkligt TestDataViewBuilder-användningsscenario](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Simuleringar

### <a name="mockivisualhost"></a>MockIVisualHost

Implementerar **IVisualHost** för att testa visuella Power BI-objekt utan externa beroenden, till exempel Power BI-ramverket.

Användbara metoder är `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` och get-egenskaper.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` skapar och returnerar en instans av **IVisualHost**, nämligen **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Exempel
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** är en falsk implementering av **IVisualHost** och bör endast användas med enhetstest.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementerar **IColorPalette** för att testa visuella Power BI-objekt utan externa beroenden, till exempel Power BI-ramverket.

**MockIColorPalette** ger användbara egenskaper för att kontrollera färgschema eller högkontrastläge i enhetstest.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` skapar och returnerar en instans av **IColorPalette**, nämligen **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Exempel
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** är en falsk implementering av **IColorPalette** och bör endast användas med enhetstest.

### <a name="mockiselectionid"></a>MockISelectionId

Implementerar **ISelectionId** för att testa visuella Power BI-objekt utan externa beroenden, till exempel Power BI-ramverket.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` skapar och returnerar en instans av **ISelectionId**, nämligen **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Exempel
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** är en falsk implementering av **ISelectionId** och bör endast användas med enhetstest.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementerar **ISelectionIdBuilder** för att testa visuella Power BI-objekt utan externa beroenden, till exempel Power BI-ramverket. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` skapar och returnerar en instans av **ISelectionIdBuilder**, nämligen **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Exempel
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** är en falsk implementering av **ISelectionIdBuilder** och bör endast användas med enhetstest.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementerar **ISelectionManager** för att testa visuella Power BI-objekt utan externa beroenden, till exempel Power BI-ramverket. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` skapar och returnerar en instans av **ISelectionManager**, nämligen **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Exempel
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** är en falsk implementering av **ISelectionManager** och bör endast användas med enhetstest.

### <a name="mockilocale"></a>MockILocale

  Ställer in nationella inställningar och ändrar dem efter behov under enhetstestningsprocessen.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` skapar och returnerar en instans av **MockILocale**
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simulerar `TooltipService` och anropar det efter behov under enhetstestningsprocessen.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` skapar och returnerar en instans av **MockITooltipService**
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` skapar och returnerar en instans av **MockIAllowInteractions**
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Tillhandahåller grundläggande funktioner för **LocalizationManager** som behövs för enhetstestning.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` skapar och returnerar en instans av **ILocalizationManager**, nämligen **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Exempel
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simulerar **TelemetryService**-användning.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Skapa `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simulerar arbetet för **AuthenticationService** genom att tillhandahålla en simulerad AAD-token.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` skapar och returnerar en instans av **IAuthenticationService**, nämligen **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Gör att du kan använda **ILocalVisualStorageService** med samma beteende som **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` skapar och returnerar en instans av **ILocalVisualStorageService**, nämligen **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` skapar och returnerar en instans av **IVisualEventService**, nämligen **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Verktyg

Verktyg innehåller hjälpmetoder för enhetstestning av visuella Power BI-objekt, inklusive hjälpfunktioner som rör färger, tal och händelser.

- `renderTimeout` returnerar timeout
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` hjälper till att ställa in fixtur i enhetstester
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Exempel
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Färgrelaterade hjälpmetoder

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Returnerar följande struktur:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` jämför **RgbColor**-objekt som har parsats från indatasträngar
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` tolkar färg från indatasträngen och returnerar den i angiven **RgbColor** för gränssnittet
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Talrelaterade hjälpmetoder

- `getRandomNumbers` genererar ett slumpmässigt tal med hjälp av min- och maxvärden. Du kan ange `exceptionList` och tillhandahålla en funktion för resultatändring.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` innehåller en matris med slumpmässiga tal som genereras av metoden `getRandomNumber` med angivna min- och maxvärden
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Händelserelaterade hjälpmetoder
Följande metoder är skrivna för händelsesimulering för webbsidor i enhetstester.

- `clickElement` simulerar ett klick på det angivna elementet
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` returnerar ett **Touch**-objekt som hjälper till att simulera en touchhändelse
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` returnerar en lista med simulerade **Touch**-händelser
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` returnerar **MouseEvent**
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` skapar och returnerar **MouseEvent**
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>D3-händelserelaterade hjälpmetoder

Följande metoder används för att simulera D3-händelser i enhetstester.

- `flushAllD3Transitions` tvingar alla D3-övergångar att slutföras

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalt utförs nollfördröjningsövergångar efter en momentan fördröjning (<10 ms), men detta kan orsaka ett kort flimmer om webbläsaren återger sidan två gånger. En gång i slutet av den första händelseloopen och sedan igen omedelbart på det första återanropet.
  >
  > Dessa flimmer är mer märkbara i IE och med ett stort antal webbvisningar och rekommenderas inte för iOS.
  > 
  > Genom att tömma timerkön i slutet av den första händelseloopen kan du köra eventuella nollfördröjningsövergångar omedelbart och undvika flimmer.

Följande metoder ingår också:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Hjälpgränssnitt
Följande gränssnitt och uppräkningar används i hjälpfunktionen.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Nästa steg

Om du vill skriva enhetstest för WebPack-baserade visuella Power BI-objekt, och enhetstest med `karma` och `jasmine`, kan du till exempel gå till [Självstudiekurs: Lägga till enhetstester för projekt med visuella Power BI-objekt](./unit-tests-introduction.md).
