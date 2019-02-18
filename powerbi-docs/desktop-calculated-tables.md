---
title: Använda beräknade tabeller i Power BI Desktop
description: Beräknade tabeller i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ffa49cc65c28e0fafb8ca72cb7a1a5bbde798861
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216342"
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Använda beräknade tabeller i Power BI Desktop
Med beräknade tabeller kan du lägga till en ny tabell i modellen. Men i stället för att fråga och läsa in värden i den nya tabellens kolumner från en datakälla kan du skapa en formel för Data Analysis-uttryck (DAX) som definierar tabellens värden. I Power BI Desktop skapas beräknade tabeller med funktionen Ny tabell i rapportvyn eller datavyn.

För det mest importerar du data till din modell från en extern datakälla. Beräknade tabeller har emellertid vissa fördelar. Beräknade tabeller är oftast bäst för mellanliggande beräkningar och data som ska lagras som en del av modellen i stället för att beräknas direkt eller som del av en fråga.

Till skillnad från tabeller som skapats som en del av en fråga baseras beräknade tabeller som skapas i rapportvyn eller datavyn redan på data som du har läst in i modellen. Du kanske vill förena eller koppla två tabeller.

Precis som vanliga tabeller kan beräknade tabeller ha relationer till andra tabeller. Kolumnerna i den beräknade tabellen har datatyper, formatering, och kan tillhöra en datakategori. Du kan kalla dina kolumner vad du vill och lägga till dem i ett visuellt objekt precis som ett annat fält. Beräknade tabeller beräknas om någon av de tabeller som den hämtar data från uppdateras på något sätt.

Beräknade tabeller beräknar resultat med hjälp av [Data Analysis-uttryck](https://msdn.microsoft.com/library/gg413422.aspx) (DAX), ett formelspråk som är avsett att fungera med relationsdata, till exempel i Power BI Desktop. DAX innehåller ett bibliotek med över 200 funktioner, operatörer och konstruktioner och ger stor flexibilitet vid skapande av formler för att beräkna resultat för nästan alla dataanalysbehov.

## <a name="lets-look-at-an-example"></a>Låt oss ta en titt på ett exempel
Jeff är projektledare på Contoso och har en tabell med anställda i regionen Nordväst och en annan tabell med anställda i Sydväst. Jeff vill förena de två tabellerna till en tabell.

**Anställdanordväst**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SouthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Det är ganska enkelt att förena de två tabellerna med en beräknad tabell. Medan Jeff kan skapa en beräknad tabell antingen i rapportvyn eller datavyn är det lite enklare att göra det i datavyn eftersom han då kan se sin nya beräknade tabell direkt.

Jeff klickar på **Ny tabell** i **datavyn** på fliken **Modellering**. Ett formelfält visas.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff skriver sedan in följande formel:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

En ny tabell med namnet Anställda i region Väst skapas.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

Jeffs nya tabell Anställda i region Väst visas precis som andra tabeller i listan Fält. Han kan skapa relationer till andra tabeller, lägga till beräknade kolumner och mått och lägga till något av dess fält i rapporter, precis som med andra tabeller.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funktioner för beräknade tabeller
Beräknade tabeller kan definieras av ett DAX-uttryck som returnerar en tabell, inklusive en enkel referens till en annan tabell. Till exempel:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

Du kan använda beräknade tabeller med DAX för att lösa många analytiska problem. Vi tillhandahåller endast en snabb introduktion till beräknade tabeller här. När du börjar arbeta med beräknade tabeller är dessa några av de vanligaste DAX-tabellfunktionerna som du kan ha nytta av:

* DISTINKTA
* VÄRDEN
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Se [DAX-funktionsreferensen](https://msdn.microsoft.com/ee634396.aspx) för dessa och andra tabeller som returnerar DAX-funktioner.

