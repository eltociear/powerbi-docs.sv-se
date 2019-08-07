---
title: Använd det visuella matrisobjektet i Power BI
description: Läs mer om hur det visuella matrisobjektet möjliggör steglayouter och detaljerade markeringar i Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2f50a6fc9fccc35333257caaf3efeb8185c8caff
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390375"
---
# <a name="use-the-matrix-visual-in-power-bi"></a>Använd det visuella matrisobjektet i Power BI
Det **visuella matrisobjektet** liknar en **tabell**.  En tabell har stöd för två dimensioner och dess data är plana, vilket innebär att dublettvärden visas och inte aggregeras. En matris gör det enklare att visa data på ett meningsfullt sätt med hjälpa av flera dimensioner – och den har stöd för stegvis layout. Matrisen aggregerar data automatiskt och gör det möjligt att öka detaljnivån. 

Du kan skapa visuella matrisobjekt i **Power BI Desktop**- och **Power BI**-rapporter och korsmarkera element i matrisen med andra visuella objekt på rapportsidan. Du kan till exempel välja rader, kolumner och även enskilda celler och korsmarkeringar. Du kan även kopiera enskilda celler och markeringar av flera celler och klistra in dem i andra program. 

![korsmarkerad matris och ringdiagram](media/desktop-matrix-visual/matrix-visual_2a.png)

Det finns många funktioner som är kopplade till matrisen och vi ska gå igenom dem i följande avsnitt i den här artikeln.


## <a name="understanding-how-power-bi-calculates-totals"></a>Beräkning av summor i Power BI

Innan vi går vidare till hur man använder det **visuella matrisobjektet** är det viktigt att du förstår hur Power BI beräknar total- och delsummor i tabeller och matriser. När det gäller summa- och delsummarader utvärderar Power BI måttet för alla rader i underliggande data – det handlar inte bara om att lägga till värdena i de tabellrader som syns eller visas. Detta innebär att du kan få andra värden än vad du räknat med i totalsummaraden.

Ta en titt på följande visuella matrisobjekt. 

![jämför tabeller och matriser](media/desktop-matrix-visual/matrix-visual_3.png)

I det här exemplet visar varje rad i det visuella matrisobjektet längst till höger *Belopp* för varje kombination säljare/datum. Men eftersom en säljare visas för flera datum kan siffrorna visas mer än en gång. Den korrekta totalsumman för underliggande data och en enkel addering av de synliga värdena överensstämmer därmed inte. Detta är ett vanligt mönster när det värde som du summerar finns på ”ett”-sidan i ett ett-till-många-samband.

När du tittar på summor och delsummor, kom ihåg att dessa värden baseras på underliggande data. De är inte bara baserade på de synliga värdena.

<!-- use Nov blog post video

## Expanding and collapsing row headers
There are two ways you can expand row headers. The first is through the right-click menu. You’ll see options to expand the specific row header you clicked on, the entire level or everything down to the very last level of the hierarchy. You have similar options for collapsing row headers as well.

![](media/desktop-matrix-visual/power-bi-expand1.png)

You can also add +/- buttons to the row headers through the formatting pane under the row headers card. By default, the icons will match the formatting of the row header, but you can customize the icons’ color and size separately if you want. 
Once the icons are turned on, they work similarly to the icons from PivotTables in Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

The expansion state of the matrix will save with your report. It can be pinned to dashboards as well, but consumers will need to open up the report to change the state. Conditional formatting will only apply to the inner most visible level of the hierarchy. Note that this expand/collapse experience is not currently supported when connecting to AS servers older than 2016 or MD servers.

![](media/desktop-matrix-visual/power-bi-expand3.png)

Watch the following video to learn more about expand/collapse in the matrix:

-->
## <a name="using-drill-down-with-the-matrix-visual"></a>Öka detaljnivån i det visuella matrisobjektet
Det finns en mängd intressanta aktiviteter som ökar detaljnivån i matrisen som inte var tillgängliga tidigare. Detta inkluderar möjligheten att öka detaljnivån för rader, kolumner och även i enskilda avsnitt och celler. Nu ska vi titta på hur var och en av dessa fungerar.

### <a name="drill-down-on-row-headers"></a>Öka detaljnivån för radrubriker

Gå till fönstret Visualiseringar. När du lägger till flera fält i avsnittet **Rader** i området **Fält** aktiveras ökad detaljnivå för raderna det visuella matrisobjektet. Detta påminner om hur du skapar en hierarki som sedan låter dig öka detaljnivån (och återgå) i hierarkin och analysera data på varje nivå.

I följande bild innehåller avsnittet **Rader** *Försäljningssteg* och *Affärsmöjlighetens storlek* och skapar en gruppering (eller hierarki) i raderna som vi kan visa i större eller mindre detalj.

![Filterkort som visar vilka rader som väljs](media/desktop-matrix-visual/power-bi-rows-matrix.png)

