---
title: Lägga till ett filter till en rapport i redigeringsvyn
description: Lägg till ett sidfilter, ett visualiseringsfilter eller ett rapportfilter till en rapport i Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 328c8ab2e236f0ddc0c5116c1f76d343999193ab
ms.sourcegitcommit: 46f1ba3f972f6e64bce05ad0fd527b27c49aedd6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52157389"
---
# <a name="add-a-filter-to-a-report-in-editing-view"></a>Lägga till ett filter till en rapport i redigeringsvyn

Den här artikeln förklarar hur du lägger till ett sidfilter, ett visualiseringsfilter, ett rapportfilter eller detaljerad information i en rapport i Power BI. Exemplen i den här artikeln finns i Power BI-tjänsten. Men stegen är nästan identiska i Power BI Desktop.

**Visste du att?** Power BI har en ny filterupplevelse som för närvarande är i förhandsversion. Läs mer om [den nya filterupplevelsen i Power BI-rapporter](power-bi-report-filter-preview.md).

## <a name="filters-in-editing-view-or-reading-view"></a>Filter i redigeringsvyn jämfört med läsvyn
Du kan interagera med rapporter i två olika vyer: läsvyn och redigeringsvyn. Vilka filtreringsfunktioner som är tillgängliga beror på vilket läge du befinner dig i. Läs allt [om filter och markeringar i Power BI-rapporter](power-bi-reports-filters-and-highlighting.md) för mer information.

Den här artikeln beskriver hur du skapar filter i rapportens **Redigeringsvy**.  Mer information om filter i läsvyn finns i [Interagera med filter i rapportens läsvy](consumer/end-user-reading-view.md).

## <a name="filter-types-in-the-filters-pane"></a>Filtertyper i Filterpanelen
Oavsett om du använder Desktop eller Power BI-tjänsten visas fönstret Filter till höger i rapportarbetsytan. Om inte fönstret Filter visas kan du öppna det genom att välja ikonen ">" längst upp till höger.

Det finns fyra typer av filter: **sidfilter**, **visuellt filter**, **filter för detaljerad information** och **rapportfilter**.

