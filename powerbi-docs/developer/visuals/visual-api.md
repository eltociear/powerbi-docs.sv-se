---
title: Visual API
description: I den här artikeln beskrivs hur du använder Visual API i visuella objekt för Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302976"
---
# <a name="visual-api"></a>Visual API
Alla visuella objekt börjar med en klass som implementerar `IVisual`-gränssnittet. Du kan ge klassen vilket namn du vill så länge det finns exakt en klass som implementerar `IVisual`-gränssnittet.

> [!NOTE]
> Den visuella klassens namn måste matcha vad som definieras i filen *pbiviz.json*.

Visa exemplet med den visuella klassen med följande metoder som ska implementeras:

* `constructor`, en standardkonstruktor som används för att initiera det visuella objektets tillstånd
* `update`, som används för att uppdatera det visuella objektets data
* `enumerateObjectInstances`, som används för att returnera objekt som ska fylla egenskapsfönstret (formateringsalternativ), där du kan ändra dem efter behov
* `destroy`, en standarddestruktor för rensning

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>konstruktor

Den visuella klassens konstruktor anropas när det visuella objektet instansieras. Den kan användas för alla konfigurationsåtgärder som behövs för det visuella objektet.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, en referens till det DOM-element som kommer att innehålla det visuella objekten
* `host: IVisualHost`, en samling egenskaper och tjänster som kan användas för att interagera med den visuella värden (Power BI)

   `IVisualHost` innehåller följande tjänster:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, genererar och lagrar metadata för valbara objekt i det visuella objektet
   * `createSelectionManager`, skapar den kommunikationsbrygga som används för att meddela visualiseringens värd om ändringar i urvalsläget. Se [Urvals-API](./selection-api.md).
   * `createLocalizationManager`, genererar en hanterare som hjälper till med [lokaliseringen](./localization.md)
   * `allowInteractions: boolean`, en boolesk flagga som anger om det visuella objektet ska vara interaktivt eller inte
   * `applyJsonFilter`, använder specifika filtertyper. Se [Filter-API](./filter-api.md)
   * `persistProperties`, tillåter användare att spara egenskaper och spara dem tillsammans med den visuella definitionen, så att de är tillgängliga vid nästa omladdning
   * `eventService`, returnerar en [händelsetjänst](./event-service.md) som stöd för **återgivnings**händelser
   * `storageService`, returnerar en tjänst som hjälper dig att använda [lokala lagring](./local-storage.md) i det visuella objektet
   * `authenticationService`, genererar en tjänst som hjälper dig med användarautentisering
   * `tooltipService`, returnerar en [knappbeskrivningstjänst](./add-tooltips.md) som hjälper dig att använda knappbeskrivningar i det visuella objektet
   * `launchUrl`, hjälper till att [starta en URL](./launch-url.md) på nästa flik
   * `locale`, returnerar en lokal sträng, se [Lokalisering](./localization.md)
   * `instanceId`, returnerar en sträng som identifierar den aktuella visuella instansen
   * `colorPalette`, returnerar den colorPalette som krävs för att använda färger på dina data
   * `fetchMoreData`, stöder användning av mer data än standardgränsen (1 000 rader)
   * `switchFocusModeState`, hjälper till att ändra fokuslägetillstånd

## <a name="update"></a>update

Alla visuella objekt måste implementera en offentlig uppdateringsmetod som anropas när det sker en ändring i data- eller värdmiljön.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, mått för det visningsområde inom vilket det visuella objektet ska återges
* `dataViews: DataView[]`, det datavyobjekt som innehåller alla de data som behövs för att återge ditt visuella objekt (som normalt använder den kategoriska egenskapen under DataView)
* `type: VisualUpdateType`, flaggor som indikerar den här uppdateringens typ(er) (**Data** | **Andra storlek** | **ViewMode** | **Format** | **ResizeEnd**)
* `viewMode: ViewMode`, flaggor som indikerar det visuella objektets visningsläge (**Visa** | **Redigera** | **InFocusEdit**)
* `editMode: EditMode`, flagga som indikerar det visuella objektets redigeringsläge (**Standard** | **Avancerat**) (om det visuella objektet stöder **AdvancedEditMode** bör det endast återge sina avancerade gränssnittskontroller när **editMode** är inställt på **Advanced**, se [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`, flagga som indikerar typen av dataändring (**Skapa** | **Lägga till**)
* `jsonFilters?: IFilter[]`, en samling med tillämpade json-filter
* `isInFocus?: boolean`, flagga som indikerar om det visuella objektet är i fokusläge eller inte
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Den här metoden anropas för alla objekt som anges i funktionerna. Med hjälp av alternativen (för närvarande bara namnet) returnerar du ett `VisualObjectInstanceEnumeration` med information om hur den här egenskapen ska visas.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, objektets namn

## <a name="destroy-optional"></a>förstöra `optional`

Förstörandefunktionen anropas när det visuella objektet är inaktiverat och kan användas för att rensa uppgifter, som t.ex. att ta bort händelselyssnare.

``` typescript
public destroy(): void
```

> [!Note]
> Power BI brukar inte anropa `destroy` eftersom det går snabbare att ta bort hela IFrame som innehåller det visuella objektet.
