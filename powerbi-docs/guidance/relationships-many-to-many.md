---
title: Vägledning för att lägga till en många-till-många-relationer
description: Vägledning för att utveckla många-till-många-modellrelationer.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 937f8ca693113cf85d265420da44f7c9f8b68f5f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260470"
---
# <a name="many-to-many-relationship-guidance"></a>Vägledning för att lägga till en många-till-många-relationer

Den här artikeln är avsedd för dig som är datamodellerare som arbetar med Power BI Desktop. I den beskrivs tre olika scenarier för många-till-många-modellering. Där finns även vägledning om hur du skapar utformning för dem i dina modeller.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

Det finns i själva verket tre många-till-många-scenarier. De kan inträffa när du måste:

- [Relatera två tabeller av dimensionstyp](#relate-many-to-many-dimensions)
- [Relatera två tabeller av faktatyp](#relate-many-to-many-facts)
- [Relatera tabeller av faktatyp med högre kornighet](#relate-higher-grain-facts) när tabellen av faktatyp lagrar rader med en högre kornighet än tabellraderna av dimensionstyp

## <a name="relate-many-to-many-dimensions"></a>Relatera många-till-många-dimensioner

Vi börjar med ett exempel för den första många-till-många-scenariotypen. I det klassiska scenariot relateras två entiteter: bankkunder och bankkonton. Kunder kan ha flera konton, och konton kan ha flera kunder. När ett konto har flera kunder kallas de ofta _innehavare av gemensamt konto_.

Det är förhållandevis enkelt att modellera dessa entiteter. En tabell av dimensionstyp lagrar konton medan en annan tabell av dimensionstyp lagrar kunder. Det finns ofta en ID-kolumn i varje tabell av dimensionstyp, och det gäller även här. Modellering av relationen mellan de två tabellerna kräver en tredje tabell. Den här tabellen kallas ofta för en _bryggningstabell_. I det här exemplet är syftet med den att lagra en rad för varje kundkontoassociation. Intressant nog kallas den här tabellen för en [_faktalös faktatabell_](star-schema.md#factless-fact-tables) när den endast innehåller ID-kolumner.

Här är ett förenklad modelldiagram över de tre tabellerna.

![Ett modelldiagram innehåller tre tabeller. Designen beskrivs i följande stycke.](media/relationships-many-to-many/bank-account-customer-model-example.png)

Den första tabellen heter **Account** och innehåller två kolumner: **AccountID** och **Account**. Den andra tabellen heter **AccountCustomer** och innehåller två kolumner: **AccountID** och **CustomerID**. Den tredje tabellen heter **Customer** och innehåller två kolumner: **CustomerID** och **Customer**. Det finns inga relationer mellan tabellerna.

Två en-till-många-relationer läggs till för att relatera tabellerna. Här är ett uppdaterat modelldiagram över de relaterade tabellerna. En tabell av faktatyp med namnet **Transaction** har lagts till. I den registreras kontotransaktioner. Bryggningstabellen och alla ID-kolumner har dolts.

![Modelldiagrammet innehåller nu fyra tabeller. En-till-många-relationer har lagts till för att relatera alla tabellerna.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

För att hjälpa till att beskriva hur spridningen av relationsfiltret fungerar har modelldiagrammet ändrats så att tabellraderna visas.

> [!NOTE]
> Det går inte att visa tabellrader i Power BI Desktop-modelldiagrammet. Det sker i den här artikeln i syfte att stödja diskussionen med tydliga exempel.

![Nu visar modelldiagrammet tabellraderna. Radinformationen beskrivs i följande stycke.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

Radinformationen för de fyra tabellerna beskrivs i följande punktlista:

- Tabellen **Account** innehåller två rader:
  - **AccountID** 1 gäller för Account-01
  - **AccountID** 2 gäller för Account-02
- Tabellen **Customer** innehåller två rader:
  - **CustomerID** 91 gäller för Customer-91
  - **CustomerID** 92 gäller för Customer-92
- Tabellen **AccountCustomer** innehåller tre rader:
  - **AccountID** 1 är associerad med **CustomerID** 91
  - **AccountID** 1 är associerad med **CustomerID** 92
  - **AccountID** 3 är associerad med **CustomerID** 92
- Tabellen **Transaction** innehåller tre rader:
  - **Date** January 1 2019, **AccountID** 1, **Amount** 100
  - **Date** February 2 2019, **AccountID** 2, **Amount** 200
  - **Date** March 3 2019, **AccountID** 1, **Amount** -25

Vi tittar på vad som händer när frågor körs mot modellen.

Nedan visas två visuella objekt som sammanfattar kolumnen **Amount** från tabellen **Transaction**. Det första visuella objektet grupperar efter konto. Summan av **Amount**-kolumnerna representerar därför _kontosaldot_. Det andra visuella objektet grupperar efter kund. Summan av **Amount**-kolumnerna representerar därför _kundsaldot_.

![Två visuella rapportobjekt är sida vid sida. De visuella objekten beskrivs i följande stycke.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

Det första visuella objektet heter **Account Balance** och innehåller två kolumner: **Account** och **Amount**. Det visar följande resultat:

- Saldobeloppet för Account-01 är 75
- Saldobeloppet för Account-02 är 200
- Summan är 275

Det andra visuella objektet heter **Customer Balance** och innehåller två kolumner: **Customer** och **Amount**. Det visar följande resultat:

- Saldobeloppet för Customer-91 är 275
- Saldobeloppet för Customer-92 är 275
- Summan är 275

En snabb överblick över tabellraderna och det visuella objektet **Account Balance** visar att resultatet är korrekt för varje konto och totalsumman. Det beror på att varje kontogruppering resulterar i en filterspridning till tabellen **Transaction** för det kontot.

Det verkar dock som att något inte stämmer med det visuella objektet **Customer Balance**. Varje kund i det visuella objektet **Customer Balance** har samma saldo som det totala saldot. Det här resultatet kan bara stämma om varje kund är en innehavare av gemensamt konto för varje konto. Så är det inte i det här exemplet. Problemet har med filterspridning att göra. Det flödar inte hela vägen till tabellen **Transaction**.

Följ riktningarna för relationsfilter från tabellen **Customer** till tabellen **Transaction**. Det bör vara uppenbart att relationen mellan tabellerna **Account** och **AccountCustomer** sprids i fel riktning. Filterriktningen för den här relationen måste anges till **Båda**.

![Modelldiagrammet har uppdaterats. En enda ändring har gjorts i relationen mellan tabellerna Account och AccountCustomer. Nu filtreras den i båda riktningarna.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Samma två visuella rapportobjekt är sida vid sida. Det första visuella objektet har inte ändrats. Det andra visuella objektet visar ett annat resultat och beskrivs i följande stycken.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Som förväntat har inga ändringar gjorts i det visuella objektet **Account Balance**.

Nu visar dock det visuella objektet **Customer Balance** följande resultat:

- Saldobeloppet för Customer-91 är 75
- Saldobeloppet för Customer-92 är 275
- Summan är 275

Det visuella objektet **Customer Balance** visar nu ett korrekt resultat. Följ filterriktningarna själv och se hur kundsaldona beräknades. Observera dessutom att den visuella summan innebär _alla kunder_.

Utan kunskap om modellrelationerna skulle man kunna tro att resultatet är felaktigt. Kanske blir frågan då: _Varför är det totala saldot för **Customer-91** och **Customer-92** lika med 350 (75 + 275)?_

Svaret på frågan har att göra med förståelsen för många-till-många-relationen. Varje kundsaldo kan representera additionen av flera kontosaldon. Därför är kundsaldona _icke-additiva_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Vägledning om hur du relaterar många-till-många-dimensioner

När du har en många-till-många-relation mellan tabeller av dimensionstyp ger vi följande vägledning:

- Lägg till varje många-till-många-relaterad entitet som en modelltabell och se till att den har en ID-kolumn (unik identifierare)
- Lägg till en bryggningstabell för att lagra associerade entiteter
- Skapa en-till-många-relationer mellan de tre tabellerna
- Konfigurera **en** dubbelriktad relation så att filterspridningen kan fortsätta till tabellerna av faktatyp
- I de fall då det inte är lämpligt att ha saknade ID-värden anger du ID-kolumnernas egenskap **Is Nullable** till FALSE – datauppdateringen misslyckas då om saknade värden används som källa
- Dölj bryggningstabellen (såvida den inte innehåller ytterligare kolumner eller mått som krävs för rapportering)
- Dölj alla ID-kolumner som inte är lämpliga för rapportering (till exempel när ID:n är surrogatnycklar)
- Om det är klokt att låta en ID-kolumn vara synlig ser du till att den finns på relationens ”en-sida” – du bör alltid dölja kolumnen på ”många-sidan”. Detta resulterar i bästa filterprestanda.
- För att undvika förvirring eller feltolkning kan du ge förklaringar till rapportanvändarna – du kan lägga till beskrivningar med textrutor eller [knappbeskrivningar för de visuella objektens sidhuvuden](report-page-tooltips.md)

Vi rekommenderar inte att du relaterar tabeller av många-till-många-dimensionstyp direkt. Den här designmetoden kräver att du konfigurerar en relation med en många-till-många-kardinalitet. Rent konceptuellt går det att utföra, men då innebär det att de relaterade kolumnerna innehåller dubblettvärden. Det är dock en brett accepterad designmetod att tabeller av dimensionstyp innehåller en ID-kolumn. Tabeller av dimensionstyp bör alltid använda ID-kolumnen som ”en-sidan” i en relation.

## <a name="relate-many-to-many-facts"></a>Relatera många-till-många-fakta

Det andra många-till-många-scenariotypen innefattar att två tabeller av faktatyp relateras. Två tabeller av faktatyp kan relateras direkt. Den här designtekniken kan vara användbar för snabb och enkel datautforskning. Men vanligtvis rekommenderar vi inte den här designmetoden. Vi förklarar anledningen till det senare i det här avsnittet.

Vi tar en titt på ett exempel med två tabeller av faktatyp: **Order** och **Fulfillment**. Tabellen **Order** innehåller en rad per orderrad, och tabellen **Fulfillment** kan innehålla noll eller fler rader per orderrad. Rader i tabellen **Order** representerar försäljningsordrar. Rader i tabellen **Fulfillment** representerar orderobjekt som har fraktats. En många-till-många-relation relaterar de två **OrderID**-kolumnerna. Filterspridning sker bara från tabellen **Order** (**Order** filtrerar **Fulfillment**).

![Ett modelldiagram innehåller två tabeller: Order och Fulfillment. En många-till-många-relation relaterar de två kolumnerna OrderID-kolumnerna med filtrering från Order till Fulfillment.](media/relationships-many-to-many/order-fulfillment-model-example.png)

Relationskardinaliteten anges till många-till-många för att stödja lagring av duplicerade **OrderID**-värden i båda tabellerna. I tabellen **Order** kan det finnas duplicerade **OrderID**-värden eftersom en order kan ha flera rader. I tabellen **Fulfillment** kan det finnas duplicerade **OrderID**-värden eftersom ordrar kan ha rader och orderrader kan uppfyllas av många leveranser.

Nu tar vi en titt på tabellraderna. Observera att orderrader i tabellen **Fulfillment** kan uppfyllas av flera leveranser. (Om det saknas en orderrad innebär det att ordern ännu inte har uppfyllts.)

![Nu visar modelldiagrammet tabellraderna. Radinformationen beskrivs i följande stycke.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

Radinformationen för de två tabellerna beskrivs i följande punktlista:

- Tabellen **Order** innehåller fem rader:
  - **OrderDate** January 1 2019, **OrderID** 1, **OrderLine** 1, **ProductID** Prod-A, **OrderQuantity** 5, **Sales** 50
  - **OrderDate** January 1 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Sales** 80
  - **OrderDate** February 2 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Sales** 40
  - **OrderDate** February 2 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Sales** 20
  - **OrderDate** March 3 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Sales** 100
- Tabellen **Fulfillment** innehåller fyra rader:
  - **FulfillmentDate** January 1 2019, **FulfillmentID** 50, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 2
  - **FulfillmentDate** February 2 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** February 2 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** January 1 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

Vi tittar på vad som händer när frågor körs mot modellen. Här är ett visuellt tabellobjekt där kvantiteter för order och uppfyllande jämförs efter **Order**-tabellens **OrderID**-kolumn.

![Ett visuellt tabellobjekt har tre kolumner: OrderID, OrderQuantity och FulfillmentQuantity. Det finns tre rader, en för varje order. OrderID 2 och 3 är inte helt uppfyllda.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

Det visuella objektet visar ett korrekt resultat. Modellens användbarhet är dock begränsad – du kan bara filtrera eller gruppera efter **Order**-tabellens **OrderID**-kolumn.

### <a name="relate-many-to-many-facts-guidance"></a>Vägledning om hur du relaterar många-till-många-fakta

I allmänhet rekommenderar vi inte att du relaterar två tabeller av faktatyp direkt med hjälp av många-till-många-kardinalitet. Den främsta orsaken är att modellen i så fall inte ger flexibilitet för de visuella rapportobjektens filtrering och gruppering. I exemplet är det endast möjligt för visuella objekt att filtrera eller gruppera efter **Order**-tabellens **OrderID**-kolumn. Ytterligare en orsak relaterar till kvaliteten på dina data. Om det finns integritetsproblem i dina data kan det hända att vissa rader utelämnas under frågekörning på grund av den _svaga relationen_. Mer information finns i [Modellrelationer i Power BI Desktop (relationsutvärdering)](../desktop-relationships-understand.md#relationship-evaluation).

Vi rekommenderar att du i stället för att relatera tabeller av faktatyp direkt inför designprinciperna för [star-schema](star-schema.md). Det gör du genom att lägga till tabeller av dimensionstyp. Tabellerna av dimensionstyp relaterar sedan till tabellerna av faktatyp med hjälp av en-till-många-relationer. Den här designmetoden är robust eftersom den ger flexibla rapporteringsalternativ. Med den kan du filtrera eller gruppera med valfri kolumn av dimensionstyp och sammanfatta valfri relaterad tabell av faktatyp.

Vi tittar på en bättre lösning.

![Ett modelldiagram innehåller sex tabeller: OrderLine, OrderDate, Order, Fulfillment, Product och FulfillmentDate. Alla tabeller är relaterade. Designen beskrivs i följande stycke.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Observera följande designändringar:

- Modellen innehåller nu ytterligare fyra tabeller: **OrderLine**, **OrderDate**, **Product** och **FulfillmentDate**
- Alla de fyra ytterligare tabellerna är tabeller av dimensionstyp, och en-till-många-relationer relaterar dessa tabeller till tabellerna av faktatyp
- Tabellen **OrderLine** innehåller en **OrderLineID**-kolumn som representerar **OrderID**-värdet multiplicerat med 100 plus **OrderLine**-värdet – en unik identifierare för varje orderrad
- Tabellerna **Order** och **Fulfillment** innehåller nu en **OrderLineID**-kolumn och innehåller inte längre kolumnerna **OrderID** och **OrderLine**
- Tabellen **Fulfillment** innehåller nu kolumnerna **OrderDate** och **ProductID**
- Tabellen **FulfillmentDate** relaterar endast till tabellen **Fulfillment**
- Alla kolumner med unika identifierare är dolda

När vi utnyttjar designprinciperna för star-schema får vi dessa fördelar:

- De visuella rapportobjekten kan _filtrera eller gruppera_ efter valfri synlig kolumn från tabellerna av dimensionstyp
- De visuella rapportobjekten kan _sammanfatta_ valfri synlig kolumn från tabellerna av faktatyp
- Filter som tillämpas på tabellerna **OrderLine**, **OrderDate** eller **Product** sprids till båda tabellerna av faktatyp
- Alla relationer är av typen en-till-många, och varje relation är en _stark relation_. Problem med dataintegritet kommer inte att döljas. Mer information finns i [Modellrelationer i Power BI Desktop (relationsutvärdering)](../desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Relatera fakta med högre kornighet

Detta många-till-många-scenario skiljer sig avsevärt från de andra två scenarierna som beskrivits tidigare i artikeln.

Vi tittar på ett exempel med fyra tabeller: **Date**, **Sales**, **Product** och **Target**. **Date** och **Product** är tabeller av dimensionstyp, och en-till-många-relationer relaterar vardera till tabellen **Sales**, som är av faktatyp. Än så länge följer detta en god design enligt principerna för star-schema. Dock har tabellen **Target** ännu inte relaterats till de andra tabellerna.

![Ett modelldiagram innehåller fyra tabeller: Date, Sales, Product och Target. Tabellen Target är inte relaterad till någon annan tabell. Designen beskrivs i följande stycke.](media/relationships-many-to-many/sales-targets-model-example.png)

Tabellen **Target** innehåller tre kolumner: **Category**, **TargetQuantity** och **TargetYear**. Tabellraderna visar på en kornighet för år och produktkategori. Mål, som används för att mäta försäljningsprestanda, anges alltså varje år för varje produktkategori.

![Tabellen Target innehåller tre kolumner: TargetYear, Category och TargetQuantity. Sex rader registrerar mål för 2019 och 2020, var och en för tre kategorier.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Eftersom tabellen **Target** lagrar data på en högre nivå än tabellerna av dimensionstyp går det inte att skapa en en-till-många-relation. Detta stämmer åtminstone för bara en av relationerna. Vi går igenom hur tabellen **Target** kan relateras till tabellerna av dimensionstyp.

### <a name="relate-higher-grain-time-periods"></a>Relatera tidsperioder med högre kornighet

En relation mellan tabellerna **Date** och **Target** bör vara en en-till-många-relation. Det beror på att **TargetYear**-kolumnvärdena är datum. I det här exemplet är varje **TargetYear**-kolumnvärde det första datumet för målåret.

> [!TIP]
> Vid lagring av fakta med en högre tidskornighet än dagar anger du kolumndatatypen till **Datum** (eller **Heltal** om du använder datumnycklar). I kolumnen lagrar du ett värde som representerar den första dagen i tidsperioden. Till exempel registreras en årsperiod som 1 januari det året, och en månadsperiod registreras som den första dagen under den månaden.

Var dock noggrann med att se till att filtren på månads- eller datumnivå ger ett meningsfullt resultat. Utan särskild beräkningslogik kan de visuella rapportobjekten rapportera att måldatumen bokstavligt talat är den första dagen under varje år. Alla andra dagar – och alla månader förutom januari – sammanfattar målkvantiteten som TOM.

Följande visuella matrisobjekt visar vad som händer när rapportanvändaren ökar detaljnivån från ett år till dess månader. Det visuella objektet sammanfattar kolumnen **TargetQuantity**. (Alternativet [Visa objekt utan data](../desktop-show-items-no-data.md) har aktiverats för matrisraderna.)

![Ett visuellt matrisobjekt visar målkvantiteten för året 2020 som 270. När det expanderas till att visa månaderna för 2020 är januari 270, och alla andra målkvantiteter på månadsnivå är TOM.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

För att undvika det här beteendet rekommenderar vi att du kontrollerar sammanfattningen av faktadata med hjälp av mått. Ett sätt att kontrollera sammanfattningen är att returnera TOM när frågor körs mot tidsperioder på lägre nivåer. Ett annat sätt – som definieras med viss sofistikerad DAX – är att fördela värden mellan tidsperioder på lägre nivåer.

Överväg följande måttdefinition som använder DAX-funktionen [ISFILTERED](/dax/isfiltered-function-dax). Den returnerar bara ett värde när kolumnerna **Date** eller **Month** inte är filtrerade.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

Följande visuella matrisobjekt använder nu **Target Quantity**-måttet. Det visar att alla målkvantiteter för månad är TOM.

![Ett visuellt matrisobjekt visar målkvantiteten för året 2020 som 270. När det expanderas till att visa månaderna för 2020 alla målkvantiteter på månadsnivå TOM.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Relatera högre kornighet (icke-datum)

En annan designmetod krävs när du relaterar en icke-datumkolumn från en tabell av dimensionstyp till en tabell av faktatyp (och när den har en högre kornighet än tabellen av dimensionstyp).

**Category**-kolumnerna (från både tabellen **Product** och tabellen **Target**) innehåller dubblettvärden. Därför finns det ingen ”en” för en en-till-många-relation. I det fallet måste du skapa en många-till-många-relation. Relationen ska sprida filter i en enda riktning, från tabellen av dimensionstyp till tabellen av faktatyp.

![Ett fragment av ett modelldiagram visar mål- och produkttabellerna. En många-till-många-relation relaterar de två tabellerna. Filterriktningen går från produkt till mål.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Nu tar vi en titt på tabellraderna.

![Ett modelldiagram innehåller två tabeller: Mål och produkt. En många-till-många-relation relaterar de två Category-kolumnerna. Radinformationen beskrivs i följande stycke.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

I tabellen **Target** finns det fyra rader: två rader för varje målår (2019 och 2020) samt två kategorier (Clothing och Accessories). I tabellen **Product** finns det tre produkter. Två hör till kategorin Clothing och en hör till kategorin Accessories. En av klädfärgerna är grön, och de andra två är blå.

Ett visuellt tabellobjekt som grupperar efter kolumnen **Category** från tabellen **Product** ger följande resultat.

![Ett visuellt tabellobjekt har två kolumner: Category och TargetQuantity. Accessories är 60, Clothing är 40 och summan är 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Det här visuella objektet är korrekt resultat. Nu tittar vi på vad som händer när kolumnen **Color** från tabellen **Product** används för att gruppera målkvantitet.

![Ett visuellt tabellobjekt har två kolumner: Color och TargetQuantity. Blue är 100, Green är 40 och summan är 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

Det visuella objektet ger en felaktig representation av data. Vad är det som händer här?

Ett filter för kolumnen **Color** från tabellen **Product** resulterar i två rader. En av raderna gäller för kategorin Clothing medan den andra gäller för kategorin Accessories. Dessa två kategorivärden sprids som filter till tabellen **Target**. Eftersom färgen blå används av produkter från två kategorier används alltså _de kategorierna_ för att filtrera målen.

För att undvika det här beteendet rekommenderar vi, som beskrevs tidigare, att du kontrollerar sammanfattningen av faktadata med hjälp av mått.

Ta följande måttdefinition som exempel. Observera att alla kolumner i tabellen **Product** som är under kategorinivån testas med avseende på filter.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

Följande visuella tabellobjekt använder nu **Target Quantity**-måttet. Det visar att alla målkvantiteter för färg är TOM.

![Ett visuellt tabellobjekt har två kolumner: Color och TargetQuantity. Blue är TOM, Green är TOM och summan är 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

Den slutgiltiga modelldesignen har följande utseende.

![Modelldiagrammet visar att tabellerna Date och Target är relaterade med en en-till-många-relation. Tabellerna Product och Target är relaterade med en många-till-många-relation med filtrering från Product till Target.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Vägledning om att relatera fakta med högre kornighet

När du behöver relatera en tabell av dimensionstyp till en tabell av faktatyp, och tabellen av faktatyp lagrar rader med högre kornighet än raderna i tabellen av dimensionstyp, ger vi följande vägledning:

- För faktadatum med högre kornighet:
  - I tabellen av faktatyp lagrar du det första datumet i tidsperioden
  - Skapa en en-till-många-relation mellan datumtabellen och faktatypstabellen
- För andra fakta med högre kornighet:
  - Skapa en många-till-många-relation mellan tabellen av dimensionstyp och tabellen av faktatyp
- För båda typerna:
  - Kontrollera sammanfattningen med måttlogik – returnera TOM när kolumner av dimensionstyp på lägre nivå används för att filtrera eller gruppera
  - Dölj sammanfattningsbara kolumner i tabeller av faktatyp – på så sätt kan endast mått användas för att sammanfatta tabellen av faktatyp

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Modellrelationer i Power BI Desktop](../desktop-relationships-understand.md)
- [Förstå star-schemat och dess betydelse för Power BI](star-schema.md)
- [Vägledning vid felsökning av relationer](relationships-troubleshoot.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
