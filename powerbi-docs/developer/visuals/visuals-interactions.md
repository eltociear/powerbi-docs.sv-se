---
title: Visuella interaktioner i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du kontrollerar huruvida visuella Power BI-objekt ska tillåta visuella interaktioner.
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f2fb2d451deb63b5e9c08472654e28d0e1a469db
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236616"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Visuella interaktioner i visuella Power BI-objekt

Visuella objekt kan fråga värdet för flaggan `allowInteractions`, som anger huruvida det visuella objektet ska tillåta visuella interaktioner. Till exempel är visuella objekt interaktiva under rapportvisning eller -redigering, men inte interaktiva när de visas på en instrumentpanel. Dessa interaktioner är *klicka*, *panorera*, *zooma*, *välja* och andra. 

> [!NOTE]
> Du bör aktivera knappbeskrivningar i alla scenarier, oavsett vilken flagga som anges.

Flaggan `allowInteractions` skickas som boolesk vid initieringen av det visuella objektet, som en medlem i IVisualHost-gränssnittet.

I alla Power BI-scenarier som kräver att de visuella objekten inte är interaktiva (till exempel instrumentpanelsrutor) anges flaggan `allowInteractions` till `false`. I annat fall (till exempel för rapport) anges `allowInteractions` till `true`.

Mer information finns på [lagringsplatsen för SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
