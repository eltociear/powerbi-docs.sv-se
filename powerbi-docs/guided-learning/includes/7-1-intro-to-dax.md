---
ms.openlocfilehash: 3966521d158c244487638be4117f98ea570e1f28
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73800162"
---
Välkommen till avsnittet i den **interaktiva utbildningen** om Power BI som har utformats för att introducera **DAX**.

**DAX** står för **Data Analysis Expressions** och det är formelspråket som används i hela Power BI (det används också av Power BI i bakgrunden). DAX finns även i andra system från Microsoft, till exempel Power Pivot och SSAS Tabular, men dessa kurser fokuserar på hur DAX används – och kan användas av dig – i Power BI.

## <a name="dax-and-this-guided-learning-video-series"></a>DAX och denna interaktiva videoutbildningsserie
Syftet med detta avsnitt av den **interaktiva utbildningen** är att lära dig grunderna i DAX – hur du förhåller dig till DAX, hur det fungerar och de mest användbara funktionerna som beskrivs av en världskänd DAX-expert med lång erfarenhet, [ Alberto Ferrari](https://www.sqlbi.com/learning-dax).

![Porträtt av Alberto Ferrari](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

Videoklippen i detta avsnitt av den **interaktiva utbildningen** om **DAX** lär dig grunderna i DAX med DAX-formelspråket som utgångspunkt. Detta är användbart när du skapar DAX-formler från början, men det är också användbar för att förstå hur Power BI skapar DAX-formler när du skapar frågor i **Frågeredigeraren**.

## <a name="in-this-video---introduction-to-dax"></a>I det här videoklippet – introduktion till DAX
DAX-principerna är enkla, men DAX är kraftfullt. DAX använder vissa unika programmeringsbegrepp och mönster som kan göra det svårt att använda och förstå fullständigt. Traditionella sätt att lära sig språk är kanske inte optimala för DAX, så syftet med den här videon är att lära dig begrepp och teori som kan vara användbart när du arbetar med Power BI.

DAX är ett *funktionellt språk*, vilket innebär att den fullständiga koden finns inuti en funktion.

I DAX kan funktioner innehålla kapslade funktioner, villkorssatser och värdereferenser. Körning i DAX börjar med den innersta funktionen eller parametern och arbetar sig utåt. I Power BI skrivs DAX formler på en enda rad vilket innebär att dina funktioner måste vara korrekt formaterade.

DAX är avsett att fungera med tabeller, så den har endast två primära datatyper: **numeriska** och **övrigt**. **Numeriska** kan innehålla *heltal*, *decimaler* och *valuta*. **Övriga** kan innehålla *strängar* och *binära objekt*. Det innebär att om du bygger DAX-funktionen för en typ av tal kan du vara säker på att den kommer att fungera med andra numeriska data.

DAX använder operatöröverlagring, vilket innebär att du kan blanda datatyper i beräkningarna och resultatet ändras beroende på vilken typ av data som används i indatan. Konverteringen sker automatiskt, vilket innebär att du behöver inte ha någon av datatyperna för kolumnerna som du arbetar med i Power BI, men det innebär också att konverteringen ibland kan inträffa på oväntade sätt. Det är bra att förstå de data som du använder för att säkerställa att dina operatörer fungerar som förväntat.

Det finns en datatyp i synnerhet som du kommer troligen att arbeta med mycket i Power BI: **DateTime**. **DateTime** lagras som ett flyttalsvärde med både heltal- och decimaldelar. DateTime kan användas korrekt för beräkningar för tidsperioder som inträffar efter 1 mars 1900.

> Videoinnehåll tillhandahållet av [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

