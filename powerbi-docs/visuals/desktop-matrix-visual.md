---
title: Använd det visuella matrisobjektet i Power BI
description: Läs mer om hur det visuella matrisobjektet möjliggör steglayouter och detaljerade markeringar i Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/10/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c091295d50bac576af411d967b9902d6804f82be
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637854"
---
# <a name="create-matrix-visualizations-in-power-bi"></a>Skapa matrisvisualiseringar i Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Det visuella matrisobjektet liknar en tabell.  En tabell har stöd för två dimensioner och dess data är plana, vilket innebär att dublettvärden visas och inte aggregeras. En matris gör det enklare att visa data på ett meningsfullt sätt med hjälpa av flera dimensioner – och den har stöd för stegvis layout. Matrisen aggregerar data automatiskt och gör det möjligt att öka detaljnivån. 

Du kan skapa visuella matrisobjekt i **Power BI Desktop**-rapporter och korsmarkera element i matrisen med andra visuella objekt på den rapportsidan. Du kan till exempel välja rader, kolumner och även enskilda celler och korsmarkeringar. Du kan även kopiera enskilda celler och markeringar av flera celler och klistra in dem i andra program. 

![korsmarkerad matris och ringdiagram](media/desktop-matrix-visual/matrix-visual_2a.png)

Det finns många funktioner som är kopplade till matrisen och vi ska gå igenom dem i följande avsnitt i den här artikeln.


## <a name="understanding-how-power-bi-calculates-totals"></a>Beräkning av summor i Power BI

Innan vi går vidare till hur man använder det visuella matrisobjektet är det viktigt att du förstår hur Power BI beräknar total- och delsummor i tabeller och matriser. När det gäller summa- och delsummarader utvärderar Power BI måttet för alla rader i underliggande data – det handlar inte bara om att lägga till värdena i de tabellrader som syns eller visas. Detta innebär att du kan få andra värden än vad du räknat med i totalsummaraden.

Ta en titt på följande visuella matrisobjekt. 

![jämför tabeller och matriser](media/desktop-matrix-visual/matrix-visual_3.png)

I det här exemplet visar varje rad i det visuella matrisobjektet längst till höger *Belopp* för varje kombination säljare/datum. Men eftersom en säljare visas för flera datum kan siffrorna visas mer än en gång. Den korrekta totalsumman för underliggande data och en enkel addering av de synliga värdena överensstämmer därmed inte. Detta är ett vanligt mönster när det värde som du summerar finns på ”ett”-sidan i ett ett-till-många-samband.

När du tittar på summor och delsummor, kom ihåg att dessa värden baseras på underliggande data. De är inte bara baserade på de synliga värdena.


## <a name="expanding-and-collapsing-row-headers"></a>Visa och dölja radrubriker
Det finns två sätt på vilka du kan visa radrubriker. Det första är att klicka på snabbmenyn. Du ser alternativen för att visa den radrubrik som du har valt, hela nivån eller allt upp till den sista nivån i hierarkin. Det finns även snarlika alternativ för att dölja radrubrikerna.

![](media/desktop-matrix-visual/power-bi-expand1.png)

Du kan också lägga till plus- och minusknappar (+/-) till radrubrikerna via formateringsrutan under kortet **Radrubriker**. Ikonerna matchar som standard radrubrikens formatering, men du kan anpassa deras färger och storlekar separat om du vill.

När ikonerna har aktiverats fungerar de ungefär som pivottabellsikoner i Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

Matrisens expansionsstatus sparas med rapporten. En matris kan fästas på en instrumentpanel som visas eller döljs. När instrumentpanelen är markerad och rapporten öppnas, kan du fortfarande ändra visningstillståndet i rapporten. 

![](media/desktop-matrix-visual/power-bi-expand3.png)

> [!NOTE]
> Om du skapar en rapport ovanpå en flerdimensionell Analysis Services-modell finns det några särskilda överväganden för expandering/minimering om modellen använder standardmedlemsfunktionen. Mer information finns i [Arbeta med flerdimensionella modeller i Power BI](../desktop-default-member-multidimensional-models.md)

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