![filterfönstret i läsvyn](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

Eftersom filter *bevaras* sparas filtren, utsnitten och andra datavisningsändringar som du gjort när du lämnar Power BI. På så sätt kan du fortsätta där du slutade när du återvänder till rapporten. Om du inte vill att filterändringarna ska sparas väljer du **Återställ till standard** från den översta menyraden.

![knapp för beständiga filter](media/power-bi-report-add-filter/power-bi-reset-to-default.png)

## <a name="add-a-filter-to-a-visual"></a>Lägga till ett filter i ett visuellt objekt
Du kan lägga till ett filter i ett specifikt visuellt objekt på två olika sätt (även kallat ett ”visuellt filter”). 

* Filtrera ett fält som redan används av visualiseringen.
* Identifiera ett fält som inte redan används av visualiseringen och lägga till fältet direkt till bucketen **Visuella nivåfilter**.

Den här proceduren använder förresten, detaljhandelsanalys om du vill ladda ned och följa den. Hämta Exempel på [Detaljhandelsanalys](sample-retail-analysis.md).

### <a name="filter-the-fields-in-the-visual"></a>Filtrera fälten i det visuella objektet


1. Öppna [rapporten i Redigeringsvyn](service-the-report-editor-take-a-tour.md).
   
   ![](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. Öppna panelerna Visualiseringar och Filter samt Fält (om de inte redan är öppna).
   
   ![](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. Välj ett visuellt objekt för att aktivera det. Alla fält som används av det visuella objektet finns på panelen **Fält** och anges även på panelen **Filter** under rubriken **Visuella nivåfilter**.
   
   ![](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. Nu ska vi lägga till ett filter till ett fält som redan används av visualiseringen. 
   
    Rulla ned till området **Visuella nivåfilter** och välj pilen för att expandera fältet som du vill filtrera. I det här exemplet ska vi filtrera **StoreNumberName**.
     
    ![](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
    
    Välj någon av filtreringskontrollerna **Grundläggande**, **Avancerade** eller **Top N**. I det här exemplet ska vi söka i grundläggande filtrering för **cha** och välja de fem butikerna.
     
    ![](media/power-bi-report-add-filter/power-bi-search-filter.png) 
   
    Det visuella objektet ändras för att återspegla det nya filtret. Om du sparar rapporten med filtret kan rapportens läsare se det filtrerade innehållet från början och interagera med filtret i läsvyn genom att välja eller rensa värden.
     
    ![](media/power-bi-report-add-filter/power-bi-search-visual-filter-results.png)

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>Filtrera med ett fält som inte finns i det visuella objektet

Nu ska vi lägga till ett helt nytt fält som ett filter på visuell nivå i vårt visuella objekt.
   
1. På panelen Fält väljer du det fält som du vill lägga till som ett nytt visuellt nivåfilter och drar det till **området för visuella nivåfilter**.  I det här exemplet ska vi dra **Distriktschef** till bucketen **Visuella nivåfilter**, söka efter **an** och välja dessa tre chefer. 
     
    ![](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    Observera att **Distriktschef***inte* läggs till i själva visualiseringen. Visualiseringen består fortfarande av **StoreNumberName** som axel och **This Year Sales (Årets försäljning)** som värde.  
     
    ![](media/power-bi-report-add-filter/power-bi-visualization.png)

    Själva visualiseringen filtreras nu för att bara visa dessa chefers försäljning i år för de angivna butikerna.
     
    ![](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    Om du sparar rapporten med filtret kan rapportens läsare interagera med filtret **Distriktschef** i läsvyn genom att välja eller rensa värden.

## <a name="add-a-filter-to-an-entire-page"></a>Lägg till ett filter för en hel sida

Du kan även lägga till ett filter för en hel sida (det vill säga sidvisningsfilter)
1. Öppna [rapporten i Redigeringsvyn](service-the-report-editor-take-a-tour.md).
2. Öppna panelerna Visualiseringar och Filter samt Fält (om de inte redan är öppna).
3. På panelen Fält väljer du det fält som du vill lägga till som ett nytt sidnivåfilter och drar det till **området för sidnivåfilter**.  
4. Välj de värden som du vill filtrera och ange **Grundläggande** eller **Avancerade** filtreringskontroller.
   
   All visualisering på sidan som påverkas av det här filtret ritas om för att avspegla ändringen. 
   
   ![](media/power-bi-report-add-filter/filterpage.gif)

    Om du sparar rapporten med filtret kan rapportens läsare interagera med filtret i läsvyn genom att välja eller rensa värden.

## <a name="add-a-drillthrough-filter"></a>Lägga till ett filter för detaljerad information
Med visning av detaljerad information i Power BI-tjänsten och Power BI Desktop kan du skapa en *målrapportsida* som fokuserar på en specifik enhet – som en leverantör, kund eller tillverkare. Användarna kan nu från övriga rapportsidor högerklicka på en datapunkt för denna entitet och gå in i detalj på fokussidan.

### <a name="create-a-drillthrough-filter"></a>Skapa ett filter för detaljerad information
Om du vill hänga på öppnar du Exempel på kundlönsamhet i redigeringsvyn. Anta att du vill skapa en sida som fokuserar på affärsområden för chefer.   

1. Lägg till en ny sida i rapporten och döp den till **Team Executive (Teamchef)**. Den här sidan blir *målet* för den detaljerade informationen.
2. Lägg till visualiseringar som spårar nyckelvärden för teamchefernas affärsområden.    
3. Lägg även till **Chef (Executive) > Executive Name (Chefens namn)** till området för filtren för detaljerad information.    
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    Observera att Power BI lägger till en bakåtpil på rapportsidan.  Om du väljer bakåtpilen returneras du till den *ursprungliga* rapportsidan, den sida där du befann dig när du valde alternativet för visning av detaljerad information. Bakåtpilen fungerar bara i läsvyn.
   
     ![](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>Använda filter för detaljerad information
Nu ska vi se hur filtret för detaljerad information fungerar.

1. Starta på rapportsidan **Teamresultatkort**.    
2. Låt oss anta att du är Andrew Ma och du vill se rapportsidan för teamchefer filtrerad bara för dina data.  Högerklicka på valfri grön datapunkt i det övre vänstra ytdiagrammet för att öppna menyalternativet Visning av detaljerad information.
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. Välj **Visning av detaljerad information > Team Executive (Teamchef)** för att komma till rapportsidan med namnet **Team Executive (Teamchef)**. Sidan filtreras för att visa information om datapunkten som du högerklickade på, i det här fallet Andrew Ma. Endast fältet som finns i filtren för detaljerad information skickas vidare till rapportsidan för detaljerad information.  
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-filter-to-an-entire-report-aka-report-filter"></a>Lägga till ett filter för en hel rapport (dvs. rapportfilter)
1. Öppna [rapporten i Redigeringsvyn](service-the-report-editor-take-a-tour.md).
2. Öppna panelerna Visualiseringar och Filter samt Fält (om de inte redan är öppna).
3. På panelen Fält väljer du det fält som du vill lägga till som ett nytt rapportnivåfilter och drar det till **området för rapportnivåfilter**.  
4. Välj de värden du vill filtrera.

    Visualiseringarna på den aktiva sidan, och på alla sidor i rapporten, ändras för att återspegla det nya filtret. Om du sparar rapporten med filtret kan rapportens läsare interagera med filtret i läsvyn genom att välja eller rensa värden.

1. Välj bakåtpilen för att återgå till den föregående rapportsidan.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

- Ibland kan det hända att ett filter på visuell nivå och ett filter på sidnivå returnerar olika resultat.  När du till exempel lägger till ett filter på visuell nivå, filtrerar Power BI de aggregerade resultaten.  Aggregeringstypen är som standard Summa, men du kan [ändra aggregeringstypen](service-aggregates.md).  

    När du sedan lägger till ett filter på sidnivå filtrerar Power BI utan aggregering.  Det aggregerar inte eftersom en sida kan ha många visuella objekt som var och ett kan använda olika aggregeringstyper.  Så filtret tillämpas på varje datarad.

- Kontrollera att du är i rapportens [Redigeringsvy](service-interact-with-a-report-in-editing-view.md) om du inte ser panelen Fält.    
- Om du har gjort många filterändringar och vill återgå till standardinställningarna som rapportförfattaren använde väljer du **Återställ till standard** från den översta menyraden.

## <a name="next-steps"></a>Nästa steg
[Ta en titt på panelen för rapportfilter](consumer/end-user-report-filter.md)

[Filtrera och markera i rapporter](power-bi-reports-filters-and-highlighting.md)

[Interagera med filter och markeringar i rapportens läsvy](consumer/end-user-reading-view.md)

[Ändra hur en rapports visuella objekt korsfiltrerar och korsmarkerar varandra](consumer/end-user-interactions.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

