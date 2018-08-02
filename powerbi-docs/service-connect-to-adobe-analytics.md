---
title: Anslut till Adobe Analytics med Power BI
description: Anslut till Adobe Analytics från Power BI för en app som visar dina kontodata i en instrumentpanel och rapporter.
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e8e9b21e62f0a91234fccf78977a696e321ed8dc
ms.sourcegitcommit: fbb7924603f8915d07b5e6fc8f4d0c7f70c1a1e1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/02/2018
ms.locfileid: "38924545"
---
# <a name="connect-to-adobe-analytics-with-power-bi"></a>Anslut till Adobe Analytics med Power BI
Du ansluter till Adobe Analytics via Power BI genom att ansluta till ditt Adobe Analytics Marketing Cloud-konto. Du får en app med en Power BI-instrumentpanel och en uppsättning Power BI-rapporter som ger insikter om din webbplatstrafik och användardimensioner. Data uppdateras automatiskt en gång per dag. Du kan interagera med instrumentpanelen och rapporterna, men du kan inte spara ändringarna.

Anslut till [Adobe Analytics](https://app.powerbi.com/getdata/services/adobe-analytics) eller läs mer om [Adobe Analytics-integrering](https://powerbi.microsoft.com/integrations/adobe-analytics) med Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

1. Välj **Adobe Analytics** \> **hämta**.
   
   ![](media/service-connect-to-adobe-analytics/adobe.png)
2. Power BI ansluter till ett specifikt Adobe Analytics-företag och Report Suite-ID (inte Report Suite-namn). Se information om att [söka efter de här parametrarna](#FindingParams) nedan.
   
   ![](media/service-connect-to-adobe-analytics/parameters.png)
3. Som **autentiseringsmetod** väljer du **oAuth2** \> **Logga in**. När du uppmanas, anger du dina Adobe Analytics-autentiseringsuppgifter. 
   
    ![](media/service-connect-to-adobe-analytics/creds.png)
   
    ![](media/service-connect-to-adobe-analytics/adobe_signin.png)
4. Klicka på **acceptera** så att Power BI kommer åt dina Adobe Analytics-data.
   
   ![](media/service-connect-to-adobe-analytics/adobe_authorize.png)
5. Efter du godkänner så startar importen automatiskt. 

## <a name="view-the-adobe-analytics-dashboard-and-reports"></a>Visa Adobe Analytics-instrumentpanelen och rapporter
[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-open-app.md)]

      ![Adobe Analytics dashboard](media/service-connect-to-adobe-analytics/dashboard.png)

[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-what-now.md)]

## <a name="whats-included"></a>Vad ingår
Power BI använder Adobe Analytics-rapport API för att definiera och köra rapporter för följande tabeller:

| **Tabellnamn** | **Kolumninformation** |
| --- | --- |
| Produkter |element=  "product" (översta 25) </br> mått="cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Webbläsare |element = ”browser” (översta 25)</br>  mått="bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "pageviews" |
| Sidor |element = ”page” (översta 25)</br>  mått="cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "visits", "uniquevisitors", "pageviews", "bounces", "bouncerate", "totaltimespent" |
| JavaScript-aktiverat |element = ”javascriptenabled”, ”browser” (översta 25) |
| Mobilt OS |element = ”mobileos” (översta 25)</br> mått="bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "checkouts", "revenue", "units", "pageviews" |
| Nyckelord för sökmotorer |element= "searchengine" "searchenginekeyword"</br>  mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Sökmotor till produkter |element= "searchengine", "product"</br>  mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Refererande sidor |element= "referrer" (översta 15), “page" (översta 10)</br>  mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Geocountry-sidor |element= "geocountry" (översta 20), "page"</br>  mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Geocountry-produkt |element= "geocountry" (översta 20), "product"</br> mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Land- och regionssökning |element= "geocountry" (översta 200)</br>  mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Språk |element= "language", "browser" (översta 25)</br>  mått="bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "pageviews", "cartadditions", "cartremovals", "checkouts", "carts", "cartviews" |
| Sökmotorsökning |element= "searchengine" (översta 100)</br>  mått="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| Webbläsarsökning |element = ”browser” (översta 25) |

## <a name="system-requirements"></a>Systemkrav
Åtkomst till [Adobe Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html) krävs, inklusive tillgång till rätt parametrar som beskrivs nedan.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
**Företag**

Företagsvärdet finns i det övre högra hörnet för ditt konto när du har loggat in. Värdet är skiftlägeskänsligt och blankstegskänsligt. Ange den exakt som det visas i ditt konto.

![](media/service-connect-to-adobe-analytics/adobe_companies.png)

**Report Suite-ID.**

Suite-ID skapas när Report Suite skapas. Du kan kontakta din administratör för att identifiera ID-värdet. Observera att detta inte är Report Suite-namnet.

Från Adobe-[dokumentationen](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html):

![](media/service-connect-to-adobe-analytics/reportsuiteid.png)

## <a name="troubleshooting"></a>Felsökning
Om du får ett fel när du har angett dina autentiseringsuppgifter som anger du inte har behörigheter, bekräfta med din administratör att du har åtkomst till Adobe Analytics API:n. Bekräfta även att det Adobe-ID som angetts är kopplat till din Marketing Cloud-organisation (som är kopplad till ett Adobe Analytics-företag).

Om du kommer förbi autentiseringsskärmen innan du påträffar felet, är det möjligt att rapporterna tar för lång tid att slutföra. Ett vanligt fel är i formatet *det gick inte att hämta data från Adobe Analytics-rapporten. Innehåll som ingår &quot;referent, sidan&quot;, ungefärlig varaktighet var xx sekunder*. Läs avsnittet vad ingår och jämför med storleken på din Adobe-instans. Det finns tyvärr inte något sätt att kringgå den här timeouten idag. Men vi överväger uppdateringar för att ge bättre stöd åt stora instanser. Ge gärna feedback till Power BI-teamet på https://ideas.powerbi.com

## <a name="next-steps"></a>Nästa steg
* [Vad är appar i Power BI?](service-install-use-apps.md)
* [Hämta data i Power BI](service-get-data.md)
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

