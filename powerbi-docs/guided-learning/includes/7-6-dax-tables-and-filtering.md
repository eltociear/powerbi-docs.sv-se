---
ms.openlocfilehash: d7f30dd43fe875380939520f3dc54fcbbe2f4c9c
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555954"
---
En viktig skillnad mellan **DAX** och Excel-formelspråket är att du kan skicka *hela tabeller* mellan uttryck med DAX i stället för begränsas till ett enstaka värde. En kraftfull effekt är att DAX låter dig filtrera tabeller i uttryck och sedan arbeta med de filtrerade värdena.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

Med DAX kan du skapa helt nya beräknade tabeller och behandla dem som andra tabeller – inklusive att skapa relationer mellan dem och andra tabeller i datamodellen.

## <a name="dax-table-functions"></a>Tabellfunktioner i DAX
DAX har en omfattande uppsättning **tabell**funktioner, inklusive följande:

* FILTRERA
* ALLA
* VÄRDEN
* DISTINKTA
* RELATEDTABLE

Dessa funktioner returnerar en fullständig tabell i stället för ett värde. Normalt använder du resultatet av en **tabell**funktion för ytterligare analys som en del av ett större uttryck, i stället för att använda den returnerade tabellen som slutvärde. Det är viktigt att observera att när du använder en tabellfunktion övertar resultaten relationerna för respektive kolumn.

Du kan blanda tabellfunktioner i ditt uttryck, förutsatt att varje funktion använder en tabell och returnerar en tabell. Överväg till exempel följande DAX-uttryck:

    FILTER (ALL (Table), Condition)

Uttrycket placerar ett filter över hela *Tabellen* vilket ignorerar allt innehåll i det aktuella filtret.

Funktionen DISTINKTA returnerar de distinkta värdena för en kolumn som också är synliga i den aktuella kontexten. Så för att använda ovanstående exempel på ett DAX-uttryck, om du använder **ALLA** i uttrycket ignoreras filter, medan om du ersätter **ALLA** med **DISTINKTA** visas de.

## <a name="counting-values-with-dax"></a>Räkna värden med DAX
En vanlig fråga som rapportutvecklare som använder Power BI ofta ställer är följande:

* Hur många värden finns för den här kolumnen?

Detta kan vara en lätt fråga att besvara med en tabell framför dig, men DAX har olika tillvägagångssätt för olika situationer, särskilt när det finns en relation mellan tabeller.

Till exempel innehåller Power BI och DAX värden som inte är korrekt korsindexerade. Om inkommande relationen är bruten lägger DAX till en ny rad i den relaterade tabellen som innehåller tomma värden i alla fält och länkar den nya raden till den icke-indexerade raden så att den kvarhåller sina referenser. Om din funktion innehåller tomma rader, som ofta är fallet när du använder **ALLA**, tas dessa tomma rader sedan med i antalet värden som returneras för den kolumnen.

Du kan också skapa hela beräknade tabeller med hjälp av DAX-funktioner. Beräknade tabeller som skapats med hjälp av DAX kräver en **namn**- och en **tabell**funktion. Samma funktioner är tillgängliga för beräknade tabeller som för andra tabeller, inklusive relationer.

> Videoinnehåll tillhandahållet av [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

