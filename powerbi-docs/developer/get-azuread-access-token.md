---
title: Autentisera användare och hämta en Azure AD-åtkomsttoken för ditt program
description: Lär dig hur du registrerar ett program i Azure Active Directory för användning med inbäddning av Power BI-innehåll.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 7b2249964f2fff26bc68fea19fd0010d8990110b
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762546"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Hämta en Azure AD-åtkomsttoken för ditt Power BI-program

Lär dig hur du autentiserar användare i Power BI-programmet och hämtar en åtkomsttoken som ska användas med REST-API:et.

Innan du kan anropa Power BI REST API behöver du hämta en **åtkomsttoken för autentisering** för Azure Active Directory (Azure AD). En **åtkomsttoken** används för att ge din app åtkomst till instrumentpaneler, paneler och rapporter i **Power BI**. Läs mer om Azure Active Directorys flöde för **åtkomsttoken** i [Flöde för att bevilja auktoriseringskod till Azure AD](https://msdn.microsoft.com/library/azure/dn645542.aspx).

En åtkomsttoken kan hämtas på olika sätt beroende på hur du bäddar in innehåll. Två olika sätt används i den här artikeln.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Åtkomsttoken för Power BI-användare (användare äger data)

Det här exemplet används när användarna loggar manuellt till Azure AD med sin organisationsinloggning. Den här uppgiften används när innehåll bäddas in för Power BI-användare som kommer åt innehåll som de har åtkomst till i Power BI-tjänsten.

### <a name="get-an-authorization-code-from-azure-ad"></a>Hämta en auktoriseringskod från Azure AD

Det första steget för att hämta en **åtkomsttoken** är att få en auktoriseringskod från **Azure AD**. Skapa en frågesträng med följande egenskaper och omdirigerar den till **Azure AD**.

#### <a name="authorization-code-query-string"></a>Frågesträng för auktoriseringskod

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

När du skapar en frågesträng omdirigeras du till **Azure AD** för att få en **auktoriseringskod**.  Nedan finns en komplett C#-metod för att konstruera en frågesträng för **auktoriseringskoden** och omdirigera till **Azure AD**. När du har auktoriseringskoden får du en **åtkomsttoken** med hjälp av **auktoriseringskoden**.

Inom redirect.aspx.cs anropas [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) för att generera en token.

#### <a name="get-authorization-code"></a>Hämta auktoriseringskod

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.net/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Hämta en åtkomsttoken från en auktoriseringskod

Du bör nu ha fått en auktoriseringskod från Azure AD. När **Azure AD** omdirigeras tillbaka till din webbapp med en **auktoriseringskod**, använder du **auktoriseringskoden** för att få en åtkomsttoken. Nedan visas ett C#-exempel som du kan använda på din omdirigeringssida och händelsen Page_Load för default.aspx-sidan.

Namnområdet **Microsoft.IdentityModel.Clients.ActiveDirectory** kan hämtas från [Active Directorys autentiseringsbiblioteks](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet-paket.

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Åtkomsttoken för användare som inte använder Power BI (appen äger data)

Den här metoden används vanligtvis för program av ISV-typ där appen äger åtkomsten till data. Användarna är inte nödvändigtvis Power BI-användare och programmet kontrollerar autentisering och åtkomst för slutanvändarna.

### <a name="access-token-with-a-master-account"></a>Åtkomsttoken med ett huvudkonto

För den här metoden använder du ett enda *huvud*konto som är en Power BI Pro-användare. Autentiseringsuppgifterna för det här kontot lagras med programmet. Programmet autentiseras mot Azure AD med de lagrade autentiseringsuppgifterna. Kodexemplet nedan kommer från [exemplet där appen äger data](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Åtkomsttoken med tjänstens huvudnamn

För den här metoden använder du [tjänstens huvudnamn](embed-service-principal.md), som är en **appspecifik** token. Programmet autentiseras mot Azure AD med tjänstens huvudnamn. Kodexemplet nedan kommer från [exemplet där appen äger data](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="next-steps"></a>Nästa steg

Nu när du har rätt åtkomsttoken kan du anropa Power BI REST API för att bädda in innehåll. Mer information om hur du bäddar in ditt innehåll finns i [Bädda in dina Power BI-innehåll](embed-sample-for-customers.md#embed-content-within-your-application).

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)