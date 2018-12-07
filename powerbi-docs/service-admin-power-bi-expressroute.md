---
title: Power BI och ExpressRoute
description: Power BI och ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 62289c974e25207f3a991e7f17a0ee965c729b8a
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900139"
---
# <a name="power-bi-and-expressroute"></a>Power BI och ExpressRoute

**ExpressRoute** är en Azure-tjänst som låter dig skapa privata anslutningar mellan Azure-datacenter (där Power BI finns) och lokal infrastruktur, eller skapa privata anslutningar mellan Azure-datacenter och din samordningsmiljö.

Med **Power BI** och **ExpressRoute** kan du skapa en privat nätverksanslutning från din organisation till Power BI (eller med hjälp av din Internet-leverantörs samordningsanläggning), vilket kringgår Internet och ger bättre skydd för dina känsliga Power BI-data och -anslutningar.

Mer information finns i [Översikt över ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI är kompatibelt med ExpressRoute, med några få undantag där Power BI hämtar eller skickar data via det offentliga Internet. En lista över URL:er som Power BI använder finns i [URL:er för Power BI](power-bi-whitelist-urls.md).

![ExpressRoute-diagram](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)