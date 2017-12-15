---
title: Anslut till Ziosk Survey Analytics med Power BI
description: "Ziosk för Power BI"
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
ms.openlocfilehash: 0f4cd7166334338e4b19586c189fd363c5b7c934
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-ziosk-survey-analytics-with-power-bi"></a>Anslut till Ziosk Survey Analytics med Power BI
Innehållspaketet Ziosk Survey Analytics för Power BI erbjuder restauranger med Ziosk-surfplattor ojämförbar tillgång till insikter från Ziosk-undersökningsdata, inklusive segmentering efter dag, plats, medarbetare och mer.

Anslut till [innehållspaketet Ziosk Survey Analytics](https://app.powerbi.com/getdata/services/ziosk-survey-analytics) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.  
   
    ![](media/service-connect-to-ziosk/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.  
   
    ![](media/service-connect-to-ziosk/services.png)
3. Välj **Ziosk Survey Analytics** och välj **hämta**.  
   
    ![](media/service-connect-to-ziosk/ziosk.png)
4. Välj **OAuth 2** och sedan **Logga in**. När du uppmanas, anger du dina autentiseringsuppgifter för Ziosk.
   
    ![](media/service-connect-to-ziosk/creds.png)
   
    ![](media/service-connect-to-ziosk/creds2.png)
5. När du är ansluten kommer en instrumentpanel, rapport och datauppsättning automatiskt att läsas in. När du är klar, uppdateras panelerna med data från ditt Ziosk-konto.
   
    ![](media/service-connect-to-ziosk/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Vad ingår
Innehållspaketet inkluderar data från följande tabeller:  

    - Alkoholkategori  
    - Förrättskategori  
    - CommentKeywords  
    - Datum  
    - Del av dagen  
    - Efterrättskategori  
    - FreeForm  
    - Barnkategori  
    - Meddelanden  
    - Premium-innehållskategori  
    - Fråga  
    - Lager  
    - Undersökningar  
    - Veckodag  


## <a name="system-requirements"></a>Systemkrav
Ett Ziosk-konto med behörigheter till ovanstående tabeller krävs för att skapa en instans av det här innehållspaketet.

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

