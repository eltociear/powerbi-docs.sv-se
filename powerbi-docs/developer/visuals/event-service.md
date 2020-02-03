---
title: Rendera händelser i visuella Power BI-objekt
description: Visuella Power BI-objekt kan meddela Power BI om att de är redo för export till Power Point eller PDF.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 873968a89a230171d8fecba81a7d528767ee7077
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819156"
---
# <a name="render-events-in-power-bi-visuals"></a>Rendera händelser i visuella Power BI-objekt

Det nya API:et består av tre metoder (`started`, `finished` eller `failed`) som ska anropas under renderingen.

När renderingen påbörjas anropar koden för visuella Power BI-objekt metoden `renderingStarted` för att indikera att renderingsprocessen har startat.

Om renderingen slutförs korrekt anropar koden för visuella Power BI-objekt omedelbart metoden `renderingFinished`, som meddelar lyssnarna (huvudsakligen *exportera till PDF* och *exportera till PowerPoint*) om att det visuella objektets bild är redo för export.

Om ett problem uppstår under processen förhindras det visuella Power BI-objektet från att renderas korrekt. I syfte att meddela lyssnarna om att renderingsprocessen inte har slutförts bör koden för visuella Power BI-objekt anropa metoden `renderingFailed`. Den här metoden tillhandahåller även en valfri sträng för att ange orsaken till felet.

## <a name="usage"></a>Användning

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Exempel: Det visuella objektet visar inga animeringar

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Exempel: Det visuella objektet visar animeringar

Om det visuella objektet har animeringar eller asynkrona funktioner för rendering ska metoden `renderingFinished` anropas efter animeringen eller inuti den asynkrona funktionen.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Återgivningshändelser för certifiering av visuellt objekt

Ett krav för certifiering av visuella objekt är det visuella objektets stöd för renderingshändelser. Mer information finns i [certifieringskrav](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements).
