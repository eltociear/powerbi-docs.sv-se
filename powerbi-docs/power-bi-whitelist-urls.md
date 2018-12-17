---
title: URL:er för Power BI för vitlistning
description: Den här artikeln beskriver de slutpunkter som bör kunna nås av kunder som använder Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.custom: seodec18
ms.openlocfilehash: dcf51f26aac018acdd58e4244f21e41a1b6f1bc6
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026646"
---
# <a name="power-bi-urls-for-whitelisting"></a>URL:er för Power BI för vitlistning

**Power BI-onlinetjänsten**, även kallad Power BI SaaS-appen (Software as a Service), kräver anslutning till Internet. Slutpunkterna nedan måste vara tillgängliga för kunder som använder Power BI-onlinetjänsten.

För att kunna använda Power BI-onlinetjänsten måste du kunna ansluta till de slutpunkter som är märkta med **krävs** i tabellerna nedan, samt till alla slutpunkter som är märkta med **krävs** på de länkade webbplatserna. Om en länk till en extern webbplats refererar till ett visst avsnitt behöver du bara granska slutpunkterna i det avsnittet.

Slutpunkter som är märkta med **valfritt** kanske också är **godkända** och rekommenderade för att specifika funktioner ska fungera.

Power BI-onlinetjänsten kräver endast att TCP-port 443 är öppen för de angivna slutpunkterna.

Jokertecken (*) representerar alla nivåer under rotdomänen, och Saknas används när ingen information är tillgänglig. Kolumnen **Mål** är en lista med fullständigt kvalificerade domännamn/domäner och länkar till externa webbplatser som innehåller ytterligare information om slutpunkter.

>[!Important]
>Informationen i tabellerna nedan gäller inte för **molnet för amerikanska myndigheter**, **molnet för Tyskland** eller **molnet för Kina**.

## <a name="authentication"></a>Autentisering

Power BI är beroende av de obligatoriska slutpunkterna i avsnitten om autentisering och identiteter i Office 365. För att kunna använda Power BI måste du kunna ansluta till slutpunkterna på den länkade webbplatsen nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Autentisering och identitet | Se Office 365-dokumentationen för [Office Online och vanliga URL:er](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | Saknas |

## <a name="general-site-usage"></a>Allmän webbplatsanvändning

För allmän användning av Power BI måste du kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Backend-API:er | *.analysis.windows.net | TCP 443 |
| 2 | **Krävs:** Office 365-integration | Se Office 365-dokumentationen för [Office Online och vanliga URL:er](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | Saknas |
| 3 | **Krävs:** Portal | app.powerbi.com | TCP 443 |
| 4 | **Krävs:** Tjänsttelemetri | dc.services.visualstudio.com | TCP 443 |
| 5 | **Valfritt:** Informationsmeddelanden | dynmsg.modpim.com | TCP 443 |
| 6 | **Valfritt:** NPS-undersökningar | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administration

För att kunna använda administrativa funktioner i Power BI måste du kunna ansluta till slutpunkterna på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** För att hantera användare och visa granskningsloggar | Se Office 365-dokumentationen för [Office Online och vanliga URL:er](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | Saknas |
| | | |

## <a name="getting-data"></a>Hämta data

För att hämta data från specifika datakällor, till exempel OneDrive, måste du kunna ansluta till slutpunkterna i tabellen nedan. Åtkomst till ytterligare Internetdomäner och URL:er kan krävas för specifika datakällor som används inom organisationen.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** AppSource (interna eller externa appar i Power BI) | appsource.microsoft.com </br> *.s-microsoft.com  | TCP 443 |
| 2 | **Valfritt:** Logga in och hämta data för innehållspaket | Beror på vilka innehållspaket som används | Beror på vilka innehållspaket som används |
| 3 | **Valfritt:** Importera filer från OneDrive – personlig | Se [webbplatsen för URL:er och portar som krävs](https://docs.microsoft.com/onedrive/required-urls-and-ports) | Saknas |
| 4 | **Valfritt:** Självstudievideon Power BI på 60 sekunder | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 5 | **Valfritt:** PubNub-strömmande datakällor | Se [PubNub-dokumentationen](https://support.pubnub.com/support/solutions/articles/14000043522) | Saknas |
| | | |

## <a name="dashboard-and-report-integration"></a>Instrumentpanels- och rapportintegration

Power BI är beroende av vissa slutpunkter för att kunna hantera dina instrumentpaneler och rapporter. Du måste kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Excel-integration | Se Office 365-dokumentationen för [Office Online och vanliga URL:er](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | Saknas |
| | | |

## <a name="custom-visuals"></a>Anpassade visuella objekt

Power BI är beroende av vissa slutpunkter för att kunna visa och komma åt de anpassade visuella objekten. Du måste kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Importera ett anpassat visuellt objekt från Microsoft Azure Marketplace-gränssnittet eller från en fil | *.azureedge.net </br> *.blob.core.windows.net </br> store.office.com | TCP 443 |
| 2 | **Valfritt:** Bing-kartor | bing.com </br> platform.bing.com </br> *.virtualearth.net | TCP 443 |
| 3 | **Valfritt:** PowerApps | Se [avsnittet om tjänster som krävs](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) på webbplatsen för PowerApps-systemkrav | Saknas |
| 4 | **Valfritt:** Visio | Se Office 365-dokumentationen för [Office Online och vanliga URL:er](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) samt [SharePoint Online och OneDrive för företag](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | Saknas |
| | | |

## <a name="related-external-sites"></a>Relaterade externa webbplatser

Power BI-länkar till andra relaterade webbplatser. Dessa webbplatser inbegriper dem som gäller dokumentation, support, förfrågningar om nya funktioner och mycket annat. Dessa webbplatser påverkar inte funktionerna i Power BI, så de kan tillåtas om så önskas.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Valfritt:** Community-webbplats | community.powerbi.com </br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Valfritt:** Dokumentationswebbplats | docs.microsoft.com </br> img-prod-cms-rt-microsoft-com.akamaized.net </br> statics-uhf-eas.akamaized.net </br> cdnssl.clicktale.net </br> ing-district.clicktale.net | TCP 443 |
| 3 | **Valfritt:** Nedladdningswebbplats (för Power BI Desktop osv.) | download.microsoft.com | TCP 443 |
| 4 | **Valfritt:** Externa omdirigeringar | aka.ms </br> go.microsoft.com | TCP 443 |
| 5 | **Valfritt:** Webbplats för feedbackidéer| ideas.powerbi.com </br> powerbi.uservoice.com | TCP 443 |
| 6 | **Valfritt:** Power BI-webbplats – landningssida, länkar för att läsa mer, supportwebbplats, nedladdningslänkar, partnerdemonstration osv. | powerbi.microsoft.com | TCP 443 |
| 7 | **Valfritt:** Power BI Developer Center | dev.powerbi.com | TCP 443 |
| 8 | **Valfritt:** Supportwebbplats | support.powerbi.com </br> s3.amazonaws.com </br> *.olark.com </br> logx.optimizely.com </br> mscom.demdex.net </br> tags.tiqcdn.com | TCP 443 |
| | | |