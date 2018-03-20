---
title: "DirectQuery för SAP HANA i Power BI"
description: "Att tänka på när du använder DirectQuery med SAP HANA"
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
ms.date: 03/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7b1b56ee467dfdf6dc8c63557a9a9f4ab86e965e
ms.sourcegitcommit: 85d18d9f11a4ce4d4ed65e4544d13da6c2d9b1d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="directquery-and-sap-hana"></a>DirectQuery och SAP HANA
Du kan ansluta till **SAP HANA**-datakällor direkt med **DirectQuery**. Det finns två alternativ när du ansluter till SAP HANA:

* **Hantera SAP HANA som en flerdimensionell källa (standard):** I det här fallet ska beteendet vara detsamma som när Power BI ansluter till andra flerdimensionella källor som SAP Business Warehouse eller Analysis Services. När du ansluter till SAP HANA med den här inställningen väljs en enda analys- eller beräkningsvy och alla åtgärder, hierarkier och attribut för den vyn blir tillgängliga i fältlistan. Då visuell information skapas, kommer sammanställda data alltid att hämtas från SAP HANA. Det är den rekommenderade metoden och är standard för nya DirectQuery-rapporter över SAP HANA.

* **Hantera SAP HANA som en relationskälla:** I det här fallet behandlar Power BI SAP HANA som relationskälla. Detta ger dig större flexibilitet, men var försiktig så att åtgärder aggregeras som förväntat och så att prestandaproblem undviks.

Den metod som används för att ansluta bestäms av ett alternativ för globala verktyg, vilket anges genom att välja **Arkiv > Alternativ och inställningar** och sedan **Alternativ > DirectQuery**, och sedan alternativet **Hantera SAP HANA som en relationskälla**, enligt följande bild. 

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

Alternativet att behandla SAP HANA som en relationskälla styr den metod som används för alla *nya* rapporter med DirectQuery över SAP HANA. Det har ingen effekt på några befintliga SAP HANA-anslutningar i den aktuella rapporten eller på anslutningar i andra rapporter som är öppna. Om alternativet för närvarande är avmarkerat gör tillägget av en ny anslutning till SAP HANA med hjälp av **Hämta data** att anslutningen behandlar SAP HANA som en flerdimensionell källa. Men om en annan rapport öppnas som också ansluter till SAP HANA kommer rapporten fortsätta att fungera enligt det alternativ som angavs *när den skapades*. Det innebär att alla rapporter som ansluter till SAP HANA som skapades före februari 2018 fortsätter att behandla SAP HANA som en relationskälla. 

De två metoderna består av mycket olika beteenden och det går inte att växla en befintlig rapport från en metod till den andra. 

Nu ska vi titta på mer information om dessa två metoder var för sig.

## <a name="treat-sap-hana-as-a-multi-dimensional-source-default"></a>Hantera SAP HANA som en flerdimensionell källa (standard)

För alla nya anslutningar till SAP HANA används den här anslutningsmetoden som standard, och SAP HANA behandlas som en flerdimensionell källa. För att behandla en anslutning till SAP HANA som relationskälla måste du välja **Arkiv > Alternativ och inställningar** och sedan kryssrutan under **Direct Query > Behandla SAP HANA som relationskälla**. När den här funktionen är i **Förhandsgranskning**, *kan inte* rapporter som skapas med den flerdimensionella metoden publiceras till Power BI-tjänsten vilket leder till fel när rapporten öppnas i Power BI-tjänsten.  

När du ansluter till SAP HANA som en flerdimensionell källa gäller följande:

* I **Hämta datanavigatör** kan en enda SAP HANA-vy väljas. Det går inte att välja enskilda åtgärder eller attribut. Det finns ingen fråga definierad vid tidpunkten för anslutning, vilket skiljer sig från att importera data eller när du använder DirectQuery när du behandlar SAP HANA som en relationskälla. Det innebär också att det inte går att använda en SAP HANA SQL-fråga direkt när du väljer den här anslutningsmetoden.

* Alla åtgärder, hierarkier och attribut för den valda vyn kommer att visas i listan. 

* Då ett mått används i en visualisering efterfrågas SAP HANA om att hämta måttvärdet på den aggregeringsnivå som krävs för visualiseringen. Så när du hanterar icke-additiva mått (räknare, kvoter och så vidare) utförs alla aggregeringar av SAP HANA, och ingen ytterligare aggregering utförs av Power BI. 