När en gruppering har skapats i avsnittet **Rader** visar det visuella objektet ikonerna *detaljgranska* och *expandera* i det övre vänstra hörnet.

![matris med detaljnivåskontroller markerade](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

På samma sätt som du kan använda funktionerna för att öka detaljnivån och expandera beteendet för andra visuella objekt, kan vi öka detaljnivån i hierarkin (eller återgå) med dessa knappar. I det här fallet kan vi gå från *Försäljningssteg* till *Affärsmöjlighetens storlek*, vilket visas i följande bild där ikonen för att öka detaljnivån en nivå (högaffeln) har valts.

![matris med högaffelns konturer markerade](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Förutom ikonerna kan du välja någon av radrubrikerna och öka detaljnivån genom att välja från menyn som visas.

![menyalternativ för rader i en matris](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Observera att det finns flera alternativ på menyn som visas, vilket genererar olika resultat:

Genom att välja **Granska nedåt** expanderas matrisen för *radnivån*, *exklusive* alla andra radrubriker med undantag för den radrubrik som valdes. I följande bild har **Förslag** > **Granska nedåt** valts. Observera att andra topprader inte längre visas i matrisen. Detta är en mycket användbar funktion och som är särskilt fiffig när det är dags att **korsmarkera** avsnitt.

![matrisen vars detaljnivå har ökats med en nivå](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Välj ikonen **Granska uppåt** för att gå tillbaka till föregående toppnivåsvy. Om du sedan väljer **Förslag** > **Visa nästa nivå** visas en fallande lista över alla objekt på nästa nivå (i det här fallet fältet *Affärsmöjlighetens storlek*) utan kategoriseringen för nästa hierarkinivå.

![matris som använder Visa nästa nivå](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Välj ikonen **Granska uppåt** i det övre vänstra hörnet för att matrisen ska visa alla toppkategorier och välj sedan **Förslag** > **Expandera till nästa nivå** för att visa alla värdena för hierarkins båda nivåer – *Försäljningssteg* och *Affärsmöjlighetens storlek*.

![matris som använder Utvidga nästa nivå](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

Du kan också använda menyalternativet **Expandera** för att styra visningen ytterligare.  Välj exempelvis **Förslag** > **Expandera** > **Val**. Power BI visar en fullständig rad för varje *Försäljningssteg* och alla alternativen för *Affärsmöjlighetens storlek* för *Förslag*.

![Matrisen efter att Expandera har tillämpats på Förslag](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Öka detaljnivån för kolumnrubriker
På samma sätt som du kan öka detaljnivån för rader kan du göra samma med **Kolumner**. I följande bild finns det två fält i fältet **Kolumner** som skapar en hierarki som liknar den som vi använde för raderna tidigare i den här artikeln. I fältområdet **Kolumner** hittar vi *Region* och *Segment*. Så snart som det andra fältet lades till i **Kolumner**, visades en ny listrutemeny på det visuella objektet som för närvarande visar **Rader**.

![Matrisen efter att det andra kolumnvärdet har lagts till](media/desktop-matrix-visual/power-bi-matrix-row.png)

Om du vill öka detaljnivån för kolumner, väljer du **Kolumner** i menyn *Fortsätt granska* som finns i det övre vänstra hörnet av matrisen. Välj den *östra* regionen och välj **Granska nedåt**.

![meny för ökad detaljnivå för kolumner](media/desktop-matrix-visual/power-bi-matrix-column.png)

När du väljer **Granska nedåt** visas nästa nivå i kolumnhierarkin för *Region > Östra*, vilket i detta fall är *Antal affärsmöjligheter*. Den andra regionen visas, men är nedtonad.

![matris med ökning av detaljnivån en nivå för kolumn](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

Resten av alternativen i menyn fungerar för kolumner på samma sätt som de gör för rader (se föregående avsnitt **Öka detaljnivån för radrubriker**). Du kan **Visa nästa nivå**, **Expandera till nästa nivå** med kolumner på samma sätt som rader.

> [!NOTE]
> Ikonerna för att öka och minska detaljnivån längst upp till vänster på matrisen gäller endast för rader. Du måste använda högerklicksmenyn för att öka detaljnivån i kolumner.

## <a name="stepped-layout-with-matrix-visuals"></a>Stegvis layout med matriser

**Visuella matrisobjekt** har automatiskt indrag för underkategorier i en hierarki under en överordnad kategori. Detta kallas **stegvis layout**.

I den ursprungliga versionen av det visuella matrisobjektet visades underkategorier i en helt annan kolumn och tog upp mer utrymme i det visuella objektet. Följande bild visar tabellen i den ursprungliga **matrisen**. Observera underkategorierna i en separat kolumn.

![Skärmbild av det gamla visuella matrisobjektet som visar underkategorierna i en separat kolumn.](media/desktop-matrix-visual/matrix-visual_14.png)

I följande bild visas en **Matris** med **Stegvis layout**. Lägg märke till kategorin *datorer* visar underkategorierna något indragna (tillbehör för datorer, stationära datorer, bärbara datorer, skärmar och så vidare) vilket är tydligare och mycket mer komprimerat.

![matrisens aktuella metod för att formatera data](media/desktop-matrix-visual/matrix-visual_13.png)

Du kan enkelt ändra inställningarna för stegvis layout. Expandera området **radrubriker** i **format**-området (rollerikonen) i fönstret **Visuella objekt** för den valda **matrisen**. Du har två alternativ: knappen **Stegvis layout** (som aktiverar eller inaktiverar funktionen) och **stegvis layoutindrag** (anger indrag i bildpunkter).

![Radrubrikskort med stegvis layoutkontroll](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Om du inaktiverar **Stegvis layout**, visar Power BI underkategorierna i en annan kolumn istället för att visas indragna under den överordnade kategorin.

## <a name="subtotals-with-matrix-visuals"></a>Delsummor med matriser

Du kan aktivera eller inaktivera delsummor i matriser, för såväl rader som kolumner. På den följande bilden kan du se att raddelsummorna är inställda på **På**.

![matris som visar summor och delsummor](media/desktop-matrix-visual/matrix-visual_20.png)

I avsnittet **Format** i fönstret **Visualiseringar** expanderar du kortet **Delsummor** och sätter skjutreglaget **Raddelsummor** till **Inaktivera**. När du gör det visas inte delsummorna.

![matris med delsummor inaktiverade](media/desktop-matrix-visual/matrix-visual_21.png)

Samma sak gäller för kolumndelsummor.

## <a name="cross-highlighting-with-matrix-visuals"></a>Korsmarkering med matriser

Med visualiseringen **Matris** kan du välja alla element i matrisen som grund för korsmarkering. Välj en kolumn i en **matris** så markerar Power BI kolumnen, precis som alla andra visuella objekt på rapportsidan. Den här typen av korsmarkering har varit en vanlig funktion för andra visuella objekt och val av datapunkter, så nu har det visuella objektet **Matris** samma funktion.

Dessutom fungerar Ctrl + klicka för korsmarkering. I följande bild valdes till exempel en samling av underkategorier från **matrisen**. Observera hur objekt som inte var markerat från det visuella objektet är nedtonade och hur övriga visuella objekt på sidan återspeglar de val du gjorde i **matrisen**.

![Skärmbild av det visuella matrisobjektet tillsammans med två andra visuella objekt som visar funktionen Ctrl + klicka för korsmarkering.](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Kopiera värdena från Power BI så att du kan använda dem i andra program

Din matris eller tabell kan ha innehåll som du vill använda i andra program: Dynamics CRM, Excel och andra Power BI-rapporter. Genom att högerklicka i Power BI kan du kopiera en cell eller ett cellurval till Urklipp. Sedan kan du klistra in dem i det andra programmet.



* Om du vill kopiera en enskild cells värde markerar du cellen, högerklickar och väljer **Kopiera värde**. Med det oformaterade cellvärdet i Urklipp kan du nu klistra in det i ett annat program.

    ![Skärmbild av det visuella matrisobjektet med en pil som pekar på ett värde och högerklicksmenyn expanderad med alternativen Kopiera värde och Kopiera markering framhävda.](media/desktop-matrix-visual/power-bi-cell-copy.png)



* Om du vill kopiera mer än en enskild cell markerar du ett cellområde eller markerar en eller flera celler med hjälp av CTRL. 

    ![Skärmbild av det visuella matrisobjektet med en pil som pekar från tre framhävda värden till högerklicksmenyn som är expanderad med alternativen Kopiera värde och Kopiera markering framhävda.](media/desktop-matrix-visual/power-bi-copy.png)

* Kopian inkluderar kolumn- och radrubrikerna.

    ![Skärmbild som visar Excel-rader och -kolumner med värdena inklistrade.](media/desktop-matrix-visual/power-bi-copy-selection.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Fyllning och teckenfärger med matriser
Med det visuella matrisobjektet kan du använda **villkorsstyrd formatering** (färger, fyllning och datastaplar) för cellernas bakgrundsfärger samt på själva texten och värdena.

Om du vill tillämpa villkorsstyrd formatering, väljer du det visuella matrisobjektet och öppnar fönstret **Format**. Expandera kortet **Villkorsstyrd formatering** och flytta skjutreglaget till **På** för antingen **Bakgrundsfärg**, **Teckenfärg** eller **Datastaplar**. När du aktiverar något av dessa alternativ visas en länk till *Avancerade kontroller*, där du kan anpassa färger och värden för formatering av färg.
  
  ![Formatfönster som visar datastapelskontroll](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Välj *Avancerade kontroller* för att visa en dialogruta där du kan göra justeringar. Det här exemplet visar dialogrutan för **Datastaplar**.

![Datastapelsfönster](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Nästa steg

[Punktdiagram och bubbeldiagram i Power BI](power-bi-visualization-scatter.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)