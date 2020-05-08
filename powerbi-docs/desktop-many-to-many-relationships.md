---
title: Många-till-många-relationer i Power BI Desktop
description: Använda relationer med kardinaliteten många-många i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761075"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Använda många-till-många-relationer i Power BI Desktop

Med *relationer som har kardinaliteten många-till-många* i Power BI Desktop kan du koppla tabeller som har kardinaliteten *många-till-många*. Du kan på ett enklare och mer intuitivt sätt skapa datamodeller som innehåller två eller flera datakällor. *Relationer med kardinaliteten många-till-många* ingår i de mer omfattande funktionerna för *sammansatta modeller* i Power BI Desktop.

![En många-till-många-relation i fönstret ”Redigera relation”, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

En *relation med kardinaliteten många-till-många* i Power BI Desktop består av en av tre relaterade funktioner:

* **Sammansatta modeller**: En *sammansatt modell* gör att rapporten kan ha två eller flera dataanslutningar i valfri kombination, som DirectQuery-anslutningar eller importer. Mer information finns i [Använda sammansatta modeller i Power BI Desktop](desktop-composite-models.md).

* **Relationer med kardinaliteten många-många**: Med sammansatta modeller kan du etablera *relationer med kardinaliteten många-till-många* mellan tabeller. Det här tillvägagångssättet tar bort krav på unika värden i tabeller. Det tar också bort behovet av tidigare lösningar. Du behöver till exempel inte lägga till nya tabeller bara för att skapa relationer. Denna funktion beskrivs ytterligare i den här artikeln.

* **Lagringsläge**: Nu kan du ange vilka visuella objekt som kräver en fråga till serverdelens datakällor. Visuella objekt som inte kräver en fråga importeras även om de är baserade på DirectQuery. Den här funktionen hjälper till att förbättra prestanda och minskar belastningen på serversidan. Tidigare så genererade även enkla visuella objekt, som utsnitt, frågor som skickades till serverdelskällorna. Mer information finns i [lagringsläget i Power BI Desktop](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Problem du kan lösa med kardinaliteten många-till-många

Innan det blev möjligt att använda *relationer med kardinaliteten många-till-många* så definierades relationen mellan två tabeller i Power BI. Minst en av de tabellkolumner som ingick i relationen var tvungen att innehålla unika värden. Ofta innehöll dock inga kolumner unika värden.

Två tabeller skulle till exempel kunna ha en kolumn med namnet Land. Landsvärdena i de båda tabellerna var heller inte unika. För att koppla sådana tabeller behövde du skapa en tillfällig lösning. En sådan lösning skulle kunna vara att införa extra tabeller med de unika värden som behövs. Med *relationer med kardinaliteten många-till-många* kan du koppla sådana tabeller direkt om du använder en relation med kardinaliteten *många-till-många*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Använda relationer med kardinaliteten många-många

När du definierar en relation mellan två tabeller i Power BI måste du definiera kardinaliteten för relationen. Till exempel skulle relationen mellan ProductSales och Product &mdash; där kolumnerna ProductSales[ProductCode] och Product[ProductCode] används &mdash; definieras som *många-1*. Vi definierar relationen så här eftersom varje produkt har många försäljningar och kolumnen i tabellen Product (ProductCode) är unik. När du definierar kardinaliteten för en relation som *många-1*, *1-många* eller *1-1* valideras den i Power BI så att kardinaliteten du väljer matchar faktiska data.

Titta till exempel på den enkla modellen i följande bild:

![Tabellerna ProductSales och Product, relationsvyn, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Tänk dig nu att tabellen **Produkt** bara visar två rader enligt nedan:

![Visualisering av tabellen Product med två rader, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Tänk dig även om tabellen Sales bara hade fyra rader, inklusive en rad för produkt C. På grund av ett fel i referensintegriteten finns inte raden för produkt C i tabellen **Product**.

![Visuellt objekt med tabellen Sales med fyra rader, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

**ProductName** och **Price** (från tabellen **Product**) samt totalsumman **Qty** för varje produkt (från tabellen ProductSales) skulle då visas så här:

![Visuellt objekt med produktnamn, pris och kvantitet, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Som du ser i föregående bild finns det en tom rad med namnet **ProductName** associerad med försäljningen för produkt C. Den här tomma raden står för följande:

* Alla rader i tabellen **ProductSales** som det inte finns någon motsvarande rad för i tabellen **Produkt**. Det finns ett problem med referensintegriteten, som vi ser för produkt C i det här exemplet.

* Alla rader i tabellen **ProductSales** där sekundärnyckelkolumnen är null.

Av dessa anledningar står den tomma raden i båda fallen för försäljning där **ProductName** och **Pris** är okända.

Ibland kopplas tabellerna via två kolumner där ingendera kolumn är unik. Tänk dig exempelvis de här två tabellerna:

* Tabellen **Försäljning** visar försäljningsdata efter **Delstat**, där varje rad innehåller försäljningsmängd för typen av försäljning i den delstaten. Delstaterna inkluderar CA, WA och TX.

    ![Försäljningstabell som visar försäljning efter delstat, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* I tabellen **CityData** visas data om städer, bland annat befolkning och delstat (som CA, WA och New York).

    ![Försäljningstabell som visar stad, delstat och befolkning, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Nu finns det en kolumn för **delstaten** i båda tabellerna. Det är rimligt att vilka rapportera både den totala försäljningen per delstat och befolkningen i respektive delstat. Det finns dock ett problem: kolumnen **State** är inte unik i någon av tabellerna.

## <a name="the-previous-workaround"></a>Den tidigare lösningen

I Power BI Desktop-versioner som är äldre än juli 2018 kunde du inte skapa en direkt relation mellan sådana tabeller. I det här läget kunde du:

* Skapa en tredje tabell som bara innehåller unika delstats-ID:n. Tabellen skulle kunna vara något av följande:
  * En beräknad tabell (definieras med hjälp av Data Analysis-uttryck [DAX]).
  * En tabell baserad på en fråga som definieras i frågeredigeraren, som kan visa de unika ID:na hämtade från en av tabellerna.
  * Den kombinerade fullständiga uppsättningen.

* Sedan relatera de två ursprungliga tabellerna till den nya tabellen med hjälp av vanliga *många-1*-relationer.

Lösningstabellen skulle kunna lämnas synlig. Du skulle också kunna välja att dölja den så att den inte visas i **fältlistan**. Om du skulle dölja tabellen skulle *många-1*-relationerna vanligtvis filtreras i båda riktningarna, och då skulle du kunna använda delstatsfältet från endera tabell. Senare korsfiltrering skulle spridas till den andra tabellen. Denna metod visas i följande bild:

![Dold delstatstabell, relationsvyn, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Ett visuellt objekt som visar **Delstat** (från tabellen **CityData**) tillsammans med total **Befolkning** och total **Försäljning**, ser då ut på följande sätt:

![Tabellerna Delstat, Befolkning och Försäljning, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Eftersom delstaten från tabellen **CityData** används i den här lösningen visas bara delstaterna från den tabellen. Därför visas inte TX. Till skillnad från fallet med *många-1*-relationer inkluderar informationen inte en tom rad som täcker sådana felmatchade rader, trots att totalraden inkluderar alla **försäljningar** (även i TX). På samma sätt skulle ingen tom rad täcka **försäljningar** med ett nullvärde för **delstaten**.

Anta att du även lägger till en stad i det visuella objektet. Även om befolkningen per stad är känd så upprepar den **försäljning** som visas per stad helt enkelt **försäljningen** för motsvarande **delstat**. Den här situationen inträffar vanligtvis när kolumngrupperingen inte är relaterad till något aggregat, som du ser här:

![Befolkning i delstater och städer samt försäljning, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Anta att du definierar den nya försäljningstabellen som en kombination av alla delstater här och att vi gör den synlig i **fältlistan**. Samma visuella objekt skulle visa **delstaten** (i den nya tabellen), den totala **befolkningen** och den totala **försäljningen**:

![Visuellt objekt med delstat, befolkning och försäljning, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Som du ser skulle TX &mdash; med data om **försäljning** men okänd *befolkning* &mdash; och New York &mdash; med känd **befolkning** men inga **försäljningsdata** &mdash; ingå. Den här lösningen inte optimal och har många problem. I relationer med kardinaliteten många-många är de här problemen åtgärdade på det sätt som beskrivs i följande avsnitt.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Använda en relation med kardinaliteten många-många i stället för den tillfälliga lösningen

Från och med versionen för juli 2018 av Power BI Desktop kan du direkt relatera tabeller, som de vi beskrev ovan, utan att behöva använda liknande tillfälliga lösningar. Nu kan du ange relationens kardinalitet som *många-till-många*. Den här inställningen anger att ingendera tabell innehåller unika värden. För sådana relationer kan du fortfarande styra vilken tabell som filtrerar den andra. Du kan också använda dubbelriktad filtrering där båda tabellerna filtrerar den andra.

I Power BI Desktop blir kardinaliteten *många-till-många* som standard när det fastställs att ingendera tabell innehåller unika värden för kolumnerna i relationen. I sådana fall visas ett varningsmeddelande om att du vill ange en relation, och att ändringen inte är en oavsiktlig följd av ett dataproblem.

När du till exempel skapar en relation direkt mellan CityData och Försäljning &mdash; där filtren skulle flöda från CityData till Försäljning &mdash; så visar Power BI Desktop dialogrutan **Redigera relation**:

![Dialogrutan Redigera relation, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Den resulterande **Relationsvyn** skulle då visa den direkta många-till-många-relationen mellan de två tabellerna. Tabellernas visas på ungefär samma sätt i listan **Fält**, och beteendet är liknande när de visuella objekten har skapats, som när vi tillämpade den tillfälliga lösningen. I den tillfälliga lösningen är inte extratabellen som visar distinkta delstater synlig. Ett visuellt objekt med **delstater**, **befolkning** och **försäljningssiffror** skulle alltså se ut så här:

![Tabellerna Delstat, Befolkning och Försäljning, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

De största skillnaderna mellan *relationer med kardinaliteten många-många* och de mer typiska *Många-1*-relationerna är följande:

* De värden som visas omfattar inte en tom rad som står för felmatchade rader i den andra tabellen. Dessutom visas inte rader där kolumnen som används i relationen i den andra tabellen är null.
* Du kan inte använda funktionen `RELATED()` eftersom fler än en rad kan vara relaterad.
* Om du använder funktionen `ALL()` i en tabell kommer inte filter som använts på andra, relaterade tabeller av en många-till-många-relation att tas bort. I föregående exempel skulle ett mått som definierats enligt det som visas här inte ta bort filter för kolumnerna i den relaterade tabellen CityData:

    ![Skriptexempel](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Ett visuellt objekt som visar **delstat**, **försäljning** och **total försäljning** skulle se ut så här:

    ![Tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Med föregående skillnader i åtanke bör du se till att de beräkningar som använder `ALL(<Table>)`, som *% av totalsumma*, returnerar förväntat resultat.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns en del begränsningar för den här versionen av *relationer med kardinaliteten många-många* och sammansatta modeller.

Följande (flerdimensionella) Live-anslutningskällor kan inte användas med sammansatta modeller:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-datauppsättningar
* Azure Analysis Services

När du ansluter till dessa flerdimensionella källor med DirectQuery kan du inte ansluta till en annan DirectQuery-källa eller kombinera den med importerade data.

De befintliga begränsningarna med att använda DirectQuery gäller fortfarande när du använder *relationer med kardinaliteten många-många*. Många av begränsningarna gäller nu per tabell beroende på tabellens lagringsläge. En beräknad kolumn i en importerad tabell kan till exempel referera till andra tabeller, men en beräknad kolumn i en DirectQuery-tabell kan fortfarande bara referera till kolumner i samma tabell. Andra begränsningar gäller för hela modellen om någon av tabellerna inom modellen är DirectQuery. Funktionerna Snabbinsikt och Frågor och svar är till exempel inte tillgängliga för en modell om någon av tabellerna i den har lagringsläget DirectQuery.

## <a name="next-steps"></a>Nästa steg

Mer information om sammansatta modeller och DirectQuery finns i följande artiklar:
* [Använda sammansatta modeller i Power BI Desktop](desktop-composite-models.md)
* [Lagringsläge i Power BI Desktop](desktop-storage-mode.md)
* [Använda DirectQuery i Power BI](desktop-directquery-about.md)
* [Power BI-datakällor](power-bi-data-sources.md)
