---
title: Använd det visuella matrisobjektet i Power BI
description: Läs mer om hur visuella matrisobjekt möjliggör steglayouter och detaljerad markering i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ad8900e5a95148b3f8333aa1953cc939d56f0e6
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375510"
---
# <a name="use-the-matrix-visual-in-power-bi"></a>Använd det visuella matrisobjektet i Power BI
Den **matris** visual liknar en **tabell**.  En tabell har stöd för 2 dimensioner och data är fast, betydelse duplicerade värden visas och inte samman. En matris gör det enklare att visa data meningsfullt över flera dimensioner – den har stöd för stegvis layout. Matrisen sammanställer data automatiskt och kan gå nedåt. 

Du kan skapa matriser i **Power BI Desktop** och **Power BI-tjänsten** rapporter och markera flera element i matrisen med andra visuella objekt på den rapportsidan. Till exempel kan du välja rader, kolumner och även enskilda celler och korsmarkeringar. Dessutom kan enskilda celler och flera cellmarkeringar kopieras och klistras in i andra program. 

![flera markerade matris och ringdiagram](media/desktop-matrix-visual/matrix-visual_2a.png)

Det finns många funktioner som är kopplade till matrisen och vi ska gå igenom dem i följande avsnitt i den här artikeln.


## <a name="understanding-how-power-bi-calculates-totals"></a>Beräkning av summor i Power BI

Innan vi går vidare till hur man använder det visuella **matris**objektet är det viktigt att du förstår hur Power BI beräknar total- och delsummor i tabeller och matriser. När det gäller summa- och delsummarader utvärderas måttet för alla rader i underliggande data – det handlar *inte* bara om att lägga till värdena i de tabellrader som syns eller visas. Detta innebär att du kan få andra värden än vad du räknat med i totalsummaraden. 

Ta en titt på följande matriser. 

![Jämför tabeller och matriser](media/desktop-matrix-visual/matrix-visual_3.png)

I det här exemplet visar varje rad i matrisen längst till höger i *belopp* för varje kombination säljare/datum. Men eftersom en säljare visas för flera datum kan siffrorna visas mer än en gång. Den korrekta totalsumman för underliggande data och en enkel addering av de synliga värdena överensstämmer därmed inte. Detta är ett vanligt mönster när det värde som du summerar finns på ”ett”-sidan i ett ett-till-många-samband.

Tänk på att dessa värden, när du arbetar med total- och delsummor, baseras på underliggande data och inte enbart på de värden som visas. 

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
## <a name="using-drill-down-with-the-matrix-visual"></a>Med hjälp av gå nedåt i matris
Du kan göra alla typer av intressanta detaljnivå aktiviteter som inte var tillgängliga tidigare i matris. Detta inkluderar möjligheten att öka detaljnivån för rader, kolumner och även i enskilda avsnitt och celler. Nu ska vi titta på hur var och en av dessa fungerar.

### <a name="drill-down-on-row-headers"></a>Öka detaljnivån för radrubriker
Gå till fönstret **Visualiseringar**. När du lägger till flera fält i avsnittet **Rader** i brunnen **Fält** aktiveras granskning nedåt på raderna i matrisen. Detta påminner om hur du skapar en hierarki som sedan låter dig öka detaljnivån (och återgå) i hierarkin och analysera data på varje nivå.

I följande bild, den **rader** innehåller *försäljningssteg* och *affärsmöjlighetsstorlek*, skapa en gruppering (eller hierarki) i de rader som vi kan visa detaljerad information.

![Filter-kort som visar vilka rader väljs](media/desktop-matrix-visual/power-bi-rows-matrix.png)

När en gruppering har skapats i avsnittet **Rader** visar det visuella objektet ikonerna *detaljgranska* och *expandera* i det övre vänstra hörnet.

