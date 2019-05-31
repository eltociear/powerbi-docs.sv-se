---
ms.openlocfilehash: eb7cba03daee47f6772fc46be50419731b41765e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61194133"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Verifiera rollerna i Power BI Desktop
När du har skapat rollerna kan du testa rollresultaten i Power BI Desktop.

1. Välj **Visa som roller**. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Du kan se roller som du har skapat i **Visa som roller**.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Välj en roll som du har skapat > **OK** för att tillämpa rollen. Rapporterna återger de data som är relevanta för rollen. 

4. Du kan också välja **Annan användare** och ange en viss användare. Det är bäst att ange användarens huvudnamn (UPN), eftersom det är det som Power BI-tjänsten och Power BI-rapportservern använder.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. När du väljer **OK** renderas rapporterna baserat på vad användaren kan se. 

I Power BI Desktop visas endast **Other user** (Annan användare) olika resultat om du använder dynamisk säkerhet som baseras på DAX-uttryck. 

