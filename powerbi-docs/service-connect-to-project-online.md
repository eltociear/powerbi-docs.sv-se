---
title: Anslut till Project Online med Power BI
description: "Project Online för Power BI"
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
ms.openlocfilehash: 509b75d91611de827b236e45dc25ef893aff8177
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-project-online-with-power-bi"></a>Anslut till Project Online med Power BI
Microsoft Project Online är en flexibel lösning för hantering av projektportföljer (PPM) och dagligt arbete. Project Online låter organisationer komma igång, prioritera investeringar i projektportföljer och leverera det avsedda verksamhetsvärdet. Project Online-innehållspaketet för Power BI låter dig utforska dina projektdata, med mått som portföljstatus och projektefterlevnad.

Anslut till [Project Online-innehållspaketet](https://app.powerbi.com/getdata/services/project-online) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-project-online/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-project-online/services.png)
3. Välj **Microsoft Project Online** \> **hämta**.
   
   ![](media/service-connect-to-project-online/mproject.png)
4. I textrutan **Project Web App-URL**, anger du URL:en för den PWA (Project Web Add) som du vill ansluta till och klicka på **nästa**. Observera att det här kan skilja sig från exemplet om du har en anpassad domän.
   
    ![](media/service-connect-to-project-online/params.png)
5. Som Autentiseringsmetod väljer du **oAuth2** \> **Logga in**. När du uppmanas till det anger du dina autentiseringsuppgifter för Project Online och följer autentiseringsprocessen.
   
    ![](media/service-connect-to-project-online/creds.png)
6. Du ser ett meddelande som visar att dina data läses in. Det kan ta en stund att läsa in datan beroende på hur stort ditt konto är. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Det här är standardinstrumentpanelen som Power BI skapade för att visa dina data. Du kan ändra den här instrumentpanelen för att visa dina data på det sätt som du vill.
   
   ![](media/service-connect-to-project-online/dashboard2.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

