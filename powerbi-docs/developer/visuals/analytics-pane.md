---
title: Analytics-fönstret
description: Så här skapar du dynamiska referenslinjer i visuella objekt för Power BI
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425538"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Fönstret Analys i visuella objekt för Power BI

**Fönstret Analys** [introducerades för inbyggda visuella objekt](https://docs.microsoft.com/power-bi/desktop-analytics-pane) i november 2018.
Egenskaper för anpassade visuella objekt med API version 2.5.0 kan visas och hanteras i **fönstret Analys**.

![Fönstret Analys](./media/visualization-pane-analytics-tab.png)

Hanteringen sker på liknande sätt som när du [hanterar egenskaper i formateringsfönstret](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), genom att definiera ett objekt i det visuella objektets capabilities.json-fil. 

Skillnader:

1. Under definitionen för `object` lägger du till ett `objectCategory`-fält med värdet 2.

    > [!NOTE]
    > Fältet `objectCategory` är ett valfritt fält som introducerades i API 2.5.0. Det definierar vilken aspekt av det visuella objektet som objektet styr (1 = formatering, 2 = analys). ”Formatering” används för utseende och känsla, färger, axlar, etiketter med mera. ”Analys” används för prognoser, trendlinjer, referenslinjer och former med mera.
    >
    > `objectCategory` får standardvärdet ”formatering” om det utelämnas.

2. Objektet måste ha de två följande egenskaperna:
    1. `show` av typen bool, med standardvärdet false.
    2. `displayName` av typen text. Standardvärdet du väljer blir instansens inledande visningsnamn.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Alla andra egenskaper kan definieras på samma sätt som för formateringsobjekt. Objektuppräkningen utförs exakt på samma sätt som i **formateringsfönstret**.

***Kända begränsningar och problem***

  1. Det finns inget stöd för flera instanser ännu. Objekt kan inte ha en annan [väljare](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) statisk (det vill säga "selector": null) och anpassade visuella objekt kan inte ha flera användardefinierade instanser av ett kort.
  2. Egenskaper av typen `integer` visas inte korrekt. Som en tillfällig lösning kan du använda typen `numeric` i stället.

> [!NOTE]
> Fönstret Analys ska endast användas för objekt som lägger till ny information eller som sprider nytt ljus över den information som visas. Dynamiska referenslinjer illustrerar till exempel viktiga trender.
> Alla alternativ som styr utseendet och känslan för det visuella objektet, det vill säga formateringen, ska vara i formateringsfönstret.
