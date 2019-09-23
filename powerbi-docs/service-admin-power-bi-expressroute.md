---
title: Power BI och ExpressRoute
description: Power BI och ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c7d12bf6a1a2a02c988f8351a1844be1080ad2b8
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074804"
---
# <a name="power-bi-and-expressroute"></a>Power BI och ExpressRoute

**ExpressRoute** är en Azure-tjänst som låter dig skapa privata anslutningar mellan Azure-datacenter (där Power BI finns) och lokal infrastruktur, eller skapa privata anslutningar mellan Azure-datacenter och din samordningsmiljö.

Med **Power BI** och **ExpressRoute** kan du skapa en privat nätverksanslutning från din organisation till Power BI (eller med hjälp av din Internet-leverantörs samordningsanläggning), vilket kringgår Internet och ger bättre skydd för dina känsliga Power BI-data och -anslutningar.

Mer information finns i [Översikt över ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI är kompatibelt med ExpressRoute, med några få undantag där Power BI hämtar eller skickar data via det offentliga Internet. En lista över URL:er som Power BI använder finns i [URL:er för Power BI](power-bi-whitelist-urls.md).

![ExpressRoute-diagram](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)