* Vissa begränsningar måste införas för att säkerställa att rätt aggregeringsvärden alltid kan hämtas från SAP HANA. T.ex. går det inte att lägga till beräknade kolumner eller kombinera data från flera SAP HANA-vyer i samma rapport. 

Att behandla SAP HANA som en flerdimensionell källa ger inte den större flexibilitet som tillhandahålls av *relations*metoden, men det är enklare och säkerställer rätt aggregeringsvärden när du hanterar mer komplexa SAP HANA-åtgärder och ger vanligtvis bättre prestanda. 

Listan **Fält** kommer att innehålla alla åtgärder, attribut och hierarkier från SAP HANA-vyn. Observera följande beteenden som gäller när du använder den här anslutningsmetoden:

* Alla attribut som ingår i minst en hierarki döljs som standard. Dock kan du se dem om det behövs genom att välja **Visa dolda** på snabbmenyn i fältlistan. På samma snabbmenyn kan de göras synliga, om det behövs.

* I SAP HANA kan du definiera ett attribut för att använda ett annat attribut som dess etikett. Till exempel kan **Produkt** (med värde 1,2,3 och så vidare) använda **ProductName** (med värden cykel, skjorta, handskar och så vidare) som dess etikett. I det här fallet kommer endast ett fält, **Produkt** att visas i listan vars värden kommer att vara etiketterna cykel, skjorta, handskar och så vidare, men som kommer att sorteras enligt, och med unikhet bestämmas av, nyckelvärdena 1,2,3. En dold kolumn **Product.Key** skapas också, för att tillåta åtkomst till de underliggande nyckelvärdena om det behövs. 

Alla variabler som definieras i den underliggande SAP HANA-vyn visas vid tidpunkten för anslutning och nödvändiga värden kan anges. Dessa värden kan senare ändras genom att välja **Redigera frågor** från menyfliken och sedan **Redigera variabler** från den nedrullningsbara menyn som visas. 

De modelleringar som tillåts är mer restriktiva än i vanliga fall när du använder DirectQuery, eftersom det är nödvändigt att säkerställa att rätt aggregeringsdata alltid kan hämtas från SAP HANA. Det är dock fortfarande möjligt att göra många tillägg och ändringar, inklusive definiera åtgärder, byta namn på och dölja fält samt definiera visningsformat. Alla ändringar kommer att bevaras vid uppdatering och alla icke motstridiga ändringar av SAP HANA-vyn kommer att tillämpas. 

### <a name="additional-modelling-restrictions"></a>Ytterligare modelleringsbegränsningar

Den primära ytterligare modelleringsbegränsningen vid anslutning till SAP HANA med DirectQuery (behandla som flerdimensionell källa) är följande: 

* **Inget stöd för beräknade kolumner:** möjligheten att skapa beräknade kolumner är inaktiverad. Det innebär också att gruppering och klustring, som skapar beräknade kolumner, inte är tillgängligt.
* **Ytterligare begränsningar för mått:** Det finns ytterligare begränsningar av de DAX-uttryck som kan användas i mått för att återspegla den supportnivå som erbjuds av SAP HANA.
* **Inget stöd för att definiera relationer:** Bara en enda vy kan vara frågor inom en rapport och därför finns inget stöd för att definiera relationer.
* **Ingen datavy:** **datavyn** visar normalt detaljerad nivådata i tabellerna. På grund av naturen för OLAP-källor som SAP HANA, är den här vyn inte tillgänglig via SAP HANA.
* **Information om kolumner och mått är fasta:** listan över kolumner och mått som visas i fältlistan korrigeras i den underliggande källan och kan inte modifieras. Det går till exempel inte att ta bort en kolumn eller ändra dess datatyp (det går däremot att byta namn på den).
* **Ytterligare begränsningar i DAX:** det finns ytterligare begränsningar för DAX som kan användas i måttdefinitioner, för att återspegla begränsningar i källan. Det är till exempel inte möjligt att använda en aggregeringsfunktion via en tabell.

### <a name="additional-visualization-restrictions"></a>Ytterligare visualiseringsbegränsningar

Den finns några begränsningar i visualiseringar vid anslutning till SAP HANA med DirectQuery (behandla som flerdimensionell källa): 
* **Ingen sammansättning av kolumner:** Det går inte att ändra aggregering för en kolumn på en visualisering och den är alltid *Sammanfatta inte*.

## <a name="treat-sap-hana-as-a-relational-source"></a>Behandla SAP HANA som en relationskälla 

