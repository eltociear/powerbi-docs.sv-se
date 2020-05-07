---
title: Från Excel-arbetsbok till fantastisk rapport i Power BI-tjänsten
description: Den här artikeln visar hur du snabbt kan skapa en fantastisk rapport från en Excel-arbetsbok.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: c2a4719a03e37569e40d4247939a9f2c73379e52
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872518"
---
# <a name="from-excel-workbook-to-stunning-report-in-the-power-bi-service"></a>Från Excel-arbetsbok till fantastisk rapport i Power BI-tjänsten
Chefen vill se en rapport om de senaste försäljningssiffrorna som kombineras med dina intryck från den senaste kampanjen i slutet av dagen. Men senaste data finns i olika tredjepartssystem och i filer på din bärbara dator. Tidigare har det tagit timmar att skapa visuella objekt och formatera en rapport, och du börjar bli nervös.

Inga problem. Med Power BI kan du skapa en fantastisk rapport på nolltid.

I det här exemplet laddar vi upp en Excel-fil från ett lokalt system, skapar en ny rapport och delar den med kollegor – allt från Power BI.

## <a name="prepare-your-data"></a>Förbereda dina data
Låt oss ta en enkel Excel-fil som exempel. 

1. Innan du kan läsa in din Excel-fil till Power BI, måste du organisera dina data i en platt tabell. I en platt tabell innehåller varje kolumn samma datatyp, till exempel text, datum, tal eller valuta. Tabellen ska ha en rubrikrad men inga kolumner eller rader som visar summor.

   ![Ordnade data i Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

2. Därefter formaterar du dina data som en tabell. I Excel går du till fliken **Start** och gruppen **Format**. Välj **Formatera som tabell**. 

3. Välj ett tabellformat för kalkylbladet. 

   Excel-kalkylbladet är nu redo att läsas in till Power BI.

   ![Data formaterade som en tabell](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-to-the-power-bi-service"></a>Ladda upp din Excel-fil till Power BI-tjänsten
Power BI-tjänsten kan ansluta till flera datakällor, däribland Excel-filer som finns på din dator. 

 > [!NOTE] 
 > Om du vill följa resten av självstudierna använder du [arbetsboken med finansiella exempel](sample-financial-download.md).

1. Kom igång genom att logga in på Power BI-tjänsten. Om du inte har registrerat dig, [kan du göra det gratis](https://powerbi.com).

2. Du vill skapa en ny instrumentpanel. Öppna **Min arbetsyta** och välj ikonen **Skapa**.

   ![Ikonen Skapa](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

3. Välj **Instrumentpanel**, ange ett namn och välj sedan **Skapa**. 

   Den nya instrumentpanelen visas utan data.

   ![Listrutan Skapa](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

4. Välj **Hämta data** längst ned i navigeringsfönstret. 

5. På sidan **Hämta data** går du till rutan **Filer** under **Skapa nytt innehåll** och väljer **Hämta**.

   ![Hämta data från filer](media/service-from-excel-to-stunning-report/pbi_get_files.png)

6. På sidan **Filer** väljer du **Lokal fil**. Gå till Excel-arbetsboksfilen på datorn och väl **Öppna** för att läsa in den till Power BI-tjänsten. 

   ![Fönstret Hämta Data > Filer](media/service-from-excel-to-stunning-report/pbi_local_file.png)

7. På sidan **Lokal fil** väljer du **Importera**.


## <a name="build-your-report"></a>Bygga upp din rapport
När Power BI-tjänsten har importerat Excel-filen börjar du skapa rapporten. 

1. När meddelandet **Datauppsättningen är klar** visas, väljer du **Visa datauppsättning**.  

   Power BI öppnas i redigeringsvyn och visar rapportarbetsytan. På höger sida visas fönstren **Visualiseringar**, **Filter** och **Fält**. Observera att din Excel-arbetsboks tabelldata visas i fönstret **Fält**. Under namnet på tabellen visar Power BI kolumnrubrikerna som enskilda fält.

   ![Så ser Excel-data ut i fönstret Fält](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

2. Nu kan du börja skapa visualiseringar. Anta att chefen vill se vinsten över tid. I fönstret **Fält** drar du **Vinst** till rapportarbetsytan. 

   Som standard visar Power BI ett stapeldiagram. 

3. Dra **Datum** till rapportarbetsytan. 

   Power BI uppdaterar stapeldiagrammet för att visa vinst per datum.

   ![Stapeldiagram i rapportredigeraren](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

   > [!TIP]
   > Kontrollera dina aggregeringar om diagrammet ser inte ut som du förväntar dig. Till exempel kan du i källan **Värde** högerklicka på det fält som du just lade till och kontrollera att data aggregeras på det sätt du vill. I det här exemplet använder vi **Summa**.
   > 

Chefen vill veta vilka länder som är mest lönsamma. Imponera på dem med en kartvisualisering. 

1. Välj ett tomt område på rapportarbetsytan. 

2. Från fönstret **Fält** drar du fälten **Land** och **Vinst** till rapportarbetsytan.

   Power BI skapar ett visuellt kartobjekt med bubblor som representerar den relativa vinsten för varje plats.

   ![Visuellt kartobjekt i rapportredigeraren](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

Vad sägs om att visa ett visuell objekt där man kan avläsa försäljning per produkt och marknadssegment? Enkelt. 

1. I fönstret **Fält** markerar du fälten **Försäljning**, **Produkt** och **Segment**. 
   
   Power BI skapar ett stapeldiagram omedelbart. 

2. Ändra diagramtypen genom att välja en av ikonerna i menyn **Visualiseringar**. Ändra till exempel till ett **stående stapeldiagram**. 

3. Om du vill sortera diagrammet väljer du **Fler alternativ** (…) > **Sortera efter**.

   ![Stående stapeldiagram i rapportredigeraren](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Fäst alla dina visuella objekt på instrumentpanelen. Nu är du redo att dela den med dina kollegor.

   ![Instrumentpanel med tre fästa visuella objekt](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Dela instrumentpanelen
Anta att du vill dela din instrumentpanel med din chef. Du kan dela din instrumentpanel och dess underliggande rapport med alla kollegor som har ett Power BI-konto. De kan interagera med rapporten men kan inte spara ändringar.

1. Om du vill dela din rapport väljer du **Dela** överst på instrumentpanelen.

   ![Delningsikon](media/service-from-excel-to-stunning-report/power-bi-share.png)

   Power BI visar sidan **Dela instrumentpanel**. 

2. Ange mottagarnas e-postadresser i rutan **Ange e-postadresser** och lägg till ett meddelande i rutan under den. 

3. Om du vill att dina medarbetare ska kunna dela instrumentpanelen med andra, väljer du **Tillåt mottagarna att dela din instrumentpanel**. Välj **Dela**.

   ![Fönstret Dela instrumentpanel](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

## <a name="next-steps"></a>Nästa steg

* [Komma igång med Power BI-tjänsten](service-get-started.md)
* [Kom igång med Power BI Desktop](desktop-getting-started.md)
* [Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)

Fler frågor? [Testa Power BI Community](https://community.powerbi.com/).

