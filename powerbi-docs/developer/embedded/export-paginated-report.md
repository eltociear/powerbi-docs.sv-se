---
title: Exportera API för Power BI-rapporter
description: Läs om hur du kan exportera en inbäddad sidnumrerad Power BI-rapport
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: ed3193e586dc05fe92d9c429584080ac80d86a17
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237163"
---
# <a name="export-paginated-report-to-file-preview"></a>Exportera sidnumrerad rapport till fil (förhandsversion)

Med API:et `exportToFile` kan du exportera en sidnumrerad Power BI-rapport genom att använda ett REST-anrop. Följande filformat stöds:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Bild**
    * När du exporterar till en bild ställer du in bildformatet med inställningen `OutputFormat`
    * Du kan använda följande värden för OutputFormat: .bmp, .emf, .gif, .jpeg, .png och .tiff (standard)

## <a name="usage-examples"></a>Användningsexempel

Du kan använda exportfunktionen på flera olika sätt. Här följer några exempel:

* **Knappen Skicka till utskrift** – Skapa en knapp i ditt program som utlöser ett exportjobb när man klickar på den. Jobbet kan exportera den visade rapporten som en .pdf- eller en .pptx-fil, och efteråt kan användaren få filen som en nedladdning. Med hjälp av rapportparametrar och formatinställningar kan du exportera rapporten i ett visst tillstånd, inklusive filtrerade data, anpassade sidstorlekar och andra formatinställningar. Eftersom API:et är asynkront kan det ta lite tid innan filen är tillgänglig.

* **E-postbilaga** – Skicka automatiskt regelbundna e-postmeddelanden med en .pdf-rapport som bilaga. Det här scenariot kan vara användbart om du vill automatisera sändningen av en veckorapport till chefer.

## <a name="using-the-api"></a>Använda API:et

API:et är asynkront. När [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile)-API:et anropas utlöser det ett exportjobb. När jobbet har utlösts använder du [avsökning](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) för att spåra jobbet tills det har slutförts.

När exportjobbet har slutförts så returnerar avsökningens API-anrop en [Power BI-URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) för hämtning av filen. URL:en är tillgänglig i 24 timmar.

## <a name="supported-features"></a>Funktioner som stöds

### <a name="format-settings"></a>Formatinställningar

Ange olika formatinställningar för varje filformat. De egenskaper och värden som stöds motsvarar [parametrarna för enhetsinformation](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) för adressparametrar för sidnumrerade rapporter.

Här följer två exempel, ett för att exportera de första fyra sidorna i en rapport med rapportsidans storlek till en .pptx-fil och ett annat för att exportera den tredje sidan i en rapport till en .jpeg-fil.

**Exportera de första fyra sidorna till en .pptx-fil**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Exportera den tredje sidan till en .jpeg-fil**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Rapportparametrar

Du kan använda API:et `exportToFile` till att programmatiskt exportera en rapport med en uppsättning rapportparametrar. Detta görs med hjälp av funktionerna för [rapportparametrar](../../paginated-reports/paginated-reports-parameters.md).

Här följer ett exempel på hur du anger värden för rapportparametrar.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Autentisering

Du kan bara autentisera med en användare (eller huvudanvändare) eller ett [huvudnamn för tjänsten](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Säkerhet på radnivå (RLS)

När du använder en Power BI-datamängd med säkerhet på radnivå (RLS) som definierats som en datakälla kan du exportera en rapport som visar data som bara visas för vissa användare. Om du exempelvis exporterar en försäljningsrapport som definieras med regionala roller kan du filtrera rapporten programmässigt så att endast en viss region visas.

Om du vill exportera med RLS måste du ha läsbehörighet för Power BI-datamängden som används som datakälla för rapporten.

Här är ett exempel på hur du anger ett giltigt användarnamn för RLS.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Kodexempel

Du kan ladda ned det Power BI API SDK som används i kodexemplen [här](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

När du skapar ett exportjobb finns det tre steg att följa:

1. Skickar en exportbegäran.
2. Avsökning.
3. Hämtar filen.

Det här avsnittet tillhandahåller exempel för varje steg.

### <a name="step-1---sending-an-export-request"></a>Steg 1 – skicka en exportbegäran

Det första steget är att skicka en exportbegäran. I det här exemplet skickas en exportbegäran för ett specifikt sidintervall, en specifik storlek och specifika värden på rapportparametrarna.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Step 2 – avsökning

Efter det att du har skickat en exportbegäran, så använd avsökning för att fastställa när den exportfil som du väntar på är klar.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Steg 3 – hämta filen

När avsökningen har returnerat en URL, så kan du använda det här exempelt när du ska hämta den mottagna filen.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Exempel på slutpunkt till slutpunkt

Detta är ett exempel på export av en rapport från slutpunkt till slutpunkt. Det här exemplet omfattar följande steg:
1. [Skicka exportbegäran](#step-1---sending-an-export-request).
2. [Avsökning](#step-2---polling).
3. [Hämta filen](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Nästa steg

Granska hur du kan bädda in innehållet för dina kunder och din organisation:

> [!div class="nextstepaction"]
>[Exportera rapport till fil](export-to.md)

> [!div class="nextstepaction"]
>[Bädda in för dina kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Bädda in för din organisation](embed-sample-for-your-organization.md)