---
title: Bädda in rapporter eller instrumentpaneler från appar
description: Lär dig hur du integrerar eller bäddar in en rapport eller instrumentpanel från en Power BI-app och inte från en apparbetsyta.
author: markingmyname
ms.author: maghan
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.date: 11/27/2018
ms.openlocfilehash: 8073696907ceff67664a0802a2b7775eea693e37
ms.sourcegitcommit: fdb54145f9bc93b312409c15c603749f3a4a876e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52452532"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Bädda in rapporter eller instrumentpaneler från appar

I Power BI kan du skapa appar som samlar relaterade instrumentpaneler och rapporter på ett och samma ställe. Du kan sedan publicera dem till stora grupper i din organisation. Användningen av dessa appar är relevant när alla dina användare är Power BI-användare. Då kan du dela innehåll med dem med hjälp av Power BI-appar. I den här artikeln delar vi med oss av några enkla steg för att utföra inbäddning av innehåll från en publicerad Power BI-App till ett program från tredje part.

## <a name="grab-a-report-embedurl-for-embedding"></a>Hämta rapportens embedURL för inbäddning

1. Skapa en instans av programmet i en användararbetsyta, **Min arbetsyta**. Dela med dig själv eller be någon annan användare genomgå det här flödet.

2. Öppna önskad rapport i Power BI-tjänsten.

3. Gå till **Arkiv** > **Bädda in i SharePoint Online** och hämta rapportens embedURL. Ett exempel på embedURL visas i nedanstående ögonblicksbild. Du kan också anropa GetReports/GetReport REST API och extrahera motsvarande embedURL-fält från svaret. REST-anrop får inte ha en identifierare för arbetsytan som en del av URL:en eftersom appen har fått en instans i användarens arbetsyta.

    ![Bädda in från appar](media/embed-from-apps/embed-from-app.png)

4. Använd embedURL som du hämtade i steg 3 i JavaScript SDK.

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
