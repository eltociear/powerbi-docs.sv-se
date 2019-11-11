---
title: 'Tjänst från tredje part: Google Analytics-anslutningsapp'
description: 'Tjänst från tredje part: Google Analytics-anslutningsprogram för Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: da7d4de1aa356c9df5004ecc07d479188d9e3a9e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881399"
---
# <a name="google-analytics-connector-for-power-bi-desktop"></a>Google Analytics-anslutningsprogram för Power BI Desktop
> [!NOTE]
> Innehållspaketet och anslutningen för Google Analytics i Power BI Desktop använder sig av Google Analytics Core Reporting API. Det innebär att funktioner och tillgänglighet kan variera över tid.

Du kan ansluta till Google Analytics-data med hjälp av **Google Analytics**-anslutningsprogrammet. Gör så här för att ansluta:

1. I **Power BI Desktop** väljer du **Hämta data** från fliken **Start** i menyfliksområdet.
2. I fönstret **Hämta data** väljer du **Onlinetjänster** från kategorierna i det vänstra fönstret.
3. Välj **Google Analytics** från alternativen i det högra fönstret.
4. Längst ned i fönstret väljer du **Anslut**.  
   ![](media/service-google-analytics-connector/tps_googleanalytics_1.png)

En dialogruta visas som förklarar att anslutningsprogrammet är en tredjepartstjänst, varnar om hur funktioner och tillgänglighet kan ändras med tiden samt andra förtydliganden.  
![](media/service-google-analytics-connector/tps_googleanalytics_2.png)

När du väljer **Fortsätt** uppmanas du att logga in på Google Analytics.  
![](media/service-google-analytics-connector/tps_googleanalytics_3.png)

När du anger dina autentiseringsuppgifter visas ett meddelande om att Power BI vill ha offlineåtkomst. Detta är hur du använder **Power BI Desktop** för att få åtkomst till dina Google Analytics-data.  

När du har accepterat visar **Power BI Desktop** att du för närvarande är inloggad.  
![](media/service-google-analytics-connector/tps_googleanalytics_5.png)

Välj **Anslut**. Dina Google Analytics-data ansluts till **Power BI Desktop** och läser in datan.  
![](media/service-google-analytics-connector/tps_googleanalytics_6.png)

## <a name="changes-to-the-api"></a>Ändringar i API:n
Även om vi försöker släppa uppdateringar i takt med ändringarna, kan API:n ändras på ett sätt som påverkar resultaten för de frågor som vi genererar. I vissa fall kanske inte vissa frågor längre stöds. På grund av detta beroende kan vi inte garantera resultatet för dina frågor när du använder det här anslutningsprogrammet.

Mer information om ändringar i Google Analytics-API:n finns i deras [ändringslogg](https://developers.google.com/analytics/devguides/changelog).

