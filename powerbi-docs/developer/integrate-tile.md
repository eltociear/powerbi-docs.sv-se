---
title: "Integrera en Power BI-panel i en app för din organisation"
description: "Genomgång för hur du integrerar en panel i en app, exempelkod"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/13/2018
ms.author: maghan
ms.openlocfilehash: c4c1b9223554491968a541c9d6b698a9655eded5
ms.sourcegitcommit: 2ceea44d3606c15b57142c37649c9d481ec4becc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/15/2018
---
# <a name="integrate-a-tile-into-an-app-user-owns-data"></a>Integrera en panel i en app (användaren äger data)
Lär dig att integrera eller bädda in en panel i en webbapp med hjälp av REST API-anrop, tillsammans med Power BI JavaScript-API vid inbäddning för din organisation.

![Inbäddad panel i ett webbprogram](media/integrate-tile/powerbi-embedded-tile.png)

För att komma igång med den här genomgången behöver du ett **Power BI**-konto. Om du inte har ett konto kan du [registrera dig för ett kostnadsfritt Power BI-konto](../service-self-service-signup-for-power-bi.md) eller skapa en egen [Azure Active Directory-klient ](create-an-azure-active-directory-tenant.md) för testning.

> [!NOTE]
> Vill du bädda in en panel för kunderna genom att i stället använda en embedtoken? Se [Integrera en instrumentpanel, panel eller rapport i programmet åt dina kunder](embed-sample-for-customers.md).
> 
> 

Om du vill integrera en panel i en webbapp använder du **åtkomsttoken** **Power BI** REST API eller Power BI C# SDK och en Azure Active Directory (AD)-auktorisering för att hämta en panel. Sedan läser du in panelen med samma åtkomsttoken. **Power BI**-API ger programmeringsåtkomst till vissa **Power BI**-resurser. Mer information finns i [Översikt över Power BI REST API](https://msdn.microsoft.com/library/dn877544.aspx) och [Power BI JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Ladda ned exemplet
Artikeln visar den kod som användes i [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) på GitHub. Om du vill följa den här genomgången kan du ladda ned exemplet.

## <a name="step-1---register-an-app-in-azure-ad"></a>Steg 1 – Registrera en app i Azure AD
Du måste registrera ditt program med Azure AD för att kunna göra REST API-anrop. Mer information finns i [Registrera en Azure AD-app för att bädda in Power BI-innehåll](register-app.md).

Om du har hämtat [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) använder du det **Klient-ID** och den **Klienthemlighet** som du får efter registreringen så att exemplet kan autentisera till Azure AD. Om du vill konfigurera exemplet ändrar du **Klient-ID** och **Klienthemlighet** i filen *cloud.config*.

![](media/integrate-tile/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Steg 2 – Hämta en åtkomsttoken från Azure AD
I ditt program måste du först hämta en **åtkomsttoken** från Azure AD innan du kan anropa Power BI REST API:t. Mer information finns i [Autentisera användare och hämta en Azure AD-åtkomsttoken för din Power BI-app](get-azuread-access-token.md).

## <a name="step-3---get-a-tile"></a>Steg 3 – Hämta en panel
Om du vill hämta en **Power BI**-panel använder du åtgärden [Hämta paneler](https://msdn.microsoft.com/library/mt465741.aspx) som hämtar en lista med **Power BI**-paneler från en angiven instrumentpanel. Från panellistan kan du hämta ett panel-ID och en inbäddad URL.

Du måste hämta ett instrumentpanels-ID först innan du kan hämta panelen. Information om hur du hämtar en instrumentpanel finns i [Integrera en instrumentpanel i en app (användaren äger data)](integrate-dashboard.md).

### <a name="get-tiles-using-an-access-token"></a>Hämta paneler med hjälp av en åtkomsttoken
Med den **åtkomsttoken** som du hämtade i [steg 2](#step-2-get-an-access-token-from-azure-ad) kan du anropa åtgärden [Hämta paneler](https://msdn.microsoft.com/library/mt465741.aspx). Åtgärden [Hämta paneler](https://msdn.microsoft.com/library/mt465741.aspx) returnerar en lista med paneler. Du kan hämta en enda panel från listan med paneler. Nedan finns en komplett C#-metod för att hämta en panel. 

Om du vill göra REST API-anrop måste du inkludera en *auktoriserings*rubrik i formatet *Ägare {åtkomsttoken}*.

#### <a name="get-tiles-with-the-rest-api"></a>Hämta paneler med REST API
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a tile from a dashboard. In this sample, you get the first tile.
protected void GetTile(string dashboardId, int index)
{
    //Configure tiles request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}Dashboards/{1}/Tiles",
        baseUri,
        dashboardId)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get tiles response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBITiles tiles = JsonConvert.DeserializeObject<PBITiles>(reader.ReadToEnd());

            //Sample assumes at least one Dashboard with one Tile.
            //You could write an app that lists all tiles in a dashboard
            if (tiles.value.Length > 0)
                tileEmbedUrl.Text = tiles.value[index].embedUrl;
        }
    }
}

