---
title: 'Tjänst från tredje part: Google Analytics-anslutningsapp'
description: 'Tjänst från tredje part: Google Analytics-anslutningsprogram för Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ec290ce53155f24a9213a4849ecb82abd6cfc592
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263652"
---
# <a name="use-the-google-analytics-connector-for-power-bi-desktop"></a>Använda Google Analytics-anslutningsprogrammet för Power BI Desktop
> [!NOTE]
> Innehållspaketet och anslutningen för Google Analytics i Power BI Desktop använder sig av Google Analytics Core Reporting API. Det innebär att funktioner och tillgänglighet kan variera över tid.

Du kan ansluta till Google Analytics-data med hjälp av **Google Analytics**-anslutningsprogrammet. Gör så här för att ansluta:

1. I **Power BI Desktop** väljer du **Hämta data** från fliken **Start** i menyfliksområdet.
2. I fönstret **Hämta data** väljer du **Onlinetjänster** från kategorierna i det vänstra fönstret.
3. Välj **Google Analytics** från alternativen i det högra fönstret.
4. Längst ned i fönstret väljer du **Anslut**.  
   ![Skärmbild av fliken Start och menyfliksområdet Hämta data med Google Analytics valt och knappen Anslut.](media/service-google-analytics-connector/tps_googleanalytics_1.png)

En dialogruta visas som förklarar att anslutningsprogrammet är en tredjepartstjänst, varnar om hur funktioner och tillgänglighet kan ändras med tiden samt andra förtydliganden.  
![Skärmbild av anslutningsdialogrutan med en varning om att anslutningsprogrammet är beroende av en tjänst från tredje part.](media/service-google-analytics-connector/tps_googleanalytics_2.png)

När du väljer **Fortsätt** uppmanas du att logga in på Google Analytics.  
![Skärmbild av Google Analytics-prompten som visar att du måste logga in för att ansluta.](media/service-google-analytics-connector/tps_googleanalytics_3.png)

När du anger dina autentiseringsuppgifter visas ett meddelande om att Power BI vill ha offlineåtkomst. Detta är hur du använder **Power BI Desktop** för att få åtkomst till dina Google Analytics-data.  

När du har accepterat visar **Power BI Desktop** att du för närvarande är inloggad.  
![Skärmbild av Google Analytics-prompten som visar att du är inloggad.](media/service-google-analytics-connector/tps_googleanalytics_5.png)

Välj **Anslut**. Dina Google Analytics-data ansluts till **Power BI Desktop** och läser in datan.  
![Skärmbild av dialogrutan Läs in som visar att Google Analytics-data är anslutna och läses in.](media/service-google-analytics-connector/tps_googleanalytics_6.png)

## <a name="changes-to-the-api"></a>Ändringar i API:n
Även om vi försöker släppa uppdateringar i takt med ändringarna, kan API:n ändras på ett sätt som påverkar resultaten för de frågor som vi genererar. I vissa fall kanske inte vissa frågor längre stöds. På grund av detta beroende kan vi inte garantera resultatet för dina frågor när du använder det här anslutningsprogrammet.

Mer information om ändringar i Google Analytics-API:n finns i deras [ändringslogg](https://developers.google.com/analytics/devguides/changelog).

