---
title: Ansluta till Azure-granskningsloggar med Power BI
description: "Azure-granskningsloggarna för Power BI"
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: cb52b8dc6aefc199ef09946bf8b58c98171c5aba
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Ansluta till Azure-granskningsloggar med Power BI
Du kan analysera och visualisera informationen som lagras i granskningsloggarna med Azure-granskningsloggarnas innehållspaket. Power BI hämtar dina data, skapar en färdig instrumentpanel och sedan rapporter baserade på dessa data.

[Anslut till Azure-granskningsloggarnas innehållspaket](https://app.powerbi.com/getdata/services/azure-audit-logs) eller läs mer om integration av [Azure-granskningsloggarna](https://powerbi.microsoft.com/integrations/azure-audit-logs) med Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Välj **Azure-granskningsloggarna** > **Hämta**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Skriv in ditt **prenumerations-ID för Azure** när du uppmanas till det. Information om hur du hittar ditt [prenumerations-ID](#FindingParams) visas nedan.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Som **autentiseringsmetod** väljer du **oAuth2** \> **Logga in**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Ange dina autentiseringsuppgifter för att avsluta inloggningsprocessen.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI hämtar dina Azure-granskningsloggdata och skapar en instrumentpanel och en rapport som är färdiga att använda. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="system-requirements"></a>Systemkrav
Azure-granskningsloggarnas innehållspaket kräver åtkomst till granskningsloggar i Azure Portal. Du hittar mer information [här](https://azure.microsoft.com/en-us/documentation/articles/insights-debugging-with-events/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Det finns två enkla sätt för att hitta ditt prenumerations-ID.

1. Från https://portal.azure.com –&gt; Bläddra –&gt; Prenumerationer –&gt; Prenumerations-ID
2. Från https://manage.windowsazure.com –&gt; Inställningar –&gt; Prenumerations-ID

Ditt prenumerations-ID är en lång uppsättning siffror och tecken, liknande exemplet i Steg \#4 ovan. 

## <a name="troubleshooting"></a>Felsökning
Om det uppstår ett fel med autentiseringsuppgifterna eller ett fel vid uppdateringsförsök till följd av ogiltiga autentiseringsuppgifter, kan du prova med att ta bort alla förekomster av Azure-granskningsloggarnas innehållspaket och ansluta igen.

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)  
[Power BI – grundläggande begrepp](service-basic-concepts.md)  

