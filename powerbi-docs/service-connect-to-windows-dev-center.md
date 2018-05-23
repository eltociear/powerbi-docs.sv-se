---
title: Ansluta till Windows Dev Center med Power BI
description: Windows Dev Center för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6cdb4d6684ec97786c7fd10da7d22515a24e9dbc
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-windows-dev-center-with-power-bi"></a>Ansluta till Windows Dev Center med Power BI
Utforska och övervaka dina Windows Dev Center-appanalysdata i Power BI med Power BI-innehållspaketet. Data uppdateras automatiskt en gång per dag.

Anslut till [Windows Dev Center-innehållspaketet](https://app.powerbi.com/getdata/services/devcenter) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-windows-dev-center/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-windows-dev-center/services.png)
3. Välj **Windows Dev Center** \>  **Hämta**.
   
   ![](media/service-connect-to-windows-dev-center/windowsdev.png)
4. Ange program-ID för en app som du äger och klicka på Nästa. Se information om att [söka efter de här parametrarna](#FindingParams) nedan.
   
   ![](media/service-connect-to-windows-dev-center/params.png)
5. Som **Autentiseringsmetod** väljer du **oAuth2** \> **Logga in**. När du uppmanas till det anger du dina autentiseringsuppgifter för Azure Active Directory som är associerade med Windows Dev Center-kontot (mer information finns i [Systemkrav](#Requirements)).
   
    ![](media/service-connect-to-windows-dev-center/creds.png)
   
    ![](media/service-connect-to-windows-dev-center/creds2.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att se dina importerade data och välj en panel för att gå till de underliggande rapporterna.
   
    ![](media/service-connect-to-windows-dev-center/dashboard.png)
   
    ![](media/service-connect-to-windows-dev-center/report.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="whats-included"></a>Vad ingår
Dev Center Power BI-innehållspaketet innehåller analysdata för din app och IAP-förvärv, klassificeringar, omdömen och apphälsa. Datan är begränsad till de senaste 3 månaderna. och är ett rörligt fönster, så datumen som ingår uppdateras när datauppsättningen uppdateras.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Systemkrav
Det här innehållspaketet kräver att minst en app publiceras till Windows Store och ett Windows Dev Center-konto (mer information finns [här](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users)).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Du hittar program-ID:t för en app på sidan Appidentitet under Apphantering.

Program-ID:t finns i slutet av din URL för Windows 10 Store, https://www.microsoft.com/store/apps/  **{applicationId}**

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

