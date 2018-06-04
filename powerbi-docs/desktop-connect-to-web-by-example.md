---
title: Extrahera data från en webbsida med exempel i Power BI Desktop (förhandsgranskning)
description: Extrahera data från en webbplats genom att ge ett exempel på vad du vill hämta
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 55c1a70e054b6bb6ff06c7fe6f83b58d8b1f26f3
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34290992"
---
# <a name="get-data-from-a-web-page-by-providing-an-example-preview"></a>Hämta data från en webbplats genom att ge ett exempel (förhandsgranskning)

Hämtning av data från en webbplats låter användare enkelt extrahera data från webbsidor och importera dessa data till **Power BI Desktop**. Många gånger finns data på webbsidor dock inte i välvårdade tabeller som är lätta att extrahera så det kan bli en utmaning att hämta data från sådana sidor, även om de är strukturerade och konsekventa. 

Det finns en lösning. Med funktionen **Hämta data från webben efter exempel**, kan du i princip visa **Power BI Desktop** vilka data som du vill extrahera genom att ge ett eller flera exempel i anslutningsdialogrutan så samlar den in övriga data på sidan som matchar dina exempel. Med den här lösningen kan du extrahera alla typer av data från webbsidor, inklusive data som hittats i tabeller *och* andra icke-tabelldata. 

![Hämta data från webben efter exempel](media/desktop-connect-to-web-by-example/web-by-example_01.png)


## <a name="enabling-the-preview-feature-get-data-from-web-by-example"></a>Aktivera förhandsfunktionen Hämta data från webben efter exempel

**Hämta data från webben efter exempel** är i förhandsversion och måste aktiveras i **Power BI Desktop**. För att aktivera det, väljer du **Arkiv > Alternativ och inställningar > Alternativ > Förhandsfunktioner** och väljer sedan kryssrutan **Ny från webbupplevelse**. Du måste starta om Power BI Desktop när du har gjort valet.

![aktivera förhandsfunktionen](media/desktop-connect-to-web-by-example/web-by-example_02.png)

När förhandsfunktionen är aktiverad, är du redo att börja använda den. 

## <a name="using-get-data-from-web-by-example"></a>Använd Hämta data från webben efter exempel

Om du vill använda **Hämta data från webben efter exempel** väljer du **Hämta data** från menyfliksområdet **Start**. I fönstret som visas väljer du **Övrigt** från kategorier i det vänstra fönstret och väljer sedan **Webb**.

![välj Webb från Hämta data](media/desktop-connect-to-web-by-example/web-by-example_03.png)

Därifrån anger du URL för den webbsida som du vill extrahera data från. I den här artikeln använder vi Microsoft Store-webbplatsen och visar hur den här anslutningsappen fungerar. 

Om du vill följa med, kan du använda den [Microsoft Store-URL](https://www.microsoft.com/en-us/store/top-paid/games/xbox?category=classics) som vi använder i den här artikeln:

    https://www.microsoft.com/en-us/store/top-paid/games/xbox?category=classics

![Webbdialog](media/desktop-connect-to-web-by-example/web-by-example_04.png)

När du väljer **OK**, tas du till dialogrutan **Navigator** där alla automatiskt identifierade tabeller från webbsidan visas. I exemplet i bilden nedan hittades inga tabeller, men det finns en knapp längst ned på sidan som heter **Extrahera tabell med exempel** där du kan ange exempel.


![Navigatorfönstret](media/desktop-connect-to-web-by-example/web-by-example_05.png)

Om du väljer **Extrahera tabell med exempel** så får du upp ett interaktivt fönster där du kan förhandsgranska innehållet på Webbsidor och ange exempelvärden för de data som du vill extrahera. 

I det här exemplet ska vi extrahera *Namn* och *Pris* för varje spel på sidan. Vi kan göra det genom att ange några exempel från sidan för varje kolumn, som visas i följande bild. Allteftersom exemplen skrivs in, kan **Power Query** (som är den underliggande teknik som hämtar data från webbsidan) extrahera data som passar mönstret för exempelposterna med hjälp av algoritmer för smart dataextrahering.

![data efter exempel](media/desktop-connect-to-web-by-example/web-by-example_06.png)

När vi är nöjda med de data som hämtats från webbsidan, väljer vi **OK** för att gå till **Frågeredigeraren**, där vi kan använda fler transformationer eller forma data, till exempel kombinera de med andra data från våra källor.

![data efter exempel](media/desktop-connect-to-web-by-example/web-by-example_07.png)

Därifrån kan du kan skapa visuell information eller på annat sätt använda webbsidans data när du skapar dina **Power BI Desktop**-rapporter.


## <a name="next-steps"></a>Nästa steg
Det finns en mängd olika typer av data du kan ansluta till med **Power BI Desktop**. Kolla in följande resurser för mer information om datakällor:

* [Lägg till kolumn efter exempel](desktop-add-column-from-example.md)
* [Anslut till en webbsida](desktop-connect-to-web.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Anslut till CSV-filer i Power BI Desktop](desktop-connect-csv.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

