---
title: Ansluta till Lithium med Power BI
description: Lithium för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 9029d5b6268cacf17fc862a4c0a3d19f440f7de1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61164087"
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
4. Ange URL:en till din Lithium-community. Den är i formen *https://community.yoursite.com* .
   
   ![](media/service-connect-to-lithium/params.png)
5. När du uppmanas till det anger du dina Lithium-autentiseringsuppgifter. Välj **oAuth 2** som autentiseringsmekanism och klicka på **Logga in** och följ autentiseringsflödet i Lithium.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. När inloggningsflödet har slutförts startar importprocessen. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
    ![](media/service-connect-to-lithium/lithium.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="system-requirements"></a>Systemkrav
Lithium-innehållspaketet kräver en Lithium-community av v15.9 eller senare. Stäm av med din Lithium-administratör för att bekräfta versionen.

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](power-bi-overview.md)

[Power BI – grundläggande begrepp](consumer/end-user-basic-concepts.md)

