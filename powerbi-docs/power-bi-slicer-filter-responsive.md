---
title: Skapa ett dynamiskt utsnitt som du kan ändra storlek på i Power BI
description: Lär dig hur du skapar ett dynamiskt utsnitt som du kan ändra storlek på så att det passar din rapport
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/04/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: fed4119946cb762fb4d9aee3b5300be225a6e379
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61419912"
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi"></a>Skapa ett dynamiskt utsnitt som du kan ändra storlek på i Power BI

Dynamiska utsnitt ändrar storlek för att passa i alla olika utrymmen i rapporten. Du kan ändra storlek på de dynamiska utsnitten till olika storlekar och former, från vågräta till kvadratiska, till lodräta och värdena i utsnittet ordnar om sig själva på samma sätt som du gör. I Power BI Desktop och Power BI-tjänsten kan du göra vågräta utsnitt och datum-/intervallutsnitt dynamiska. Datum-/intervallutsnitt har också förbättrade pekområden så att det är lättare att ändra dem med ett fingertryck. Du kan göra dynamiska utsnitt så små eller stora som du vill. De ändrar också storlek automatiskt så att de passar bra för rapporter i Power BI-tjänsten och även i Power BI-appar. 

![Dynamiska utsnitt kan ha olika former](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer.gif)

## <a name="create-a-slicer"></a>Skapa ett utsnitt

Det första steget för att skapa ett dynamiskt utsnitt är att skapa ett grundläggande utsnitt. 

1. Välj ikonen **Utsnitt** ![Utsnittsikonen](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer-icon.png) i fönstret **Visualiseringar**.
2. Dra fältet som du vill filtrera till **Fält**.

    ![Lägg till ett fält till utsnittet](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-1-create.png)

## <a name="convert-to-a-horizontal-slicer"></a>Konvertera till ett vågrätt utsnitt

1. Med det valda utsnittet väljer du fliken **Format** i fönstret **Visualiseringar**.
2. Expandera avsnittet **Allmänt** och välj sedan **Vågrätt** som **Orientering**.

    ![Ange utsnittet till vågrätt](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-2-horizontal.png) 

1.  Du vill förmodligen göra det bredare för att visa fler värden.

     ![Gör utsnittet bredare](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-3-wider.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>Gör det dynamiskt och experimentera med det

Det här steget är enkelt. 

1. Precis under **Orientering** i avsnittet **Allmänt** under fliken **Format** drar du **Responsiv** till **På**.  

    ![Utsnittet är nu dynamiskt](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-4-responsive-on.png)

1. Nu kan du experimentera med det. Dra i hörnen för att göra det kortare, längre, bredare och smalare. Om du gör det tillräckligt litet, blir det bara en filterikon.

    ![Dynamiskt utsnitt som är så litet så det är en filterikon](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-5-mini-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>Lägg till det i en telefonrapportlayout

I Power BI Desktop kan du skapa en telefonlayout för varje sida i en rapport. Om en sida har en telefonlayout, visas den på en mobiltelefon i stående vy. I annat fall måste du visa den i liggande vy. 

1. På menyn **Visa** väljer du **Telefonlayout**.

     ![Ikon för telefonlayout, menyn Visa](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-6-phone-layout-button.png)
    
1. Dra all visuell information du vill ha i telefonrapporten till rutnätet. Dra det dynamiska utsnittet till den storlek du önskar – i det här fallet bara en filterikon.

    ![Lägg till utsnittet till telefonrapportlayouten](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-7-phone-slicer-icon.png)

Läs mer om hur du skapar [rapporter som är optimerade för Power BI-appar](desktop-create-phone-report.md).

## <a name="make-a-time-or-range-slicer-responsive"></a>Gör ett tids- eller intervallutsnitt dynamiskt

Du kan följa samma steg för att göra en panel eller ett intervallutsnitt dynamiskt. När du ställer in **Dynamiskt** till **På**, upptäcker du några saker:

- Visuell information optimerar ordningen på indatarutorna beroende på arbetsytans storlek. 
- Visningen av dataelement är optimerad för att göra utsnittet så användbart som möjligt, baserat på den storleken som är tillåten på arbetsytan. 
- Nya runda handtag på reglagen optimerar pekinteraktioner. 
- När en visuell information blir för liten för att användas, blir den en ikon som representerar typen av visuell information i dess ställe. För att interagera med den dubbelklickar du bara på den för att öppna den i Fokusläge. Detta sparar värdefullt utrymme på sidan utan att förlora funktionerna.

## <a name="next-steps"></a>Nästa steg

- [Utsnitt i Power BI-tjänsten](visuals/power-bi-visualization-slicers.md)
- Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)