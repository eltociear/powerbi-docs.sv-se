---
ms.openlocfilehash: 240045c05a35a6583b537b785c6639a39c6aa9d4
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58051809"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definiera roller och regler i Power BI Desktop
Du kan definiera roller och regler i Power BI Desktop. När du publicerar till Power BI publiceras även rolldefinitionerna.

Följ dessa steg för att definiera säkerhetsroller.

1. Importera data till Power BI Desktop-rapporten eller konfigurera en DirectQuery-anslutning.
   
   > [!NOTE]
   > Du kan inte definiera roller i Power BI Desktop för live-anslutningar i Analysis Services. Du måste göra det i Analysis Services-modellen.
   > 
   > 
1. Välj fliken **Modellering**.
2. Välj **Hantera roller**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Välj **Skapa**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Ange ett namn på rollen. 
6. Välj den tabell som du vill tillämpa DAX-regeln på.
7. Ange DAX-uttrycken. Uttrycket måste returnera sant eller falskt. Exempelvis: [Entity ID] = ”Value”.
   
   > [!NOTE]
   > Du kan använda *username()* i detta uttryck. Observera att *username()* har formatet *DOMÄN\användarnamn* i Power BI Desktop. I Power BI-tjänsten och Power BI-rapportservern används formatet för användarens huvudnamn (UPN). Du kan även använda *userprincipalname()*, vilket alltid returnerar användaren i samma format som dess huvudnamn, *användarnamn\@contoso.com*.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. När du har skapat DAX-uttrycket markerar du kryssrutan ovanför uttrycksrutan för att verifiera uttrycket.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
9. Välj **Spara**.

Du kan inte tilldela användare till en roll i Power BI Desktop. Du kan tilldela dem i Power BI-tjänsten. Du kan aktivera dynamisk säkerhet i Power BI Desktop genom att använda DAX-funktionerna *username()* eller *userprincipalname()* samt konfigurera rätt relationer. 

