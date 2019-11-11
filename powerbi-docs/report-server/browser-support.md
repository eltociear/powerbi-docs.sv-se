---
title: Webbläsarstöd för Power BI-rapportserver
description: Lär dig mer om vilka webbläsarversioner som stöds för att hantera och visa Power BI-rapportservern och rapportvisningskontrollerna.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
ms.openlocfilehash: 724bd7a9a11c42520c520019f1c4a67415aa5487
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874291"
---
# <a name="browser-support-for-power-bi-report-server"></a>Webbläsarstöd för Power BI-rapportserver
Lär dig mer om vilka webbläsarversioner som stöds för att hantera och visa Power BI-rapportservern och rapportvisningskontrollerna.

## <a name="browser-requirements-for-the-web-portal"></a>Webbläsarkrav för webbportalen
Följande är en aktuell lista med de webbläsare som stöds för webbportalen.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9–10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone och iPad med iOS 10*

* Apple Safari (+)

**Google Android**  
*Telefoner och surfplattor med Android 4.4 (KitKat) eller senare*

* Google Chrome (+)
  
  **(+)**  Senaste offentligt utgivna versionen

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Webbläsarkrav för webbkontrollen för rapportvisningsprogrammet (2015)
Följande är en aktuella list med de webbläsare som stöds för webbkontrollen för rapportvisningsprogrammet. Rapportvisningsprogrammet stöder visning av rapporter från webbportalen.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9–10.11*

* Apple Safari (+)
  
  **(+)**  Senaste offentligt utgivna versionen

### <a name="authentication-requirements"></a>Autentisering krävs
Webbläsaren stöder specifika autentiseringsscheman som måste hanteras av rapportservern för att klientbegäran ska lyckas. I följande tabell visas de standardautentiseringstyper som stöds av varje webbläsare som körs på ett Windows-operativsystem.

| **Typ av webbläsare** | **Stöder** | **Webbläsarens standard** | **Serverstandard** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, Basic |Negotiate |Ja. Standardinställningarna för autentisering fungerar med Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, Basic |Negotiate |Ja. Standardinställningarna för autentisering fungerar med Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, Basic |Negotiate |Ja. Standardinställningarna för autentisering fungerar med Chrome. |
| **Mozilla Firefox**(+) |NTLM, Basic |NTLM |Ja. Standardinställningarna för autentisering fungerar med Firefox. |
| **Apple Safari**(+) |NTLM, Basic |Grundläggande |Ja. Standardinställningarna för autentisering fungerar med Safari. |

 **(+)**  Senaste offentligt utgivna versionen

### <a name="script-requirements-for-viewing-reports"></a>Skriptkrav för att visa rapporter
Konfigurera webbläsaren för att köra skript om du vill använda rapportvisningsprogrammet.

Om skript inte är aktiverade, visas ett felmeddelande som liknar följande när du öppnar en rapport:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Om du vill visa rapporten utan stöd för skript återges rapporten i HTML utan funktioner för rapportvisning, till exempel rapportverktygsfältet och dokumentöversikten.

> [!NOTE]
> Rapportverktygsfältet är en del av HTML-visarens komponenter. Som standard visas i verktygsfältet längst upp i varje rapport som återges i ett webbläsarfönster. Rapportvisningsprogrammet har funktioner för att söka efter information i rapporten, bläddra till en specifik sida och justera sidan för bättre visning. Mer information om rapportverktygsfältet eller HTML-läsaren finns i [HTML-visningsverktyget och rapportverktygsfältet](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Stöd för webbläsare för webbserverkontroller för rapportvisningsverktyget i Visual Studio
Webbserverkontrollen för rapportvisningsverktyget används för att bädda in rapportfunktioner i ASP.NET-webbprogram. Mer information om hur du hämtar rapportvisningskontrollen finns i [Integrera rapporttjänster med hjälp av rapportvisningskontroller – Komma igång](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Använd en webbläsare som har stöd för skript är aktiverat. Om webbläsaren inte kan köra skript, kan du inte visa rapporten.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)**  Senaste offentligt utgivna versionen

## <a name="next-steps"></a>Nästa steg
[Administratörsöversikt](admin-handbook-overview.md)  
[Installera Power BI-rapportserver](install-report-server.md)  
[Hämta Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Ladda ned SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

