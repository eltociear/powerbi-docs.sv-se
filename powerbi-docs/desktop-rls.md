---
title: Förstå säkerhet på radnivå (RLS) med Power BI Desktop
description: Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI Desktop.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/03/2018
ms.author: maghan
LocalizationGroup: Create reports
ms.openlocfilehash: 022668737f6bcce987b2923ba7a4416f4a08460a
ms.sourcegitcommit: 001ea0ef95fdd4382602bfdae74c686de7dc3bd8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38875998"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Säkerhet på radnivå (RLS) med Power BI Desktop
Säkerhet på radnivå (RLS) med Power BI Desktop begränsar åtkomst till data för givna användare. Filter begränsar data på radnivå. Du kan definiera filter inom roller.

Du kan nu konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan också konfigurera RLS på datauppsättningar som använder DirectQuery, till exempel SQL Server. Tidigare kunde du endast att implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För Analysis Services live-anslutningar konfigurerar du säkerhet på radnivå på den lokala modellen. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

> [!IMPORTANT]
> Om du har definierat roller och regler i Power BI-tjänsten måste du återskapa de här rollerna i Power BI Desktop och publicera rapporten till tjänsten.
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

