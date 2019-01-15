---
title: Registrera en app för att bädda in Power BI-innehåll
description: Lär dig hur du registrerar ett program i Azure Active Directory för användning med inbäddning av Power BI-innehåll.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 96f91eefeab038419ce64e31c7b4b5755d6adf2c
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54286598"
---
# <a name="register-an-azure-ad-app-to-embed-power-bi-content"></a>Registrera en Azure AD-app för att bädda in Power BI-innehåll

Lär dig hur du registrerar en app i Azure Active Directory (Azure AD) för användning med inbäddning av Power BI-innehåll.

Du kan registrera din app med Azure AD så att din ansökan ger åtkomst till Power BI REST-API: er. När du väl har registrerat ditt program kan du upprätta en identitet för programmet och ange behörigheter till Power BI REST-resurser.

> [!IMPORTANT]
> Innan du registrerar en Power BI-app behöver du en [Azure Active Directory-klient och en organisationsanvändare](create-an-azure-active-directory-tenant.md). Appregistreringen misslyckas om du inte har registrerat dig för Power BI med en användare i din klientorganisation.

Det finns två sätt att registrera din app. Du kan antingen använda [registreringsverktyget för Power BI-appen](https://dev.powerbi.com/apps/) eller göra det direkt i Azure Portal. Registreringsverktyget för Power BI-appen är det enklaste alternativet eftersom du bara behöver fylla i ett fåtal fält. Använd Azure Portal om du vill göra ändringar i din app.

## <a name="register-with-the-power-bi-app-registration-tool"></a>Registrera med registreringsverktyget för Power BI-appen

Du måste registrera ditt program i **Azure Active Directory** om du vill upprätta en identitet för ditt program och ange behörigheter till Power BI REST-resurser. När du registrerar en ett program, t.ex. en konsolapp eller en webbplats, får du en identifierare som programmet använder för att identifiera sig gentemot de användare som det begär behörigheter från.

Så här gör du för att registrera din app med registreringsverktyget för Power BI-appen:

1. Gå till [dev.powerbi.com/apps](https://dev.powerbi.com/apps).
2. Välj **Logga in med ditt befintliga konto**.
3. Ange ett **Appnamn**.
4. Valet av apptyp beror på vilken sorts app du använder.

   * Använd **inbyggd app** för appar som körs på klientenheter. Välj **Inbyggd app** om du bäddar in innehåll för kunder oavsett vilken typ av program det gäller, även webbprogram.
   * Använd **webbapp för serversidan** för webbappar eller webb-API:er.

5. Ange ett värde för **omdirigerings-URL** och **hemsidans URL**. **Omdirigerings-URL:en** fungerar med alla giltiga URL:er.

    **URL:en för startsidan** är endast tillgänglig om du väljer apptypen **Webbapp för serversidan**.

    För exemplen som beskriver hur du *bäddar in för dina kunder* och hur du *integrerar en instrumentpanel i en webbapp* är **omdirigerings-URL**:en `http://localhost:13526/Redirect`. För rapport- och panelexemplet är **omdirigerings-URL**:en `http://localhost:13526/`.
6. Välj API:erna för det program som har åtkomst. Läs mer om Power BI-behörigheter i [Power BI-behörigheter](power-bi-permissions.md).

    ![Appregistrerings-API:er](media/register-app/app-registration-apis.png)
7. Välj **Registrera app**.

    När du gör det får du ett **klient-ID**, och om du väljer **Webbapp för serversidan** får du en **klienthemlighet**. Ditt **klient-ID** kan hämtas från Azure Portal vid ett senare tillfälle om det behövs. Om du tappar bort din **klienthemlighet** måste du skapa en ny på Azure Portal.

8. Navigera till Azure och välj **Bevilja behörigheter**.

   > [!Note]
   > Användare i klientorganisationen behöver åtkomst till **_Bevilja behörigheter_** för att kunna slutföra det här steget.

* Gå till Azure.
* Sök och välj **App-registreringar**.
* Välj din app.
* Välj **inställningar**.
* Välj **Nödvändiga behörigheter**.
* Välj **Power BI-tjänsten** för att verifiera de behörigheter som du har valt från App-registreringsplatsen.
* Välj **Bevilja behörigheter**.

Du kan nu använda det registrerade programmet som del av ditt anpassade program så att det interagerar med Power BI-tjänsten.

> [!IMPORTANT]
> Om du bäddar in innehåll för dina kunder måste du konfigurera ytterligare behörigheter på Azure Portal. Mer information finns i [tillämpa behörigheter för ditt program](#apply-permissions-to-your-application).

## <a name="register-with-the-azure-portal"></a>Registrera med Azure Portal

Ett annat alternativ för att registrera ditt program är att göra det direkt i Azure Portal. Följ dessa steg om du vill registrera din app.

1. Godkänn [villkoren för Microsoft Power BI-API](https://powerbi.microsoft.com/api-terms).
2. Logga in på [Azure Portal](https://portal.azure.com).
3. Välj Azure AD-klientorganisationen genom att markera ditt konto i sidans övre högra hörn.
4. I det vänstra navigeringsfönstret väljer du **Fler tjänster**, **App-registreringar** under **Säkerhet + Identitet**. Välj **Ny appregistrering**.

    ![Ny appregistrering](media/register-app/azuread-new-app-registration.png)
5. Följ anvisningarna och skapa ett nytt program.

   * För webbprogram anger du inloggnings-URL:en, som är bas-URL:en för din app där användare kan logga in, t. ex. `http://localhost:13526`).
   * Ange en **omdirigerings-URI** som används i Azure AD för att returnera tokensvar för interna program. Ange ett specifikt värde för din app (t.ex. `http://myapplication/Redirect`).

Mer information om hur du registrerar program i Azure Active Directory finns i [Integrera program med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)

## <a name="how-to-get-the-client-id"></a>Så här gör du för att hämta klient-id

När du registrerar ett program får du ett **klient-ID**.  **Klient-ID:t** begär behörigheter till användarna genom programmet för identifiering.

Så här får du ett klient-id:

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj Azure AD-klientorganisationen genom att markera ditt konto i sidans övre högra hörn.
3. I det vänstra navigeringsfönstret väljer du **Fler tjänster** och **App-registreringar**.
4. Välj det program som du vill hämta klient-id för.
5. Som du ser visas **Program-ID** som en GUID. Detta är klient-id för programmet.

    ![Klient-ID som visas som app-ID i appregistreringen](media/register-app/powerbi-embedded-app-registration-client-id.png)

## <a name="apply-permissions-to-your-application-within-azure-ad"></a>Tillämpa behörigheter för ditt program i Azure AD

> [!IMPORTANT]
> Det här avsnittet gäller endast för program som **bäddar in innehåll för sin organisation**.

Aktivera ytterligare behörigheter för programmet utöver de som finns på appregistreringssidan. Du kan göra detta via Azure AD Portal eller med programmering.

Logga in med *huvudkontot*, som används för inbäddning, eller med ett globalt administratörskonto.

### <a name="using-the-azure-ad-portal"></a>Med hjälp av Azure AD Portal

1. Bläddra till [App-registreringar](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) i Azure Portal och välj den app som du använder för att bädda in.

    ![Azure AD-registrerade appar](media/register-app/powerbi-embedded-azuread-registered-apps.png)
2. Välj **Nödvändiga behörigheter** under **API-åtkomst**.

    ![Behörigheter som krävs för Azure AD-appen](media/register-app/powerbi-embedded-azuread-app-required-permissions.png)

3. Inom **Nödvändiga behörigheter** väljer du **Power BI-tjänsten (Power BI)**.

    ![Appbehörigheter 03](media/register-app/powerbi-embedded-azuread-app-permissions03.png)

   > [!NOTE]
   > Om du har skapat appen direkt i Azure AD Portal är **Power BI-tjänsten (Power BI)** kanske inte tillgänglig. Väl i sådant fall **+ Lägg till** och sedan **1 Välj och API**. Välj **Power BI-tjänsten** i API-listan och välj **Välj**.  Om **Power BI-tjänsten (Power BI)** är inte tillgänglig i **+ Lägg till** ska du registrera dig för Power BI med minst en användare.

4. Välj alla behörigheter under **Delegerade behörigheter**. Du måste välja dem separat för valen ska sparas. Välj **Spara** när du är klar.

    ![Appbehörigheter 04](media/register-app/powerbi-embedded-azuread-app-permissions04.png)
5. Inom **Nödvändiga behörigheter** väljer du **Bevilja behörigheter**.

    Åtgärden **Bevilja behörigheter** krävs för *huvudkontot*. Annars blir du tillfrågad av Azure AD. Om kontot som utför den här åtgärden är en global administratör beviljar du behörighet till alla användare i din organisation för den här appen. Om kontot som utför den här åtgärden är *huvudkontot* och inte en global administratör beviljar du endast behörigheter till *huvudkontot* för den här appen.

    ![Bevilja behörigheter med dialogrutan](media/register-app/powerbi-embedded-azuread-app-grant-permissions.png)

### <a name="applying-permissions-programmatically"></a>Tillämpa behörigheter via programmering

1. Du måste hämta de befintliga tjänstobjekten (användare) i din klientorganisation. Mer information om hur du gör det finns i [hämta servicePrincipal](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/serviceprincipal_get).

    Du kan anropa *Get servicePrincipal*-API:et utan {id} så hämtas alla tjänstobjekt i klientorganisationen.
2. Sök efter ett huvudnamn för tjänsten med ditt appklients-ID som **appId**-egenskap.

3. Skapa en ny serviceplan om din app inte har någon.

    ```json
    Post https://graph.microsoft.com/beta/servicePrincipals
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

4. Bevilja appbehörigheter till Power BI-API:et

   Om du använder en befintlig klient och inte är intresserad av att bevilja behörigheter för alla klientanvändare kan du ge behörigheter till en specifik användare genom att ersätta värdet för **contentType** till **Principal**.

   Värdet för **consentType** kan vara antingen **AllPrincipals** eller **Principal**.

   * **AllPrincipals** används av administratören för en klientorganisation för att bevilja behörigheter för alla användare i klientorganisationen.
   * **Principal** används för att bevilja behörigheter för en specifik användare. I det här fallet bör ytterligare en egenskap läggas till i själva begäran, *principalId = {User_ObjectId}*.

     Du måste *bevilja behörigheter* för huvudkontot så att inte användarna uppmanas att ge sitt tillstånd av Azure AD, vilket inte är möjligt vid icke-interaktiv inloggning.

     ```json
     Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    **resourceId** *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* är inte universellt utan är olika för olika klienter. Det här värdet är objectId för Power BI-tjänsten i AAD-klienten.

    Du kan snabbt få det här värdet i Azure Portal:
    1. https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps
    2. Sök efter ”Power BI Service” i sökrutan

5. Bevilja appbehörigheter till Azure Active Directory (AAD)

   Värdet för **consentType** kan vara antingen **AllPrincipals** eller **Principal**.

   * **AllPrincipals** används av administratören för en klientorganisation för att bevilja behörigheter för alla användare i klientorganisationen.
   * **Principal** används för att bevilja behörigheter för en specifik användare. I det här fallet bör ytterligare en egenskap läggas till i själva begäran, *principalId = {User_ObjectId}*.

   Du måste *bevilja behörigheter* för huvudkontot så att inte användarna uppmanas att ge sitt tillstånd av Azure AD, vilket inte är möjligt vid icke-interaktiv inloggning.

   ```json
   Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
   Authorization: Bearer ey..qw
   Content-Type: application/json
   { 
   "clientId":"{Service_Plan_ID}",
   "consentType":"AllPrincipals",
   "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
   "scope":"User.Read Directory.AccessAsUser.All",
   "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
   "startTime":"2017-03-29T14:35:32.4933413+03:00"
   }
   ```

## <a name="next-steps"></a>Nästa steg

Nu när du har registrerat din app i Azure AD måste du autentisera användarna i appen. Mer information finns i [Autentisera användare och hämta en Azure AD-åtkomsttoken för din Power BI-app](get-azuread-access-token.md).

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)
