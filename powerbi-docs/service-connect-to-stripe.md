---
title: Anslut till Stripe med Power BI
description: Stripe för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ddcbee2c6d60541db0d71ea5ccfbfd5e6cf037ac
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184574"
---
# <a name="connect-to-stripe-with-power-bi"></a>Anslut till Stripe med Power BI
Visualisera och utforska dina Stripe-data med Power BI-innehållspaket. Power BI Stripe-innehållspaketet tar in data om dina kunder, avgifter, händelser och fakturor. Datan omfattar de senaste tiotusen händelserna och femtusen utgifterna under de senaste 30 dagarna. Innehållet uppdateras automatiskt en gång per dag enligt ett schema som du bestämmer. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

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

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](power-bi-overview.md)

[Hämta data för Power BI](service-get-data.md)

