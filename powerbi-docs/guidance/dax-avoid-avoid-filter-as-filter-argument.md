---
title: 'DAX: Undvik att använda FILTER som ett filterargument'
description: Vägledning om att använda funktionen FILTER som filterargument.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 935b453dabeaa731a218175526ddddeb980a2b92
ms.sourcegitcommit: b09de56e971b8844a3771413d1f56d49b31baaaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692469"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Undvik att använda FILTER som ett filterargument

Som datamodellerare skriver du ofta DAX-uttryck som måste utvärderas i en ändrad filterkontext. Du kan till exempel skriva en måttdefinition för att beräkna försäljningen för ”produkter med hög marginal”. Vi beskriver den här beräkningen senare i artikeln.

> [!NOTE]
> Den här artikeln är särskilt relevant för modellberäkningar där filter används till att importera tabeller.

DAX-funktionerna [CALCULATE](/dax/calculate-function-dax) och [CALCULATETABLE](/dax/calculatetable-function-dax) är viktiga och användbara funktioner. De gör att du kan skriva beräkningar som tar bort eller lägger till filter, eller ändrar relationsvägar. Du gör det genom att skicka filterargument som antingen är booleska uttryck, tabelluttryck eller särskilda filterfunktioner. I den här artikeln tar vi bara upp booleska uttryck och tabelluttryck.

Tänk dig följande måttdefinition, som beräknar försäljningen av röda produkter med hjälp av ett tabelluttryck. Den ersätter alla filter som tillämpas på tabellen **Product**.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

Funktionen CALCULATE tar emot ett tabelluttryck som returneras av DAX-funktionen [FILTER](/dax/filter-function-dax), som utvärderar filteruttrycket för varje rad i tabellen **Product**. Det här ger rätt resultat – försäljningsresultatet för röda produkter. Du kan dock göra det här mycket mer effektivt genom att använda ett booleskt uttryck.

Här är en bättre måttdefinition som använder ett booleskt uttryck i stället för tabelluttrycket.

```dax
Red Sales =
CALCULATE(
    [Sales],
    'Product'[Color] = "Red"
)
```

Vi rekommenderar att du skickar filterargument som booleska uttryck när du kan. Det beror på att tabeller för modellimport är kolumnlager i minnet. De är uttryckligen optimerade för att effektivt filtrera kolumner på det här sättet.

Det finns dock begränsningar som gäller när booleska uttryck används som filter argument. Här är några av dem:

- de kan inte jämföra kolumner med andra kolumner
- de kan inte referera till ett mått
- de kan inte använda kapslade CALCULATE-funktioner
- de kan inte använda funktioner som skannar eller returnerar en tabell.

Det här innebär att du måste använda tabelluttryck för mer komplicerade filtreringsbehov.

Tänk dig nu en annan måttdefinition.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Definitionen av en _produkt med hög marginal_ är en som har ett försäljningspris högre än dubbla standardkostnaden. I det här exemplet måste du använda funktionen FILTER. Det beror på att filteruttrycket är för komplicerat för ett booleskt uttryck.

Här är ett exempel till. Den här gången ska du beräkna försäljningen, men bara för de månader som har uppnått vinst.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

I det här exemplet måste du också använda funktionen FILTER. Det beror på att du måste utvärdera måttet **Profit** för att eliminera de månader som inte uppnådde någon en vinst. Du kan inte använda mått i ett booleskt uttryck när det används som filterargument.

## <a name="recommendations"></a>Rekommendationer

Du får bästa prestanda om du använder booleska uttryck som filterargument när det är möjligt.

Därför ska du bara använda funktionen FILTER när du måste. Du kan använda den till att filtrera komplexa kolumnjämförelser. Här är några exempel på vad sådana jämförelser kan innehålla:

- Mått
- Andra kolumner
- DAX-funktionen [OR](/dax/or-function-dax) eller den logiska operatorn OR (||)

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- [Filterfunktioner (DAX)](/dax/filter-function-dax)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
