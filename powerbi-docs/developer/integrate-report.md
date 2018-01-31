---
title: "Integrera en Power BI-rapport i en app för din organisation"
description: "Lär dig att integrera eller bädda in en rapport i en webbapp med hjälp av Power BI-API:er."
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
ms.date: 10/05/2017
ms.author: maghan
ms.openlocfilehash: 9ed341eb4428795bb4714ae8f1a34fd11c1bcbcd
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="integrate-a-report-into-an-app-for-your-organization"></a>Integrera en rapport i en app för din organisation
Lär dig att integrera eller bädda in en rapport i en webbapp med hjälp av REST API-anrop, tillsammans med Power BI:s JavaScript-API vid inbäddning för din organisation.

![Exempel på inbäddad rapport](media/integrate-report/powerbi-embedded-report.png)

För att komma igång med den här genomgången behöver du ett **Power BI**-konto. Om du inte har ett konto kan du [registrera dig för ett kostnadsfritt Power BI-konto](../service-self-service-signup-for-power-bi.md) eller skapa en egen [Azure Active Directory-klient ](create-an-azure-active-directory-tenant.md) för testning.

> [!NOTE]
> Vill du bädda in en rapport för kunderna genom att i stället använda en embedtoken? Se [Integrera en instrumentpanel, panel eller rapport i programmet åt dina kunder](embed-sample-for-customers.md).
> 
> 

Om du vill integrera en rapport i en webbapp använder du **Power BI** REST-API eller Power BI C# SDK och en Azure Active Directory-**åtkomsttoken** för auktorisering till att hämta en rapport. Sedan kan du läsa in rapporten med samma åtkomsttoken. **Power BI**-API ger programmeringsåtkomst till vissa **Power BI**-resurser. Mer information finns i [Översikt över Power BI REST API](https://msdn.microsoft.com/library/dn877544.aspx) och [Power BI JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Ladda ned exemplet
Artikeln visar den kod som används i [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) på GitHub. Om du vill följa den här genomgången kan du ladda ned exemplet.

## <a name="step-1---register-an-app-in-azure-ad"></a>Steg 1 – Registrera en app i Azure AD
Du måste registrera ditt program med Azure AD för att kunna göra REST API-anrop. Mer information finns i [Registrera en Azure AD-app för att bädda in Power BI-innehåll](register-app.md).

Om du hämtade [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) använder du det **klient-ID** och den **klienthemlighet** som du fick efter registreringen, så att exemplet kan autentisera till Azure AD. Om du vill konfigurera exemplet ändrar du **Klient-ID** och **Klienthemlighet** i filen *cloud.config*.

![](media/integrate-report/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Steg 2 – Hämta en åtkomsttoken från Azure AD
I ditt program måste du först hämta en **åtkomsttoken** från Azure AD innan du kan anropa Power BI REST API:t. Mer information finns i [Autentisera användare och hämta en Azure AD-åtkomsttoken för din Power BI-app](get-azuread-access-token.md).

## <a name="step-3---get-a-report"></a>Steg 3 – Hämta en rapport
Hämta en **Power BI**-rapport genom att använda åtgärden [Hämta rapporter](https://msdn.microsoft.com/library/mt634543.aspx) som hämtar en lista med **Power BI**-rapporter. Du kan hämta ett rapport-ID från listan med rapporter.

### <a name="get-reports-using-an-access-token"></a>Hämta rapporter med hjälp av en åtkomsttoken
Med den **åtkomsttoken** du hämtade i [steg 2](#step-2-get-an-access-token-from-azure-ad) kan du anropa åtgärden [Hämta rapporter](https://msdn.microsoft.com/library/mt634543.aspx). Åtgärden [Hämta rapporter](https://msdn.microsoft.com/library/mt634543.aspx) returnerar en lista med rapporter. Du kan hämta en enda rapport från listan med rapporter. Nedan finns en komplett C#-metod för att hämta en rapport. 

Om du vill göra REST API-anrop måste du inkludera en *auktoriserings*rubrik i formatet *Ägare {åtkomsttoken}*.

#### <a name="get-reports-with-the-rest-api"></a>Hämta rapporter med REST API
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>Hämta rapporter med .NET SDK
Du kan använda .NET SDK för att hämta en lista med rapporter i stället för att anropa REST API direkt.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

## <a name="step-4---load-a-report-using-javascript"></a>Steg 4 – Läs in en rapport med hjälp av JavaScript
Du kan använda JavaScript för att läsa in en rapport till olika element på webbsidan.

**Default.aspx**

```
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

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
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Om du har hämtat och kört [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) ser exemplet ut ungefär som nedan.

![Exempel på inbäddad rapport](media/integrate-report/powerbi-embedded-report.png)

## <a name="working-with-groups-app-workspaces"></a>Arbeta med grupper (apparbetsytor)
Bädda in en rapport från en grupp (apparbetsyta) genom att hämta en lista med alla tillgängliga rapporter i en grupps instrumentpanel med hjälp av följande REST API-anrop. Du hittar mer information om det här REST API-anropet i [Hämta rapporter](https://msdn.microsoft.com/library/mt634543.aspx). Du måste ha behörighet i gruppen för att din begäran ska kunna returnera resultat.

```
https://api.powerbi.com/v1.0/myorg/groups/{group_id}/reports
```

Ovanstående API returnerar listan med tillgängliga rapporter. Varje rapport har en EmbedUrl-egenskap som redan har skapats för inbäddningen av grupper.

```
https://app.powerbi.com/reportEmbed?reportId={report_id}&groupId={group_id}
```

## <a name="next-steps"></a>Nästa steg
Det finns ett exempelprogram på GitHub som du kan granska. Mer information finns i [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app).

Mer information finns tillgänglig för JavaScript-API i [Power BI JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript).

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

