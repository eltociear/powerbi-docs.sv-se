---
title: 'Självstudie: Kombinera data från Excel och en OData-feed i Power BI Desktop'
description: 'Självstudie: Kombinera data från Excel och en OData-feed'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 2ef73377728703926ac6bc51f847a54451e1321e
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878714"
---
# <a name="tutorial-analyze-sales-data-from-excel-and-an-odata-feed"></a>Självstudie: Analysera försäljningsdata från Excel och en OData-feed

Det är vanligt att ha data i flera datakällor. Du kan till exempel ha två databaser, en för produktinformation och en annan för försäljningsinformation. Med *Power BI Desktop*, kan du kombinera data från olika källor för att skapa intressanta, attraktiva dataanalyser och visualiseringar.

I den här självstudien får du lära dig att kombinera data från två datakällor:

* En Excel-arbetsbok med produktinformation
* Ett OData-flöde med orderdata

Du kommer att importera datauppsättningarna och utföra transformering och aggregering. Sedan använder du data från de två datakällorna till att skapa en säljanalysrapport med interaktiva visualiseringar. Senare kan du även använda de här teknikerna för SQL Server-frågor, CSV-filer och andra datakällor i Power BI Desktop.

>[!NOTE]
>I Power BI Desktop finns det flera sätt att utföra en åtgärd. Du kan till exempel högerklicka på eller använda menyn **Fler alternativ** på en kolumn eller cell om du vill se fler val i menyfliksområdet. Flera alternativa metoder beskrivs i stegen nedan.

## <a name="import-excel-product-data"></a>Importera produktdata från Excel

Importera först produktdata från Excel-arbetsboken *Products.xlsx* till Power BI Desktop.

