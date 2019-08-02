---
title: Återgivningshändelser
description: Visuella objekt för Power BI kan meddela Power BI att de är redo att exporteras till Power Point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425101"
---
# <a name="event-service"></a>Händelsetjänst

Det nya API:et består av tre metoder (started, finished eller failed) som ska anropas under återgivningen.

När återgivningen startar anropar den anpassade visuella koden metoden renderingStarted för att indikera att återgivningsprocessen har startat.

Om återgivningen har slutförts anropar den anpassade visuella koden omedelbart metoden `renderingFinished` som meddelar lyssnarna (**primärt "Exportera till PDF" och "Exportera till PowerPoint"** ) att det visuella objektets bild är klar.

Om ett problem uppstår under återgivningsprocessen, som gör att den anpassade virtuella koden inte kan utföras, ska den anpassade visuella koden anropa metoden `renderingFailed` för att meddela lyssnaren att återgivningsprocessen inte har slutförts. Den här metoden tillhandahåller också en valfri sträng för orsaken till felet.

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
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Enkelt exempel. Det visuella objektet har ingen animering vid återgivning

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

### <a name="sample-the-visual-with-animation"></a>Exempel. Det visuella objektet med animering

Om det visuella objektet har animeringar eller asynkrona funktioner för återgivning ska metoden `renderingFinished` anropas efter animeringen eller inuti den asynkrona funktionen.

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
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Återgivningshändelser för certifiering av visuellt objekt

Stöd för återgivningshändelser av det visuella objektet är ett av kraven för certifiering av visuella objekt. Läs mer om [certifieringskrav](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
