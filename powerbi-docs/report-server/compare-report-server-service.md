---
title: En jämförelse av Power BI-rapportservern och Power BI-tjänsten
description: I den här artikeln jämförs funktionerna i Power BI-rapportservern och Power BI-tjänsten.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.date: 09/13/2019
ms.openlocfilehash: d2c0ab82a3b262a975c461a4414ed7fd3b1bc060
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075909"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>En jämförelse av Power BI-rapportservern och Power BI-tjänsten

Power BI-rapportservern och Power BI-tjänsten har många likheter och vissa viktiga skillnader. Den här tabellen beskriver vad som är vad.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funktioner i Power BI-rapportservern och i Power BI-tjänsten

| Funktioner | Power BI-rapportserver | Power BI-tjänst | Anteckningar |
|---------|---------|---------|---------|
| Distribution | Lokal eller värdbaserat moln | Moln | Power BI-rapportservern kan distribueras i virtuella Azure-datorer (värdbaserat moln) om den är licensierad via Power BI Premium. |
| Källdata | I molnet och/eller lokalt | I molnet och/eller lokalt |  |
| Licens | Power BI Premium eller SQL Server EE med SA | Power BI Pro och/eller för Power BI Premium | |  
| Livscykel | Modern livscykelprincip | Helt hanterad tjänst |  |
| Publiceringscykeln | Var fjärde månad | En gång i månaden | De senaste funktionerna och korrigeringarna levereras till Power BI-tjänsten först. De flesta grundläggande funktionerna kommer till Power BI-rapportservern under de kommande versionerna och vissa funktioner är endast avsedda för Power BI-tjänsten. |
| Skapa Power BI-rapporter i Power BI Desktop | Ja | Ja |  |
| Skapa Power BI-rapporter i webbläsaren | Nej | Ja |  |
| Gateway krävs | Nej | Ja, för lokala datakällor |  |
| Realtidsuppspelning | Nej | Ja | [Realtidsuppspelning i Power BI](../service-real-time-streaming.md) |
| Instrumentpaneler | Nej | Ja | [Instrumentpaneler i Power BI-tjänsten](../consumer/end-user-dashboards.md) |
| Distribuera grupp av rapporter med hjälp av appar | Nej | Ja | [Skapa och publicera appar med instrumentpaneler och rapporter](../service-create-distribute-apps.md) |
| Innehållspaket | Nej | Ja | [Organisationsinnehållspaket: Introduktion](../service-organizational-content-pack-introduction.md) |
| Ansluta till tjänster som Salesforce | Ja | Ja | [Ansluta till de tjänster som du använder](../service-connect-to-services.md) med innehållspaket i Power BI-tjänsten. I Power BI-rapportservern använder du certifierade kopplingar för att ansluta till tjänster. Mer information finns i [Power BI-rapportdatakällor i Power BI-rapportserver](data-sources.md). |
| Frågor och svar | Nej | Ja | [Frågor och svar i Power BI-tjänsten och Power BI Desktop](../power-bi-tutorial-q-and-a.md) 
| Snabba insikter | Nej | Ja | [Automatiskt skapa datainsikter med Power BI](../consumer/end-user-insights.md) |
| Analysera i Excel | Nej | Ja | [Analysera i Excel](../service-analyze-in-excel.md) 
| Sidnumrerade rapporter | Ja | Ja | [Sidnumrerade rapporter är tillgängliga i Power BI-tjänsten](../paginated-reports-report-builder-power-bi.md) som en förhandsversion i Premium-kapacitet |
| Power BI-mobilappar | Ja | Ja | [Översikt över Power BI-mobilappar](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ArcGIS-mappar | Nej | Ja | [ArcGIS-kartor i Power BI-tjänsten och Power BI Desktop från Esri](../visuals/power-bi-visualization-arcgis.md) |
| E-postprenumerationer för Power BI-rapporter | Nej | Ja | [Skapa en prenumeration åt dig eller andra](../service-report-subscribe.md) på en rapport eller instrumentpanel i Power BI-tjänsten |
| E-postprenumerationer för sidnumrerade rapporter | Ja | Ja | [Skapa en prenumeration åt dig själv och andra på en sidnumrerad rapport i Power BI-tjänsten](../paginated-reports-subscriptions.md)<br><br>[E-postleverans i Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  |
| Datavarningar | Nej | Ja | [Datavarningar](../service-set-data-alerts.md) i Power BI-tjänsten
| Säkerhet på radnivå (RLS) | Ja | Ja | Tillgängligt i både DirectQuery- (datakälla) och Import-läge <br><br>Säkerhet på radnivå (RLS) med [Power BI-tjänsten](../service-admin-rls.md) <br><br>Säkerhet på radnivå (RLS) i [Power BI-rapportservern](row-level-security-report-server.md) |
| Helskärmsläge | Nej | Ja | [Helskärmsläge](../consumer/end-user-focus.md) i Power BI-tjänsten |
| Avancerat Office 365-samarbete | Nej | Ja | [Samarbeta på en apparbetsyta](../service-collaborate-power-bi-workspace.md) med Office 365 |
| R-visualiseringar | Nej | Ja | [Skapa visuella R-objekt](../desktop-r-visuals.md) i Power BI Desktop och publicera dem till Power BI-tjänsten. Du kan inte spara Power BI-rapporter med visuella R-objekt till Power BI-rapportserver.  |
| Förhandsgranskningsfunktioner | Nej | Ja | [Anmäl dig till förhandsversionsfunktioner](../consumer/end-user-preview-features.md) i Power BI-tjänsten |
| Anpassade visuella objekt | Ja | Ja | [Anpassade visuella objekt i Power BI](../power-bi-custom-visuals.md) |
| Power BI Desktop | Version som är optimerad för rapportservern och som kan laddas ned med rapportservern | Version som är optimerad för Power BI-tjänsten, tillgänglig från Windows Store | [Power BI Desktop för rapportservern](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop för Power BI-tjänsten](http://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Nästa steg

[Installera Power BI-rapportserver](install-report-server.md)
