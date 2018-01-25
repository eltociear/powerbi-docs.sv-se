---
title: Anslut till Stripe med Power BI
description: "Stripe för Power BI"
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
ms.openlocfilehash: 5ed68a3ee64803fa895ad9837fe37351163d09af
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-stripe-with-power-bi"></a>Anslut till Stripe med Power BI
Visualisera och utforska dina Stripe-data med Power BI-innehållspaket. Power BI Stripe-innehållspaketet tar in data om dina kunder, avgifter, händelser och fakturor. Datan omfattar de senaste tiotusen händelserna och femtusen utgifterna under de senaste 30 dagarna. Innehållet uppdateras automatiskt en gång per dag enligt ett schema som du bestämmer. 

Anslut till [Stripe-innehållspaketet](https://app.powerbi.com/getdata/services/stripe) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj Hämta data längst ned i det vänstra navigeringsfönstret.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Välj **Stripe** &gt; **hämta**.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. Ange din Stripe [API-nyckel](https://dashboard.stripe.com/account/apikeys) för att ansluta.  
   
    ![](media/service-connect-to-stripe/creds.png)
5. Importen startar automatiskt. När den är klar, visas en ny instrumentpanel och modell i navigeringsfönstret markerade med en asterisk. Välj instrumentpanelen för att se dina importerade data.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Hämta data för Power BI](service-get-data.md)

