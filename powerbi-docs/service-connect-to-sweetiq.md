---
title: Anslut till SweetIQ med Power BI
description: SweetIQ för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 535a5b0d24abcd76d7c7b9becedad152e17829ed
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54007762"
---
# <a name="connect-to-sweetiq-with-power-bi"></a>Anslut till SweetIQ med Power BI
Power BI-innehållspaketet hämtar data från ditt SweetIQ-konto och skapar specifikt innehåll så att du enkelt kan utforska dina data. Använd SweetIQ-innehållspaketet om du vill analysera data om dina platser, listplaceringar, betyg och recensioner. Data har ställts in att uppdateras varje dag för att säkerställa att de data som du övervakar är uppdaterade.

Anslut till [SweetIQ-innehållspaketet](https://app.powerbi.com/groups/me/getdata/services/sweetiq) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. I navigeringsfönstret till vänster, klickar du på **hämta data.**
   
    ![](media/service-connect-to-sweetiq/getdata.png)
2. Välj **SweetIQ** och klicka på **hämta.**
   
    ![](media/service-connect-to-sweetiq/sweetiq.png)
3. Ange ditt SweetIQ-klient-ID. Det är vanligtvis ett alfanumeriskt värde. Mer information om att hitta det här värdet finns nedan.
   
    ![](media/service-connect-to-sweetiq/parameter.png)
4. Välj autentiseringstypen **nyckel** och ange din SweetIQ API-nyckel. Det är vanligtvis ett alfanumeriskt värde. Mer information om att hitta det här värdet finns nedan.
   
    ![](media/service-connect-to-sweetiq/credentials.png)
5. Power BI börjar läsa in dina data, vilket kan ta lite tid beroende på storleken för data i ditt konto. När inläsningen är klar, kommer du att se en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-sweetiq/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="finding-parameters"></a>Hitta parametrar
Klient-ID och API-nyckeln för det här innehållspaketet är inte samma som ditt användarnamn och lösenord för SweetIQ.

Välj ett klient-ID för en av klienterna som ditt konto har åtkomst till. Du hittar listan över klienter under klienthantering i ditt SweetIQ-konto.

Kontakta administratören för din API-nyckel för att få tillgång till data för en specifika klient.

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](power-bi-overview.md)

[Hämta data för Power BI](service-get-data.md)

