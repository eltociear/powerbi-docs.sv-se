---
title: Filterrapport efter geografisk plats i en Power BI-mobilapp
description: Lär dig hur du kan filtrera en rapport efter din geografiska plats i Microsoft Power BI-mobilappar om rapportägaren har konfigurerat geografiska taggar.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 4cf94628b1d423d5b382e718d850fc403d516083
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85234327"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Filtrera en rapport efter geografisk plats i Power BI-mobilappar
Gäller för:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android-telefon](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android-surfplatta](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Windows-telefon](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone-enheter |iPad-surfplattor |Android-telefoner |Android-surfplattor |Windows 10-telefoner |

Ser du en liten kartnålsikon i det övre högra hörnet när du tittar på en Power BI-rapport på din mobila enhet? I så fall kan du filtrera rapporten baserat på var du befinner dig.

> [!NOTE]
> Du kan bara filtrera efter plats om geografiska namn i rapporten är på engelska, t.ex. New York City eller Germany. Windows 10-surfplattor och datorer stöder inte geografisk filtrering, men det gör Windows 10-telefoner.

>[!NOTE]
>Stöd för Power BI-mobilappen för **telefoner som använder Windows 10 Mobile** kommer att upphöra den 16 mars 2021. [Läs mer](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="filter-your-report-by-your-geographic-location"></a>Filtrera din rapport efter geografisk plats
1. Öppna en rapport i Power BI-mobilappen på din mobila enhet.
2. Om rapporten innehåller geografiska data visas ett meddelande där Power BI ber dig om åtkomst till din plats. Klicka på **Tillåt**, och tryck sedan på **Tillåt** igen.
3. Tryck på kartnålen ![Kartnålsikon](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). Du kan filtrera efter ort, region eller land/region, beroende på rapportens data. Filtret innehåller endast alternativ som matchar din aktuella plats.
   
    ![Kartnålsfilter](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Varför ser jag inga platstaggar i rapporten?
Alla följande tre villkor måste vara uppfyllda för att du ska kunna se platstaggar. 

* Den person som skapade rapporten i Power BI Desktop måste ha [kategoriserade geografiska data](../../transform-model/desktop-mobile-geofiltering.md) för minst en kolumn, t.ex. City, State eller Country/Region.
* Du befinner dig på en av de platser som har data i den kolumnen.
* Du använder någon av följande mobila enheter:
  * iOS (iPad, iPhone, iPod).
  * Android (telefon, surfplatta).
  * Windows 10-telefon (andra Windows 10-enheter, t.ex. stationära datorer och surfplattor stöder inte geografisk filtrering).

Läs mer om [Konfigurera geografiskt filtrering](../../transform-model/desktop-mobile-geofiltering.md) i Power BI Desktop.

### <a name="next-steps"></a>Nästa steg
* [Ansluta till Power BI-data från verkligheten](mobile-apps-data-in-real-world-context.md) med mobilapparna
* [Datakategorisering i Power BI Desktop](../../transform-model/desktop-data-categorization.md) 
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
