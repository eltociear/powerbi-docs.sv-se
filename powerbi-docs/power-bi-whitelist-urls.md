---
title: URL:er för Power BI
description: Slutpunkter måste vara tillgängliga för kunder som använder Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101149"
---
# <a name="power-bi-urls"></a>URL:er för Power BI

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
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Krävs:** Autentisering och identitet | Se [avsnittet om autentisering och identiteter i Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) på webbplatsen för Office 365-vitlistan | Saknas |

## <a name="general-site-usage"></a>Allmän webbplatsanvändning

För allmän användning av Power BI måste du kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Krävs:** API:er på serversidan | *.analysis.windows.net | TCP 443 |
| 2 | **Krävs:** Office 365-integration | Se [avsnittet om portalen och delade tjänster för Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) på webbplatsen för Office 365-vitlistan | Saknas |
| 3 | **Krävs:** Portal | app.powerbi.com | TCP 443 |
| 4 | **Krävs:** Tjänsttelemetri | dc.services.visualstudio.com | TCP 443 |
| 5 | **Valfritt:** Informationsmeddelanden | dynmsg.modpim.com | TCP 443 |
| 6 | **Valfritt:** NPS-undersökningar | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>Administration

För att kunna använda administrativa funktioner i Power BI måste du kunna ansluta till slutpunkterna på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Krävs:** För att hantera användare och visa granskningsloggar | Se [avsnittet om portalen och delade tjänster för Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) på webbplatsen för Office 365-vitlistan | Saknas |

## <a name="get-data"></a>Hämta data

För att kunna hämta data från specifika datakällor, till exempel OneDrive, måste du kunna ansluta till slutpunkterna i tabellen nedan.

| Rad | Syfte | Mål | Portar |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Krävs:** AppSource (interna eller externa appar i Power BI) | appsource.microsoft.com | TCP 443 |
| 2 | **Valfritt:** Importera filer från OneDrive – personlig | Se [webbplatsen för URL:er och portar som krävs](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) | Saknas |
| 3 | **Valfritt:** Självstudievideon Power BI på 60 sekunder | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **Valfritt:** PubNub-strömmande datakällor | Se [PubNub-dokumentationen](https://support.pubnub.com/support/solutions/articles/14000043522) | Saknas |

## <a name="dashboard-and-report-integration"></a>Instrumentpanels- och rapportintegration 

Power BI är beroende av vissa slutpunkter för att kunna hantera dina instrumentpaneler och rapporter. Du måste kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Krävs:** Excel-integration | Se [avsnittet om Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) på webbplatsen för Office 365-vitlistan | Saknas |

## <a name="custom-visuals"></a>Anpassade visuella objekt

Power BI är beroende av vissa slutpunkter för att kunna visa och komma åt de anpassade visuella objekten. Du måste kunna ansluta till slutpunkterna i tabellen och på de länkade webbplatserna nedan.

| Rad | Syfte | Mål | Portar |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Krävs:** Importera ett anpassat visuellt objekt från Marketplace-gränssnittet och en fil | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **Valfritt:** Bing Maps | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Valfritt:** PowerApps | Se [avsnittet om tjänster som krävs](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) på webbplatsen för PowerApps-systemkrav | Saknas |
| 4 | **Valfritt:** Visio | Se [avsnittet om Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) på webbplatsen för Office 365-vitlistan | Saknas |