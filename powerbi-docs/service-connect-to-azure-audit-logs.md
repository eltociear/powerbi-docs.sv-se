---
title: Ansluta till Azure-granskningsloggar med Power BI
description: Azure-granskningsloggarna för Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d0bd4e90dac6e71d95c38bed83f1c9507acc4fd3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855400"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Ansluta till Azure-granskningsloggar med Power BI
Du kan analysera och visualisera informationen som lagras i granskningsloggarna med Azure-granskningsloggarnas innehållspaket. Power BI hämtar dina data, skapar en färdig instrumentpanel och sedan rapporter baserade på dessa data.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Anslut till Azure-granskningsloggarnas innehållspaket](https://app.powerbi.com/getdata/services/azure-audit-logs) eller läs mer om integration av [Azure-granskningsloggarna](https://powerbi.microsoft.com/integrations/azure-audit-logs) med Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i navigeringsfönstret.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Välj **Azure-granskningsloggarna** > **Hämta**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Skriv in ditt **prenumerations-ID för Azure** när du uppmanas till det. Information om hur du hittar ditt [prenumerations-ID](#FindingParams) visas nedan.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Som **autentiseringsmetod** väljer du **oAuth2** \> **Logga in**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Avsluta inloggningsprocessen genom att ange dina autentiseringsuppgifter.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI hämtar dina Azure-granskningsloggdata och skapar en instrumentpanel och en rapport som är färdiga att använda. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="system-requirements"></a>Systemkrav
Azure-granskningsloggarnas innehållspaket kräver åtkomst till granskningsloggar i Azure Portal. Du hittar mer information [här](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Det finns två enkla sätt för att hitta ditt prenumerations-ID.

1. Från https://portal.azure.com -&gt; Bläddra –&gt; Prenumerationer –&gt; Prenumerations-ID
2. Från https://manage.windowsazure.com -&gt; Inställningar –&gt; Prenumerations-ID

Ditt prenumerations-ID är en lång uppsättning siffror och tecken, likt exemplet i Steg \#4 ovan. 

## <a name="troubleshooting"></a>Felsökning
Om det uppstår ett fel med autentiseringsuppgifterna eller ett fel vid uppdateringsförsök till följd av ogiltiga autentiseringsuppgifter, så kan du prova med att ta bort alla förekomster av Azure-granskningsloggarnas innehållspaket och ansluta igen.

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](fundamentals/power-bi-overview.md)  
[Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)  