När du väljer att ansluta till SAP HANA som relationskälla blir viss ytterligare flexibilitet tillgänglig. Du kan exempelvis skapa beräknade kolumner, ta med data från flera SAP HANA-vyer och skapa relationer mellan de resulterande tabellerna. När du använder SAP HANA på detta sätt, är det dock viktigt att förstå vissa aspekter av hur anslutningar behandlas, för att kontrollera följande: 

* Resultaten motsvarar förväntningarna när SAP HANA-vyn innehåller icke-additiva mått (till exempel olika antal, eller medelvärden, istället för enkla summor).
* De resulterande frågorna är effektiva

Det är en god idé att börja med att förstå beteendet för en relationskälla såsom SQL Server när frågan som definierats i **Hämta data** eller **Frågeredigeraren** utför en aggregering. I exemplet som följer returnerar en fråga som definierats i **Frågeredigeraren** det genomsnittliga priset enligt *ProductID*.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Om data som importeras till Power BI (jämfört med DirectQuery), återges följande resultat:

* Data importeras på den aggregationsnivå som definierats av frågan som skapades i **Frågeredigeraren**. Till exempel, genomsnittligt pris på produkten. Detta resulterar i en tabell med de två kolumnerna *ProductID* och *AveragePrice* som kan användas i visuella objekt.
* I ett visuellt objekt kommer all efterföljande aggregation (exempelvis *summa*, *medelvärde*, *minimivärde*, övrigt) att utföras över den importerade informationen. Till exempel, om du inkluderar *genomsnittspris* i ett visuellt objekt kommer *Summa* att användas som standard. Summan returneras över *AveragePrice* för varje  *ProductID* – vilket i detta exempelfall är 13,67. Samma gäller för en annan mängdfunktion (t.ex *minimivärde*, *medelvärde*, osv) som används på den visuella informationen. Till exempel returnerar *medelvärde* för *genomsnittspris* medelvärdet för 6,66, 4 och 3, vilket är lika med 4,56 och inte medelvärdet av *Pris* från 6 poster i den underliggande tabellen, vilket är 5,17.
  
Om **DirectQuery** (över samma relationskälla) används i stället för Importera gäller samma semantik och samma resultat skapas:  

* Exakt samma data presenteras på rapportnivån för samma fråga – trots att data inte importeras.

* I ett visuellt objekt kommer all efterföljande aggregation (*summa*, *medelvärde*, *minimivärde*, övrigt) att utföras över den logiska tabellen från frågan. Och igen, ett visuellt objekt med *medelvärdet* av *Genomsnittspris* returnerar 4,56 igen.
  
Nu ska vi titta på SAP HANA när anslutningen behandlas som en relationskälla. Power BI kan arbeta med både *Analytiska vyer* och *Beräkningsvyer* i SAP HANA och båda innehåller mått. I dagsläget följer metoden för SAP HANA samma principer som vi beskriv tidigare i det här avsnittet: frågan som definierades i **Hämta data** eller **Frågeredigeraren** avgör tillgängliga data och alla efterföljande aggregeringar i visuella objekt sker över dessa data. Samma gäller för både Importera och DirectQuery.  
Men SAP HANA:s specifika egenskaper gör att frågan i den första dialogrutan i **Hämta data** eller **Frågeredigeraren** alltid är en aggregeringsfråga och kommer oftast innehålla mått där den faktiska aggregeringen som används definieras av SAP HANA-vyn.

Motsvarigheten till SQL Server-exemplet ovan är att det finns en SAP HANA-vy som innehåller *ID*, *ProductID*, *DepotID* och mått inklusive *AveragePrice* som har definierats i vyn som *Medelvärde av priset*.  
    
Om upplevelsen **Hämta data** innehåller val för måtten **ProductID** och **AveragePrice** är detta den definierande frågan för vyn som begär aggregerade data (i tidigare exempel har pseudo-SQL använts för enkelhetens skull, även om detta inte motsvarar den exakta syntaxen hos SAP HANA SQL). I sådant fall kommer ytterligare aggregeringar som definieras i det visuella objektet att aggregeras ytterligare till följd av en sådan fråga. Igen, enligt beskrivningen ovan för SQL Server gäller detta både för Import och DirectQuery. Observera att frågan från **Hämta data** eller **Frågeredigeraren** med DirectQuery är ett underordnat val inom en fråga som har skickats till SAP HANA. Således kommer inte alla data att läsas in före nästa aggregering.  

