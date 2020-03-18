---
title: Introduktion till användning av typverktyg för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du använder SVG-verktyg för att utöka de grundläggande typerna för visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 5a3cfb7ea9c9f398193b45652aa43c6b83c8f70b
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378005"
---
# <a name="type-utils"></a>Typverktyg

TypeUtils är en uppsättning funktioner och klasser som utökar de grundläggande typerna för visuella Power BI-objekt.

## <a name="installation"></a>Installation

Om du vill installera paketet kör du följande kommando i katalogen med ditt nuvarande anpassade visuella objekt:

npm install powerbi-visuals-utils-typeutils --save Det här kommandot installerar paketet och lägger till ett paket som ett beroende till filen package.json

## <a name="double"></a>Double

`Double` ger möjligheter att manipulera precisionen för talen.

Modulen har följande funktioner:

### <a name="pow10"></a>pow10

Den här funktionen returnerar en tiopotens.

```typescript
function pow10(exp: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Den här funktionen returnerar en logaritm med basen tio för talet.

```typescript
function log10(val: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Den här funktionen returnerar en tiopotens som representerar talets precision.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Den här funktionen kontrollerar om en förändring mellan två tal är mindre än den angivna precisionen.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Den här funktionen kontrollerar om det första värdet är mindre än det andra värdet.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Den här funktionen kontrollerar om det första värdet är mindre än eller lika med det andra värdet.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Den här funktionen kontrollerar om det första värdet är större än det andra värdet.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Den här funktionen kontrollerar om det första värdet är större än eller lika med det andra värdet.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Den här funktionen ger golvet för talet med den angivna precisionen.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Den här funktionen `ceils` talet med den angivna precisionen.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Den här funktionen ger golvet för talet till den angivna precisionen.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Den här funktionen `ceils` talet till den angivna precisionen.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Den här funktionen avrundar talet till den angivna precisionen.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Den här funktionen returnerar ett tal som är mellan min och max.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Den här funktionen avrundar talet.

```typescript
function round(x: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Den här funktionen tar bort decimalbruset.

```typescript
function removeDecimalNoise(value: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Den här funktionen kontrollerar om talet är ett heltal.

```typescript
function isInteger(value: number): boolean;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Den här funktionen ökar antalet med det angivna talet och returnerar det avrundade talet.

```typescript
function toIncrement(value: number, increment: number): number;
```

Exempel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototyp

`Prototype` ger möjligheter att ärva objekt.

Modulen har följande funktioner:

## <a name="inherit"></a>inherit

Den här funktionen returnerar ett nytt objekt med det tillhandahållna objektet som prototyp.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Exempel:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Den här funktionen returnerar ett nytt objekt med det tillhandahållna objektet som prototyp om, och endast om, prototypen inte har angetts.

```typescript
function inheritSingle<T>(obj: T): T;
```

Exempel:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` ger möjlighet att konvertera bildpunkter till punkter och pekare till bildpunkter.

Modulen har följande funktioner:

## <a name="tostring"></a>toString

Den här funktionen konverterar bildpunktsvärdet till en sträng.

```typescript
function toString(px: number): string;
```

Exempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Den här funktionen konverterar det angivna punktvärdet till bildpunktsvärdet och returnerar strängtolkningen.

```typescript
function fromPoint(pt: number): string;
```

Exempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Den här funktionen konverterar det angivna punktvärdet till bildpunktsvärdet.

```typescript
function fromPointToPixel(pt: number): number;
```

Exempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Den här funktionen konverterar bildpunktsvärdet till punktvärdet.

```typescript
function toPoint(px: number): number;
```

Exempel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
