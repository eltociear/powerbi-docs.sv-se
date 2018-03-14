---
title: "Självstudie: Analysera försäljningsdata från Excel och en OData-feed i Power BI Desktop"
description: "Självstudie: Analysera försäljningsdata från Excel och en OData-feed"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 4cab3ed114d03d42c6acf1bf62f70e7d920e16b2
ms.sourcegitcommit: d91b7bf18d5c504037134f375886633379f28ede
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2018
---
# <a name="tutorial-analyzing-sales-data-from-excel-and-an-odata-feed"></a>Självstudie: Analysera försäljningsdata från Excel och en OData-feed
Med **Power BI Desktop** kan du ansluta till alla typer av datakällor och sedan kombinera och forma dem på ett sätt som gör det lättare att skapa intressant dataanalys och visualiseringar. I den här kursen lär du dig hur du kombinerar data från två datakällor. 

Data är ofta fördelade över många datakällor, till exempel produktinformation i den databas och säljinformation i en annan. De tekniker som du lär dig i det här dokumentet omfattar en Excel-arbetsbok och en OData-feed, men dessa metoder kan användas för andra datakällor, som SQL Server-frågor, CSV-filer eller alla datakällor i Power BI Desktop.

I den här självstudien importerar du data från Excel (som innehåller produktinformation) och från OData (som innehåller beställningsdata). Du utför transformerings- och aggregeringssteg och kombinerar data från både källor för att skapa rapporten **totalförsäljning per produkt och år** som innehåller interaktiva visualiseringar. 

Den slutgiltiga produkten ser ut så här:

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

Du behöver produktarbetsboken för att följa stegen i den här självstudiekursen. Gör så här för att hämta den: **[Klicka här för att hämta Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**

I dialogrutan **Spara som** namnger du filen **Products.xlsx**.

## <a name="task-1-get-product-data-from-an-excel-workbook"></a>Aktivitet 1: Hämta produktdata från en Excel-arbetsbok
I den här uppgiften importerar du produkter från filen Products.xlsx till Power BI Desktop.

### <a name="step-1-connect-to-an-excel-workbook"></a>Steg 1: Anslut till en Excel-arbetsbok
1. Starta Power BI Desktop.
2. Välj Home-menyfliksområdet och välj **Hämta data**. Excel är en av de **vanligaste** dataanslutningarna så du kan välja den direkt från menyn **Hämta data**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
3. Om du klickar på Hämta data direkt, kan du också välja **Arkiv \> Excel** och välja **Connect.**
4. I dialogrutan **Öppna fil** markerar du filen **Products.xlsx**.
5. I fönstret **Navigator** markerar du tabellen **Produkter** och väljer sedan **Redigera**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

### <a name="step-2-remove-other-columns-to-only-display-columns-of-interest"></a>Steg 2: Ta bort övriga kolumner för att bara visa intressanta kolumner
I det här steget tar du bort alla kolumner utom **ProductID**, **ProductName**, **UnitsInStock** och **QuantityPerUnit**. I Power BI Desktop finns det flera sätt att utföra samma åtgärd. Många knappar i menyfliksområdet kan uppnås genom att använda snabbmenyn på en kolumn eller en cell.

Power BI Desktop innehåller frågeredigeraren där du formar och transformerar dina dataanslutningar. Frågeredigeraren öppnas automatiskt när du väljer **Redigera** från **Navigator**. Du gör detta genom att välja **Redigera frågor** från menyfliksområdet **Start** i Power BI Desktop. Följande steg utförs i frågeredigeraren.

1. Välj kolumnerna **ProductID**, **ProductName**, **QuantityPerUnit**, och **UnitsInStock** i frågeredigeraren (Använd  **ctrl + klicka** för att välja mer än en kolumn eller **Skift + klicka** för att välja kolumner som är bredvid varandra).
2. Välj **Ta bort kolumner** \> **Ta bort andra kolumner** från menyfliksområdet eller högerklicka på en kolumnrubrik och klicka på **Ta bort andra kolumner**.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_removeothercolumns.png)

### <a name="step-3-change-the-data-type-of-the-unitsinstock-column"></a>Steg 3: Ändra datatypen för kolumnen UnitsInStock
När frågeredigeraren ansluter till data går den igenom varje fält för att avgöra den bästa datatypen. För Excel-arbetsböcker ska produkter i lager ska alltid vara ett heltal. I det här steget bekräftar du att datatypen för kolumnen **UnitsInStock** är heltal.

1. Välj kolumnen **UnitsInStock**.
2. Välj den nedrullningsbara knappen **Datatyp** i menyfliksområdet **Start**.
3. Om den inte redan är ett heltal, väljer du **Heltal** för datatyp i listrutan (knappen **Datatyp:** visar även datatypen för den aktuella markeringen).
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_wholenumber.png)      

