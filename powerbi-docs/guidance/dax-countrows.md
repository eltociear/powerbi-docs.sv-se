---
title: 'DAX: Använd COUNTROWS istället för COUNT'
description: Vägledning om när du ska använda COUNTROWS-funktionerna.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: fd3b50e9016298db8b692d6a2f3549b770f143e8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700672"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: Använd COUNTROWS istället för COUNT

Som datamodellerare kan du ibland behöva skriva DAX-uttryck som räknar antalet tabellrader. Tabellen kan vara en modelltabell eller ett uttryck som returnerar en tabell.

Du kan göra det här på två sätt. Du kan använda funktionen [COUNT](/dax/count-function-dax) och räkna antalet kolumnvärden, eller så kan du använda funktionen [COUNTROWS](/dax/countrows-function-dax) och räkna antalet tabellrader. Båda funktionerna ger samma resultat, förutsatt att kolumnen du räknar inte innehåller några tomma värden.

Här är ett exempel på en sådan måttdefinition. Här beräknar vi antalet värden i kolumnen **OrderDate**.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Förutsatt att kornigheten i tabellen **Sales** är en rad per försäljningsorder och att kolumnen **OrderDate** inte innehåller några tomma värden så ger måttet rätt resultat.

Det är dock bättre att använda den här måttdefinitionen.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Det finns tre skäl till varför den andra måttdefinitionen är bättre:

- Den är mer effektiv och ger därför bättre prestanda.
- Det spelar ingen roll om tabellkolumnerna har tomma värden.
- Avsikten med formeln blir tydligare.

## <a name="recommendation"></a>Rekommendation

När du vill räkna antalet tabellrader rekommenderar vi att du alltid använder funktionen COUNTROWS.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
