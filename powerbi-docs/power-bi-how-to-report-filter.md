---
title: Översikt av panelen för Power BI-filter
description: Översikt av rapportens filterpanel i Power BI-tjänsten och Power BI-instrumentpanelen
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 6d0a1afe27372c808e63adb34fda96e978b2e2be
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34721396"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ta en titt på panelen för rapportfilter
Den här artikeln tar en djup titt på filterrapportfönstret. Du ser fönstret i [Power BI-tjänsten Redigeringsvyn och Läsvyn](service-reading-view-and-editing-view.md) och i [Power BI Desktop Rapportvyn](desktop-report-view.md).

Det finns många olika sätt att filtrera data i Power BI och vi rekommenderar att först läsa [Om filter och markering](power-bi-reports-filters-and-highlighting.md).

## <a name="working-with-the-report-filters-pane"></a>Arbeta med panelen för rapportfilter
I Power BI Desktop öppnas rapporter i rapportvyn. I Power BI-tjänsten kan rapporter öppnas i [redigeringsvyn eller läsvyn](service-reading-view-and-editing-view.md). I redigeringsvyn, och i rapportvyn i Desktop, kan rapportägare [lägga till filter för en rapport](power-bi-report-add-filter.md) och dessa filter sparas med rapporten. Användare som visar rapporten i läsvyn kan interagera med filtren och spara sina ändringar, men de kan inte lägga till nya filter i rapporten.

I Power BI-tjänsten sparas ändringar du gör i fönstret Filter i rapporterna, och dessa ändringar följer med till mobilversionen av rapporten. Om du vill återställa standardvärdena i fönstret Filter väljer du **Återställ till standard** på den översta menyraden.     

## <a name="open-the-filters-pane"></a>Öppna fönstret Filter
När en rapport har öppnats visas fönstret Filter längst till höger i rapportarbetsytan. Om du inte ser fönstret väljer du pilen i det övre högra hörnet för att expandera det. I läsvyn i Power BI-tjänsten är fönstret Filter det enda fönstret som är tillgängligt på höger sida.

I det här exemplet har vi valt ett visuellt objekt som innehåller 6 filter. Sidan har också filter som visas under rubriken **Sidonivåfilter**. Det finns ett [filter för detaljerad information](power-bi-report-add-filter.md) och hela rapporten har också ett filter: **räkenskapsår** är 2013 eller 2014.

![](media/power-bi-how-to-report-filter/power-bi-filter-list.png)

Vissa filter har ordet **alla** och detta innebär att alla värden ingår i filtret.  Som exempel kan vi av **Chain(All) (Kedja(alla))** på skärmbilden nedan avläsa att den här rapportsidan innehåller data om alla butikskedjorna.  Å andra sidan berättar filtret på rapportnivå för **Räkenskapsår 2013 eller 2014** att rapporten bara innehåller data för räkenskapsåren 2013 och 2014.

Alla som visar den här rapporten kan interagera med filtren.

* Visa information om filtret genom att hålla muspekaren över och klicka på pilen bredvid filtret.
  
   ![](media/power-bi-how-to-report-filter/power-bi-expan-filter.png)
* Ändra filtret, till exempel, ändra **Lindseys** till **Fashion Direct**.
  
     ![](media/power-bi-how-to-report-filter/power-bi-filter-chain.png)

* Återställ filtren till deras ursprungliga tillstånd genom att välja **Återställ till standard** på den översta menyraden.    
    ![](media/power-bi-how-to-report-filter/power-bi-reset-to-default.png)
    
* Ta bort filtret genom att välja **x** intill filternamnet.
  
  När du tar bort ett filter försvinner den från listan och data raderas från rapporten.  Om du till exempel tar bort filtret **räkenskapsår är 2013 eller 2014** finns räkenskapsårets informationen kvar i rapporten men den kommer inte längre att filtreras så att endast 2013 och 2014 visas. Istället visas alla räkenskapsår som innehåller data.  När du tar bort filtret, kommer inte du att kunna ändra det igen eftersom det har tagits bort från listan. Ett bättre alternativ är att ta bort filtret genom att välja ikonen Radera ![](media/power-bi-how-to-report-filter/power-bi-eraser-icon.png).
  
  ![](media/power-bi-how-to-report-filter/power-bi-delete-filter.png)

## <a name="filters-in-editing-view"></a>Filter i redigeringsvyn
När en rapport har öppnats i redigeringsläge i Desktop eller Power BI-tjänsten visas fönsterfiltret längst till höger i rapportarbetsytan i den nedre delen av fönstret **Visualisering**. Om du inte ser fönstret väljer du pilen i det övre högra hörnet för att expandera det.

![](media/power-bi-how-to-report-filter/power-bi-all-filters.png).  

Om inga visuella objekt markeras på arbetsytan visar fönstret Filter endast de filter som gäller för hela rapportsidan eller hela rapporten, samt eventuella filter för detaljerad information (om några sådana finns). I nedanstående exempel har inga visuella objekt valts och det finns inga filter på sidnivå eller filter för detaljerad information, men det finns ett filter på rapportnivå.  

![](media/power-bi-how-to-report-filter/power-bi-no-visual.png)  

