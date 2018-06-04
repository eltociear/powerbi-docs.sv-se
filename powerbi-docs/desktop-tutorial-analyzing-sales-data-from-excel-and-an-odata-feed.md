---
title: 'Självstudie: Kombinera data från Excel och en OData-feed i Power BI Desktop'
description: 'Självstudier: Kombinera data från Excel och en OData-feed'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: c6cd75efd44259c2812f98a37875cf716d4843ad
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34456213"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Självstudier: Kombinera försäljningsdata från Excel och en OData-feed

Det är vanligt att sprida data över flera datakällor, såsom produktinformation i en databas och försäljningsinformation i en annan. Med **Power BI Desktop**, kan du kombinera data från olika källor för att skapa intressanta, attraktiva dataanalyser och visualiseringar. 

I den här självstudien kommer du att lära dig att kombinera data från två datakällor: en Excel-arbetsbok som inkluderar produktinformation och en OData-feed som innehåller beställningsdata. Efter att du har importerat varje datauppsättning och utfört omvandlingar och sammanslagningar, använder du data från båda källorna för att skapa en försäljningsanalysrapport med interaktiva visualiseringar. De här teknikerna kan också tillämpas till SQL Server-frågor, CSV-filer och alla andra datakällor i Power BI Desktop.

>[!NOTE]
>I Power BI Desktop finns det flera sätt att utföra en åtgärd. Till exempel finns många menyfliksområdesval också tillgängliga genom att högerklicka eller via menyn **Fler alternativ** i en kolumn eller cell. Flera alternativa metoder beskrivs i stegen nedan. 

## <a name="import-the-product-data-from-excel"></a>Importera produktdata från Excel

Importera först produktdata från Excel-arbetsboken Products.xlsx till Power BI Desktop.

1. [Hämta Excel-arbetsboken Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) och spara den som **Products.xlsx**.
   
