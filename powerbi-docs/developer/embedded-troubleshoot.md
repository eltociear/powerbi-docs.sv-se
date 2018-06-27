---
title: Felsök ditt inbäddade program
description: Den här artikeln går igenom några vanliga problem som kan uppstå när du bäddar in innehåll från Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: maghan
ms.openlocfilehash: ad23161985cc2721562cfdfd9128e326db887ece
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34813168"
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

* Användaren har överskridit mängden inbäddningstoken som kan skapas på en delad kapacitet. Du måste köpa Azure-kapaciteter för att generera inbäddningstoken och tilldela arbetsytan till kapaciteten. Mer information finns på sidan om hur du [skapar en Power BI Embedded-kapacitet i Azure Portal](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity).
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

* Kör [get dataset](https://docs.microsoft.com/rest/api/power-bi/datasets). Är egenskapen IsEffectiveIdentityRequired sann?
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

## <a name="onboarding-experience-tool-for-embedding"></a>Integrationsverktyget för inbäddning

Du kan gå igenom [integrationsverktyget](https://aka.ms/embedsetup) och snabbt ladda ned ett exempelprogram. Sedan kan du jämföra ditt program med exemplet.

### <a name="prerequisites"></a>Förutsättningar

Kontrollera att du uppfyller förhandskraven innan du använder integrationsverktyget. Du behöver ett **Power BI Pro**-konto och en **Microsoft Azure**-prenumeration.

* Om du inte har registrerat dig för **Power BI Pro**, [registrerar du dig för en kostnadsfri utvärderingsversion](https://powerbi.microsoft.com/en-us/pricing/) innan du börjar.
* Om du inte har någon Azure-prenumeration kan du [skapa ett kostnadsfritt konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) innan du börjar.
* Du måste ha en egen installation för [Azure Active Directory-klient](create-an-azure-active-directory-tenant.md).
* Du behöver [Visual Studio](https://www.visualstudio.com/) installerad (version 2013 eller senare).

### <a name="common-issues"></a>Vanliga problem

Här följer exempel på några vanliga problem som kan uppstå vid testning med integrationsverktyget:

#### <a name="using-the-embed-for-your-customers-sample-application"></a>Använda exempelprogrammet Embed for your customers (Bädda in för dina kunder)

Om du arbetar med upplevelsen **Embed for your customers**  (Bädda in för dina kunder) börjar du med att spara och packa upp filen *PowerBI-Developer-Samples.zip*. Öppna sedan mappen *PowerBI-Developer-Samples-master\App Owns Data* och kör filen *PowerBIEmbedded_AppOwnsData.sln*.

När du väljer **Bevilja behörigheter** (steget Bevilja behörigheter) visas följande fel:

    AADSTS70001: Application with identifier <client ID> was not found in the directory <directory ID>

Du kommer runt det här problemet genom att stänga popup-fönstret, vänta några sekunder och sedan försöka igen. Du kan behöva upprepa den här åtgärden några gånger. En tidsförskjutning gör att programregistreringen inte kan slutföras förrän den är tillgänglig för externa API:er.

Följande felmeddelande visas när du kör exempelappen:

    Password is empty. Please fill password of Power BI username in web.config.

Det här felet uppstår eftersom det enda värdet som inte matas in i exempelprogrammet är användarlösenordet. Öppna filen Web.config i lösningen och fyll i fältet pbiPassword med användarens lösenord.

#### <a name="using-the-embed-for-your-organization-sample-application"></a>Använda exempelprogrammet Embed for your organization (Bädda in för din organisation)

Om du arbetar med upplevelsen **Embed for your organization** (Bädda in för din organisation) börjar du med att spara och packa upp filen *PowerBI-Developer-Samples.zip*. Öppna sedan mappen *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* och kör filen *pbi-saas-embed-report.sln*.

När du kör exempelappen **Embed for your organization** (Bädda in för din organisation) visas följande fel:

    AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: <client ID>

Felet beror på att omdirigerings-URL:en som angetts för webbserverprogrammet skiljer sig från exemplets URL. Om du vill registrera exempelprogrammet använder du *http://localhost:13526/* som omdirigerings-URL.

Om du vill redigera det registrerade programmet läser du avsnittet om hur du redigerar ett [AAD-registrerat program](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application), så att programmet kan ge åtkomst till webb-API:erna.

Om du vill redigera din Power BI-användarprofil eller dina Power BI-data läser du avsnittet om hur du redigerar [Power BI-data](https://docs.microsoft.com/en-us/power-bi/service-basic-concepts).

Mer information finns i [Vanliga frågor om Power BI Embedded](embedded-faq.md).

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)