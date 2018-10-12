---
title: Bädda in rapporter eller instrumentpaneler från appar
description: Lär dig hur du integrerar eller bäddar in en rapport eller instrumentpanel från en Power BI-app och inte från en apparbetsyta.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 53803c77dec8eb35c10db7f19a82f58144f88414
ms.sourcegitcommit: b45134887a452f816a97e384f4333db9e1d8b798
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237995"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Bädda in rapporter eller instrumentpaneler från appar

I Power BI kan du skapa appar som samlar relaterade instrumentpaneler och rapporter på ett och samma ställe. Du kan sedan publicera dem till stora grupper i din organisation. Användningen av dessa appar är relevant när alla dina användare är Power BI-användare. Då kan du dela innehåll med dem med hjälp av Power BI-appar. I den här artikeln delar vi med oss av några enkla steg för att utföra inbäddning av innehåll från en publicerad Power BI-App till ett program från tredje part.

## <a name="grab-a-report-embedurl-for-embedding"></a>Hämta rapportens embedURL för inbäddning

1. Skapa en instans av programmet i en användararbetsyta, **Min arbetsyta**. Dela med dig själv eller be någon annan användare genomgå det här flödet.

2. Öppna önskad rapport i Power BI-tjänsten.

3. Gå till **Arkiv** > **Bädda in i SharePoint Online** och hämta rapportens embedURL därifrån. Den visas i följande ögonblicksbild. Du kan annars anropa GetReports/GetReport REST API och extrahera motsvarande embedURL-fält från svaret. REST-anrop får inte ha en identifierare för arbetsytan som en del av URL:en eftersom appen har fått en instans i användarens arbetsyta.

4. Använd embedURL som du hämtade i steg 3 i JavaScript SDK.

    ![Bädda in från appar](media/embed-from-apps/embed-from-app.png)

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Hämta instrumentpanelens embedURL för inbäddning

1. Skapa en instans av programmet i en användararbetsyta, **Min arbetsyta**. Dela med dig själv eller be någon annan användare genomgå det här flödet.

2. Anropa GetDashboards REST API och extrahera motsvarande embedURL-fält från svaret. REST-anrop får inte ha en identifierare för arbetsytan som en del av URL:en eftersom appen har fått en instans i användarens arbetsyta.

3. Använd embedURL som du hämtade i steg 2 i JavaScript SDK.

## <a name="next-steps"></a>Nästa steg

Läs om hur du bäddar in från apparbetsytor för kunder från tredje part och din organisation:

> [!div class="nextstepaction"]
>[Bädda in för kunder från tredje part](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Bädda in för din organisation](embed-sample-for-your-organization.md)