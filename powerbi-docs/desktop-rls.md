---
title: Begränsa dataåtkomsten med säkerhet på radnivå (RLS) för Power BI Desktop
description: Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 7a9aa0ca62ae4f1008d4cf47caa909841f9ec495
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464471"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Begränsa dataåtkomsten med säkerhet på radnivå (RLS) för Power BI Desktop

Du kan använda säkerhet på radnivå (RLS) med Power BI Desktop för att begränsa åtkomst till data för vissa användare. Filter begränsar data på radnivå. Du kan definiera filter inom roller.

Du kan nu konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan även konfigurera RLS på datamängder som använder [DirectQuery](desktop-use-directquery.md), till exempel SQL Server. Tidigare kunde du endast implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För Analysis Services live-anslutningar konfigurerar du säkerhet på radnivå på den lokala modellen. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

> [!IMPORTANT]
> Om du har definierat roller och regler i Power BI-tjänsten behöver du återskapa de rollerna i Power BI Desktop och publicera rapporten till tjänsten. Läs mer om alternativ för [RLS i Power BI-tjänsten](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Nästa steg

[Sälkerhet på radnivå (RLS) med Power BI-tjänsten](service-admin-rls.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/).