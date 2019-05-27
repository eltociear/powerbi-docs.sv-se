---
title: Felsök inloggningsproblem i Power BI Desktop
description: Lösningar på vanliga problem för att logga in till Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f81517bf4d7857b5c86b4fd8d801e989abb0399b
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514479"
---
# <a name="troubleshooting-sign-in-for-power-bi-desktop"></a>Felsök inloggning i Power BI Desktop
Det kan finnas tillfällen när du försöker logga in på **Power BI Desktop** men stöter på fel. Det finns två primära orsaker för inloggningsproblem: **Proxy-autentiseringsfel** och **icke-HTTPS-URL omdirigeringsfel**. 

För att avgöra vilka problem som orsakar inloggningsproblemet, är det första steget att kontakta din administratör och ange diagnostisk information så att de kan fastställa orsaken till problemet. Genom att spåra problem associerade med dina inloggningsproblem, kan administratörer vilket av följande fel som gäller för dig. 

Låt oss ta en titt på var och ett av problemen i turordning. I slutet av den här artikeln hittar du en diskussion om hur du kan spara en *spårning* i Power BI Desktop som kan hjälpa dig spåra felsökningsproblem.


## <a name="proxy-authentication-required-error"></a>Felet proxyautentisering krävs

Följande skärmbild visar ett exempel på felet *Proxyautentisering krävs*.

![Inloggningsfel för proxyautentiseringsfel](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_01.png)

Följande undantag i *Power BI Desktop*-spårningsfiler är associerat med det här felet:

* *Microsoft.PowerBI.Client.Windows.Services.PowerBIWebException*
* *HttpStatusCode: ProxyAuthenticationRequired*

När det här felet uppstår är den troligaste orsaken att en proxyserver för autentisering i ditt nätverk blockerar webbegäranden som utfärdats av **Power BI Desktop**. 

Om ditt nätverk använder en proxyserver för autentisering, kan din administratör åtgärda problemet genom att vitlista följande domäner på proxyservern för autentisering:

* app.powerbi.com
* api.powerbi.com
* domäner i namnområdet *.analysis.windows.net

För kunder som ingår i ett myndighetsmoln, kan man åtgärda problemet genom att vitlista följande domäner på proxyservern för autentisering:

* app.powerbigov.us
* api.powerbigov.us
* domäner i namnområdet *.analysis.usgovcloudapi.net

## <a name="non-https-url-redirect-not-supported-error"></a>Felet omdirigering för icke-HTTPS-URL:er stöds inte

Aktuella versioner av **Power BI Desktop** använder den aktuella versionen av Active Directory Authentication Library (ADAL), vilket inte tillåter en omdirigering till icke-säkra URL:er (icke-HTTPS). 

Följande undantag i *Power BI Desktop*-spårningsfiler är associerat med det här felet:

* *Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException: Omdirigering av Icke-HTTPS-URL stöds inte i webbvy*
* *ErrorCode: non_https_redirect_failed*

Om *ErrorCode: non_https_redirect_failed* inträffar, innebär det att en eller flera omdirigeringssidor eller providers i omdirigeringskedjan inte är en HTTPS-skyddad slutpunkt eller att en certifikatutfärdare för en eller flera omdirigeringar inte finns bland enhetens betrodda rotcertifikat. Alla leverantörer i en omdirigeringskedja för inloggning måste använda en HTTPS-URL. Kontakta din administratör och begär att säkra URL:er används för deras autentiseringswebbplatser för att lösa problemet. 

## <a name="how-to-collect-a-trace-in-power-bi-desktop"></a>Så här samlar du in ett spår i Power BI Desktop

Om du vill samla in ett spår i **Power BI Desktop** gör du följande:

1. Aktivera spårning i **Power BI Desktop** genom att gå till **Arkiv > Alternativ och inställningar > Alternativ** och sedan välja **Diagnostik** från alternativen i den vänstra rutan. I fönstret som visas, markerar du kryssrutan bredvid **Aktivera spårning**, enligt följande bild. Du kan behöva starta om **Power BI Desktop**.
   
   ![Aktivera spårning i Power BI Desktop](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_02.png)

2. Följ sedan de steg som återskapar felet. När detta sker lägger **Power BI Desktop** till händelser i spårningsloggen som sparas på den lokala datorn.

3. Navigera till mappen Spår på din lokala dator. Du hittar den mappen genom att välja länken i **Diagnostik** där du aktiverade spårning, visas som *Öppna kraschdump/spårningar-mappen* i föregående bild. Ofta finns det här på den lokala datorn på följande plats:

    `C:\Users/<user name>/AppData/Local/Microsoft/Power BI Desktop/Traces`

Det kan finnas många spårningsfiler i den mappen. Kontrollera att du bara skickar de senaste filerna till din administratör för att underlätta snabb identifiering av felet. 

