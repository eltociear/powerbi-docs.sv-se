---
title: Utforska rapporter i Power BI-mobilappar
description: "Läs mer om att visa och interagera med rapporter i Power BI-mobilappar på din telefon eller surfplatta. Du skapar rapporter i Power BI-tjänsten eller Power BI Desktop och interagerar med dem i de mobila apparna. "
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 3515a57f88db1c8a7b12706680c0aade8b2cdbfa
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Utforska rapporter i Power BI-mobilappar
Gäller:

| ![iPhone](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android-telefon](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android-surfplatta](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10-enheter](media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone-enheter |iPad-surfplattor |Android-telefoner |Android-surfplattor |Windows 10-enheter |

En Power BI-rapport är en interaktiv vy över dina data med visuell information som representerar olika resultat och insikter från dessa data. Att visa rapporter i Power BI-mobilappar är det tredje steget i en trestegsprocess.

1. [Skapa rapporter i Power BI Desktop](desktop-report-view.md). Du kan även [optimera en rapport för telefoner](mobile-apps-view-phone-report.md) i Power BI Desktop. 
2. Publicera dessa rapporter till Power BI-tjänsten [(https://powerbi.com)](https://powerbi.com) eller [Power BI Report Server](report-server/get-started.md).  
3. Interagera sedan med dessa rapporter i Power BI-mobilappar.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Öppna en Power BI-rapport i mobilappen
Power BI-rapporter lagras på olika ställen i mobilappen, beroende på var du fick dem från. De kan vara i appar, delade med mig, arbetsytor (inklusive Min arbetsyta) eller på en rapportserver. Du går ibland igenom en relaterad instrumentpanel för att komma till en rapport och ibland listas de.

* I en instrumentpanel, knackar du på ellipsen (...) i det övre högra hörnet på en panel > **öppna rapporten**.
  
  ![Öppna rapporten](media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Alla paneler går inte att öppna i en rapport. Paneler som skapats genom att ställa en fråga i frågor och svar-rutan, öppnar inte rapporter när du klickar på dem. 
  
  På en telefon öppnas rapporten i liggande läge, om den inte har [optimerats för visning på en telefon](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones).
  
  ![Telefonrapport i liggande läge](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>Visa rapporter optimerade för telefoner
Power BI-rapportskribenter kan skapa en rapportlayout som optimerats för telefoner. I en lista över rapporter, har en optimerad rapport en särskild ikon ![Telefonrapportikon](media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png):

![Öppna telefonrapporten](media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

När du visar den rapporten på en telefon, öppnas den i stående vy.

![Rapport i stående vy](media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

En rapport kan ha en blandning av sidor som inte är optimerade för telefoner. I så fall, kommer vyn att ändras från stående till liggande läge för varje sida, när du bläddrar genom rapporten.

Läs mer om [rapporter optimerade för telefonvy](mobile-apps-view-phone-report.md).

## <a name="use-slicers-to-filter-a-report-page"></a>Använd utsnitt för att filtrera en rapportsida
När du skapar en rapport i Power BI-tjänsten [(https://powerbi.com)](https://powerbi.com), bör du tänka på att på en telefon kan du inte se filterfönstret, men du kan [se utsnitt på en rapportsida](power-bi-visualization-slicers.md). Lägg till utsnitt i en rapport så att du och dina kollegor kan använda utsnitt för att filtrera sidan på en telefon.

* När du väljer ett värde i ett utsnitt på rapportsidan, filtreras övrig visuell information på sidan.
  
  ![Rapportutsnitt](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  I den här bilden, filtrerar utsnittet stapeldiagrammet för att endast visa julivärden.

## <a name="cross-filter-and-highlight-a-power-bi-report-page"></a>Korsfiltrera och markera en Power BI-rapportsida
När du väljer ett värde i en visuell information så filtreras inte övrig visuell information. Den visar relaterade värden i övrig visuell information.

* Knacka på ett värde i en visualisering.
  
  ![Korsfiltrera en sida](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  Om du trycker på den stora kolumnen i en visuell information så markeras relaterade värden i övrig visuell information. 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>Sortera en visualisering på en iPad eller en surfplatta
* Tryck på diagrammet, tryck på ellipsen (**...** ) och tryck på fältnamnet.
  
   ![Sortera en visualisering](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* För att kasta om sorteringsordningen, trycker du på ellipsen (**...** ) igen och trycker sedan på samma fältnamn igen.

## <a name="drill-down-and-up-in-a-visual-on-an-ipad-or-a-tablet"></a>Öka eller minska detaljnivån i visuell information på en iPad eller en surfplatta
Om en rapportförfattare har lagt till den här funktionen i en visualisering, kan du öka detaljnivån för visuell information för att se värdena som utgör en del av den. Du kan [lägga till öka detaljnivån för en visualisering](power-bi-visualization-drill-down.md) i Power BI Desktop eller Power BI-tjänsten. 

> [!NOTE]
> För tillfället fungerar det inte att öka detaljnivån för kartor på en iPad eller surfplatta.
> 
> 

* Tryck på någon visuell information. Om den har upp- och nedpilar i de övre hörnen ![Ikoner för att öka, minska detaljnivån](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-down.png)så kan du öka detaljnivån. Om du vill öka detaljnivån för ett värde, trycker du på pilen i det övre högra hörnet och sedan ett värde i visualiseringen &#151; i det här fallet, den mörkblå FD-04-bubblan.
  
  ![Öka detaljnivån i ett visuellt objekt](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-one.png)
* Tryck på uppåt-pilen i det övre vänstra hörnet för att minska detaljnivån igen.
  
  ![Minska detaljnivån](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up.png)

## <a name="go-back-to-my-workspace"></a>Gå tillbaka till Min arbetsyta
* Tryck på pilen bredvid rapportnamnet > tryck på **Min arbetsyta**.
  
  ![Gå tillbaka upp](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-back.png)

## <a name="next-steps"></a>Nästa steg
* [Visa och interagera med Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md)
* [Skapa en version av en rapport som är optimerad för telefoner](desktop-create-phone-report.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