Om ett visuellt väljs i arbetsytan visas också de filter som endast gäller för det visuella objektet:   

![](media/power-bi-how-to-report-filter/power-bi-visual-filters.png)

Välj nedpilen bredvid namnet på filtret om du vill visa alternativ för ett visst filter.  I exemplet nedan ställs filtret för rapporten in på 2013 och 2014. Och det här är ett exempel på **grundläggande filtrering**.  Om du vill visa avancerade alternativ väljer du **avancerade filter**.

![](media/power-bi-how-to-report-filter/pbi_filterlistdropdown.jpg)

## <a name="clear-a-filter"></a>Rensa ett filter
 Välj ikonen Radera ![](media/power-bi-how-to-report-filter/pbi_erasericon.jpg) i antingen grundläggande eller avancerat filtreringsläge för att rensa filtret. 

## <a name="add-a-filter"></a>Lägg till ett filter
* I redigeringsvyn i Desktop eller Power BI-tjänsten lägger du till ett filter i ett visuellt objekt, en sida, en visning av detaljerad information eller en rapport genom att välja ett fält från fönstret Fält och dra det till en lämplig filterbrunn, där du ser orden **Dra fält hit**. När ett fält har lagts till som ett filter, finjustera det med hjälp av grundläggande filtrering och avancerad filtrering (beskrivs nedan).

- **Om du drar ett nytt fält till området för filter på visuell nivå läggs fältet inte till i det visuella objektet**, men du kan filtrera det visuella objektet med det nya fältet. I exemplet nedan, har **Kedja** lagts till som ett nytt filter i det visuella objektet. Observera när du lägger till **Kedja** som ett filter att detta inte ändrar det visuella objektet förrän du använder grundläggande eller avancerade filtreringskontroller.

    ![](media/power-bi-how-to-report-filter/power-bi-visual-filter.gif)

* Alla fält som används för att skapa ett visuellt objekt är också tillgängliga som filter. Välj först ett visuellt objekt för att aktivera det. Fält som används i det visuella objektet visas i fönstret Visualiseringar och i fönstret Filter under rubriken **Visuella nivåfilter**.
  
   ![](media/power-bi-how-to-report-filter/power-bi-visual-filter.png)  
  
   Finjustera något av fälten med hjälp av grundläggande filtrering och avancerad filtrering (beskrivs nedan).

## <a name="types-of-filters-text-field-filters"></a>Typer av filter: textfältfilter
### <a name="list-mode"></a>Listläge
Om du markerar en kryssruta markeras eller avmarkeras värdet. Kryssrutan **Alla** kan användas för att växla tillståndet för alla kryssrutor. Kryssrutorna representerar de tillgängliga värdena för det här fältet.  När du justerar filtret uppdateras omformuleringen efter dina val. 

![](media/power-bi-how-to-report-filter/pbi_restatement.png)

Nu står det ”är Amarilla eller Carretera” i omformuleringen

### <a name="advanced-mode"></a>Avancerat läge
Välj **Avancerade filter** för att övergå till avancerat läge. Använd listrutekontroller och textrutor för att ange vilka fält som ska inkluderas. Genom att välja mellan **Och** och **Eller** kan du skapa komplexa filteruttryck. Välj knappen **Använd Filter** när du har angett dina önskade värden.  

![](media/power-bi-how-to-report-filter/aboutfilters.png)

## <a name="types-of-filters-numeric-field-filters"></a>Typer av filter: sifferfältfilter
### <a name="list-mode"></a>Listläge
Om värdena är begränsade, visar fältnamnet en lista.  Se **Textfältfilter** &gt; **Listläge** ovan för att få hjälp med att använda kryssrutor.   

### <a name="advanced-mode"></a>Avancerat läge
Om värdena är oändliga eller motsvarar ett värde öppnas det avancerade filterläget när du markerar fältnamnet. Använd listrutan och textrutor för att ange ett intervall med värden som du vill se. 

![](media/power-bi-how-to-report-filter/pbi_dropdown-and-text.png)

Genom att välja mellan **Och** och **Eller** kan du skapa komplexa filteruttryck. Välj knappen **Använd Filter** när du har angett dina önskade värden.

## <a name="types-of-filters-date-and-time"></a>Typer av filter: datum och tid
### <a name="list-mode"></a>Listläge
Om värdena är begränsade, visar fältnamnet en lista.  Se **Textfältfilter** &gt; **Listläge** ovan för att få hjälp med att använda kryssrutor.   

### <a name="advanced-mode"></a>Avancerat läge
Om fältvärdena representerar datum och tid, kan du ange en starttid/sluttid med datum/tid-filter.  

![](media/power-bi-how-to-report-filter/pbi_date-time-filters.png)

## <a name="next-steps"></a>Nästa steg
[Filtrera och markera i rapporter](power-bi-reports-filters-and-highlighting.md)  
[Interagera med filter och markeringar i rapportens läsvy](service-reading-view-and-editing-view.md)  
[Skapa filter i rapportens redigeringsvy](power-bi-report-add-filter.md)  
[Ändra hur en rapports visuella objekt korsfiltrerar och korsmarkerar varandra](service-reports-visual-interactions.md)

Läs mer om [rapporter i Power BI](service-reports.md)  
[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

