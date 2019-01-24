---
ms.openlocfilehash: 0ef0f2e250c61f11cc6418635a8e132242201072
ms.sourcegitcommit: 2c49a7cee9c77f46830ddfa59fdedbf30186d389
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54488985"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Verifiera rollerna i Power BI Desktop
När du har skapat rollerna kan du testa rollresultaten i Power BI Desktop.

1. Välj **Visa som roller**. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Du kan se roller som du har skapat i **Visa som roller**.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Välj en roll som du har skapat > **OK** för att tillämpa rollen. Rapporterna återger de data som är relevanta för rollen. 

4. Du kan också välja **Annan användare** och ange en viss användare. Det är bäst att ange användarens huvudnamn (UPN), eftersom det är det som Power BI-tjänsten och Power BI-rapportservern använder.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. Välj **OK** så återges rapporterna baserat på vad användaren kan se. 

I Power BI Desktop visas endast **Other user** (Annan användare) olika resultat om du använder dynamisk säkerhet som baseras på DAX-uttryck. 

