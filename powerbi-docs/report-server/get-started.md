---
title: Vad är Power BI-rapportserver?
description: Få en översikt över Power BI-rapportservern för att förstå hur den passar in med SQL Server Reporting Services (SSRS) och resten av Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: 1be2270074011f73c3d942677211dd99d18c6b2b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34294581"
---
# <a name="what-is-power-bi-report-server"></a>Vad är Power BI-rapportserver?

Power BI Report Server är en lokal rapportserver med en webbportal där du kan visa och hantera rapporter och KPI:er, tillsammans med verktyg för att skapa Power BI-rapporter, sidnumrerade rapporter, mobila rapporter och KPI:er. Användarna kan använda rapporterna på olika sätt: visa dem i en webbläsare eller en mobil enhet eller som e-post i sin i inkorg.

![Webbportalen för Power BI-rapportserver](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Jämföra Power BI-rapportserver 
Power BI-rapportserver är lik både SQL Server Reporting Services och Power BI-tjänsten online, men på olika sätt. Precis som Power BI-tjänsten är Power BI Report Server värd för Power BI-rapporter (.PBIX) och Excel-filer. Exempel Reporting Services är Power BI Report Server lokalt och värdar sidbrytning rapporter (.RDL). Power BI Report Server är en supermängd av Reporting Services: allt som du kan göra i Reporting Services, kan du göra med Power BI-rapportservern och mer, med tillagt stöd för Power BI-rapporter. Se [Jämföra Power BI-rapportservern och Power BI-tjänsten](compare-report-server-service.md) för mer information.

## <a name="licensing-power-bi-report-server"></a>Licensiera Power BI-rapportserver
Power BI-rapportservern är tillgänglig via två olika licenser: [Power BI Premium](../service-premium.md) och [SQL Server Enterprise Edition](https://www.microsoft.com/sql-server/sql-server-2017-editions) med Software Assurance. Med Power BI Premium-licensen kan du skapa en hybrid distributionsblandning för moln och lokalt.  

## <a name="web-portal"></a>Webbportalen
Startpunkten för Power BI-rapportservern är en säker webbportal som du kan visa i alla moderna webbläsare. Här kan du komma åt alla dina rapporter och KPI:er. Innehållet på webbportalen ordnas i en traditionell mapphierarki. I dina mappar grupperas innehållet efter typ: Power BI-rapporter, mobila rapporter, sidnumrerade rapporter, KPI:er och Excel-arbetsböcker, plus delade datauppsättningar och delade datakällor som kan användas som byggblock för dina rapporter. Du kan tagga favoriter om du vill visa dem i en enda mapp. Och du kan skapa KPI:er direkt i webbportalen. 

![Webbportalen för Power BI-rapportserver](media/get-started/web-portal.png)

Du kan hantera innehållet i webbportalen beroende på dina behörigheter. Du kan även schemalägga rapportbearbetning, få åtkomst till rapporter på begäran och prenumerera på publicerade rapporter. Du kan också använda din egen anpassade [företagsanpassning](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal) till webbportalen. 

Mer om webbportalen för [Power BI-rapportserver](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Power BI-rapporter
Du skapar Power BI-rapporter (.PBIX) med versionen av Power BI Desktop som är optimerad för rapportservern. Sedan publicerar du dem och visar dem i webbportalen i din egen miljö.

![Power BI-rapporter i Power BI-rapportservern](media/get-started/powerbi-reports.png)

En Power BI-rapport visar en datamodell från flera perspektiv med visualiseringar som representerar olika fynd och insikter från datamodellen.  En rapport kan ha en enda visualisering eller sidor som är fulla av visualiseringar. Beroende på din roll kan du läsa och utforska rapporter eller skapa dem för andra.

Installera [Power BI Desktop som har optimerats för Power BI-rapportservern](quickstart-create-powerbi-report.md).

## <a name="paginated-reports"></a>Sidnumrerade rapporter
Sidbrytningsrapporter (.RDL) är rapporter i dokumentformat med visualiseringar där tabeller expanderar vågrätt och lodrätt för att visa alla sina data, och fortsätter från sida till sida enligt behov. Det är bra för att skapa dokument med fast layout och bra utseende som är optimerade för utskrift, till exempel PDF- och Word-filer.

![Sidnumrerade rapporter i Power BI-rapportservern](media/get-started/paginated-reports.png)

Du kan skapa rapporter med modernt utseende med [Report Builder](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) eller rapportdesignern i [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Reporting Services-mobila rapporter
Mobila rapporter ansluter till lokala data och har en dynamisk layout som anpassar sig efter olika enheter och hur du håller dem. Du skapar dem med SQL Server Mobile Report Publisher.

Mer om [Reporting Services-mobila rapporter](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Programmeringsfunktioner för rapportservern
Dra nytta av Power BI-rapportserverns programmeringsfunktioner för att utöka och anpassa dina rapportfunktioner med API:er för att integrera eller utöka data och rapportbearbetning i anpassade program.

Fler [utvecklardokumentation för rapportservern](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Nästa steg
[Installera Power BI-rapportserver](install-report-server.md)  
[Installera Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)


