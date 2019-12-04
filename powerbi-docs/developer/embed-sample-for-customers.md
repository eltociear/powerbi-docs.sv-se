---
title: Bädda in innehåll i ett program för dina kunder
description: Lär dig att integrera eller bädda in en rapport, instrumentpanel eller panel i ett program med hjälp av Power BI-API:er för inbäddad analys åt dina kunder. Lär dig hur du integrerar Power BI i ditt program med inbäddad analysprogramvara, inbäddade analysverktyg eller inbäddade business intelligence-verktyg.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 04/02/2019
ms.openlocfilehash: 85b21d95cb992449d3b7a910c619d049237fc9d8
ms.sourcegitcommit: 7f27b9eb0e001034e672050735ab659b834c54a3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74311082"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-customers"></a>Självstudie: Bädda in Power BI-innehåll i ett program för dina kunder

Med **Power BI Embedded i Azure** eller **Power BI-inbäddning i Office** kan du bädda in rapporter, instrumentpaneler och paneler i en app och använda appens egna data. **App äger data** handlar om ett program som använder Power BI som en inbäddad analysplattform. Som **ISV** eller **utvecklare** kan du skapa Power BI-innehåll som visar rapporter, instrumentpaneler eller paneler i ett program som är helt integrerat och interaktivt, utan att användarna behöver någon Power BI-licens. Den här självstudien visar hur du integrerar en rapport i ett program med .NET SDK och JavaScript-API i Power BI.

