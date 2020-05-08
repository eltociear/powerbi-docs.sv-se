---
title: Använda beräknade tabeller i Power BI Desktop
description: Beräknade tabeller i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: c72387d40ddf4b193481a37dbcb40695668eab66
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75837348"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>Skapa beräknade tabeller i Power BI Desktop
För det mest skapar du tabeller genom att importera data till din modell från en extern datakälla. Men med *beräknade tabeller* kan du lägga till nya tabeller baserat på data som du redan har läst in till modellen. I stället för att köra frågor och läsa in värden i den nya tabellens kolumner från en datakälla kan du skapa en [DAX-formel](/dax/index) (Data Analysis Expressions) som definierar tabellens värden.

DAX är ett formelspråk för att arbeta med relationsdata, som i Power BI Desktop. DAX innehåller ett bibliotek med över 200 funktioner, operatörer och konstruktioner och ger stor flexibilitet vid skapande av formler för att beräkna resultat för nästan alla dataanalysbehov. Beräknade tabeller passar bäst för mellanliggande beräkningar och data som ska lagras i modellen, snarare än att beräkna i farten eller som frågeresultat. Du kanske vill *förena* eller *korskoppla* två tabeller.

Precis som andra tabeller i Power BI Desktop så kan beräknade tabeller ha relationer till andra tabeller. Kolumnerna i beräknade tabeller har datatyper, formatering och kan tillhöra en datakategori. Du kan kalla dina kolumner vad du vill och lägga till dem visualiseringar precis som andra fält. Beräknade tabeller beräknas om ifall någon av de tabeller som de hämtar data från uppdateras.

## <a name="create-a-calculated-table"></a>Skapa en beräknad tabell

Du skapar beräknade tabeller med funktionen **Ny tabell** i rapportvyn eller datavyn i Power BI Desktop.

Anta till exempel att du är en personalchef som har en tabell med **Northwest Employees** och en annan tabell med **Southwest Employees**. Du vill kombinera de två tabellerna i en enda tabell med namnet **Western Region Employees**.

**Northwest Employees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**Southwest Employees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Gå till gruppen **Beräkningar** på fliken **Modellering** och välj **Ny tabell** i rapportvyn eller datavyn i Power BI Desktop. Det är lite enklare att göra i datavyn, eftersom du då ser den nya beräknade tabellen direkt.

 ![Ny tabell i datavyn](media/desktop-calculated-tables/calctables_formulabarempty.png)

Ange följande formel i formelfältet:

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

Då skapas en ny tabell med namnet **Western Region Employees**, som visas precis som de andra tabellerna i fönstret **Fält**. Du kan skapa relationer till andra tabeller, lägga till mått och beräknade kolumner och lägga till fälten i rapporter precis som med andra tabeller.

 ![Ny beräknad tabell](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![Ny tabell i fönstret Fält](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funktioner för beräknade tabeller

Du kan definiera beräknade tabeller med DAX-uttryck som returnerar en tabell, även om det bara är en enkel referens till en annan tabell. Exempel:

```dax
New Western Region Employees = 'Western Region Employees'
```

I den här artikeln ges bara en snabb introduktion till beräknade tabeller. Du kan använda beräknade tabeller med DAX för att lösa många analytiska problem. Här är några av de vanligare DAX-tabellfunktionerna du kan använda:

* DISTINKTA
* VÄRDEN
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Läs mer om de här funktionerna och andra DAX-funktioner som returnerar tabeller i [DAX-funktionsreferensen](/dax/dax-function-reference).

