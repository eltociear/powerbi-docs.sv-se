---
title: Integrera en instrumentpanel i en app för din organisation
description: Lär dig att integrera eller bädda in en instrumentpanel i en webbapp med hjälp av Power BI-API:er.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: maghan
ms.openlocfilehash: 979b76350b9867bbc684a70bd89a82f88993e625
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="integrate-a-dashboard-into-an-app-for-your-organization"></a>Integrera en instrumentpanel i en app för din organisation
Lär dig att integrera eller bädda in en instrumentpanel i en webbapp med hjälp av REST API-anrop, tillsammans med Power BI JavaScript-API vid inbäddning för din organisation.

![Inbäddad instrumentpanel](media/integrate-dashboard/powerbi-embed-dashboard.png)

För att komma igång med den här genomgången behöver du ett **Power BI**-konto. Om du inte har ett konto kan du [registrera dig för ett kostnadsfritt Power BI-konto](../service-self-service-signup-for-power-bi.md) eller skapa en egen [Azure Active Directory-klient ](create-an-azure-active-directory-tenant.md) för testning.

> [!NOTE]
> Vill du bädda in en instrumentpanel för kunderna genom att i stället använda en embedtoken? Se [Integrera en instrumentpanel, panel eller rapport i programmet åt dina kunder](embed-sample-for-customers.md).
> 
> 

Om du vill integrera en instrumentpanel i en webbapp använder du åtkomsttoken **Power BI** REST API eller Power BI C# SDK och en Azure Active Directory (AD)-auktorisering**åtkomsttoken** för att hämta en instrumentpanel. Sedan läser du in instrumentpanelen med samma åtkomsttoken. **Power BI**-API ger programmeringsåtkomst till vissa **Power BI**-resurser. Mer information finns i [Översikt över Power BI REST API](https://msdn.microsoft.com/library/dn877544.aspx) och [Power BI JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Ladda ned exemplet
Artikeln visar den kod som användes i [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) på GitHub. Om du vill följa den här genomgången kan du ladda ned exemplet.

## <a name="step-1---register-an-app-in-azure-ad"></a>Steg 1 – Registrera en app i Azure AD
Du måste registrera ditt program med Azure AD för att kunna göra REST API-anrop. Mer information finns i [Registrera en Azure AD-app för att bädda in Power BI-innehåll](register-app.md).

Om du har hämtat [Integrera en exempelinstrumentpanel](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) använder du det **Klient-ID** och den **Klienthemlighet** som du får efter registreringen så att exemplet kan autentisera till Azure AD. Om du vill konfigurera exemplet ändrar du **Klient-ID** och **Klienthemlighet** i filen *cloud.config*.

