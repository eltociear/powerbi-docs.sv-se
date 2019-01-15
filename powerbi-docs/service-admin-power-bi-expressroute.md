---
title: Power BI och ExpressRoute
description: Power BI och ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0c4618150094a4eabb0dc9745e9ac93e4f342ff1
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54291106"
---
# <a name="power-bi-and-expressroute"></a>Power BI och ExpressRoute

**ExpressRoute** är en Azure-tjänst som låter dig skapa privata anslutningar mellan Azure-datacenter (där Power BI finns) och lokal infrastruktur, eller skapa privata anslutningar mellan Azure-datacenter och din samordningsmiljö.

Med **Power BI** och **ExpressRoute** kan du skapa en privat nätverksanslutning från din organisation till Power BI (eller med hjälp av din Internet-leverantörs samordningsanläggning), vilket kringgår Internet och ger bättre skydd för dina känsliga Power BI-data och -anslutningar.

Mer information finns i [Översikt över ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI är kompatibelt med ExpressRoute, med några få undantag där Power BI hämtar eller skickar data via det offentliga Internet. En lista över URL:er som Power BI använder finns i [URL:er för Power BI](power-bi-whitelist-urls.md).

![ExpressRoute-diagram](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)