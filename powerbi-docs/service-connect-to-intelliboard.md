---
title: Anslut till IntelliBoard med Power BI
description: IntelliBoard för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 06fc561d3fbe07cbf553be63c7b19de3ab11992e
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060949"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Anslut till IntelliBoard med Power BI
IntelliBoard erbjuder en förenklad åtkomst till dina Moodle learning management system-data via Reporting Services. IntelliBoard-innehållspaketet för Power BI erbjuder ytterligare analys, inklusive mått på dina kurser, registrerade användare, övergripande prestanda och din LMS-aktivitet.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Anslut till [IntelliBoard-innehållspaketet](https://app.powerbi.com/getdata/services/intelliboard) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Välj **IntelliBoard**och välj sedan **hämta**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Välj **OAuth 2** och sedan **Logga in**. När du uppmanas, anger du dina autentiseringsuppgifter för IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. När du är ansluten kommer en instrumentpanel, rapport och datauppsättning automatiskt att läsas in. När du är klar, uppdateras panelerna med data från ditt IntelliBoard-konto.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Innehållspaketet inkluderar data från följande tabeller:  

    - Aktivitet  
    - Agenter  
    - Författare  
    - Länder  
    - CoursesProgress  
    - Registreringar
    - Språk  
    - Plattform  
    - Summor  
    - UsersProgress    

## <a name="system-requirements"></a>Systemkrav
Ett IntelliBoard-konto med behörigheter till ovanstående tabeller krävs för att skapa en instans av det här innehållspaketet.

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](fundamentals/power-bi-overview.md)

[Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)

