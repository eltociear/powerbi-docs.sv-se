---
title: Visuella interaktioner i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du kontrollerar huruvida visuella Power BI-objekt ska tillåta visuella interaktioner.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1fb4f7d5950ab18a74dcacfdfef9c3ada90512c4
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378948"
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
