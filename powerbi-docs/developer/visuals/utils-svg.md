---
title: Introduktion till användning av SVG-verktyg för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du använder SVG-verktyg för att förenkla SVG-manipulering för anpassade visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 612c253e53cdaec5819387548354595c8bd94fa0
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819317"
---
# <a name="svg-utils"></a>SVG-verktyg

SVGUtils är en uppsättning funktioner och klasser som förenklar SVG-manipulering för anpassade visuella Power BI-objekt

## <a name="installation"></a>Installation

Om du vill installera paketet kör du följande kommando i katalogen med ditt nuvarande visuella objekt:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

Modulen `CssConstants` tillhandahåller specialfunktionen och gränssnittet för arbete med klassväljare.

Modulen `powerbi.extensibility.utils.svg.CssConstants` har följande funktioner och gränssnitt:

## <a name="classandselector"></a>ClassAndSelector

Det här gränssnittet beskriver vanliga egenskaper hos klassväljaren.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Den här funktionen skapar en instans av ClassAndSelector med klassens tilldelade namn.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Exempel:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulering

`manipulation` innehåller vissa specialfunktioner för generering av strängar för användning med SVG-transformeringsegenskapen.

Modulen har följande funktioner:

### <a name="translate"></a>translate

Den här funktionen skapar en translate-sträng för användning med SVG-transformeringsegenskapen.

```typescript
function translate(x: number, y: number): string;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Den här funktionen skapar en translateX-sträng för användning med SVG-transformeringsegenskapen.

```typescript
function translateXWithPixels(x: number): string;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Den här funktionen skapar en translate-sträng för användning med SVG-transformeringsegenskapen.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Den här funktionen skapar en translate-rotate-sträng för användning med SVG-transformeringsegenskapen.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Den här funktionen skapar en scale-sträng för användning i en CSS-transformeringsegenskap.

```typescript
function scale(scale: number): string;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Den här funktionen skapar en transform-origin-sträng för användning i en CSS-transform-origin-egenskap.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Den här funktionen tvingar alla D3-övergångar att slutföras.

```typescript
function flushAllD3Transitions(): void;
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Den här funktionen parsar transformeringssträngen med värdet "translate(x,y)".

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Den här funktionen skapar en pil.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Exempel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

Modulen `Rect` innehåller vissa specialfunktioner för manipulering av rektanglar.

Modulen har följande funktioner:

### <a name="getoffset"></a>getOffset

Den här funktionen returnerar en förskjutning av rektangeln.

```typescript
function getOffset(rect: IRect): IPoint;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Den här funktionen returnerar rektangelns storlek.

```typescript
function getSize(rect: IRect): ISize;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Den här funktionen ändrar rektangelns storlek.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Den här funktionen returnerar en högerposition för rektangeln.

```typescript
function right(rect: IRect): number;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Den här funktionen returnerar en nedre position för rektangeln.

```typescript
function bottom(rect: IRect): number;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Den här funktionen returnerar en övre vänstra position för rektangeln.

```typescript
function topLeft(rect: IRect): IPoint;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Den här funktionen returnerar en övre högra position för rektangeln.

```typescript
function topRight(rect: IRect): IPoint;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Den här funktionen returnerar en nedre vänstra position för rektangeln.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Den här funktionen returnerar en nedre högra position för rektangeln.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Exempel

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Den här funktionen skapar en kopia av rektangeln.

```typescript
function clone(rect: IRect): IRect;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Den här funktionen konverterar rektangeln till en sträng.

```typescript
function toString(rect: IRect): string;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Den här funktionen tillämpar angiven förskjutning på rektangeln.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Den här funktionen lägger till den första rektangeln till den andra rektangeln.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Den här funktionen returnerar den punkt på rektangeln som är närmast den angivna punkten.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Den här funktionen jämför rektanglar och returnerar true om de är identiska.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Den här funktionen jämför rektanglar genom att beakta precisionen hos värdena.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Den här funktionen kontrollerar om rektangeln är tom.

```typescript
function isEmpty(rect: IRect): boolean;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Den här funktionen kontrollerar om rektangeln innehåller punkten.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Den här funktionen kontrollerar om rektanglar genomskär varandra.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Den här funktionen returnerar en genomskärning av rektanglar.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Den här funktionen kombinerar rektanglar.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Den här funktionen returnerar en mittpunkt för rektangeln.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Exempel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>pointer

Modulen `pointer` innehåller en specialfunktion för att hämta pekarens position.

Modulen har följande funktion:

### <a name="getcoordinates"></a>getCoordinates

Den här funktionen returnerar pekarens position.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Exempel:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
