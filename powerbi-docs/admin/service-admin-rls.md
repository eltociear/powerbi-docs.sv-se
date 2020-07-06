---
title: Säkerhet på radnivå (RLS) med Power BI
description: Så här konfigurerar du säkerhet på radnivå för importerade datauppsättningar och DirectQuery i Power BI-tjänsten.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.author: kfollis
ms.date: 12/05/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 94a65a826cce3cdb0821e8127e45a1f983ad7d89
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85227871"
---
# <a name="row-level-security-rls-with-power-bi"></a>Säkerhet på radnivå (RLS) med Power BI

Säkerhet på radnivå (RLS) med Power BI kan användas för att begränsa åtkomst till data för givna användare. Filter begränsar åtkomst till data på radnivå och du kan definiera filter inom roller. Tänk på att medlemmar i en arbetsyta har åtkomst till datauppsättningar i arbetsytan i Power BI-tjänsten. RLS begränsar inte åtkomsten till data.

Du kan konfigurera RLS för datamodeller som importerats till Power BI med Power BI Desktop. Du kan också konfigurera RLS på datauppsättningar som använder DirectQuery, till exempel SQL Server. Tidigare kunde du endast att implementera RLS inom lokala Analysis Services-modeller utanför Power BI. För live-anslutningar med Analysis Services eller Azure Analysis Services konfigurerar du säkerhet på radnivå i modellen, inte i Power BI Desktop. Säkerhetsalternativet visas inte för datauppsättningar med live-anslutning.

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

Som standard använder säkerhetsfiltrering på radnivå sig av enkelriktade filter, oavsett om relationerna är inställda på enkelriktade eller dubbelriktade. Du kan aktivera dubbelriktad korsfiltrering med säkerhet på radnivå manuellt genom att markera relationen och markera kryssrutan **Tillämpa säkerhetsfilter i båda riktningarna**. Du bör markera den här rutan när du även har implementerat dynamisk säkerhet på radnivå på servernivån, där säkerhet på radnivå baseras på användarnamn eller inloggnings-ID.

Mer information finns i [dubbelriktad korsfiltrering med DirectQuery i Power BI Desktop](../transform-model/desktop-bidirectional-filtering.md) och den tekniska artikeln [skydda Tabular BI-Semantikmodellen](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

![Använd säkerhetsfilter](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Hantera säkerheten på din modell

Om du vill hantera säkerheten på din datamodell, gör du följande.

1. Välj **ellipsen (...)**  för en datauppsättning.
2. Välj **Säkerhet**.
   
   ![Tillämpa säkerhetsfilter i båda riktningarna](media/service-admin-rls/rls-security.png)

Det här tar dig till RLS-sidan där du kan lägga till medlemmar i en roll som du skapade i Power BI Desktop. Endast ägare av datauppsättningen ser säkerhet. Om datauppsättningen är i en grupp, visas bara säkerhetsalternativet för gruppens administratörer. 

Du kan bara skapa eller ändra roller i Power BI Desktop.

## <a name="working-with-members"></a>Arbeta med medlemmar

### <a name="add-members"></a>Lägg till medlemmar

Du kan lägga till en medlem i rollen genom att skriva in e-postadressen eller namnet på användaren, säkerhetsgruppen eller distributionslistan som du vill lägga till. Du kan inte lägga till grupper som skapas i Power BI. Du kan lägga till medlemmar [som är externa för organisationen](../guidance/whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Lägga till en medlem](media/service-admin-rls/rls-add-member.png)

Du kan också se hur många medlemmar som är en del av rollen efter numret i parentes bredvid rollnamnet eller bredvid medlemmar.

![Medlemmar i rollen](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Ta bort medlemmar

Du kan ta bort medlemmar genom att välja X bredvid deras namn. 

![Ta bort medlem](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validera rollen i Power BI-tjänsten

Du kan validera att den roll som du har definierat fungerar genom att testa rollen. 

1. Välj **Fler alternativ** (...) bredvid rollen.
2. Välj **testa data som roll**

![Testa som roll](media/service-admin-rls/rls-test-role.png)

Du ser sedan rapporter som är tillgängliga för den här rollen. Instrumentpaneler visas inte i den här vyn. I det blå fältet ovan visas vad som används.

![Visas nu som <roll>](media/service-admin-rls/rls-test-role2.png)

Du kan testa andra roller eller en kombination av roller, genom att välja **visar som**.

![Testa andra roller](media/service-admin-rls/rls-test-role3.png)

Du kan välja att visa data som en specifik person, eller så kan du välja en kombination av tillgängliga roller för att verifiera att de fungerar. 

Om du vill återgå till normal visning, väljer du **tillbaka till säkerhet på radnivå**.

[!INCLUDE [include-short-name](../includes/rls-usernames.md)]

## <a name="using-rls-with-workspaces-in-power-bi"></a>Använda RLS med arbetsytor i Power BI

Om du publicerar din Power BI Desktop-rapport till en arbetsyta i Power BI-tjänsten används rollerna för skrivskyddade medlemmar. Du måste ange att medlemmar bara ska kunna visa Power BI-innehållet i inställningarna för arbetsytan.

> [!WARNING]
> Om du har konfigurerat arbetsytan så att medlemmar har redigeringsbehörighet så används inte RLS-rollerna för dem. Användare kommer att kunna se alla data.

![Gruppinställningar](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Begränsa dataåtkomsten med säkerhet på radnivå (RLS) för Power BI Desktop](../create-reports/desktop-rls.md)
- [Vägledning säkerhet på radnivå (RLS) med Power BI Desktop](../guidance/rls-guidance.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