### <a name="power-bi-desktop-steps-created"></a>Power BI Desktop-steg som skapas
När du utför frågeaktiviteter i frågeredigeraren skapas och visas frågesteg i rutan **Frågeinställningar** i listan **Tillämpade steg**. Varje frågesteg har en motsvarande frågeformel, även kallat ”M”-språk. Läs mer om formelspråket ”M” i [Lär dig mer om Power BI formler](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

| Aktivitet | Frågesteg | Formel |
| --- | --- | --- |
| Anslut till en Excel-arbetsbok |Källa |Source{[Name="Products"]}[Data] |
| Omvandla den översta raden till tabellkolumnrubriker |FirstRowAsHeader |[Table.PromoteHeaders](https://support.office.com/Article/TablePromoteHeaders-b8eaeb95-042a-42e1-9164-6d3c646acadc "Table.PromoteHeaders") <br /> (Produkter) |
| Ta bort övriga kolumner för att bara visa intressanta kolumner |RemovedOtherColumns |[Table.SelectColumns](https://support.office.com/Article/TableSelectColumns-20bb9e28-9fd3-4cd2-a21b-97972c82ec22 "Table.SelectColumns")  <br />(FirstRowAsHeader,{"ProductID", "ProductName", "QuantityPerUnit", "UnitsInStock"}) |
| Ändra datatyp |Ändrade typ |Table.TransformColumnTypes(\#"Removed Other Columns",{{"UnitsInStock", Int64.Type}}) |

## <a name="task-2-import-order-data-from-an-odata-feed"></a>Aktivitet 2: Importera ordningsdata från en OData-feed
I den här aktiviteten ordnar du data. Detta steg representerar anslutning till ett försäljningssystem. Du kan importera data till Power BI Desktop från exemplet Northwind OData-feed på följande URL som du kan kopiera (och klistra in) i stegen nedan: <http://services.odata.org/V3/Northwind/Northwind.svc/> 

### <a name="step-1-connect-to-an-odata-feed"></a>Steg 1: Anslut till en OData-feed
1. Från menyfliken **Start** i frågeredigeraren väljer du **Hämta data.**
2. Bläddra till datakällan **OData-Feed**.
3. I dialogrutan **OData-Feed** klistrar du in **URL:en** för Northwind OData-feeden.
4. Välj **OK**.
5. I fönstret **Navigator** markerar du tabellen **Beställningar** och väljer sedan **Redigera**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_odatafeed.png)

>[!NOTE]
>Du kan klicka på en tabell utan att markera kryssrutan om du vill visa en förhandsgranskning.

### <a name="step-2-expand-the-orderdetails-table"></a>Steg 2: Visa tabellen Beställnings\_Information
Tabellen **Beställningar** innehåller en referens till en **information**stabell som innehåller de enskilda produkter som ingick i varje Beställning. När du ansluter till datakällor med flera tabeller (till exempel en relationsdatabas) använder du dessa referenser för att bygga upp din fråga. 

I det här steget kan du expandera tabellen **beställnings\_information** som är kopplad till **beställnings**tabellen för att kombinera kolumnerna **ProductID**, **Enhetspris** och **kvantitet** från **beställnings\_information** till tabellen **Beställningar**. Det här är en representation av data i dessa tabeller:

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orderdetails.png)

Åtgärden **Expandera** kombinerar kolumner från en relaterad tabell till en ämnestabell. När frågan körs kombineras rader från den relaterade tabellen (**Order\_Details**) till rader från ämnestabellen (**Beställningar**).

När du har expanderat tabellen **Order\_Details** läggs tre nya kolumner och ytterligare rader till i tabellen **Beställningar**, en för varje rad i den kapslade eller relaterade tabellen.

1. I **frågevyn**, bläddra till kolumnen **Order\_Details**.
2. I kolumnen **Order\_Details** väljer du ikonen för Expandera (![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)).
3. I listrutan **Expandera**:
   1. Välj **(Välj alla kolumner)** ta bort alla kolumner.
   2. Välj **ProductID**, **Enhetspris** och **Kvantitet**.
   3. Klicka på **OK**.
      ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)

### <a name="step-3-remove-other-columns-to-only-display-columns-of-interest"></a>Steg 3: Ta bort övriga kolumner för att bara visa intressanta kolumner
I det här steget du ta bort alla kolumner utom **OrderDate, ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** och **Order\_Details.Quantity**. I föregående uppgift använde du **Ta bort andra kolumner**. Ta bort markerade kolumner för den här uppgiften.

1. I **frågevyn** markerar du alla kolumner genom att slutföra a. och b.:
   1. Klicka på den första kolumnen (**OrderID**).
   2. Skift + klicka på den sista kolumnen (**leverantör**).
   3. Nu när alla kolumner har valts kan du använda ctrl + klicka för att avmarkera följande kolumner: **OrderDate**, **ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** och **Order\_Details.Quantity**.
2. Nu när endast de kolumner som vi vill ta bort är markerade högerklickar du på alla valda kolumnrubriker och klickar på **Ta bort kolumner**.

### <a name="step-4-calculate-the-line-total-for-each-orderdetails-row"></a>Steg 4: Beräkna den totala raden för varje Order\_Details-rad
Med Power BI Desktop kan du skapa beräkningar baserat på kolumnerna som du importerar och utöka de data som du ansluter till. I det här steget skapar du en **anpassad kolumn** för att beräkna radsumman för varje **beställnings\_information**-rad.

Beräkna den totala raden för varje **beställnings\_information**-rad:

1. I bandfliken **Add Column** klickar du på **Lägg till** **Anpassad kolumn**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. I dialogrutan **Lägg till anpassad kolumn** i textrutan **Egen kolumnformel** anger du **[Order\_Details.UnitPrice] \* [Order\_ Details.Quantity]**.
3. I textrutan **Nytt kolumnnamn** anger du **LineTotal**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)
4. Klicka på **OK**.

