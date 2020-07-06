---
title: Begränsa dataåtkomsten med säkerhet på radnivå (RLS) för Power BI Desktop
description: Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 9036967c826dee83847c3bc3d4a903bbe749b2ce
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238652"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Begränsa dataåtkomsten med säkerhet på radnivå (RLS) för Power BI Desktop

Du kan använda säkerhet på radnivå (RLS) med Power BI Desktop för att begränsa åtkomst till data för vissa användare. Filter begränsar data på radnivå. Du kan definiera filter inom roller.

Du kan nu konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan även konfigurera RLS på datamängder som använder [DirectQuery](../connect-data/desktop-use-directquery.md), till exempel SQL Server. Tidigare kunde du endast implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För Analysis Services live-anslutningar konfigurerar du säkerhet på radnivå på den lokala modellen. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

> [!IMPORTANT]
> Om du har definierat roller och regler i Power BI-tjänsten behöver du återskapa de rollerna i Power BI Desktop och publicera rapporten till tjänsten. Läs mer om alternativ för [RLS i Power BI-tjänsten](../admin/service-admin-rls.md).

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Säkerhet på radnivå (RLS) med Power BI](../admin/service-admin-rls.md)
- [Vägledning om säkerhet på radnivå (RLS) med Power BI Desktop](../guidance/rls-guidance.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
