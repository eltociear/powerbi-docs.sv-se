---
title: Skapa en datauppsättning
description: Genomgång – Skicka data till en datauppsättning – Skapa en datauppsättning i Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: f0815f3712992b26a69ac60aba6eecae8b60fde4
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216181"
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>Steg 3: Skapa en datauppsättning i Power BI
Den här artikeln ingår i en stegvis genomgång för att [skicka data till en datauppsättning](walkthrough-push-data.md).

I **steg 2** av Skicka data till en datauppsättning [Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md) hämtade du en token för autentisering till **Azure AD**. I det här steget använder du en token för att anropa åtgärden [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets).

För att anropa en REST-resurs kan du använda en webbadress som söker efter resursen och skicka en JSON-sträng (JavaScript Object Notation) som beskriver datauppsättningen till resursen i Power BI-tjänsten. En REST-resurs identifierar en del av Power BI-tjänsten som du vill arbeta med. För att skicka data till datauppsättningen är målresursen en **Datauppsättning**. Den URL som identifierar en datamängd är https://api.PowerBI.com/v1.0/myorg/datasets. Om du sänder data i en grupp, är URL-adressen https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets.

Lägg till den token som du fick i [Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md) i en rubrik för begäran för att autentisera Power BI REST-åtgärden:

När du anropar åtgärden [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) skapas en ny datauppsättning. 

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

Skapa en datauppsättning i Power BI.

## <a name="create-a-dataset-in-power-bi"></a>Skapa en datauppsättning i Power BI
> [!NOTE]
> Innan du börjar kontrollerar du att du har följt de föregående stegen i genomgången för att [skicka data till en datauppsättning](walkthrough-push-data.md).
> 
> 

1. I konsolprogramprojektet som du skapade i steg 2 [Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md) lägger du till **using System.Net;**, och **using System.IO;** i Program.cs.
2. Lägg till koden nedan i Program.cs.
3. Kör konsolappen och logga in på ditt Power BI-konto. Du bör se **Datauppsättningen har skapats** i konsolfönstret. Dessutom kan du logga in till Power BI för att se den nya datauppsättningen.

**Exempel på att skicka data till en datauppsättning**

Lägg till den här koden i Program.cs.

* In static void Main(string[] args):
  
    ```csharp
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Lägg till en CreateDataset()-metod:
  
    ```csharp
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

Nästa steg visar hur du gör för att [få en datauppsättning att lägga till rader i en tabell med Power BI](walkthrough-push-data-get-datasets.md).

Nedan visas den [fullständiga kodlistan](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Fullständig kodlista

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

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


        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion
    }
}
```

[Nästa steg >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>Nästa steg
[Hämta en datauppsättning för att lägga till rader i en Power BI-tabell](walkthrough-push-data-get-datasets.md)  
[Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md)  
[PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)  
[PostDatasetInGroup](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdatasetingroup)  
[Skicka data till en Power BI-instrumentpanel](walkthrough-push-data.md)  
[Översikt över Power BI REST API](overview-of-power-bi-rest-api.md)  
[Power BI REST API-referens](https://docs.microsoft.com/rest/api/power-bi/)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

