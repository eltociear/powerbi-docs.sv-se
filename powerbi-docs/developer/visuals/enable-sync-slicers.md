---
title: Aktivera funktionen Synkronisering av utsnitt i visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till funktionen Synkronisering av utsnitt i visuella Power BI-objekt.
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4d7b73a5d06f34fd197464d4444d0e19d6c1c026
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237207"
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

![Fönstret ”Synkronisera utsnitt”](./media/sync-slicers-panel.png)

I fönstret **Synkronisera utsnitt** kan du se att utsnittets synlighet och filtrering kan tillämpas på flera rapportsidor.
