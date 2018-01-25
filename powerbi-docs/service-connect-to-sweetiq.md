---
title: Anslut till SweetIQ med Power BI
description: "SweetIQ för Power BI"
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
ms.openlocfilehash: eff79e26549ee67482a6876dc7850d2a922a4586
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2018
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

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="finding-parameters"></a>Hitta parametrar
Klient-ID och API-nyckeln för det här innehållspaketet är inte samma som ditt användarnamn och lösenord för SweetIQ.

Välj ett klient-ID för en av klienterna som ditt konto har åtkomst till. Du hittar listan över klienter under klienthantering i ditt SweetIQ-konto.

Kontakta administratören för din API-nyckel för att få tillgång till data för en specifika klient.

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Hämta data för Power BI](service-get-data.md)

