---
title: "Förstå säkerhet på radnivå (RLS) med Power BI Desktop"
description: "Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI Desktop."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: asaxton
ms.openlocfilehash: e6b6efb976de8df6064f2eb1156237d1a1250807
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Säkerhet på radnivå (RLS) med Power BI Desktop
Säkerhet på radnivå (RLS) med Power BI Desktop kan användas för att begränsa åtkomst till data för givna användare. Filter begränsar data på radnivå. Du kan definiera filter inom roller.

Du kan nu konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan också konfigurera RLS på datauppsättningar som använder DirectQuery, till exempel SQL Server. Tidigare kunde du endast att implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För Analysis Services live-anslutningar konfigurerar du säkerhet på radnivå på den lokala modellen. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

> [!IMPORTANT]
> Om du definierat roller/regler i Power BI-tjänsten, måste du återskapa dessa roller i Power BI Desktop och publicera rapporten till tjänsten.
> 
> 

Läs mer om alternativ för [RLS i Power BI-tjänsten](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Nästa steg
[Sälkerhet på radnivå (RLS) med Power BI-tjänsten](service-admin-rls.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

