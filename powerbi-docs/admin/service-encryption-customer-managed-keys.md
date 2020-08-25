---
title: Använda kundhanterade nycklar i Power BI
description: Lär dig hur du använder kundhanterade nycklar i Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160950"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Använda kundhanterade nycklar i Power BI

Power BI krypterar data i vila och under bearbetning. Som standard använder Power BI Microsoft-hanterade nycklar till datakrypteringen. Organisationer kan välja att använda egna nycklar till kryptering av användarinnehåll i vila i hela Power BI, från rapportbilder till importerade datamängder i Premium-kapaciteter. 

## <a name="why-use-customer-managed-keys"></a>Skäl till att använda kundhanterade nycklar
Med kundhanterade nycklar i Power BI kan organisationer uppfylla efterlevnadskraven för datakryptering i vila hos sin molntjänstleverantör (i det här fallet Microsoft). CMK gör att organisationer kan kryptera sitt Power BI-användarinnehåll med en nyckel de tillhandahåller och hanterar själva. Om en kundhanterad nyckel återkallas blir innehållet i Power BI oläsligt för alla inom en timme, även för Microsoft. Jämfört med BYOK-erbjudandet omfattar CMK även användarinnehåll utanför Power BI Premium-kapaciteter. Dessutom används striktare policyer för cachelagring, och BYOK aktiveras för alla kapaciteter som standard. 
 
## <a name="how-to-use-customer-managed-keys"></a>Så här använder du kundhanterade nycklar
Om du vill använda kundhanterade nycklar i Power BI måste din organisation uppfylla storlekskraven. Organisationens globala administratör måste skicka in en supportbegäran till Microsoft, eller så kan administratören kontakta den som ansvarar för organisationens Microsoft-konto med eventuella frågor.  


## <a name="next-steps"></a>Nästa steg

Följande länk ger information om kundhanterade nycklar du kan ha nytta av:

* [Använda egna krypteringsnycklar för Power BI](service-encryption-byok.md)
* [Konfigurera Multi-Geo-stöd för Power BI Premium](service-admin-premium-multi-geo.md)
* [Så fungerar kapaciteter](service-premium-what-is.md#how-capacities-function)
* [Inkrementell uppdatering](service-premium-incremental-refresh.md).
