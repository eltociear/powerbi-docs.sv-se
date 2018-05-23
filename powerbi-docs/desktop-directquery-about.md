---
title: Använda DirectQuery i Power BI
description: Förstå hur man använder DirectQuery med Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 472be555bb4c46da41eb762c1eeae14ef991e742
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="using-directquery-in-power-bi"></a>Använda DirectQuery i Power BI
Du kan ansluta till alla typer av olika datakällor när du använder **Power BI Desktop** eller **Power BI-tjänsten**, och du kan göra dessa dataanslutningar på olika sätt. Du kan antingen *importera* data till Power BI, vilket är det vanligaste sättet att hämta data på, eller så kan du ansluta direkt till informationen i dess ursprungliga källdatabas, vilket kallas **DirectQuery**. Den här artikeln beskriver **DirectQuery** och dess funktioner, däribland följande avsnitt:

* Olika anslutningsalternativ för DirectQuery
* Riktlinjer för när du bör använda DirectQuery i stället för import
* Nackdelar med att använda DirectQuery
* Bästa praxis för att använda DirectQuery

Bästa praxis när det gäller om man ska använda import eller DirectQuery är i korthet följande:

* Du bör **importera** data till Power BI närhelst det är möjligt. Då utnyttjar du den högpresterande frågemotorn i Power BI och du får tillgång till en mycket interaktiv och funktionsrik hantering av dina data.
* Om det av någon anledning inte fungerar för dig att importera data, så bör du använda **DirectQuery**. Om dina data t.ex. ändras ofta, och rapporterna måste spegla senaste data, då kan DirectQuery vara det bästa alternativet. Men att använda DirectQuery är oftast bara möjligt när den underliggande datakällan kan tillhandahålla interaktiva frågor (mindre än 5 sekunder) för vanliga mängdfrågor, och kan hantera den frågebelastning som genereras. Du bör dessutom noga läsa igenom listan över de begränsningar som omger användningen av DirectQuery, och på så vis försäkra dig om att du kan uppfylla dina mål.

Den uppsättning funktioner som Power BI erbjuder för båda anslutningslägena – import respektive DirectQuery – kommer att utvecklas med tiden. Detta gäller bl.a. större flexibilitet vid användning av importerade data, så att import kan användas i fler fall, och att några av nackdelarna med att använda DirectQuery kan elimineras. Oavsett dessa förbättringar så är den underliggande datakällans prestanda alltid av högsta vikt när du använder DirectQuery. Om den underliggande datakällan är långsam så är det inte lämpligt att använda DirectQuery.

