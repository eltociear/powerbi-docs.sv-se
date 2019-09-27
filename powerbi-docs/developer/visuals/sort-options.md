---
title: Sorteringsalternativ för visuella Power BI-objekt
description: I den här artikeln diskuteras standardbeteendet för sortering för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: a360f619428a01c4e7a30481374d042b8e368682
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193913"
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

![Sorteringsalternativ i snabbmenyn](./media/sorting.png)

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
