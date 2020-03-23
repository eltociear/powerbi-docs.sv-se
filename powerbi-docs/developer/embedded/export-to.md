---
title: Exportera API för Power BI-rapporter
description: Läs om hur du kan exportera en inbäddad Power BI-rapport
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/01/2020
ms.openlocfilehash: eb08eb2ed8ecead4e5a2437cafced6194f05acbe
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79492317"
---
# <a name="export-report-to-file-preview"></a>Exportera rapport till fil (förhandsversion)

Med `exportToFile`-API:et kan du exportera en Power BI-rapport genom att använda ett REST-anrop. Följande filformat stöds:
* **PPTX** (PowerPoint)
* **PDF**
* **PNG**
    * När du exporterar till en PNG komprimeras en rapport med flera sidor till en zip-fil
    * Varje fil i PNG-zipfilen representerar en rapportsida
    * Sidnamnen är desamma som returvärdena för API:erna för[Hämta sidor](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) eller [Hämta sidor i grupp](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Användningsexempel

Du kan använda exportfunktionen på flera olika sätt. Här följer några exempel:

* **Knappen Skicka till utskrift** – Skapa en knapp i ditt program som utlöser ett exportjobb när man klickar på den. Jobbet kan exporteras till den visade rapporten som en PDF- eller PPTX-fil, och när den är klar kan användaren ta emot filen som en nedladdning. Med hjälp av bokmärken kan du exportera rapporten i ett särskilt tillstånd, inklusive konfigurerade filter, utsnitt och ytterligare inställningar. Eftersom API:et är asynkront kan det ta lite tid innan filen är tillgänglig.

* **E-postbilaga** – Skicka automatiska e-postmeddelande i angivna intervall med en bifogad PDF-rapport. Det här scenariot kan vara användbart om du vill automatisera sändningen av en veckorapport till chefer.

## <a name="using-the-api"></a>Använda API:et

Innan du använder API:et måste du verifiera att följande [administratörsklientinställningar](../../service-admin-portal.md#tenant-settings) har aktiverats:
* **Exportera rapporter som PowerPoint-presentationer eller PDF-dokument** – aktiverat som standard.
* **Exportera rapporter som bildfiler** – krävs endast för PNG-filer och är inaktiverat som standard.

API:et är asynkront. När [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile)-API:et anropas utlöser det ett exportjobb. När jobbet har utlösts använder du [avsökning](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) för att spåra jobbet tills det har slutförts.

Under avsökningen returnerar API:et tal som representerar den mängd arbete som har slutförts. Arbetet i exportjobbet beräknas utifrån det antal sidor som rapporten innehåller. Alla sidor har samma vikt. Om du t.ex. exporterar en rapport på 10 sidor, och avsökningen returnerar 70, så innebär det att API:et har bearbetat 7 av exportjobbets 10 sidor.

När exportjobbet har slutförts så returnerar avsökningens API-anrop en [Power BI-URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) för hämtning av filen. URL:en är tillgänglig i 24 timmar.

## <a name="supported-features"></a>Funktioner som stöds

### <a name="selecting-which-pages-to-print"></a>Välja vilka sidor som ska skrivas ut

Ange de sidor som du vill skriva ut enligt returvärdet för [Hämta sidor](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) eller [Hämta sidor i grupp](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup). Du kan också ange ordningen för de sidor som du exporterar.

### <a name="bookmarks"></a>Bokmärken

 Du kan använda `exportToFile` API:et till att programmässigt exportera en rapport i ett särskilt tillstånd, efter att ha tillämpat filter på den. Detta görs med hjälp av [bokmärkes](../../consumer/end-user-bookmarks.md)funktioner. Om du vill exportera en rapport med hjälp av bokmärken så använd [bokmärkets JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 Du kan exempelvis använda bokmärkets `capturedBookmark.state` metod för att fånga de ändringar som en bestämd användare som har gjort i en rapport och sedan exportera den i det aktuella tillståndet.

[Personliga bokmärken](../../consumer/end-user-bookmarks.md#personal-bookmarks) och [beständiga filter](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) stöds inte.

### <a name="authentication"></a>Autentisering

Du kan bara autentisera med en användare (eller huvudanvändare). [Tjänstens huvudnamn](embed-service-principal.md) saknar för närvarande stöd.

### <a name="row-level-security-rls"></a>Säkerhet på radnivå (RLS)

Med [säkerhet på radnivå (RLS)](embedded-row-level-security.md)kan du exportera en rapport som visar data som bara visas för vissa användare. Om du exempelvis exporterar en försäljningsrapport som definieras med regionala roller kan du filtrera rapporten programmässigt så att endast en viss region visas.

Om du vill exportera RLS måste du ha följande behörigheter:
* Skriv-och delningsbehörigheter för den datamängd som rapporten är ansluten till
* Om rapporten finns på en v1-arbetsyta måste du vara arbetsytans administratör
* Om rapporten finns på en v2-arbetsyta måste du vara arbetsytsmedlem eller administratör

### <a name="data-protection"></a>Dataskydd

PDF- och PPTX-formaten stöder [känslighetsetiketter](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi). Om du exporterar en rapport med en känslighetsetikett till en PDF- eller PPTX-fil så visas rapporten med dess känslighetsetikett i den exporterade filen.

### <a name="localization"></a>Lokalisering

När du använder `exportToFile`-API:et kan du skicka din önskade lokala plats. Lokaliseringsinställningarna påverkar hur rapporten visas, t.ex. genom att ändra formateringen enligt vald lokal plats.

## <a name="concurrent-requests"></a>Samtidiga förfrågningar

`exportToFile` stöder begäranden om samtidiga exportjobb. I tabellen nedan visas antalet jobb som du kan köra samtidigt, beroende på vilken SKU som rapporten finns på. Samtidiga begäranden avser rapportsidor. 20 sidor i en exportbegäran förfrågan på en A6-SKU bearbetas t.ex. samtidigt. Det tar ungefär lika lång tid att skicka 20 exportbegäranden med vardera en sida.

Ett jobb som överskrider antalet samtidiga begäranden avslutas inte. Om du exempelvis exporterar tre sidor i en a1-SKU körs det första jobbet, och de två sistnämnda väntar på de två nästföljande körningscyklerna.

|Azure-SKU  |Office-SKU  |Maximalt antal samtidiga rapportsidor  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Begränsningar

* Den rapport som du exporterar måste finnas på en Premium- eller inbäddad kapacitet.
* Datauppsättningen i den rapport som du exporterar måste finnas på en Premium- eller inbäddad kapacitet.
* För den offentliga förhandsversionen är antalet Power BI-rapportsidor som exporteras per timme begränsat till 50 per kapacitet.
* Exporterade rapporter får inte överskrida en filstorlek på 250 MB.
* Känslighetsetiketter stöds inte när du exporterar till PNG.
* [Tjänstens huvudnamn](embed-service-principal.md) stöds inte.
* Det antal sidor som kan ingå i en exporterad rapport är 30. Om rapporten innehåller fler sidor returnerar API:et ett fel och exportjobbet avbryts.
* [Personliga bokmärken](../../consumer/end-user-bookmarks.md#personal-bookmarks) och [beständiga filter](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) stöds inte
* Paginerade rapporter stöds inte för tillfället.
* De visuella Power BI-objekt som listas nedan stöds inte. När en rapport som innehåller dessa visuella objekt exporteras så återges inte de delar av rapporten som innehåller dessa visuella objekt, och en felsymbol visas.
    * Ocertifierade visuella Power BI-objekt
    * R-visualiseringar
    * PowerApps
    * Visuella Python-objekt
    * Visio

## <a name="code-examples"></a>Kodexempel

När du skapar ett exportjobb finns det tre steg att följa:

1. Skickar en exportbegäran.
2. Avsökning.
3. Hämtar filen.

Det här avsnittet tillhandahåller exempel för varje steg.

### <a name="step-1---sending-an-export-request"></a>Steg 1 – skicka en exportbegäran

Det första steget är att skicka en exportbegäran. I det här exemplet skickas en exportbegäran för en specifik sida.

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
        {
            var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
            {
                Settings = new ExportReportSettings
                {
                    Locale = "en-us",
                },

                // Note that page names differ from the page display names.
                // To get the page names use the GetPages API.
                Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
            };

            var exportRequest = new ExportReportRequest
            {
                Format = format,
                PowerBIReportConfiguration = powerBIReportExportConfiguration,
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
        const int c_secToMillisec = 1000;
        do
        {
            if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
            {
                // Error handling for timeout and cancellations
                return null;
            }

            var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            exportStatus = httpMessage.Body;

            // You can track the export progress using the PercentComplete that's part of the response
            SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);

            if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
            {
                // The recommended waiting time between polling requests can be found in the RetryAfter header
                // Note that this header is only populated when the status is either Running or NotStarted
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
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
private readonly IDictionary<string, string> mediaTypeToSuffix = new Dictionary<string, string>
    {
        { "image/png", "png" },
        { "application/zip", "zip" },
        { "application/pdf", "pdf" },
        { "application/vnd.openxmlformats-officedocument.presentationml.presentation", "pptx" },
    };

private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
    {
        if (export.Status == ExportState.Succeeded)
        {
            var httpMessage = await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);
            var mediaType = httpMessage.Response.Content.Headers.ContentType.ToString().ToLower();

            if (!mediaTypeToSuffix.TryGetValue(mediaType, out string fileSuffix))
            {
                // Handle unexpected errors
            }
            else
            {
                return new ExportedFile
                {
                    FileStream = httpMessage.Body,
                    FileSuffix = fileSuffix,
                };
            }
        }

        return null;
    }

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>Exempel på slutpunkt till slutpunkt

Detta är ett exempel på export av en rapport från slutpunkt till slutpunkt. Det här exemplet omfattar följande steg:
1. [Skicka exportbegäran](#step-1---sending-an-export-request).
2. [Avsökning](#step-2---polling).
3. [Hämta filen](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
        {
            try
            {
                var exportId = await PostExportRequest(reportId, groupId, format, pageNames);

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
>[Bädda in för dina kunder](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Bädda in för din organisation](embed-sample-for-your-organization.md)