![Inbäddad Power BI-rapport](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

I de här självstudierna får du lära dig att
> [!div class="checklist"]
> * Registrera ett program i Azure.
> * Bädda in en Power BI-rapport i ett program.

## <a name="prerequisites"></a>Förutsättningar

Du måste ha följande för att komma igång:

* Ett [Power BI Pro-konto](../service-self-service-signup-for-power-bi.md) (ett huvudkonto som är ett användarnamn och lösenord för inloggning på ditt Power BI Pro-konto), eller [tjänstens huvudnamn (appspecifik token)](embed-service-principal.md).
* Du måste ha en egen installation för [Azure Active Directory-klient](create-an-azure-active-directory-tenant.md).

Om du inte har registrerat dig för **Power BI Pro**, [registrerar du dig för en kostnadsfri utvärderingsversion](https://powerbi.microsoft.com/pricing/) innan du börjar.

## <a name="set-up-your-embedded-analytics-development-environment"></a>Konfigurera den inbäddade utvecklingsmiljön för analysverktyg

Innan du börjar bädda in rapporter, en instrumentpanel eller paneler i din app måste du se till att det går att bädda in Power BI i din miljö.

Med [konfigurationsverktyget för inbäddning](https://aka.ms/embedsetup/AppOwnsData) kommer du snabbt igång och kan ladda ned ett exempelprogram som steg för steg beskriver hur du skapar en miljö och bäddar in en rapport.

Om du i stället vill konfigurera miljön manuellt, fortsätter du bara nedan.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrera ett program i Azure Active Directory (Azure AD)

[Registrera appen](register-app.md) med Azure Active Directory så att ditt program får åtkomst till [Power BI REST-API:er](https://docs.microsoft.com/rest/api/power-bi/). Genom att registrera din app kan du upprätta en identitet för din app och ange behörigheter till Power BI REST-resurser. Bestämmer hur du kommer igång med registreringen av en app, beroende på om du vill använda ett huvudkonto eller [tjänstens huvudnamn](embed-service-principal.md).

Påverkar vilken typ app du registrerar i Azure, beroende på vilken metod du väljer.

Om du fortsätter att använda ett huvudkonto fortsätter du med registreringen av en **intern** app. Du använder en intern app eftersom du arbetar ned en icke-interaktiv inloggning.

Men om du fortsätter att använda tjänstens huvudnamn måste du fortsätta med att registrera en **webbapp på serversidan**. Du registrerar en webbapp på serversidan för att skapa en apphemlignet.

## <a name="set-up-your-power-bi-environment"></a>Konfigurera din Power BI-miljö

### <a name="create-a-workspace"></a>Skapa en arbetsyta

Om du bäddar in rapporter, instrumentpaneler eller paneler för dina kunder måste du placera innehållet i en arbetsyta. Det finns olika typer av arbetsytor du kan konfigurera: [traditionella arbetsytor](../service-create-workspaces.md) eller [nya arbetsytor](../service-create-the-new-workspaces.md). Om du använder ett *huvudkonto* spelar det ingen roll vilken typ av arbetsytor du använder. Om du däremot använder *[tjänstens huvudnamn](embed-service-principal.md)* för inloggning i programmet måste du använda de nya arbetsytorna. I båda scenarierna måste både *huvudkontot* och *tjänstens huvudnamn* vara administratör för arbetsytorna som används i programmet.

### <a name="create-and-publish-your-reports"></a>Skapa och publicera rapporter

Du kan skapa rapporter och datauppsättningar som använder Power BI Desktop och publicera dessa rapporter till en arbetsyta. Det finns två sätt att åstadkomma detta: Som slutanvändare kan du publicera rapporter på en traditionell arbetsyta med ett huvudkonto (Power BI Pro-licens). Om du använder tjänstens huvudnamn kan du publicera rapporter på nya arbetsytor med [Power BI REST-API:er](https://docs.microsoft.com/rest/api/power-bi/imports/postimportingroup).

I stegen nedan beskrivs hur du publicerar dina PBIX-rapporter på Power BI-arbetsytan.

1. Ladda ner exemplet [Bloggdemo](https://github.com/Microsoft/powerbi-desktop-samples) från GitHub.

    ![rapportera exempel](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Öppna PBIX-exempelrapporten i **Power BI Desktop**.

   ![PBI-skrivbordsrapport](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publicera på **arbetsytor**. Den här processen skiljer sig beroende på om du använder ett huvudkonto (Power Pro-licens) eller tjänstens huvudnamn. Om du använder ett huvudkonto kan du sedan publicera rapporten via Power BI Desktop.  Om du nu använder tjänstens huvudnamn måste du använda Power BI REST-API:er.

## <a name="embed-content-using-the-sample-application"></a>Bädda in innehåll med exempelprogrammet

Det här exemplet hålls medvetet enkelt i demonstrationssyfte. Det är upp till dig eller dina utvecklare att skydda apphemligheten eller autentiseringsuppgifterna för huvudkontot.

Följ de här stegen nedan om du vill börja bädda in innehåll med hjälp av exempelprogrammet.

1. Ladda ned [Visual Studio](https://www.visualstudio.com/) (version 2013 eller senare). Se till att ladda ned det senaste [NuGet-paketet](https://www.nuget.org/profiles/powerbi).

2. Ladda ner [exempel på app äger data](https://github.com/Microsoft/PowerBI-Developer-Samples) från GitHub för att komma igång.

    ![Exempelprogram för app äger data](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

3. Öppna filen **Web.config** i exempelprogrammet. Du måste fylla i fälten för att kunna köra programmet. Du kan välja **MasterUser** eller **ServicePrincipal** för **AuthenticationType**. Beroende på vilken typ av autentiseringsmetod du väljer finns det olika fält att fylla i.

    > [!Note]
    > Standardinställd **AuthenticationType** i det här exemplet är MasterUser.

    <center>

    | **MasterUser** <br> (Power BI Pro-licens) | **ServicePrincipal** <br> (appspecifik token)|
    |---------------|-------------------|
    | [applicationId](#application-id) | [applicationId](#application-id) |
    | [workspaceId](#workspace-id) | [workspaceId](#workspace-id) |
    | [reportId](#report-id) | [reportId](#report-id) |
    | [pbiUsername](#power-bi-username-and-password) |  |
    | [pbiPassword](#power-bi-username-and-password) |  |
    |  | [applicationsecret](#application-secret) |
    |  | [tenant](#tenant) |

   </center>

    ![Webbkonfigurationsfil](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

### <a name="application-id"></a>Program-ID

Det här attributet behövs för både AuthenticationTypes (huvudkonto och [tjänstens huvudnamn](embed-service-principal.md)).

Fyll i **applicationId** med **program-ID:t** från **Azure**. **applicationId** används av programmet för att identifiera sig för användare som du begär behörighet från.

Så här hämtar du **applicationId**:

1. Logga in på [Azure Portal](https://portal.azure.com).

2. Välj **Alla tjänster** i det vänstra navigeringsfönstret och välj sedan **Appregistreringar**.

    ![Sök efter appregistrering](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Välj det program som behöver **applicationId**.

    ![Att välja App](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

4. Det finns ett **program-ID** som listas som en GUID. Använd detta **program-ID** som **applicationId** för appen.

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

### <a name="workspace-id"></a>ID för arbetsyta

Det här attributet behövs för både AuthenticationTypes (huvudkonto och [tjänstens huvudnamn](embed-service-principal.md)).

Fyll i **workspaceId** med arbetsytans (gruppens) GUID från Power BI. Du kan få den här informationen från URL:en när du är inloggad i Power BI-tjänsten eller med hjälp av Powershell.

URL <br>

![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test"
```

   ![workspaceId från powershell](media/embed-sample-for-customers/embed-sample-for-customers-031-ps.png)

### <a name="report-id"></a>Rapport-ID

Det här attributet behövs för både AuthenticationTypes (huvudkonto och [tjänstens huvudnamn](embed-service-principal.md)).

Fyll i **reportId**-information med rapport-GUID från Power BI. Du kan få den här informationen från URL:en när du är inloggad i Power BI-tjänsten eller med hjälp av Powershell.

URL<br>

![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test" | Get-PowerBIReport
```

![reportId från powershell](media/embed-sample-for-customers/embed-sample-for-customers-032-ps.png)

### <a name="power-bi-username-and-password"></a>Användarnamn och lösenord för Power BI

Dessa attribut behövs bara för huvudkontots AuthenticationType.

Om du använder [tjänstens huvudnamn](embed-service-principal.md) för autentisering behöver du inte fylla i användarnamn- eller lösenordsattributen.

* Fyll i **pbiUsername** med huvudanvändarkontot för Power BI.
* Fyll i **pbiPassword** med lösenordet för huvudkontot för Power BI.

### <a name="application-secret"></a>Apphemlighet

Det här attributet behövs bara för AuthenticationType [tjänstens huvudnamn](embed-service-principal.md).

Fyll i **ApplicationSecret**-uppgifterna från avsnittet **Nycklar** från avsnittet **Appregistreringar** i **Azure**.  Det här attributet fungerar när du använder [tjänstens huvudnamn](embed-service-principal.md).

Hämta **ApplicationSecret** genom att utföra följande steg:

1. Logga in på [Azure-portalen](https://portal.azure.com).

2. Välj **Alla tjänster** i det vänstra navigeringsfönstret och välj sedan **Appregistreringar**.

    ![Sök efter appregistrering](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Välj det program som behöver använda **ApplicationSecret**.

    ![Välj en app](media/embed-sample-for-customers/embed-sample-for-customers-0038.png)

4. Välj **Certifikat och hemligheter** under **Hantera**.

5. Välj **Nya klienthemligheter**.

6. Ange ett namn i rutan **Beskrivning** och välj en varaktighet. Välj sedan **Spara** för att hämta **värdet** för ditt program. När du stänger fönstret **Nycklar** efter att ha sparat nyckelvärdet visas värdefältet bara som dolt. I det här läget kan du inte att hämta nyckelvärdet. Om du tappar bort nyckelvärdet måste du skapa ett nytt på Microsoft Azure-portalen.

    ![Nyckelvärde](media/embed-sample-for-customers/embed-sample-for-customers-042.png)

### <a name="tenant"></a>Klientorganisation

Det här attributet behövs bara för AuthenticationType [tjänstens huvudnamn](embed-service-principal.md).

Fyll i informationen om **klientorganisationen** med ditt Azure-klientorganisations-ID. Du kan få den här informationen från [Azure AD-administratörsportalen](/onedrive/find-your-office-365-tenant-id) när du är inloggad i Power BI-tjänsten eller med hjälp av Powershell.

### <a name="run-the-application"></a>Kör programmet

1. Välj **Kör** i **Visual Studio**.

    ![Kör programmet](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

2. Välj sedan **Bädda in rapport**. Beroende på vilket innehåll du väljer att testa med – rapporter, instrumentpaneler eller paneler – väljer du det alternativet i programmet.

    ![Välj ett innehåll](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

3. Nu kan du visa rapporten i exempelprogrammet.

    ![Visa program](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-content-within-your-application"></a>Bädda in innehåll i programmet

Innehåll kan bäddas in med hjälp av [Power BI REST API:er](https://docs.microsoft.com/rest/api/power-bi/), men exempelkoderna som beskrivs i den här artikeln görs med **.NET SDK**.

Om du vill bädda in för dina kunder i programmet måste du hämta en **åtkomsttoken** för huvudkontot eller [tjänstens huvudnamn](embed-service-principal.md) från **Azure AD**. Du måste hämta en [Azure AD-åtkomsttoken](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) för ditt Power BI-program innan du gör anrop till [Power BI REST API:erna](https://docs.microsoft.com/rest/api/power-bi/).

Skapa Power BI-klienten med din **åtkomsttoken** genom att skapa Power BI-klientobjektet som gör att du kan interagera med [Power BI REST API:er](https://docs.microsoft.com/rest/api/power-bi/). Du skapar Power BI-klientobjektet genom att omsluta **AccessToken** med ett ***Microsoft.Rest.TokenCredentials***-objekt.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Hämta innehållsobjektet som du vill bädda in

Använd Power BI-klientobjektet för att hämta en referens till det objekt du vill bädda in.

Här är ett kodexempel på hur du hämtar den första rapporten från en given arbetsyta.

*Ett exempel på hur du hämtar ett innehållsobjekt, vare sig du vill bädda in en rapport, instrumentpanel eller panel, finns i filen Services\EmbedService.cs i [exempelprogrammet](https://github.com/Microsoft/PowerBI-Developer-Samples).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Skapa inbäddningstoken
Skapa en inbäddningstoken som kan användas från JavaScript-API:et. Det finns två typer av API:er, den första gruppen innehåller fem API:er som alla genererar en inbäddningstoken för ett visst objekt. Den andra gruppen innehåller bara ett API, som genererar en token du kan använda till att bädda in flera objekt.

**API:er för att generera en inbäddningstoken för ett visst objekt**

Den inbäddningstoken du skapar med dessa API:er gäller bara för det objekt du bäddar in. När du bäddar in ett Power BI-objekt (till exempel en rapport, en instrumentpanel eller en panel) med de här API:erna måste du skapa en ny inbäddningstoken för det.
* [Dashboards GenerateTokenInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)
* [Datasets GenerateTokenInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)
* [Reports GenerateTokenForCreateInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)
* [Reports GenerateTokenInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokeningroup)
* [Tiles GenerateTokenInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

Du kan se exempel på hur du skapar en inbäddningstoken för en rapport, instrumentpanel eller panel i följande filer i [exempelprogrammet](https://github.com/Microsoft/PowerBI-Developer-Samples).
* Services\EmbedService.cs
* Models\EmbedConfig.cs
* Models\TileEmbedConfig.cs

Här är ett kodexempel för hur du använder API:et för inbäddningstoken Reports GenerateTokenInGroup.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

**API för att generera en inbäddningstoken för flera objekt**<a id="multiEmbedToken"></a>

API:et [Generate Token](https://docs.microsoft.com/rest/api/power-bi/embedtoken/generatetoken) för inbäddning genererar en token som du kan använda för att bädda in flera objekt.

Du kan även använda den till att dynamiskt välja en datamängd när du bäddar in en rapport. Mer information om hur du använder det här API:et finns i [Dynamisk bindning](embed-dynamic-binding.md).


Här är ett exempel på hur du kan använda API:et.
 
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var reports = new List<GenerateTokenRequestV2Report>()
{ 
    new GenerateTokenRequestV2Report()
    {
        AllowEdit = false,
        Id = report1.Id
    },
    new GenerateTokenRequestV2Report()
    {
        AllowEdit = true,
        Id = report2.Id
    }
};

var datasets= new List<GenerateTokenRequestV2Dataset>()
{
    new GenerateTokenRequestV2Dataset(dataset1.Id),
    new GenerateTokenRequestV2Dataset(dataset2.Id),
    new GenerateTokenRequestV2Dataset(dataset3.Id),
};

var targetWorkspaces = new List<GenerateTokenRequestV2TargetWorkspace>()
{
    new GenerateTokenRequestV2TargetWorkspace(workspace1.Id),
    new GenerateTokenRequestV2TargetWorkspace(workspace2.Id),
};

var request = new GenerateTokenRequestV2()
{
    Datasets = datasetsRequestDetails ?? null,
    Reports = reportsRequestDetails,
    TargetWorkspaces = targetWSRequestdetials ?? null,
};

var token = client.GetClient().EmbedToken.GenerateToken(request);
```

### <a name="load-an-item-using-javascript"></a>Läsa in ett objekt med JavaScript

Du kan använda JavaScript för att läsa in en rapport till olika element på webbsidan.

Du kan använda ett fullständigt exempel i JavaScript API i [Playground-verktyget](https://microsoft.github.io/PowerBI-JavaScript/demo). Playground-verktyget är ett snabbt sätt att leka med olika typer av Power BI Embedded-exempel. Du kan även få mer information om API:et för JavaScript genom att besöka wiki-sidan för [PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

I det här exemplet används en **EmbedConfig**-modell och en **TileEmbedConfig**-modell tillsammans med vyer för en rapport.

*Ett exempel på hur du lägger till en vy för en rapport, instrumentpanel eller panel finns i filerna Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml och Views\Home\Embedtile.cshtml i [exempelprogrammet](#embed-content-using-the-sample-application).*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>Flytta till produktion

Nu när du har utvecklat ditt program är det dags att skapa dedikerad kapacitet för arbetsytan. 

> [!Important]
> Dedikerad kapacitet krävs för att flytta till produktion. Alla arbetsytor (de som innehåller rapporter och instrumentpaneler, och de som innehåller datamängderna) måste tilldelas till en kapacitet.

### <a name="create-a-dedicated-capacity"></a>Skapa en dedikerad kapacitet

Genom att skapa en dedikerad kapacitet kan du dra nytta av att ha en dedikerad resurs för dina kunder. Det finns två typer av kapaciteter att välja mellan:
* **Power BI Premium** – en Office 365-prenumeration för klientorganisationer som finns i två olika SKU-serier, *EM* och *P*. När du bäddar in Power BI-innehåll kallas den här lösningen för *Power BI-inbäddning*. Mer information om den här prenumerationen finns i [Vad är Power BI Premium?](../service-premium-what-is.md)
* **Azure Power BI Embedded** – du kan köpa en dedikerad kapacitet i [Microsoft Azure-portalen](https://portal.azure.com). Den här prenumerationen använder *A*-SKU:er. Mer information om hur du skapar Power BI Embedded-kapacitet finns i [Skapa Power BI Embedded-kapacitet i Azure-portalen](azure-pbie-create-capacity.md).
> [!NOTE]
> Med A-SKU:er kan du inte komma åt Power BI-innehåll med en kostnadsfri Power BI-licens.

I tabellen nedan beskrivs resurser och begränsningar för respektive SKU. När du ska avgöra vilken kapacitet som passar bäst för dina behov kan du använda tabellen [Vilken SKU ska jag köpa till mitt scenario](https://docs.microsoft.com/power-bi/developer/embedded-faq#power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario).

| Kapacitetsnoder | Totalt antal virtuella kärnor | Virtuella kärnor för serverdel | RAM (GB) | Virtuella kärnor för klientdel | DirectQuery/Live Connection (per sek) | Modellens uppdateringsparallellitet |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="development-testing"></a>Utvecklingstestning

Inbäddningstoken med Pro-licenser är avsedda för testning under utveckling, så antalet inbäddningstoken ett Power BI-huvudkonto eller tjänstens huvudnamn kan generera är begränsat. En dedikerad kapacitet krävs för inbäddning i en produktionsmiljö. Det finns ingen gräns för att hur många inbäddningstoken du kan generera med en dedikerad kapacitet. Gå till [Tillgängliga funktioner](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) för att kontrollera användningsvärdet som anger aktuell inbäddad användning i procent. Användningsmängden baseras per huvudkonto.

För mer information, se [White paper om kapacitetsplanering för inbäddad analys](https://aka.ms/pbiewhitepaper).

### <a name="assign-a-workspace-to-a-dedicated-capacity"></a>Tilldela en arbetsyta till en dedikerad kapacitet

När du har skapat en dedikerad kapacitet kan du tilldela arbetsytan till den dedikerade kapaciteten.

Tilldela en dedikerad kapacitet till en arbetsyta med hjälp av [service principal](embed-service-principal.md) genom att använda [Power BI REST-API:et](https://docs.microsoft.com/rest/api/power-bi/capacities/groups_assigntocapacity). När du använder Power BI REST-API:erna ser du till att använda [objekt-ID för tjänstens huvudnamn](embed-service-principal.md#how-to-get-the-service-principal-object-id).

Följ stegen nedan för att tilldela en dedikerad kapacitet till en arbetsyta med hjälp av ett **huvudkonto**.

1. I **Power BI-tjänsten** expanderar du arbetsytorna och väljer ellipsen för arbetsytan som du vill bädda in ditt innehåll med. Välj sedan **Redigera arbetsytor**.

    ![Redigera arbetsyta](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Expandera **Avancerat**, aktivera **Dedikerad kapacitet** och välj den dedikerade kapacitet du skapade. Välj sedan **Spara**.

    ![Tilldela dedikerad kapacitet](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. När du har valt **Spara** ska du se en **romb** bredvid namnet på arbetsytan.

    ![arbetsyta kopplad till en kapacitet](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Nästa steg

I den här självstudien har du lärt dig hur du bäddar in Power BI-innehåll i ett program för dina kunders räkning. Du kan även prova att bädda in Power BI-innehåll för din organisation.

> [!div class="nextstepaction"]
>[Bädda in för din organisation](embed-sample-for-your-organization.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
