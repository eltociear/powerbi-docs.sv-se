---
title: Anslut till Azure Security Center med Power BI
description: "Azure Security Center för Power BI"
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
ms.openlocfilehash: e26a26d7cba2ae3d68586a2e0dcdf87481009bd6
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-azure-security-center-with-power-bi"></a>Anslut till Azure Security Center med Power BI
Få insikter om din Azure-arbetsbelastning i Azure-säkerhet genom att ansluta dina Azure-säkerhetsdata med Power BI. Power BI skapar automatiskt en instrumentpanel och rapport ovanpå Azure Security Center-data så att du kan analysera och utforska data.

Anslut till [Azure Security Center-innehållspaketet](https://app.powerbi.com/getdata/services/azure-security-center) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-azure-security-center/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-azure-security-center/services.png)
3. Välj **Azure Security Center** \>  **Get**.
   
   ![](media/service-connect-to-azure-security-center/asc.png)
4. Ange din prenumerations-ID. Se information om att [söka efter de här parametrarna](#FindingParams) nedan.
   
   ![](media/service-connect-to-azure-security-center/params.png)
5. Som **autentiseringsmetod** väljer du **oAuth2** \> **Logga in**. När du uppmanas till det anger du dina Azure-autentiseringsuppgifter.
   
    ![](media/service-connect-to-azure-security-center/creds.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
     ![](media/service-connect-to-azure-security-center/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="whats-included"></a>Vad ingår
Innehållspaketet innehåller information om säkerhetsstatus för resursen, aviseringsanalys och analys om förebyggande.

## <a name="system-requirements"></a>Systemkrav
Det här innehållspaketet kräver åtkomst till en prenumerations-ID med Azure Security Center-aktiverat. Se mer information i [Azure Security Center](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityDashboardStartBladeV2) i Azure Portal.

Innehållspaketet kräver också att användaren ansluter med ett organisationskonto (inte ett personligt konto).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Det finns två enkla sätt för att hitta ditt prenumerations-ID.

1. Från https://portal.azure.com –&gt; Bläddra –&gt; Prenumerationer –&gt; Prenumerations-ID
2. Från https://manage.windowsazure.com –&gt; Inställningar –&gt; Prenumerations-ID

Ditt prenumerations-ID är en lång uppsättning siffror och tecken, liknande exemplet i Steg \#4 ovan. 

## <a name="troubleshooting"></a>Felsökning
Det kan ta en stund att läsa in datan beroende på hur stort ditt konto är. Om du stöter på ett fel vid inloggningen, bekräftar du att parametrarna och kontot har Azure Security Center aktiverat.

Om innehållspaketet läses in men inte visar några data, bekräfta att du ansluter med ett organisationskonto. Även om personliga konton som stöds av Azure Security Center, returnerar API:n (och därför innehållspaketet) inte de förväntade värdena om användaren ansluter med ett icke-organisationskonto. Ge åtkomst till ett organisationskonto och försök ansluta igen.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

