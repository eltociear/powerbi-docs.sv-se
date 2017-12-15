---
title: Anslut till Smartsheet med Power BI
description: "Smartsheet för Power BI"
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
ms.openlocfilehash: 6e212f1a3cf114ebdd4eeba59aee20cfa4e02182
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Anslut till Smartsheet med Power BI
Smartsheet erbjuder en enkel plattform för samarbete och fildelning. Smartsheet-Innehållspaketet för Power BI erbjuder en instrumentpanel, rapporter och datauppsättningar som visar en översikt över ditt Smartsheet-konto. Du kan också använda [Power BI Desktop](desktop-connect-to-data.md) för att ansluta direkt till enskilda blad i ditt konto. 

Anslut till [Smartsheet-innehållspaketet](https://app.powerbi.com/groups/me/getdata/services/smartsheet) för Power BI.

>[!NOTE]
>Smartsheet-administratörskontot rekommenderas för att ansluta till och läsa in Power BI-innehållspaketet eftersom det har ytterligare åtkomst.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-smartsheet/pbi_getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-smartsheet/pbi_getservices.png) 
3. Välj **Smartsheet \> hämta**.
   
   ![](media/service-connect-to-smartsheet/smartsheet.png)
4. Som autentiseringsmetod väljer du **oAuth2 \> logga in**.
   
   När du uppmanas till det anger du dina autentiseringsuppgifter för Smartsheet och följer autentiseringsprocessen.
   
   ![](media/service-connect-to-smartsheet/creds.png)
   
   ![](media/service-connect-to-smartsheet/creds2.png)
5. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt markeras med en gul asterisk \*, välj Smartsheet-posten.
   
   ![](media/service-connect-to-smartsheet/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Vad ingår
Smartsheet-innehållspaketet för Power BI inkluderar en översikt över ditt Smartsheet-konto, till exempel hur många arbetsytor, rapporter och ark du har, när de har ändrats och så vidare. Administratörer kan även se information om användarna i sina system, till exempel de som skapat flest ark.  

Om du vill ansluta direkt till enskilda ark i ditt konto, kan du använda Smartsheet-anslutningsprogrammet för [Power BI Desktop](desktop-connect-to-data.md).  

## <a name="next-steps"></a>Nästa steg:

[Kom igång med Power BI](service-get-started.md)

[Hämta data för Power BI](service-get-data.md)