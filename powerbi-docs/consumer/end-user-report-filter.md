---
title: En titt på rapportfönstret Filter
description: Så här lägger du till ett filter i en rapport i Power BI-tjänsten för användare
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67533016"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ta en titt på panelen för rapportfilter

I den här artikeln tittar vi närmare på fönstret **Filter** för rapporter i Power BI-tjänsten. Använd filtren för att upptäcka nya insikter i dina data.

Det finns många olika sätt att filtrera data i Power BI. Mer information om filter finns i [Filter och markeringar i Power BI-rapporter](../power-bi-reports-filters-and-highlighting.md).

![Skärmbild av en rapport i en webbläsare med en pil som pekar på alternativet Filter.](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Arbeta med panelen för rapportfilter

Glöm inte att titta i fönstret **Filter** när en kollega delar en rapport med dig. Ibland är fönstret dolt på den högra kanten av rapporten. Välj fönstret för att visa det.

![Skärmbild av rapporten med fönstret Filter expanderat.](media/end-user-report-filter/power-bi-filter-pane.png)

Fönstret *Filter* innehåller de filter som **rapportdesignern** har lagt till i rapporten. Som *användare* kan du interagera med befintliga filter och spara dina ändringar, men du kan inte lägga till nya filter i rapporten. På skärmbilden ovan har designern lagt till två sidnivåfilter: **Segment** och **År**. Du kan interagera och ändra filtren, men du kan inte lägga till ett tredje sidnivåfilter.

I Power BI-tjänsten sparas de ändringar du gör för fönstret **Filter** i rapporten. Tjänsten överför dessa ändringar till den mobila versionen av rapporten.

Om du vill återställa fönstret **Filter** till designerns standardinställningar väljer du ![Skärmbild av alternativet Återställ till standard](media/end-user-report-filter/power-bi-reset.png). på den översta menyraden.

## <a name="view-all-the-filters-for-a-report-page"></a>Visa alla filter för en rapportsida

I fönstret **Filter** visas alla filter som designern lägger till i rapporten. Fönstret **Filter** är också det område där du kan visa information om filter och interagera med dem. Du kan spara ändringar du gör eller använda alternativet **Återställ till standard** för att återställa de ursprungliga inställningarna i filtret.

Om du vill spara ändringar kan du även skapa ett personligt bokmärke.  Mer information finns i [Vad är bokmärken?](end-user-bookmarks.md).

Fönstret **Filter** visar och hanterar flera typer av rapportfilter. De kan tillämpas på ett visuellt objekt, för en rapportsida eller för hela rapporten.

I det här exemplet har vi valt ett visuellt objekt som innehåller två filter. Rapportsidan har också filter som visas under rubriken **Filter på den här sidan**. Dessutom har hela rapporten ett filter för **Datum**.

![Skärmbild av en rapport med en visualisering och dess relaterade filter markerade.](media/end-user-report-filter/power-bi-all-filters2.png)

Intill vissa filter finns texten **(Alla)** . **(Alla)**  innebär att alla värden ingår i filtret. På skärmbilden ovan visar **Segment(Alla)** att rapportsidan innehåller data om alla produktsegmenten. Om du väljer sidnivåfiltret **för regionen Västra** kommer rapportsidan bara innehålla data för regionen Västra.

Alla som visar den här rapporten kan interagera med filtren.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Visa bara filter som används för ett visuellt objekt

Om du vill se vilka filter som används i ett specifikt visuellt objekt hovrar du över det visuella objektet för att visa filterikonen ![Skärmbild av Filter-ikonen.](media/end-user-report-filter/power-bi-filter-icon.png). Välj filterikonen för att se ett popup-fönster med alla filter, sektorer osv. som påverkar det visuella objektet. Filtren i fönstret som visas är de samma som visas på fönstret **Filter**.

![Skärmbild av en lista över filter med pilar som pekar på var dessa filter finns i fönstret Filter.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

Här är de typer av filter som den här vyn kan visa:

- Grundläggande filter

- Utsnitt

- Korsmarkering

- Korsfiltrering

- Avancerad filtrering

- Högsta N-filter

- Relativa datumfiltrer

- Synkroniseringsutsnitt

- Inkludera/exkludera filter

- Filter som skickas via en URL

Se följande exempel:

1. Vi kan se att stapeldiagrammet har korsfiltrerats.

1. **Ingår** visar att korsfiltret avser **Segment**, och att tre ingår.

1. Ett utsnitt har tillämpats för **Kvartal**.

1. **Region** är ett filter som tillämpas på den här rapportsidan och

1. **isVanArsdel** och **År** är filter som tillämpas för det här visuella objektet.

![Skärmbild av en rapport och dess filter med en lista över filter, numrerade för att stämma överens med den numrerade listan ovan.](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Söka i ett filter

Ibland kan det finnas en lång lista med värden för ett filter. Använd sökrutan för att hitta och välja det värde som du vill ha.

![Skärmbild av hur du söker i ett filter.](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Visa filterdetaljer

Ta en titt på tillgängliga värden och antal för att förstå ett filter.  Visa information om filtret genom att hålla muspekaren över och klicka på pilen bredvid filternamnet.
  
![Skärmbild av ett filter som visar Västra som vald region.](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Ändra val av filter

Ett sätt att söka efter insikter från data är att interagera med filtren. Du kan ändra filtren med hjälp av den nedrullningsbara pilen bredvid fältnamnet.  Dina alternativ varierar från enkla val från en lista till att identifiera datum- eller sifferintervall, beroende på filtret och den typ av data som Power BI filtrerar. I det avancerade filtret nedan har vi ändrat filtret **Totalt antal enheter hittills i år** på trädkartan att ligga mellan 2000 och 3000. Observera att den här ändringen tar bort Prirum från trädkartan.
  
![Skärmbild av en rapport och dess filter, med Fashions Direct markerat.](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Håll ned CTRL-tangenten för att välja mer än ett filtervärde åt gången. De flesta filter har stöd för flerval.

### <a name="reset-filter-to-default"></a>Återställ filter till standard

Om du vill återställa alla ändringar du har gjort i filtret väljer du **Återställ till standard** från den översta menyraden.  Det här alternativet återställer filtren till deras ursprungliga tillstånd, som de ställts in av reportdesignern.

![Skärmbild av alternativet Återgå till standard.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Rensa ett filter

Om du bara vill ange ett filter för **(Alla)** , avmarkerar du det genom att välja radergummiikonen ![Skärmbild av radergummiikonen.](media/end-user-report-filter/power-bi-eraser-icon.png) vid filternamnet.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Nästa steg

Lär dig hur och varför [visuella objekt korsfiltrerar och korsmarkerar varandra på en rapportsida](end-user-interactions.md)