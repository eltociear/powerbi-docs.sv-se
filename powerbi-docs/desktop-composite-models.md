---
title: Använd sammansatta modeller i Power BI Desktop (förhandsversion)
description: Skapa datamodeller med flera dataanslutningar och många-till-många-relationer i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 49540dd491d02c6a6b474ff80690a75eecfd27db
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2018
ms.locfileid: "49337000"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Sammansatta modeller i Power BI Desktop (förhandsversion)

Tidigare i **Power BI Desktop** när du använde en DirectQuery i en rapport, tilläts inga andra dataanslutningar oavsett om DirectQuery eller importera tilläts för rapporten eller inte. Med **sammansatta modeller** har den begränsningen tagits bort och en rapport kan sömlöst inkludera dataanslutningar från mer än en DirectQuery- eller importera data-anslutning i valfri kombination.

![sammansatta modeller i Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

Funktionen **sammansatta modeller** i **Power BI Desktop** består av tre relaterade funktioner:

* **Sammansatta modeller** – låter en rapport ha flera dataanslutningar, inklusive DirectQuery-anslutningar eller importera, i valfri kombination.
* **Många-till-många-relationer** – med **sammansatta modeller** kan du etablera **många-till-många-relationer** mellan tabeller, vilket tar bort kravet om unika värden i tabeller och tar bort tidigare lösningar som att introducera nya tabeller bara för att etablera relationer. 
* **Lagringsläge** – du kan nu ange vilka visuella objekt som kräver en fråga till datakällor i serverdelen och de som inte kräver det importeras även om de baseras på DirectQuery, vilket förbättrar prestandan och minskar belastningen på serverdelen. Tidigare initierade även enkla visuella objekt som utsnitt frågor som skickades till serverdelskällor. 

Den här samlingen med tre relaterade funktioner för **sammansatta modeller** beskrivs var och en i separata artiklar:

* **Sammansatta modeller** beskrivs i detalj i den här artikeln.
* **Många-till-många-relationer** beskrivs i sin egen artikel [många-till-många-relationer i Power BI Desktop (förhandsversion)](desktop-many-to-many-relationships.md).
* **Lagringsläge** beskrivs i en egen artikel, [lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md).

## <a name="enabling-the-composite-models-preview-feature"></a>Aktivera förhandsfunktionen sammansatta modeller

Funktionen **sammansatta modeller** är i förhandsversion och måste aktiveras i **Power BI Desktop**. Om du vill aktivera **sammansatta modeller** väljer du **Arkiv > Alternativ och inställningar > Alternativ > Förhandsfunktioner** och markera sedan kryssrutan **sammansatta modeller**. 

![aktivera förhandsfunktioner](media/desktop-composite-models/composite-models_02.png)

Du måste starta om **Power BI Desktop** för att funktionen ska aktiveras.

![omstart krävs för att ändringarna ska börja gälla](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>Använd sammansatta modeller

Med **sammansatta modeller**, kan du ansluta till en mängd olika datakällor när du använder **Power BI Desktop** eller **Power BI-tjänsten** och du kan skapa de dataanslutningarna på olika sätt. Du kan importera data till Power BI, vilket är det vanligaste sättet att hämta data på, eller så kan du ansluta direkt till data i den ursprungliga källdatabasen med DirectQuery. Du kan läsa mer om DirectQuery-detaljer i artikeln [använd DirectQuery i Power BI](desktop-directquery-about.md).

När du använder DirectQuery med **sammansatta modeller** är det möjligt att skapa en Power BI-modell (till exempel en enskild .pbix Power BI Desktop-fil) som gör följande:

* kombinerar data från en eller flera DirectQuery-källor, och/eller
* kombinerar data från DirectQuery-källor och importerar data

Med **sammansatta modeller** är det till exempel möjligt att skapa en modell som kombinerar försäljningsdata från ett företags informationslager med data över försäljningsmål som är i en avdelnings SQL Server-databas, tillsammans med vissa data som importerats från ett kalkylblad. En modell som kombinerar data från mer än en DirectQuery-källa eller kombinerar DirectQuery med importerade data kallas en *sammansatt modell*.

> [!NOTE]
> Från och med oktober 2018-versionen av **Power BI Desktop**, *kan* du publicera sammansatta modeller i Power BI-tjänsten. För schemalagd uppdatering och uppdateringen av instrumentpanelen fungerar sammansatta modeller i Power BI-tjänsten på samma sätt som importmodeller. 

Du kan skapa relationer mellan tabeller precis som alltid, även när dessa tabeller kommer från olika källor, med följande begränsning: alla relationer som är mellan källor måste definieras som att ha en kardinalitet på **många-till-många**, oavsett deras faktiska kardinalitet. Beteendet för dessa relationer är sedan samma som normalt **många-till-många** relationer, enligt beskrivningen i [många-till-många-relationer i Power BI Desktop (förhandsversion)](desktop-many-to-many-relationships.md). Observera att inom ramen för sammansatta modeller, är alla importerade tabeller i princip en enda källa, oavsett den faktiska underliggande datakällan som importeras från.   

## <a name="example-of-using-composite-models"></a>Exempel på användning av sammansatta modeller

Som ett exempel på en **sammansatt modell** kan du tänka dig en rapport som har anslutit till ett företags informationslager (i SQL Server) med hjälp av DirectQuery, där informationslagret innehåller data för *Försäljning efter land*,  *Kvartal* och *Cykel (produkt)* som det visas i följande bild.

![relationsvy för sammansatta modeller](media/desktop-composite-models/composite-models_04.png)

Du kan nu skapa enkla visuella objekt med fält från den här källan. Följande visuella objekt visar till exempel totalt försäljningsbelopp per *ProductName* för ett valt kvartal. 

![visuellt objekt baserat på data](media/desktop-composite-models/composite-models_05.png)

Men vad händer om har viss information om den produktansvarige som tilldelats varje produkt, tillsammans med marknadsföringsprioritet där data ligger på ett Excel-kalkylblad? Du kanske vill se *Försäljningsmängd* efter *Produktansvarig*, men att lägga till dessa lokala data till företagets informationslager skulle antagligen inte gå att göra eller ta månader. Även om det skulle gå att importera försäljningsdata från informationslagret (istället för att använda DirectQuery) vilken då skulle kunna kombineras med data som importerats från kalkylbladet så är den metoden orimligt med tanke på de orsaker som ledde till att använda DirectQuery, till exempel en kombination av de säkerhetsregler som används för den underliggande datakällan, behovet att kunna se de senaste data och själva dataskalan. 

Det är där **sammansatta modeller** kommer in. Sammansatta modeller ger dig möjligheten att ansluta till informationslagret med DirectQuery och sedan även använda GetData för ytterligare källor. I det här fallet vi upprättar vi DirectQuery-anslutningen till företagets informationslager och använder sedan GetData och väljer Excel, navigerar till det kalkylblad som innehåller våra lokala data och kan importera bladet som innehåller *ProductNames*, den tilldelade *SalesManager* och *Priority*.  

![Navigatorfönstret](media/desktop-composite-models/composite-models_06.png)

I den **Fält**-listan ser vi nu den ursprungliga tabellen *Cykel* (från SQL Server) och en ny tabell *Produktansvariga* (med data som importerades från Excel). 

![Fältvy av tabeller](media/desktop-composite-models/composite-models_07.png)

Likaså om du tittar på **Relationsvyn** i **Power BI Desktop**, ser vi nu en ytterligare tabell med namnet *Produktansvariga*. 

![relationsvy av tabeller](media/desktop-composite-models/composite-models_08.png)

Nu behöver vi relatera de här till andra tabeller i modellen, vilket vi gör på samma sätt som alltid genom att skapa en relation mellan tabellen *Cykel* (i SQL Server) och tabellen *Produktansvariga* (som har importerats) som mellan *Cykel[ProductName]* och *ProductManagers[ProductName]*. Som det beskrivs tidigare i den här artikeln, måste alla relationer mellan källor ha kardinaliteten **många-till-många** och därmed är det den standardkardinalitet som väljs. 

![dialogrutan skapa relation](media/desktop-composite-models/composite-models_09.png)

När den här relationen har skapats, visas den i **Relationsvyn** i **Power BI Desktop** precis som man kan förvänta sig.

![ny relationsvy](media/desktop-composite-models/composite-models_10.png)

När de här tabellrelationerna har upprättats, kan vi nu skapa visuella objekt med något av fälten i **Fält**-listan och sömlöst blanda data från flera källor. Det visuella objektet nedan visar exempelvis total *Försäljningsmängd* för varje *Produktansvarig*. 

![visuellt objekt med Fält-fönstret](media/desktop-composite-models/composite-models_11.png)

Det här exemplet visar ett vanligt fall av en *dimension*-tabell (t.ex. *Produkt* eller *Kund*) som utökas med extra data som importerats från någon annanstans, det är också möjligt att låta tabeller använda DirectQuery som ansluter till olika källor. Så för att utöka vårt exempel, tänk dig att *SalesTargets* per *Land* och *Period* lagras i databasen för en separat avdelning. Du kan använda **GetData** för att ansluta till dessa data på vanligt sätt, som det visas i följande bild. 

![Navigeringsdialogruta](media/desktop-composite-models/composite-models_12.png)

På ett liknande sätt som vi gjorde tidigare i det här exemplet, kan vi sedan skapa relationer mellan den nya tabellen och andra tabeller i modellen och skapa visuella objekt som kombinerar sina data. Låt oss titta igen på **Relationsvyn**, där vi har skapat nya relationer i vårt utökade exempelscenario.

![relationsvy med många tabeller](media/desktop-composite-models/composite-models_13.png)

Som du ser i följande bild, som baseras på de nya data och relationer som vi precis har skapat, visar det visuella objektet i det nedre vänstra hörnet total *Försäljningsmängd* kontra *Mål* där avvikelseberäkningen visar skillnaden, där *Försäljningsmängd* och *Mål* kommer från två olika SQL Server-databaser. 

![visuellt objekt som visar mer data](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>Konfigurera lagringsläge

Varje tabell i en **sammansatt modell** har ett **lagringsläge** som indikerar om tabellen är baserad på DirectQuery eller importera. **Lagringsläge** kan visas och ändras i **Egenskaper**-fönstret. För att komma dit, väljer du **Egenskaper** från **Fält**-listans snabbmeny som du får fram när du högerklickar. Följande bild visar **lagringsläge** (förkortat till **Lagring...**  i bilden på grund av fönstrets bredd).

![Konfigurera lagringsläge](media/desktop-composite-models/composite-models_15.png)

**Lagringsläge** kan också visas i knappbeskrivningen för varje tabell.

![knappbeskrivning med lagringsläge](media/desktop-composite-models/composite-models_16.png)

För alla **Power BI Desktop**-filer (en .pbix-fil) som innehåller några tabeller från DirectQuery och vissa importtabeller, visar statusfältet ett **lagringsläge** som **Kombinerat**. Du kan klicka på den termen i statusfältet och enkelt växla alla tabeller till importera.

Information om **lagringsläge** beskrivs i sin helhet i artikeln [lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md).  

## <a name="calculated-tables"></a>Beräknade tabeller

Beräknade tabeller kan läggas till en modell som använder DirectQuery och den DAX som definierar den beräknade tabellen kan referera antingen till importerade eller DirectQuery-tabeller eller en kombination. 

Beräknade tabeller är alltid importerade och data i de tabellerna uppdateras när tabellen uppdateras. Om en beräknad tabell därmed refererar till en DirectQuery-tabell, visar visuella objekt som refererar till DirectQuery-tabellen alltid de senaste värdena i den underliggande källan men visuella objekt som refererar till den beräknade tabellen visar värdena från den tidpunkt då den beräknade tabellen senast uppdaterades.

## <a name="security-implications"></a>Säkerhetsaspekter 

Sammansatta modeller innebär vissa säkerhetsaspekter. En fråga som skickas till en datakälla kan innehålla datavärden som har hämtats från en annan källa. I exemplet som beskrivs tidigare i den här artikeln, resulterar det visuella objektet som visar *Försäljningsmängd* efter *Produktansvarig* i att en SQL-fråga skickas till den relationella databasen **Försäljning**, där den SQL-frågan kan innehålla namnen på *Produktansvariga* och deras associerade *Produkter*. 

![skript som visar säkerhetsaspekter](media/desktop-composite-models/composite-models_17.png)

Därför inkluderas information som lagras i kalkylbladet nu i en fråga som skickas till den relationella databasen. Om den här informationen är konfidentiell, bör säkerhetsaspekterna av det här övervägas. Särskilt bör du tänka på följande aspekter:

* Alla administratörer av databasen som kan se spår eller granskningsloggar skulle kunna se den här informationen, även om de inte har behörighet till dessa data i sin ursprungliga källa (i det här fallet behörigheter till Excel-filen).

* Krypteringsinställningarna för varje källa bör övervägas för att undvika att information hämtas från en källa som använder en krypterad anslutning och sedan oavsiktligt inkluderas i en fråga som skickas till en annan källa med en okrypterad anslutning. 

**Power BI Desktop** visar ett varningsmeddelande när en åtgärd vidtas för att skapa en sammansatt modell så att man kan bekräfta att alla säkerhetsaspekter har övervägts.  

Av liknande skäl måste du vara försiktig när du öppnar en **Power BI Desktop**-fil som skickats från en ej betrodd källa. Om den filen innehåller sammansatta modeller, innebär det att information som hämtas från en källa (med autentiseringsuppgifterna för användaren att öppna filen) skulle skickas till en annan datakälla som en del av frågan (där den eventuellt kan ses av den skadliga skaparen av Power BI Desktop-filen). Därmed visas en varning när en Power BI Desktop-fil öppnas för första gången, om den innehåller flera källor. Den här varningen liknar den varning som visas när du öppnar en fil som innehåller inbyggda SQL-frågor.  

## <a name="performance-implications"></a>Prestandaöverväganden  

När du använder DirectQuery så ska prestanda alltid övervägas, främst för att säkerställa att serverdelskällan har tillräckligt med resurser för att ge en bra upplevelse för användare. En bra upplevelse innebär att visuella objekt bör uppdateras på 5 sekunder eller mindre. Du bör också följa prestandaråden i artikeln [använd DirectQuery i Power BI](desktop-directquery-about.md). Sammansatta modeller lägger till ytterligare prestandaöverväganden, eftersom ett enda visuellt objekt kan resultera i att frågor skickas till flera källor och ofta skickas resultaten vidare från en fråga till en andra källa. Den här situationen kan resultera i följande möjliga typer av körning:

* **En SQL-fråga som innehåller ett stort antal literala värden** – till exempel ett visuellt objekt som begär total *Försäljningsmängd* (från SQL-databasen) för en vald uppsättning *Produktansvariga* (från den relaterade tabellen som importerades från ett kalkylblad) skulle först behöva hitta vilka *Produkter* som hanterades av de Produktansvariga innan den skickar en SQL-fråga, inklusive alla produkt-ID i en *WHERE*-sats.

* **En SQL-fråga som frågar på en lägre detaljnivå, där data sammanställs lokalt** – med samma exempel som föregående punkt i listan, eftersom antalet *Produkter* som uppfyller filtret på *Produktansvarig* blir väldigt stort, blir det vid någon punkt ineffektivt eller olämpligt att inkludera dem i en *WHERE*-sats. Det är istället nödvändigt att fråga relationskällan på den lägre nivån av *Produkt* och därefter sammanställa resultaten lokalt. Om kardinaliteten för *Produkter* överskrider en gräns på 1 miljon så kommer frågan att misslyckas.

* **Flera SQL-frågor, en per gruppera efter värde** – när sammanställningen använder **DistinctCount**, grupperade efter en kolumn från en annan källa så behöver du skicka en SQL-fråga per grupp efter värde om den externa källan inte stöder effektiv överföring av många literalvärden som definierar grupperingen. Ett visuellt objekt som till exempel begär ett distinkt antal *CustomerAccountNumber* (från SQL Server-tabellen) efter *Produktansvarig* (från den relaterade tabellen som har importerats från ett kalkylblad) behöver skicka information från tabellen *Produktasvariga* i frågan som skickas till SQL Server. Över andra källor, som Redshift, är det här inte möjligt utan istället blir det en SQL-fråga som skickas per *Försäljningsansvariga* (upp till någon praktiskt gräns, varefter frågan misslyckas). 

Var och ett av dessa fall har sina egna prestandaimplikationer, där de exakta detaljerna varierar för varje datakälla. En bra tumregel är att medan kardinaliteten för de kolumner som används i relationen mellan de två källorn fortfarande är låg (några tusen) så bör inte prestanda påverkas avsevärt. När kardinaliteten växer, måste man ta mer hänsyn till inverkan på den resulterande prestandan. 

Dessutom kan användning av **många-till-många** relationer innebära att separata frågor måste skickas till den underliggande källan för varje total/delsumma, istället för att sammanställa de detaljerade värdena lokalt. Därför måste skickar ett enkelt tabell-visuellt objekt med summor behöva skicka två SQL-frågor istället för en. 

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns några begränsningar för den här versionen av **sammansatta modeller**.

Följande (flerdimensionella) Live-anslutningskällor kan inte användas med **sammansatta modeller**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-datauppsättningar
* Azure Analysis Services

När du ansluter till de flerdimensionella källorna med DirectQuery, kan du inte också ansluta till en annan DirectQuery-källa eller kombinera med importerade data.

De befintliga begränsningarna med att använda DirectQuery gäller fortfarande när du använder **sammansatta modeller**. Många av dessa begränsningarna är nu per tabell, beroende på tabellens **lagringsläge**. En beräknad kolumn på en importerad tabell kan till exempel referera till andra tabeller, men en beräknad kolumn i en DirectQuery-tabell är fortfarande begränsad till att enbart referera till kolumner i samma tabell. Andra begränsningar gäller för modellen som helhet, om någon av tabellerna inom modellen är DirectQuery. Funktionerna **QuickInsights** och **Q & A** är till exempel inte tillgängliga på en modell om någon av tabellerna i den har **lagringsläget** DirectQuery. 

## <a name="next-steps"></a>Nästa steg

Följande artiklar beskriver mer om sammansatta modeller och beskriver DirectQuery i detalj.

* [Många-till-många-relationer i Power BI Desktop (förhandsversion)](desktop-many-to-many-relationships.md)
* [Lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md)

DirectQuery-artiklar:

* [Använd DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery i Power BI](desktop-directquery-data-sources.md)

