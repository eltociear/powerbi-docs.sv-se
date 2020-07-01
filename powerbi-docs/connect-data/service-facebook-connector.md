---
title: 'Tjänst från tredje part: Facebook-anslutningsprogram för Power BI Desktop'
description: 'Tjänst från tredje part: Facebook-anslutningsprogram för Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4dfdd21eebe0f8a66aea9dd3d30c38318e975daf
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236595"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Använda Facebook-anslutningsprogrammet för Power BI Desktop
Facebook-anslutningsprogrammet i **Power BI Desktop** använder sig av Facebook Graph API. Det innebär att funktioner och tillgänglighet kan variera över tid.

Du kan se en [självstudiekurs om Facebook-anslutningsprogrammet för Power BI Desktop](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Meddelande om utfasning av Facebook-dataanslutningen:** Import och uppdatering av data från Facebook i Excel kommer att sluta fungera från och med april 2020. Tills dess kan du använda Facebook-anslutningsprogrammet *Get & Transform (Power Query)* . Efter det datumet kommer du inte att kunna ansluta till Facebook och får i stället ett felmeddelande. Vi rekommenderar att du ändrar eller tar bort befintliga *Get & Transform-frågor (Power Query)* som använder Facebook-anslutningsprogrammet så snart som möjligt, så att du undviker eventuella oväntade resultat.


Facebook gjorde v1.0 av sitt Graph API inaktuellt 30 april 2015. Power BI använder sig av Graph API i bakgrunden för Facebook-anslutningsprogrammet så att du kan ansluta till dina data och analysera dem.

Frågor som skapats före 30 april 2015 fungerar inte längre eller returnerar färre data. Efter 30 april 2015 använder Power BI v2.8 i alla anrop till Facebook-API:et. Om din fråga skapades innan 30 April 2015 och du inte har använt den sen dess, behöver du förmodligen autentisera den igen, för att godkänna den nya uppsättningen behörigheter som vi ber om.

Även om vi försöker släppa uppdateringar i takt med förändringar, kan API:t ändras på ett sätt som påverkar resultaten för de frågor som vi skapar. I vissa fall kanske inte vissa frågor längre stöds. På grund av detta beroende kan vi inte garantera resultatet för dina frågor när du använder det här anslutningsprogrammet.

Mer information om ändringen i Facebook-API:t finns [här](https://developers.facebook.com/docs/apps/changelog#v2_0).

