---
title: 'Tjänst från tredje part: Facebook-anslutningsprogram för Power BI Desktop'
description: 'Tjänst från tredje part: Facebook-anslutningsprogram för Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b02717c49a1207dfec39ebb1529e7e9b222fa62
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65512864"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook-anslutningsprogram för Power BI Desktop
Facebook-anslutningsprogrammet i **Power BI Desktop** använder sig av Facebook Graph API. Det innebär att funktioner och tillgänglighet kan variera över tid.

Du kan se en [självstudiekurs om Facebook-anslutningsprogrammet för Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Facebook upphörde April 30 2015 v1.0 av dess Graph-API. Power BI använder sig av Graph API i bakgrunden för Facebook-anslutningsprogrammet så att du kan ansluta till dina data och analysera dem.

Frågor som skapats före den 30 April 2015 fungerar inte längre eller returnerar mindre data. Efter 30 April-2015 använder Power BI v2.8 i alla anrop till Facebook-API. Om din fråga skapades innan 30 April 2015 och du inte har använt den sen dess, behöver du förmodligen autentisera den igen, för att godkänna den nya uppsättningen behörigheter som vi ber om.

Även om vi försöker släppa uppdateringar i takt med förändringar, kan API:t ändras på ett sätt som påverkar resultaten för de frågor som vi skapar. I vissa fall kanske inte vissa frågor längre stöds. Vi kan inte garantera resultatet för dina frågor när du använder den här anslutningen på grund av det här beroendet.

Mer information om ändringen i Facebook-API:t finns [här](https://developers.facebook.com/docs/apps/changelog#v2_0).

