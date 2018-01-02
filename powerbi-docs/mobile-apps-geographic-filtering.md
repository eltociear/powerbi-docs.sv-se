---
title: Filterrapport efter geografisk plats i en Power BI-mobilapp
description: "Lär dig hur du kan filtrera en rapport efter din geografiska plats i Microsoft Power BI-mobilappar om rapportägaren har konfigurerat geografiska taggar."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
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
ms.openlocfilehash: 340df05c0fcf4e839f8c6223d513ec55964fb5de
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Filtrera en rapport efter geografisk plats i Power BI-mobilappar
Gäller:

| ![iPhone](media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android-telefon](media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android-surfplatta](media/mobile-apps-geographic-filtering/android-tablet-logo-50-px.png) | ![Android-surfplatta](media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone-enheter |iPad-surfplattor |Android-telefoner |Android-surfplattor |Windows 10-telefoner |

Ser du en liten kartnålsikon i det övre högra hörnet när du tittar på en Power BI-rapport på din mobila enhet? I så fall kan du filtrera rapporten baserat på var du befinner dig.

> [!NOTE]
> Du kan bara filtrera efter plats om geografiska namn i rapporten är på engelska, t.ex. New York City eller Germany. Windows 10-surfplattor och datorer stöder inte geografisk filtrering, men det gör Windows 10-telefoner.
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>Filtrera din rapport efter geografisk plats
1. Öppna en rapport i Power BI-mobilappen på din mobila enhet.
2. Om rapporten innehåller geografiska data visas ett meddelande där Power BI ber dig om åtkomst till din plats. Klicka på **Tillåt**, och tryck sedan på **Tillåt** igen.
3. Tryck på kartnålen ![Kartnålsikon](media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). Du kan filtrera efter ort, region eller land/region, beroende på rapportens data. Filtret innehåller endast alternativ som matchar din aktuella plats.
   
    ![Kartnålsfilter](media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Varför ser jag inga platstaggar i rapporten?
Alla följande tre villkor måste vara uppfyllda för att du ska kunna se platstaggar. 

* Den person som skapade rapporten i Power BI Desktop [kategoriserade geografiska data](desktop-mobile-geofiltering.md) för minst en kolumn, t.ex. City, State eller Country/Region.
* Du befinner dig på en av de platser som har data i den kolumnen.
* Du använder någon av följande mobila enheter:
  * iOS (iPad, iPhone, iPod).
  * Android-telefon eller surfplatta.
  * Windows 10-telefon (andra Windows 10-enheter, t.ex. stationära datorer och surfplattor stöder inte geografisk filtrering).

Läs mer om [Konfigurera geografiskt filtrering](desktop-mobile-geofiltering.md) i Power BI Desktop.

### <a name="next-steps"></a>Nästa steg
* [Ansluta till Power BI-data från verkligheten](mobile-apps-data-in-real-world-context.md) med mobilapparna
* [Datakategorisering i Power BI Desktop](desktop-data-categorization.md) 
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

