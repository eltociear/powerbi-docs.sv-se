---
title: Ansluta till VMob med Power BI
description: "VMob för Power BI"
services: powerbi
documentationcenter: 
author: SarinaJoan
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
ms.author: sarinas
ms.openlocfilehash: f81c132de6ab2d7c086379dc538e23fd2f4072e8
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-vmob-with-power-bi"></a>Ansluta till VMob med Power BI
Det är enkelt att spåra och utforska dina VMob-data med Power BI och VMob-innehållspaketet. Power BI hämtar följande data: användarstatistik för hela tiden och de senaste 30 dagarna, detaljhandels-KPI för de senaste 30 dagarna och kampanjresultat för de senaste 30 dagarna.

Anslut till [VMob-innehållspaketet](https://app.powerbi.com/getdata/services/vmob) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-vmob/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-vmob/services.png)
3. Välj **VMob** \> **Hämta**.
   
   ![](media/service-connect-to-vmob/vmob.png)
4. När du uppmanas till det anger du din VMob-URL och klickar på Nästa. Denna URL tillhandahålls av VMob separat.
   
    ![](media/service-connect-to-vmob/params.png)
5. Välj alternativet **Grundläggande** i listrutan för autentiseringsmetod, ange ditt VMob-användarnamn och -lösenord och klicka på knappen **Logga in**.
   
    ![](media/service-connect-to-vmob/creds.png)
6. Importen startar automatiskt och Power BI hämtar dina VMob-data för att skapa en instrumentpanel och en rapport som är färdiga att använda.
   
   ![](media/service-connect-to-vmob/dashboard2.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

