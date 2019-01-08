---
title: Ansluta till Webtrends med Power BI
description: Webtrends för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 1166808dc827448f94bb84cc37bf4000df178c1d
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008682"
---
# <a name="connect-to-webtrends-with-power-bi"></a>Ansluta till Webtrends med Power BI
Innehållspaketet Webtrends för Power BI och innehåller en mängd out-of-box-mått, till exempel antal sidvisningar och besök enligt trafikkälla. Du kan visualisera dina Webtrends-data i Power BI genom att först ansluta till ditt Webtrends-konto. Du kan använda instrumentpanelen de rapporter som tillhandahålls, eller anpassa dem för att fokusera på den information som du är mest intresserad av.  Data uppdateras automatiskt en gång per dag.

Anslut till [Webtrends-innehållspaket för Power BI.](https://app.powerbi.com/getdata/services/webtrends)

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-webtrends/getdata3.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-webtrends/services.png)
3. Välj **Webtrends** \> **Hämta**.
   
   ![](media/service-connect-to-webtrends/webtrends.png)
4. Innehållspaketet ansluter till ett visst Webtrends profil-ID. Visa information om att [hitta de här parametrarna](#FindingParams) nedan.
   
   ![](media/service-connect-to-webtrends/parameters.png)
5. Ange Webtrends-autentiseringsuppgifter för att ansluta. Observera att fältet användarnamn förväntar sig ditt konto och användarnamn. Se [information](#FindingParams) nedan.
   
   ![](media/service-connect-to-webtrends/creds.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
   ![](media/service-connect-to-webtrends/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
<a name="Included"></a>

Innehållspaketet Webtrends hämtar data från följande rapporter:  

| Rapportnamn | Rapport-ID |
| --- | --- |
| Nyckelmått | |
| Lokala sökningar |34awBVEP0P6 |
| Slutsidor |7FshY8eP0P6 |
| Nästa sidor |CTd5rpeP0P6 |
| Föregående sidor |aSdOeaUgnP6 |
| Webbplatssidor |oOEWQj3sUo6 |
| Klickningar på reklam på webbplatsen |41df19b6d9f |
| Orter |aUuHskcP0P6 |
| Länder |JHWXJNcP0P6 |
| Besökare |xPcmTDDP0P6 |
| Besökslängd |U5KAyqdP0P6 |
| Sökord |IKYEDxIP0P6 |
| Trafikkällor |JmttAoIP0P6 |
| Sökmotorer |yGz3gAGP0P6 |
| Startsidor |i6LrkNVRUo6 |

>[!NOTE]
>Tjänstmåttets namn kan vara lite annorlunda än vad som visas i Webtrends UI för SharePoint-profiler. Följande kartläggning görs för att vara konsekvent mellan SharePoint- och Webtrends-profiler:   

    - Sessioner = besök  
    - Nya användare = nya besökare  
    - Vyer per session = sidvisningar per besök  
    - Genomsn. daglig användningslängd = Genomsnittlig tid på plats per besökare  

## <a name="system-requirements"></a>Systemkrav
Innehållspaketet kräver åtkomst till en Webtrends-profil med en [korrekt uppsättning rapporter](#Included) aktiverade.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Ditt profil-ID för Webtrends kan hittas i URL: en när du har valt en profil:

![](media/service-connect-to-webtrends/webtrendsparameters.png)

Dina autentiseringsuppgifter är samma som du anger när du loggar in på Webtrends, men vi förväntar oss ditt konto och ditt användarnamn på samma rad, avgränsade med ett omvänt snedstreck:

![](media/service-connect-to-webtrends/webtrendscreds.png)

## <a name="troubleshooting"></a>Felsökning
Du kan stöta på problem när innehållspaketet läses in när du har angett dina autentiseringsuppgifter. Granska felsökningsförslagen nedan om du ser meddelandet ”Oops” under inläsningen. Om du fortfarande har problem kan du skicka ett supportärende på https://support.powerbi.com

1. Rätt profil-ID används, se [Hitta parametrar](#FindingParams) för mer information.
2. Användaren har åtkomst till de rapporter som anges i avsnittet [”Vad ingår”](#Included)

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](power-bi-overview.md)

[Power BI – grundläggande begrepp](consumer/end-user-basic-concepts.md)