![](media/integrate-dashboard/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Steg 2 – Hämta en åtkomsttoken från Azure AD
I ditt program måste du först hämta en **åtkomsttoken** från Azure AD innan du kan anropa Power BI REST API:t. Mer information finns i [Autentisera användare och hämta en Azure AD-åtkomsttoken för din Power BI-app](get-azuread-access-token.md).

## <a name="step-3---get-a-dashboard"></a>Steg 3 – hämta en instrumentpanel
Hämta en **Power BI**-instrumentpanel genom att använda åtgärden [Hämta instrumentpaneler](https://msdn.microsoft.com/library/mt465739.aspx) som hämtar en lista med **Power BI**-instrumentpaneler. Du kan hämta ett instrumentpanel-id i listan över instrumentpaneler.

![](media/integrate-dashboard/powerbi-embed-dashboard-get-dashboards.png)

### <a name="get-dashboards-using-an-access-token"></a>Hämta instrumentpaneler med hjälp av en åtkomsttoken
Med den **åtkomsttoken** som du hämtade i [steg 2](#step-2-get-an-access-token-from-azure-ad) kan du anropa åtgärden [Hämta instrumentpaneler](https://msdn.microsoft.com/library/mt465739.aspx). Åtgärden [Hämta instrumentpaneler](https://msdn.microsoft.com/library/mt465739.aspx) returnerar en lista över instrumentpaneler. Du kan hämta en enda instrumentpanel från listan över instrumentpaneler. Nedan finns en komplett C#-metod för att hämta en instrumentpanel. 

Om du vill göra REST API-anrop måste du inkludera en *auktoriserings*rubrik i formatet *Ägare {åtkomsttoken}*.

#### <a name="get-dashboards-with-the-rest-api"></a>Hämta instrumentpaneler med REST API
**Default.aspx.cs**

```
protected void getDashboardsButton_Click(object sender, EventArgs e)
{
    string responseContent = string.Empty;

    //Configure dashboards request
    System.Net.WebRequest request = System.Net.WebRequest.Create(String.Format("{0}dashboards", baseUri)) as System.Net.HttpWebRequest;
    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", authResult.AccessToken));

    //Get dashboards response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            responseContent = reader.ReadToEnd();

            //Deserialize JSON string
            PBIDashboards PBIDashboards = JsonConvert.DeserializeObject<PBIDashboards>(responseContent);

            if (PBIDashboards != null)
            {
                var gridViewDashboards = PBIDashboards.value.Select(dashboard => new {
                    Id = dashboard.id,
                    DisplayName = dashboard.displayName,
                    EmbedUrl = dashboard.embedUrl
                });

                this.GridView1.DataSource = gridViewDashboards;
                this.GridView1.DataBind();
            }
        }
    }
}

//Power BI Dashboards used to deserialize the Get Dashboards response.
public class PBIDashboards
{
    public PBIDashboard[] value { get; set; }
}
public class PBIDashboard
{
    public string id { get; set; }
    public string displayName { get; set; }
    public string embedUrl { get; set; }
    public bool isReadOnly { get; set; }
}
```

#### <a name="get-dashboards-using-the-net-sdk"></a>Hämta instrumentpaneler med .NET SDK
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
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    var embedUrl = dashboard.EmbedUrl
}
```

## <a name="step-4---load-a-dashboard-using-javascript"></a>Steg 4 – Läs in en instrumentpanel med hjälp av JavaScript
Du kan använda JavaScript för att läsa in en instrumentpanel till olika element på webbsidan.

**Default.aspx**

```
<!-- Embed Dashboard-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a dashboard</div>

            <div>Enter an embed url for a dashboard from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedDashboardAction" value="Embed Dashboard" />
        </div>

        <div id="dashboardContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected dashboard.
    var el = document.getElementById("bEmbedDashboardAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedDashboard, false);
    } else {
        el.attachEvent('onclick', updateEmbedDashboard);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded dashboard if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedDashboard();
    }
};

// update embed dashboard
function updateEmbedDashboard() {

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
        type: 'dashboard',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the dashboard.
    var dashboardContainer = document.getElementById('dashboardContainer');

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("tileClicked", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Om du har hämtat och kört [Integrera en exempelinstrumentpanel](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) ser exemplet ut ungefär som nedan.

![](media/integrate-dashboard/powerbi-embed-dashboard.png)

## <a name="tile-clicked-events"></a>Panelklickade händelser
I exemplet ovan såg du kanske att du kan hantera händelser när användaren klickar på ikonen på instrumentpanelen. Mer information om händelser finns [Hantera händelser i JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

```
// dashboard.on will add an event handler which prints to Log window.
dashboard.on("tileClicked", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});

// dashboard.on will add an event handler which prints to Log window.
dashboard.on("error", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Error<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});
```

Om du har hämtat och kört [Integrera ett exempel på en instrumentpanel](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/PowerBI.com%20Integrate/integrate-dashboard-web-app) kommer text att skapas under instrumentpanelen när du klickar på en panel. Texten bör se ut ungefär så här. Därmed kan du logga en panel har klickats och sedan vidarebefordra användaren till lämplig plats.

```
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "", "navigationUrl": "https://app.powerbi.com/dashboards/fcff76f9-15ff-4a8e-8242-275ac9c25b90/qna?q=count%20of%20new%20hires%20from%20July%202014%20to%20December%202014", "tileId": "0e99b45c-9b53-4920-b239-cee7d37d2369" }
---------
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "https://app.powerbi.com/reportEmbed?reportId=ab199308-80b1-4626-9823-43a84623bd9c", "navigationUrl": "https://app.powerbi.com/reports/ab199308-80b1-4626-9823-43a84623bd9c/ReportSection1", "tileId": "ffc30447-674a-4511-944f-79e182d719de", "pageName": "ReportSection1" }
---------
```

## <a name="working-with-groups-app-workspaces"></a>Arbeta med grupper (apparbetsytor)
Om du ska bädda in en instrumentpanel från en grupp (apparbetsyta), hämtar du en lista med alla tillgängliga instrumentpaneler i en grupp med hjälp av följande REST API-anrop. Du hittar mer information om det här REST API-anropet i [Hämta instrumentpaneler](https://msdn.microsoft.com/library/mt465739.aspx). Du måste ha behörighet i gruppen för att din begäran ska kunna returnera resultat.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards
```

Ovanstående API returnerar listan med tillgängliga instrumentpaneler. Varje instrumentpanel har en EmbedUrl-egenskap som redan har skapats för inbäddning av grupper.

```
https://app.powerbi.com/dashboardEmbed?dashboardId={dashboardId}&groupId={groupId}
```

## <a name="limitations"></a>Begränsningar
* De användare som har åtkomst till inbäddade instrumentpaneler måste ha ett Power BI-konto och åtkomst till instrumentpanelen. Antingen äger de instrumentpanelen eller också har instrumentpanelen delats med användaren.
* Frågor och svar stöds för närvarande inte i inbäddade instrumentpaneler.
* Som en tillfällig begränsning måste användaren först komma åt instrumentpaneler i PowerBI.com när du delar en dem med säkerhetsgrupper innan de kan se dem inbäddade.

## <a name="next-steps"></a>Nästa steg
Det finns ett exempelprogram på GitHub som du kan granska. Ovanstående exempel baseras på det exemplet. Mer information finns i [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app).

Mer information finns tillgänglig för JavaScript-API i [Power BI JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript).

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

