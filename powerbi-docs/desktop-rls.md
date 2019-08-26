---
title: Förstå säkerhet på radnivå (RLS) med Power BI Desktop
description: Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI Desktop.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 08/14/2019
LocalizationGroup: Create reports
ms.openlocfilehash: 91f2da65764480a0cf9cf298a052436b27e18c83
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560969"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Säkerhet på radnivå (RLS) med Power BI Desktop

Du kan använda säkerhet på radnivå (RLS) med Power BI Desktop för att begränsa åtkomst till data för vissa användare. Filter begränsar data på radnivå. Du kan definiera filter inom roller.

Du kan nu konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan även konfigurera RLS på datamängder som använder [DirectQuery](desktop-use-directquery.md), till exempel SQL Server. Tidigare kunde du endast implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För Analysis Services live-anslutningar konfigurerar du säkerhet på radnivå på den lokala modellen. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

> [!IMPORTANT]
> Om du har definierat roller och regler i Power BI-tjänsten behöver du återskapa de rollerna i Power BI Desktop och publicera rapporten till tjänsten.

Läs mer om alternativ för [RLS i Power BI-tjänsten](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Nästa steg

[Sälkerhet på radnivå (RLS) med Power BI-tjänsten](service-admin-rls.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)