2. Välj den nedrullningsbara pilen bredvid **Hämta data** i fliken **Start** för Power BI Desktop-menyfliksområdet och välj sedan **Excel** från listrutan **Vanligaste**. 
   
   ![Hämta data](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >Du kan också välja själva objektet **Hämta data** eller välja **Hämta data** från Power BI-dialogrutan **Kom igång**, välj sedan **Excel** eller **Fil** > **Excel** i dialogrutan **Hämta data** och välj sedan **Anslut**.
   
3. I dialogrutan **Öppna** navigerar du till och väljer filen **Products.xlsx** och välj sedan **Öppna**.
   
4. I fönstret **Navigator** markerar du tabellen **Produkter** och väljer sedan **Redigera**.
   
   ![Navigatorfönstret för Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
En förhandsgranskning av tabellen öppnas i **Power Query Editor**, där du kan använda omvandlingar för att rensa data. 
   
![Power Query Editor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>Du kan också öppna **Power Query Editor** genom att välja **Redigera frågor** > **Redigera frågor** från menyfliken **Start** i Power BI Desktop eller genom att högerklicka eller välja **Fler alternativ** bredvid någon fråga i **Rapportvyn**, och välja **Redigera fråga**.

## <a name="clean-up-the-products-columns"></a>Rensa produktkolumner

Din kombinerade rapport kommer endast att använda kolumnerna **ProductID**, **ProductName**, **QuantityPerUnit** och **UnitsInStock** från Excel-arbetsboken så kan du ta bort de andra kolumnerna. 

1. I **Power Query Editor**, välj kolumnerna **ProductID**, **ProductName**, **QuantityPerUnit**, och **UnitsInStock** (använd **Ctrl**+**Klick** för att välja mer än en kolumn eller **SKIFT**+**Klick** för att välja kolumner som ligger intill varandra).
   
2. Högerklicka på någon av de markerade rubrikerna och välj **Ta bort andra kolumner** i listrutan för att ta bort alla utom de markerade kolumnerna från tabellen. 
   Du kan också välja **Ta bort kolumner** > **Ta bort andra kolumner** från gruppen **Hantera kolumner** i menyfliken **Start**. 
   
   ![Ta bort andra kolumner](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Importera beställningsdata från en OData-feed

Importera sedan beställningsdata från exemplet på försäljningssystemet Northwind OData-feed. 

1. I **Power Query Editor**, välj **Ny källa** och välj sedan **OData-feed** från listrutan **Vanligaste**. 
   
   ![Hämta OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. I dialogrutan **OData Feed** klistrar du in URL för Northwind ODat-feed, `http://services.odata.org/V3/Northwind/Northwind.svc/` och väljer **OK**.
   
   ![Dialogrutan OData-feed](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. I rutan **Navigator** väljer du tabellen **Beställningar** och väljer sedan **OK** för att läsa in data till **Power Query Editor**.
   
   ![Navigatorfönstret för OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >I **Navigator**, kan du välja alla tabellnamn utan att markera kryssrutan om du vill visa en förhandsgranskning.

## <a name="expand-the-order-data"></a>Expandera beställningsdata

När du ansluter till datakällor som har flera tabeller såsom relationsdatabaser eller Northwind OData-feed, kan du använda referenser mellan tabeller för att bygga upp dina frågor. Tabellen **Beställningar** innehåller referenser till flera relaterade tabeller. Du kan lägga till kolumnerna **ProductID**, **UnitPrice** och **Quantity** från den relaterade tabellen **Order_Details** i ämnesraden (tabellen **Beställningar**) med hjälp av åtgärden **Expandera**. 

1. Bläddra till höger i tabellen **Beställningar** tills du ser kolumnen **Order_Details**. Observera att i stället för data innehåller den referenser till en annan tabell.
   
   ![Kolumnen Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Välj ikonen **Expandera** (![Expandera-ikon](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) i kolumnrubriken **Order_Details**. 
   
3. I listrutan **Expandera**:
   
   1. Välj **(Välj alla kolumner)** ta bort alla kolumner.
      
   2. Välj **ProductID**, **UnitPrice** och **Quantity**, och välj sedan **OK**.
      
      ![Expandera dialogrutan](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

När du har expanderat tabellen **Order_Details** byts kolumnen **Order_Details** ut med tre nya kolumner från den kapslade tabellen och det finns nya rader i tabellen för de data som lagts till från varje beställning. 

![Utökade kolumner](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Skapa en anpassad beräknad kolumn

Med Power Query Editor kan du skapa beräkningar och anpassade fält för att utöka dina data. Du skapar en egen kolumn som beräknar det totala priset för varje radpost i en beställning genom att multiplicera enhetspriset med artikelantal.

1. I menyfliken **Add Column** i Power Query Editor, välj **Anpassad kolumn**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. I dialogrutan **Anpassad kolumn** skriver du **LineTotal** i fältet **Nytt kolumnnamn**.

3. I fältet **Anpassad kolumnformel** efter **=**, ange **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]**. (Du kan också välja fältnamn från rullningsrutan **Tillgängliga kolumner** och välja **<< Infoga**, i stället för att skriva dem.) 
3. Välj **OK**.
   
   ![Dialogrutan Anpassad kolumn](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

Det nya fältet **LineTotal** visas som den sista kolumnen i tabellen **Beställningar**.

## <a name="set-the-data-type-for-the-new-field"></a>Ange datatyp för det nya fältet

När Power Query Editor ansluter till data, avgörs bästa datatyp för varje fält och data visas i enlighet med detta. Du kan se de datatyper som tilldelats till fält via ikonerna i sidhuvuden eller under **Datatyp** i gruppen **Transformera** i menyfliken **Start**. 

Din nya kolumn **LineTotal** har datatypen **Alla**, men dess värden är valuta. Om du vill tilldela en datatyp, högerklicka på kolumnrubriken **LineTotal**, välj **Ändra datatyp** från listrutan och välj sedan **Fast decimaltal**. 

![Ändra datatyp](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>Du kan också välja kolumnen **LineTotal**, välj sedan den nedrullningsbara pilen bredvid **Datatyp** i området **Transformera** i menyfliken **Start** och markera sedan **Fast decimaltal**.

## <a name="clean-up-the-orders-columns"></a>Rensa beställningskolumner

För att göra din modell enklare att arbeta med i rapporter kan du ta bort, byta namn på och ändra ordning på kolumnerna.

Din rapport kommer endast att använda kolumnerna **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** och **Order_Details.Quantity**. Du kan välja dessa kolumner och använda **Ta bort andra kolumner** som du gjorde med Excel-data eller så kan du välja alla kolumner utom de listade, högerklicka på en av de markerade kolumnerna och välja **Ta bort kolumner** för att ta bort alla. 

Du kan göra kolumnerna **Order_Details.ProductID**, **Order_Details.UnitPrice** och **Order_Details.Quantity** enklare att identifiera genom att ta bort *Order_Details.* prefix från kolumnnamn. För att byta namn på kolumnerna till **ProductID**, **UnitPrice** och **Quantity**:

1. Dubbelklicka eller tryck på och håll nere varje kolumnrubrik eller högerklicka på kolumnrubriken och välj **Byt namn** i listrutan. 
2. Ta bort *Order_Details.* prefixet från varje namn och tryck sedan på **Retur**.

Slutligen för att göra kolumnen **LineTotal** enklare att komma åt, dra och släpp den till vänster, precis till höger om kolumnen **ShipCountry**.

![Rensad tabell](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>Gå igenom frågestegen

Medan du formade och omvandlade data i Power Query Editor registrerades varje steg i området **Tillämpade steg** i rutan **Frågeinställningar** till höger i Power Query Editor. Du kan gå tillbaka genom stegen som använts för att granska ändringar du gjort, och redigera, ta bort eller ordna om dem om det behövs (även om det kan vara riskabelt, eftersom en ändring av ovanstående steg kan skada senare steg). 

Välj var och en av dina frågor i listan **Frågor** till vänster i Power Query Editor och granska **Tillämpade steg** i **Frågeinställningar**. När du har använt tidigare datatransformationer bör de tillämpade stegen för dina två frågor se ut som följande:

![Tillämpade steg för produktfrågor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Tillämpade steg för beställningsfrågor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Under Tillämpade steg finns formler som skrivits i **Power Query-språk**, även kallat **M**-språk. Om du vill se och redigera formlerna, välj **Avancerad redigerare** i gruppen **Fråga** på fliken Start i menyfliksområdet. 

## <a name="import-the-transformed-queries"></a>Importera omvandlade frågor

När du är nöjd med dina transformerade data, välj **Stäng och tillämpa** > **Stäng och tillämpa** i gruppen **Stäng** i menyfliksområdet **Start**  för att importera data till Power BI Desktop-rapportvyn. 

![Stäng och använd](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

När data lästs in visas frågorna i listan **Fält** i Power BI Desktop-rapportvyn.

![Frågor i fältlistan](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Hantera relationen mellan datauppsättningar

Med Power BI Desktop behöver du inte kombinera frågor för att rapportera om dem. Du kan dock använda relationerna mellan datauppsättningar, baserat på fält de har gemensamt, för att utöka och förbättra dina rapporter. Power BI Desktop kan identifiera relationer automatiskt och du kan skapa dem i Power BI Desktop-dialogen **Hantera relationer**. Mer information om relationer i Power BI Desktop finns i [Skapa och hantera relationer](desktop-create-and-manage-relationships.md).

Datauppsättningar för beställningar och produkter i den här självstudien delar ett gemensam *ProductID*-fält, så det finns en relation mellan dem baserat på den kolumnen. 

1. I Power BI Desktop-rapportvyn, välj **Hantera relationer** i området **Relationer** i menyfliksområdet **Start**.
   
   ![Menyfliksområdet Hantera relationer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. I dialogrutan **Hantera relationer**, observera att Power BI Desktop redan har identifierat och en angett en aktiv relation mellan tabellerna Produkter och Beställningar. Om du vill visa relationen, välj **Redigera**. 
   
   ![Dialogrutan Hantera relationer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   Dialogrutan **Redigera relation** öppnas och visar information om relationen.  
   
   ![Dialogrutan Redigera relation](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. Power BI Desktop har automatiskt spårat relationen korrekt, så du kan välja **Avbryt** och sedan **Stäng** för att avsluta dialogrutorna för relationen.

Du kan också visa och hantera relationer mellan dina frågor genom att välja vyn **Relation** på vänster sida av fönstret för Power BI Desktop. Dubbelklicka på pilen på raden som ansluter de två frågorna för att öppna dialogrutan **Redigera relation** och visa eller ändra relationen. 

![Relationsvy](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

För att gå tillbaka till Rapportvyn från Relationsvyn, välj ikonen **Rapportvy**. 

![Ikonen Rapportvy](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Skapa visualiseringar med hjälp av dina data

I Power BI Desktop-rapportvyn kan du skapa en mängd olika visualiseringar för att få insikter från dina data. Du kan skapa rapporter med flera sidor och varje sida kan ha flera visuella objekt. Du och andra kan interagera med dina visuella objekt för att analysera och förstå dina data. Läs mer om att visa och redigera rapporter i Power BI-tjänsten (din plats) i [Redigera en rapport](service-interact-with-a-report-in-editing-view.md).

Du kan använda både dina datauppsättningar och relationen mellan dem för att visualisera och analysera dina försäljningsdata. 

Skapa först ett stående stapeldiagram som använder fälten från båda frågorna för att visa kvantitet för varje produkt som beställts. 

1. Välj fältet **Kvantitet** från **Beställningar** i rutan **Fält** till höger eller dra det till ett tomt utrymme på arbetsytan. Detta skapar ett stapeldiagram som visar det totala antalet av alla produkter som har beställts. 
   
2. Välj **ProductName** från **Produkter** i rutan **Fält** eller dra det till schemat för att visa kvantitet för varje produkt som beställts. 
   
3. Om du vill sortera produkterna efter flest till minst beställda, välj ellipsen (**...** ) **Fler alternativ** längst upp till höger om visualiseringen och välj sedan **Sortera efter antal**.
   
4. Använd handtagen i diagrammets hörn för att göra det större så fler produktnamn visas. 
   
   ![Liggande stapeldiagram för Antal efter ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Skapa sedan ett diagram som visar beställt belopp i dollar (**LineTotal**) över tid (**OrderDate**). 

1. Utan att ha valt något på arbetsytan, välj **LineTotal** från **Beställningar** i rutan **Fält** eller dra den till ett tomt utrymme på arbetsytan. Stapeldiagrammet visar totalt värde i dollar för alla beställningar. 
   
2. När schemat är markerat, välj **OrderDate** från **Beställningar**, eller drar det till diagrammet. Diagrammet visar nu summan för varje beställningsdatum. 
   
3. Ändra visualiseringen genom att dra i hörnen för att kunna se fler data. 
   
   ![Linjediagram för LineTotals efter OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Om du bara ser År i schemat (endast tre datapunkter) rulla ner pilen bredvid **OrderDate** i fältet **Axel** i fönstret **Visualiseringar** och välj **OrderDate** i stället för **Datumhierarki**. 

Skapa slutligen en kartvisualisering som visar beställningsbelopp från varje land. 

1. Utan att ha valt något på arbetsytan, välj **ShipCountry** från **Beställningar** i rutan **Fält** eller dra den till ett tomt utrymme på arbetsytan. Power BI Desktop upptäcker att data är Landsnamn och skapar automatiskt en kartvisualisering med en datapunkt för varje land som hade beställningar. 
   
2. Om du vill göra så att datapunkternas storlekar återspeglar beställningsbeloppet för varje land, dra fältet **LineTotal** till kartan (eller dra det till **Dra datafält hit** under **Storlek**i nedre halvan av fönstret **Visualiseringar**). Storleken på cirkel i kartan avspeglar nu beställningsbeloppet från varje land. 
   
   ![Kartvisualisering för LineTotals efter Leveransland](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagera med visuella objekt i rapporten för att analysera närmare

Power BI Desktop gör att du kan upptäcka ytterligare trender genom att interagera med visuella objekt som korsmarkerar och filtrerar varandra. Mer information finns i [Filtrering och markering i rapporter](power-bi-reports-filters-and-highlighting.md). 

På grund av relationen mellan dina frågor påverkar interaktioner med en visualisering alla andra visualiseringar på sidan. 

I kartvisualiseringen, markera cirkeln som är centrerad i **Kanada**. Observera att de andra två visualiseringarna filtrerar för att fokusera på radsumma och beställningskvantiteter för Kanada.

![Försäljningsdata filtrerade för Kanada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Om du väljer en av produkterna i diagrammet **Antal efter ProductName** filtreras kart- och datumdiagrammet för att återspegla data för denna produkt, och om du markerar ett datum i diagrammet **LineTotal efter OrderDate** filtreras kart- och produktdiagrammet för att visa data för detta datum. 
>[!TIP]
>Om du vill avmarkera en markering väljer du den igen eller väljer en av andra visualiseringar. 

## <a name="complete-the-sales-analysis-report"></a>Slutför analysrapporten för försäljning

Din färdiga rapport kombinerar data från Products.xlsx Excel-filen och Northwind OData-feeden i visuell information som hjälper till att analysera beställningsinformation för olika länder, tidsramar och produkter. När rapporten är klar, kan du [överföra den till Power BI-tjänsten](desktop-upload-desktop-files.md) för att dela den med andra Power BI-användare.

## <a name="next-steps"></a>Nästa steg
* [Läs andra Power BI Desktop-självstudier](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Se Power BI Desktop-videor](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Besök Power BI-forumet](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Läs Power BI-bloggen](http://go.microsoft.com/fwlink/?LinkID=519327)