---
title: Skapa datumtabeller i Power BI Desktop
description: Tekniker och vägledning för att skapa datumtabeller i Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2020
ms.author: v-pemyer
ms.openlocfilehash: ad85ad56db907ca19af7dc14681eb34f8c2b9abc
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85398342"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Skapa datumtabeller i Power BI Desktop

Den här artikeln är avsedd för dig som är datamodellerare som arbetar med Power BI Desktop. Den beskriver metodtips för att skapa datumtabeller i dina datamodeller.

För att arbeta med dataanalysuttryck (DAX) [tidsinformationsfunktioner](/dax/time-intelligence-functions-dax) så finns det ett förhandsmodellkrav: Du måste ha minst en _datumtabell_ i din modell. En datumtabell är en tabell som uppfyller följande krav:

> [!div class="checklist"]
> - Den måste ha en kolumn med datatypen **datum** (eller **datum/tid**) – kallas _datumkolumnen_.
> - Datumkolumnen måste innehålla unika värden.
> - Datumkolumnen får inte innehålla tomrum.
> - Inga datum får saknas i datumkolumnen.
> - Datumkolumnen måste omfatta hela år. Ett år är inte nödvändigtvis ett kalenderår (januari–december).
> - Datumtabellen måste [markeras som en datumtabell](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

Du kan använda någon av flera metoder för att lägga till en datumtabell i din modell:

- Alternativet automatisk datum/tid
- Power Query för att ansluta till en datumdimensionstabell
- Power Query för att generera en datumtabell
- DAX för att generera en datumtabell
- DAX för att klona en befintlig datumtabell

> [!TIP]
> En datumtabell kanske är den mest konsekventa funktionen som du lägger till i någon av dina modeller. En datumtabell inom en organisation bör dessutom vara konsekvent definierad. Oavsett vilken metod du väljer att använda rekommenderar vi att du skapar en [Power BI Desktop-mall](../create-reports/desktop-templates.md) som innehåller en fullständigt konfigurerad datumtabell. Dela mallen med alla modellskapare i organisationen. När någon sedan utvecklar en ny modell kan de börja med en konsekvent definierad datumtabell.

## <a name="use-auto-datetime"></a>Använda automatisk datum/tid

Alternativet [Automatiskt datum/tid](../transform-model/desktop-auto-date-time.md) tillhandahåller praktisk, snabb och lättanvänd tidsinformation. Rapportförfattarna kan arbeta med tidsinformation när de filtrerar, grupperar och ökar detaljnivån i kalenderns tidsperioder.

Vi rekommenderar att du enbart har alternativet Automatisk datum/tid aktiverat när du arbetar med kalendertidsperioder och när du har förenklade modellkrav när det gäller tid. Det kan också vara praktiskt att använda det här alternativet när du skapar ad hoc-modeller eller genomför datautforskning eller profilering. Den här metoden stöder dock inte en tabelldesign med ett enda datum som kan sprida filter till flera tabeller. Mer information finns i [Vägledning för automatisk datum/tid i Power BI Desktop](auto-date-time.md).

## <a name="connect-with-power-query"></a>Anslut med Power Query

När datakällan redan har en datumtabell rekommenderar vi att du använder den som källa för modellens datumtabell. Det är vanligtvis fallet när du ansluter till ett informationslager, eftersom det kommer att ha en datumdimensionstabell. På så sätt använder din modell en enda sanningskälla för tid i organisationen.

Om du utvecklar en DirectQuery-modell och datakällan inte innehåller någon datumtabell rekommenderar vi starkt att du lägger till en datumtabell i datakällan. Den bör uppfylla alla modellkrav för en datumtabell. Du kan sedan använda Power Query för att ansluta till datumtabellen. På så sätt kan dina modellberäkningar använda sig av funktionerna för DAX-tidsinformation.

## <a name="generate-with-power-query"></a>Generera med Power Query

Du kan skapa en datumtabell med Power Query. Här är två blogginlägg som visar hur du gör:

- [Skapa en datumdimension med ett Power Query-skript](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/) av Matt Masson
- [Generera en datumdimensionstabell i Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/) av Chris Webb

> [!TIP]
> Om du inte har ett informationslager eller någon annan konsekvent definition för tid i organisationen, bör du överväga att använda Power Query för att publicera ett [dataflöde](../transform-model/service-dataflows-overview.md). Sedan kan alla datamodellskapare ansluta till dataflödet för att lägga till datumtabeller i sina modeller. Dataflödet blir den enda sanningskällan för tid i organisationen.

Om du behöver generera en datumtabell kan du göra det med DAX. Det kan vara lättare. Dessutom är det sannolikt mer användbart eftersom DAX inkluderar inbyggd intelligens för att förenkla skapandet och hantering av datumtabeller.

## <a name="generate-with-dax"></a>Generera med DAX

Du kan generera en datumtabell i din modell genom att skapa en beräknad tabell med antingen DAX-funktionerna [CALENDAR](/dax/calendar-function-dax) eller [CALENDARAUTO](/dax/calendarauto-function-dax). Varje funktion returnerar en tabell med datum med en kolumn. Du kan sedan utöka den beräknade tabellen med beräknade kolumner så att den stöder filtrering av datumintervall och grupperingskrav.

- Använd funktionen **CALENDAR** när du vill definiera ett datumintervall. Du skickar in två värden: startdatum och slutdatum. Dessa värden kan definieras av andra DAX-funktioner som `MIN(Sales[OrderDate])` eller `MAX(Sales[OrderDate])`.
- Använd funktionen **CALENDARAUTO** när du vill att datumintervallet automatiskt ska omfatta alla datum som lagras i modellen. Du kan överföra en enda valfri parameter som är årets slutmånad (om året är ett kalenderår som slutar i december behöver du inte ange något värde). Det är en användbar funktion, eftersom det garanterar att hela året med datum returneras – det är ett krav för en markerad datumtabell. Dessutom behöver du inte hantera att utöka tabellen till framtida år: När en datauppdatering har slutförts utlöses omberäkningen av tabellen. En omberäkning utökar automatiskt tabellens datumintervall när datum för ett nytt år läses in i modellen.

## <a name="clone-with-dax"></a>Klona med DAX

När din modell redan har en datumtabell och du behöver ytterligare en datumtabell, kan du enkelt klona den befintliga datumtabellen. Det är fallet när datumet är en [dimension med olika roller](star-schema.md#role-playing-dimensions). Du kan klona en tabell genom att skapa en beräknad tabell. Det beräknade tabelluttrycket är helt enkelt namnet på den befintliga datumtabellen.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Automatisk datum/tid i Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Vägledning om automatiskt datum/tid i Power BI Desktop](auto-date-time.md)
- [Konfigurera och använda datumtabeller i Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Dataförberedelser med självbetjäning i Power BI](../transform-model/service-dataflows-overview.md)
- [CALENDAR-funktionen (DAX)](/dax/calendar-function-dax)
- [CALENDARAUTO-funktionen (DAX)](/dax/calendarauto-function-dax)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
