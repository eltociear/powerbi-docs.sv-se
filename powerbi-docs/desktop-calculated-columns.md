---
title: Använda beräknade kolumner i Power BI Desktop
description: Beräknade kolumner i Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 2a92426061b37753c529b84a1de6b8068cb3bc5f
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Använda beräknade kolumner i Power BI Desktop
Med beräknade kolumner kan du lägga till nya data i en tabell direkt i modellen. Men i stället för att fråga och läsa in värden i nya kolumner från en datakälla kan du skapa en formel för Data Analysis-uttryck (DAX) som definierar kolumnens värden. I Power BI Desktop skapas beräknade kolumner med funktionen Ny kolumn i rapportvyn.

Till skillnad från anpassade kolumner som skapats som en del av en fråga med hjälp av Lägg till anpassade kolumn i frågeredigeraren, baseras beräknade kolumner som skapats i rapportvyn eller datavyn på data som du redan har läst in i modellen. Du kan exempelvis välja att sammanfoga värden från två olika kolumner i två relaterade tabeller och addera eller extrahera underordnade strängar.

Beräknade kolumner som du har skapat visas i listan Fält precis som andra fält, men de har en särskild ikon som visar deras värden som resultat av en formel. Du kan kalla dina kolumner vad du vill och lägga till dem i ett visuellt objekt precis som ett annat fält.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Beräknade kolumner beräknar resultat med hjälp av [Data Analysis-uttryck](https://msdn.microsoft.com/library/gg413422.aspx) (DAX), ett formelspråk som är avsett att fungera med relationsdata, till exempel i Power BI Desktop. DAX innehåller ett bibliotek med över 200 funktioner, operatörer och konstruktioner och ger stor flexibilitet vid skapande av formler för att beräkna resultat för nästan alla dataanalysbehov. För mer information om DAX, se avsnittet Läs mer i slutet av artikeln.

DAX-formler påminner mycket om Excel-formler. I själva verket har DAX många av funktionerna i Excel. DAX-funktioner, är avsedda att fungera interaktivt över data segmenterat eller filtrerat i en rapport, precis som i Power BI Desktop. Till skillnad från Excel, där du kan använda en annan formel för varje rad i en tabell beräknas ett resultat för varje rad i tabellen när du skapar en DAX-formel för en ny kolumn. Kolumnvärdena räknas vid behov, precis som när underliggande data uppdateras och värden har ändrats.

## <a name="lets-look-at-an-example"></a>Låt oss ta en titt på ett exempel
Jeff är en leveranschef på Contoso. Han vill skapa en rapport som visar antalet leveranser till olika orter. Han har en geografisk tabell med olika fält för orter och delstater. Men Jeff vill att rapporterna ska visa stad, delstat som ett enda värde på samma rad. Just nu har Jeffs geografiska tabell inte fältet som han vill ha.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Men med en beräknad kolumn kan Jeff sammanföra städerna från kolumnen Orter med delstaterna från kolumnen Delstater.

Jeff högerklickar på den geografiska tabellen och klickar på Ny kolumn. Han anger sedan följande DAX-formel i formelfältet:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Den här formeln skapar helt enkelt en ny kolumn som heter StadDelstat och hämtar ett värde från Stad-kolumnen, lägger till ett komma och ett mellanslag och sammanfogar därefter värden från Delstats-kolumnen från samma rad i den geografiska tabellen.

Jeff har nu fältet han vill ha.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Han kan lägga till det i sin rapportarbetsyta tillsammans med antalet försändelser. Snabbt och enkelt har Jeff nu skapat ett fält med Stad, Delstat som han kan lägga till i praktiskt taget alla sorters visuella objekt. Jeff kan se att Power BI Desktop vet hur värdena Stad, Delstat ska läsas i den nya kolumnen när han skapar en karta.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>Läs mer
Vi tillhandahåller endast en snabb introduktion till beräknade kolumner här. Läs [Självstudie: skapa beräknade kolumner i Power BI Desktop](desktop-tutorial-create-calculated-columns.md), där du kan ladda ned en exempelfil och få stegvisa anvisningar om hur du skapar fler kolumner. 

Läs mer om DAX i [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Mer information om kolumner som du skapar som en del av en fråga finns i avsnittet Skapa anpassade kolumner i [vanliga frågeuppgifter i Power BI Desktop.](desktop-common-query-tasks.md)  

