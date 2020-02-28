---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464416"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Verifiera rollerna i Power BI Desktop
När du har skapat rollerna kan du testa rollresultaten i Power BI Desktop.

1. Välj **Visa som roller** på fliken **Modellering**. 

    ![Välj Visa som roller](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Du kan se de roller du har skapat i fönstret **Visa som roller**.

    ![Fönstret Visa som roller](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Välj en roll du har skapat och sedan **OK** för att tillämpa rollen. 

   Rapporterna återger de data som är relevanta för rollen.

4. Du kan också välja **Annan användare** och ange en viss användare. 

    ![Välj Annan användare](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Det är bäst att ange användarens huvudnamn (UPN), eftersom det är det som Power BI-tjänsten och Power BI-rapportservern använder.

   I Power BI Desktop visar bara **Annan användare** olika resultat om du använder dynamisk säkerhet baserad på dina DAX-uttryck. 

5. Välj **OK**. 

   Rapporten återges baserat på vad användaren kan se.



