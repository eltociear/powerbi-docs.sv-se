---
title: Interaktioner med visuella objekt
description: Så kontrollerar du att visuella Power BI-objekt ska tillåta visuella interaktioner
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424503"
---
# <a name="visuals-interactions"></a>Interaktioner med visuella objekt

Visuella objekt kan fråga värdet för flaggan "allowInteractions", som anger huruvida det visuella objektet ska tillåta visuella interaktioner.
Till exempel är visuella objekt interaktiva under rapportvisning eller -redigering, men inte interaktiva när de visas på en instrumentpanel.
Dessa interaktioner är klicka, panorera, zooma, välja och andra.
Observera att knappbeskrivningar ska aktiveras i alla scenarier, oavsett hur den här flaggan är inställd.

Flaggan "allowInteractions" skickas som boolesk vid initieringen av det visuella objektet som en medlem i IVisualHost-gränssnittet.

I ett Power BI scenario som kräver att visuella objekt inte är interaktiva (till exempel instrumentpanelsrutor) anges flaggan "allowInteractions" till falskt.
I övriga fall (till exempel för rapporter) anges "allowInteractions" till sant.

Mer information finns på [lagringsplatsen för SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

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
