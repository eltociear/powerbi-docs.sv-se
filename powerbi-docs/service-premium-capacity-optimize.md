---
title: Optimera Power BI Premium-kapaciteter
description: Beskriver optimeringsstrategier för Power BI Premium-kapaciteter.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 4d03419105244b7fddafea3b26b69e4f4f5f874c
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207699"
---
# <a name="optimizing-premium-capacities"></a>Optimera Premium-kapaciteter

Om det uppstår prestandaproblem för Premium-kapaciteter börjar du vanligtvis med att optimera eller finjustera lösningarna för att återställa godtagbara svarstider. Tanken är att du ska undvika att köpa ytterligare Premium-kapacitet såvida det inte är motiverat.

När du behöver ytterligare Premium-kapacitet finns två alternativ. Dessa beskrivs i den här artikeln:

- Skala upp en befintlig Premium-kapacitet
- Lägg till en Premium-kapacitet

Artikeln avslutas med test av metoder och Premium-kapacitetsstorlek.

## <a name="best-practices"></a>Metodtips

Det finns rekommenderade metoder för att få bästa användning och prestanda. Du kan till exempel:

- Använda arbetsytor i stället för personliga arbetsytor.
- Dela upp verksamhetskritisk och BI med självbetjäning (SSBI) i olika kapaciteter.

  ![Dela upp verksamhetskritisk och BI med självbetjäning i olika kapaciteter](media/service-premium-capacity-optimize/separate-capacities.png)

- Om du delar innehåll endast med Power BI Pro-användare, kanske det inte finns något behov av att lagra innehållet i en dedikerad kapacitet.
- Använd dedikerade kapaciteter när du vill uppnå en specifik uppdateringstid eller när specifika funktioner är nödvändiga. Det kan till exempel gälla stora datauppsättningar eller sidnumrerade rapporter.

### <a name="addressing-common-questions"></a>Adressering av vanliga frågor

Att optimera distributioner för Power BI Premium är ett komplext ämne som inbegriper en förståelse för arbetsbelastningskraven, tillgängliga resurser och effektiv användning.

Den här artikeln behandlar sju vanliga supportfrågor, som beskriver eventuella problem och förklaringar, samt information om hur du identifierar och löser dem.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Varför är kapaciteten långsam och vad kan jag göra?

Det finns många skäl som kan bidra till en långsam Premium-kapacitet. Den här frågan kräver ytterligare information om vad som menas med långsam. Läses rapporter in långsamt? Eller läses de inte in alls? Tar det lång tid att läsa in eller uppdatera visuella rapportobjekt när användare interagerar med rapporten? Tar uppdateringar längre tid än väntat eller längre tid än de gjorde tidigare?

Om du får en uppfattning om orsaken kan du sedan börja undersöka. Svar på följande sex frågor kommer hjälpa dig att lösa mer specifika problem.

### <a name="what-content-is-using-up-my-capacity"></a>Vilket innehåll använder upp min kapacitet?

Du kan använda **Kapacitetsmåttappen för Power BI Premium** för att filtrera efter kapacitet och granska prestandamått för arbetsyteinnehåll. Du kan granska prestandamått och resursanvändningen per timme för de senaste sju dagarna för allt innehåll som lagras i en Premium-kapacitet. Övervakning är ofta det första steget när du felsöker ett allmänt prestandaproblem för Premium-kapacitet.

Viktiga mått att övervaka är:

- Processorgenomsnitt och antal med hög användning.
- Genomsnittligt minne och antal hög användning, och minnesanvändning för specifika datauppsättningar, dataflöden och sidnumrerade rapporter.
- Aktiva datauppsättningar som lästs in i minnet.
- Genomsnittliga och högsta frågevaraktigheter.
- Genomsnittliga frågeväntetider.
- Genomsnittliga uppdateringstider för datauppsättning och dataflöde.

I kapacitetsmåttappen för Power BI Premium visar aktivt minne den totala mängd minne som tilldelats till en rapport som inte kan tas bort eftersom den använts under de senaste tre minuterna. En hög topp i väntetid för uppdatering kan kopplas till en stor och/eller aktiv datauppsättning.

