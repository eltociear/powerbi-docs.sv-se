---
title: "Felsök ditt inbäddade program"
description: "Den här artikeln går igenom några vanliga problem som kan uppstå när du bäddar in innehåll från Power BI."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 2/26/2018
ms.author: maghan
ms.openlocfilehash: 78e3361578b82a9ebf69feae1f7a8ac54966bbc9
ms.sourcegitcommit: 0a16dc12bb2d39c19e6b0002b673a8c1d81319c9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2018
---
# <a name="troubleshooting-your-embedded-application"></a>Felsök ditt inbäddade program

Den här artikeln går igenom några vanliga problem som kan uppstå när du bäddar in innehåll från Power BI.

## <a name="tools-for-troubleshooting"></a>Verktyg för felsökning

### <a name="fiddler-trace"></a>Fiddlerspårning

[Fiddler](http://www.telerik.com/fiddler) är ett kostnadsfritt verktyg från Telerik som övervakar HTTP-trafik.  Du kan se till- och fråntrafiken med Power BI-API:erna från klientdatorn. Detta kan visa fel och annan relaterad information.

![Fiddlerspårning](../includes/media/gateway-onprem-tshoot-tools-include/fiddler.png)

### <a name="f12-in-browser-for-front-end-debugging"></a>F12 i webbläsaren för felsökning av klientdelen

F12 startar utvecklarfönstret i din webbläsare. Detta ger dig möjlighet att titta på nätverkstrafik och annan information.

![F12 webbläsarfelsökning](media/embedded-troubleshoot/browser-f12.png)

### <a name="extracting-error-details-from-power-bi-response"></a>Extrahera felinformation från Power BI-svaret

Det här kodstycket visar hur man extraherar felinformationen från HTTP-undantaget:

```
public static string GetExceptionText(this HttpOperationException exc)
{
    var errorText = string.Format("Request: {0}\r\nStatus: {1} ({2})\r\nResponse: {3}",
    exc.Request.Content, exc.Response.StatusCode, (int)exc.Response.StatusCode, exc.Response.Content);
    if (exc.Response.Headers.ContainsKey("RequestId"))
    {
        var requestId = exc.Response.Headers["RequestId"].FirstOrDefault();
        errorText += string.Format("\r\nRequestId: {0}", requestId);
    }

    return errorText;
}
```
Vi rekommenderar att du loggar begärande-ID:erna (och felinformationen för felsökning).
Ange begäran-ID när du tar kontakt med Microsoft-supporten.

## <a name="app-registration"></a>Appregistrering

**Appregistreringsfel**

Felmeddelanden i Azure-portalen eller Power BI-appregistreringssidan kommer att nämna bristande behörigheter. Du måste vara en administratör i Azure AD-klienten för att registrera ett program eller så måste programregistreringar vara aktiverade för icke-administratörer.

**Power BI-tjänsten visas inte i Azure-portalen när du registrerar en ny App**

Minst en användare måste vara registrerad för Power BI. Om du inte ser **Power BI-tjänsten** listad i API-listan så är ingen användare registrerad för Power BI.

## <a name="rest-api"></a>REST API

**API-anropet returnerar 401**

En fiddler-avbildning kan krävas för att undersöka vidare. Det nödvändiga behörighetsomfånget kan saknas för det registrerade programmet i Azure AD. Verifiera att det nödvändiga omfånget finns i appregistreringen för Azure AD i Azure-portalen.

**API-anropet returnerar 403**

En fiddler-avbildning kan krävas för att undersöka vidare. Det kan finnas flera skäl för ett 403-fel.

* Användaren har överskridit mängden inbäddningstoken som kan skapas på en delad kapacitet. Du måste köpa Azure-kapaciteter för att generera inbäddningstoken och tilldela arbetsytan till kapaciteten. Mer information finns på sidan om hur du [skapar en Power BI Embedded-kapacitet i Azure Portal](https://docs.microsoft.com/en-us/azure/power-bi-embedded/create-capacity).
* Azure AD-autentiseringstoken har upphört att gälla.
* Den autentiserade användaren är inte medlem i gruppen (app-arbetsytan).
* Den autentiserade användaren är inte administratör i gruppen (app-arbetsytan).
* Auktoriseringsrubriken är kanske inte korrekt listad. Kontrollera att det inte finns några stavfel.

Programmets serverdel kan behöva uppdatera auktoriseringstoken innan du anropar GenerateToken.

```
    GET https://wabi-us-north-central-redirect.analysis.windows.net/metadata/cluster HTTP/1.1
    Host: wabi-us-north-central-redirect.analysis.windows.net
    ...
    Authorization: Bearer eyJ0eXAiOi...
    ...
 
    HTTP/1.1 403 Forbidden
    ...
     
    {"error":{"code":"TokenExpired","message":"Access token has expired, resubmit with a new access token"}}
```

**Skapa token misslyckas när du anger en effektiv identitet**

GenerateToken kan misslyckas med den effektiva identitet som angetts, av några olika skäl.

* Datauppsättningen stöder inte effektiv identitet
* Användarnamnet har inte angetts
* Rollen har inte angetts
* DatasetId har inte angetts
* Användaren har inte rätt behörighet

Prova följande för att verifiera vad det är.

* Kör [hämta datauppsättning](https://msdn.microsoft.com/library/mt784653.aspx). Är egenskapen IsEffectiveIdentityRequired sann?
* Användarnamnet är obligatoriskt för alla EffectiveIdentity.
* Om IsEffectiveIdentityRolesRequired är sant, krävs rollen.
* DatasetId är obligatoriskt för alla EffectiveIdentity.
* För Analysis Services måste huvudanvändaren vara en gatewayadministratör.

## <a name="data-sources"></a>Datakällor

**ISV vill ha olika autentiseringsuppgifter för samma datakälla**

En datakälla kan ha en enda uppsättning autentiseringsuppgifter för en huvudanvändare. Skapa ytterligare huvudanvändare om du behöver använda andra autentiseringsuppgifter. Tilldela därefter de olika autentiseringsuppgifterna i kontexten för varje huvudanvändare och bädda in med hjälp av Azure AD-token för den användaren.

## <a name="content-rendering"></a>Innehållsåtergivning

**Återgivning eller förbrukning av det inbäddade innehållet misslyckas eller får timeout**

Kontrollera att inbäddningstoken inte har upphört att gälla. Var noga att kontrollera utgångsdatumet för inbäddningstoken och uppdatera den. Mer information finns i [uppdatera token med JavaScript SDK](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Refresh-token-using-JavaScript-SDK-example).

**Rapporten eller instrumentpanelen läses inte in**

Om användaren inte kan se rapporten eller instrumentpanelen, kontrollera att rapporten eller instrumentpanelen laddas korrekt i powerbi.com. Rapporten eller instrumentpanelen fungerar inte i ditt program om det inte laddas i powerbi.com.

**Rapporten eller instrumentpanelen har dålig prestanda**

Öppna filen från Power BI Desktop eller på powerbi.com och verifiera att prestandan är acceptabel för att kunna utesluta problem med ditt program eller inbäddnings-API:erna.


Svar på vanliga frågor finns i [Power BI Embedded vanliga frågor och svar](embedded-faq.md).

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