Genom att välja **Granska nedåt** expanderas matrisen för *radnivån*, *exklusive* alla andra radrubriker med undantag för den radrubrik som valdes. I följande bild har **Förslag** > **Granska nedåt** valts. Observera att andra topprader inte längre visas i matrisen. Detta är en mycket användbar funktion och som är särskilt fiffig när det är dags att korsmarkera avsnitt.

![matrisen vars detaljnivå har ökats med en nivå](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Välj ikonen **Granska uppåt** för att gå tillbaka till föregående toppnivåsvy. Om du sedan väljer **Förslag** > **Visa nästa nivå** visas en fallande lista över alla objekt på nästa nivå (i det här fallet fältet *Affärsmöjlighetens storlek*) utan kategoriseringen för nästa hierarkinivå.

![matris som använder Visa nästa nivå](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Välj ikonen **Granska uppåt** i det övre vänstra hörnet för att matrisen ska visa alla toppkategorier och välj sedan **Förslag** > **Expandera till nästa nivå** för att visa alla värdena för hierarkins båda nivåer – *Försäljningssteg* och *Affärsmöjlighetens storlek*.

![matris som använder Utvidga nästa nivå](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

Du kan också använda menyalternativet **Expandera** för att styra visningen ytterligare.  Välj exempelvis **Förslag** > **Expandera** > **Val**. Power BI visar en fullständig rad för varje *Försäljningssteg* och alla alternativen för *Affärsmöjlighetens storlek* för *Förslag*.

![Matrisen efter att Expandera har tillämpats på Förslag](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Öka detaljnivån för kolumnrubriker
På samma sätt som du kan öka detaljnivån för rader kan du göra samma med Kolumner. I följande bild finns det två fält i fältet **Kolumner** som skapar en hierarki som liknar den som vi använde för raderna tidigare i den här artikeln. I fältområdet **Kolumner** hittar vi *Region* och *Segment*. Så snart som det andra fältet lades till i **Kolumner**, visades en ny listrutemeny på det visuella objektet som för närvarande visar **Rader**.

![Matrisen efter att det andra kolumnvärdet har lagts till](media/desktop-matrix-visual/power-bi-matrix-row.png)

Om du vill öka detaljnivån för kolumner, väljer du **Kolumner** i menyn *Fortsätt granska* som finns i det övre vänstra hörnet av matrisen. Välj den *östra* regionen och välj **Granska nedåt**.

![meny för ökad detaljnivå för kolumner](media/desktop-matrix-visual/power-bi-matrix-column.png)

När du väljer **Granska nedåt** visas nästa nivå i kolumnhierarkin för *Region > Östra*, vilket i detta fall är *Antal affärsmöjligheter*. Den andra regionen är dold.

![matris med ökning av detaljnivån en nivå för kolumn](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

Resten av alternativen i menyn fungerar för kolumner på samma sätt som de gör för rader (se föregående avsnitt **Öka detaljnivån för radrubriker**). Du kan **Visa nästa nivå**, **Expandera till nästa nivå** med kolumner på samma sätt som rader.

> [!NOTE]
> Ikonerna för att öka och minska detaljnivån längst upp till vänster på matrisen gäller endast för rader. Du måste använda högerklicksmenyn för att öka detaljnivån i kolumner.

## <a name="stepped-layout-with-matrix-visuals"></a>Stegvis layout med matriser

Visuella matrisobjekt har automatiskt indrag för underkategorier i en hierarki under en överordnad kategori. Detta kallas stegvis layout.

I den ursprungliga versionen av det visuella matrisobjektet visades underkategorier i en helt annan kolumn och tog upp mer utrymme i det visuella objektet. Följande bild visar tabellen i den ursprungliga matrisen. Observera underkategorierna i en separat kolumn.

![Skärmbild av det gamla visuella matrisobjektet som visar underkategorierna i en separat kolumn.](media/desktop-matrix-visual/matrix-visual_14.png)

I följande bild visas en matris med stegvis layout. Lägg märke till kategorin *datorer* visar underkategorierna något indragna (tillbehör för datorer, stationära datorer, bärbara datorer, skärmar och så vidare) vilket är tydligare och mycket mer komprimerat.

![matrisens aktuella metod för att formatera data](media/desktop-matrix-visual/matrix-visual_13.png)

Du kan enkelt ändra inställningarna för stegvis layout. Med det visuella matrisobjektet markerat, i **Formatera**-avsnittet (färgvalsikonen) i **Visualiseringar**-fönstret, expanderar du radrubriksavsnittet. Du har två alternativ: knappen stegvis layout (som aktiverar eller inaktiverar funktionen) och stegvis layoutindrag (anger indrag i bildpunkter).

![Radrubrikskort med stegvis layoutkontroll](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Om du inaktiverar stegvis layout, visar Power BI underkategorierna i en annan kolumn istället för att visas indragna under den överordnade kategorin.

## <a name="subtotals-and-grand-totals-with-matrix-visuals"></a>Delsummor och totalsummor med visuella matrisobjekt

Du kan aktivera eller inaktivera delsummor i matriser, för såväl rader som kolumner. I den här bilden ser du att raddelsummorna har inställningen **På** och att de ska visas längst ned.

![matris som visar summor och delsummor](media/desktop-matrix-visual/power-bi-subtotals.png)

När du aktiverar **Delsummor** och lägger till en etikett så lägger Power BI också till en rad och samma etikett för totalsumman. Om du vill formatera totalsumman väljer du formateringsalternativet för **Totalsumma**. 

![matris som visar kortet Totalsumma](media/desktop-matrix-visual/power-bi-grand-total.png)

Om du vill inaktivera delsummor och totalsumma expanderar du kortet **Delsummor** i formateringsavsnittet i fönstret Visualiseringar. Flytta skjutreglaget för raddelsummor till **Av**. När du gör det visas inte delsummorna.

![matris med delsummor inaktiverade](media/desktop-matrix-visual/power-bi-no-subtotals.png)

Samma sak gäller för kolumndelsummor.

## <a name="add-conditional-icons"></a>Lägg till villkorsstyrda ikoner
Du kan ge visuell vägledning i dina tabeller och matriser med *villkorsstyrda ikoner*. 

Expandera kortet **Villkorsstyrd formatering** i formateringsavsnittet i fönstret Visualiseringar. Flytta reglaget för **Ikoner** till **På** och välj **Avancerade kontroller**.

![Matris med skärmen Ikoner visas](media/desktop-matrix-visual/power-bi-icons.png)

Justera villkor, ikoner och färger för matrisen och välj **OK**. I det här exemplet använder vi en röd flagga för låga värden, en lila cirkel för höga värden och en gul triangel för alla värden där emellan. 

![Matris med ikoner visas](media/desktop-matrix-visual/power-bi-icons-applied.png)

## <a name="cross-highlighting-with-matrix-visuals"></a>Korsmarkering med matriser

Med det visuella matrisobjektet kan du välja valfria element i matrisen som grund för korsmarkering. Välj en kolumn i en matris så markerar Power BI kolumnen, precis som alla andra visuella objekt på rapportsidan. Den här typen av korsmarkering har varit en vanlig funktion för andra visuella objekt och val av datapunkter, så nu har det visuella matrisobjektet samma funktion.

Dessutom fungerar Ctrl + klicka för korsmarkering. I följande bild valdes till exempel en samling av underkategorier från det visuella matrisobjektet. Observera hur objekt som inte var markerat från det visuella objektet är nedtonade och hur övriga visuella objekt på sidan återspeglar de val du gjorde i det visuella matrisobjektet.

![Skärmbild av det visuella matrisobjektet tillsammans med två andra visuella objekt som visar funktionen Ctrl + klicka för korsmarkering.](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Kopiera värdena från Power BI så att du kan använda dem i andra program

Din matris eller tabell kan ha innehåll som du vill använda i andra program: Dynamics CRM, Excel och andra Power BI-rapporter. Genom att högerklicka i Power BI kan du kopiera en cell eller ett cellurval till Urklipp. Sedan kan du klistra in dem i det andra programmet.


* Om du vill kopiera en enskild cells värde markerar du cellen, högerklickar och väljer **Kopiera värde**. Med det oformaterade cellvärdet i Urklipp kan du nu klistra in det i ett annat program.

    ![Skärmbild av det visuella matrisobjektet med en pil som pekar på ett värde och högerklicksmenyn expanderad med alternativen Kopiera värde och Kopiera markering framhävda.](media/desktop-matrix-visual/power-bi-cell-copy.png)



* Om du vill kopiera mer än en enskild cell markerar du ett cellområde eller markerar en eller flera celler med hjälp av CTRL. 

    ![Skärmbild av det visuella matrisobjektet med en pil som pekar från tre framhävda värden till högerklicksmenyn som är expanderad med alternativen Kopiera värde och Kopiera markering framhävda.](media/desktop-matrix-visual/power-bi-copy.png)

* Kopian inkluderar kolumn- och radrubrikerna.

    ![Skärmbild som visar Excel-rader och -kolumner med värdena inklistrade.](media/desktop-matrix-visual/power-bi-copy-selection.png)

* Om du vill göra en kopia av den visuella objektet som bara innehåller de markerade cellerna, markerar du en eller flera celler med CTRL, högerklick och väljer **Kopiera visuellt objekt**

    ![Skärmbild som visar alternativet Kopiera visuellt objekt](media/desktop-matrix-visual/power-bi-copy-visual.png)

* Kopian kommer att vara en annan matris visualisering, men innehåller bara dina kopierade data.

    ![Skärmbild som visar exempel på Kopiera visuellt objekt](media/desktop-matrix-visual/power-bi-copy-visual-example.png)

## <a name="setting-a-matrix-value-as-a-custom-url"></a>Ange ett matrisvärde som en anpassad URL

Om du har en kolumn eller ett mått som innehåller webbadresser kan du använda villkorsstyrd formatering så att webbadresserna används som aktiva länkar för fälten. Du hittar det här alternativet under kortet **Villkorsstyrd formatering** i formateringsfönstret.

![Filterkort som visar vilka rader som väljs](media/desktop-matrix-visual/power-bi-web-url.png)

Ställ in **Webb-URL** på värdet PÅ och välj ett fält som ska användas som URL för kolumnen. När värdena i fältet (kolumnen) används blir de aktiva länkar. Hovra om du vill se länken och välj att hoppa till den sidan. 

Mer information finns i [Villkorsstyrd tabellformatering](../desktop-conditional-table-formatting.md)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Fyllning och teckenfärger med matriser
Med det visuella matrisobjektet kan du använda villkorsstyrd formatering (färger, fyllning och datastaplar) för cellernas bakgrundsfärger inom matrisen samt tillämpa villkorsstyrd formatering på själva texten och värdena.

Om du vill tillämpa villkorsstyrd formatering, väljer du det visuella matrisobjektet och öppnar fönstret **Format**. Expandera kortet **Villkorsstyrd formatering** och flytta skjutreglaget till **På** för antingen **Bakgrundsfärg**, **Teckenfärg** eller **Datastaplar**. När du aktiverar något av dessa alternativ visas en länk till *Avancerade kontroller*, där du kan anpassa färger och värden för formatering av färg.
  
  ![Formatfönster som visar datastapelskontroll](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Välj *Avancerade kontroller* för att visa en dialogruta där du kan göra justeringar. Det här exemplet visar dialogrutan för **Datastaplar**.

![Datastapelsfönster](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

* Om textdata i matrisens celler eller rubriker innehåller tecken för ny rad, så ignoreras dessa tecken om du inte växlar alternativet "Automatiskt radbyte" i elementets associerade formatpanelskort. 

## <a name="next-steps"></a>Nästa steg

[Visuellt Power Apps-objekt för Power BI](power-bi-visualization-powerapp.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
