---
title: Aktivera funktionen Synkronisering av utsnitt i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till funktionen Synkronisering av utsnitt i visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 345971384fff0e0b215d2898ee1684f4a5bac486
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114323"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Synkronisering av utsnitt i visuella Power BI-objekt

För att stödja funktionen [Synkronisering av utsnitt](https://docs.microsoft.com/power-bi/desktop-slicers) måste ditt anpassade utsnittsobjekt använda API-version 1.13 eller senare.

Dessutom behöver du aktivera alternativet i filen *capabilities.json* enligt följande kod:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

När du har uppdaterat filen *capabilities.json* kan du visa fönstret med alternativ för **Synkronisera utsnitt** när du väljer det anpassade visuella utsnittsobjektet.

> [!NOTE]
> Funktionen Synkronisering av utsnitt stöder inte fler än ett fält. Om utsnittet har fler än ett fält (**Kategori** eller **Mått**) inaktiveras funktionen.

![Fönstret ”Synkronisera utsnitt”](media/enable-sync-slicers/sync-slicers-panel.png)

I fönstret **Synkronisera utsnitt** kan du se att utsnittets synlighet och filtrering kan tillämpas på flera rapportsidor.
