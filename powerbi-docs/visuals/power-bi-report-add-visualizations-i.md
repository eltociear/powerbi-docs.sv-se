---
title: Del 1, Lägg till visualiseringar i en Power BI-rapport
description: Del 1, Lägg till visualiseringar i en Power BI-rapport
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299222"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Del 1, Lägg till visualiseringar i en Power BI-rapport

Den här artikeln ger en snabb introduktion till att skapa en visualisering i en rapport. Den gäller för både Power BI-tjänsten och Power BI Desktop. För mer avancerat innehåll, [se del 2](power-bi-report-add-visualizations-ii.md) i den här serien. Amanda visar ett par sätt att skapa, redigera och formatera visuella objekt på rapportarbetsytan. Prova sedan att skapa en egen rapport med hjälp av den [Försäljning- och marknadsföringsexempel](../sample-datasets.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Öppna en rapport och lägg till en ny sida

1. Öppna en rapport i [redigeringsvyn](../service-interact-with-a-report-in-editing-view.md).

    Den här kursen använder exemplet för [försäljning och marknadsföring](../sample-datasets.md).

1. Om fönstret **Fält** inte visas, väljer du pilikonen för att öppna det.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Lägg till en tom sida i rapporten.

## <a name="add-visualizations-to-the-report"></a>Lägg till visuella objekt i rapporten

1. Skapa ett visuellt objekt genom att välja ett fält från fönstret **Fält**.

    Börja med ett numeriskt fält som **SalesFact** > **Försäljning i USD**. Power BI skapar ett stapeldiagram med en enda kolumn.

    ![Skärmbild av ett kolumndiagram med en enda kolumn.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    Eller börja med ett kategorifält, till exempel **Namn** eller **Produkt**. Power BI skapar en tabell och lägger till fältet till området **Värden**.

    ![GIF för en person som väljer produkt och sedan en kategori för att skapa en tabell.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Eller börja med ett geografiskt fält, till exempel **Geo** > **Stad**. Power BI och Bing Maps skapar en kartvisualisering.

    ![Skärmbild av en kartvisualisering.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Skapa en visualisering och ändra dess typ. Välj **Produkt** > **Kategori** och sedan **Produkt** > **Antal produkter** för att lägga till dem i området **Värden**.

   ![Skärmbild av fönstret Fält med området Värden framhävt.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Ändra visualiseringen till ett kolumndiagram genom att välja ikonen för **staplade kolumndiagram**.

   ![Skärmbild av visualiseringsfönstret med ikonen för staplat kolumndiagram framhävd.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. När du skapar visualiseringar i rapporten kan du [fästa dem på din instrumentpanel](../service-dashboard-pin-tile-from-report.md). Välj fästikonen för att fästa visualiseringen ![Skärmbild av fästikonen.](media/power-bi-report-add-visualizations-i/pinnooutline.png)

   ![Skärmbild av en kolumndiagramsvisualisering med fästikonen framhävd.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Nästa steg

 Fortsätt till:

* [Del 2: Lägg till visualiseringar i en Power BI-rapport](power-bi-report-add-visualizations-ii.md)

* [Interagera med visualiseringar](../consumer/end-user-reading-view.md) i rapporten.

* [Gör ännu mer med visualiseringar](power-bi-report-visualizations.md).

* [Spara rapporten](../service-report-save.md).
