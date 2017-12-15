---
title: Ansluta till Lithium med Power BI
description: "Lithium för Power BI"
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
ms.openlocfilehash: ed7255df535cf2e6703fe9235b192c85d98d92d3
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-lithium-with-power-bi"></a>Ansluta till Lithium med Power BI
Lithium skapar betrodda relationer mellan världens bästa varumärken och deras kunder och hjälper användarna att få svar och dela sina erfarenheter. Genom att ansluta Lithium-innehållspaketet till Power BI kan du mäta viktiga mått rörande din online-community för att öka försäljningen, minska tjänstekostnaderna och öka lojaliteten. 

Anslut till [Lithium-innehållspaketet](https://app.powerbi.com/getdata/services/lithium) för Power BI.

>[!NOTE]
>Power BI-innehållspaketet använder Lithiums API. Långa anrop till API:n kan resultera i ytterligare avgifter från Lithium. Kontrollera detta med din Lithium-administratör.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-lithium/pbi_getdata.png) 
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-lithium/pbi_getservices.png) 
3. Välj **Lithium** \> **Hämta**.
   
   ![](media/service-connect-to-lithium/lithiumconnect.png)
4. Ange URL:en till din Lithium-community. Den har formatet *https://community.dinwebbplats.com*.
   
   ![](media/service-connect-to-lithium/params.png)
5. När du uppmanas till det anger du dina Lithium-autentiseringsuppgifter. Välj **oAuth 2** som autentiseringsmekanism och klicka på **Logga in** och följ autentiseringsflödet i Lithium.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. När inloggningsflödet har slutförts startar importprocessen. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att se dina importerade data.
   
    ![](media/service-connect-to-lithium/lithium.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="system-requirements"></a>Systemkrav
Lithium-innehållspaketet kräver en Lithium-community av v15.9 eller senare. Stäm av med din Lithium-administratör för att bekräfta versionen.

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

