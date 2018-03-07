---
title: Sortera efter kolumn i Power BI Desktop
description: Sortera efter kolumn i Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 05/01/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: cb23034c207bd272f716e8074bb3702ea30e893a
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Sortera efter kolumn i Power BI Desktop
I **Power BI Desktop** och **Power BI-tjänsten** kan du ändra utseendet på ett visuellt objekt genom att sortera det enligt olika datafält. Genom att ändra hur du sorterar ett visuellt objekt kan du markera den information som du vill förmedla och vara säker på att det visuella objektet speglar den trend (eller betoning) som du vill förmedla.

Om du använder numeriska data (till exempel försäljningssiffror) eller textdata (till exempel namn på delstater) kan du sortera dina visuella objekt och utforma dem som du vill ha dem.  **Power BI** ger stor flexibilitet för sortering och snabb menyer som du kan använda. Välj ellipsmenyn (...) på ett visuellt objekt och sedan **Sortera efter**. Välj sedan fältet som du vill sortera, enligt följande bild.

![](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="more-depth-and-an-example"></a>Mer djup och ett exempel
Låt oss ta ett exempel som är djupare och se hur det fungerar i **Power BI Desktop**.

Följande visuella objekt utgör en lista över 15 delstater i väderordning (flest dagar med sol från 1 till 50, där 1 har flest dagar med sol). Så här ser det visuella objektet ut innan vi börjar sortera.

![](media/desktop-sort-by-column/sortbycolumn_1.png)

Det visuella objektet är för närvarande sorterat enligt **Levnadskostnad** – vi ser det tack vare att staplarnas färg matchar förklaringen, men det finns ett bättre sätt att avgöra hur staplarna är ordnade: dialogrutan **Sortera efter** som är tillgänglig från ellipsmenyn (...) i det visuella objektets övre högra hörn. Vi ser följande när vi väljer ellipserna:

![](media/desktop-sort-by-column/sortbycolumn_2.png)

Det finns vissa objekt att observera på menyn som visas när du väljer ellipserna:

* Det gula fältet intill **Levnadskostnader** och att **Levnadskostnader** står i fet stil
* Den lilla ikonen bredvid orden **Sortera efter** visar **Z/A** (från Z till A) och en nedpil.

Vi ska titta på båda för sig i nästa två avsnitt.

## <a name="selecting-which-column-to-use-for-sorting"></a>Så här väljer du vilken kolumn som ska användas för sortering
Du lade säkert märke till det gula fältet intill **levnadskostnader** i menyn **Sortera efter** menyn, vilket visade att det visuella objektet använde kolumnen **levnadskostnader** för att sortera informationen. Det är lätt att sortera efter en annan kolumn – bara välj ellipserna att visa menyn **Sortera efter**. Välj sedan en annan kolumn. Så enkelt är det.

I följande bild valde vi **Folkhälsa** som parameter för att ordna kolumnen. Den här kolumnen råkar vara en av linjerna i det visuella objektet snarare än en stapel. Så här ser det ut när vi har valt **Folkhälsa**.

![](media/desktop-sort-by-column/sortbycolumn_3.png)

Observera hur den visuella informationen har ändrats. Nu sorteras värdena från det högsta värdet för ”Folkhälsa” (i det här fallet RI för Rhode Island) för delstaterna i det visuella objektet till AZ (för Arizona) som har det lägsta värdet. Kom ihåg att det övergripande diagrammet endast innehåller de 15 delstaterna med mest solsken – vi har bara ordnat dem baserat på en annan kolumn som ingår i det visuella objektet.

Men vad händer om vi vill sortera stigande i stället för fallande? I nästa avsnitt visar vi hur enkelt det är.

## <a name="selecting-the-sort-order---smallest-to-largest-largest-to-smallest"></a>Att välja sorteringsordning – minsta till största, största till minsta
När vi tar en närmare titt på menyn **Sortera efter** från den föregående bilden ser vi att ikonen bredvid **Sortera efter** visar **Z/A** (Z till A). Låt oss ta en titt:

![](media/desktop-sort-by-column/sortbycolumn_4.png)

När **Z/A** är visas, betyder det visuella objektet sorteras efter den markerade kolumnen från det största till det minsta värdet. Vill du ändra det? Inga problem – bara tryck eller klicka på **Z/A**-ikonen så ändras sorteringsordningen till **A/Z** och sorterar det visuella objektet (baserat på den markerade kolumnen) från det minsta till största värdet.

Här är visuella objekt, den här gången efter att vi har tryckt på ikonen **Z/A** på menyn **sortera efter** för att ändra dess ordning. Observera att AZ (Arizona) nu är den första delstaten i listan och att RI (Rhode Island) är den sista – det vill säga omvänt från innan.

![](media/desktop-sort-by-column/sortbycolumn_5.png)

Du kan sortera efter valfri kolumn som ingår i det visuella objektet – vi kan lika gärna välja väder och välj **Z/A** från menyn **Sortera efter** för att visa delstater med mest sol först (högsta värde: väder är lika med dagar med solsken i den här datamodellen) och fortfarande behålla de andra kolumnerna i det visuella objektet, oavsett vilka värden de har för den delstaten. Så här ser det visuella objektet ut med dessa inställningar.

![](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Sortera med knappen Sortera efter kolumn
Det finns ett annat sätt att sortera data och det är med hjälp av knappen **Sortera efter kolumn** i menyfliksområdet **Modellering**.

![](media/desktop-sort-by-column/sortbycolumn_8.png)

Den här sorteringsmetoden kräver att du väljer en kolumn från fönstret **Fält** och sedan väljer knappen **Sortera efter kolumn** för att välja hur (genom vilken kolumn) som du vill sortera ditt visuella objekt. Du måste markera kolumnen (fältet) som du vill sortera från rutan **Fält** för att aktivera knappen **Sortera efter kolumn** – annars är knappen inaktiv.

Nu ska vi titta på ett vanligt exempel: du har data från varje dag i veckan och du vill sortera dem i kronologisk ordning. Följande steg visar hur du gör.

1. Observera att knappen är inaktiv (grå) när det visuella objektet har valts men ingen kolumn har markerats i rutan **Fält** i **Sortera efter kolumn**.
   
   ![](media/desktop-sort-by-column/sortbycolumn_9a.png)
2. När vi väljer den kolumn som vi vill sortera i rutan **fält** i **Sortera efter kolumn** blir knappen aktiv.
   
   ![](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Nu när vi har valt ett visuellt objekt kan vi välja *Dag i veckan*, istället för standard (*Namn på dag*) varpå det visuella objektet sorteras i den önskade ordningen: enligt veckodag.
   
   ![](media/desktop-sort-by-column/sortbycolumn_11.png)

Och sedan är du klar. Kom ihåg att du måste markera en kolumn i rutan **Fält** för knappen **Sortera efter kolumn** ska aktiveras.

## <a name="getting-back-to-default-column-for-sorting"></a>Gå tillbaka till standardkolumnen för sortering
Du kan sortera efter valfri kolumn men det kan finnas tillfällen när du vill att det visuella objektet ska återgå till dess standardsorteringskolumn. Inga problem. För ett visuellt objekt som har en markerad sorteringskolumn (vi vet nu att en markerad sorteringskolumn har ett gult fält bredvid det i menyn **Sortera efter**) kan du öppna menyn **Sortera efter** och markera kolumnen på nytt så ordnas det visuella objektet åter efter dess standardkolumn.

Till exempel, här diagrammet vi visade tidigare:

![](media/desktop-sort-by-column/sortbycolumn_6.png)

När vi går tillbaka till menyn och markerar **Väder** igen återgår kolumnen till att sorteras i bokstavsordning enligt **Delstatskod**, enligt följande bild.

![](media/desktop-sort-by-column/sortbycolumn_7.png)

Med så här många alternativ för att sortera dina visuella objekt är det lätt att bara skapa diagrammet eller bilden.

