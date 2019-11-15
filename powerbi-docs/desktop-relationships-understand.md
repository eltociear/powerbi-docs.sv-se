---
title: Modellrelationer i Power BI Desktop
description: Presentation av teorier kring modellrelationer i Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: c8ad6153ba1fcfb22987c5399bb82a9a8f4e664c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879797"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Modellrelationer i Power BI Desktop

Den här artikeln är avsedd för importdatamodellerare som arbetar med Power BI Desktop. Modelldesign är viktigt när det kommer till att leverera intuitiva, exakta och optimala modeller.

Du hittar en djupare diskussion om optimal modelldesign, inklusive tabellroller och relationer, i artikeln om [hur man kan förstå star-scheman och dess betydelse för Power BI](guidance/star-schema.md).

## <a name="relationship-purpose"></a>Syftet med relationer

Lite förenklat kan man säga att Power BI-relationer sprider filter som tillämpas på kolumnerna i modelltabeller till andra modelltabeller. Filter kommer att spridas vidare så långt relationens sökväg sträcker sig, vilket betyder att de kan spridas till flera tabeller.

Relationssökvägar är deterministiska, vilket innebär att filter alltid sprids på samma sätt och utan slumpmässig variation. Relationer kan emellertid inaktiveras eller så kan filterkontexten ändras av modellberäkningar som använder särskilda DAX-funktioner. Mer information finns i avsnittet om [relevanta DAX-funktioner](#relevant-dax-functions) längre fram i den här artikeln.

> [!IMPORTANT]
> Det är viktigt att förstå att modellrelationer inte automatiskt leder till dataintegritet. Mer information finns i avsnittet om [utvärdering av relationer](#relationship-evaluation) längre fram i den här artikeln. I det här avsnittet beskrivs hur modellrelationer fungerar när det uppstår integritetsproblem för dina data.

Nu ska vi se hur relationer sprider filter vidare med ett animerat exempel.

![Animerat exempel på spridning av ett relationsfilter](media/desktop-relationships-understand/animation-filter-propagation.gif)

I det här exemplet består modellen av fyra tabeller: **Kategori**, **Produkt**, **År** och **Försäljning**. Tabellen **Kategori** är relaterad till tabellen **Produkt** och tabellen **Produkt** är relaterad till tabellen **Försäljning**. Tabellen **År** är också relaterad till tabellen **Försäljning**. Alla relationer är av typen en-till-många (detta förklaras närmare i slutet av artikeln).

En fråga – kanske genererad av ett visuellt objekt för ett Power BI-kort – frågar efter den totala försäljningskvantiteten för säljordrar för en enda kategori, **Cat-A**, och för ett enda år, **CY2018**. Det är därför du kan se filter som tillämpas på tabellerna **Kategori** och **År**. Filtret för tabellen **Kategori** sprids till tabellen **Produkt** för att isolera två produkter som har tilldelats kategorin **Cat-A**. Sedan kan tabellfiltren för **Produkt** spridas till tabellen **Försäljning** för att isolera bara två försäljningsrader för dessa produkter. Dessa två försäljningsrader representerar försäljningen av produkter som tilldelats kategorin **Cat-A**. Deras sammanlagda kvantitet är 14 enheter. Samtidigt sprids tabellfiltret för **År** vidare, för att ytterligare filtrera tabellen **Försäljning**, vilket ger bara en försäljningsrad för produkter som är tilldelade kategorin **Cat-A** och som beställdes under året **CY2018**. Frågan returnerar värdet 11 enheter. Observera att när flera filter tillämpas på en tabell (t.ex. tabellen **Försäljning** i det här exemplet) är det alltid en AND-operation, vilket kräver att alla villkor måste vara uppfyllda.

### <a name="disconnected-tables"></a>Frånkopplade tabeller

Det är ovanligt att en modelltabell inte alls är relaterad till en annan modelltabell. En sådan tabell, i en giltig modelldesign, kallas en _frånkopplad tabell_. En frånkopplad tabell är inte avsedd att sprida filter till andra modelltabeller. Den används istället för att godkänna "användarindata" (kanske med ett visuellt utsnitt), så att modellberäkningar kan använda indatavärdet på ett meningsfullt sätt. Anta till exempel att en frånkopplad tabell har lästs in med ett intervall av värden för valutaväxelkurser. Om ett filter används för att filtrera efter ett enda värde, kan värdet användas genom ett måttuttryck för att konvertera försäljningsvärden.

Power BI Desktop konsekvensparameter är en funktion som skapar en frånkopplad tabell. Mer information finns i artikeln om att [skapa och använda en konsekvensparameter för att visualisera variabler i Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Relationsegenskaper

En modellrelation relaterar en kolumn i en tabell till en kolumn i en annan tabell. (Det finns ett specialfall, där detta krav inte är uppfyllt, och det gäller endast för relationer i flera kolumner i DirectQuery-modeller. Mer information finns i artikeln om DAX-funktionen [COMBINEVALUES](/dax/combinevalues-function-dax).)

> [!NOTE]
> Det går inte att relatera en kolumn till en annan kolumn _i samma tabell_. Detta förväxlas ibland med möjligheten att definiera en begränsning för en sekundärnyckel för en relationsdatabas, med självrefererande tabeller. Detta relationsdatabaskoncept kan användas för att lagra relationer mellan överordnade och underordnade objekt (t.ex. är varje anställds post relaterad till en anställd med egenskapen "rapporterar till"). Det går inte att lösa generering av en modell-hierarki baserat på den här typen av relation genom att skapa modellrelationer. För att åstadkomma detta kan du läsa artikeln om [funktioner för över- och underordnade objekt](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Kardinalitet

Varje modellrelation måste definieras med en kardinalitetstyp. Det finns fyra alternativ för kardinalitetstyp, som representerar dataegenskaperna för relaterade kolumner "från" och "till". ”En”-sidan innebär att kolumnen innehåller unika värden. ”Två”-sidan innebär att kolumnen kan innehålla dubblettvärden.

> [!NOTE]
> Om en datauppdateringsåtgärd försöker läsa in dubblettvärden till en ”en”-sidekolumn, kommer hela datauppdateringen att misslyckas.

De fyra alternativen, tillsammans med deras stenografiska format, beskrivs i följande punktlista:

- En-till-många (1:\*)
- Många-till-en (\*:1)
- En-till-en (1:1)
- Många-till-många (\*:\*)

När du skapar en relation i Power BI Desktop, kommer designern automatiskt detektera och ange kardinalitetstypen. Designern kan göra det eftersom den skickar frågor till modellen för att veta vilka kolumner som innehåller unika värden. För importmodeller använder den intern lagringsstatistik, för DirectQuery-modeller skickar den profileringsfrågor till datakällan. Men ibland går det fel. Det beror på att tabellerna inte har fyllts på med data än, eller på att kolumnerna du förväntar dig ska innehålla dubblettvärden bara innehåller unika värden för tillfället. I vilket fall kan du uppdatera kardinalitetstypen, under förutsättning att ”en”-sidekolumner innehåller unika värden (eller att tabellen väntar på att laddas med datarader).

Kardinaliteten **En-till-många-** och **Många-till-en** är i stort sett samma, och de är även de vanligaste kardinalitetstyperna.

När du konfigurerar en en-till-många-relationer eller många-till-en-relationer, väljer du den som matchar den ordning du har relaterat kolumnerna i. Överväg hur du skulle konfigurera relationen från tabellen **Produkt** till tabellen **Försäljning** med hjälp av kolumnen **ProduktID** som finns i varje tabell. Kardinalitetstypen skulle vara _En-till-många_, eftersom kolumnen **ProduktID** i tabellen **Produkt** innehåller unika värden. Om du har relaterat tabellerna i omvänd riktning, **Försäljning** till **Produkt**, skulle kardinaliteten bli _Många-till-en_.

Ett förhållande **En-till-en** innebär att båda kolumnerna innehåller unika värden. Den här typen av kardinalitet är inte vanlig, och det är troligen inte en optimal modelldesign, eftersom den leder till lagring av redundanta data.<!-- For guidance on using this cardinality type, see the [One-to-one relationship guidance](guidance/relationships-one-to-one) article.-->

En **många-till-många**-relation innebär att båda kolumnerna kan innehålla dubblettvärden. Den här typen av kardinalitet används sällan. Den används vanligen när du utformar komplexa modellkrav.<!-- For guidance on using this cardinality type, see the [Many-to-many relationship guidance](guidance/relationships-many-to-many) article.-->

> [!NOTE]
> Det finns för närvarande inte stöd för kardinalitetstypen många-till-många för modeller som har utvecklats för Power BI-rapportserver.

> [!TIP]
> I Power BI Desktop modellvy kan du tolka en relations kardinalitetstyp genom att titta på indikatorerna (1 eller \*) på endera sidan av relationslinjen. För att avgöra vilka kolumner som är relaterade måste du välja – eller lägga markören över – relationslinjen för att markera kolumnerna.

### <a name="cross-filter-direction"></a>Korsfilterriktning

Varje modellrelation måste definieras med en korsfilterriktning. Ditt val avgör i vilken riktning som filtren kommer att spridas. Vilka korsfilteralternativ som är möjliga beror på kardinalitetstypen.

| Kardinalitetstyp | Korsfilteralternativ |
| --- | --- |
| En-till-många (eller många-till-en) | Enkel<br>Båda |
| En-till-en | Båda |
| Många-till-många | Enkel (tabell1 till tabell2)<br>Enkel (tabell2 till tabell1)<br>Båda |

_Enkel_ korsfilterriktning betyder "enkel riktning" och _båda_ betyder "båda riktningar". En relation som filtrerar i båda riktningarna kallas ofta _dubbelriktad_.

För en-till-många-relationer går korsfilterriktningen alltid från ”en”-sidan och som tillval från ”många”-sidan (dubbelriktad). För en-till-en-relationer går korsfilterriktningen alltid från båda tabellerna. Slutligen, för många-till-många-relationer, kan korsfilterriktningen gå från en av tabellerna eller från båda tabellerna. Observera att när kardinalitetstypen innehåller en "en"-sida, kommer filtret alltid att spridas från den sidan.

När korsfilterriktningen är satt till **Båda**, är ytterligare en egenskap tillgänglig för att tillämpa dubbelriktad filtrering när regler för säkerhet på radnivå (RLS) används. Mer information om RLS finns i artikeln om [säkerhet på radnivå (RLS) med Power BI Desktop](desktop-rls.md).

Ändringar av relationskorsfilterriktningen, inklusive inaktivering av filterspridning, kan också göras med en modellberäkning. Detta görs med DAX-funktionen [CROSSFILTER](/dax/crossfilter-function).

Dubbelriktade relationer kan påverka prestandan negativt. Om du försöker konfigurera en dubbelriktad relation kan det leda till tvetydiga filterspridningsvägar. I det här fallet kan det hända att Power BI Desktop inte kan genomföra relationsändringen och du får då ett felmeddelande. Ibland kan Power BI Desktop emellertid tillåta att du definierar tvetydiga relationsvägar mellan tabeller. Prioritetsregler som påverkar detekteringen av tvetydigheter och sökvägsupplösning beskrivs längre fram i den här artikeln om [prioritetsregler](#precedence-rules).

Vi rekommenderar att du bara använder dubbelriktad filtrering när det verkligen behövs.<!-- For guidance on bi-directional filtering, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

> [!TIP]
> I Power BI Desktop-modellvyn kan du tolka relationens riktning för ett korsfilter genom att titta på pilspetsen/pilspetsarna längs relationslinjen. En pilspets representerar ett filter med en riktning i pilspetsens riktning. En dubbel pilspets representerar en dubbelriktad relation.

### <a name="make-this-relationship-active"></a>Gör den här relationen aktiv

Det kan bara finnas en aktiv väg för filtreringsspridning mellan två modelltabeller. Det går emellertid att lägga till ytterligare relationsvägar, även om dessa relationer måste konfigureras som _inaktiva_. Inaktiva relationer kan bara göras aktiva under utvärderingen av en modellberäkning. Detta görs med DAX-funktionen [USERELATIONSHIP](/dax/userelationship-function-dax).

<!--For guidance on defining inactive relationships, see the [Active vs inactive relationship guidance](guidance/relationships-active-inactive) article.-->

> [!TIP]
> I Power BI Desktop-modellvyn kan du läsa av en relations aktiva resp. inaktiva status. En aktiv relation visas som en heldragen linje och en inaktiv relation visas som en streckad linje.

### <a name="assume-referential-integrity"></a>Anta referensintegritet

Egenskapen _Anta referensintegritet_ är bara tillgängligt för en-till-många-relationer och en-till-en-relationer mellan två DirectQuery-tabeller i lagringsläge som baseras på samma datakälla. När den är aktiverad kommer internfrågor som skickas till datakällan att koppla samman de två tabellerna med en inre koppling istället för en yttre koppling. Den här egenskapen leder vanligtvis till en allmän förbättring av frågeprestanda om den aktiveras, även om det beror på de specifika egenskaperna för datakällan.

Egenskapen bör alltid vara aktiverad när det finns en begränsning för den sekundära nyckeln för databasen mellan de två tabellerna. Om det inte finns en begränsning för sekundärnyckeln, kan du fortfarande aktivera egenskapen, om du är säker på att dataintegritet föreligger.

> [!IMPORTANT]
> Om dataintegriteten skulle bli komprometterad, tar den inre kopplingen bort omatchade rader mellan tabellerna. Ta till exempel en modelltabell **Försäljning** med ett kolumnvärde **ProduktID**, som inte fanns i den relaterade tabellen **Produkt**. Filterspridningen från tabellen **Produkt** till tabellen **Försäljning** tar bort försäljningsrader för okända produkter. Detta leder till för låga försäljningsresultat.
>
> Mer information finns i artikeln om att [anta referensintegritetsinställningar i Power BI Desktop](desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Relevanta DAX-funktioner

Det finns flera DAX-funktioner som är relevanta för modellrelationer. Varje funktion beskrivs kortfattat i följande punktlista:

- [RELATED](/dax/related-function-dax): Hämtar värdet från "en"-sidan.
- [RELATEDTABLE](/dax/relatedtable-function-dax): Hämta en tabell med rader från "många"-sidan.
- [USERELATIONSHIP](/dax/userelationship-function-dax): Tvingar fram användningen av en specifik inaktiv modellrelation.
- [CROSSFILTER](/dax/crossfilter-function): Ändrar relationens korsfilterriktning (till en eller båda), eller inaktiverar filterspridningen (ingen).
- [COMBINEVALUES](/dax/combinevalues-function-dax): Förenar två eller fler textsträngar till en textsträng. Syftet med den här funktionen är att stödja relationer med flera kolumner i DirectQuery-modeller.
- [TREATAS](/dax/treatas-function): Applicerar resultatet av ett tabelluttryck som filter till kolumner från en orelaterad tabell.
- [Över-och underordnade funktioner](/dax/parent-and-child-functions-dax): En serie relaterade funktioner som kan användas för att generera beräknade kolumner, för att naturalisera en överordnad-underordnad hierarki. Dessa kolumner kan sedan användas för att skapa en hierarki med fast nivå.

## <a name="relationship-evaluation"></a>Relationsbedömning

Modellrelationer klassificeras, ur ett utvärderingsperspektiv, antingen som _starka_ eller _svaga_. Det är inte en konfigurerbar relationsegenskap. Den är faktiskt härledd från kardinalitetstypen och datakällan för de två relaterade tabellerna. Det är viktigt att förstå utvärderingstypen, eftersom det kan uppstå prestandaeffekter eller konsekvenser om dataintegriteten komprometteras. Dessa konsekvenser och integritetskonsekvenser beskrivs i det här avsnittet.

Men först behöver vi lite modelleringsteori för att helt kunna förstå relationsutvärderingarna.

En import- eller DirectQuery-modell lagrar alla sina data från antingen Vertipaq-cachen eller källdatabasen. I båda fall kan Power BI avgöra om det finns en "en"-sida av en relation.

En sammansatt modell kan emellertid bestå av tabeller med olika lagringslägen (import, DirectQuery eller dubbel) eller flera DirectQuery-källor. Alla källor, inklusive Vertipaq-cachen för importdata, anses vara en _dataö_. Modellrelationer kan sedan klassificeras som _intra-öar_ eller _kors-öar_. En relation av typen intra-ö relaterar två tabeller inom en dataö, och en relation av typen kors-ö relaterar tabeller från olika dataöar. Observera att relationer i Import- eller DirectQuery-modeller är alltid av typen intra-ö.

Låt oss titta på en sammansatt modell.

![Exempel på en sammansatt modell bestående av två öar](media/desktop-relationships-understand/data-island-example.png)

I det här exemplet består den sammansatta modellen av två öar: en Vertipaq-dataö och en DirectQuery-källdataö. Vertipaq-dataön innehåller tre tabeller och DirectQuery-källdataön innehåller två tabeller. En relation av typen kors-ö finns för att koppla en tabell i Vertipaq-dataön till en tabell i DirectQuery-källdataön.

### <a name="strong-relationships"></a>Starka relationer

En modellrelation är _stark_ när frågemotorn kan bestämma "en"-sidan av relationen. Den har fått bekräftelse på att kolumnen på "en"-sidan innehåller unika värden. Alla en-till-många-relationer av typen intra-öar är starka relationer.

I följande exempel finns det två starka relationer, båda markerade som **S**. Relationer omfattar en-till-många-relationerna som finns i Vertipaq-ön samt en-till-många-relationerna i DirectQuery-källan.

![Exempel på en sammansatt modell bestående av två öar med starka relationer markerade](media/desktop-relationships-understand/data-island-example-strong.png)

För importmodeller där alla data lagras i Vertipaq-cachen, skapas en datastruktur för varje stark relation vid datauppdateringen. Datastrukturerna består av indexerade mappningar för alla kolumn-till-kolumn-värden och syftet är att snabba upp kopplingen av tabeller när frågan körs.

När frågan körs tillåter starka relationer _tabellexpansioner_. Tabellexpansionen resulterar i att en virtuell tabell skapas, genom att de interna kolumnerna i bastabellen inkluderas och sedan utökas till relaterade tabeller. För importtabeller görs detta i frågemotorn. För DirectQuery-tabeller görs det i den interna frågan som skickas till källdatabasen (förutsatt att egenskapen "Anta referensintegritet" inte är aktiverad). Frågemotorn jobbar sedan med den expanderade tabellen och använder filter och gruppering utifrån värdena i de expanderade tabellkolumnerna.

> [!NOTE]
> Inaktiva relationer expanderas också, även om relationen inte används av en beräkning. Dubbelriktade relationer påverkar inte tabellexpansionen.

För många-till-många-relationer sker tabellexpansionen från "många"- till ”en”-sidorna med hjälp av vänster yttre kopplings-semantik. Om det inte finns ett matchande värde från "många"- till "en"-sidan, läggs en tom virtuell rad till i tabellen på "en"-sidan.

Tabellexpansion utförs även för en-till-en-relationer av typen intra-ö, men med fullständig yttre kopplings-semantik. Det säkerställer att tomma virtuella rader läggs till på endera sidan, om det behövs.

De tomma virtuella raderna är i praktiken _okända medlemmar_. Okända medlemmar representerar överträdelser av referensintegriteten, där värdet på "många"-sidan inte har något motsvarande värde på "en"-sidan. I det optimala fallet ska dessa tomma rader inte existera, och de kan tas bort genom rengöring eller reparation av källdata.

Låt oss ta en titt på hur tabellexpansionen fungerar med ett animerat exempel.

![Animerat exempel på tabellexpansion](media/desktop-relationships-understand/animation-expanded-table.gif)

I det här exemplet består modellen av tre tabeller: **Kategori**, **Produkt** och **Försäljning**. Tabellen **Kategori** är relaterad till tabellen **Produkt** med en en-till-många-relation, och tabellen **Produkt** är relaterad till tabellen **Försäljning** med en en-till-många-relation. Tabellen **Kategori** innehåller två rader, tabellen **Produkt** innehåller tre rader och tabellen **Försäljning** innehåller fem rader. Det finns matchande värden på båda sidor av alla relationer, vilket innebär att det inte finns några överträdelser av referensintegriteten. En expanderad tabell visas när frågan körs. Tabellen består av kolumnerna från alla tre tabeller. Det är i praktiken ett avnormaliserat perspektiv av de data som finns i de tre tabellerna. En ny rad läggs till i tabellen **Försäljning**, med ett produktions-ID-värde (9) som inte har något matchande värde i tabellen **Produkt**. Det är en överträdelse av referensintegriteten. I den expanderade tabellen har den nya raden (tomma) värden för tabellkolumnerna **Kategori** och **Produkt**.

### <a name="weak-relationships"></a>Svaga relationer

En modellrelation är _svag_ när det inte finns någon garanterad "en"-sida. Det kan bero på två saker:

- Relationen använder kardinalitetstypen många-till-många (även om en eller båda kolumner innehåller unika värden)
- Relationen är av typen kors-ö (som bara kan användas för sammansatta modeller)

I följande exempel finns det två svaga relationer, båda markerade som **W**. De två relationerna omfattar de många-till-många-relationer som finns i Vertipaq-ön samt en-till-många-relationerna i kors-ö-relationen.

![Exempel på en sammansatt modell bestående av två öar med svaga relationer markerade](media/desktop-relationships-understand/data-island-example-weak.png)

För importmodeller skapas aldrig datastrukturer för svaga relationer. Det innebär att tabellkopplingarna måste lösas vid när frågan körs.

För svaga relationer sker ingen tabellexpansion. Tabellkopplingar uppnås med hjälp av inre kopplings-semantik, och därför läggs tomma virtuella rader inte till för att kompensera för överträdelser av referensintegriteten.

Det finns fler restriktioner för svaga relationer:

- DAX-funktionen RELATED kan inte användas för att hämta kolumnvärden på ”en”-sidan
- Det finns begränsningar i topologin för tvingande RLS

> [!NOTE]
> I Power BI Desktops modellvy går det inte alltid att avgöra om en modellrelation är stark eller svag. En många-till-många-relation kommer alltid att vara svag, precis som en-till-många-relationer är när de är en relation av typen kors-ö. För att avgöra om det är en relation av typen kors-ö måste du kontrollera tabellagringslägena och datakällorna.

### <a name="precedence-rules"></a>Regler för prioritet

Dubbelriktade relationer kan leda till flera – och därför tvetydiga – filterspridningsvägar mellan modelltabellerna. I följande lista visas de regler för prioritet som Power BI använder för att identifiera tvetydigheter och vägupplösning:

1. Många-till-en- och en-till-en-relationer, inklusive svaga relationer
2. Många-till-många-relationer
3. Dubbelriktade relationer, i omvänd riktning (dvs. från "många"-sidan)

### <a name="performance-preference"></a>Inställningar för prestanda

I följande lista visas prestanda för filterspridning, från snabbast till långsammast prestanda:

1. En-till-många-relationer av typen intra-ö
2. Många-till-många-kardinalitetsrelationer
3. Många-till-många-modellrelationer som uppnås med en mellanliggande tabell och som omfattar minst en dubbelriktad relation
4. Relationer av typen kors-ö

<!--For further information and guidance on many-to-many relationships, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

## <a name="next-steps"></a>Nästa steg

- [Förstå star-schemat och dess betydelse för Power BI](guidance/star-schema.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