Det här avsnittet beskriver DirectQuery med Power BI och inte SQL Server Analysis Services. DirectQuery är också en funktion i **SQL Server Analysis Services**, och många detaljer som beskrivs nedan gäller även där, men det finns viktiga skillnader. Information om hur du använder DirectQuery med SQL Server Analysis Services finns i [det white paper som beskriver DirectQuery i SQL Server Analysis Services 2016](http://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

Den här artikeln fokuserar på det rekommenderat arbetsflöde för DirectQuery, där rapporten skapas i **Power BI Desktop**, men tar även upp direktanslutning i **Power BI-tjänsten**.

## <a name="power-bi-connectivity-modes"></a>Power BI-anslutningslägen
Power BI ansluter till ett mycket stort antal olika datakällor, bl.a. följande:

* Online-tjänster (Salesforce, Dynamics 365 m.fl.)
* Databaser (SQL Server, Access, Amazon Redshift m.fl.)
* Enkla filer (Excel, JSON, m.fl.)
* Andra datakällor (Spark, webbplatser, Microsoft Exchange, m.fl.)

För dessa källor går det oftast att importera data till Power BI. För vissa är det också möjligt att ansluta med DirectQuery. Exakt vilka källor som stöder DirectQuery beskrivs i artikeln [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md). Fler källor kommer att bli DirectQuery-kompatibla i framtiden, i synnerhet sådana som kan förväntas leverera bra interaktiva frågeprestanda.

**SQL Server Analysis Services** är ett specialfall. När du ansluter till SQL Server Analysis Services kan du importera data eller använda en *live-anslutning*.  Att använda en live-anslutning påminner om att använda DirectQuery, eftersom inga data importeras och den underliggande datakällan alltid tillfrågas när ett visuellt objekt ska uppdateras, men en *live-anslutning* är annorlunda i många andra avseenden, så därför används en annan term (*live* istället för *DirectQuery*).

Dessa tre alternativ för att ansluta till data – **importera**, **DirectQuery** och **live-anslutning** – beskrivs i detalj i följande avsnitt.

### <a name="import-connections"></a>Importanslutningar
När du använder **Hämta data** i **Power BI Desktop** för att ansluta till en datakälla som SQL Server, och väljer **Import**, så upprättar du en anslutning av följande slag:

* När du väljer **Hämta data** så definierar var och en av de tabeller du har valt en fråga som returnerar en uppsättning data. Du kan redigera dessa frågor innan du hämtar data, t.ex. genom att använda filter, aggregera data eller koppla ihop olika tabeller.
* Vid inläsningen importeras alla de data som definieras av frågorna till Power BI-cachen.
* När du skapar ett visuellt objekt i **Power BI Desktop** skickas frågor till dessa importerade data. Power BI-arkivet garanterar att frågorna ställs mycket snabbt, så därför återspeglas alla ändringar i det visuella objektet direkt.
* Eventuella ändringar i underliggande data visas inte i det visuella objektet. Du måste *uppdatera*, så att data importeras på nytt.
* När du publicerar rapporten (.pbix-filen) i **Power BI-tjänsten**, så skapas en datauppsättning som överförs till Power BI-tjänsten.  Importerade data inkluderas i den datauppsättningen. Efter det är det möjligt att schemalägga uppdateringar av dessa data, t.ex. för att återimportera informationen varje dag. Beroende på den ursprungliga datakällans plats kan det vara nödvändigt att konfigurera en lokal datagateway.
* När du öppnar en befintlig rapport i **Power BI-tjänsten**, eller skapar en ny rapport, så frågas dessa data igen, vilket garanterar interaktivitet.
* Visuella objekt, eller hela rapportsidor, kan fästas på instrumentpaneler. Panelerna uppdateras automatiskt varje gång den underliggande datauppsättningen uppdateras.  

### <a name="directquery-connections"></a>DirectQuery-anslutningar
När du använder **Hämta data** i **Power BI Desktop** för att ansluta till en datakälla, och väljer **DirectQuery**, så upprättar du en anslutning av följande slag:

* Först, när du har valt **Hämta data**, så väljs en datakälla. Detta innebär, när det gäller relationella källor, att en uppsättning tabeller har valts, och att var och en av dem fortfarande definierar en fråga som logiskt returnerar en uppsättning data. När det gäller flerdimensionella källor som SAP BW väljs bara källan.
* Men vid inläsningen importeras i själva verket inga data till Power BI-arkivet. I stället för att ett visuellt objekt skapas i **Power BI Desktop**, så skickas frågor till den underliggande datakällan, så att nödvändiga data kan hämtas. Den tid det sedan tar att uppdatera det visuella objektet beror på den underliggande datakällans prestanda.
* Eventuella ändringar i underliggande data visas inte direkt i det visuella objektet. Det är ändå nödvändigt att uppdatera, och då skickas de nödvändiga frågorna igen för varje visuellt objekt, och detta uppdateras när så är nödvändigt.
* När rapporten publiceras i **Power BI-tjänsten** resulterar det återigen i en datauppsättning i Power BI-tjänsten, precis som vid import. *Inga data* ingår dock med den datauppsättningen.
* När du öppnar en befintlig rapport i **Power BI-tjänsten**, eller skapar en ny, frågas återigen den underliggande datakällan, så att nödvändiga data kan hämtas. Beroende på den ursprungliga datakällans plats kan det vara nödvändigt att konfigurera en lokal datagateway, som kan behövas i importläge om data uppdateras.
* Visuella objekt, eller hela rapportsidor, kan fästas på instrumentpaneler. För att säkerställa att en instrumentpanel öppnas snabbt, så uppdateras panelerna automatiskt enligt ett fastlagt schema (t.ex. varje timma). Du kan kontrollera den här uppdateringens frekvens, så att den reflekterar hur ofta data ändras, och därför att det är viktigt att se den allra senaste informationen. När du öppnar en instrumentpanel, avspeglar alltså panelerna data som de såg ut vid tiden för den senaste uppdateringen, och inte nödvändigtvis de allra senaste ändringarna i den underliggande datakällan. Du kan alltid uppdatera en öppen instrumentpanel så att den hålls uppdaterad.    

### <a name="live-connections"></a>Live-anslutningar
När du ansluter till **SQL Server Analysis Services** (SSAS) kan du välja att importera data från, eller live-ansluta till, den valda datamodellen. Om du väljer **importera** så definierar du en fråga för den externa SSAS-källan, och data importeras som vanligt. Om du väljer **live-anslutning** så definieras inte någon fråga, och hela den externa modellen visas i fältlistan. Om du väljer **DirectQuery**, när visuella objekt skapas, så skickas frågorna till den externa SSAS-källan. Till skillnad från vad som är fallet med DirectQuery, så skapas dock ingen ny *modell*. Det är med andra ord inte möjligt att definiera nya beräknade kolumner, hierarkier, relationer osv. Istället ansluter du helt enkelt direkt till den externa SSAS-modellen.

Den situation som beskrivs i föregående stycke gäller vid anslutning även till följande källor, förutom att det inte finns något alternativ för att importera data:

* Power BI-datauppsättningar (när du t.ex. ansluter till en Power BI-datauppsättning som tidigare har skapats och publicerats i tjänsten för att skapa en ny rapport över den)
* Common Data Services

Rapporter via SSAS vid publicering till **Power BI-tjänsten** liknar DirectQuery-rapporter på följande sätt:

* När du öppnar en befintlig rapport i **Power BI-tjänsten** eller redigerar en ny rapport, så frågas den underliggande SSAS-källan (vilket kan kräva en lokal datagateway)
* Instrumentpaneler uppdateras automatiskt enligt ett schema (t.ex. varje timma eller vilken frekvens som nu har valts)

Det finns dock viktiga skillnader, som t.ex. den att vid live-anslutningar så skickas alltid identiteten för den som öppnar rapporten till den underliggande SSAS-källan.

När vi nu är klara med dessa jämförelser kan vi fortsättningsvis helt fokusera på **DirectQuery** i den här artikeln.

## <a name="when-is-directquery-useful"></a>När är DirectQuery användbart?
I följande tabell beskrivs scenarier där anslutning med DirectQuery kan vara användbart, inklusive sådana fall där det kan ses som fördelaktigt att lämna data i den ursprungliga källan. Beskrivningen innehåller en diskussion om huruvida det angivna scenariot är tillgänglig i Power BI.

| Begränsning | Beskrivning |
| --- | --- |
| Data ändras ofta, och rapportering i näst intill realtid behövs |Modeller med importerade data kan uppdateras högst en gång i timman. Därför om data ändras kontinuerligt, och det är nödvändigt för rapporter att visa den senaste informationen, kan det därför vara så att import med schemalagd uppdatering helt enkelt inte uppfyller dessa behov. Observera att det också är möjligt att sända data direkt till Power BI, även om det i detta fall finns begränsningar när det gäller vilka datavolymer som stöds. <br/> <br/> Om du använder DirectQuery innebär det däremot att varje gång du öppnar eller uppdaterar en rapport eller instrumentpanel, så visas alltid den senaste informationen i källan. Instrumentpanelens paneler kan dessutom uppdateras oftare (så ofta som var 15:e minut). |
| Data är mycket omfattande |Om det rör sig om mycket stora datamängder, då är det självklart inte möjligt att importera allt. DirectQuery kräver däremot inga större dataöverföringar, eftersom frågorna gör på plats. <br/> <br/> Stora mängder data kan dock innebära att prestanda för frågor mot den underliggande källan blir för långsamma (mer information finns i avsnittet *Effekterna av att använda DirectQuery* längre fram i den här artikeln). Och naturligtvis är det inte alltid nödvändigt att importera alla data i detalj. I stället kan dessa data preaggregeras under importen, något som med fördel kan göras av **Frågeredigeraren**. I yttersta fall skulle det gå att importera exakt de aggregerade data som behövs för respektive virtuellt objekt. Så även om det är enklast att använda DirectQuery när man vill hantera stora datamängder, så bör du alltid ha i åtanke att import av aggregerade data kan vara en lösning om den underliggande källan är för långsam. |
| Säkerhetsregler definieras i den underliggande datakällan |När data importeras ansluter Power BI till datakällan med den aktuella användarens autentiseringsuppgifter (från Power BI Desktop) eller de autentiseringsuppgifter som har definierades när den schemalagda uppdateringen konfigurerades (från Power BI-tjänsten). När du publicerar och delar en sådan rapport måste du därför vara noga med att bara dela den med användare som har tillåtelse att se dessa data, eller med att definiera säkerhet på radnivå som en del av datauppsättningen. <br/> <br/> Eftersom DirectQuery alltid frågar den underliggande datakällan, skulle detta innebära att all eventuell säkerhet i den underliggande källan ska tillämpas. Idag ansluter dock Power BI alltid till den underliggande källan med samma autentiseringsuppgifter som används för import. <br/> <br/> Det innebär att fram till det att Power BI låter rapportkonsumentens identitet skickas till den underliggande källan, så erbjuder DirectQuery inte några fördelar avseende datakällans säkerhet. |
| Begränsningar för datasuveränitet gäller |Vissa organisationer har principer avseende datasuveränitet, vilket innebär att dessa data inte tillåts lämna organisationen lokaler. En lösning baserad på import skulle i sådana fall utgöra ett uppenbart problem. Men med DirectQuery skulle dessa data finnas kvar i den underliggande datakällan. <br/> <br/> Tänk dock på att vissa cacheminnen av data på visuell objektnivå ligger kvar i Power BI-tjänsten (pga den schemalagda uppdateringen av panelerna). |
| Den underliggande datakällan är en OLAP-källa som innehåller åtgärder |Om den underliggande datakällan innehåller *mått* (t.ex. SAP HANA eller SAP Business Warehouse), så innebär import av data andra problem. Det innebär att de data som importeras ligger på en viss aggregeringsnivå, som definieras av frågan. Mått t.ex. Total försäljning per klass, år och stad. Om ett visuellt objekt sedan skapas baserat på en högre aggregeringsnivå (t.ex. Total försäljning per år) så aggregeras aggregeringsvärdet ytterligare. Det här är bra för additiva mått (t.ex Sum, Min) men utgör ett problem för icke-additiva mått (t.ex. Average, DistinctCount). <br/> <br/> Om du vill göra det enklare att hämta rätt aggregeringsdata (som behövs för de specifika visuella objekten) direkt från källan, så måste du skicka frågorna per visuellt objekt, som i DirectQuery. <br/> <br/> Om du väljer DirectQuery när du ansluter till SAP Business Warehouse (BW), så möjliggör du den här hanteringen av mått. Stöd för SAP BW beskrivs ytterligare i [DirectQuery och SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> Men för närvarande behandlar DirectQuery via SAP HANA källan som en relationskälla och importerar på samma sätt. Detta beskrivs ytterligare i [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md). |

Så sammanfattningsvis, givet de aktuella funktionerna i DirectQuery i Power BI, är de scenarier där det medför fördelar följande:

* Data ändras ofta, och rapportering i näst intill realtid behövs
* Hantering av mycket stora datamängder utan att de behöver aggregeras i förväg
* Begränsningar för datasuveränitet gäller
* Källan är en flerdimensionell källa som innehåller mått (t.ex. SAP BW)

Observera att informationen i listan ovan gäller för användning av enbart Power BI. Det finns alltid möjlighet att använda en extern modell för SQL Server Analysis Services (eller Azure Analysis Services) för att importera data och sedan använda Power BI för att ansluta till den modellen. Denna metod kräver visserligen ytterligare kunskaper, men ger den ger större flexibilitet. Det går t.ex. att importera mycket större datamängder och det finns ingen begränsning för hur ofta data kan uppdateras.

## <a name="implications-of-using-directquery"></a>Effekter av att använda DirectQuery
Att använda **DirectQuery** kan ha potentiellt negativa effekter, så som beskrivs i det här avsnittet. Vissa av dessa begränsningar kan variera beroende på vilken källa som används. Detta påtalas där så är fallet, och de källor som avviker markant behandlas i separata avsnitt.  

### <a name="performance-and-load-on-the-underlying-source"></a>Prestanda och belastning på den underliggande källan
När du använder **DirectQuery**, är den övergripande processen väldigt beroende på den underliggande datakällans prestanda. Om uppdateringen av varje enskilt visuellt objekt (t.ex. när du har ändrat ett utsnittsvärde) tar några sekunder (< 5 sek) så är det acceptabelt, men kan fortfarande upplevas som långsamt jämfört med den omedelbara respons vi är vana vid när vi importerar data till Power BI. Om källans långsamhet däremot leder till att de enskilda visuella objekten tar ännu längre tid att importera (tio sekunder eller mer), då är mycket dåligt, och det kan gå så långt att frågorna når sin tidsgräns.

Förutom den underliggande källans prestanda, bör du vara uppmärksam på vilken belastning den utsätts för (vilket naturligtvis i hög grad påverkar dess prestanda). Som vi diskuterar längre fram så skickas minst en fråga per visuellt objekt till den underliggande källan varje gång en användare öppnar en delad rapport eller när en instrumentpanel uppdateras. Detta kräver att källan ska kunna hantera en sådan frågebelastning, men samtidigt kunna uppvisa rimliga prestanda.

### <a name="limited-to-a-single-source"></a>Begränsad till en enda källa
När du importerar data är det möjligt att kombinera data från flera källor till en enskild modell, som när du t.ex. enkelt vill kunna ansluta till vissa data från en SQL Server-företagsdatabas med vissa lokala data i en Excel-fil. Detta är inte möjligt när du använder DirectQuery. När du väljer DirectQuery för en källa kan du sedan bara använda data från den enskilda källan (t.ex. en SQL Server-databas).

### <a name="limited-data-transformations"></a>Begränsade datatransformationer
Det finns på samma sätt, begränsningar när det gäller vilka datatransformationer som kan användas i **Frågeredigeraren**. Med importerade data kan du enkelt använda en avancerad uppsättning transformationer för att rensa och transformera data innan du använder dem för att skapa visuella objekt (t.ex. parsa JSON-dokument eller pivotera data från en kolumn till ett radorienterat formulär). Dessa transformationer är mer begränsade i DirectQuery. När du först ansluter till en OLAP-källa som SAP Business Warehouse går det inte att definiera några transformationer överhuvudtaget, och hela den externa modellen hämtas från källan. Det är fortfarande möjligt att definiera en uppsättning transformationer per fråga för relationskällor som SQL Server, men dessa transformationer är begränsade av prestandaskäl. Sådana transformationer måste tillämpas på varje fråga till den underliggande källan, snarare än en gång vid datauppdatering, så de är begränsad till de transformationer som rimligen kan översättas till ett enda intern fråga. Om du använder en transformation som är för komplex, får du ett fel som måste tas bort eller så växlar modellen till importläge.

Dessutom används den fråga som är resultatet av dialogrutan **Hämta data** eller **Frågeredigeraren** i en markering i de frågor som genererats och skickas för att hämta nödvändiga data för ett visuellt objekt. Den fråga som definierats i Frågeredigeraren måste därför vara giltig i den här kontexten. Detta innebär i synnerhet att det inte går inte att använda en fråga med vanliga tabelluttryck eller en fråga som anropar lagrade procedurer.

### <a name="modeling-limitations"></a>Modelleringsbegränsningar
Termen *modellering* innebär i den här kontexten att rådata förfinas och berikas som en del av redigeringen av rapporten som använder dem. Exempel:

* Definiera relationer mellan tabeller
* Lägga till nya beräkningar (beräknade kolumner och mått)
* Byta namn på och dölja kolumner och mått
* Definiera hierarkier
* Definiera en kolumns formatering, standardsammanfattning och sorteringsordning
* Grupperings- eller klustringsvärden

När du använder **DirectQuery** kan många av dessa modellberikningar fortfarande göras, och fortfarande gäller principen att rådata berikas för att förbättra senare användning. Vissa modelleringsfunktioner är dock inte tillgängliga, eller begränsas, när DirectQuery används. Begränsningar tillämpas vanligtvis för att undvika prestandaproblem. Uppsättningen med begränsningar som är gemensam för alla DirectQuery-källor listas i följande punktlista. Ytterligare begränsningar kan gälla för enskilda datakällor, så som beskrivs i *Datakällsspecifik information* mot slutet av den här artikeln.

* **Ingen inbyggd datumhierarki:** När du importerar data får varje datum/datetime-kolumn som standard en tillgänglig inbyggd datumhierarki. Om du t.ex. importerar en tabell med försäljningsorder, som innehåller kolumnen OrderDate, och sedan använder OrderDate i ett visuellt objekt, så kan du välja lämplig nivå (år, månad, dag) att använda. Denna inbyggda datumhierarki är inte tillgänglig när du använder DirectQuery-läge. Observera dock att om det finns en tillgänglig datumtabell i den underliggande källan (som är vanligt i många datalager), så kan sedan DAX-tidsinformationsfunktionerna användas som vanligt.
* **Begränsningar i beräknade kolumner:** Beräknade kolumner är begränsade till att bara kunna hänvisa till värden på andra kolumner i samma tabell, utan att några aggregeringsfunktioner används. De tillåtna DAX-skalärfunktionerna (som t.ex. LEFT()) begränsas dessutom till dem som bara kan skickas till den underliggande källan, och varierar därför beroende på källans exakta funktioner. Funktioner som inte stöds listas inte vid automatisk komplettering när du redigerar DAX för en beräknad kolumn, och de skulle resultera i ett fel om de användes.
* **Inget stöd för överordnade-underordnade DAX-funktioner:** I DirectQuery-modellen går det inte att de DAX-PATH()-funktioner, som normalt hanterar strukturer med överordnad-undererordnad (som i t.ex. kontoplaner eller organisationshierarkier).
* **Måttbegränsningar (standard):** Som standard är de DAX-funktioner och -uttryck som kan användas i mått begränsade. Återigen så begränsar automatisk komplettering de funktioner som listas, och ett fel inträffar om en ogiltig funktion eller uttryck används. Skälet är helt enkelt att säkerställa att åtgärderna som standard är begränsade till enkla åtgärder som på egen hand sannolikt inte kan orsaka några prestandaproblem. Avancerade användare kan välja att kringgå den här begränsningen genom att välja **Arkiv > Alternativ och inställningar > Alternativ** och sedan **DirectQuery**, följt av alternativet *Tillåt obegränsade åtgärder i DirectQuery-läge*. När du väljer det alternativet kan du använda DAX-uttryck som gäller för ett mått. Användarna måste dock vara medvetna om att vissa uttryck som fungerar bra när data importeras kan resultera i mycket långsamt frågor till serverdelskällan i DirectQuery-läge.
  
  * Exempel:
    
    * Det skulle vara möjligt att skapa en åtgärd som helt enkelt summerar försäljningsbeloppet:
      
          SalesAmount = SUMX(Web_Sales, [ws_sales_price]* [ws_quantity])
    * Det skulle *inte* vara möjligt att skapa en åtgärd som sedan utgjorde ett SalesAmount-genomsnitt för alla objekt:
      
          AverageItemSalesAmount = AVERAGEX('Item', [SalesAmount])
    
    Anledningen är att en sådan åtgärd kan resultera i sämre prestanda om det finns ett stort antal objekt.
* **Beräknade tabeller stöds inte:** Möjligheten att definiera en beräknad tabell med hjälp av ett DAX-uttryck stöds inte i DirectQuery-läge.
* **Relationsfiltrering är begränsat till en riktning:** När du använder DirectQuery gå det inte att ställa in korsfiltreringsriktningen för en relation till ”båda”. Med de tre tabellerna nedan skull det inte vara möjligt att skapa ett visuellt objekt som visar varje kund [kön] och det antal av en produkt [kategori] som var och en har köpt. Användning av sådan dubbelriktad filtrering beskrivs [i detta detaljerade white paper](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional cross-filtering in Analysis Services 2016 and Power BI.docx) (här presenteras exempel i SQL Server Analysis Services-kontext, men de grundläggande punkterna gäller lika mycket för Power BI).
  
  ![](media/desktop-directquery-about/directquery-about_01.png)
  
  Återigen orsakas begränsningen av prestandaskäl. En särskilt viktig tillämpning av detta är när du definierar säkerhet på radnivå som en del av rapporten, som ett gemensamt mönster av en många-många-relation mellan användarna och de enheter de har åtkomst till, och då dubbelriktad filtrering krävs för att åstadkomma detta. Dubbelriktad filtrering för DirectQuery-modeller bör dock användas sparsamt, och med stor uppmärksamhet på eventuell skadlig inverkan på prestanda.  
* **Ingen klustring:** När du använder DirectQuery gå det inte att använda klustringskapaciteten för att automatiskt söka efter grupper

### <a name="reporting-limitations"></a>Rapporteringsbegränsningar
Nästan alla rapporteringsfunktioner stöds för DirectQuery-modeller. Så länge som den underliggande källan erbjuder en lämplig prestandanivå kan samma uppsättning visualiseringar användas. Det finns dock några viktiga begränsningar i några av de funktioner som erbjuds i **Power BI-tjänsten** efter det att en rapport har publicerats, så som beskrivs i följande punkter:

* **Quick Insights stöds inte:** Power BI Quick Insights söker igenom olika delmängder av din datauppsättning och tillämpar samtidigt en uppsättning avancerade algoritmer för att identifiera potentiellt intressanta insikter. På grund av de höga prestandakraven är den här funktionen tillgänglig för datauppsättningar som använder DirectQuery.
* **Frågor och svar stöds inte:** Med frågor och svar i Power BI kan du utforska dina data med hjälp av intuitiva, naturliga språkfunktioner och få svar i form av tabeller och diagram. Funktionen stöds för närvarande dock inte för datauppsättningar som använder DirectQuery.
* **Använda Utforska i Excel resulterar sannolikt i sämre prestanda:** Det är möjligt att utforska dina data genom att använda funktionen Utforska i Excel för en datauppsättning. Detta gör det möjligt att skapa Pivot-tabeller och Pivot-diagram i Excel. Även om den här funktionen stöds för datauppsättningar som använder DirectQuery, så prestanda vanligtvis långsammare jämfört med om du skapar visuella objekt i Power BI. Därför, om det är viktigt för dig att använda Excel i dina scenarier, bör du ta detta i beaktande i ditt beslut att använda DirectQuery.

### <a name="security"></a>Säkerhet
Som har diskuterats tidigare i den här artikeln så kommer en rapport som använder **DirectQuery** alltid att använda samma fasta autentiseringsuppgifter för att ansluta till den underliggande datakällan, efter publicering i **Power BI-tjänsten**. Observera återigen att detta specifikt refererar till DirectQuery, och inte till live-anslutningar till SQL Server Analysis Services, som avviker i detta avseende. Därför är det nödvändigt att omedelbart efter det att en DirectQuery-rapport har publicerats, konfigurera autentiseringsuppgifterna för den användare som ska användas. Så länge det inte har gjorts så resulterar varje försök att öppna rapporten i Power BI-tjänsten i ett fel.

När användarens autentiseringsuppgifter har tillhandahållits används de, *oavsett vilken användare som öppnar rapporten*. I detta avseende fungerar det precis som med importerade data, i det att varje användare ser samma data, såvida inte säkerhet på radnivå har definierats som en del av rapporten. Därför måste samma uppmärksamhet fästas på att dela rapporten, ifall det skulle finnas några definierade säkerhetsregler i den underliggande datakällan.

### <a name="behavior-in-the-power-bi-service"></a>Beteende i Power BI-tjänsten
I det här avsnittet beskrivs hur en **DirectQuery**-rapport i **Power BI-tjänsten** fungerar. Det primära syftet är att du ska förstå graden av belastning som placeras på ursprungsdatakällan, givet det antal användare som rapporten och instrumentpanelen kommer att delas med, rapportens komplexitet och huruvida säkerhet på radnivå har definierats i rapporten.

#### <a name="reports--opening-interacting-with-editing"></a>Rapporter – öppna, interagera med, redigera
När en rapport öppnas uppdateras alla visuella objekt på den sida som visas. Varje visuellt objekt kräver vanligtvis minst en fråga till den underliggande datakällan. Vissa visuella objekt kan kräva mer än en fråga (om det t.ex. visar sammanställda värden från två olika faktatabeller eller innehåller ett mer komplext mått eller summor för ett icke-additivt mått som Count Distinct). Om du flyttar till en ny sida så leder det till att dessa visuella objekt uppdateras, vilket resulterar i en ny uppsättning frågor till den underliggande källan.

Varje användaråtgärd i rapporten kan resultera i att visuella objekt uppdateras. Om du t.ex. väljer ett annat värde på ett utsnitt så krävs det att en ny uppsättning frågor skickas för att uppdatera alla de berörda visuella objekten. Detsamma gäller om du klickar på något visuellt objekt för att korsmarkera andra visuella objekt, eller ändrar ett filter.  

Om du redigerar en ny rapport krävs naturligtvis på motsvarande sätt att frågor skickas för varje steg på vägen mot att ta fram det slutgiltiga önskade visuella objektet.

Viss cachelagring av resultaten görs, så att uppdateringen av ett visuellt objekt sker direkt om exakt samma resultat nyligen har erhållits. Dessa cacheminnen delas inte mellan användare, om säkerhet på radnivå som har definierats som en del av rapporten.

#### <a name="dashboard-refresh"></a>Uppdatering av instrumentpanelen
Enskilda visuella objekt, eller hela sidor, kan fästas på instrumentpanelen som paneler. Paneler som baseras på **DirectQuery**-datauppsättningar uppdateras sedan automatiskt enligt ett schema, vilket resulterar i att frågor skickas till ursprungsdatakällan. Detta sker som standard varje timma, men kan konfigureras som en del av datauppsättningsinställningarna från ett veckovis intervall ned till var 15:e minut.

Om ingen säkerhet på radnivå har definierats i modellen, så innebär det att varje panel skulle uppdateras en gång och att resultatet skulle delas mellan alla användare. Om säkerhet på radnivå har definierats kan det medföra att frågorna mångdubblas – varje panel kräver att separata frågor skickas per användare till den underliggande källan.  

En instrumentpanel med tio paneler, som delas med 100 användare, och som skapats utifrån en datauppsättning med hjälp av **DirectQuery** med säkerhet på radnivå, och konfigurerats för att uppdateras var 15:e minut, skulle därför leda till att minst 1000 frågor skulle skickas var 15:e minut till ursprungskällan.

Därför måste du vara mycket uppmärksam på användningen av säkerhet på radnivå och uppdateringsschemats konfiguration.

#### <a name="timeouts"></a>Tidsgränser
En tidsgräns på fyra minuter tillämpas på enskilda frågor i **Power BI-tjänsten**, och frågor som tar längre tid än så blir resultatlösa. Som tidigare betonats, så rekommenderar vi att DirectQuery används för källor som ger nästintill interaktiva frågeprestanda, så syftet med den här gränsen är att förhindra alltför långa körningstider.

### <a name="other-implications"></a>Andra effekter
Några andra allmänna effekter av att använda **DirectQuery** är följande:

* **Om data ändras, måste en uppdatering göras, så att senaste data visas:** Givet användningen av cacheminnen är det inte säkert att det visuella objektet alltid visar den senaste informationen. Ett visuellt objekt kan t.ex. visa den senaste dagens transaktioner. På grund av att ett utsnitt har ändrats kan objektet komma att uppdateras, så att transaktionerna för de senaste två dagarna visas, inklusive några helt nya och nyligen gjorda transaktioner. Om du skulle returnera utsnittet till sitt ursprungliga värde skulle det leda till att det visade det cachelagrade värde som hämtats tidigare, och det skulle inte omfatta de nyligen gjorda transaktionerna.
  
  Om du väljer Uppdatera rensas alla cacheminnen bort, och alla visuella objekt på sidan uppdateras och visar senaste data.
* **Om data ändras, finns det ingen garanti för att det ska råda samstämmighet mellan de visuella objektet:** Olika visuella objekt, oavsett om de är på samma sida eller olika sidor, kan komma att uppdateras vid olika tidpunkter. Om informationen i den underliggande källan ändras så finns det följaktligen ingen garanti för att varje visuellt objekt visar samma data vid exakt samma tidpunkt. Med tanke på att det ibland faktiskt krävs mer än en fråga för ett enskilt visuellt objekt (t.ex. detaljerad information och totalsumma), så kan inte ens enhetligheten i ett och samma visuella objekt garanteras. En sådan garanti skulle innebära att alla visuella objekt måste uppdateras varje gång som något enskilt visuellt objekt uppdateras tillsammans med användandet av kostsamma funktioner som ögonblicksbildisolering i den underliggande datakällan.
  
  Det här problemet kan du minimera i stor utsträckning genom att återigen välja Uppdatera, så att alla visuella objekt på sidan uppdateras. Och det bör noteras att även om du använder importläge, så finns det ett liknande problem med att garantera konsekvens om du importerar från mer än en tabell.
* **Att uppdatera i Power BI Desktop är nödvändigt för att man ska kunna återspegla ändringar i metadata:** När du använder Uppdatera efter det att en rapport har publicerats uppdateras bara de visuella objekten i rapporten. Om schemat för den underliggande datakällan har ändrats, så tillämpas inte dessa ändringar automatiskt i de tillgängliga fälten i fältlistan. Om tabeller eller kolumner har tagits bort från den underliggande datakällan, så kan detta därför leda till att frågorna misslyckas efter en uppdatering. Om du öppnar rapporten i Power BI Desktop och väljer Uppdatera, så uppdateras fälten i modellen så att dessa ändringar återspeglas.
* **Begränsning till en miljon returnerade rader per fråga:** Det finns en fast gräns på en miljon rader när det gäller hur många rader som kan returneras för en enskild fråga till den underliggande datakällan. Denna begränsning har vanligtvis inga praktiska konsekvenser och de visuella objekten visar inte så många punkter. Gränsen kan dock nås i fall där Power BI inte fullständigt optimerar de frågor som skickas, vilket ger upphov till mellanfrågor som överskrider gränsen. Det kan också inträffa medan ett visuellt objekt skapas, på vägen till ett mer rimligt sluttillstånd. Om t.ex. både Customer och TotalSalesQuantity ingår, så skulle den här gränsen uppnås om det finns mer än 1 miljon kunder innan några filter tillämpats.
  
  Det fel som skulle returneras skulle vara ”Resultatuppsättningen till en fråga riktad till en extern datakälla har överskridit det högsta tillåtna storleken på 1000000 rader.”
* **Det går inte att ändra från importläge till DirectQuery-läge:** Observera att det är vanligtvis möjligt att växla en modell från DirectQuery-läge till importläge, vilket innebär att alla nödvändiga data måste importeras. Det går heller inte att växla tillbaka (främst på grund av en uppsättning funktioner som inte stöds i DirectQuery-läge). DirectQuery-modeller via flerdimensionella källor som SAP BW kan heller inte växlas från DirectQuery till import, eftersom de hanterar externa källor på två helt olika sätt.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery i Power BI-tjänsten
Alla datakällor som stöds från **Power BI Desktop**. Vissa datakällor är också tillgängliga direkt från **Power BI-tjänsten**. Ett företag kan t.ex. använda Power BI för att ansluta till sina data i Salesforce och omedelbart får en instrumentpanel, utan att behöva använda **Power BI Desktop**.

Endast två av de DirectQuery-aktiverade källorna är tillgängliga direkt i tjänsten:

* Spark
* Azure SQL Data Warehouse

Vi rekommenderar dock starkt att all användning av **DirectQuery** med dessa två källor börjar från **Power BI Desktop**. Anledningen är att när anslutningen görs i **Power BI-tjänsten**, så gäller många viktiga begränsningar, vilket innebär att om startpunkten var enkelt (med början i Power BI-tjänsten), så finns det begränsningar när det gäller att förbättra den resulterande rapporten. (Det är t.ex. inte möjligt att därefter skapa några beräkningar eller använda många analytiska funktioner, eller ens att uppdatera metadata så att de återspeglar eventuella ändringar i det underliggande schemat).   

## <a name="guidance-for-using-directquery-successfully"></a>Riktlinjer för att använda DirectQuery
Om du tänker använda **DirectQuery**, så kan du ha hjälp av det här avsnittet som ger vägledning på hög nivå om hur du kan göra detta med framgång. Riktlinjerna i det här avsnittet har härletts utifrån den användning av DirectQuery som har beskrivits i den här artikeln.

### <a name="backend-data-source-performance"></a>Prestanda för ursprungsdatakälla
Vi rekommenderar starkt att du verifierar att enkla visuella objekt kan uppdateras inom rimlig tid. Detta innebär att uppdateringen bör ske inom 5 sekunder för att det ska kännas rimligt. Och en sak som är säker är att om uppdateringen av de visuella objekten ter mer än 30 sekunder, så är det mycket troligt att ytterligare problem kommer att uppstå i samband med publiceringen av rapporten, vilket gör att lösningen inte fungerar.

Om frågorna är långsamma, så är den första punkten att granska de frågor som skickas till den underliggande källan, och orsaken till den frågeprestanda som observeras. Det här avsnittet täcker inte in det breda utbud av bästa praxis för databasoptimeringar för hela uppsättningen av potentiella underliggande källor, men det gäller för de standarddatabasmetoder som gäller i de flesta situationer:

* Relationer som baseras på heltalskolumner har vanligtvis bättre prestanda än kopplingar till kolumner med andra datatyper
* Rätt index ska skapas, vilket vanligtvis innebär att kolumnlagringsindex används i de källor som stöds (t.ex. SQL Server).
* Alla nödvändig statistik i källan ska uppdateras

### <a name="model-design-guidance"></a>Riktlinjer för modelldesign
Tänk på följande när du definierar modellen:

* **Undvik komplexa frågor i Frågeredigeraren.** Den fråga som definieras i frågeredigeraren kommer att översättas till en enskild SQL-fråga som sedan kommer att inkluderas för varje fråga som skickas till tabellen. Om frågan är komplex kan det resultera i prestandaproblem för varje fråga som skickas. Du kan hämta den faktiska SQL-frågan för en uppsättning steg genom att markera det sista steget i frågeredigeraren och välja *Visa inbyggd fråga* på snabbmenyn.
* **Håll det enkelt.** Åtminstone till en början rekommenderar vi att du begränsar åtgärderna till enkla aggregeringar. Om de fungerar på ett tillfredsställande sätt, så kan mer komplexa åtgärder definieras, samtidigt som man är uppmärksam på prestanda för var och en.
* **Undvik relationer för beräknade kolumner.** Detta är särskilt relevant för databaser där det är nödvändigt att genomföra flera flerkolumnskopplingar. Power BI tillåter inte idag att en relation baseras på flera kolumner som FK/PK. Den vanliga lösningen är att man sammanfogar kolumnerna med hjälp av en beräknad kolumn, och baserar kopplingen på den. Även om den här lösningen är rimlig för importerade data, som i fallet med **DirectQuery**, så resulterar den i en koppling till ett uttryck som ofta förhindrar att index används, vilket leder till dåliga prestanda. Det enda sättet att ta sig förbi det här är att materialisera flera kolumner i en enda kolumn i den underliggande databasen.
* **Undvik relationer med kolumner med datatypen uniqueidentifier.** Power BI stöder inte datatypen uniqueidentifier internt. Att definiera en relation mellan kolumner med datatypen uniqueidentifier resulterar därför i en fråga med en koppling som inbegriper en typkonvertering. Även detta leder ofta till dåliga prestanda. Inte förrän det här fallet specifikt har optimerats är den enda lösningen att materialisera kolumner av en annan typ i den underliggande databasen.
* **Dölj *till*-kolumnen i relationer.** *Till*-kolumnen i relationer (vanligtvis den primära nyckeln i *till*-tabellen) ska vara dold, så att den inte visas i listan och därför inte kan användas i visuella objekt. Ofta är de kolumner som baseras på relationer i själva verket *systemkolumner* (t.ex. surrogatnycklar i ett informationslager), och att dölja sådana kolumner är en bra idé. Om kolumnen har betydelse, så använd då en beräknad kolumn som är synlig, och som har ett enkelt uttryck av att vara lika med den primära nyckeln. Till exempel:
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  Orsaken till att man gör så är att man vill undvika de prestandaproblem som kan uppstå annars om ett visuellt objekt innehåller primärnyckelkolumnen.
* **Granska all användning av beräknade kolumner och datatypsändringar.** Att använda dessa funktioner är inte nödvändigtvis skadligt. De resulterar i frågor som skickats till den underliggande källan och innehåller uttryck snarare än enkla referenser till kolumner som kan resultera i att index inte används.  
* **Undvik att använda dubbelriktad korsfiltrering för relationer (förhandsversion).**
* **Experimentera med att ställa in *Anta referensintegritet*.** Inställningen *Anta referensintegritet* för relationer gör det möjligt för frågor för att använda INNER JOIN-instruktioner istället för OUTER JOIN. Detta innebär vanligtvis en allmän förbättring av frågeprestanda, även om det beror datakällans specifika egenskaper.
* **Använd inte relativ datumfiltrering i Frågeredigeraren.** Det är möjligt att definiera relativ datumfiltrering i Frågeredigeraren. Du kan t.ex. filtrera fram de rader där datumet infaller under de senaste 14 dagarna.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  Detta översätts dock till ett filter baserat på fast datum, som vid vilken tidpunkt frågan skapades. Detta ser man om man visar den interna frågan.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Detta är förmodligen inte vad som önskades. Försäkra dig om att filtret tillämpas baserat på det datum då rapporten körs genom att istället tillämpa filtret i rapporten som ett rapportfilter. För närvarande skulle detta göras genom att du skapar en beräknad kolumn som beräknar antalet förfluta dagar (med funktionen DAX DATE()), och sedan använder den beräknade kolumnen i ett filter.

### <a name="report-design-guidance"></a>Riktlinjer för rapportdesign
När du skapar en rapport med en DirectQuery-anslutning måste du tänka på följande:

* **Överväg användning av alternativ för Frågereduktion:** Power BI ger alternativ i rapporten för att skicka färre frågor och för att inaktivera vissa interaktioner som skulle leda till en dålig upplevelse om de resulterande frågorna tar lång tid att köra. Du får åtkomst till alternativen i **Power BI Desktop**, gå till **Fil > Alternativ och inställningar > Alternativ** och välj **Frågereduktion**. 

   ![](media/desktop-directquery-about/directquery-about_03b.png)

    Via kryssrutorna i **Frågereduktion** kan du inaktivera korsmarkering i hela rapporten. Du kan också visa knappen *Tillämpa* vid utsnitts- och/eller filterval där du sedan kan göra många utsnitts- och filterval innan du tillämpar dem, vilket innebär att inga frågor skickas förrän du väljer knappen **Tillämpa** på utsnittet. Dina val kan sedan användas för att filtrera data.

    Dessa alternativ gäller för din rapport medan du använder den i **Power BI Desktop**, samt när användarna använder rapporten i **Power BI-tjänsten**.

* **Använd filter först:** Använd alltid alla tillämpliga filter från början när du skapar ett visuellt objekt. Snarare än att använda TotalSalesAmount och ProductName och sedan filtrera till ett visst år, så använd istället filtret Year redan från början. Detta beror på att varje steg i processen att skapa ett visuellt objekt skickar en fråga, och även om det då är möjligt att göra ytterligare en ändring innan den första frågan har slutförts, så innebär detta fortfarande en onödig belastning på den underliggande källan. Om du använder filter tidigt medför det vanligtvis att dessa mellanliggande frågor blir kostnadseffektivare. Om du skulle undlåta att använda dessa filter tidigt, så kan det dessutom leda till att når gränsen på 1 miljon rader.
* **Begränsa antalet visuella objekt på en sida:** När en sida öppnas (eller vissa sidnivåutsnitt eller filter har ändrats) så uppdateras alla visuella objekt på en sida. Det finns också en gräns för hur många frågor som kan skickas parallellt, och i takt med att antalet visuella objekt ökar, så uppdateras vissa visuella objekt seriellt, vilket ökar den tid det tar att uppdatera hela sidan. Av det skälet rekommenderar vi att du begränsar antalet visuella objekt på en enda sida, och istället har fler, och enklare, sidor.
* **Överväg att stänga av interaktion mellan visuella objekt:** Som standard kan visualiseringar på en rapportsida användas för korsfilter och korsmarkeringar i andra visualiseringar på sidan. Om du t.ex. har valt ”1999” i cirkeldiagrammet, så korsmarkeras stapeldiagrammet så att försäljningen per kategori 1999 visas.                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  I DirectQuery kräver sådan korsfiltrering och korsmarkering att frågorna skickas till den underliggande källan. Det innebär att interaktionen bör stängas av om den tid det tar att svara på användarnas val skulle visa sig bli orimligt lång. Interaktionen kan emellertid stängas av, antingen för hela rapporten (såsom beskrivs ovan för *Alternativ för frågereduktion*), eller på grundval av fall som beskrivs [i den här artikeln](service-reports-visual-interactions.md).

Utöver listan över förslag ovan, så tänk på att följande rapportfunktioner kan orsaka prestandaproblem:

* **Åtgärdsfilter:** Visuella objekt som innehåller åtgärder (eller kolumnaggregat) kan innehålla filter i dessa åtgärder. Det visuella objektet nedan visar t.ex. försäljningsbelopp per kategori, men endast med de kategorier med mer än 20 miljoners försäljning.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Detta leder till två frågor skickas till den underliggande datakällan:
  
  * Den första frågan hämtar de kategorier som uppfyller villkoret (försäljning > 20 miljoner)
  * Den andra frågan hämtar sedan nödvändig information för det visuella objektet, inklusive de kategorier som uppfyller villkoret i WHERE-satsen.  
  
  Detta fungerar i allmänhet utmärkt om det finns hundratals eller tusentals kategorier, som i det här exemplet. Prestanda kan försämras om antalet kategorier är mycket större (och frågan riskerar faktiskt att misslyckas om det finns mer än en miljon kategorier som uppfyller villkoret, vilket beror på den gräns på en miljon rader som diskuterats ovan).
* **TopN-filter:** Avancerade filter kan definieras till att filtrera enbart på de översta (eller nedersta) N-värdena rangordnade efter ett visst mått, så att t.ex. enbart de 10 översta kategorigerna i det visuella objektet ovan inkluderas. Detta leder återigen till att två frågor skickas till den underliggande datakällan. Den första frågan returnerar dock alla kategorier från den underliggande källan, och sedan fastställs TopN-värdena utifrån de returnerade resultaten. Detta kan leda till problem med prestanda beroende på kolumnens kardinalitet (eller till frågefel som beror på gränsen på 1 miljon rader).
* **Medianvärdet:** Normalt skickas alla aggregeringar (Sum, Count Distinct osv) till den underliggande källan. Men detta gäller inte för Median, eftersom den här aggregeringen vanligtvis inte stöds av den underliggande datakällan. I sådana fall hämtas detaljerade data från den underliggande källan och medianvärdet beräknas från de returnerade resultaten. Detta är rimligt när medianvärdet ska beräknas för ett relativt litet antal resultat, men prestandaproblem (eller frågefel som beror på begränsningen på 1 miljon rader) uppstår om kardinaliteten är stor.  Median Country Population kan t.ex. vara rimligt, medan Median Sales Price inte är det.
* **Avancerade textfilter (”contains” och liknande):** När du filtrerar en textkolumn använder den avancerade filtreringen filter som ”contains”, ”begins with” osv. Dessa filter kan tveklöst resultera i sämre prestanda för vissa datakällor. I synnerhet standardfiltret ”contains” bör inte användas om vad som verkligen krävs är en exakt matchning (”is” eller ”is not”). Även om resultaten kan vara samma, beroende på faktiska data, så kan prestanda avvika drastiskt beroende på användningen av index.
* **Flervalsutsnitt:** Utsnitt tillåter som standard bara enskilda val. Att tillåta flervalsfilter kan orsaka vissa prestandaproblem, eftersom varje nytt val som du gör när du väljer en uppsättning objekt i utsnittet (t.ex. de tio produkter du finner intressanta) resultera i att frågor skickas till ursprungskällan. Samtidigt som du kan välja nästa objekt innan frågan slutförs, så leder detta till en extra belastning på den underliggande källan.

* **Överväg att inaktivera summor på visualiseringar:** Som standard visar tabeller och matriser summor och delsummor. I många fall skickas separata frågor till underliggande källa för att hämta värden för dessa summor. Detta gäller när du använder *DistinctCount*-aggregering, eller i alla fall när du använder DirectQuery över SAP BW eller SAP HANA. Sådana summor ska inaktiveras (med hjälp av fönstret **Format**) om de inte krävs. 

### <a name="diagnosing-performance-issues"></a>Diagnostisera prestandaproblem
I det här avsnittet beskrivs hur du diagnostiserar prestandaproblem eller hämtar mer detaljerad information så att du kan optimera rapporterna.

Vi rekommenderar starkt att du låter all diagnostisering av prestandaproblem utgå från **Power BI Desktop** istället för **Power BI-tjänsten**. Prestandaproblem baseras ofta på den underliggande källans prestandanivå, och denna kan enkelt identifieras och diagnostiseras i den mycket mer isolerade miljön i **Power BI Desktop**, varvid vissa komponenter (t.ex. Power BI Gateway) elimineras initialt. Endast om några prestandaproblem inte hittas i Power BI Desktop bör undersökningen fokuseras på det specifika i rapporten i Power BI-tjänsten.

På motsvarande sätt rekommenderar vi att du först försöker isolera problemen till ett enskilt visuellt objekt, istället för till flera visuella objekt på samma sida.

Så låt oss säga att du har vidtagit dessa åtgärder (som beskrivs i ovanstående stycken i det här avsnittet) – då har vi nu ett enda visuellt objekt på en sida i **Power BI Desktop** som är fortfarande långsamt. Om du vill fastställa vilka frågor som skickas till den underliggande källan av Power BI Desktop kan du visa spår/diagnostikinformation som kan ha orsakats av källan. Sådana spår kan också innehålla användbar information om hur frågan har körts, och hur den kan förbättras.

Även i frånvaron av sådana spår från källan kan du visa de frågor som skickats av Power BI, tillsammans med deras körningstider, så som beskrivs nedan.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Fastställa vilka frågor som skickats av Power BI Desktop
**Power BI Desktop** loggar som standard händelser under en viss session till en spårningsfil som kallas FlightRecorderCurrent.trc.

För vissa **DirectQuery**-källor inkluderar den här loggfilen alla frågor som skickats till den underliggande datakällan (de återstående DirectQuery-källorna inkluderas längre fram). De källor som skickar frågor till loggen är följande:

* SQL Server
* Azure SQL Database
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

Du hittar spårningsfilen i **AppData**-mappen för den aktuella användaren:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Så här hittar du mappen på ett enkelt sätt: Välj **Arkiv > Alternativ och inställningar > Alternativ** i **Power BI Desktop** och välj sedan **Diagnostik**. Följande dialogruta visas:

![](media/desktop-directquery-about/directquery-about_06.png)

När du väljer länken *Öppna mapp för spårningar* under **Diagnostikalternativ** öppnas följande mapp:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

Om du går till mappens överordnade mapp visas den mapp som innehåller *AnalysisServicesWorkspaces*, som innehåller en arbetsyteundermapp för varje öppen instans av **Power BI Desktop**. Dessa undermappar namnges med ett heltalssuffix, t.ex. *AnalysisServicesWorkspace2058279583*.

I den mappen finns en *\\Data*-undermapp som innehåller den aktuella Power BI-sessionens spårningsfil FlightRecorderCurrent.trc. Motsvarande arbetsytemapp tas bort när den associerade Power BI Desktop-sessionen avslutas.

Du kan läsa spårningsfilerna med hjälp av verktyget **SQL Server Profiler**, vilket du kan hämta kostnadsfritt som en del av **SQL Server Management Studio**. Du kan hämta det från [den här platsen](https://msdn.microsoft.com/library/mt238290.aspx).

När du har hämtat och installerat **SQL Server Management Studio**, så kör **SQL Server Profiler**.

![](media/desktop-directquery-about/directquery-about_07.png)

Öppna spårningsfilen så här:

1. Välj **Arkiv > Öppna > Spårningsfil** i **SQL Server Profiler**
2. Ange sökvägen till den för tillfället öppna Power BI-sessionens spårningsfil, t.ex.:
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Öppna FilghtRecorderCurrent.trc

Alla händelser från den aktuella sessionen visas. Ett kommenterat exempel visas nedan, där olika grupper av händelser har markerats. Varje grupp har följande:

* En *Frågan börjar*- och en *Frågan slutar*-händelse, som representerar en DAX-frågas början och slut, och som genererats av gränssnittet (exempelvis från ett visuellt objekt eller efter det att lista med värden i filtergränssnittet har fyllts i)
* Ett eller flera par med *DirectQuery börjar*- och *DirectQuery slutar*-händelser, som representerar en fråga som skickats till den underliggande datakällan, som en del av utvärderingen av DAX-frågan.

Observera att flera DAX-frågor kan köras parallellt, så händelser från olika grupper kan interfolieras. ActivityID-värdet kan användas för att avgöra vilka händelser som hör till samma grupp.

![](media/desktop-directquery-about/directquery-about_08.png)

Andra kolumner av intresse är följande:

* **TextData:** Textinformation om händelsen. För ”Frågan börjar/slutar”-händelser är detta DAX-frågan. För ”DirectQuery börjar/slutar”-händelser är detta den SQL-fråga som skickats till den underliggande källan. TextData för den valda händelsen visas också i regionen längst ned.
* **EndTime:** När händelsen slutförts.
* **Duration:** Den varaktighet i millisekunder som krävs för att köra DAX- eller SQL-frågan.
* **Error:** Anger om ett fel har uppstått (i vilket fall händelsen även visas i rött).

Observera att några av de mindre intressanta kolumnerna har gjorts smalare i bilden ovan, så att de intressanta kolumnerna ska synas tydligare.

Den rekommenderade metoden för att samla in en spårning för att diagnosticera potentiella prestandaproblem är följande:

* Öppna endast en **Power BI Desktop**-session (så att du undviker eventuell förvirring genom att ha flera arbetsytemappar)
* Genomför en uppsättning intressanta åtgärder i **Power BI Desktop**. Inkludera några ytterligare åtgärder utöver dessa, så att du kan vara säker på att de intressanta händelserna hamnar i spårningsfilen.
* Öppna **SQL Server Profiler** och undersök spåret, så som beskrivits ovan. Kom ihåg att spårningsfilen tas bort när du stänger **Power BI Desktop**. Ytterligare åtgärder i Power BI Desktop visas heller inte omedelbart – spårningsfilen ska vara stängd och öppnas på nytt om du vill se de nya händelserna.
* Om du håller de enskilda sessionerna rimligt små (tio sekunders åtgärder, snarare än hundratals) gör det lättare att tolka spårningsfilen (och eftersom det finns en gräns för spårningsfilens storlek, så finns det en risk att mycket långa sessioner ökar risken för att tidiga händelser tas bort).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Förstå vilken typ av fråga som Power BI Desktop skickar
Formatet på de frågor som skapas och skickas av **Power BI Desktop** använder underfrågor för var och en av de refererade tabellerna, där underfrågan definieras av den fråga som definierats i **Frågeredigeraren**. Låt oss t.ex. anta att följande TPC DS-tabeller finns i SQL Server:

![](media/desktop-directquery-about/directquery-about_09.png)

Överväg följande fråga:

![](media/desktop-directquery-about/directquery-about_10.png)

Frågan resulterar i följande visuella objekt:

![](media/desktop-directquery-about/directquery-about_11.png)

När du uppdaterar det visuella objektet resulterar det i den SQL-fråga som visas i nästa stycke. Som du ser finns det tre underfrågor för Web Sales, Item och Date_dim, som var och en returnerar alla kolumner i respektive tabell även om det visuella objektet bara refererar till fyra kolumner. Dessa frågor i underfrågorna (de är skuggade) är exakt resultatet av de frågor som definierats i **Frågeredigeraren**. Denna användning av underfrågor har inte påvisats påverka prestandan hos de datakällor som hittills stöds för DirectQuery. Datakällor som SQL Server optimerar helt enkelt bort referenser till de övriga kolumnerna.

En orsak till att Power BI använder ett sådant mönster är att den SQL-fråga som används kan anges direkt av analytikern, så den används ”i befintligt skick”, utan något försök att skriva om den.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Nästa steg
I den här artikeln beskrivs olika aspekter av **DirectQuery** som är gemensamma för alla datakällor. Vissa detaljer är specifika för enskilda datakällor. Följande avsnitt behandlar olika specifika källor:

* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)

Mer information om **DirectQuery** finns i följande resurser:

* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)

