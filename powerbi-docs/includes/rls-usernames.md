## <a name="using-the-username-or-userprincipalname-dax-function"></a>Använda DAX-funktionen username() eller userprincipalname()
Du kan använda funktionerna DAX *username()* eller *userprincipalname()* i din datauppsättning. Du kan använda dem i uttryck i Power BI Desktop. När du publicerar din modell kommer den att användas i Power BI-tjänsten.

I Power BI Desktop *username()* returneras en användare i formatet *domän\användare* och *userprincipalname()* returneras en användare i formatet  *user@contoso.com*.

I Power BI-tjänsten *username()* och *userprincipalname()* både returnerar användarens primära namn (User Principal Name). Detta liknar en e-postadress.

