---
title: Anslut till Mandrill med Power BI
description: "Mandrill för Power BI"
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
ms.openlocfilehash: 92b069bded7fc6a22480d8190c1b8d0f53f959e4
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-mandrill-with-power-bi"></a>Anslut till Mandrill med Power BI
Power BI-innehållspaketet hämtar data från ditt Mandrill-konto och genererar en instrumentpanel, en uppsättning rapporter och en datauppsättning för att utforska dina data. Använd Mandrills analys för att snabbt få insikter om ditt nyhetsbrev eller din marknadsföringskampanj. Data har ställts in att uppdateras varje dag för att säkerställa att de data som du övervakar är uppdaterade.

Anslut till [Mandrill-innehållspaketet för Power BI.](http://app.powerbi.com/getdata/services/mandrill)

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-mandrill/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
    ![](media/service-connect-to-mandrill/services.png)
3. Välj **Mandrill** > **hämta**.
   
    ![](media/service-connect-to-mandrill/mandrill.png)
4. Som **autentiseringsmetod**, väljer du **nyckel** och anger din API-nyckel. Du hittar nyckeln på fliken **inställningar** på Mandrill-instrumentpanelen. Välj **logga in** för att starta importen, vilket kan ta några minuter beroende på mängden data i ditt konto.
   
    ![](media/service-connect-to-mandrill/auth.png)
5. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Det här är standardinstrumentpanelen som Power BI skapade för att visa dina data.
   
    ![](media/service-connect-to-mandrill/mandrill-dashboard1.jpg)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

