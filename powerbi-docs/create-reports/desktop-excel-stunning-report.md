---
title: 'Självstudie: Från Excel-arbetsbok till proffsig rapport i Power BI Desktop'
description: Den här självstudien beskriver hur du snabbt skapar en proffsig rapport från en Excel-arbetsbok.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 07/21/2020
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: b628502ad5658388065a197c1c722a59dd9ad2b4
ms.sourcegitcommit: e9cd61eaa66eda01cc159251d7936a455c55bd84
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86973742"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>Självstudie: Från Excel-arbetsbok till proffsig rapport i Power BI Desktop

I den här självstudien lär du dig att skapa en proffsig rapport på bara 20 minuter! 

Din chef vill ha en rapport över dina senaste försäljningssiffror. Rapporten ska ge svar på följande frågor: 

- Vilken månad och vilket år var vinsten störst? 
- Var är försäljningen störst (efter land)? 
- Vilken produkt och vilket segment bör företaget fortsätta investera i? 

Vi kan snabbt skapa den här rapporten med hjälp av vår exempelarbetsbok med ekonomiska data. Så här ser den slutliga rapporten ut. Då sätter vi igång! 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Skärmbild av Power BI-rapport i Power BI-tjänsten."::: 

I den här självstudien får du lära dig att:

> [!div class="checklist"]
> * Hämta exempeldata
> * Förbereda data med några transformeringar
> * Skapa en rapport med en rubrik, tre visuella objekt och ett utsnitt
> * Publicera rapporten till Power BI-tjänsten så att du kan dela den med dina kollegor

## <a name="prerequisites"></a>Förutsättningar