### <a name="step-5-set-the-datatype-of-the-linetotal-field"></a>Steg 5: Ange datatyp för fältet LineTotal
1. Högerklicka på kolumnen **LineTotal**.
2. Välj **Ändra typ** och välj **Decimalnummer**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

### <a name="step-6-rename-and-reorder-columns-in-the-query"></a>Steg 6: Byt namn på och ändra ordningen på kolumnerna i frågan
I det här steget har du gjort det enkelt att arbeta med modellen när du skapar rapporter genom att byta namn på de sista kolumnerna och ändra deras inbördes ordning.

1. I **frågeredigeraren** drar du kolumnen **LineTotal** till vänster efter **ShipCountry**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
2. Ta bort prefixet *Order\_Details.* prefixet från kolumnerna **Order\_Details.ProductID**, **Order\_Details.UnitPrice** och **Order\_Details.Quantity** genom att dubbelklicka på varje kolumnrubrik och sedan ta bort texten från kolumnnamnet.

### <a name="power-bi-desktop-steps-created"></a>Power BI Desktop-steg som skapas
När du utför frågeaktiviteter i frågeredigeraren skapas och visas frågesteg i rutan **Frågeinställningar** i listan **Tillämpade steg**. Varje frågesteg har en motsvarande Power Query-formel, även kallat ”M”-språk. Läs mer om formelspråket i [Lär dig mer om Power BI formler](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f "Läs mer om Power Query-formler").

| Aktivitet | Frågesteg | Formel |
| --- | --- | --- |
| Anslut till en OData-feed |Källa |Source{[Name="Orders"]}[Data] |
| Visa tabellen Order\_Details |Expandera Order\_Details |[Table.ExpandTableColumn](https://support.office.com/Article/TableExpandTableColumn-54903f25-75a2-4a44-a9a3-52a9d895ee98 "Table.ExpandTableColumn") <br /> (Orders, "Order\_Details", {"ProductID", "UnitPrice", "Quantity"}, {"Order\_Details.ProductID", "Order\_Details.UnitPrice", "Order\_Details.Quantity"}) |
| Ta bort övriga kolumner för att bara visa intressanta kolumner |RemovedColumns |[Table.RemoveColumns](https://support.office.com/Article/TableRemoveColumns-6265190e-2f58-4300-85b8-df88fc1a67d3 "Table.RemoveColumns") <br />(\#"Expand Order\_Details",{"OrderID", "CustomerID", "EmployeeID", "RequiredDate", "ShippedDate", "ShipVia", "Freight", "ShipName", "ShipAddress", "ShipCity", "ShipRegion", "ShipPostalCode", "ShipCountry", "Customer", "Employee", "Shipper"}) |
| Beräkna den totala raden för varje Order\_Details-rad |InsertedColumn |[Table.AddColumn](https://support.office.com/Article/TableAddColumn-6c64d0a5-9654-4d15-bfb6-9cc380aaf3c0 "Table.AddColumn") <br /> (RemovedColumns, "Custom", each [Order\_Details.UnitPrice] \* [Order\_Details.Quantity]) |

## <a name="task-3-combine-the-products-and-total-sales-queries"></a>Aktivitet 3: Kombinera frågorna produkter och totalförsäljning
Med Power BI Desktop behöver du inte kombinera frågor för att rapportera om dem. Skapa i stället **Relationer** mellan datauppsättningar. Dessa relationer kan skapas på alla kolumner som är gemensamma för dina datauppsättningar. Mer information finns i [Skapa och hantera relationer](desktop-create-and-manage-relationships.md).

I den här självstudiekursen har vi data om beställningar och produkter som delar ett gemensamt 'ProductID'-fält. Vi måste se till att det finns en relation mellan dem i modellen som vi använder med Power BI Desktop. Ange bara i Power BI Desktop att kolumnerna i varje tabell är relaterade (dvs. kolumner som har samma värden). Power BI Desktop avgör relationens riktning och kardinalitet. I vissa fall kan identifieras även relationerna automatiskt.

I det här steget bekräftar du en relation i Power BI Desktop mellan frågorna **Produkter** och **Totalförsäljning**.

### <a name="step-1-confirm-the-relationship-between-products-and-total-sales"></a>Steg 1: Kontrollera relationen mellan produkter och totalförsäljning
1. Vi måste först läsa in modellen som vi skapade i frågeredigeraren till Power BI Desktop. Från menyfliken **Start** i frågeredigeraren väljer du **Stäng och överför**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. Power BI Desktop läser in data från båda frågor.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)      
3. När data har lästs in, markerar du knappen **Hantera relationer** i menyfliksområdet **Start**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
4. Välj **Nytt...** knapp
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
5. När vi försöker skapa en relation kan vi se att det redan finns en! Enligt dialogrutan **Skapa relation** (med skuggade kolumner) har fältet **ProductsID** i varje fråga redan en upprättad relation.
   
    ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)
6. Välj **Avbryt** och välj sedan vyn **Relation** i Power BI Desktop.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
7. Vi kan se följande vilket visualiserar relationen mellan frågorna.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)
8. När du dubbelklickar på pilen på raden som ansluter den till frågor visas **Redigera relation**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)
9. Vi behöver inte göra några ändringar, så vi väljer helt enkelt **Avbryt** för att stänga dialogrutan **Redigera relation**.

