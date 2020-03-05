---
title: Använda sidnumrerade rapporter i Power BI
description: Vägledning för när du ska använda sidnumrerade rapporter i Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 3838c0b487be7faace2e58dd706aa7d172841215
ms.sourcegitcommit: b59ec11a4a0a3d5be2e4d91548d637d31b3491f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290508"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Använda sidnumrerade rapporter i Power BI

Den här artikeln är avsedd för rapportförfattare som skapar rapporter för Power BI. Den innehåller förslag som hjälper dig att välja när du ska utveckla [sidnumrerade Power BI-rapporter](../paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> Du måste ha en Power BI Premium-prenumeration när du ska publicera sidnumrerade Power BI-rapporter. Rapporterna återges bara när de ligger på en arbetsyta i en dedikerad kapacitet som har [arbetsbelastningen Sidnumrerade rapporter aktiverad](../service-admin-premium-workloads.md#paginated-reports).

Sidnumrerade Power BI-rapporter är optimerade för **utskrift** eller **PDF-generering**. De gör även att du kan skapa mycket formaterade, bildpunktsperfekta layouter. Sidnumrerade rapporter passar därför särskilt bra för driftsrapporter som försäljningsfakturor.

Power BI-rapporter är å andra sidan optimerade för **utforskning och interaktivitet**. De kan också presentera dina data med hjälp av en stor mängd moderna visuella objekt. Power BI-rapporter passar därför särskilt bra till analysrapporter där rapportanvändarna kan utforska data och identifiera relationer och mönster.

Vi rekommenderar att du använder en sidnumrerad Power BI-rapport i följande fall:

- Du vet att rapporten ska skrivas ut eller matas in som ett PDF-dokument.
- Rutnätslayouter kan expandera och spilla över. Tänk på att en tabell eller matris i en Power BI-rapport inte kan ändra storlek dynamiskt så att alla data visas, utan visar rullningslister i stället. Om den skrivs ut går det dock inte att rulla för att visa data utanför visningsfältet.
- Sidnumrerade Power BI-rapporter har funktioner som är till hjälp. Vi går igenom några sådana scenarier längre fram i artikeln.

## <a name="legacy-reports"></a>Äldre rapporter

Om du redan har [RDL-rapporter (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) i SSRS (SQL Server Reporting Services) kan du välja att utveckla om dem som [Power BI-rapporter](../consumer/end-user-reports.md), eller så kan du migrera dem som sidnumrerade rapporter till Power BI. Läs mer i [Migrera SQL Server Reporting Services-rapporter till Power BI](migrate-ssrs-reports-to-power-bi.md).

När du har publicerat sidnumrerade rapporter på en Power BI-arbetsyta är de tillgängliga på samma sätt som Power BI-rapporter. Du kan enkelt distribueras dem via [Power BI-appar](../service-create-distribute-apps.md).

Du kan överväga att utveckla om SSRS-rapporter i stället för att migrera dem. Det gäller särskilt rapporter som är avsedda för analys. I sådana fall kan du förmodligen ge användarna en bättre upplevelse med hjälp av Power BI-rapporter.

## <a name="paginated-report-scenarios"></a>Scenarier för sidnumrerade rapporter

Det finns många scenarier där du med fördel kan använda sidnumrerade Power BI-rapporter. Det är många funktioner som inte stöds i Power BI-rapporter.

- **Redo för utskrift**: Sidnumrerade rapporter är optimerade för utskrift eller PDF-generering. Om det behövs kan du expandera dataområden och spilla över till flera sidor på ett kontrollerat sätt. Du kan definiera marginaler, sidhuvuden och sidfötter i dina rapportlayouter.
- **Återgivningsformat**: Power BI kan återge sidnumrerade rapporter i olika format. Några exempel är Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML och MHTML. (Formatet MHTML används till att återge rapporter i Power BI-tjänsten.) Dina rapportanvändare kan välja att exportera i det format som passar dem.
- **Noggrann layout**: Du kan skapa mycket formaterade, bildpunktsperfekta layouter och definiera storlek och plats ned till bråkdelar av tum eller centimeter.
- **Dynamisk layout**: Du kan skapa följsamma layouter genom att ange VB.NET-uttryck för många rapportegenskaper. Uttrycken har åtkomst till många kärnbibliotek i .NET Framework.
- **Återgivningsspecifik layout**: Du kan använda uttryck för att ändra rapportens layout baserat på vilket återgivningsformat som används. Du kan till exempel inaktivera växling av synlighet (för att öka eller minska detaljnivån) när rapporten återges i ett icke-interaktivt format som PDF.
- **Interna frågor**: Du behöver inte först utveckla någon Power BI-datamängd. Du kan skriva interna frågor (eller använda lagrade procedurer) för [alla datakällor som stöds](../paginated-reports-data-sources.md). Frågor kan innehålla parametrisering.
- **Grafiska frågedesigners**: Power BI Report Builder innehåller grafiska designverktyg som hjälper dig att skriva och testa dina frågor mot datamängden.
- **Statiska datamängder**: Du kan definiera en datamängd och ange data direkt i rapportdefinitionen. Den här funktionen är särskilt användbar när du ska hålla en demonstration eller visa upp ett koncepttest (POC).
- **Dataintegrering**: Du kan kombinera data från olika datakällor eller statiska datamängder. Det gör du genom att skapa anpassade fält med hjälp av VB.NET-uttryck.
- **Parametrisering**: Du kan skapa mycket anpassade parametriseringar, bland annat med datadrivna och sammanhängande parametrar. Du kan också definiera standardvärden för parametrar. De här funktionerna kan hjälpa rapportanvändarna att snabbt ställa in lämpliga filter. Parametrarna behöver inte heller filtrera rapportdata. De kan användas till ”Vad händer”-scenarier, dynamisk filtrering eller formatering.
- **Bilddata**: Rapporten kan återge bilder när de lagras i binärt format i en datakälla.
- **Anpassad kod**: Du kan utveckla kodblock med VB.NET-funktioner i rapporten och använda dem i alla rapportuttryck.
- **Underrapporter**: Du kan bädda in andra sidnumrerade Power BI-rapporter (från samma arbetsyta) i rapporten.
- **Flexibla datarutnät**: Du har detaljerad kontroll över rutnätslayouter med hjälp av tablix-dataområden. De har även stöd för komplexa layouter som kapslade och intilliggande grupper. Du kan konfigureras dem för upprepade rubriker vid utskrift över flera sidor. Dessutom kan du bädda in underrapporter eller andra visualiseringar som datastaplar, miniatyrdiagram och indikatorer.
- **Rumsliga datatyper**: Du kan visualisera [rumsliga SQL Server-datatyper](/sql/relational-databases/spatial/spatial-data-sql-server) i kartdataområden. Du kan alltså använda datatyperna GEOGRAPHY och GEOMETRY till att visualisera punkter, linjer och polygoner. Du kan även visualisera polygoner som är definierade i ESRI-formfiler.
- **Moderna mätare**: Du kan visa KPI-värden och status med radiella och linjära mätare. Du kan till och med bädda in dem i rutnätsområden och upprepa dem inom grupper.
- **HTML-återgivning**: Du kan visa formaterad text när den lagras som HTML.
- **Koppla dokument**: Du kan använda platshållare för textrutor och mata in datavärden i text. På så sätt kan du skapa en dokumentkopplingsrapport.
- **Funktioner för interaktivitet**: Interaktiva funktioner kan vara att växla synlighet (för att öka eller minska detaljnivån), länkar, interaktiv sortering och knappbeskrivningar. Du kan också lägga till länkar som leder till Power BI-rapporter eller andra sidnumrerade Power BI-rapporter. Länkar kan även leda till andra en annan plats i samma rapport.
- **Prenumerationer**: Power BI kan leverera sidnumrerade rapporter som e-postmeddelanden enligt ett schema, där rapporterna kan vara bilagor i alla format som stöds.
- **Användarbaserad layout**: Du kan skapa följsamma rapportlayouter som anpassar sig till den autentiserade användare som öppnar rapporten. Du kan utforma rapporten för att filtrera data på olika sätt, dölja dataområden eller visualiseringar, använda olika format eller ange standardvärden för användardefinierade parametrar.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Vad är sidnumrerade rapporter i Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Migrera SQL Server Reporting Services-rapporter till Power BI](migrate-ssrs-reports-to-power-bi.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
