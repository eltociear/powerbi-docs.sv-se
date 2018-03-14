---
title: "Självstudier: Från Excel-arbetsbok till otrolig rapport på nolltid"
description: "Självstudier: Från Excel-arbetsbok till otrolig rapport på nolltid"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Data from files
ms.openlocfilehash: 64872b94d13f30cbab08d67530cc6ae0ccbe8fc3
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/09/2018
---
# <a name="from-excel-workbook-to-stunning-report-in-no-time"></a>Från Excel-arbetsbok till otrolig rapport på nolltid
Chefen vill se en rapport om de senaste försäljningssiffrorna som kombineras med dina intryck från den senaste kampanjen i slutet av dagen. Men den senaste informationen finns i olika tredjepartssystem och i filer på din bärbara dator. Tidigare har det tagit timmar att skapa visuella objekt och bygga upp en rapport. Du börjar känna dig bekymrad.

Inga problem. Med Power BI kan du skapa en fantastisk rapport på nolltid.

I det här exemplet ska vi överföra en Excel-fil från ett lokalt system, skapa en ny rapport och dela den med kollegor – allt från Power BI.

## <a name="prepare-your-data"></a>Förbereda dina data
Låt oss ta en enkel Excel-fil som exempel. Innan du kan läsa in din Excel-fil till Power BI, måste du organisera dina data i en platt tabell. Det innebär att varje kolumn innehåller samma datatyp – exempelvis text, datum, tal eller valuta. Du bör ha en rubrikrad, men det får inte finnas någon kolumn eller rad som visar sammanlagda värden.

![ordnade data i Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

Därefter formaterar du dina data som en tabell. Välj **Formatera som tabell** i gruppen Format på fliken Start i Excel. Välj ett tabellformat för kalkylbladet. Excel-kalkylbladet är nu redo att läsas in till Power BI.

![data formaterade som en tabell](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-into-power-bi"></a>Överföra din Excel-fil till Power BI
Power BI kan ansluta till flera datakällor, inklusive Excel-filer som finns på din dator. Logga in till Power BI för att komma igång. Om du inte har registrerat dig, [kan du göra det gratis](https://powerbi.com).

Du vill skapa en ny instrumentpanel. Öppna **Min arbetsyta** och välj ikonen **+ Skapa**.

![Ikonen Skapa](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

Välj **Instrumentpanel**, ange ett namn och välj **Skapa**. Den nya instrumentpanelen visas – utan data.

![Listrutan Skapa](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

Välj **Hämta data** längst ned till vänster i navigeringsfönstret. På sidan Hämta data, under Importera eller Anslut till Data i rutan Filer, väljer du **Hämta**.

![Hämta data från filer](media/service-from-excel-to-stunning-report/pbi_get_files.png)

Välj **Lokal fil** på sidan Filer. Navigera till Excel-arbetsboksfilen på datorn och väl den för att läsa in den till Power BI. Välj **Importera**.

> **OBS**: Om du vill följa resten av självstudierna använder du [arbetsboken med finansiella exempel](sample-financial-download.md).
> 
> 

![Fönstret Hämta Data > Filer](media/service-from-excel-to-stunning-report/pbi_local_file.png)

## <a name="build-your-report"></a>Bygga upp din rapport
När Power BI har importerat din Excel-fil kan du börja skapa rapporten. När meddelandet **Datauppsättningen är klar** visas, väljer du **Visa datauppsättning**.  Power BI öppnas i redigeringsvyn och visar rapportarbetsytan. På höger sida visas fönstren Visualiseringar, Filter och Fält.

Observera att din Excel-arbetsboks tabelldata visas i fönstret Fält. Under namnet på tabellen visar Power BI kolumnrubrikerna som enskilda fält.

![så ser Excel-data ut i fältfönstret](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

Nu kan du börja skapa visualiseringar. Chefen vill se vinsten över tid. I fönstret Fält drar du **Vinst** till rapportarbetsytan. Power BI visar ett stapeldiagram som standard. Dra därefter **Datum** till rapportarbetsytan. Power BI uppdaterar stapeldiagrammet för att visa vinst per datum.

![stapeldiagram i rapportredigeraren](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

> **Tips**: Kontrollera din aggregeringar om diagrammet ser inte ut som du förväntade dig. Som exempel kan du högerklicka på det fält som du just har lagt till i området **Värde** och se till att dina data aggregeras på det sätt som du önskar.  I det här exemplet använder vi **Summa**.
> 
> 

Chefen vill veta vilka länder som är mest lönsamma. Imponera henne med en kartvisualisering. Välj ett tomt område på arbetsytan och dra fälten **Land** och **Vinst** från Fält-fönstret. Power BI skapar ett visuellt kartobjekt med bubblor som representerar den relativa vinsten för varje plats.

![karta i rapportredigeraren](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

Vad sägs om att visa ett visuell objekt där man kan avläsa försäljning per produkt och marknadssegment? Enkelt. I fönstret Fält markerar du kryssrutorna bredvid fälten Försäljning, Produkt och Segment. Power BI skapar ett stapeldiagram omedelbart. Ändra diagramtypen genom att välja en av ikonerna i menyn Visualiseringar. Ändra till exempel till ett liggande stapeldiagram.  Om du vill sortera diagrammet väljer du ellipserna (...) > **Sortera efter**.

![stående stapeldiagram i rapportredigeraren](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Fäst alla dina visuella objekt på instrumentpanelen. Nu är du redo att dela den med dina kollegor.

![instrumentpanel med 3 fästa visuella objekt](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Dela instrumentpanelen
Nu vill du dela din instrumentpanel med din chef Paula. Du kan dela din instrumentpanel och dess underliggande rapport med alla kollegor som har ett Power BI-konto. De kan interagera med rapporten men inte spara ändringarna.

Om du vill dela din rapport väljer du **Dela** överst på instrumentpanelen.

![Delningsikon](media/service-from-excel-to-stunning-report/power-bi-share.png)

Power BI visar sidan Dela instrumentpanel. Ange e-postadresser till mottagarna i det översta området. Lägg till ett meddelande i fältet nedan. Om du vill att dina medarbetare ska kunna dela instrumentpanelen med andra, väljer du **Tillåt mottagarna att dela din instrumentpanel**. Välj **Dela**.

![Fönstret Dela instrumentpanel](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

Nästa steg

* [Kom igång med Power BI-tjänsten](service-get-started.md)
* [Kom igång med Power BI Desktop](desktop-getting-started.md)
* [Power BI – grundläggande begrepp](service-basic-concepts.md)
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

