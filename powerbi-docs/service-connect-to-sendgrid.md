---
title: Ansluta till SendGrid med Power BI
description: "SendGrid för Power BI"
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
ms.openlocfilehash: b4f4a999ed9929366f58f719030490fc56f5364d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Ansluta till SendGrid med Power BI
Med Power BI-innehållspaketet för SendGrid kan du extrahera insikter och statistik från ditt SendGrid-konto. Med SendGrid-innehållspaketet kan du visualisera din SendGrid-statistik på en instrumentpanel.

Ansluta till [SendGrid-innehållspaketet](https://app.powerbi.com/getdata/services/sendgrid) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. Välj **SendGrid**-innehållspaketet och klicka på **Hämta**.
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. När du uppmanas till det anger du ditt SendGrid-användarnamn och lösenord. Välj **Logga in**.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. När Power BI har importerat datan visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret, ifyllt med din e-poststatistik för de senaste 90 dagarna. Nya objekt markeras med en gul asterisk \*.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Vad ingår
I SendGrid-instrumentpanelen finns följande mått:

* Övergripande e-poststatistik – förfrågningar, levererade, studsade, blockerad skräppost, skräppostrapport etc.
* E-poststatistik efter kategori
* E-poststatistik efter geografi
* E-poststatistik efter Internetleverantör
* E-poststatistik efter enhet, klient, webbläsare

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Hämta data](service-get-data.md)

