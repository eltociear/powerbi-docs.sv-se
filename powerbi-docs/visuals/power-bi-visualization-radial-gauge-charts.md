---
title: Diagram med radiella mätare i Power BI
description: Diagram med radiella mätare i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b0db9aebe72d54aa464ec012e614ae0ec5bc723
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390644"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Diagram med radiella mätare i Power BI

Ett diagram med radiell mätare har en cirkelformad båge och visar ett värde som mäter framstegen mot ett mål eller en Key Performance Indicator (KPI). Linjen (eller *nålen*) representerar målet eller målvärdet. Skuggningen representerar framstegen mot målet. Värdet i bågen representerar framstegsvärdet. Power BI sprider alla möjliga värden jämnt fördelade längs bågen, från det lägsta (värdet längst till vänster) till det högsta (värdet längst till höger).

![Skärmbild av radiell mätare.](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

I det här exemplet är du en bilåterförsäljare som spårar säljteamets genomsnittliga försäljning per månad. Nålen representerar ett försäljningsmål på 140 bilar. Minsta möjliga genomsnittliga försäljning är 0 och högsta är 200.  Den blå skuggningen visar att teamet snittar ca 120 försäljningar den här månaden. Som tur är, är det fortfarande en vecka kvar till målet.

Du kan också titta på när Will visar hur du skapar enskilda visuella måttobjekt: måttdiagram, kort och KPI:er.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>När är det bra att använda en radiell mätare

Radiella mätare är ett bra val för att:

* visa framsteg mot ett mål

* representera ett procentmått, t.ex. ett KPI

* visa hälsotillståndet för ett enskilt mått

* visa information som lätt kan sökas av och förstås.

## <a name="prerequisites"></a>Förutsättningar

* Power BI-tjänsten eller Power BI Desktop

* Excel-arbetsboken finansiellt exempel: [hämta exempelfilerna direkt](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Skapa en grundläggande radiell mätare

De här anvisningarna använder Power BI-tjänsten. Om du vill följa med kan du logga in på Power BI och öppna Excel finansiella exempelfilen.

### <a name="step-1-open-the-financial-sample-excel-file"></a>Steg 1: Öppna Excel-filen med finansexemplet

1. Ladda ned [Excel-filen Finansiellt exempel](../sample-financial-download.md) om du inte redan har gjort det. Kom ihåg var du sparar den.

1. Välj **Hämta data** > **Filer** i Power BI-tjänsten.

1. Välj **Lokal fil** och bläddra till platsen för exempelfilen.

1. Välj **Importera**. Power BI lägger till finansexemplet på din arbetsyta som en datamängd.

1. Från innehållslistan **Datamängder** väljer du ikonen **Skapa rapport** ikonen för **Finansiellt exempel**.

    ![Skärmbild av datamängdslistan med en pil som pekar på ikonen Skapa rapport för det finansiella exemplet.](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Steg 2: Skapa en mätare för att spåra bruttomarginalförsäljning

I det sista avsnittet, när du valde ikonen **Skapa rapport**, skapade Power BI en tom rapport i redigeringsvyn.

1. Välj **Bruttoförsäljning** i rutan **Fält**.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)

1. Ändra aggregering till **Genomsnitt**.

   ![Skärmbild av rutan Fält med bruttoförsäljning och genomsnittligt aggregerat framhävt.](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)

1. Välj mätarikonen ![Skärmbild av mätarikonen.](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) för att konvertera kolumndiagrammet till ett mätardiagram.

    ![Skärmbild av mätardiagrammet.](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

    Det kan hända att du, beroende på när du laddar ned filen **Finansiellt exempel**, får se siffror som inte stämmer överens med de här siffrorna.

    > [!TIP]
    > Som standard skapar Power BI ett mätardiagram där det antas att det aktuella värdet (i det här fallet **genomsnittlig bruttoförsäljning**) är mätarens mittpunkt. Eftersom den **genomsnittliga bruttoförsäljningen** är USD 182 760 är startvärdet (minst) 0 och slutvärdet (max) dubbla det aktuella värdet.

### <a name="step-3-set-a-target-value"></a>Steg 3: Ange ett målvärde

1. Dra **KSV** från rutan **Fält** till området **Målvärde**.

1. Ändra aggregering till **Genomsnitt**.

   Power BI lägger till en nål som representerar vårt målvärde på **145 480 $** .

   ![Skärmbild av mätardiagrammet med KSV-genomsnitt tillagt.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)

    Observera att vi har överskridit våra mål.

   > [!NOTE]
   > Du kan också ange ett målvärde manuellt. Se avsnittet om att [använda manuella formateringsalternativ för att ange värden för minimum, maximum och mål](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Steg 4: Ange ett maxvärde

I steg 2 använde Power BI fältet **Värde** för att automatiskt ange min- och maxvärden. Men vad händer om du vill ange ett eget maxvärde? Anta att du i stället för att använda dubbla det aktuella värdet som största möjliga värde, vill ställa in maxvärdet på den högsta bruttoförsäljningen i datamängden.

1. Dra **Bruttoförsäljning** från fönstret **Fält** till området **Maxvärde**.

1. Ändra aggregering till **Maxvärde**.

   ![Skärmbild av fältfönstret med bruttoförsäljning och maximalt aggregerat framhävt.](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)

   Mätaren ritas om med ett nytt slutvärde på 1,21 miljoner i bruttoförsäljning.

   ![Skärmbild av det färdiga mätardiagrammet.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Steg 5: Spara rapporten

1. [Spara rapporten](../service-report-save.md).

1. [Lägga till mätardiagrammet som en panel på instrumentpanelen](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Använd manuella formateringsalternativ för att ange värden för Minimum, Maximum och Mål nedan.

1. Ta bort **Maxvärde för bruttoförsäljning** från brunnen **Maxvärde**.

1. Välj rollerikonen för att öppna fönstret **Format**.

   ![Skärmbild av mätardiagrammet formatfönstret med rollerikonen framhävd.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Expandera **Mätaxel** och ange värden för **Min** och **Max**.

    ![Skärmbild av mätaxelsalternativen.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Rensa alternativet **KSV** i rutan **Fält** för att ta bort målvärdet.

    ![Skärmbild av det rensade KSV-alternativet.](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)

1. När fältet **Mål** visas under **Mätaraxeln** och ange ett värde.

     ![Skärmbild av mätaxelsalternativen med Mål framhävt.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Du kan också fortsätta formatera ditt mätardiagram.

När du är klar med de här stegen, har du ett mätardiagram som ser ut ungefär så här:

![Skärmbild av det slutliga mätardiagrammet.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Nästa steg

* [Visuella KPI-objekt (Key Performance Indicator)](power-bi-visualization-kpi.md)

* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)