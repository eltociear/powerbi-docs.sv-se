---
title: En jämförelse av Power BI-rapportservern och Power BI-tjänsten
description: I den här artikeln jämförs funktionerna i Power BI-rapportservern och Power BI-tjänsten.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 07/27/2020
ms.openlocfilehash: c91642a08642a52b333ccba14078068eaa9ba616
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87252876"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>En jämförelse av Power BI-rapportservern och Power BI-tjänsten

Power BI-rapportservern och Power BI-tjänsten har många likheter och vissa viktiga skillnader. Den här tabellen beskriver vad som är vad.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funktioner i Power BI-rapportservern och i Power BI-tjänsten

| Funktioner | Power BI-rapportserver | Power BI-tjänst | Anteckningar |
|---------|---------|---------|---------|
| Distribution | Lokal eller värdbaserat moln | Molnet | Power BI-rapportservern kan distribueras i virtuella Azure-datorer (värdbaserat moln) om den är licensierad via Power BI Premium eller SQL Server Enterprise med Software Assurance.|
| Källdata | I molnet och/eller lokalt | I molnet och/eller lokalt |  |
| Licens | Power BI Premium eller SQL Server EE med Software Assurance (SA) | Power BI Pro och/eller för Power BI Premium | |  
| Livscykel | Modern livscykelprincip | Helt hanterad tjänst |  |
| Publiceringscykeln | Tre gånger per år (januari, maj, september) | En gång i månaden | De senaste funktionerna och korrigeringarna levereras till Power BI-tjänsten först. En sammanfattning av funktioner från Power BI Desktop-versioner för tjänsten kommer i Power BI-rapportservern i varje version. De flesta andra funktioner är endast avsedda för Power BI-tjänsten. |
| Skapa Power BI-rapporter i Power BI Desktop | Ja | Ja |  |
| Skapa Power BI-rapporter i webbläsaren | Nej | Ja |  |
| Vara värd för och ansluta till delade datamängder i Power BI | Nej | Ja | [Introduktion till datamängder på arbetsytor](../connect-data/service-datasets-across-workspaces.md) |
| Gateway krävs | Nej | Ja, för lokala datakällor |  |
| Realtidsuppspelning | Nej | Ja | [Realtidsuppspelning i Power BI](../connect-data/service-real-time-streaming.md) |
| Instrumentpaneler | Nej | Ja | [Instrumentpaneler i Power BI-tjänsten](../consumer/end-user-dashboards.md) |
| Distribuera grupp av rapporter med hjälp av appar | Nej | Ja | [Skapa och publicera appar med instrumentpaneler och rapporter](../collaborate-share/service-create-distribute-apps.md) |
| Innehållspaket | Nej | Ja | [Organisationsinnehållspaket: Introduktion](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Ansluta till tjänster som Salesforce | Ja | Ja | [Ansluta till de tjänster som du använder](../connect-data/service-connect-to-services.md) med innehållspaket i Power BI-tjänsten. I Power BI-rapportservern använder du certifierade kopplingar för att ansluta till tjänster. Mer information finns i [Power BI-rapportdatakällor i Power BI-rapportserver](data-sources.md). |
| Frågor och svar | Nej | Ja | [Frågor och svar i Power BI-tjänsten och Power BI Desktop](../create-reports/power-bi-tutorial-q-and-a.md) 
| Snabba insikter | Nej | Ja | [Automatiskt skapa datainsikter med Power BI](../consumer/end-user-insights.md) |
| Analysera i Excel | Nej | Ja | [Analysera i Excel](../collaborate-share/service-analyze-in-excel.md) 
| Sidnumrerade rapporter | Ja | Ja | [Sidnumrerade rapporter är tillgängliga i Power BI-tjänsten](../paginated-reports/paginated-reports-report-builder-power-bi.md) som en förhandsversion i Premium-kapacitet |
| Power BI-mobilappar | Ja | Ja | [Översikt över Power BI-mobilappar](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ArcGIS-mappar | Nej | Ja | [ArcGIS-kartor i Power BI-tjänsten och Power BI Desktop från Esri](../visuals/power-bi-visualization-arcgis.md) |
| E-postprenumerationer för Power BI-rapporter | Nej | Ja | [Skapa en prenumeration åt dig eller andra](../collaborate-share/service-report-subscribe.md) på en rapport eller instrumentpanel i Power BI-tjänsten |
| E-postprenumerationer för sidnumrerade rapporter | Ja | Ja | [Skapa en prenumeration åt dig själv och andra på en sidnumrerad rapport i Power BI-tjänsten](../consumer/paginated-reports-subscriptions.md)<br><br>[E-postleverans i Reporting Services](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Datavarningar | Nej | Ja | [Datavarningar](../create-reports/service-set-data-alerts.md) i Power BI-tjänsten
| Säkerhet på radnivå (RLS) | Ja | Ja | Tillgängligt i både DirectQuery- (datakälla) och Import-läge <br><br>Säkerhet på radnivå (RLS) med [Power BI-tjänsten](../admin/service-admin-rls.md) <br><br>Säkerhet på radnivå (RLS) i [Power BI-rapportservern](row-level-security-report-server.md) |
| Detaljerad korsrapport | Nej | Ja | [Använda detaljerade korsrapporter](../create-reports/desktop-cross-report-drill-through.md) |
| Helskärmsläge | Nej | Ja | [Helskärmsläge](../consumer/end-user-focus.md) i Power BI-tjänsten |
| Avancerat Microsoft 365-samarbete | Nej | Ja | [Samarbeta på en arbetsyta](../collaborate-share/service-collaborate-power-bi-workspace.md) med Microsoft 365 |
| R-skript och kontroller | Nej | Ja | [Skapa R-kontroller](../create-reports/desktop-r-visuals.md), kör R-skript i Power BI Desktop och publicera dem till Power BI-tjänsten. Du kan inte spara Power BI-rapporter med R-skript eller kontroller till Power BI-rapportserver.  |
| Python-skript och kontroller | Nej | Ja | [Skapa Python-skript](../connect-data/desktop-python-scripts.md) och kontroller i Power BI Desktop och publicera dem till Power BI-tjänsten. Du kan inte spara Power BI-rapporter med Python-skript eller kontroller till Power BI-rapportserver. |
| Förhandsgranskningsfunktioner | Nej | Ja | [Anmäl dig till förhandsversionsfunktioner](../consumer/end-user-preview-features.md) i Power BI-tjänsten |
| Visuella objekt för Power BI | Ja | Ja | [Visuella Power BI-objekt](../developer/visuals/power-bi-custom-visuals.md) |
| Sammansatta modeller | Nej | Ja |
| Power BI Desktop | Version som är optimerad för rapportservern och som kan laddas ned med rapportservern | Version som är optimerad för Power BI-tjänsten, tillgänglig från Windows Store | [Power BI Desktop för rapportservern](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop för Power BI-tjänsten](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Nästa steg

[Installera Power BI-rapportserver](install-report-server.md)






