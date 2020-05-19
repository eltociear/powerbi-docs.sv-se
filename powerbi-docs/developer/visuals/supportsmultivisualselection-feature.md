---
title: Funktionen supportsMultiVisualSelection
description: I den här artikeln beskrivs hur man använder funktionen supportsMultiVisualSelection och dess krav i virtuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272705"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Använd funktionen supportsMultiVisualSelection

Med funktionen `supportsMultiVisualSelection` kan du använda markering i flera visuella objekt i en rapport.

## <a name="example"></a>Exempel

I en rapport med mer än ett visuellt objekt väljer du två värden som du sedan använder för andra visuella objekt. I [detaljhandelsanalysexemplet](../../create-reports/sample-retail-analysis.md) kan du t.ex. välja **Fasions Direct** i ett visuellt objekt. Tryck på och välj **Jan** i ett annat visuellt objekt. I rapporten gäller dina val för de andra visuella objekt som har stöd för den här funktionen. Andra visuella objekt är nu begränsade till **Fashions Direct** och **Jan**.

## <a name="requirements"></a>Krav

Den här funktionen kräver API v3.2.0 eller senare.

Du kan inte använda den här funktionen för visuella bildobjekt. Du kan inte tillämpa den på vissa avancerade visuella objekt, som exempelvis nyckeldrivrutiner, dekompositionsträd, visuella frågor och svar-objekt, textrutor eller mätdiagram.

## <a name="usage"></a>Användning

Om du vill använda funktionen `supportsMultiVisualSelection`, så lägg till följande kod i det visuella objektets `capabilities.json`-fil.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Nästa steg

Mer information om Power BI-koncept finns i [Visuella objekt i Power BI](power-bi-visuals-concept.md).

Information om hur du provar Power BI-utveckling finns i [Utveckla ett visuellt objekt i Power BI](custom-visual-develop-tutorial.md).
