---
title: Påverkansanalys för datakälla
description: Förstå var din datakälla används.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/20/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: 2c9834310179d8936cda8b769e3b7e3f80d328e6
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254177"
---
# <a name="data-source-impact-analysis"></a>Påverkansanalys för datakälla

Med påverkansanalys för datakälla kan du se var datakällan används i organisationen. Det kan vara användbart när datakällan tillfälligt eller permanent tas offline, och du vill få en uppfattning om vem som påverkas. Det visar hur många arbetsytor, dataflöden och datamängder som använder datakällan och ger enkel navigering till arbetsytorna där de berörda dataflödena och datamängderna finns så att du kan undersöka ytterligare.

Påverkansanalys för datakälla kan också hjälpa dig att upptäcka dataduplicering i klientorganisationen, som när ett antal olika användare skapar liknande modeller på samma datakälla. Genom att hjälpa dig att identifiera sådana redundanta datamängder och dataflöden stöder påverkansanalys för datakälla målet att ha ”en enda sanningskälla”.

## <a name="perform-data-source-impact-analysis"></a>Utföra påverkansanalys för datakälla

Så här utför du påverkansanalys för datakälla:

1. Gå till den arbetsyta som innehåller den datakälla du är intresserad av och öppna [vyn för dataursprung](service-data-lineage.md).
1. Leta reda på datakällans kort och klicka på påverkansanalysikonen.

    ![Skärmbild av datakällans kort med knappen för påverkansanalys.](media/service-data-source-impact-analysis/data-source-impact-analysis-button.png)
 
Sidopanelen för påverkansanalys öppnas.

![Skärmbild av sidofönstret för påverkansanalys för datakälla.](media/service-data-source-impact-analysis/data-source-impact-analyis-side-pane.png)
 
* **Typ av datakälla**: Anger typ av datakälla
* **Sökväg till datakälla**: Sökväg till datakällan enligt definitionen i Power BI Desktop. Till exempel är sökvägen i bilden ovan till SQL Server-databasens datakälla anslutningssträngen ”twitterDB-yaronctestingdb1.database.windows.net”, enligt definitionen i Power BI Desktop (visas nedan). Den består av databasnamnet ”twitterDB” och servernamnet ”yaronctestingdb1.database.windows.net”.

    ![Skärmbild av definitionen av anslutningssträng i Power B I Desktop.](media/service-data-source-impact-analysis/connection-string-definition-in-desktop.png)
 
* **Sammanfattning av påverkan**: Visar antalet potentiellt påverkade arbetsytor, dataflöden och datamängder. Det här antalet omfattar arbetsytor du inte har åtkomst till.
* **Användning på detaljnivå**: Visar dig namnen på påverkade dataflöden och datamängder, för varje arbetsyta. Om du vill utforska vidare påverkan på en viss arbetsyta klickar du på arbetsytenamnet för att öppna arbetsytan. I den berörda arbetsytan använder du [påverkansanalys för datamängd](service-dataset-impact-analysis.md) för att se användningsinformationen om anslutna rapporter och instrumentpaneler.

## <a name="privacy"></a>Sekretess

I sidofönstret för påverkansanalysen ser du bara namnen på de arbetsytor, datamängder och dataflöden du har åtkomst till. Objekt du inte har åtkomst till visas som Begränsad åtkomst. Det här beror på att vissa objektnamn kan innehålla personlig information.
Sammanfattningen av påverkan innehåller alla påverkade dataflöden och datamängder, även dem som finns i arbetsytor du inte har åtkomst till.

## <a name="limitations"></a>Begränsningar

Påverkansanalys för datakälla stöds inte än för sidnumrerade rapporter, så du kan inte se om datakällan har någon direkt påverkan på dessa typer av rapporter i klientorganisationen.

## <a name="next-steps"></a>Nästa steg

* [Påverkansanalys för en datamängd](service-dataset-impact-analysis.md)
* [Dataursprung](service-data-lineage.md)