---
title: Aktivera synkronisering av utsnitt
description: Så lägger du till funktioner för synkronisering av utsnitt i visuella Power BI-objekt
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425032"
---
# <a name="sync-slicers"></a>Synkronisering av utsnitt

För att stödja [synkronisering av utsnitt](https://docs.microsoft.com/power-bi/desktop-slicers) måste ditt anpassade utsnitt använda API 1.13 eller senare.

Den andra nödvändiga aspekten är aktiverat alternativ i `capabilities.json` (se ett exempel nedan).

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

Efter ändringar i `capabilities.json` kan du se panelen med alternativ för synkronisering av utsnitt när du klickar på ditt anpassade visuella utsnittsobjekt.

> [!NOTE]
> Om utsnittet har fler än 1 fält (kategori eller mått) inaktiveras funktionen eftersom Synkronisering av utsnitt inte stöder flera fält.

![Panelen Synkronisera utsnitt](./media/sync-slicers-panel.png)

I panelen kan du se att utsnittets synlighet och filtrering kan tillämpas för flera rapportsidor.
