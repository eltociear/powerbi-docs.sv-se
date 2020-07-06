---
title: Lägg till Power BI-URL:er i listan över tillåtna
description: I den här artikeln listas URL-slutpunkter och -portar som ska läggas till i listan över tillåtna för anslutning till Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 38e6668c0fb15d1279923b77042cdedebe6dd139
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485080"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>Lägg till Power BI URL:er till din lista över tillåtna
[//]: # "suparnap, miwehnia, natham är kontaktpersoner för att underhålla den här listan"

Power BI-tjänsten kräver en Internetanslutning. De slutpunkter som anges i tabellerna i den här artikeln ska vara nåbara för kunder som använder Power BI-tjänsten.

För att kunna använda Power BI-tjänsten måste du kunna ansluta till de slutpunkter som är märkta med **krävs** i tabellerna nedan, samt till alla slutpunkter som är märkta med **krävs** på de länkade webbplatserna. Om en länk till en extern webbplats refererar till ett visst avsnitt behöver du bara granska slutpunkterna i det avsnittet.

Slutpunkter som är märkta med **valfritt** kan även läggas till i listor över tillåtna för att specifika funktioner ska fungera.

Power BI-tjänsten kräver endast att TCP-port 443 är öppen för de listade slutpunkterna.

Jokertecken (*) representerar alla nivåer under rotdomänen, och Saknas används när ingen information är tillgänglig. Kolumnen **Mål** är en lista med domännamn och länkar till externa webbplatser som innehåller ytterligare slutpunktsinformation.

>[!Important]
>Informationen i tabellerna nedan gäller inte för Power BI Tyskland, Power BI Kina som drivs av 21Vianet eller Power BI för amerikanska myndigheter. Läs [anslut myndigheter och globala Azure Cloud Services](service-govus-overview.md#connect-government-and-global-azure-cloud-services) för att läsa mer om kommunikation mellan molntjänster.

## <a name="authentication"></a>Autentisering

Power BI är beroende av de obligatoriska slutpunkterna i avsnitten om autentisering och identiteter i Microsoft 365. För att kunna använda Power BI måste du kunna ansluta till slutpunkterna på den länkade webbplatsen nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Autentisering och identitet | Se dokumentationen om [vanliga URL:er och Office Online-URL:er för Microsoft 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | Saknas |

## <a name="general-site-usage"></a>Allmän webbplatsanvändning

För allmän användning av Power BI måste du kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Backend-API:er | api.powerbi.com | TCP 443 |
| 2 | **Krävs:** Backend-API:er | *.analysis.windows.net | TCP 443 |
| 3 | **Krävs:** Backend-API:er | *.pbidedicated.windows.net | TCP 443 |
| 4 | **Krävs:** Innehållsleverantörsnätverk (CDN) | content.powerapps.com | TCP 443 |
| 5 | **Krävs:** Microsoft 365-integrering | Se dokumentationen om [vanliga URL:er och Office Online-URL:er för Microsoft 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | Saknas |
| 6 | **Krävs:** Portal | *.powerbi.com | TCP 443 |
| 7 | **Krävs:** Tjänsttelemetri | dc.services.visualstudio.com | TCP 443 |
| 8 | **Valfritt:** Informationsmeddelanden | dynmsg.modpim.com | TCP 443 |
| 9 | **Valfritt:** NPS-undersökningar | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administration

För att kunna använda administrativa funktioner i Power BI måste du kunna ansluta till slutpunkterna på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** För att hantera användare och visa granskningsloggar | Se dokumentationen om [vanliga URL:er och Office Online-URL:er för Microsoft 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | Saknas |
| | | |

## <a name="getting-data"></a>Hämta data

För att hämta data från specifika datakällor, till exempel OneDrive, måste du kunna ansluta till slutpunkterna i tabellen nedan. Åtkomst till ytterligare Internetdomäner och URL:er kan krävas för specifika datakällor som används inom organisationen.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** AppSource (interna eller externa appar i Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Valfritt:** Logga in och hämta data för innehållspaket | Beror på vilka innehållspaket som används | Beror på vilka innehållspaket som används |
| 3 | **Valfritt:** Importera filer från OneDrive – personlig | Se [webbplatsen för URL:er och portar som krävs](https://docs.microsoft.com/onedrive/required-urls-and-ports) | Saknas |
| 4 | **Valfritt:** Självstudievideon Power BI på 60 sekunder | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Valfritt:** PubNub-strömmande datakällor | Se [PubNub-dokumentationen](https://support.pubnub.com/support/solutions/articles/14000043522) | Saknas |
| | | |

## <a name="dashboard-and-report-integration"></a>Instrumentpanels- och rapportintegration

Power BI är beroende av vissa slutpunkter för att kunna stödja dina instrumentpaneler och rapporter. Du måste kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Excel-integration | Se dokumentationen om [vanliga URL:er och Office Online-URL:er för Microsoft 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | Saknas |
| | | |

## <a name="power-bi-visuals"></a>Visuella objekt för Power BI

Power BI är beroende av vissa slutpunkter för att kunna visa och få åtkomst till anpassade visuella Power BI-objekt. Du måste kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Krävs:** Importera ett anpassat visuellt objekt från Microsoft Azure Marketplace-gränssnittet eller från en fil | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Valfritt:** Bing-kartor | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Valfritt:** PowerApps | Se [avsnittet om tjänster som krävs](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) på webbplatsen för PowerApps-systemkrav | Saknas |
| 4 | **Valfritt:** Visio | Se dokumentationen om [vanliga URL:er och Office Online-URL:er för Microsoft 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), samt [SharePoint Online och OneDrive för Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | Saknas |
| | | |

## <a name="related-external-sites"></a>Relaterade externa webbplatser

Power BI-länkar till andra relaterade webbplatser. Dessa webbplatser är värdar för dokumentation, support, förfrågningar om nya funktioner och mycket annat. Åtkomst till dessa webbplatser påverkar inte funktionerna i Power BI, så det är valfritt att lägga till dem i listan över tillåtna.

| Rad | Syfte | Mål | Portar |
| --- | --- | --- | --- |
| 1 | **Valfritt:** Community-webbplats | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Valfritt:** Dokumentationswebbplats | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Valfritt:** Nedladdningswebbplats (för Power BI Desktop osv.) | download.microsoft.com | TCP 443 |
| 4 | **Valfritt:** Externa omdirigeringar | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Valfritt:** Webbplats för feedbackidéer| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Valfritt:** Power BI-webbplats – landningssida, länkar för att läsa mer, supportwebbplats, nedladdningslänkar, partnerdemonstration osv. | powerbi.microsoft.com | TCP 443 |
| 7 | **Valfritt:** Power BI Developer Center | dev.powerbi.com | TCP 443 |
| 8 | **Valfritt:** Supportwebbplats | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