## <a name="task-4-build-visuals-using-your-data"></a>Aktivera 4: Skapa visuella objekt med data
Med Power BI Desktop kan du skapa en mängd olika visualiseringar och få insikter från dina data. Du kan skapa rapporter med flera sidor och varje sida kan ha flera visuella objekt. Du kan interagera med dina visuella objekt för att analysera och förstå dina data. Mer information om hur du redigerar rapporter finns i [Redigera en rapport](service-interact-with-a-report-in-editing-view.md).

I det här steget skapar du en rapport baserad på data som har lästs in tidigare. Du kan använda fönstret Fält för att välja de kolumner som du skapar från visualiseringar.

### <a name="step-1-create-charts-showing-units-in-stock-by-product-and-total-sales-by-year"></a>Steg 1: Skapa diagram som visar Enheter på lager enligt Produkt och Totalförsäljning per år
Dra **UnitsInStock** från fönstret Fält (fältpanelen är längst till höger på skärmen) till en tom plats på arbetsytan. En tabellvisualisering skapas. Dra sedan ProductName till rutan Axlar i den nedre hälften av visualiseringsfönstret. Sedan väljer vi **Sortera efter \> UnitsInStock** med skittles i det övre högra hörnet av visualiseringen.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

Dra **OrderDate** till arbetsytan under det första diagrammet och sedan dra LineTotal (igen från fönstret Fält) till det visuella objektet och välj Linjediagram. Följande visuella objekt skapas.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png)

 Dra därefter **ShipCountry** till ett utrymme på arbetsytan uppe till höger. Eftersom du har valt ett geografiskt fält har en karta skapats automatiskt. Dra **LineTotal** till fältet **Värden**.Cirklarna på kartan för varje land är nu relativa i storlek till **LineTotal** för beställningar som har levererats till landet i fråga.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

### <a name="step-2-interact-with-your-report-visuals-to-analyze-further"></a>Steg 2: Interagera med visuella objekt i rapporten för att analysera närmare
Power BI Desktop gör att du kan interagera med visuella objekt som korsmarkerar och filtrerar varandra för att upptäcka fler trender. Mer information finns i [Filtrering och markering i rapporter](power-bi-reports-filters-and-highlighting.md)

1. Klicka på den ljusa blå cirkeln i mitten av **Canad***a.** Observera hur övriga visuella objekt filtreras för att visa Lager (**Leveransland**) och Totalt antal beställningar (**LineTotal**) för Kanada.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="complete-sales-analysis-report"></a>Slutför analysrapporten för försäljning
När du utför de här stegen bör du ha en försäljningsrapport som kombinerar data från filen Products.xlsx och Northwind OData-feeden. Rapporten visar visuella objekt som hjälper dig att analysera försäljningsinformation från olika länder. Du kan hämta den färdiga Power BI Desktop-filen för den här självstudien [här](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Sales_Data.pbix).

## <a name="next-steps"></a>Nästa steg
* [Läs andra Power BI Desktop-självstudier](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Se Power BI Desktop-videor](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Besök Power BI-forumet](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Läs Power BI-bloggen](http://go.microsoft.com/fwlink/?LinkID=519327)


