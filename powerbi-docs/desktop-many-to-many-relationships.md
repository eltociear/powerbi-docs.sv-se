---
title: Många-till-många-relationer i Power BI Desktop (förhandsversion)
description: Använd många-till-många-relationer i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/23/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 1105de002f6461589d61c6f0077cceeedaada471
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39211781"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Många-till-många-relationer i Power BI Desktop (förhandsversion)

Med funktionen **många-till-många relation** i **Power BI Desktop** kan du ansluta tabeller med en kardinalitet på **många till många** och skapa datamodeller som innehåller flera datakällor på ett enklare och mer intuitivt sätt. Funktionen **många-till-många-relation** är en del av de mer omfattande **sammansatta modeller**-funktionerna i **Power BI Desktop**.

![många-till-många i dialogrutan Redigera relation](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Funktionen **många-till-många-relationer** i **Power BI Desktop** är en del av en samling av tre relaterade funktioner:

* **Sammansatta modeller** – låter en rapport ha flera dataanslutningar, inklusive DirectQuery-anslutningar eller importera, i valfri kombination.
* **Många-till-många-relationer** – med **sammansatta modeller** kan du etablera **många-till-många-relationer** mellan tabeller, vilket tar bort kraven om unika värden i tabeller och gör tidigare lösningar som att introducera nya tabeller bara för att etablera relationer onödiga. 
* **Lagringsläge** – du kan nu ange vilka visuella objekt som kräver en fråga till datakällor i serverdelen och de som inte kräver det importeras även om de baseras på DirectQuery, vilket förbättrar prestandan och minskar belastningen på serverdelen. Tidigare initierade även enkla visuella objekt som utsnitt frågor som skickades till serverdelskällor. 

Den här samlingen med tre relaterade funktioner för **sammansatta modeller** beskrivs var och en i separata artiklar:

* **Sammansatta modeller** beskrivs i detalj i artikeln [sammansatta modeller i Power BI Desktop (förhandsversion)](desktop-composite-models.md).
* **Många-till-många-relationer** beskrivs i den här artikeln.
* **Lagringsläge** beskrivs i sin egen artikel [lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md).

## <a name="enabling-the-many-to-many-relationships-preview-feature"></a>Aktivera förhandsfunktionen många-till-många-relationer

Funktionen **många-till-många-relationer** är en del av funktionerna för **sammansatta modeller** och är i förhandsversion så måste aktiveras i **Power BI Desktop**. Om du vill aktivera **sammansatta modeller** väljer du **Arkiv > Alternativ och inställningar > Alternativ > Förhandsfunktioner** och markera sedan kryssrutan **sammansatta modeller**.

![aktivera förhandsfunktioner](media/desktop-composite-models/composite-models_02.png)

Du måste starta om **Power BI Desktop** för att funktionen ska aktiveras.

![omstart krävs för att ändringarna ska börja gälla](media/desktop-composite-models/composite-models_03.png)


## <a name="what-many-to-many-relationships-solves"></a>Vad många-till-många relationer löser

När du definierade en relation mellan två tabeller i Power BI innan **många-till-många-relationer** fanns att tillgå, behövde minst en av kolumnerna i relationen innehålla unika värden. I många fall innehöll dock ingen kolumn i tabellen unika värden. 

Två tabeller kanske till exempel hade en kolumn som innehåller *Land*, men värdena för *Land* var inte unika i någon av tabellerna. För att ansluta sådana tabeller så behövde du skapa en lösning, till exempel införa ytterligare tabeller i modellen som innehåller nödvändiga unika värden. Funktionen **många-till-många-relationer** erbjuder ett alternativt tillvägagångssätt så att sådana tabeller kan anslutas direkt med hjälp av en relation med en kardinalitet på **många-till-många**.  

## <a name="using-many-to-many-relationships"></a>Använd många-till-många-relationer

När du definierar en relation mellan två tabeller i Power BI, måste du definiera kardinaliteten för relationen. Relationen mellan *ProductSales* och *Produkt* (med hjälp av kolumnerna *ProductSales[ProductCode]* och *Product[ProductCode]*) skulle till exempel definieras som **Många-1**, eftersom det finns många försäljningar för varje produkt och kolumnen i *Produkt*-tabellen *(ProductCode)* är unik. När du definierar en relationskardinalitet som **Många-1**, **1-många** eller **1-1**, utför Power BI validering för att säkerställa att den kardinalitet som valts matchar de faktiska data.

Ta till exempel en titt på den enkla modellen i följande bild.

![relationsvy](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Tänk dig sedan om *Produkt*-tabellen bara innehöll två rader.

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Tänk dig också att *Försäljning*-tabellen bara hade fyra rader, inklusive *Försäljning* för en produkt **C** som inte finns i *Produkt*-tabellen (på grund av ett referensintegritetsfel).

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Ett visuellt objekt som visade *ProductName* och *Pris* (från den *Produkt*-tabellen), tillsammans med den totala *Mängden* för varje produkt (från *ProductSales*-tabellen) skulle då visas som i följande bild: 

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Som du ser i föregående bild, finns det en rad i det visuella objektet med en tom *ProductName* associerad med försäljning av produkt *C*. Den här tomma raden visar följande:

* Alla rader i *ProductSales*-tabellen där det inte finns en motsvarande rad i *Produkt*-tabellen – det finns ett referensintegritetsproblem, som vi kan se för produkten *C* i det här exemplet.

* Alla rader i *ProductSales*-tabellen där sekundärnyckelkolumnen är Null. 

Av den anledning motsvarar de tomma raderna i bägge fall försäljning där *ProductName* och *Pris* är okända.

Det är dock ibland fallet att tabellerna ansluts av två kolumner men ingendera kolumn är unik. Tänk dig exempelvis följande två tabeller:

* *Försäljning*-tabellen innehåller försäljningsdata efter *Stat*, där varje rad innehåller försäljningsmängd för den typen av försäljning i den staten (inklusive staterna CA, WA och TX) 

    ![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* *CityData*-tabellen innehåller data om städer, inklusive befolkning och stat (inklusive staterna CA, WA och New York)

    ![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Även om det finns en kolumn för *Stat* i bägge tabeller och det är rimligt att vilja rapportera om total *Försäljning* efter *Stat*, tillsammans med den totala befolkningen i varje stat så finns det ett problem: kolumnen *Stat* är inte unik i någon av tabellerna. 

## <a name="the-prior-workaround"></a>Den tidigare lösningen

I versioner av **Power BI Desktop** före juli 2018-versionen så gick det inte att skapa en relation direkt mellan dessa tabeller. En vanlig lösning på problemet var att göra följande:

* Skapa en tredje tabell som bara innehåller ID för de unika *Staterna*. Det kan antingen vara en beräknad tabell (definierad med hjälp av DAX), eller en tabell som definieras med en fråga som definierats i **Frågeredigeraren** som kan innehålla unika ID som tagits från en av tabellerna eller den sammanslagna fullständiga uppsättningen.

* Relatera de två ursprungliga tabellerna till den nya tabellen med vanliga **många-1* relationer.

Den lösningstabellen kunde antingen vara synlig eller döljas så att den inte syns i fältlistan. I det senare fallet skulle **Många-1** relationerna vanligtvis anges att filtrera i bägge riktningar så att *Stat*-fältet från endera tabell kan användas, med efterföljande korsfiltrering som fyller i den andra tabellen. Den lösningen visas i följande bild av **Relationsvyn**.

![relationsvy](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Ett visuellt objekt som visar *Stat* (från tabellen *CityData*) tillsammans med den totala *Befolkningen* och total *Försäljning* blir då på följande sätt.

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

Observera att för användningen av stat från *CityData*-tabellen i den här lösningen, kan endast de *Stat*er i den tabellen listas (och därför utesluts TX). Dessutom, till skillnad från i fallet med **Många-1** så även om den totala raden inkluderar all *Försäljning* (inklusive från TX) så inkluderar informationen inte en tom rad som täcker sådana felmatchade rader. På samma sätt skulle det inte finnas någon tom rad som täcker *Försäljning* där det var ett null-värde för *Staten*.

Om *Stad* också lades till i det visuella objektet så medan befolkning per *Stad* är känt, skulle den *Försäljning* som visas för *Stad* bara upprepa *Försäljning* för motsvarande *Stat* (som normalt är fallet när du grupperar på en kolumn som inte är relaterad till ett visst sammanställningsmått) som det visas i följande bild.

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Om den nya tabellen *Försäljning* definierades att vara summan av alla *Stater* i den här lösningen och gjordes synlig i fältlistan så skulle samma visuella objekt som visar *Stat* (på den nya tabellen) tillsammans med total *Befolkning* och total *Försäljning* vara som följer.

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

I det fallet som det visas i det visuella objektet, skulle *TX* (med *Försäljning* men okänd befolkning) och *New York* (med känd befolkning med utan *Försäljning*) inkluderas. 

Som du ser var den här lösningen inte optimal och hade många problem. I och med skapandet av **många-till-många-relationen** har de här problemen åtgärdats, som det beskrivs i följande avsnitt.

## <a name="using-many-to-many-relationships-instead-of-the-workaround"></a>Använd många-till-många-relationer istället för lösningen

I versioner av **Power BI Desktop** från och med juli 2018, kan du direkt relatera sådana tabeller som beskrivs i föregående avsnitt utan att behöva använda den typen av lösningar. Det går nu att ställa in kardinaliteten för en relation till **Många-till-många** vilket anger att ingen av tabellerna innehåller unika värden. För sådana relationer kan du fortfarande kontrollera vilken tabell som filtrerar den andra, eller ha tvåriktad filtrering där bägge tabeller filtrerar varandra.  

> [!NOTE]
> Möjligheten att skapa **Många till många** relationer är i förhandsversion och medan den är det så går det inte att publicera modeller med **Många till många** relationer till Power BI service. 

I **Power BI Desktop** är kardinaliteten som standard **Många till många** när det fastställs att ingendera tabell innehåller unika värden för kolumnerna i relationen. I sådana fall visas en varning för att bekräfta att relationsinställningen är ditt avsedda beteende istället för en oavsedd effekt av ett dataproblem. 

När du till exempel skapar en relation direkt mellan *CityData* och *Försäljning* där filter skulle flöda från *CityData* till *Försäljning*, visas relationsdialogen som det visas i följande bild.

![Dialogrutan Redigera relation](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Den resulterande **Relationsvyn** skulle då innehålla den direkta **Många till många** relationen mellan de två tabellerna. Utseendet i **Fält**-listan och efterföljande beteende när visuella objekt skapas, är sedan detsamma som att använda lösningen som beskrivs i föregående avsnitt, där extratabellen (med de olika *Staterna* i den) inte syns. Till exempel som i föregående avsnitt som beskriver lösningen en visuell objekt där *tillstånd* tillsammans med totala befolkningen och försäljning blir som följer.

![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Så den största skillnaden mellan **Många till många** relationer och typiska **Många-1** relationer är följande.

* De värden som visas inkluderar inte en tom rad för att hantera felmatchade rader i den andra tabellen och inte heller för rader där kolumnen som används i relationen i den andra tabellen är null.
* Det går inte att använda funktionen *RELATED()* (eftersom mer än en rad kan vara relaterad)
* Om du använder funktionen *ALL()* på en tabell så kommer inte filter som använts på andra tabeller relaterade till den med en **Många till många** relation att tas bort. Ett mått som definierats som följande i föregående exempel skulle till exempel inte ta bort filter för kolumner på den relaterade *CityData* tabellen:

    ![skriptexempel](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Därmed resulterar ett visuellt objekt som visar *Stat*, *Försäljning* och *Total försäljning* i följande:

    ![tabellvisualisering](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Därmed är det viktigt att se till att beräkningar som använder *ALL(\<Table>)* som *% av totalsumma* returnerar de förväntade resultaten. 


## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns en del begränsningar för den här versionen av **många-till-många-relationer** och **sammansatta modeller**.

Följande flerdimensionella källor kan inte användas med **sammansatta modeller**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-datauppsättningar

När du ansluter till de flerdimensionella källorna med DirectQuery, kan du inte också ansluta till en annan DirectQuery-källa eller kombinera med importerade data.

De befintliga begränsningarna med att använda DirectQuery gäller fortfarande när du använder **många-till-många-relationer**. Många av dessa begränsningarna är nu per tabell, beroende på tabellens **lagringsläge**. En beräknad kolumn på en importerad tabell kan till exempel referera till andra tabeller, men en beräknad kolumn i en DirectQuery-tabell är fortfarande begränsad till att enbart referera till kolumner i samma tabell. Andra begränsningar gäller för modellen som helhet, om någon av tabellerna inom modellen är DirectQuery. Funktionerna **QuickInsights** och **Q & A** är till exempel inte tillgängliga på en modell om någon av tabellerna i den har **lagringsläget** DirectQuery. 

## <a name="next-steps"></a>Nästa steg

Följande artiklar beskriver mer om sammansatta modeller och beskriver DirectQuery i detalj.

* [Sammansatta modeller i Power BI Desktop (förhandsversion)](desktop-composite-models.md)
* [Lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md)

DirectQuery-artiklar:

* [Använd DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery i Power BI](desktop-directquery-data-sources.md)

