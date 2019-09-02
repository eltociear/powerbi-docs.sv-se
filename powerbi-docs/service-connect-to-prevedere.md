---
title: Anslut till Prevedere med Power BI
description: Prevedere för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 8abf93b30b976aea1d0164238d173abe1be260e8
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185359"
---
# <a name="connect-to-prevedere-with-power-bi"></a>Anslut till Prevedere med Power BI
Få åtkomst till exklusiv och viktig ekonomisk information för driva din verksamhet framåt konfidentiellt och proaktivt.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Anslut till [Prevedere-innehållspaketet](https://app.powerbi.com/getdata/services/prevedere) för Power BI.

>[!NOTE]
>Om du inte är en befintlig Prevedere-användare, kan du använda [exempelnyckeln](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html) för att testa.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-prevedere/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-prevedere/services.png)
3. Välj **Prevedere** och sedan **hämta**.
   
   ![](media/service-connect-to-prevedere/connect.png)
4. Som **autentiseringsmetod**, väljer du **nyckel** och anger din Prevedere API-nyckel.
   
    ![](media/service-connect-to-prevedere/creds.png)
5. Välj **logga in** för att starta importen. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
     ![](media/service-connect-to-prevedere/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Innehållspaketet får insikter om dina detaljhandelsprognoser, prognosmodeller, ledande indikatorer och mycket mer.

## <a name="system-requirements"></a>Systemkrav
Det här innehållspaketet kräver åtkomst till en Prevedere API-nyckel eller en exempelnyckel (se nedan).

## <a name="finding-parameters"></a>Hitta parametrar
<a name="FindingParams"></a>

Befintliga kunder kan komma åt sina data med sin API-nyckel. Om du inte ännu är en kund, kan du se ett exempel på data och analyser med hjälp av [exempelnyckeln](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html).

## <a name="troubleshooting"></a>Felsökning
Det kan ta en stund att läsa in alla data beroende på hur stor instans du har.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

