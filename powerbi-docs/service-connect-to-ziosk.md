---
title: Anslut till Ziosk Survey Analytics med Power BI
description: Ziosk för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e16264c3cf5b6d361353c18ba9eb666fd00ce5d
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060467"
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

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
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
[Vad är Power BI?](fundamentals/power-bi-overview.md)

[Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)

