---
title: "Använd gruppering i Power BI Desktop"
description: "Lär dig att gruppera och diskretisera element i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/19/2018
ms.author: davidi
ms.openlocfilehash: 6d398a7594cfde65d878cbd317a2669b945da9e6
ms.sourcegitcommit: a973bc6adc88507932e7e1535a74208e3842f5c4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/20/2018
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Använd gruppering i Power BI Desktop
När **Power BI Desktop** skapar visuella objekt sammanställer den dina data i segment (eller **grupper**) baserat på värdena i underliggande data. Det är ofta bra, men ibland vill du begränsa hur dessa segmentvisas. Du kanske exempelvis vill placera tre produktkategorier i en större kategori (en *grupp*). Du vill kanske se försäljningsfigurer i diskreta enheter motsvarande 1 000 000 kronor istället för jämnt fördelade med 923 983 kronor per grupp.

Du kan **gruppera** datapunkter i Power BI Desktop, vilket hjälper dig att tydligt visa, analysera och utforska data och trender i visuella objekt. Du kan också definiera storleken på **diskreta grupper**, vilket ofta kallas **diskretisering**, dvs placera värden i lika stora grupper som hjälper dig att visa information på ett tydligt sätt.

### <a name="using-grouping"></a>Med gruppering
För att använda **gruppering**, markera två eller flera element på ett visuellt objekt genom att använda CTRL + klicka för att välja flera element. Högerklicka sedan på ett av de valda elementen och välj *Gruppera* från menyn som visas.

![](media/desktop-grouping-and-binning/grouping-binning_1.png)

När du skapat gruppen läggs den till i **Förklaringen** för det visuella objektet och visas också i listan **Fält**.

![](media/desktop-grouping-and-binning/grouping-binning_2.png)

När du har en grupp kan du enkelt redigera medlemmar i gruppen genom att högerklicka på fältet från bucketen **Förklaring** eller från listan **Fält** och välja *Redigera grupper*.

![](media/desktop-grouping-and-binning/grouping-binning_3.png)

I fönstret **Grupper** som visas som du kan skapa nya grupper eller ändra befintliga grupper. Du kan också *Byt namn på* valfri grupp genom att dubbelklicka på **gruppens** rubrik i rutan **Grupper och medlemmar** och skriva in ett nytt namn.

Det finns olika typer av saker du kan göra med grupper i det här fönstret. Du kan lägga till objekt från listan **Ej grupperade värden** i en ny grupp eller i en av de befintliga grupperna. Om du vill skapa en ny grupp markerar du två eller fler objekt (med CTRL + klicka) från rutan **Ej grupperade värden** och klickar på knappen **Gruppera** under rutan.

Du kan lägga till ett en grupperat värde i en befintlig grupp: bara markera det ej grupperade värdet och välj sedan den befintliga gruppen där du vill lägga till värdet och klicka på knappen **Gruppera**. Om du vill ta bort ett objekt från en grupp väljer du det från rutan **Grupper och medlemmar** och klickar sedan på **Dela upp grupp**. Du kan också välja om uppdelade kategorier ska placeras i den **andra** gruppen eller förbli uppdelade.

![](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> Du kan skapa grupper för varje fält i brunnen **Fält**, utan att behöva välja värden från ett befintligt visuellt objekt. Det är bara att högerklicka på fältet och välja **Grupp** från menyn som visas.
> 
> 

### <a name="using-binning"></a>Med hjälp av diskretisering
Du kan ange diskretiseringsstorlek för numeriska och tidvärden i **Power BI Desktop.** Du kan använda diskretisering för att anpassa storleken på data som visas i **Power BI Desktop**.

Om du vill använda en diskretiseringsstorlek högerklickar du på ett **fält** och väljer **Grupper**.

![](media/desktop-grouping-and-binning/grouping-binning_5.png)

Från fönstret **Grupper** kan du ange den önskade **diskretiseringsstorleken**.

![](media/desktop-grouping-and-binning/grouping-binning_6.png)

När du väljer **OK**, lägg märke till att ett nytt fält visas i rutan **Fält** med *(diskreta grupper)*. Du kan sedan dra fältet till arbetsytan för att använda diskretiseringsstorleken i ett visuellt objekt.

![](media/desktop-grouping-and-binning/grouping-binning_7.png)

Titta på den här [videon](https://www.youtube.com/watch?v=BRvdZSfO0DY) för att se hur **diskretisering** går till.

Och så enkelt är det att använda **gruppering** och **diskretisering** så att visuella objekt i dina rapporter visar data precis som du vill.

