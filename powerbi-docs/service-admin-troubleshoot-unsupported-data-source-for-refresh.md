---
title: Felsöka datakälla utan stöd för uppdatering
description: Felsöka datakälla utan stöd för uppdatering
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 340c3fe2dc18fadb6be0ac47556547e6131833bc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280411"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Felsöka datakälla utan stöd för uppdatering
Du kan se ett fel vid försök att konfigurera en datauppsättning för schemalagd uppdatering.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Detta händer när datakällan som du använde i Power BI Desktop inte stöds för uppdatering. Du behöver hitta datakällan som du använder och jämföra den med listan över stödda datakällor i [Refresh data in Power BI (Uppdatera data i Power BI)](refresh-data.md). 

## <a name="find-the-data-source"></a>Hitta datakällan
Om du inte är säker på vilken datakälla som användes, kan du hitta den med följande steg i Power BI Desktop.  

1. Kontrollera att du är i fönstret **Rapport** i Power BI Desktop.  
   ![Skrivbordsrapportfönster](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Välj **Redigera frågor** från menyfliksområdet.  
   ![Redigera frågor](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Välj **Avancerad redigerare**.  
   ![Avancerad redigerare](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Anteckna providern som är angiven för datakällan i listan.  I det här exemplet är providern ActiveDirectory.  
   ![Datakällprovider](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Jämför providern med listan över stödda datakällor som finns i [Refresh data in Power BI (Uppdatera data i Power BI)](refresh-data.md).  Du kommer märka att Active Directory inte är en datakälla som stöds för uppdatering.  

## <a name="next-steps"></a>Nästa steg
[Datauppdatering](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[Lokal datagateway](service-gateway-onprem.md)  
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

