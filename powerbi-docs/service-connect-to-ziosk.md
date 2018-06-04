---
title: Anslut till Ziosk Survey Analytics med Power BI
description: Ziosk för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 3308abbb3fbc1ceadb78b83d13d69d014de1bff1
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34238559"
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

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

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

