---
title: Autentisera användare och hämta en Azure AD-åtkomsttoken för ditt program
description: Lär dig hur du registrerar ett program i Azure Active Directory för användning med inbäddning av Power BI-innehåll.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: cac59a4689eecd75c53ca1c62d7b097438b2ae53
ms.sourcegitcommit: 7f27b9eb0e001034e672050735ab659b834c54a3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74310845"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Hämta en Azure AD-åtkomsttoken för ditt Power BI-program

I den här artikeln får du lära dig hur du autentiserar användare i Power BI-appen och hämtar en åtkomsttoken som ska användas med [REST-API:et för Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Innan appen kan anropa REST-API:et måste du hämta en **åtkomsttoken för autentisering** för Azure Active Directory (Azure AD). Appen använder en token för att få åtkomst till instrumentpaneler, paneler och rapporter i Power BI. Mer information finns i [Auktorisera åtkomst till Azure Active Directory-webbappar med beviljandeflödet för OAuth 2.0-kod](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

En åtkomsttoken kan hämtas på olika sätt beroende på hur du bäddar in innehåll. I den här artikeln visas två olika sätt.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Åtkomsttoken för Power BI-användare (användare äger data)

Det här exemplet används när användarna loggar in manuellt till Azure AD med sin organisationsinloggning. Den här uppgiften används när du bäddar in innehåll för användare som har åtkomst till Power BI-tjänsten.

### <a name="get-an-azure-ad-authorization-code"></a>Hämta en auktoriseringskod för Azure AD

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
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

När du skapar en frågesträng omdirigeras du till **Azure AD** för att få en **auktoriseringskod**.  Nedan finns en komplett C#-metod för att konstruera en frågesträng för **auktoriseringskoden** och omdirigera till **Azure AD**. Du använder sedan **auktoriseringskoden** till att hämta en **åtkomsttoken**.

Inom redirect.aspx.cs anropas [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) för att generera en token.

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
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Hämta en åtkomsttoken från en auktoriseringskod

När **Azure AD** omdirigeras tillbaka till din webbapp med en **auktoriseringskod** kan du använda den till att få en åtkomsttoken. Nedan visas ett C#-exempel som du kan använda på din omdirigeringssida och i händelsen `Page_Load` i default.aspx.

Du kan hämta namnområdet **Microsoft.IdentityModel.Clients.ActiveDirectory** från NuGet-paketet för [Active Directorys autentiseringsbibliotek](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

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

Den här metoden används vanligtvis för appar av ISV-typ där appen äger dataåtkomsten. Användarna är inte nödvändigtvis Power BI-användare och appen styr autentisering och åtkomst för slutanvändarna.

### <a name="access-token-with-a-master-account"></a>Åtkomsttoken med ett huvudkonto

För den här metoden använder du ett enda *huvud*konto som är en Power BI Pro-användare. Autentiseringsuppgifterna för kontot lagras med appen. Appen autentiseras mot Azure AD med de lagrade autentiseringsuppgifterna. Kodexemplet nedan kommer från [exemplet där appen äger data](https://github.com/guyinacube/PowerBI-Developer-Samples)

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

## <a name="troubleshoot"></a>Felsök

Felmeddelande: ”'AuthenticationContext' innehåller inte någon definition för ’AcquireToken’ och det gick inte att hitta någon tillgänglig ’AcquireToken’ som tar emot ett första argument av typen ’AuthenticationContext' (saknar du ett användningsdirektiv eller en sammansättningsreferens?)”.

   Prova att hämta [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) om du ser det här felet.

## <a name="next-steps"></a>Nästa steg

Nu när du har rätt åtkomsttoken kan du anropa Power BI REST API för att bädda in innehåll. Mer information finns i [Så här bäddar du in ditt Power BI-innehåll](embed-sample-for-customers.md#embed-content-within-your-application).

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
