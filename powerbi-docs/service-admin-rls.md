---
title: "Säkerhet på radnivå (RLS) med Power BI"
description: "Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI-tjänsten."
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
ms.date: 11/29/2017
ms.author: asaxton
ms.openlocfilehash: 338921df57b77b1e79f9b71e814203734ab5971c
ms.sourcegitcommit: 7742f952c20695dfb475f74965c0065b02c01521
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/29/2017
---
# <a name="row-level-security-rls-with-power-bi"></a>Säkerhet på radnivå (RLS) med Power BI
<iframe width="560" height="315" src="https://www.youtube.com/embed/67fK0GoVQ80?showinfo=0" frameborder="0" allowfullscreen></iframe>

Säkerhet på radnivå (RLS) med Power BI kan användas för att begränsa åtkomst till data för givna användare. Filter begränsar data på radnivå. Du kan definiera filter inom roller.

Du kan konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan också konfigurera RLS på datauppsättningar som använder DirectQuery, till exempel SQL Server. Tidigare kunde du endast att implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För Analysis Services live-anslutningar konfigurerar du säkerhet på radnivå på den lokala modellen. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Hantera säkerheten på din modell
Om du vill hantera säkerheten på din datamodell, gör du följande.

1. Välj **ellipsen (...)**  för en datauppsättning.
2. Välj **säkerhet**.
   
   ![](media/service-admin-rls/rls-security.png)

Det här tar dig till RLS-sidan där du kan lägga till medlemmar i en roll som du skapade i Power BI Desktop. Endast ägare av datauppsättningen ser säkerhet. Om datauppsättningen är i en grupp, visas bara säkerhetsalternativet för gruppens administratörer. 

Du kan bara skapa eller ändra roller i Power BI Desktop.

## <a name="working-with-members"></a>Arbeta med medlemmar
### <a name="add-members"></a>Lägg till medlemmar
Du kan lägga till en medlem i rollen genom att skriva in e-postadressen eller namnet på användaren, säkerhetsgruppen eller distributionslistan som du vill lägga till. Den här medlemmen måste vara inom din organisation. Du kan inte lägga till grupper som skapas i Power BI.

![](media/service-admin-rls/rls-add-member.png)

Du kan också se hur många medlemmar som är en del av rollen efter numret i parentes bredvid rollnamnet eller bredvid medlemmar.

![](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Ta bort medlemmar
Du kan ta bort medlemmar genom att välja X bredvid deras namn. 

![](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validera rollen i Power BI-tjänsten
Du kan validera att den roll som du har definierat fungerar genom att testa rollen. 

1. Välj **ellipsen (...)**  bredvid rollen.
2. Välj **testa data som roll**

![](media/service-admin-rls/rls-test-role.png)

Du ser sedan rapporter som är tillgängliga för den här rollen. Instrumentpaneler visas inte i den här vyn. I det blå fältet ovan visas vad som används.

![](media/service-admin-rls/rls-test-role2.png)

Du kan testa andra roller eller en kombination av roller, genom att välja **visar som**.

![](media/service-admin-rls/rls-test-role3.png)

Du kan välja att visa data som en specifik person, eller så kan du välja en kombination av tillgängliga roller för att verifiera att de fungerar. 

Om du vill återgå till normal visning, väljer du **tillbaka till säkerhet på radnivå**.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-app-workspaces-in-power-bi"></a>Använd RLS med apparbetsytor i Power BI
Om du publicerar din Power BI Desktop-rapport till en apparbetsyta i Power BI-tjänsten, används rollerna till skrivskyddade medlemmar. Du behöver indikera att medlemmar bara kan se Power BI-innehåll i inställningarna för apparbetsytan.

> [!WARNING]
> Om du har konfigurerat apparbetsytan så att medlemmar har redigeringsbehörighet, tillämpas inte RLS-roller för dem. Användare kommer att kunna se alla data.
> 
> 

![](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Nästa steg
[Sälkerhet på radnivå (RLS) med Power BI Desktop](desktop-rls.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