//Power BI Tiles used to deserialize the Get Tiles response.
public class PBITiles
{
    public PBITile[] value { get; set; }
}
public class PBITile
{
    public string id { get; set; }
    public string title { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-tiles-using-the-net-sdk"></a>Hämta paneler med .NET SDK
Du kan använda .NET SDK för att hämta en lista med instrumentpaneler i stället för att anropa REST API direkt.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get a list of dashboards your "My Workspace"
    ODataResponseListDashboard tiles = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    // Get the first tile from the above dashbaord
    ODataResponseListTile tiles = client.Dashboards.GetTiles(dashboard.Id);

    Tile tile = tiles.Value.FirstOrDefault();
}
```

## <a name="step-4---load-a-tile-using-javascript"></a>Steg 4 – Läs in en panel med hjälp av JavaScript
Du kan använda JavaScript för att läsa in en panel till olika element på webbsidan.

**Default.aspx**

```
<!-- Embed Tile-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a tile</div>

            <div>Enter an embed url for a tile from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedTileAction" value="Embed Tile" />
        </div>

        <div id="tileContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected tile.
    var el = document.getElementById("bEmbedTileAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedTile, false);
    } else {
        el.attachEvent('onclick', updateEmbedTile);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded tile if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedTile();
    }
};

// update embed tile
function updateEmbedTile() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the tile.
    var tileContainer = document.getElementById('tileContainer');

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);

    // tile.on will add an event handler which prints to Log window.
    tile.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Om du har hämtat och kört [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) ser exemplet ut ungefär som nedan.

![Inbäddad panel i ett webbprogram](media/integrate-tile/powerbi-embedded-tile.png)

## <a name="working-with-groups-app-workspaces"></a>Arbeta med grupper (apparbetsytor)
Om du ska bädda in en panel från en grupp (apparbetsyta), hämtar du en lista med alla tillgängliga paneler i en grupps instrumentpanel med hjälp av följande REST API-anrop. Du hittar mer information om det här REST API-anropet i [Hämta paneler](https://msdn.microsoft.com/library/mt465741.aspx). Du måste ha behörighet i gruppen för att din begäran ska kunna returnera resultat.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards/{dashboard_id}/tiles
```

Ovanstående API returnerar listan med tillgängliga paneler. Varje panel har en EmbedUrl-egenskap som redan har skapats för inbäddning av grupper.

```
https://app.powerbi.com/embed?dashboardId={dashboard_id}&tileId={tile_id}&groupId={group_id}
```

## <a name="next-steps"></a>Nästa steg
Wiki om att [bädda in en panel](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Tile-Embed) i Power BI med JavaScript

[Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript).

Exempel på [webbapp för panelintegrering](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) på GitHub.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

