---
title: Funktionen supportsKeyboardFocus
description: Den här artikeln beskriver hur du använder supportsKeyboardFocus-funktionen i virtuella Power BI-objekt och dess krav.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: c8cf0f4e896b8a44764d1c363c597182f55d30b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276523"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>Använd funktionen supportsKeyboardFocus

I den här artikeln beskrivs hur du kan använda `supportsKeyboardFocus`-funktionen i virtuella objekt i Power BI.
Med funktionen `supportsKeyboardFocus` kan du navigera efter det visuella objektets datapunkter med hjälp av enbart tangentbordet.

Mer information om tangentbordsnavigering för visuella objekt finns i [Tangentbordsnavigering](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Exempel

Öppna ett visuellt objekt som använder `supportsKeyboardFocus`-funktionen. Välj en datapunkt i det visuella objektet och välj en flik. Fokus flyttas till nästa datapunkt varje gång du använder tabbtangenten. Välj den markerade datapunkten med Retur.

![Exempel på stöd för tangentbordsfokus](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Krav

Den här funktionen kräver API v-2.1.0 eller senare.

Den här funktionen kan användas för alla visuella objekt förutom visuella bilder.

## <a name="usage"></a>Användning

Om du vill använda funktionen `supportsKeyboardFocus`, så lägg till följande kod i det visuella objektets *capability.json*-fil.
Den här funktionen gör det möjligt för det visuella objektet att ta emot fokus genom tangentbordsnavigering.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Nästa steg

Mer information om hjälpmedelsfunktioner finns i [Utforma Power BI-rapporter för tillgänglighet](../../create-reports/desktop-accessibility-creating-reports.md).

Information om hur du provar Power BI-utveckling finns i [Utveckla ett visuellt objekt i Power BI](custom-visual-develop-tutorial.md).
