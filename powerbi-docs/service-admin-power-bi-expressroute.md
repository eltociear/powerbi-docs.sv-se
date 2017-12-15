---
title: Power BI och ExpressRoute
description: Power BI och ExpressRoute
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: cad995ba0abbcc475a28dbddbf060b1017f9da90
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2017
---
# <a name="power-bi-and-expressroute"></a>Power BI och ExpressRoute
Med **Power BI** och **ExpressRoute** kan du skapa en privat nätverksanslutning från din organisation till Power BI (eller med hjälp av din Internet-leverantörs samordningsanläggning), vilket kringgår Internet och ger bättre skydd för dina känsliga Power BI-data och -anslutningar.

**ExpressRoute** är en Azure-tjänst som låter dig skapa privata anslutningar mellan Azure-datacenter (där Power BI finns) och lokal infrastruktur, eller skapa privata anslutningar mellan Azure-datacenter och din samordningsmiljö.

![](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)

Du kan hämta [mer information om ExpressRoute](https://azure.microsoft.com/services/expressroute/) eller läsa mer om [hur du registrerar dig](https://azure.microsoft.com/pricing/details/expressroute/).

> [!NOTE]
> Power BI stöds i offentlig peering-läge enligt beskrivningen i [dessa frågor och svar](https://docs.microsoft.com/azure/expressroute/expressroute-faqs).
> 
> 

## <a name="power-bi-expressroute-exceptions"></a>Power BI ExpressRoute-undantag
Power BI är kompatibelt med ExpressRoute med några få undantag där Power BI hämtar eller skickar data via det offentliga Internet. Dessa specifika undantag gäller ofta statiska data, till exempel webbläsarkonfigurationsfiler som hämtas från den närmaste noden i **innehållsleverantörsnetverket (CDN)**. Det finns vissa breda undantag som gäller för hela Power BI och det finns vissa tjänst- eller funktionsspecifika undantag som beskrivs i följande avsnitt.

### <a name="overall-exceptions-to-power-bi-and-expressroute"></a>Övergripande undantag till Power BI och ExpressRoute
Ett undantag till **Power BI** och **ExpressRoute** innebär att data som skickas till eller från Power BI går via det offentliga Internet i stället att sändas över den privata ExpressRoute-länken.

De två övergripande undantagen för Power BI med ExpressRoute är:

* Statiska filer som hämtas från  **innehållsleverantörsnätverk (CDN)** och webbplatser
* **Telemetridata** som överförs via det offentliga Internet

Power BI använder **innehållsleverantörsnätverk** (CDN) eller webbplatser till att distribuera det statiska innehåll som krävs samt filer till användarna, baserat på nationella inställningar via det offentliga Internet. Dessa statiska filer inkluderar produktnedladdningar (som **Power BI Desktop**, **Lokala datagatewayer** eller **Power BI-innehållspaket** från olika oberoende tjänstleverantörer), webbläsarkonfigurationsfiler som används för att initiera och skapa alla efterföljande anslutningar med Power BI, samt den första säkra inloggningssidan till Power BI – de faktiska inloggningsuppgifterna skickas endast via ExpressRoute.   

Vissa **telemetridata** skickas via det offentliga Internet och över ExpressRoute. Telemetridata omfattar användningsstatistik och liknande data som överförs till de tjänster som används för att övervaka användning och aktivitet.

### <a name="power-bi-saas-application-and-expressroute"></a>Power BI SaaS-program och ExpressRoute
När en användare initierar en anslutning till Power BI-tjänsten (powerbi.com eller via Cortana) hämtas startsidan för Power BI, inloggningssidan och statiska filer som förbereder webbläsaren för att ansluta till och interagera med Power BI från en CDN eller webbplatser som ansluter via det offentliga Internet.

När inloggningen har upprättats kan efterföljande datainteraktioner med Power BI ske via ExpressRoute, med undantag för visa funktioner och tjänster som beror på data från det offentliga Internet:

* **Kartvisuella objekt** kräver en anslutning och dataöverföring till tjänsterna Bing Virtual Earth eller Bin-geokodning, som har upprättats över det offentliga Internet.
* Power BI-integrering med **Cortana** kräver åtkomst till Bing via det offentliga Internet.
* När **anpassade länkar** har lagts till av en användare, t.ex. en bildwidget eller en video, begär Power BI data baserat på länken som anges av användaren, vilket kan men inte behöver använda ExpressRoute.
* Användarna kan skicka **feedback till Power BI** i text (och alternativt bilder) via mekanismen User Voice-feedback, som överförs via det offentliga Internet.
* Innehållsleverantören **Bing News**  laddar ned innehåll från Bing med hjälp av det offentliga Internet.
* När du ansluter till **appar** (till exempel innehållspaket) måste användare ofta ange inloggningsuppgifter och inställningar via sidor som tillhandahålls av SaaS-leverantören. Dessa sidor kan men behöver inte använda ExpressRoute.

| Användaraktivitet | Mål |
| --- | --- |
| Landningssida (före inloggningen) |`maxcdn.bootstrapcdn.com ; ajax.aspnetcdn.com ; netdna.bootstrapcdn.com ; cdn.optimizely.com; google-analytics.com ` |
| Inloggning |`*.mktoresp.com ; *.aadcdn.microsoftonline-p.com ; *.msecnd.com ; *.localytics.com ; ajax.aspnetcdn.com` |
| Instrumentpanel, rapport, hantering av datauppsättning (omfattar kartor och geokodning) |`*.localytics.com ; *.virtualearth.net ; platform.bing.com; powerbi.microsoft.com; c.microsoft.com; app.powerbi.com; *.powerbi.com; dc.services.visualstudio.com ` |
| Support |`support.powerbi.com ; powerbi.uservoice.com ; go.microsoft.com ` |

### <a name="power-bi-desktop-and-expressroute"></a>Power BI Desktop och ExpressRoute
Power BI Desktop är också kompatibelt ExpressRoute, med några få undantag som beskrivs i följande lista:

* **Uppdateringsmeddelanden** som används för att identifiera om användaren har den senaste versionen av Power BI Desktop sänds via det offentliga Internet.
* Vissa **telemetridata** överförs via det offentliga Internet.
* **Kartvisuella objekt** kräver en anslutning och dataöverföring till tjänsterna **Bing Virtual Earth** eller **Bing-geokodning**, som har upprättats över det offentliga Internet.
* **Hämta Data** från flera data datakällor som **Webben** eller externa SaaS-leverantörer sker via det offentliga Internet.

### <a name="power-bi-paas-and-expressroute"></a>Power BI PaaS och ExpressRoute
Power BI erbjuder API:er och andra plattformbaserade funktioner som gör att utvecklare kan skapa anpassade Power BI-lösningar och appar. Följande tjänster, förutom telemetri- och CDN-data som beskrivs tidigare i det här avsnittet, används vid överföring av data i Power BI PaaS via det offentliga Internet:

| PaaS-aktivitet | Ytterligare använda mål |
| --- | --- |
| Inbäddad offentligt (telemetri) |`c1.microsoft.com` |
| Anpassade visuella objekt (CDN) |`*.azureedge.net` |

Vissa **anpassade visuella objekt** skapas av tredje part, andra skapas av Microsoft. Dessa sidor kan men behöver inte använda ExpressRoute.

### <a name="power-bi-mobile-and-expressroute"></a>Power BI Mobile och ExpressRoute
Det här dokumentet omfattar inte användning av Power BI Mobile-appar.  

### <a name="on-premises-data-gateway-and-expressroute"></a>Lokal datagateway och ExpressRoute
När en **lokal datagateway** används med Power BI är överföringarna kompatibla med ExpressRoute, med undantag för användaraktiviteter som beskrivs i avsnittet **Power BI SaaS-program och ExpressRoute** tidigare i det här avsnittet.  

