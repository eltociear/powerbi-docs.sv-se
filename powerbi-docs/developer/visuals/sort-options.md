---
title: Sortera
description: Standardsorteringsbeteende för det visuella Power BI-objektet.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f3d913e2bce34850dfae4c9486b2e43c78521a58
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424526"
---
# <a name="sorting-options"></a>Sorteringsalternativ

`Sorting` anger standardsorteringsbeteendet för det visuella objektet.
Funktionen kräver en av de parametrar som beskrivs nedan:

## <a name="default-sorting"></a>Standardsortering

Alternativet `default` är den enklaste varianten. Det gör det möjligt att sortera data som visas i avsnittet "DataMappings".
Det här alternativet möjliggör sortering av "DataMappings" av användaren och för att ange sorteringsriktningen.

```json
    "sorting": {
        "default": {   }
    }
```

![Sorteringsalternativ i snabbmenyn](./media/sorting.png)

## <a name="implicit-sorting"></a>Implicit sortering

`implicit` är sortering med matrisparameter – `clauses`, som beskriver sortering för varje dataroll.
`implicit` innebär att det visuella objektets användare inte kan ändra sorteringsordningen.
Power BI visar inte sorteringsalternativ i menyn för visuella objekt. Power BI kommer dock att sortera data enligt angivna inställningar.

`clauses`-parametrar kan innehålla flera objekt med två parametrar:

- `role` – bestämmer `DataMapping` för sortering.

- `direction` – bestämmer sorteringsriktningen (1 = stigande, 2 = fallande).

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

`custom` innebär att sorteringen hanteras av utvecklare i det visuella objektets kod.