- Innan du börjar måste du [ladda ned Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Om du planerar att publicera rapporten till Power BI-tjänsten och inte har registrerat dig än, [registrerar du dig för en kostnadsfri utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="download-the-sample"></a>Ladda ned exemplet

För att kunna följa stegen i självstudien måste du ladda ned exempelarbetsboken. 

1. Ladda ned [Excel-arbetsboken Financial Sample](https://go.microsoft.com/fwlink/?LinkID=521962).
1. Öppna Power BI Desktop.
1. Välj **Excel** i avsnittet **Data** på fliken **Start**.
1. Navigera till den plats där du sparade exempelarbetsboken och välj **Öppna**.

## <a name="prepare-your-data"></a>Förbereda dina data 

I **navigatören** kan du välja att *transformera* eller *läsa in* data. Navigatören visar en förhandsgranskning av dina data så att du kan kontrollera att dataområdet stämmer. Numeriska datatyper visas i kursiv stil. Om du behöver göra ändringar kan du transformera dina data innan du läser in dem. För att göra det enklare att förstå visualiseringarna senare ska vi transformera våra data nu. När du transformerar data läggs transformeringen till i listan under **Frågeinställningar** i **Tillämpade steg** 

1. Välj tabellen **Financials** (Ekonomi) och välj sedan **Transformera data**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Skärmbild av navigatören i Power BI med ekonomiska exempeldata."::: 

1. Välj kolumnen **Units Sold** (Sålda enheter). Välj **Datatyp** på fliken **Start** och välj sedan **Heltal**. Ändra kolumntypen genom att välja **Ersätt aktuell**. 

    Det vanligaste dataförberedelsesteget är att byta datatyp. I vårt exempel uttrycks de sålda enheterna i decimalform. Men det är meningslöst att visa 0,2 eller 0,5 av en såld enhet? Så vi ändrar det till heltal. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="Skärmbild som visar hur du ändrar ett decimaltal till ett heltal."::: 

1. Välj kolumnen **Segment**. Välj **Format** på fliken **Transformera** och välj sedan **VERSALER**.

    Vi vill också att det ska vara lättare att se segmenten i diagrammet. Så vi formaterar kolumnen Segment. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="Skärmbild som visar hur du ändrar rubriker från gemener till versaler.":::

1. Vi vill också korta ned kolumnnamnet från **Month Name** (Namn på månad) till bara **Month** (Månad). Dubbelklicka på kolumnen **Month Name** (Namn på månad) och ändra till **Month** (Månad).  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="Skärmbild som visar hur du kortar ned kolumnnamnet.":::

1. Välj listrutan i kolumnen **Product** (Produkt) och avmarkera rutan bredvid **Montana**. 

     Eftersom vi vet att produkten Montana togs ur försäljning förra månaden vill vi filtrera bort dessa data från rapporten för att undvika förvirring. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Skärmbild som visar hur du tar bort Montana-värden.":::

1. Du ser att transformeringarna har lagts till i listan under **Frågeinställningar** i **Tillämpade steg**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="Skärmbild som visar listan med tillämpade steg.":::

1. Välj **Stäng och tillämpa** på fliken **Start**. Snart är allt klart för att skapa rapporten. 

    Ser du Sigma-symbolen i fältlistan? Power BI har identifierat dessa fält som numeriska. Och datumfältet visas med en kalendersymbol.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="Skärmbild av fältlistan med numeriska fält och datumfältet.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>Överkurs: Skriva ett mått i DAX

Att skriva *mått* i formelspråket *DAX* är extremt kraftfullt för datamodellering. Du kan lära dig massor om DAX i Power BI-dokumentationen. Vi nöjer oss med att skriva ett grundläggande mått och att koppla ihop två tabeller. 

1. Välj **Datavy** till vänster. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="Skärmbild av ikonen för datavy.":::

1. Välj **Ny tabell** på menyfliken **Start**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="Skärmbild av ikonen för ny tabell.":::

1. Skriv det här måttet för att skapa en kalendertabell med alla datum mellan den 1 januari 2013 och den 31 december 2014.  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. Välj bockmarkeringen för att bekräfta.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="Skärmbild av DAX-uttryck.":::

1. Välj **modellvyn** till vänster. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="Skärmbild av ikonen för modellvyn.":::

1. Dra fältet **Date** (Datum) från tabellen Financials (Ekonomi) till fältet **Datum** i tabellen Calendar (Kalender) för att koppla tabellerna och skapa en *relation* mellan dem.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="Skärmbild av relationen mellan datumfält.":::

## <a name="build-your-report"></a>Bygga upp din rapport 

Nu när du har transformerat och läst in dina data är det dags att skapa rapporten. I fältrutan till höger ser du fälten i datamodellen som du skapade. 

Nu ska vi skapa den slutliga rapporten, en visualisering i taget. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="Skärmbild av alla element i rapporten, efter nummer.":::

### <a name="visual-1-add-a-title"></a>Visuellt objekt 1: Lägg till en rubrik 

1. Välj **Textruta** på menyfliken **Infoga**. Skriv ”Executive Summary – Finance Report” (Sammanfattning – ekonomisk rapport). 
1. Markera texten som du precis skrev. Välj teckenstorlek 20 och fetstil. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="Skärmbild av rubrikformatering.":::

1. Växla **Bakgrund** till **Av** i fönstret Visualiseringar. 
1. Ändra storlek på rutan så att den får plats på en rad. 

### <a name="visual-2-profit-by-date"></a>Visuellt objekt 2: Vinst efter datum 

Nu ska du skapa ett linjediagram för att se vilken månad och vilket år som hade störst vinst. 

1. Dra fältet **Profit** (Vinst) från fältrutan till ett tomt område på rapportarbetsytan. Som standard visas ett stapeldiagram med en kolumn, Profit (Vinst), i Power BI. 
1. Dra fältet **Date** (Datum) till samma visuella objekt. Stapeldiagrammet uppdateras så att vinsten för de två åren visas.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="Skärmbild som visar stapeldiagrammet över vinsten.":::

1. I avsnittet **Fält** i fönstret Visualiseringar väljer du listrutan för **axelns värde**. Ändra **Date** (Datum) från **Datumhierarki** till **Datum**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="Skärmbild av hur du ändrar Datumhierarki till Datum.":::

    Stapeldiagrammet uppdateras så att vinsten för varje månad visas.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="Skärmbild som visar stapeldiagrammet efter månad.":::

1. I fönstret Visualiseringar ändrar du visualiseringstypen till **Linjediagram**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="Skärmbild som visar hur du ändrar från stapeldiagram till linjediagram.":::

    Nu kan du enkelt se att vinsten var störst i december 2014.

### <a name="visual-3-profit-by-country"></a>Visuellt objekt 3: Vinst efter land 

Skapa en karta för att se vilket land som hade störst vinst.

1. Dra fältet **Country** (Land) från fältrutan till ett tomt område på rapportarbetsytan för att skapa en karta.
1. Dra fältet **Profit** (Vinst) till kartan.

    Power BI skapar ett visuellt kartobjekt med bubblor som representerar den relativa vinsten för varje plats. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="Skärmbild av hur du skapar ett diagram med en karta.":::

    Det ser ut att gå bättre i Europa än i Nordamerika. 

### <a name="visual-4-sales-by-product-and-segment"></a>Visuellt objekt 4: Försäljning efter produkt och segment 

Skapa ett stapeldiagram för att se vilka företag och segment företaget bör investera i.

1. Dra de två diagrammen som du har skapat och placera dem bredvid varandra i den övre halvan av arbetsytan. Spara lite plats på vänster sida av arbetsytan. 
1. Välj ett tomt område i den nedre halvan av rapportarbetsytan. 

1. Välj fälten **Sales** (Försäljning), **Product** (Produkt) och **Segment** i fältrutan. 

    Power BI skapar automatiskt ett grupperat stående stapeldiagram. 

1. Dra diagrammet så att det fyller området under de två diagrammen ovanför.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="Skärmbild av ett grupperat stående stapeldiagram.":::

    Det verkar som företaget bör fortsätta investera i Paseo-produkten och rikta in sig på segmenten Small Business (Mindre företag) och Government (Myndigheter).  

### <a name="visual-5-year-slicer"></a>Visuellt objekt 5: Utsnitt för år 

Utsnitt är ett bra verktyg för att filtrera fram ett specifikt urval i visualiseringarna på en rapportsida. I vårt exempel kan vi skapa ett utsnitt som visar prestanda för varje månad och år.  

1. Välj fältet **Date** (Datum) i fältrutan och dra det till det tomma området till vänster på arbetsytan. 
2. Välj **Utsnitt** i fönstret Visualiseringar. 
3. Välj listrutan i **Fält** i avsnittet Fält i fönstret Visualiseringar. Ta bort kvartal och dag så att endast år och månad är kvar. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="Skärmbild som visar hur du ändrar datumhierarkin.":::

4. Expandera varje år och ändra storlek på det visuella objektet så att alla månader visas.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="Skärmbild som visar ett utsnitt för datumhierarkin.":::

Nu, om din chef bara vill se data för 2013, kan du använda utsnittet för att snabbt växla mellan år eller specifika månader i varje år. 

### <a name="extra-credit-format-the-report"></a>Överkurs: Formatera rapporten

Om du vill förbättra rapporten med lite enklare formatering kan du prova funktionerna nedan. 

**Tema**

- Ändra temat till **Executive** på menyfliken **Visa**.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Skärmbild som visar hur du väljer temat Executive."::: 

**Förbättra visualiseringarna** 

Gör följande ändringar på fliken **Format** i fönstret Visualiseringar.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="Skärmbild som visar fliken Format i fönstret Visualiseringar.":::

1. Välj Visuellt objekt 2. Ändra **Rubriktext** till ”Profit by Month and Year” (Vinst efter månad och år) och **Textstorlek** till **16 punkter** i avsnittet **Rubrik**. Växla **Skugga** till **På**. 

1. Välj Visuellt objekt 3. Ändra **Tema** till **Gråskala** i avsnittet **Mappningsformat**. Ändra rubrikens **textstorlek** till **16 punkter** i avsnittet **Rubrik**. Växla **Skugga** till **På**.

1. Välj Visuellt objekt 4. Ändra rubrikens **textstorlek** till **16 punkter** i avsnittet **Rubrik**. Växla **Skugga** till **På**.

1. Välj Visuellt objekt 5. Växla **Visa alternativet ”Markera allt”** till **På** i avsnittet **Markeringskontroller**. Öka **Textstorlek** till **16 punkter** i avsnittet **Sidhuvud för utsnitt**. 

**Lägga till en bakgrundsform för rubriken**

1. Gå till menyfliken **Infoga** och välj **Former** > **Rektangel**. Placera rektangeln överst på sidan och ändra storleken till sidans bredd och rubrikens höjd. 
1. Ändra **Transparens** till **100 %** i avsnittet **Linje** i fönstret **Formatera figur**. 
1. Ändra **Fyllningsfärg** till **Temafärg 5 #6B91C9** (blå) i avsnittet **Fyll**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="Skärmbild som visar Temafärg 5.":::

1. Gå till fliken **Format** och välj **Flytta bakåt** > **Placera längst bak**. 
1. Markera texten i Visuellt objekt 1, rubriken, och ändra teckenfärgen till **Vit**. 

**Lägga till en bakgrundsform för visualisering 2 och 3**

1. Gå till menyfliken **Infoga**, välj **Former** > **Rektangel** och ändra storleken till bredden och höjden på Visuellt objekt 2 och 3. 
1. Ändra **Transparens** till **100 %** i avsnittet **Linje** i fönstret **Formatera figur**. 
1. Gå till fliken **Format** och välj **Flytta bakåt** > **Placera längst bak**. 

### <a name="finished-report"></a>Färdig rapport

Så här ser den slutliga formaterade rapporten ut:  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Skärmbild som visar den slutliga, formaterade rapporten.":::

Den här rapporten ger svar på chefens viktigaste frågor: 

- Vilken månad och vilket år var vinsten störst? 

    December 2014 

- Var är försäljningen störst? 

    I Europa, särskilt i Frankrike och Tyskland. 

- Vilken produkt och vilket segment bör företaget fortsätta investera i? 

    Företaget bör fortsätta investera i Paseo-produkten och rikta in sig på mindre företag och myndigheter. 

## <a name="save-your-report"></a>Spara rapporten

- Välj **Spara** på **Arkiv**-menyn.

## <a name="publish-to-the-power-bi-service-to-share"></a>Dela rapporten genom att publicera den till Power BI-tjänsten 

Om du vill dela rapporten med din chef och dina kollegor publicerar du den till Power BI-tjänsten. När du delar rapporten med kollegor som har ett Power BI-konto kan de interagera med rapporten, men de kan inte spara ändringar. 

1. Välj **Publicera** på menyfliken **Start** i Power BI Desktop. 

    Du kan behöva logga in till Power BI-tjänsten. Om du inte redan har ett konto kan du registrera dig för en [kostnadsfri utvärdering](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Välj ett mål, t.ex. **Min arbetsyta** i Power BI-tjänsten > **Välj**.
1. Välj **Öppna ”filens namn” i Power BI**.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Skärmbild som visar hur du öppnar rapporten i Power BI-tjänsten.":::

    Den färdiga rapporten öppnas i webbläsaren.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Skärmbild som visar Power BI-rapporten i Power BI-tjänsten."::: 

1. Välj **Dela** överst i rapporten för att dela rapporten med andra.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Skärmbild som visar hur du delar rapporten från Power BI-tjänsten.":::

## <a name="next-steps"></a>Nästa steg

- [Självstudie: Analysera försäljningsdata från Excel och en OData-feed](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

Har du fler frågor? [Testa Power BI Community](https://community.powerbi.com/).
