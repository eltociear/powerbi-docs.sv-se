---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555961"
---
Med Power BI kan du skapa relationer mellan flera tabeller, inklusive tabeller som kommer från helt olika datakällor. Du kan visa dessa relationer för alla datamodeller i vyn **Relationer** i Power BI Desktop.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>DAX relationella funktioner
DAX har **relationella funktioner** som gör att du kan interagera med tabeller som har etablerade relationer.

Du kan returnera värdet för en kolumn, eller alla rader i en relation, med hjälp av DAX-funktioner.

**RELATED**-funktionen följer som exempel relationer och returnerar värdet för en kolumn, medan **RELATEDTABLE** följer relationer och returnerar en hel tabell som har filtrerats för att bara inkludera relaterade rader.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

**RELATED**-funktionen fungerar på *många-till-en*-relationer, medan **RELATEDTABLE** är avsedd för *en-till-många*-relationer.

Du kan använda relationella funktioner för att skapa uttryck som innehåller värden från flera tabeller. DAX returnerar ett resultat med dessa funktioner, oavsett hur lång relationskedjan är.

> Videoinnehåll tillhandahållet av [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

