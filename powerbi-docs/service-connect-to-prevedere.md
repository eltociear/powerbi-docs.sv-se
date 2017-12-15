---
title: Anslut till Prevedere med Power BI
description: "Prevedere för Power BI"
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
ms.openlocfilehash: 44871137e63572d801525c1f070dac5d07a32308
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-prevedere-with-power-bi"></a>Anslut till Prevedere med Power BI
Få åtkomst till exklusiv och viktig ekonomisk information för driva din verksamhet framåt konfidentiellt och proaktivt.

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
5. Välj **logga in** för att starta importen. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att se dina importerade data.
   
     ![](media/service-connect-to-prevedere/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Vad ingår
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

