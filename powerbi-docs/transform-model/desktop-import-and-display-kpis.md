---
title: Importera och visa KPI:er i Power BI
description: Importera och visa KPI:er
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: b12cc24c7ddddd0bc866a3bbeb23e0c7097711db
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86215250"
---
# <a name="import-and-display-kpis-in-power-bi"></a>Importera och visa KPI:er i Power BI
Med **Power BI Desktop**, kan du importera och visa KPI:er i tabeller, matriser och kort.

Följ de här stegen för att importera och visa KPI:er.

1. Starta med en Excel-arbetsbok som har en Power Pivot-modell och KPI:er. Den här övningen använder en arbetsbok som heter *KPI:er*.

1. Importera Excel-arbetsboken till Power BI med hjälp av **Arkiv -> Importera -> Innehåll i Excel-arbetsboken**. Du kan även [läsa hur man importerar arbetsböcker](../connect-data/desktop-import-excel-workbooks.md). 

1. Efter importen till Power BI, visas din KPI i rutan **Fält** som markerats med ![trafikljus](media/desktop-import-and-display-kpis/traffic.png)-ikonen. Om du vill använda en KPI i din rapporten, måste du expandera dess innehåll, vilket visar fälten **Värde**, **Mål** och **Status**.

    ![Skärmbild av Power BI Desktop med DeltaKPI expanderat i rutan Fält.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon2.png)
 
1. Importerade KPI:er är bäst att använda i standard visualiseringstyper som **Tabell**-typen. Power BI inkluderar även visualiseringstypen **KPI**, som bara bör användas för att skapa nya KPI:er.
   
    ![Skärmbild av Power BI Desktop med Table1-fälten valda i rutan Fält.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon3.png)

Det är allt det är. Du kan använda KPI:er för att markera trender, förlopp eller andra viktiga indikatorer.
