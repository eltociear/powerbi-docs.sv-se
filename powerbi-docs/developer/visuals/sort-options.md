---
title: Sorteringsalternativ för visuella Power BI-objekt
description: I den här artikeln diskuteras standardbeteendet för sortering för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 3cb8f5af63960667dc46cab1d818ba48943fd582
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378094"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Sorteringsalternativ för visuella Power BI-objekt

I den här artikeln beskrivs hur *sorteringsalternativ* anger sorteringsbeteendet för visuella Power BI-objekt. 

Sorteringsfunktionen kräver en av följande parametrar.

## <a name="default-sorting"></a>Standardsortering

Alternativet `default` är den enklaste varianten. Det gör det möjligt att sortera data som visas i avsnittet "DataMappings". Det här alternativet möjliggör sortering av datamappningarna av användaren anger sorteringsriktningen.

```json
    "sorting": {
        "default": {   }
    }
```

![Sorteringsalternativ i snabbmenyn](media/sort-options/sorting.png)

## <a name="implicit-sorting"></a>Implicit sortering

Implicit sortering är sortering med matrisparametern `clauses`, som beskriver sortering för varje dataroll. `implicit` innebär att det visuella objektets användare inte kan ändra sorteringsordningen. Power BI visar inte sorteringsalternativ i menyn för det visuella objektet. Power BI sorterar dock data enligt angivna inställningar.

`clauses`-parametrar kan innehålla flera objekt med två parametrar:

- `role`: Bestämmer `DataMapping` för sortering
- `direction`: Bestämmer sorteringsriktningen (1 = stigande, 2 = fallande)

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Anpassad sortering

Anpassad sortering innebär att sorteringen hanteras av utvecklaren i det visuella objektets kod.
