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
ms.openlocfilehash: 976ca32f0c43f6d8412f9468dc9f61ab9768fa4c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
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

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

