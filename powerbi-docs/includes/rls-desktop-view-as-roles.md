## <a name="validating-the-role-within-power-bi-desktop"></a>Verifiera rollen i Power BI Desktop
När du har skapat din roll kan du testa rollresultaten i Power BI Desktop. Om du vill göra detta väljer du **Visa som roller**.

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

I dialogrutan **Visa som roller** kan du ändra det du ser för den specifika användaren eller rollen. Du kan se roller som du har skapat.

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

Välj först den roll som du skapade och sedan **OK** för att tillämpa rollen på det du ser. Rapporterna återger endast de data som är relevanta för rollen.

Du kan också välja **Annan användare** och ange en viss användare. Det är bäst att ange användarens huvudnamn (UPN) eftersom det är det som Power BI-tjänsten använder. Välj **OK** så återges rapporterna baserat på vad användaren kan se. 

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

> [!NOTE]
> I Power BI Desktop visas endast olika resultat om du använder dynamisk säkerhet som baseras på DAX-uttryck.
> 
> 

