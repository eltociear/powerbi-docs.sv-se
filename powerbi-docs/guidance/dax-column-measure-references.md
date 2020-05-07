---
title: 'DAX: Referenser för kolumner och mått'
description: Vägledning om referenser till kolumner i mått i dina DAX-uttryck.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75498747"
---
# <a name="dax-column-and-measure-references"></a>DAX: Referenser för kolumner och mått

Som datamodellerare gör du att dina DAX-uttryck refererar till modellkolumner och mått. Kolumner och mått associeras alltid med modelltabeller, men de här associationerna är annorlunda. Därför ger vi andra rekommendationer om hur du refererar till dem i uttryck.

## <a name="columns"></a>Kolumner

En kolumn är ett objekt på tabellnivå, och kolumnnamn måste vara unika i en tabell. Därför är det möjligt att samma kolumnnamn används flera gånger i din modell, förutsatt att de tillhör olika tabeller. Det finns ytterligare en regel: ett kolumnnamn kan inte ha samma namn som ett måttnamn eller hierarkinamn som finns i samma tabell.

I allmänhet gäller att DAX inte framtvingar användning av en _fullständigt kvalificerad_ referens till en kolumn. En fullständigt kvalificerad referens innebär att tabellnamnet föregår kolumnnamnet.

Här är ett exempel på en definition av en beräknad kolumn där endast kolumnnamnsreferenser används. Kolumnerna **Sales** (Försäljning) och **Cost** (Kostnad) tillhör båda en tabell som heter **Orders** (Beställningar).

```dax
Profit = [Sales] - [Cost]
```

Samma definition kan skrivas om med fullständigt kvalificerade kolumnreferenser.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Ibland måste du dock använda fullständigt kvalificerade kolumnreferenser när Power BI upptäcker tvetydighet. När du anger en formel visas då röd vågig understrykning och ett felmeddelande. Dessutom kräver vissa DAX-funktioner, till exempel DAX-funktionen [LOOKUPVALUE](/dax/lookupvalue-function-dax), att fullständigt kvalificerade kolumner används.

Vi rekommenderar att du alltid kvalificerar kolumnreferenser fullständigt. Orsakerna anges i avsnittet [Rekommendationer](#recommendations).

## <a name="measures"></a>Mått

Ett mått är ett objekt på modellnivå. Därför måste måttnamn vara unika i modellen. I fönstret **Fält** ser rapportförfattare dock varje mått associerat med en enda modelltabell. Den här associationen anges av utseendeskäl. Du kan konfigurera den genom att ange måttets egenskap **Home Table** (Starttabell). Mer information finns i [Mått i Power BI Desktop (Ordna dina mått)](../desktop-measures.md#organizing-your-measures).

Det går att använda ett fullständigt kvalificerat mått i uttryck. DAX IntelliSense erbjuder rentav förslag om det. Däremot är det inte nödvändigt och rekommenderas inte. Om du ändrar starttabellen för ett mått gör det att uttryck som använder en fullständigt kvalificerad måttreferens till tabellen slutar fungera. Du måste då redigera varje bruten formel genom att ta bort (eller uppdatera) måttreferensen.

Vi rekommenderar att du aldrig kvalificerar måttreferenser. Orsakerna anges i avsnittet [Rekommendationer](#recommendations).

## <a name="recommendations"></a>Rekommendationer

Våra rekommendationer är enkla och lätta att komma ihåg:

- Använd alltid fullständigt kvalificerade kolumnreferenser
- Använd aldrig fullständigt kvalificerade måttreferenser

Skälet är följande:

- **Formelinmatning**: Uttryck godkänns eftersom det inte finns några tvetydiga referenser att lösa. Dessutom uppfyller du kraven för de DAX-funktioner som kräver fullständigt kvalificerade kolumnreferenser.
- **Robusthet**: Uttrycken fortsätter att fungera även när du ändrar egenskapen för starttabell för ett mått.
- **Läsbarhet**: Det går snabbt och enkelt att förstå uttryck – du kan snabbt avgöra om det är en kolumn eller ett mått baserat på huruvida det är fullständigt kvalificerat.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
