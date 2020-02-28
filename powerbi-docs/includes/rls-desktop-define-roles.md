---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464445"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definiera roller och regler i Power BI Desktop
Du kan definiera roller och regler i Power BI Desktop. När du publicerar till Power BI publiceras även rolldefinitionerna.

Följ dessa steg för att definiera säkerhetsroller.

1. Importera data till Power BI Desktop-rapporten eller konfigurera en DirectQuery-anslutning.
   
   > [!NOTE]
   > Du kan inte definiera roller i Power BI Desktop för live-anslutningar i Analysis Services. Du måste göra det i Analysis Services-modellen.
   > 
   > 
2. Välj **Hantera roller** på fliken **Modellering**.
   
   ![Välj Hantera roller](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. Välj **Skapa** i fönstret **Hantera roller**.
   
   ![Välj Skapa](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. Ange ett namn på rollen under **Roller**. 
5. Välj den tabell som du vill tillämpa DAX-regeln på under **Tabeller**.
6. I rutan **DAX-uttryck för tabellfilter** anger du DAX-uttrycket. Det här uttrycket returnerar värdet true eller false. Exempel: ```[Entity ID] = “Value”```.
      
   ![Fönstret Hantera roller](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > Du kan använda *username()* i detta uttryck. Observera att *username()* har formatet *DOMÄN\användarnamn* i Power BI Desktop. I Power BI-tjänsten och Power BI-rapportservern används formatet för användarens huvudnamn (UPN). Du kan även använda *userprincipalname()* , vilket alltid returnerar användaren i samma format som dess huvudnamn, *användarnamn\@contoso.com*.
   > 
   > 

7. När du har skapat DAX-uttrycket markerar du kryssrutan ovanför uttrycksrutan för att verifiera uttrycket.
      
   ![Validera DAX-uttrycket](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > I den här uttrycksrutan använder du kommatecken för att separera DAX-funktionsargumenten även om du använder ett språk som normalt använder semikolonavgränsare (t.ex. franska eller tyska). 
   >
   >
   
8. Välj **Spara**.

Du kan inte tilldela användare till en roll i Power BI Desktop. Du kan tilldela dem i Power BI-tjänsten. Du kan aktivera dynamisk säkerhet i Power BI Desktop genom att använda DAX-funktionerna *username()* eller *userprincipalname()* samt konfigurera rätt relationer. 

