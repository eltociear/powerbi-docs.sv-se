---
title: 'Tredjepartstjänst: Facebook-anslutningsprogram för Power BI Desktop'
description: 'Tredjepartstjänst: Facebook-anslutningsprogram för Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/22/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6e33e1a27903cc3fbce5c3f504287fa96dbf8305
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34296628"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook-anslutningsprogram för Power BI Desktop
Facebook-anslutningsprogrammet i **Power BI Desktop** använder sig av Facebook Graph API. Det innebär att funktioner och tillgänglighet kan variera över tid.

Du kan se en [självstudiekurs om Facebook-anslutningsprogrammet för Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Facebook gjorde v1.0 av sitt Graph API inaktuellt 30<sup>:e</sup> april 2015. Power BI använder sig av Graph API i bakgrunden för Facebook-anslutningsprogrammet så att du kan ansluta till dina data och analysera dem.

Frågor som skapats innan 30 <sup>april</sup> 2015 fungerar inte längre eller returnerar mindre data. Efter 30 april<sup></sup> 2015, använder sig Power BI av v2.8 i alla anrop till Facebook-API:t. Om din fråga skapades innan 30 April 2015 och du inte har använt den sen dess, behöver du förmodligen autentisera den igen, för att godkänna den nya uppsättningen behörigheter som vi ber om.

Även om vi försöker släppa uppdateringar i takt med förändringar, kan API:t ändras på ett sätt som påverkar resultaten för de frågor som vi skapar. I vissa fall kanske inte vissa frågor längre stöds. På grund av detta beroende kan vi inte garantera resultatet för dina frågor när du använder det här anslutningsprogrammet.

Mer information om ändringen i Facebook-API:t finns [här](https://developers.facebook.com/docs/apps/changelog#v2_0).

