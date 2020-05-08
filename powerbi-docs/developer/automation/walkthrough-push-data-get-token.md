---
title: Hämta en autentiseringsåtkomsttoken
description: Genomgång för att push-överföra data – hämta en åtkomsttoken för autentisering
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488279"
---
# <a name="step-2-get-an-authentication-access-token"></a>Steg 2: hämta en åtkomsttoken för autentisering

Den här artikeln är det andra steget i serien [Push-överföra data till en Power BI-datamängd](walkthrough-push-data.md).

I steg 1 [registrerade du en klientapp i Azure AD](../embedded/register-app.md). I det här steget, hämtar du en åtkomsttoken för autentisering. Power BI-appar är integrerade i Azure Active Directory så att appen ska få säker inloggning och auktorisering. Appen använder en token för autentisering med Azure AD och för att få åtkomst till Power BI-resurser.

## <a name="get-an-authentication-access-token"></a>Hämta en autentiseringsåtkomsttoken

Innan du börjar ska du kontrollera att du har utfört [föregående steg](../embedded/register-app.md) i serien [Push-överföra data till en Power BI-datamängd](walkthrough-push-data.md). 

För den här proceduren behöver du Visual Studio 2015 eller senare.

1. Skapa ett nytt C#-projekt med ett **Konsolprogram** i Visual Studio.

2. Installera [Azure AD-autentiseringsbiblioteket för .NET NuGet-paket](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). .NET-appen behöver det här paketet för att få en säkerhetstoken för autentisering. 

     a. Välj **Verktyg** > **NuGet-pakethanteraren** > **Pakethanterarkonsolen**.

     b. Skriv **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. Lägg till `using Microsoft.IdentityModel.Clients.ActiveDirectory;` i Program.cs.

3. Lägg till exempelkoden nedan i Program.cs.

4. Ersätt ”{ClientID}” med det **klient-ID** du fick i den [föregående artikeln](../embedded/register-app.md) när du registrerade appen.

5. Kör konsolappen och logga in på ditt Power BI-konto. 

   Du bör se en tokensträng i konsolfönstret.

**Exempelkod för att hämta säkerhetstoken för autentisering**

Lägg till den här koden i Program {...}.

* En tokenvariabel för att anropa åtgärder: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* In static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Lägg till en GetToken()-metod:

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

När du får en autentiseringstoken, kan du anropa valfri Power BI-åtgärd.

I nästa artikel i serien ska du [skapa en datamängd i Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Slutföra kodlistning

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Nästa steg

* Nästa artikel i den här serien är [Skapa en datamängd i Power BI](walkthrough-push-data-create-dataset.md)
* [Översikt över Power BI REST API](overview-of-power-bi-rest-api.md)  
* [REST API:er för Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)