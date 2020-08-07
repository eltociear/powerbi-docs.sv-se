---
title: 'DAX: Skapa bättre formler med hjälp av variabler'
description: Vägledning om att använda variabler i DAX-uttryck.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: ade84d1523d79e4e233604905627e8e862278fa1
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537422"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Skapa bättre formler med hjälp av variabler

Som datamodellerare kan det vara svårt att skriva och felsöka vissa DAX-beräkningar. I komplexa beräkningar måste du ofta använda sammansatta eller komplexa uttryck. Sammansatta uttryck kan bestå av många kapslade funktioner och eventuellt även uttryckslogik.

När du använder variabler i dina DAX-formler kan du skriva komplexa och effektiva beräkningar. Variabler ger:

- [bättre prestanda](#improve-performance)
- [bättre läsbarhet](#improve-readability)
- [enklare felsökning](#simplify-debugging)
- [mindre komplexitet](#reduce-complexity)

I den här artikeln går vi igenom de tre första fördelarna genom att använda ett exempelmått för försäljningstillväxten från år till år. (Formeln för tillväxten på årsbasis är periodens försäljning, minus försäljningen för samma period föregående år _dividerat med_ försäljningen under samma period föregående år.)

Vi börjar med följande måttdefinition.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

Måttet ger rätt resultat, men nu ska vi se om vi kan förbättra det.

## <a name="improve-performance"></a>Bättre prestanda

Observera att uttrycket som beräknar ”samma period förra året” upprepas i formeln. Den här formeln är ineffektiv eftersom Power BI måste utvärdera samma uttryck två gånger. Måttdefinitionen kan göras effektivare med hjälp av en variabel.

Det här är en bättre måttdefinition. Där används ett uttryck för att tilldela resultatet för ”samma period förra året” till en variabel med namnet **SalesPriorYear**. Variabeln används sedan två gånger i RETURN-uttrycket.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

Måttet ger fortfarande rätt resultat men på ungefär halva tiden.

## <a name="improve-readability"></a>Bättre läsbarhet

Lägg märke till hur valet av variabelnamn gör RETURN-uttrycket enklare att förstå i föregående måttdefinition. Uttrycket är kort och beskrivande.

## <a name="simplify-debugging"></a>Enklare felsökning

Variabler kan också göra en formel enklare att felsöka. Du kan testa ett uttryck som tilldelats till en variabel genom att tillfälligt skriva om RETURN-uttrycket så att variabeln matas ut.

I följande måttdefinition returneras endast variabeln **SalesPriorYear**. Observera hur det ursprungliga RETURN-uttrycket är utkommenterat. På så sätt kan du enkelt återställa koden när felsökningen är färdig.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Mindre komplexitet

I tidigare versioner av DAX saknades stöd för variabler. Du behövde använda DAX-funktionerna [EARLIER](/dax/earlier-function-dax) eller [EARLIEST](/dax/earliest-function-dax) som referenser till yttre filtreringskontexter i komplexa uttryck med nya filterkontexter. De här funktionerna kunde tyvärr vara svåra att använda och förstå.

Variabler utvärderas alltid utanför de filter som används i RETURN-uttrycket. När du använder en variabel i en modifierad filterkontext får du därför samma resultat som med funktionen EARLIEST. Det gör att du inte behöver använda funktionerna EARLIER eller EARLIEST. På så sätt kan du skriva formler som är mindre komplexa och enklare att förstå.

Titta på den här beräknade kolumnen som lagts till i tabellen **Subcategory**. Där utvärderas en rangordning för varje produktkategori baserat på värdena i kolumnen **Subcategory**.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

Funktionen EARLIER används till att referera till kolumnvärdet **Subcategory Sales**_i den aktuella radkontexten_.

Du kan förbättra definitionen av den beräknade kolumnen genom att använda en variabel i stället för funktionen EARLIER. Variabeln **CurrentSubcategorySales** lagrar värdet i kolumnen **Subcategory Sales**_i den aktuella radkontexten_, och i RETURN-uttrycket används det i en modifierad radkontext.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- [VAR](/dax/var-dax) DAX-artikel
- Utbildningsväg: [Använda DAX i Power BI Desktop](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
