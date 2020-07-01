---
title: Använda beräknade kolumner i Power BI Desktop
description: Beräknade kolumner i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 90a8cf81c2dd0dae3a31a15197785e64432f1a01
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237899"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Skapa beräknade kolumner i Power BI Desktop
Med beräknade kolumner kan du lägga till nya data i en tabell direkt i modellen. Men i stället för att fråga och läsa in värden i nya kolumner från en datakälla kan du skapa en formel för Data Analysis-uttryck (DAX) som definierar kolumnens värden. I Power BI Desktop skapas beräknade kolumner via funktionen Ny kolumn i **rapportvyn**.

Till skillnad från anpassade kolumner som skapats som en del av en fråga med hjälp av **Lägg till anpassad kolumn** i frågeredigeraren baseras beräknade kolumner som skapas i **rapportvyn** eller **datavyn** på data som du redan har läst in i modellen. Du kan exempelvis välja att sammanfoga värden från två olika kolumner i två olika men relaterade tabeller samt addera eller extrahera delsträngar.

Beräknade kolumner som du skapar visas i listan **Fält** precis som andra fält, men de har en särskild ikon som visar att värdena kommer från en formel. Du kan kalla dina kolumner vad du vill och lägga till dem i ett visuellt objekt precis som ett annat fält.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Beräknade kolumner beräknar resultat med hjälp av DAX, ett formelspråk som är avsett att fungera med relationsdata, till exempel i Power BI Desktop. DAX innehåller ett bibliotek med över 200 funktioner, operatorer och konstruktioner. Det ger stor flexibilitet när du skapar formler för att beräkna resultat för praktiskt taget alla dataanalysbehov. Läs mer om DAX i [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

DAX-formler påminner mycket om Excel-formler. I själva verket har DAX många av funktionerna i Excel. DAX-funktioner, är avsedda att fungera interaktivt över data segmenterat eller filtrerat i en rapport, precis som i Power BI Desktop. I Excel kan du ha en egen formel för varje rad i en tabell. När du skapar en DAX-formel för en ny kolumn i Power BI beräknar den ett resultat för varje rad i tabellen. Kolumnvärdena räknas vid behov, precis som när underliggande data uppdateras och värden har ändrats.

## <a name="lets-look-at-an-example"></a>Låt oss ta en titt på ett exempel
Jeff, leveranschef på Contoso, vill skapa en rapport som visar antalet leveranser till olika orter. Jeff har en **geografitabell** med olika fält för orter och delstater. Men Jeff vill att rapporterna ska visa värden för ort och delstat som ett enda värde på samma rad. Just nu har Jeffs **geografitabell** inte det fält som behövs.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Men med en beräknad kolumn kan Jeff sammanföra orterna från kolumnen **City** (Ort) med delstaterna från kolumnen **State** (Delstat).

Jeff högerklickar på **geografitabellen** och väljer sedan **Ny kolumn**. Jeff anger sedan följande DAX-formel i formelfältet:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Den här formeln skapar helt enkelt en ny kolumn med namnet **CityState**. För varje rad i **geografitabellen** tar den värden från kolumnen **City**, lägger till ett komma och ett blanksteg och sammanfogar värden från kolumnen **State**.

Jeff har nu det önskade fältet.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Jeff kan lägga till det i rapportarbetsytan tillsammans med antalet leveranser. Jeff har nu enkelt skapat fältet **CityState**, som kan läggas till i praktiskt taget alla sorters visuella objekt. När Jeff skapar en ny karta vet Power BI Desktop redan vet hur värdena för ort och delstat ska läsas i den nya kolumnen.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Nästa steg
Vi tillhandahåller endast en snabb introduktion till beräknade kolumner här. Mer information finns i följande källor:

* Du kan ladda ned en exempelfil och få stegvisa instruktioner för hur du skapar fler kolumner med hjälp av [Självstudie: Skapa beräknade kolumner i Power BI Desktop](desktop-tutorial-create-calculated-columns.md)

* Läs mer om DAX i [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

* Mer information om kolumner som du skapar som en del av en fråga finns i avsnittet **Skapa anpassade kolumner** i [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md).  

