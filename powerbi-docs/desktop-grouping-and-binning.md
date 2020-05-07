---
title: Använd gruppering i Power BI Desktop
description: Lär dig att gruppera och diskretisera element i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 525f7bf4c967722d8f98a9184127bc8c7907cea1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75729933"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Använd gruppering i Power BI Desktop
När Power BI Desktop skapar visuella objekt aggregeras dina data i segment (eller grupper) baserat på värdena i underliggande data. Det är ofta bra, men ibland vill du begränsa hur dessa segmentvisas. Du kanske exempelvis vill placera tre produktkategorier i en större kategori (en *grupp*). Du vill kanske se försäljningssiffror i diskreta enheter om 1 000 000 kronor istället för att visa storleken 923 983 kronor.

Du kan *gruppera* datapunkter i Power BI Desktop, vilket hjälper dig att tydligt visa, analysera och utforska data och trender i visuella objekt. Du kan också definiera en *diskretiseringsstorlek* som gör att värden placeras i lika stora grupper som gör det enklare att visa informationen tydligt. Den här åtgärden kallas ofta för *diskretisering*.

## <a name="using-grouping"></a>Med gruppering
När du ska använda gruppering väljer du två eller flera element i ett visuellt objekt genom att Ctrl+klicka. Högerklicka sedan på ett av de valda elementen och välj **Grupp** på snabbmenyn.

![Kommandot Grupp, graf, gruppering, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_1.png)

När du har skapat gruppen läggs den till i bucketen **Förklaring** för det visuella objektet. Gruppen visas också i listan **Fält**.

![Listorna Förklaring och Fält, gruppering, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_2.png)

När du har en grupp kan du enkelt redigera gruppens medlemmar. Högerklicka på fältet i bucketen **Förklaring** eller i listan **Fält** och välj sedan **Redigera grupper**.

![Kommandot Redigera grupper, listorna Förklaring och Fält, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_3.png)

I dialogrutan **Grupper** kan du skapa nya grupper och ändra befintliga grupper. Du kan också *byta namn* på dina grupper. Dubbelklicka bara på grupprubriken i rutan **Grupper och medlemmar** och ange sedan det nya namnet.

Du kan göra många olika saker med grupper. Du kan lägga till objekt från listan **Ej grupperade värden** i en ny grupp eller i en av de befintliga grupperna. Om du vill skapa en ny grupp markerar du två eller flera objekt (genom att Ctrl+klicka) i rutan **Ej grupperade värden** och väljer sedan knappen **Gruppera** under rutan.

Du kan lägga till ett ej grupperat värde i en befintlig grupp: markera det **ej grupperade värdet**, markera den befintliga gruppen där du vill lägga till värdet och välj knappen **Gruppera**. Om du vill ta bort ett objekt från en grupp markerar du det i rutan **Grupper och medlemmar** väljer sedan **Dela upp grupp**. Du kan också flytta ej grupperade kategorier till gruppen **Andra** eller låta dem vara enskilda.

![Dialogrutan Grupper, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> Du kan skapa grupper för valfritt fält i brunnen **Fält** utan att behöva välja flera objekt från ett befintligt visuellt objekt. Det är bara att högerklicka på fältet och välja **Ny grupp** på den meny som visas.

## <a name="using-binning"></a>Med hjälp av diskretisering
Du kan ange diskretiseringsstorlek för numeriska och tidvärden i **Power BI Desktop.** Du kan använda diskretisering till att anpassa storleken för data som visas i Power BI Desktop.

Om du vill använda en diskretiseringsstorlek högerklickar du på ett **fält** och väljer **Ny grupp**.

![Kommandot Ny grupp, listan Fält, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_5.png)

I dialogrutan **Grupper** kan du ange önskad **diskretiseringsstorlek**.

![Diskretiseringsstorlek, dialogrutan Grupper, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_6.png)

När du väljer **OK**, lägg märke till att ett nytt fält visas i rutan **Fält** med **(diskreta grupper)** . Du kan sedan dra fältet till arbetsytan för att använda diskretiseringsstorleken i ett visuellt objekt.

![Dra fältet för diskreta grupper till arbetsytan, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_7.png)

Titta på den här *videon* för att se hur [diskretisering](https://www.youtube.com/watch?v=BRvdZSfO0DY) går till.

Och så enkelt är det att använda *gruppering* och *diskretisering* så att visuella objekt i dina rapporter visar data precis som du vill.
