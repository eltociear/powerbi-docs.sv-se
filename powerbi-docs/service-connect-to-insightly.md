---
title: Ansluta till Insightly med Power BI
description: Insightly för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 87d294c81cbf9a342ce238bb198173516c1f3215
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61174053"
---
# <a name="connect-to-insightly-with-power-bi"></a>Ansluta till Insightly med Power BI
Visualisera och dela dina Insightly CRM-data i Power BI med innehållspaketet för Insightly. Anslut till Power BI med din Insightly API-nyckel för att visa och skapa rapporter och instrumentpaneler från dina CRM-data. Med Power BI kan du analysera dina data på nya sätt, skapa kraftfulla diagram och grafer och visa kontakter, leads och organisationer på en karta.

Anslut till [Insightly-innehållspaket](https://app.powerbi.com/getdata/services/insightly) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-insightly/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-insightly/services.png)
3. Välj **Insightly** \> **Hämta**.
   
   ![](media/service-connect-to-insightly/insightly.png)
4. Välj **Nyckel** som autentiseringstyp och ange din Insightly-API-nyckel. Välj sedan **Logga In**. Mer information om hur du [hittar det](#FindingParams) nedan.
   
   ![](media/service-connect-to-insightly/creds.png)
5. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
     ![](media/service-connect-to-insightly/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Innehållspaketet innehåller följande tabeller med fält från motsvarande poster:

| Tabeller |  |  |  |
| --- | --- | --- | --- |
| Kontakter |Möjligheter |Pipeline-stadier |Uppgift slutförd datum |
| Anpassade fält |Slutdatum för affärsmöjlighet |Projektet slutfört datum |Uppgifter |
| Händelser |Prognosdatum för affärsmöjlighet |Projekt |Team/medlemmar |
| Leads |Organisationer |Tags |Användare |

Många tabeller och rapporter innehåller även unika beräknade fält, exempelvis:  

* Tabeller med ”grupperade” slutdatum för möjlighetsprognos, verkliga slutdatum för möjligheter, datum för projektets slutförande och datum för uppgifters slutförande enligt månad, kvartal eller år.  
* Ett viktat värdefält för möjligheter (möjlighetsvärde * sannolikheten för vinst).  
* Fält för genomsnittlig och total varaktighet för uppgifter baserat på start- och slutdatum.  
* Rapporter med beräknade fält för affärsmöjligheternas vinstfrekvens (antal vunna/antal totala affärsmöjligheter) och vinstvärde (värdet vunna/värdet för totalt antal affärsmöjligheter).  

## <a name="system-requirements"></a>Systemkrav
Ett Insightly-konto med åtkomst till Insightly API krävs. Synlighetsbehörigheter kommer att baseras på API-nyckeln som används för att upprätta en anslutning till Power BI. Alla Insightly-poster som du kan visa kommer att vara synliga i Power BI-rapporter och instrumentpaneler som du delar med andra.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
**API-nyckel**

Kopiera API-nyckeln från Insightly genom att markera Användarinställningar från Insightly-profilmenyn och rulla ned. Den här teckensträngen används för att ansluta dina data till Power BI.

![](media/service-connect-to-insightly/findapi.png)

## <a name="troubleshooting"></a>Felsökning
Data importeras via Insightly API, som innehåller en daglig gräns baserat på ditt Insightly-abonnemang. Gränserna anges i avsnittet om hastighetsbegränsning/begränsningsbegäran i vår API-dokumentation: https://api.insight.ly/v2.2/Help#!/Overview/Introduction#ratelimit

De angivna rapporterna använder standardfält från Insightly och innehåller kanske inte dina anpassningar. Redigera rapporten för att visa alla tillgängliga fält.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