Alla dessa överväganden och beteenden kräver följande viktiga överväganden när du använder DirectQuery över SAP HANA:  

* Lägg märke till all annan aggregering som utförs i visuella objekt när måttet i SAP HANA inte är additivt (till exempel inte en enkel *summa*, *minimivärde* eller *maxvärde*).

* I **Hämta data** eller **Frågeredigeraren** tas endast de obligatoriska kolumnerna med för att hämta nödvändiga data, vilket speglar det faktum att resultatet måste vara en rimlig fråga som kan skickas till SAP HANA. Till exempel, om du väljer dussintals kolumner eftersom du tror att de kommer att behövas för efterföljande visuella objekt kommer aggregatfrågan som används i det underordnade valet för DirectQuery att innehålla dessa dussintals kolumner. De kommer att prestera under förväntan.
  
Låt oss ta en titt på ett exempel. Om vi väljer fem kolumner i följande exempel (**CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**) i dialogrutan **Hämta data** tillsammans med måttet *OrderQuantity* betyder det att följande SQL-fråga ställs till SAP HANA om vi skapar ett enkelt visuellt objekt med Min OrderQuantity (minsta beställningskvantitet). Den skuggade delen är delmarkeringen som innehåller frågan från **Hämta data** / **frågeredigeraren**. Om den här delmarkeringen ger ett resultat med mycket hög kardinalitet kommer resultatet från SAP HANA antagligen vara otillfredsställande.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
På grund av detta beteende rekommenderar vi att objekt som valts i **Hämta data** eller **Frågeredigeraren** begränsas till nödvändiga objekt för att utgöra en lämplig fråga för SAP HANA.  

## <a name="best-practices"></a>Metodtips 

För båda metoderna för att ansluta till SAP HANA gäller även rekommendationer för att använda DirectQuery för SAP HANA, särskilt de som är relaterade till att säkerställa bra prestanda. De här rekommendationerna beskrivs i detalj i artikeln [använda DirectQuery i Power BI](desktop-directquery-about.md).
   
## <a name="limitations"></a>Begränsningar

I följande lista beskrivs alla SAP HANA-funktioner som inte stöds fullt ut eller funktioner som fungerar annorlunda mot när du använder Power BI. 

* **Överordnade-underordnade hierarkier** – Överordnade-underordnade hierarkier visas inte i Power BI.
Detta beror på att Power BI har åtkomst till SAP HANA med SQL-gränssnittet och överordnade-underordnade hierarkier inte fullständigt kan nås via SQL.
* **Andra metadata för hierarki** – Grundstrukturen för hierarkier visas i Power BI, men vissa metadata för hierarki (till exempel att styra beteendet för ojämna hierarkier) har ingen effekt.
Detta beror på begränsningar av SQL-gränssnittet.
* **Anslutningen med SSL** – Du kan inte ansluta till SAP HANA-instanser som konfigurerats för att använda SSL.
Stöd för attributvyer – Power BI kan ansluta till vyer för analys och beräkning, men det går inte att ansluta direkt till attributvyer.
* **Stöd för katalogobjekt** – Power BI kan inte ansluta till katalogobjekt.
* **Ändra till variabler efter publicering** – Du kan inte ändra värdena för SAP HANA-variabler direkt i Power BI-tjänsten när rapporten har publicerats. 
 
## <a name="known-issues"></a>Kända problem 
I följande lista beskrivs alla kända problem vid anslutning till SAP HANA (DirectQuery) med hjälp av Power BI. 

* **SAP HANA-problem vid fråga för räknare och andra åtgärder** – Felaktiga data returneras från SAP HANA om anslutning till en analysvy och ett räknarmått och vissa andra förhållandemått ingår i samma visualisering. Detta omfattas av SAP-kommentar 2128928 (oväntade resultat vid fråga för en beräknad kolumn och en räknare. Förhållandemåttet blir felaktig i det här fallet. 

* **Flera Power BI-kolumner från en enda SAP HANA-kolumn** – För vissa beräkningsvyer, där en SAP HANA-kolumn används i fler än en hierarki, visar SAP HANA detta som två separata attribut. Detta resulterar i att två kolumner skapas i Power BI.  Dessa kolumner döljs som standard, men alla frågor som rör hierarkierna eller kolumnerna direkt fungerar korrekt. 
 
## <a name="next-steps"></a>Nästa steg

Mer information om DirectQuery finns i följande resurser:

* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [Lokal datagateway](service-gateway-onprem.md)

