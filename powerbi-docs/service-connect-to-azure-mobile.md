---
title: Ansluta till Azure Mobile Engagement med Power BI
description: Azure Mobile Engagement för Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 7ce73dffd21426ac0687df65068712069c112c22
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-azure-mobile-engagement-with-power-bi"></a>Ansluta till Azure Mobile Engagement med Power BI
Med innehållspaketet Power BI Azure Mobile Engagement kan du snabbt få insikter om dina appdata.

Ansluta till innehållspaketet [Azure Mobile Engagement](https://app.powerbi.com/groups/me/getdata/services/azme) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-azure-mobile/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
    ![](media/service-connect-to-azure-mobile/services.png)
3. Välj **Azure Mobile Engagement** \> **Hämta**.
   
    ![](media/service-connect-to-azure-mobile/azme.png) 
4. Ange appsamling och appnamn. Den här informationen kan hittas i ditt Azure Mobile Engagement-konto.
   
    ![](media/service-connect-to-azure-mobile/parameters.png) 
5. För autentiseringsmetoden väljer du din nyckel och klickar sedan på Logga in.
   
    ![](media/service-connect-to-azure-mobile/creds.png)
6. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt har markerats med en gul asterisk \* som försvinner när de markeras:
   
    ![](media/service-connect-to-azure-mobile/dashboard.png)

 **Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