1. [Ladda ned Excel-arbetsboken Products.xlsx](https://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) och spara den som *Products.xlsx*.

1. Välj pilen bredvid **Hämta data** i menyfliksområdet **Start** i Power BI Desktop och välj sedan **Excel** på menyn **Vanligaste**.

   ![Hämta data](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)

   >[!NOTE]
   >Du kan också välja själva objektet **Hämta data** eller välja **Hämta data** från Power BI-dialogrutan **Kom igång**, välj sedan **Excel** eller **Fil** > **Excel** i dialogrutan **Hämta data** och välj sedan **Anslut**.

1. I dialogrutan **Öppna** navigerar du till och väljer filen **Products.xlsx** och välj sedan **Öppna**.

1. I fönstret **Navigatör** markerar du tabellen **Produkter** och väljer sedan **Transformera data**.

   ![Navigatorfönstret för Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

En förhandsgranskning av tabellen öppnas i Power Query-redigeraren, där du kan använda transformeringar till att rensa data.

![Power Query Editor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)

>[!NOTE]
>Du kan också öppna Power Query-redigeraren genom att välja **Redigera frågor** > **Redigera frågor** från menyfliken **Start** i Power BI Desktop eller genom att högerklicka eller välja **Fler alternativ** bredvid någon fråga i **Rapportvyn** och välja **Redigera fråga**.

## <a name="clean-up-the-products-columns"></a>Rensa produktkolumner

I den kombinerade rapporten används kolumnerna **ProductID**, **ProductName**, **QuantityPerUnit** och **UnitsInStock** från Excel-arbetsboken. Du kan ta bort de andra kolumnerna.

1. Använd Power Query-redigeraren och välj kolumnerna **ProductID**, **ProductName**, **QuantityPerUnit** och **UnitsInStock**. Du kan använda Ctrl för att välja mer än en kolumn eller Skift för att välja kolumner intill varandra.

1. Högerklicka på någon av de markerade rubrikerna. Välj **Ta bort andra kolumner** på den nedrullningsbara menyn.
   Du kan också välja **Ta bort kolumner** > **Ta bort andra kolumner** från gruppen **Hantera kolumner** i menyfliken **Start**.

   ![Ta bort andra kolumner](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-odata-feeds-order-data"></a>Importera orderdata från OData-flödet

Importera sedan beställningsdata från exemplet på försäljningssystemet Northwind OData-feed.

1. Använd Power Query-redigeraren och välj **Ny källa**. På menyn **Vanligaste** väljer du **OData-feed**.

   ![Hämta OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)

1. I dialogrutan **OData-flöde** klistrar du in webbadressen till Northwind OData-flödet, `https://services.odata.org/V3/Northwind/Northwind.svc/`. Välj **OK**.

   ![Dialogrutan OData-feed](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)

1. I **Navigatör** väljer du tabellen **Beställningar** och väljer sedan **Transformera data** för att läsa in data till Power Query-redigeraren.

   ![Navigatör för OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)

   >[!NOTE]
   >I **Navigator**, kan du välja alla tabellnamn utan att markera kryssrutan om du vill visa en förhandsgranskning.

## <a name="expand-the-order-data"></a>Expandera beställningsdata

Du kan använda tabellreferenser till att skapa frågor när du ansluter till datakällor som har flera tabeller, som relationsdatabaser eller Northwind OData-flödet. Tabellen **Beställningar** innehåller referenser till flera relaterade tabeller. Du kan använda åtgärden Expandera när du ska lägga till kolumnerna **ProductID**, **UnitPrice** och **Quantity** från den relaterade tabellen **Order_Details** i måltabellen (**Orders**).

1. Bläddra till höger i tabellen **Orders** tills du ser kolumnen **Order_Details**. Den innehåller referenser till en annan tabell snarare än faktiska data.

   ![Kolumnen Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/order-details-column.png)

1. Välj ikonen **Expandera** (![Expandera-ikon](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) i kolumnrubriken **Order_Details**.

1. Gör följande i den nedrullningsbara menyn:

   1. Välj **(Välj alla kolumner)** ta bort alla kolumner.

   1. Välj **ProductID**, **UnitPrice** och **Quantity**, och välj sedan **OK**.

      ![Expandera den nedrullningsbara menyn](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand-drop-down-menu.png)

När du har expanderat tabellen **Order_Details** ersätter tre nya kapslade tabellkolumner kolumnen **Order_Details**. Tabellen får nya rader för varje ny order.

![Utökade kolumner](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expanded-columns.png)

## <a name="create-a-custom-calculated-column"></a>Skapa en anpassad beräknad kolumn

Med Power Query Editor kan du skapa beräkningar och anpassade fält för att utöka dina data. Du skapar en anpassad kolumn som multiplicerar enhetspriset med antalet artiklar för att beräkna det totala priset för varje radpost i ordern.

1. I menyfliksområdet **Lägg till kolumn** i Power Query Editor väljer du **Anpassad kolumn**.

   ![Lägga till en anpassad kolumn](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/adding-a-custom-column.png)

1. I dialogrutan **Anpassad kolumn** skriver du **LineTotal** i fältet **Nytt kolumnnamn**.

1. I fältet **Anpassad kolumnformel** efter **=** , anger du **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . Du kan också välja fältnamn från rullningsrutan **Tillgängliga kolumner** och välja **<< Infoga**, i stället för att skriva dem.

1. Välj **OK**.

   ![Dialogrutan Anpassad kolumn](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/custom-column-dialog-box.png)

   Det nya fältet **LineTotal** visas som den sista kolumnen i tabellen **Beställningar**.

## <a name="set-the-new-fields-data-type"></a>Ange en datatyp för det nya fältet

När Power Query Editor ansluter till data görs en kvalificerad gissning om varje fälts datatyp i visningssyfte. En rubrikikon indikerar den tilldelade datatypen för varje fält. Du kan också leta **Datatyp** i menyfliksområdet **Start**, i gruppen **Transformera**.

Den nya kolumnen **LineTotal** har datatypen **Valfri**, men den innehåller valutavärden. Om du vill tilldela en datatyp högerklickar du på kolumnrubriken **LineTotal**, väljer **Ändra datatyp** från den nedrullningsbara menyn och väljer sedan **Fast decimaltal**.

![Ändra datatypen till fast decimal](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/change-data-type-to-fixed-decimal.png)

>[!NOTE]
>Du kan också välja kolumnen **LineTotal**, välj sedan pilen bredvid **Datatyp** i området **Transformera** på menyfliken **Start** och markera sedan **Fast decimaltal**.

## <a name="clean-up-the-orders-columns"></a>Rensa beställningskolumner

För att göra modellen enklare att arbeta med i rapporter kan du ta bort, byta namn på och ändra ordning på kolumnerna.

Följande kolumner används i rapporten:

* **OrderDate**
* **ShipCity**
* **ShipCountry**
* **Order_Details.ProductID**
* **Order_Details.UnitPrice**
* **Order_Details.Quantity**
* **LineTotal**

Välj de här kolumnerna och använd **Ta bort andra kolumner** som du gjorde med dina Excel-data tidigare. Du kan också markera övriga kolumner, högerklicka på en av dem och välja **Ta bort kolumner**.

Du kan byta namn på kolumnerna som föregås av prefixet ”**Order_Details.** ” så att de blir enklare att läsa:

1. Dubbelklicka eller tryck och håll kvar på respektive kolumnrubrik, eller högerklicka på kolumnrubriken och välj **Byt namn** från den nedrullningsbara menyn.

1. Ta bort **Order_Details.** prefix från varje namn.

Slutligen för att göra kolumnen **LineTotal** enklare att komma åt, dra och släpp den till vänster, precis till höger om kolumnen **ShipCountry**.

![Rensad tabell](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/cleaned-up-table.png)

## <a name="review-the-query-steps"></a>Gå igenom frågestegen

Dina Power Query Editor-åtgärder för att utforma och transformera data registreras. Varje åtgärd visas till höger i fönstret **Frågeinställningar** under **Tillämpade steg**. Du kan gå tillbaka genom **Tillämpade steg** om du vill gå igenom stegen och redigera, ta bort eller ordna om dem om det behövs. Det är dock riskabelt att ändra tidigare steg eftersom det kan göra att senare steg inte fungerar.

Välj var och en av dina frågor i listan **Frågor** till vänster i Power Query Editor och granska **Tillämpade steg** i **Frågeinställningar**. När du har tillämpat datatransformationerna ska **Tillämpade steg** för dina två frågor se ut så här:

![Tillämpade steg för produktfrågor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/products-query-applied-steps.png) &nbsp;&nbsp; ![Tillämpade steg för beställningsfrågor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orders-query-applied-steps.png)

>[!TIP]
>Under Tillämpade steg finns formler som skrivits i *Power Query Language*, även kallat [M-språk](https://docs.microsoft.com/powerquery-m/power-query-m-reference). Om du vill se och redigera formlerna, välj **Avancerad redigerare** i gruppen **Fråga** på fliken **Start** i menyfliksområdet.

## <a name="import-the-transformed-queries"></a>Importera omvandlade frågor

När du är nöjd med dina transformerade data och vill importera dem till **rapportvyn** i Power BI väljer du **Stäng och tillämpa** > **Stäng och tillämpa** på **Start**-menyfliksområdets grupp **Stäng**.

![Stäng och använd](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

När data har lästs in ser du frågorna i listan **Fält** i Power BI Desktop-**rapportvyn**.

![Frågor i fältlistan](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/queries-in-fields-list.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Hantera relationen mellan datauppsättningar

Med Power BI Desktop behöver du inte kombinera frågor för att rapportera om dem. Du kan dock använda relationerna mellan datamängder som baseras på gemensamma fält för att utöka och förbättra dina rapporter. Power BI Desktop kan identifiera relationer automatiskt och du kan skapa dem i Power BI Desktop-dialogrutan **Hantera relationer**. Mer information finns i [Skapa och hantera relationer i Power BI Desktop](../transform-model/desktop-create-and-manage-relationships.md).

Det delade fältet `ProductID` skapar en relation mellan datamängderna `Orders` och `Products` i den här självstudien.

1. I Power BI Desktop **-rapportvyn** väljer du **Hantera relationer** i området **Relationer** i menyfliksområdet **Start**.

   ![Menyfliksområdet Hantera relationer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)

1. I dialogrutan **Hantera relationer** ser du att Power BI Desktop redan har identifierat och en angett en aktiv relation mellan tabellerna **Products** och **Orders**. Om du vill visa relationen, välj **Redigera**.

   ![Dialogrutan Hantera relationer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)

   **Redigera relation** öppnas och visar information om relationen.  

   ![Dialogrutan Redigera relation](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)

1. Power BI Desktop har identifierat relationen automatiskt, så du kan välja **Avbryt** och sedan **Stäng**.

Välj **Modell** till vänster i Power BI Desktop för att visa och hantera frågerelationer. Dubbelklicka på pilen på raden som kopplar samman de två frågorna för att öppna dialogrutan **Redigera relation** och visa eller ändra relationen.

![Relationsvy](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

För att gå tillbaka till **rapportvyn** från **modellvyn** väljer du ikonen **Rapport**.

![Ikonen Rapportvy](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Skapa visualiseringar med hjälp av dina data

Du kan skapa olika visualiseringar i rapportvyn i Power BI Desktop för att få insikter om data. Rapporter kan ha flera sidor och på varje sida kan det finnas flera visuella objekt. Du och andra kan interagera med dina visualiseringar för att analysera och förstå dina data. Mer information finns i [Interagera med en rapport i redigeringsvyn i Power BI-tjänsten](../create-reports/service-interact-with-a-report-in-editing-view.md).

Du kan använda både dina datauppsättningar, och relationen mellan dem, för att visualisera och analysera dina försäljningsdata.

Skapa först ett stående stapeldiagram som använder fälten från båda frågorna för att visa kvantitet för varje produkt som beställts.

1. Välj fältet **Kvantitet** från **Beställningar** i rutan **Fält** till höger eller dra det till ett tomt utrymme på arbetsytan. Nu skapas ett stapeldiagram som visar det totala antalet produkter som har beställts.

1. Välj **ProductName** från **Products** i fönstret **Fält** eller dra den till diagrammet för att visa antalet av varje produkt som har beställts.

1. Om du vill sortera produkterna efter flest till minst beställda väljer du ellipsen **Fler alternativ** ( **...** ) längst upp till höger om visualiseringen och väljer sedan **Sortera efter antal**.

1. Använd handtagen i diagrammets hörn för att göra det större så fler produktnamn visas.

   ![Liggande stapeldiagram för Antal efter ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/quantity-by-productname-bar-chart.png)

Skapa sedan ett diagram som visar beställt belopp i dollar (**LineTotal**) över tid (**OrderDate**).

1. Utan att ha valt något på arbetsytan, välj **LineTotal** från **Beställningar** i rutan **Fält** eller dra den till ett tomt utrymme på arbetsytan. Stapeldiagrammet visar totalt värde i dollar för alla beställningar.

1. Markera stapeldiagrammet och välj **OrderDate** från **Orders** eller dra den till diagrammet. Diagrammet visar nu summan för varje beställningsdatum.

1. Dra i hörnen om du vill ändra storlek på visualiseringen och se mer data.

   ![Linjediagram för LineTotals efter OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-orderdate-line-chart.png)

   >[!TIP]
   >Om du bara ser **År** i diagrammet och endast tre datapunkter markerar du pilen bredvid **OrderDate** i fältet **Axel** i fönstret **Visualiseringar** och väljer **OrderDate** i stället för **Datumhierarki**.

Skapa slutligen en kartvisualisering som visar beställningsbelopp från varje land.

1. Utan att ha valt något på arbetsytan, välj **ShipCountry** från **Beställningar** i rutan **Fält** eller dra den till ett tomt utrymme på arbetsytan. Power BI Desktop identifierar data som landsnamn. Sedan skapas automatiskt en kartvisualisering med en datapunkt för varje land som har beställningar.

1. Om du vill att datapunkternas storlek ska återge orderbeloppen för respektive land drar du fältet **LineTotal** till kartan. Du kan också dra det till **Dra datafält hit** under **Storlek** i fönstret **Visualiseringar**. Storleken på cirkel i kartan avspeglar nu beställningsbeloppet från varje land.

   ![Kartvisualisering för LineTotals efter Leveransland](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-shipcountry-map-visualization.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagera med visuella objekt i rapporten för att analysera närmare

I Power BI Desktop kan du interagera med visuella objekt som korsmarkerar och filtrerar varandra för att upptäcka fler trender. Mer information finns i [Filter och markeringar i Power BI-rapporter](../create-reports/power-bi-reports-filters-and-highlighting.md).

På grund av relationen mellan dina frågor påverkar interaktioner med en visualisering alla andra visualiseringar på sidan.

I kartvisualiseringen, markera cirkeln som är centrerad i **Kanada**. De andra två visualiseringarna filtrerar fram ett fokus på radsummor och beställningskvantiteter för Kanada.

![Försäljningsdata filtrerade för Kanada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/sales-data-filtered-for-canada.png)

Välj diagramprodukten **Quantity per ProductName** för att se kartan och datumdiagramfiltret som visar data för den aktuella produkten. Välj diagramdatumet **LineTotal per OrderDate** för att se kartan och produktdiagramfiltret som visar data för det aktuella datumet.

>[!TIP]
>Om du vill avmarkera en markering väljer du den igen eller väljer en av andra visualiseringar.

## <a name="complete-the-sales-analysis-report"></a>Slutför analysrapporten för försäljning

I din färdiga rapport kombineras data från Excel-filen *Products.xlsx* och Northwind OData-flödet i visuella objekt som hjälper dig att analysera orderinformationen för olika länder, tidsramar och produkter. När rapporten är klar, kan du [överföra den till Power BI-tjänsten](../create-reports/desktop-upload-desktop-files.md) för att dela den med andra Power BI-användare.

## <a name="next-steps"></a>Nästa steg

* [Läs andra Power BI Desktop-självstudier](/power-bi/guided-learning/)
* [Se Power BI Desktop-videor](/power-bi/fundamentals/desktop-videos)
* [Besök Power BI-forumet](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Läs Power BI-bloggen](https://go.microsoft.com/fwlink/?LinkID=519327)
