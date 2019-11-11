---
title: Visuella interaktioner i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du kontrollerar huruvida visuella Power BI-objekt ska tillåta visuella interaktioner.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b8b1a1a59ee9fae5a1c248548a14c5f91438edc9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875516"
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
