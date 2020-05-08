---
title: Del 1, Lägg till visualiseringar i en Power BI-rapport
description: Del 1, Lägg till visualiseringar i en Power BI-rapport
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b275d4e7fdb4e289d2331a2f58db504071ea609b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758610"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Lägga till visuella objekt i en Power BI-rapport (del 1)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Den här artikeln ger en snabb introduktion till att skapa en visualisering i en rapport. Den gäller för både Power BI-tjänsten och Power BI Desktop. För mer avancerat innehåll, [se del 2](power-bi-report-add-visualizations-ii.md) i den här serien. Amanda visar ett par sätt att skapa, redigera och formatera visuella objekt på rapportarbetsytan. Prova sedan att skapa en egen rapport med hjälp av den [Försäljning- och marknadsföringsexempel](../sample-datasets.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Förutsättningar

I den här självstudien används [pbix-filen Sales & marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).

1. Välj **Arkiv** > **Öppna** uppe till vänster i menyraden i Power BI Desktop
   
2. Leta rätt på din kopia av **pbix-exempelfilen Sales and marketing**

1. Öppna **PBIX-exempelfilen Sales and marketing** i rapportvyn ![Skärmbild av rapportvyikonen.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Välj ![Skärmbild av den gula fliken.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) för att lägga till en ny sida.

## <a name="add-visualizations-to-the-report"></a>Lägg till visuella objekt i rapporten

1. Skapa ett visuellt objekt genom att välja ett fält från fönstret **Fält**.

    Börja med ett numeriskt fält som **Sales** > **TotalSales**. Power BI skapar ett stapeldiagram med en enda kolumn.

    ![Skärmbild av ett kolumndiagram med en enda kolumn.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    Eller börja med ett kategorifält, till exempel **Namn** eller **Produkt**. Power BI skapar en tabell och lägger till fältet till området **Värden**.

    ![Skärmbild av en tabell med fyra kategorier](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Eller börja med ett geografiskt fält, till exempel **Geo** > **Stad**. Power BI och Bing Maps skapar en kartvisualisering.

    ![Skärmbild av en kartvisualisering.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Ändra typen av visualisering

 Skapa en visualisering och ändra dess typ. 
 
 1. Välj **Produkt** > **Kategori** och sedan **Produkt** > **Antal produkter** för att lägga till dem i området **Värden**.

    ![Skärmbild av fönstret Fält med området Värden framhävt.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Ändra visualiseringen till ett kolumndiagram genom att välja ikonen för **staplade kolumndiagram**.

   ![Skärmbild av visualiseringsfönstret med ikonen för staplat kolumndiagram framhävd.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Du ändrar hur det visuella objektet sorteras genom att välja **Fler åtgärder** (...).  Använd sorteringsalternativen till att ändra sorteringsordningen (stigande eller fallande) och ändra vilken kolumn som används till sorteringen (**Sortera efter**).

   ![Skärmbild av listrutan Fler åtgärder.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Nästa steg

 Fortsätt till:

* [Del 2: Lägg till visualiseringar i en Power BI-rapport](power-bi-report-add-visualizations-ii.md)

* [Interagera med visualiseringar](../consumer/end-user-reading-view.md) i rapporten.

