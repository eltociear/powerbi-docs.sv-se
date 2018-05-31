---
title: En jämförelse av Power BI-rapportservern och Power BI-tjänsten
description: I den här artikeln jämförs funktionerna i Power BI-rapportservern och Power BI-tjänsten.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: c47722fda28fc45289858f082a0838f583b53dbb
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34296800"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>En jämförelse av Power BI-rapportservern och Power BI-tjänsten

Power BI-rapportservern och Power BI-tjänsten har många likheter och vissa viktiga skillnader. Den här tabellen beskriver vad som är vad.

| Funktioner | Power BI-rapportserver | Power BI-tjänst | Anteckningar
|---------|---------|---------|---------|
| Distribution | Lokal eller värdbaserat moln | Moln | Power BI-rapportservern kan distribueras i virtuella Azure-datorer (värdbaserat moln) om den är licensierad via Power BI Premium.
| Källdata | I molnet och/eller lokalt | I molnet och/eller lokalt |  
| Licens | Power BI Premium eller SQL Server EE med SA | Power BI Pro och/eller för Power BI Premium |  
| Livscykel | Modern livscykelprincip | Helt hanterad tjänst |  
| Publiceringscykeln | Var fjärde månad | En gång i månaden | De senaste funktionerna och korrigeringarna levereras till Power BI-tjänsten först. De flesta grundläggande funktionerna kommer till Power BI-rapportservern under de kommande versionerna och vissa funktioner är endast avsedda för Power BI-tjänsten.
| Skapa Power BI-rapporter i Power BI Desktop | Ja | Ja |  
| Skapa Power BI-rapporter i webbläsaren | Nej | Ja |  
| Gateway krävs | Nej | Ja, för lokala datakällor |  
| Realtidsuppspelning | Nej | Ja | [Realtidsuppspelning i Power BI](../service-real-time-streaming.md)
| Instrumentpaneler | Nej | Ja | [Instrumentpaneler i Power BI-tjänsten](../service-dashboards.md) 
| Distribuera grupp av rapporter med hjälp av appar | Nej | Ja | [Skapa och publicera appar med instrumentpaneler och rapporter](../service-create-distribute-apps.md) 
| Innehållspaket | Nej | Ja | [Organisationsinnehållspaket: introduktion](../service-organizational-content-pack-introduction.md) 
| Ansluta till tjänster som Salesforce | Nej | Ja | [Ansluta till de tjänster som du använder](../service-connect-to-services.md) med Power BI-tjänsten
| Frågor och svar | Nej | Ja | [Frågor och svar i Power BI-tjänsten och Power BI Desktop](../power-bi-q-and-a.md) 
| Snabba insikter | Nej | Ja | [Automatiskt skapa datainsikter med Power BI](../service-insights.md) 
| Analysera i Excel | Nej | Ja | [Analysera i Excel](../service-analyze-in-excel.md) 
| Sidnumrerade rapporter | Ja | Nej | Sidnumrerade rapporter är inte tillgängliga i Power BI-tjänsten, men du kan [fästa sidnumrerade rapportobjekt på Power BI-instrumentpaneler](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)
| Power BI-mobilappar | Ja | Ja | [Översikt över Power BI-mobilappar](../mobile-apps-for-mobile-devices.md) 
| ArcGIS-mappar | Nej | Ja | [ArcGIS-kartor i Power BI-tjänsten och Power BI Desktop från Esri](../power-bi-visualization-arcgis.md)
| E-postprenumerationer för Power BI-rapporter | Nej | Ja | [Prenumerera på en rapport eller en instrumentpanel](../service-report-subscribe.md) i Power BI-tjänsten 
| E-postprenumerationer för sidnumrerade rapporter | Ja | Nej | [E-postleverans i Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| Datavarningar | Nej | Ja | [Datavarningar](../service-set-data-alerts.md) i Power BI-tjänsten
| Säkerhet på radnivå | Endast via datakälla i DirectQuery-läge | Tillgängligt i både DirectQuery- (datakälla) och Import-läge | [Säkerhet på radnivå (RLS)](../service-admin-rls.md) med Power BI 
| Helskärmsläge | Nej | Ja | [Helskärmsläge](../service-fullscreen-mode.md) i Power BI-tjänsten 
| Avancerat Office 365-samarbete | Nej | Ja | [Samarbeta på en apparbetsyta](../service-collaborate-power-bi-workspace.md) med Office 365 
| R-visualiseringar | Nej | Ja | [Skapa visuella R-objekt](../service-r-visuals.md) i Power BI-tjänsten  
| Förhandsversionsfunktioner | Nej | Ja | [Anmäl dig till förhandsversionsfunktioner](../service-preview-features.md) i Power BI-tjänsten 
| Anpassade visuella objekt | Ja | Ja | [Anpassade visuella objekt i Power BI](../power-bi-custom-visuals.md) 
| Power BI Desktop | Version som är optimerad för rapportservern och som kan laddas ned med rapportservern | Version som är optimerad för Power BI-tjänsten, tillgänglig från Windows Store | [Power BI Desktop för rapportservern](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop för Power BI-tjänsten](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>Nästa steg
[Installera Power BI-rapportserver](install-report-server.md)  