Diagrammet **De 5 främsta efter genomsnittlig varaktighet** visar de fem främsta datauppsättningarna, sidnumrerade rapporter och dataflöden som förbrukar kapacitetsresurser. Innehåll i de fem främsta listorna lämpar sig för undersökning och möjlig optimering.

### <a name="why-are-reports-slow"></a>Varför är rapporter långsamma?

I följande tabeller visas eventuella problem och hur du kan identifiera och hantera dem.

#### <a name="insufficient-capacity-resources"></a>Inte tillräckligt med kapacitetsresurser

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Högt totalt aktivt minne (modellen kan inte tas bort eftersom den använts under de senaste tre minuterna).<br><br> Flera höga toppar i frågeväntetider.<br><br> Flera höga toppar i uppdateringsväntetider. | Övervaka minnesmått \[[1](#endnote-1)\], och antal borttagningar \[[2](#endnote-2)\]. | Minska modellstorleken eller konvertera till DirectQuery-läge. Se avsnittet [Optimera modeller](#optimizing-models) i den här artikeln.<br><br> Skala upp kapaciteten.<br><br> Tilldela innehållet till en annan kapacitet. |

#### <a name="inefficient-report-designs"></a>Ineffektiva rapportutformningar

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Rapportsidor innehåller för många visuella objekt (interaktiv filtrering kan utlösa minst en fråga per visuellt objekt).<br><br> Visuella objekt hämtar mer data än vad som behövs. | Granska rapportutformningar.<br><br> Intervjua rapportanvändare för att förstå hur de interagerar med rapporter.<br><br> Övervaka frågemått för datauppsättningen \[[3](#endnote-3)\]. | Designa om rapporter med färre visuella objekt per sida. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Datauppsättningen är långsam (särskilt när rapporter tidigare har presterat bra)

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Allt större volymer av importdata.<br><br> Komplex eller ineffektiv beräkningslogik, inklusive RLS-roller.<br><br> Modellen inte helt optimerad.<br><br> (DQ/LC) Gateway-svarstid.<br><br> Långsamma frågesvarstider från DQ-källa. | Granska modellutformningar.<br><br> Övervaka gateway-prestandaräknare. | Se avsnittet [Optimera modeller](#optimizing-models) i den här artikeln. |

#### <a name="high-concurrent-report-usage"></a>Hög samtidig rapportanvändning

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Höga frågeväntetider.<br><br> Processormättnad.<br><br> DQ-/LC-anslutningsgräns har överskridits. | Övervaka processoranvändning \[[4](#endnote-4)\], frågeväntetider och DQ-/LC-användning \[[5](#endnote-5)\] mått + frågevaraktigheter. Om det fluktuerar kan detta antyda samtidighetsproblem. | Skala upp kapaciteten eller tilldela innehållet till en annan kapacitet.<br><br> Designa om rapporter med färre visuella objekt per sida. |

**Obs!**    
<a name="endnote-1"></a>\[1\] Genomsnittlig minnesanvändning (GB) och högsta minnesförbrukning (GB).   
<a name="endnote-2"></a>\[2\] Borttagna datauppsättningar.   
<a name="endnote-3"></a>\[3\] Datauppsättningsfrågor, Total minskning av frågevaraktighet (ms), Andel väntande datauppsättningar och Datauppsättningens genomsnittliga väntetid (ms).   
<a name="endnote-4"></a>\[4\] Hög användning av CPU och CPU-tid för högsta användning (senaste sju dagarna).   
<a name="endnote-5"></a>\[5\] Hög användning av DQ/LC och DQ/LC-tid för högsta användning (senaste sju dagarna).   

### <a name="why-are-reports-not-loading"></a>Varför läses rapporter inte in?

Om det inte går att läsa in rapporter är detta ett säkert tecken på att kapaciteten inte har tillräckligt med minne och är överhettad. Detta kan inträffa när alla inlästa modeller aktivt efterfrågas och därför inte kan tas bort och uppdateringsåtgärder har pausats eller fördröjts. Power BI-tjänsten kommer att försöka läsa in datauppsättningen i 30 sekunder och användaren meddelas smidigt om felet med ett förslag att försöka igen om en stund.

Det finns för närvarande inga mått att övervaka för fel vid rapportinläsning. Du kan identifiera risken för det här problemet genom att övervaka systemminnet, särskilt högsta användning och tidpunkt för högsta användning. Hög borttagning av datauppsättning och långa genomsnittliga väntetider för uppdateringar av datauppsättningar kan innebära att det här problemet sker.

Om det händer mycket sällan, kanske detta inte är ett problem med prioritet. Rapportanvändare informeras om att tjänsten är upptagen och att de kan försöka igen om en liten stund. Om det händer för ofta, kan problemet lösas genom att skala upp Premium-kapaciteten eller genom att tilldela innehållet till en annan kapacitet.

Kapacitetsadministratörer (och Power BI-tjänstadministratörer) kan övervaka måttet **Frågefel** för att avgöra när det här händer. De kan också starta om kapaciteten för att återställa alla åtgärder vid systemöverbelastning.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Varför startar inte uppdateringar enligt schemat?

Schemalagda uppdateringsstarttider är inte garanterade. Kom ihåg att Power BI-tjänsten alltid prioriterar interaktiva åtgärder över bakgrundsåtgärder. Uppdatering är en bakgrundsåtgärd som kan ske när två villkor är uppfyllda:

- Det finns tillräckligt med minne
- Antalet samtidiga uppdateringar som stöds för Premium-kapacitet överskrids inte

När villkoren inte uppfylls, köas uppdateringen tills villkoren är tillräckliga.

Kom ihåg att det krävs minst dubbelt av den aktuella datauppsättningens minnesstorlek för en fullständig uppdatering. Om det inte finns tillräckligt med minne, kan inte uppdateringen påbörjas förrän modellborttagning frigör minne – detta innebär fördröjningar tills en eller flera datauppsättningar blir inaktiva och kan tas bort.

Kom ihåg att det högsta tillåtna antalet samtidiga uppdateringar är inställt på 1,5 gånger serverdelens v-kärnor, avrundat uppåt.

En schemalagd uppdatering misslyckas när den inte kan påbörjas innan nästa schemalagda uppdatering ska påbörjas. En uppdatering på begäran som utlöses manuellt från användargränssnittet försöker köra upp till tre gånger innan åtgärden misslyckas.

Kapacitetsadministratörer (och Power BI-tjänstadministratörer) kan övervaka måttet **Genomsnittlig uppdateringsväntetid (minuter)** för att fastställa genomsnittlig fördröjning mellan den schemalagda tiden och start för åtgärden.

Även om det vanligtvis inte är en administrativ prioritet, se till att det finns tillräckligt med minne för att underlätta att datauppdateringar sker i tid. Detta kan innebära att isolera datauppsättningar till kapaciteter med kända tillräckliga resurser. Det är också möjligt för administratörer att prata med datauppsättningens ägare för att sprida ut eller minska schemalagda uppdateringstider för att minimera kollisioner. Observera att det inte är möjligt för en administratör att visa uppdateringskön eller hämta datauppsättningens scheman.

### <a name="why-are-refreshes-slow"></a>Varför är uppdateringarna långsamma?

Uppdateringar kan vara långsamma eller upplevas långsamma (som tidigare vanliga fråga tar upp).

När uppdateringen faktiskt är långsam, kan det vara av flera olika orsaker:

- Otillräcklig CPU (uppdateringar kan vara mycket CPU-intensiva).
- Otillräckligt med minne, vilket resulterar i att uppdateringen pausas (vilket kräver att uppdateringen början om när villkoren är tillräckliga för att upprepa).
- Icke-kapacitetsskäl, till exempel datakällans systemsvarstid, nätverksfördröjning, ogiltig behörighet eller gateway-genomflöde.
- Datavolym – ett bra skäl att konfigurera inkrementell uppdatering, som beskrivs nedan.

Kapacitetsadministratörer (och Power BI-tjänstadministratörer) kan övervaka måttet **Genomsnittlig uppdateringsvaraktighet (minuter)** för att fastställa benchmark för jämförelse över tid och måttet **Genomsnittlig uppdateringsväntetid (minuter)** för att fastställa genomsnittlig fördröjning mellan den schemalagda tiden och start för åtgärden.

Inkrementell uppdatering kan avsevärt minska varaktighet för uppdatering, särskilt för stora datamodellstabeller. Det finns fyra fördelar med inkrementell uppdatering:

- **Snabbare uppdateringar** – Endast en del av en tabell behöver läsas in, vilket minskar CPU- och minnesanvändning och parallellitet kan vara högre när du uppdaterar flera partitioner.
- **Uppdateringar sker bara vid behov** – Inkrementella uppdateringsprinciper kan konfigureras så att inläsningar bara sker när data har ändrats.
- **Mer tillförlitliga uppdateringar** – Kortare körning av anslutningar till ej beständiga datakällsystem är mindre känsliga för frånkoppling.
- **Modeller förblir trimmade** – Inkrementella uppdateringsprinciper kan konfigureras för att automatiskt ta bort historik utöver en glidande tidsperiod.

Mer information finns i [Inkrementell uppdatering i Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Varför slutförs inte datauppdateringar?

När datauppdateringen påbörjas men inte kan slutföras, kan det finnas flera olika orsaker:

- Otillräckligt minne, även om det endast finns en modell i Premium-kapaciteten, d.v.s. modellstorleken är mycket stor.
- Icke-kapacitetsskäl, inklusive frånkoppling av datakällan, ogiltig behörighet eller gateway-fel.

Kapacitetsadministratörer (och Power BI-tjänstadministratörer) kan övervaka måttet **Uppdateringsfel på grund av minnesbrist**.

## <a name="optimizing-models"></a>Optimera modeller

Optimal modelldesign är avgörande för att leverera en effektiv och skalbar lösning. Det är dock utanför omfattningen av den här artikeln att tillhandahålla en fullständig beskrivning. I stället innehåller det här avsnittet viktiga områden att överväga när du optimerar modeller.

### <a name="optimizing-power-bi-hosted-models"></a>Optimera Power BI-värdbaserade modeller

Optimering av modeller som finns i en Premium-kapacitet kan uppnås vid datakällorna och modellagren.

Överväg optimeringsmöjligheterna för en importmodell:

![Optimeringsmöjligheterna för en importmodell](media/service-premium-capacity-optimize/import-model-optimizations.png)

På datakällans nivå:

- Relationsdatakällor kan optimeras för att säkerställa den snabbaste möjliga uppdateringen av i förväg integrerande data, tillämpa rätt index, definiera tabellpartitioner som passar för inkrementella uppdateringsperioder och materialiseringsberäkningar (i stället för beräknade modelltabeller och kolumner) eller lägga till beräkningslogik till vyer.
- Icke-relationella datakällor kan integreras i förväg med relationslagringsplatser.
- Se till att gatewayer har tillräckligt med resurser, helst på dedikerade virtuella datorer, med tillräckligt med nätverksbandbredd och närheten till datakällor.

På modellnivå:

- Power Query-frågeutformningar kan minimera eller ta bort komplexa omvandlingar och särskilt de som slår ihop olika datakällor (informationslager uppnår detta under steget extrahering-transformering-inläsning). Dessutom kan de säkerställa att lämpliga sekretessnivåer för datakällor är inställda. Detta kan göra att Power BI inte behöver läsa in fullständiga resultat för att skapa ett kombinerat resultat för frågor.
- Modellstrukturen identifierar data som ska läsas in och har direkt inverkan på modellstorleken. Den kan utformas till att undvika att onödiga data läses in genom att ta bort kolumner, ta bort rader (särskilt historiska data) eller genom att läsa in sammanfattningsdata (på bekostnad av inläsning av detaljerade data). Dramatisk storleksminskning kan uppnås genom att ta bort kolumner med hög kardinalitet (särskilt textkolumner) som inte lagrar eller komprimerar särskilt effektivt.
- Modellfrågeprestanda kan förbättras genom att konfigurera relationer med enkelriktning om det inte finns en bra anledning till att tillåta dubbelriktad filtrering. Du kan också använda funktionen [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) i stället för dubbelriktad filtrering.
- Aggregeringstabeller kan uppnå snabba frågesvar genom att läsa i förväg sammanfattade data, men det här ökar storleken på modellen och leder till längre uppdateringstider. I allmänhet ska aggregeringstabeller reserveras för mycket stora modeller eller sammansatta modellutformningar.
- Beräknade tabeller och kolumner ökar storleken på modellen och resulterar i längre uppdateringstider. I allmänhet kan en mindre lagringsstorlek och snabbare uppdateringstid ske när data är materialiserad eller beräknad i datakällan. Om detta inte är möjligt kan användning av Power Query-anpassade kolumner erbjuda förbättrad lagringskomprimering.
- Det kan finnas möjlighet att finjustera DAX-uttryck för mått och RLS-regler, kanske skriva om logik för att undvika dyra formler
- Inkrementell uppdatering kan avsevärt minska uppdateringstiden och spara minne och processor. Inkrementell uppdatering kan också konfigureras för att ta bort historiska data för att hålla modellstorlekar i trim.
- En modell kan göras om till två modeller när det finns olika och motstridiga frågemönster. Till exempel har vissa rapporter höga nivåer av aggregeringar över all historik och kan tolerera 24 timmars svarstid. Andra rapporter gäller för dagens data och behöver detaljerad åtkomst till enskilda transaktioner. Skapa hellre två modeller som är optimerade för alla behov i stället för att utforma en enda modell som ska räcka åt alla rapporter.

Överväg optimeringsmöjligheterna för en DirectQuery-modell. När modellen utfärdar frågebegäranden till den underliggande datakällan, är optimering av datakällan mycket viktigt för att leverera dynamiska modellfrågor.

 ![Optimeringsmöjligheterna för en DirectQuery-modell](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

På datakällans nivå:

- Datakällan kan optimeras för att säkerställa snabbaste möjliga frågor genom att integrera data i förväg (vilket inte är möjligt på modellnivån), tillämpa rätt index, definiera tabellpartitioner materialisera sammanfattade data (med indexerade vyer), och minimera mängden beräkning. Den bästa upplevelsen uppnås när direktfrågor bara behöver filtrera och utföra inre kopplingar mellan indexerade tabeller eller vyer.
- Se till att gatewayer har tillräckligt med resurser, helst på dedikerade virtuella datorer, med tillräckligt med nätverksbandbredd och i närheten till datakällan.

På modellnivå:

- Power Query-frågedesigner ska helst inte tillämpa några omvandlingar – försök annars hålla omvandlingar till ett absolut minimum.
- Modellfrågeprestanda kan förbättras genom att konfigurera relationer med enkelriktning om det inte finns en bra anledning till att tillåta dubbelriktad filtrering. Dessutom ska modellrelationer konfigureras till att anta referensintegritet användas (när så är fallet) vilket leder till att datakällfrågor använder inre kopplingar effektivare (i stället för yttre kopplingar).
- Undvik att skapa anpassade kolumner för Power Query-frågor eller modellberäknad kolumn – materialisera dessa i datakällan, när det är möjligt.
- Det kan finnas möjlighet att finjustera DAX-uttryck för mått och RLS-regler, kanske skriva om logik för att undvika dyra formler.

Överväg optimeringsmöjligheterna för en sammansatt modell. Kom ihåg att en sammansatt modell möjliggör en blandning av import- och DirectQuery-tabeller.

![Optimeringsmöjligheterna för en sammansatt modell](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- I allmänhet gäller optimeringen för import- och DirectQuery-modeller för sammansatta modelltabeller som använder dessa lagringslägen.
- Normalt ska du sträva efter att uppnå en belastningsutjämnade design genom att konfigurera tabeller av dimensionstyp (som representerar affärsentiteter) som dubbelt lagringsläge och tabeller av faktatyp (ofta stora tabeller som representerar operativa fakta) som DirectQuery-lagringsläge. Dubbelt lagringsläge innebär både import- och DirectQuery-lagringslägena, och detta gör att Power BI-tjänsten kan fastställa det mest effektiva lagringsläget att använda när du genererar en intern fråga för genomströmning.
- Se till att gatewayer har tillräckligt med resurser, helst på dedikerade virtuella datorer, med tillräckligt med nätverksbandbredd och närheten till datakällor
- Aggregeringstabeller konfigurerade som importlagringsläge kan leverera dramatiska förbättringar i frågeprestanda när de används för att sammanfatta tabeller av faktatyp för DirectQuery-lagringsläge. I det här fallet ökar aggregeringstabeller storleken på modellen och ökar uppdateringstiden, och det här är ofta en acceptabel kompromiss för snabbare frågor.

### <a name="optimizing-externally-hosted-models"></a>Optimera externt värdbaserade modeller

Många optimeringsmöjligheter som beskrivs i avsnittet [Optimera Power BI-värdbaserade modeller](#optimizing-power-bi-hosted-models) gäller även för modeller som utvecklats med Azure Analysis Services och SQL Server Analysis Services. Klara undantag är vissa funktioner som för närvarande inte stöds, inklusive sammansatta modeller och aggregeringstabeller.

Ytterligare ett övervägande för externt värdbaserade datauppsättningar är den databas som är värd i förhållande till Power BI-tjänsten. För Azure Analysis Services innebär det att skapa Azure-resursen i samma region som Power BI-klienten (hemregion). För SQL Server Analysis Services, för IaaS, innebär detta värdskap för den virtuella datorn i samma region, och för lokala datorer innebär det att säkerställa en effektiv gateway-installation.

Det kan vara av intresse att observera att Azure Analysis Services-databaser och SQL Server Analysis Services-tabelldatabaser kräver att deras modeller fullständigt läses in i minnet och att de förblir där hela tiden som stöd för frågor. Precis som för Power BI-tjänsten måste det finnas tillräckligt med minne för att uppdatera om modellen måste vara online under uppdateringen. Till skillnad från Power BI-tjänsten finns det inget koncept för att modeller automatiskt föråldras in och ut ur minnet enligt användning. Power BI Premium, erbjuder därför en mer effektiv metod för att maximera modellfrågor med lägre minnesanvändning.

## <a name="capacity-planning"></a>Kapacitetsplanering

Storleken på en Premium-kapacitet anger dess tillgängliga minne och processorresurser och begränsningar som har införts på kapaciteten. Antal Premium-kapaciteter är också något att överväga, eftersom man genom att skapa flera Premium-kapaciteter kan hjälpa till att isolera arbetsbelastningar från varandra. Observera att lagringen är 100 TB per kapacitetsnod och det är troligen mer än tillräckligt för alla arbetsbelastningar.

Att fastställa storleken på och antalet Premium-kapaciteter kan vara en utmaning, särskilt för den inledande kapaciteten som du skapar. Det första steget vid fastställande av kapacitetsstorlek är att förstå genomsnittlig arbetsbelastning som representerar förväntad daglig användning. Det är viktigt att förstå att inte alla arbetsbelastningar är lika. I ena änden av spektrumet kan t.ex. 100 samtidiga användare med åtkomst till en enda rapportsida som innehåller ett enda visuellt objekt enkelt uppnås. Men i den andra änden av spektrumet kommer 100 samtidiga användare med åtkomst till 100 olika rapporter, var och en med 100 visuella objekt på rapportsidan, att ha mycket olika krav på resurskapacitet.

Kapacitetsadministratörer behöver därför inte tänka på många faktorer specifika för miljö, innehåll och förväntad användning. Det övergripande målet är att maximera kapacitetsanvändning samtidigt som konsekventa frågetider, godkända väntetider och borttagningsintervall levereras. Faktorer att överväga kan innefatta:

- **Modellstorlek och dataegenskaper** – Importmodeller måste vara helt inlästa i minnet för att fråga eller uppdatera. LC-/DQ-datauppsättningar kan kräva betydande processortid och eventuellt betydande minne för att utvärdera komplexa åtgärder eller RLS-regler. Minne- och processorstorlek och LC-/DQ-frågedataflöde är begränsat av kapacitetsstorleken.
- **Samtidiga aktiva modeller** – Samtidiga frågor för olika importmodeller kommer att leverera bästa svarstider och prestanda när de finns kvar i minnet. Det bör finnas tillräckligt med minne för att vara värd för alla mycket frågade modeller, med ytterligare minne för att möjliggöra deras uppdateringar.
- **Uppdatering av importmodell** – Uppdateringstyp (fullständig eller inkrementell), varaktighet och komplexitet i Power Query-frågor och beräknad logik för tabell/kolumn kan påverka minnesanvändningen och särskilt processoranvändningen. Samtidiga uppdateringar är begränsade av kapacitetsstorlek (1,5 x serverdelens v-kärnor, avrundas uppåt).
- **Samtidiga frågor** – Många samtidiga frågor kan resultera i rapporter som inte svarar när processor- eller LC-/DQ-anslutningar överskrider kapacitetsgränsen. Detta gäller särskilt för rapportsidor som innehåller många visuella objekt.
- **Dataflöden och sidnumrerade rapporter** – Kapaciteten kan konfigureras till att stödja dataflöden och sidnumrerade rapporter, och var och en kräver en konfigurerbar högsta procentandel av kapacitetsminne. Minne allokeras dynamiskt till dataflöden, men allokeras statiskt till sidnumrerade rapporter.

Förutom de här faktorerna kan kapacitetsadministratörer överväga att skapa flera kapaciteter. Flera kapaciteter möjliggör isolering av arbetsbelastningar och kan konfigureras för att säkerställa att prioritetsarbetsbelastningar har garanterade resurser. Till exempel kan två kapaciteter skapas för att avgränsa affärskritiska arbetsbelastningar från självbetjänade BI (SSBI) arbetsbelastningar. Affärskritisk kapacitet kan användas för att isolera stora företagsmodeller vilket ger dem garanterade resurser med redigeringsåtkomst beviljad endast till IT-avdelningen. SSBI-kapaciteten kan användas som värd för ett växande antal mindre modeller med åtkomst beviljad till affärsanalytiker. SSBI-kapaciteten kan ibland uppleva väntetider för frågor eller uppdateringar som är acceptabla.

Framöver kan kapacitetsadministratörer balansera arbetsytor i kapaciteter genom att flytta innehåll mellan arbetsytor eller arbetsytor mellan kapaciteter, och genom att skala upp eller ner kapaciteter. För större modeller skalar du i allmänhet upp och för högre samtidighet skalar du ut.

Kom ihåg att köpa en licens som ger klienten v-kärnor. Köp av en **P3**-prenumeration kan användas för att skapa en eller upp till fyra Premium-kapaciteter, d.v.s. 1 x P3 eller 2 x P2 eller 4 x P1. Dessutom före uppskalning av en P2-kapacitet till en P3-kapacitet kan hänsyn tas till uppdelningen av v-kärnor för att skapa två P1-kapaciteter.

## <a name="testing-approaches"></a>Testa metoder

När en kapacitetsstorlek avgörs kan testning utföras genom att skapa en kontrollerad miljö. Ett praktiskt och ekonomiskt alternativ är att skapa en Azure-kapacitet (A SKU:er), notera att en P1-kapacitet har samma storlek som en A4-kapacitet, och P2- och P3-kapaciteter har samma storlek som A5- och A6-kapaciteten respektive. Azure-funktionerna kan skapas snabbt och debiteras per timme. Så när testningen är klar, kan de enkelt tas bort om du vill sluta ha kostnader.

Testinnehållet kan läggas till arbetsytor som skapats på Azure-kapacitet och sedan kan en enskild användare köra rapporter för att generera en realistisk och representativ arbetsbelastning för frågor. Om det finns importmodeller, ska en uppdatering för varje modell också utföras. Övervakningsverktyg kan sedan användas för att granska alla mått för att förstå resursanvändning.

Det är viktigt att testerna är upprepningsbara. Testerna ska köras flera gånger och de ska leverera ungefär samma resultat varje gång. Ett medeltal av de här resultaten kan användas för att extrapolera och beräkna en arbetsbelastning under sanna produktionsvillkor.

Om du redan har en kapacitet och de rapporter som du vill göra ett belastningstest för, kan du använda [PowerShell-verktyget för belastningsgenerering](https://aka.ms/PowerBILoadTestingTool) för att snabbt generera ett belastningstest. Med verktyget kan du uppskatta hur många instanser av varje rapport din kapacitet kan köra på en timme. Du kan använda verktyget till att utvärdera din kapacitets förmåga att återge en enskild rapport eller flera olika rapporter samtidigt. Mer information finns i videon [Microsoft Power BI: Premiumkapacitet](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Om du vill generera ett mer komplext test kan du utveckla ett belastningstestprogram som simulerar en realistisk arbetsbelastning. Mer information finns i webbseminariet [Load Testing Power BI Applications with Visual Studio Load Test](https://powerbi.microsoft.com/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/).

## <a name="acknowledgements"></a>Bekräftelser

Den här artikeln är skriven av Peter Myers, Data Platform MVP och oberoende BI-expert på [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Premium-kapacitetsscenarier](service-premium-capacity-scenarios.md)   
  
Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)