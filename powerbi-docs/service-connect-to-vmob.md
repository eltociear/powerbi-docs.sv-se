---
title: Ansluta till VMob med Power BI
description: VMob för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 01c7866a47d20b51055aa77bdd4792e2277c335f
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46549758"
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

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

