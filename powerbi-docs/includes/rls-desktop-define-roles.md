## <a name="define-roles-and-rules-within-power-bi-desktop"></a>Definiera roller och regler i Power BI Desktop
Du kan definiera roller och regler i Power BI Desktop. När du publicerar till Power BI publiceras även rolldefinitionerna.

Gör följande för att definiera säkerhetsroller.

1. Importera data till Power BI Desktop-rapporten eller konfigurera en DirectQuery-anslutning.
   
   > [!NOTE]
   > Du kan inte definiera roller i Power BI Desktop för live-anslutningar i Analysis Services. Du måste göra det i Analysis Services-modellen.
   > 
   > 
2. Välj fliken **Modellering**.
3. Välj **Hantera roller**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Välj **Skapa**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Ange ett namn på rollen. 
6. Välj den tabell som du vill tillämpa DAX-regeln på.
7. Ange DAX-uttrycken. Uttrycket måste returnera sant eller falskt. Exempelvis: [Entity ID] = ”Value”.
   
   > [!NOTE]
   > Du kan använda *username()* i detta uttryck. Observera att *username()* har formatet *DOMÄN\användarnamn* i Power BI Desktop. I Power BI-tjänsten har den samma format som användarens UPN. Du kan även använda *userprincipalname()*, vilket alltid returnerar användaren i samma format som dess huvudnamn.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. När du har skapat DAX-uttrycket markerar du kryssrutan ovanför uttrycksrutan för att verifiera uttrycket.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
9. Välj **Spara**.

Du kan inte tilldela användare till en roll i Power BI Desktop. Detta görs i Power BI-tjänsten. Du kan aktivera dynamisk säkerhet i Power BI Desktop genom att använda DAX-funktionerna *username()* eller *userprincipalname()* samt konfigurera rätt relationer.