![matris med ökad detaljnivå kontroller som beskrivs](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

På samma sätt som du kan använda funktionerna för att öka detaljnivån och expandera beteendet för andra visuella objekt, kan vi öka detaljnivån i hierarkin (eller återgå) med dessa knappar. I det här fallet vi gå från *försäljningssteg* till *affärsmöjlighetsstorlek*, enligt följande bild, där gå nedåt en nivå ikon (högaffeln) har valts.

![matris med högaffeln beskrivs](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Förutom dessa ikoner kan du välja någon av dessa radrubriker och öka detaljnivån genom att välja från menyn som visas.

![menyalternativen för rader i en matris](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Observera att det finns flera alternativ på menyn som visas, vilket genererar olika resultat:

Att välja **detaljnivån** expanderas matrisen för *som* radnivån, *exklusive* alla andra radrubriker förutom radrubriken som har valts. I följande bild, **förslag** > **detaljnivån** har valts. Observera att andra topprader inte längre visas i matrisen. Detta är en mycket användbar funktion och som är särskilt fiffig när det är dags att **korsmarkera** avsnitt.

![matrisen Detaljgranskning nedåt en nivå](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Välj den **detaljnivån** ikon för att gå tillbaka till föregående toppnivån. Om du sedan väljer **förslag** > **Visa nästa nivå**, får du en stigande lista över alla objekt på nästa nivå (i det här fallet den *affärsmöjlighetsstorlek* fältet), utan kategoriseringen hierarkinivå.

![matris med hjälp av Visa nästa nivå](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Välj den **detaljnivån** ikonen i det övre vänstra hörnet av matrisen visas alla toppkategorier, sedan väljer **förslag** > **Expandera till nästa nivå**till Visa alla värden för båda nivåerna av hierarkin - *försäljningssteg* och *affärsmöjlighetsstorlek*.

![matris med hjälp av Visa nästa nivå](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

Du kan också använda den **Expandera** menyalternativet att styra visningen ytterligare.  Välj exempelvis **förslag** > **Expandera** > **val av**. Powerbi visar en totala raden för varje *försäljningssteg* och alla de *affärsmöjlighetsstorlek* alternativ för *förslag*.

![Matrisen efter Expandera som tillämpas på förslag](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Öka detaljnivån för kolumnrubriker
Liknar möjlighet att öka detaljnivån för rader, du kan också öka detaljnivån på **kolumner**. I följande bild, det finns två fält i den **kolumner** fältbrunnen, skapar en hierarki som liknar den som vi använder för rader tidigare i den här artikeln. I den **kolumner** fältbrunnen, har vi *Region* och *Segment*. När andra fält har lagts till i **kolumner**, en ny listruta som visas på det visuella objektet, för närvarande visas **rader**.

![Matrisen efter den andra kolumnvärde har lagts till](media/desktop-matrix-visual/power-bi-matrix-row.png)

Om du vill öka detaljnivån för kolumner, Välj **kolumner** från den *detaljgranska i* meny som finns i det övre vänstra hörnet av matrisen. Välj den *östra* region och välj **detaljnivån**.

![menyn för ökad detaljnivå för kolumner](media/desktop-matrix-visual/power-bi-matrix-column.png)

När du väljer **detaljnivån**, nästa nivå i hierarkin för kolumnen *Region > östra* visas, som i det här fallet är *Antal affärsmöjligheter*. Den andra regionen visas, men är nedtonat.

![matrisen med kolumner Granska nedåt en nivå](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

Resten av menyobjekt som fungerar för kolumner på samma sätt som de gör för rader (se avsnittet ovan **öka detaljnivån för radrubriker**). Du kan **Visa nästa nivå** och **Expandera till nästa nivå** med kolumner som är precis som du kan göra med rader.

> [!NOTE]
> Ikonerna för att öka och minska detaljnivån längst upp till vänster på matrisen gäller endast för rader. Du måste använda högerklicksmenyn för att öka detaljnivån i kolumner.
> 
> 

## <a name="stepped-layout-with-matrix-visuals"></a>Stegvis layout med matriser
**Matriser** har automatiskt indrag för underkategorier i en hierarki när de visas under en överordnad kategori. Detta kallas **Stegvis layout**.

I den *ursprungliga* versionen av matrisen visades underkategorier i en helt annan kolumn och tog upp mer utrymme i det visuella objektet. Följande bild visar tabellen i den ursprungliga **matrisen**. Observera underkategorierna i en separat kolumn.

![gamla sätt att standardformat för matriser](media/desktop-matrix-visual/matrix-visual_14.png)

I följande bild visas en **Matris** med **Stegvis layout**. Lägg märke till kategorin *datorer* visar underkategorierna något indragna (tillbehör för datorer, stationära datorer, bärbara datorer, skärmar och så vidare) vilket är tydligare och mycket mer komprimerat.

![aktuella vägen som matris formaterar data](media/desktop-matrix-visual/matrix-visual_13.png)

Du kan enkelt ändra inställningarna för stegvis layout. Expandera området **radrubriker** i **format**-området (rollerikonen) i fönstret **Visuella objekt** för den valda **matrisen**. Du har två alternativ: knappen **Stegvis layout** (som aktiverar eller inaktiverar funktionen) och **stegvis layoutindrag** (anger indrag i bildpunkter).

![Radrubriker kortkontroll med stegvis layout](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Om du inaktiverar **stegvis layout** visas underkategorierna har i en annan kolumn snarare än under överordnad kategori.

## <a name="subtotals-with-matrix-visuals"></a>Delsummor med matriser
Du kan aktivera eller inaktivera delsummor i matriser, för såväl rader som kolumner. I följande bild ser du att raddelsummor är inställda på **På**.

![matris som visar summor och delsummor](media/desktop-matrix-visual/matrix-visual_20.png)

I avsnittet **Format** i fönstret **Visualiseringar** expanderar du kortet **Delsummor** och sätter skjutreglaget **Raddelsummor** till **Inaktivera**. När du gör det visas inte delsummor.

![matris med delsummor stängs av](media/desktop-matrix-visual/matrix-visual_21.png)

Samma sak gäller för kolumndelsummor.

## <a name="cross-highlighting-with-matrix-visuals"></a>Korsmarkering med matriser
Med visualiseringen **Matris** kan du välja alla element i matrisen som grund för korsmarkering. Markera en kolumn i en **matris** för att markera den och alla andra visuella objekt på rapportsidan. Den här typen av korsmarkering har varit en vanlig funktion för andra visuella objekt och val av datapunkter, så nu har det visuella objektet **Matris** samma funktion.

Dessutom fungerar Ctrl + klicka för korsmarkering. I följande bild valdes till exempel en samling av underkategorier från **matrisen**. Observera hur objekt som inte var markerat från det visuella objektet är nedtonade och hur övriga visuella objekt på sidan återspeglar de val du gjorde i **matrisen**.

![rapporten sidan mellan highighted genom en matris](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Kopiera värdena från Power BI så att du kan använda dem i andra program

Din matris eller en tabell kan ha innehåll som du vill använda i andra program som Dynamics CRM eller Excel eller t.o.m. i andra Power BI-rapporter. Genom att högerklicka i Power BI kan du kopiera en cell eller ett cellurval till Urklipp och klistra in informationen i det andra programmet.

![kopieringsalternativ](media/desktop-matrix-visual/power-bi-cell-copy.png)

* Om du vill kopiera en enskild cells värde markerar du cellen, högerklickar och väljer **Kopiera värde**. Med det oformaterade cellvärdet i Urklipp kan du nu klistra in det i ett annat program.

    ![kopieringsalternativ](media/desktop-matrix-visual/power-bi-copy.png)

* Om du vill kopiera mer än en enskild cell markerar du ett cellområde eller markerar en eller flera celler med hjälp av CTRL. Kopian inkluderar kolumn- och radrubrikerna.

    ![klistra in i Excel](media/desktop-matrix-visual/power-bi-copy-selection.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Fyllning och teckenfärger med matriser
Du kan använda i matris **villkorsstyrd formatering** (färger och fyllning och data) för cellernas bakgrundsfärger och du kan använda villkorsstyrd formatering för de själva texten och värdena.

Om du vill tillämpa villkorsstyrd formatering, Välj matrisen visual och öppna den **Format** fönstret. Expandera den **villkorsstyrd formatering** kort och för **bakgrundsfärg**, **teckenfärg**, eller **datastaplar**, skjutreglaget till **På**. Aktivera ett av dessa alternativ visas en länk till *avancerade kontroller*, där du kan anpassa färger och värden för formatering av färg.
  
  ![Formatera fönstret som visar Data staplar kontroll](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Välj *avancerade kontroller* att visa en dialogruta där du kan du göra justeringar. Det här exemplet visar dialogrutan för **datastaplar**.

![Fönstret för data staplar](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Nästa steg

[Punktdiagram och bubbeldiagram i Power BI](power-bi-visualization-scatter.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)