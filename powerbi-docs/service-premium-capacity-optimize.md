---
title: Optimera Microsoft Power BI Premium-kapaciteter
description: Beskriver optimering strategier för Power BI Premium-kapacitet.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565340"
---
# <a name="optimizing-premium-capacities"></a>Optimera Premium-kapaciteter

När det uppstår prestandaproblem för Premium-kapacitet, är ett vanligt första sätt att optimera eller finjustera dina lösningar om du vill återställa godtagbara svarstider. Anledningen är att undvika att köpa ytterligare Premium-kapacitet om inte visas.

När det krävs ytterligare Premium-kapacitet, det finns två alternativ som beskrivs i den här artikeln:

- Skala upp en befintlig Premium-kapacitet
- Lägg till en Premium-kapacitet

Slutligen testar metoder och Premium-kapacitetsstorlek avslutar den här artikeln.

## <a name="best-practices"></a>Metodtips

När du försöker få bästa användning och prestanda, finns det några rekommenderade metodtips, inklusive:

- Med app-arbetsytor i stället för personliga arbetsytor.
- Att dela upp affärskritisk och Self-Service BI () pådin stationära i olika kapaciteter.

  ![Dela upp verksamhetskritisk och BI med självbetjäning i olika kapaciteter](media/service-premium-capacity-optimize/separate-capacities.png)

- Om delar innehåll endast med Power BI Pro-användare kan finnas det behöver du inte lagra innehållet i en dedikerad kapacitet.
- Använda dedikerade kapacitet när du vill uppnå en specifik Uppdateringstid eller när specifika funktioner krävs. Till exempel med stora datauppsättningar eller sidnumrerade rapporter.

### <a name="addressing-common-questions"></a>Åtgärda vanliga frågor

Optimera distributioner av Power BI Premium är ett komplext ämne som inbegriper en förståelse för arbetsbelastningskraven, tillgängliga resurser och effektiv användning.

Den här artikeln tar upp till sju vanliga supportfrågor, som beskriver eventuella problem och förklaringar och information om hur du identifierar och löser dem.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Varför är kapaciteten långsam och vad kan jag göra?

Det finns många skäl som kan bidra till en långsam Premium-kapacitet. Den här frågan kräver ytterligare information om vad som menas med långsam. Läses rapporter in långsamt? Eller läses de inte in alls? Tar det lång tid att läsa in eller uppdatera visuella rapportobjekt när användare interagerar med rapporten? Uppdateras tar längre tid än väntat eller tidigare gav?

Om du får en uppfattning om orsaken kan du sedan börja undersöka. Svar på följande sex frågor kommer hjälpa dig att lösa mer specifika problem.

### <a name="what-content-is-using-up-my-capacity"></a>Vilket innehåll använder upp min kapacitet?

Du kan använda **Kapacitetsmåttappen för Power BI Premium** för att filtrera efter kapacitet och granska prestandamått för arbetsyteinnehåll. Det är möjligt att granska prestanda mått och resursanvändningen per timme för de senaste sju dagarna för allt innehåll som lagras i en Premium-kapacitet. Övervakning är ofta det första steget för att ta när du felsöker ett allmänt problem om prestanda för Premium-kapacitet.

Viktiga mått att övervaka är:

- Genomsnittlig processoranvändning och antal för hög användning.
- Genomsnittlig minne och antal hög användning och minnesanvändning för specifika datauppsättningar, dataflöden och sidnumrerade rapporter.
- Aktiva datauppsättningar läses in i minnet.
- Genomsnittligt och högsta fråga varaktigheter.
- Genomsnittlig fråga väntetider.
- Uppdatera gånger genomsnittlig datauppsättningen och dataflöde.

Aktiva minne visar den totala mängden minne som tilldelas en rapport som inte kan tas bort eftersom den har använts under de senaste tre minuterna i appen Power BI Premium-kapacitet. En hög topp i väntetid för uppdatering kan kopplas till en stor och/eller aktiv datauppsättning.

Den **5 främsta av Genomsnittlig varaktighet** diagram visar de fem främsta datauppsättningar, sidnumrerade rapporter och dataflöden som förbrukar resurser för kapacitet. Innehåll i fem främsta listor är lämpliga för undersökning och möjliga optimering.

### <a name="why-are-reports-slow"></a>Varför är rapporter långsamma?

I följande tabeller visas eventuella problem och hur du kan identifiera och hantera dem.

#### <a name="insufficient-capacity-resources"></a>Inte tillräckligt med kapacitetsresurser

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Totalt antal aktiva RAM-minne (modellen kan inte tas bort eftersom den inte används under de senaste tre minuterna).<br><br> Väntetid för flera hög toppar i fråga.<br><br> Flera hög toppar i uppdatering vänta gånger. | Övervaka minne mått \[ [1](#endnote-1)\], och borttagning antal \[ [2](#endnote-2)\]. | Minska storleken modell, eller konvertera till DirectQuery-läge. Se den [optimera modeller](#optimizing-models) i den här artikeln.<br><br> Skala upp kapaciteten.<br><br> Tilldela innehållet till en annan kapacitet. |

#### <a name="inefficient-report-designs"></a>Ineffektiva rapportutformningar

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Rapportsidor innehåller för många visuella objekt (Interaktiv filtrering kan utlösa minst en fråga per visuellt objekt).<br><br> Visuella objekt att hämta mer data än vad som krävs. | Granska report Designer.<br><br> Intervjua rapportanvändare för att förstå hur de interagerar med rapporter.<br><br> Övervaka datauppsättning fråga mått \[ [3](#endnote-3)\]. | Designa om rapporter med färre visuella objekt per sida. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Datauppsättningen är långsam, särskilt när rapporter har tidigare utfört bra

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Allt större mängder importera data.<br><br> Komplex eller ineffektiv beräkning logik, inklusive RLS-roller.<br><br> Modellen inte helt optimerad.<br><br> (DQ/LC) Svarstid för gateway.<br><br> Långsam DQ källa frågesvarstiderna. | Granska modellen Designer.<br><br> Övervaka gateway-prestandaräknare. | Se den [optimera modeller](#optimizing-models) i den här artikeln. |

#### <a name="high-concurrent-report-usage"></a>Hög samtidig rapportanvändning

| Möjliga förklaringar | Så här identifierar du | Så här löser du |
| --- | --- | --- |
| Stora frågearbetsbelastningar väntetider.<br><br> Processormättnad till.<br><br> DQ/LC anslutningsgräns har överskridits. | Övervaka CPU-användning \[ [4](#endnote-4)\], fråga väntetider och DQ/LC användning \[ [5](#endnote-5) \] mått + fråga varaktigheter. Om du växlar, ange samtidighet problem. | Skala upp kapaciteten eller tilldela innehållet till en annan kapacitet.<br><br> Designa om rapporter med färre visuella objekt per sida. |

**Kommentarer:**    
<a name="endnote-1"></a>\[1\] genomsnittlig minnesanvändning (GB) och högsta minnesförbrukning (GB).   
<a name="endnote-2"></a>\[2\] datauppsättning borttagna.   
<a name="endnote-3"></a>\[3\] datauppsättning frågor, datauppsättning medelvärde fråga varaktighet (ms), datauppsättning vänta antal och datauppsättningen Genomsnittlig väntetid (ms).   
<a name="endnote-4"></a>\[4\] CPU högt värde för användning och CPU-tid för största användning (senaste sju dagarna).   
<a name="endnote-5"></a>\[5\] DQ/LC högt värde för användning och DQ/LC tid för största användning (senaste sju dagarna).   

### <a name="why-are-reports-not-loading"></a>Varför läses rapporter inte in?

När det gick inte att läsa in rapporter, är det ett säkert tecken kapaciteten har inte tillräckligt med minne och är över värmas upp. Detta kan inträffa när alla inlästa modeller aktivt efterfrågas och därför inte kan tas bort och uppdateringsåtgärder har pausats eller fördröjts. Power BI-tjänsten kommer att försöka läsa in datauppsättningen i 30 sekunder och användaren meddelas smidigt om felet med ett förslag att försöka igen om en stund.

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

Även om det vanligtvis inte är en administrativ prioritet, se till att det finns tillräckligt med minne för att underlätta att datauppdateringar sker i tid. Detta kan innebära att isolera datauppsättningar till kapaciteter med kända tillräckliga resurser. Det är också möjligt att administratörer kan du prata med datauppsättningens ägare för att sprida ut eller minska schemalagda uppdateringstider för att minimera kollisioner. Observera att det inte är möjligt för en administratör att visa uppdatera kön eller hämta datauppsättningen scheman.

### <a name="why-are-refreshes-slow"></a>Varför är uppdateringarna långsamma?

Uppdateringar kan vara långsamma eller upplevas långsamma (som tidigare vanliga fråga tar upp).

När uppdateringen faktiskt är långsam, kan det vara av flera olika orsaker:

- Otillräcklig CPU (uppdatering kan vara mycket CPU-intensiva).
- Otillräckligt med minne, vilket resulterar i uppdatering pausar (som kräver uppdatering början när villkoren är tillräckliga för att upprepa).
- Icke-kapacitet orsaker, bland annat datasource systemets svarstid, nätverkssvarstid, ogiltiga behörigheter eller gateway, genomflöde.
- Datavolym - ett bra skäl att konfigurera inkrementell uppdatering, enligt beskrivningen nedan.

Kapacitetsadministratörer (och Power BI-tjänstadministratörer) kan övervaka måttet **Genomsnittlig uppdateringsvaraktighet (minuter)** för att fastställa benchmark för jämförelse över tid och måttet **Genomsnittlig uppdateringsväntetid (minuter)** för att fastställa genomsnittlig fördröjning mellan den schemalagda tiden och start för åtgärden.

Inkrementell uppdatering kan avsevärt minska varaktighet för uppdatering, särskilt för stora datamodellstabeller. Det finns fyra fördelar med inkrementell uppdatering:

- **Uppdateringar är snabbare** – endast en del av en tabell måste inläsning, för att minska CPU och minnesanvändning och parallellitet kan vara högre när du uppdaterar flera partitioner.
- **Uppdateringar sker bara vid behov** -inkrementella uppdateringsprinciper kan konfigureras för att läsa in bara när data har ändrats.
- **Uppdateringar som är mer tillförlitliga** -kortare körs anslutningar till föränderliga datasource-system är mindre känsliga för frånkoppling.
- **Modeller förblir trim** -inkrementella uppdateringsprinciper kan konfigureras för att automatiskt ta bort historik utöver en glidande tidsperiod.

Mer information finns i [inkrementell uppdatering i Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Varför slutförs inte datauppdateringar?

När datauppdateringen påbörjas men inte kan slutföras, kan det finnas flera olika orsaker:

- Otillräckligt med minne, även om det finns endast en modell i Premium-kapacitet, dvs. modellen storleken är mycket stora.
- Icke-kapacitet orsaker, bland annat frånkoppling av datasource-system, ogiltig behörighet eller gateway-fel.

Kapacitetsadministratörer (och Power BI-tjänstadministratörer) kan övervaka måttet **Uppdateringsfel på grund av minnesbrist**.

## <a name="optimizing-models"></a>Optimera modeller

Optimal modelldesign är avgörande för att leverera en effektiv och skalbar lösning. Det är dock utanför omfattningen för den här artikeln om du vill ange en fullständig beskrivning. I stället innehåller det här avsnittet viktiga områden att överväga när du optimerar modeller.

### <a name="optimizing-power-bi-hosted-models"></a>Optimera Power BI finns modeller

Optimera modeller som finns i en Premium-kapacitet kan ske på plattformsnivå datakällorna och modellen.

Överväg optimeringsmöjligheterna för en importmodell:

![Optimeringsmöjligheterna för en importmodell](media/service-premium-capacity-optimize/import-model-optimizations.png)

På datasource-nivå:

- Relationsdatakällor kan optimeras för att säkerställa att den snabbaste möjliga uppdateringen av förväg integrerande data, tillämpa rätt index, definiera tabellpartitioner som passar för inkrementell uppdatering perioder och materialisering av beräkningar (i stället för beräknas modellera tabeller och kolumner) eller lägga till logik för beräkning i vyer.
- Icke-relationella datakällor kan vara förintegrerade med relationella butiker.
- Kontrollera att gatewayer har tillräckligt med resurser, helst på dedikerade virtuella datorer, med tillräckligt med nätverksbandbredd och i närheten till datakällor.

På modellnivå:

- Power Query-frågeutformningar kan minimera eller ta bort komplexa omvandlingar och särskilt de som slår ihop olika datakällor (informationslager uppnår detta under steget extrahering-transformering-inläsning). Dessutom att säkerställa att lämpliga datasource sekretessnivåer anges, detta kan undvika att Power BI för att läsa in alla resultat för att skapa ett kombinerade resultat för frågor.
- Modellstrukturen identifierar data som ska läsas in och har direkt inverkan på modellstorleken. Den kan utformas till att undvika att onödiga data läses in genom att ta bort kolumner, ta bort rader (särskilt historiska data) eller genom att läsa in sammanfattningsdata (på bekostnad av inläsning av detaljerade data). Dramatisk storleksminskning kan uppnås genom att ta bort kolumner med hög kardinalitet (särskilt textkolumner) som inte lagrar eller komprimerar särskilt effektivt.
- Modellfrågeprestanda kan förbättras genom att konfigurera relationer med enkelriktning om det inte finns en bra anledning till att tillåta dubbelriktad filtrering. Bör du också använda den [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) funktionen i stället för dubbelriktad filtrering.
- Aggregeringstabeller kan uppnå snabba frågesvar genom att läsa i förväg sammanfattade data, men det här ökar storleken på modellen och leder till längre uppdateringstider. I allmänhet ska aggregeringstabeller reserveras för mycket stora modeller eller sammansatta modellutformningar.
- Beräknade tabeller och kolumner ökar storleken på modellen och resulterar i längre uppdateringstider. I allmänhet kan en mindre lagringsstorlek och snabbare Uppdateringstid ske när data är materialiserad eller beräknas i datakällan. Om detta inte är möjligt kan användning av Power Query-anpassade kolumner erbjuda förbättrad lagringskomprimering.
- Det kan finnas möjlighet att finjustera DAX-uttryck för mått och RLS-regler, kanske skriva om logik för att undvika dyra formler
- Inkrementell uppdatering kan avsevärt minska uppdateringstiden och spara minne och processor. Inkrementell uppdatering kan också konfigureras för att ta bort historiska data för att hålla modellstorlekar i trim.
- En modell kan göras om till två modeller när det finns olika och motstridiga frågemönster. Till exempel har vissa rapporter höga nivåer av aggregeringar över all historik och kan tolerera 24 timmars svarstid. Andra rapporter gäller för dagens data och behöver detaljerad åtkomst till enskilda transaktioner. Skapa hellre två modeller som är optimerade för alla behov i stället för att utforma en enda modell som ska räcka åt alla rapporter.

Överväg optimeringsmöjligheterna för en DirectQuery-modell. När modellen utfärdar frågebegäranden till den underliggande datakällan, är datasource optimering viktigt att leverera dynamiskt modellen frågor.

 ![Optimeringsmöjligheterna för en DirectQuery-modell](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

På datasource-nivå:

- Datakällan kan optimeras för att säkerställa den snabbaste möjliga frågor genom att integrera förväg data (som inte är möjligt på modell-nivå), tillämpa rätt index, definiera tabellpartitioner materialisering sammanfattade data (med indexerade vyer), och minimera mängden beräkning. Den bästa upplevelsen uppnås när direktfrågor behöver bara filtrerar och utföra inre kopplingar mellan indexerade tabeller eller vyer.
- Kontrollera att gatewayer har tillräckligt med resurser, helst på dedikerade virtuella datorer, med tillräckligt med nätverksbandbredd och i närheten till datakällan.

På modellnivå:

- Power Query-fråga Designer ska helst tillämpas inga omvandlingar - annars försöker hålla transformeringar som ett absolut minsta.
- Modellfrågeprestanda kan förbättras genom att konfigurera relationer med enkelriktning om det inte finns en bra anledning till att tillåta dubbelriktad filtrering. Dessutom modeller av relationer ska konfigureras för att anta referensintegritet används (när så är fallet) och leder datasource-frågor med effektivare inre kopplingar (i stället för yttre kopplingar).
- Undvik att skapa anpassade kolumner i Power Query-fråga eller modell beräknad kolumn – Materialisera dessa i datakällan, när det är möjligt.
- Det kan finnas möjlighet att finjustera DAX-uttryck för mått och RLS-regler, kanske skriva om logik för att undvika dyra formler.

Överväg optimeringsmöjligheterna för en sammansatt modell. Kom ihåg att en sammansatt modell möjliggör en blandning av import- och DirectQuery-tabeller.

![Optimeringsmöjligheter för en sammansatt modell](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- I allmänhet gäller optimering för Import och DirectQuery-modeller sammansatta datamodellstabeller som använder dessa lägen för lagring.
- Normalt ska du sträva efter att uppnå en belastningsutjämnade design genom att konfigurera tabeller av dimensionstyp (som representerar affärsentiteter) som dubbelt lagringsläge och tabeller av faktatyp (ofta stora tabeller som representerar operativa fakta) som DirectQuery-lagringsläge. Dubbel lagringsläge innebär att både importera och DirectQuery-lägena för lagring och detta gör att Power BI-tjänsten att fastställa det mest effektiva lagringsläget att använda när du genererar en intern fråga för direktautentisering.
- Se till att gatewayer har tillräckligt med resurser, helst på dedikerade virtuella datorer, med tillräckligt med nätverksbandbredd och närheten till datakällor
- Aggregeringstabeller konfigurerade som importlagringsläge kan leverera dramatiska förbättringar i frågeprestanda när de används för att sammanfatta tabeller av faktatyp för DirectQuery-lagringsläge. I det här fallet ökar aggregeringstabeller storleken på modellen och ökar uppdateringstiden, och det här är ofta en acceptabel kompromiss för snabbare frågor.

### <a name="optimizing-externally-hosted-models"></a>Optimera externt värdbaserad modeller

Många optimeringsmöjligheter som beskrivs i den [optimera Power BI finns modeller](#optimizing-power-bi-hosted-models) gäller även för modeller som utvecklats med Azure Analysis Services och SQL Server Analysis Services. Klara undantag är vissa funktioner som för närvarande inte stöds, inklusive sammansatta modeller och aggregeringstabeller.

Ytterligare ett övervägande för externt värdbaserade datauppsättningar är den databas som är värd i förhållande till Power BI-tjänsten. För Azure Analysis Services innebär det att skapa Azure-resursen i samma region som Power BI-klienten (hemregion). För SQL Server Analysis Services, för IaaS, innebär detta värdskap för den virtuella datorn i samma region, och för lokala datorer innebär det att säkerställa en effektiv gateway-installation.

Det kan vara av intresse att observera att Azure Analysis Services-databaser och SQL Server Analysis Services-tabelldatabaser kräver att deras modeller fullständigt läses in i minnet och att de förblir där hela tiden som stöd för frågor. Precis som för Power BI-tjänsten måste det finnas tillräckligt med minne för att uppdatera om modellen måste vara online under uppdateringen. Till skillnad från Power BI-tjänsten finns det inget koncept för att modeller automatiskt föråldras in och ut ur minnet enligt användning. Power BI Premium, erbjuder därför en mer effektiv metod för att maximera modellfrågor med lägre minnesanvändning.

## <a name="capacity-planning"></a>Kapacitetsplanering

Storleken på en Premium-kapacitet anger dess tillgängliga minne och processorresurser och begränsningar som har införts på kapaciteten. Antal Premium-kapaciteter är också något att överväga, eftersom man genom att skapa flera Premium-kapaciteter kan hjälpa till att isolera arbetsbelastningar från varandra. Observera att lagringen är 100 TB per kapacitetsnod och det är troligen mer än tillräckligt för alla arbetsbelastningar.

Att fastställa storleken på och antalet Premium-kapaciteter kan vara en utmaning, särskilt för den inledande kapaciteten som du skapar. Det första steget vid fastställande av kapacitetsstorlek är att förstå genomsnittlig arbetsbelastning som representerar förväntad daglig användning. Det är viktigt att förstå att inte alla arbetsbelastningar är lika. I ena änden av spektrumet kan t.ex. 100 samtidiga användare med åtkomst till en enda rapportsida som innehåller ett enda visuellt objekt enkelt uppnås. Men i den andra änden av spektrumet kommer 100 samtidiga användare med åtkomst till 100 olika rapporter, var och en med 100 visuella objekt på rapportsidan, att ha mycket olika krav på resurskapacitet.

Kapacitetsadministratörer behöver därför inte tänka på många faktorer specifika för miljö, innehåll och förväntad användning. Det övergripande målet är att maximera kapacitetsanvändning samtidigt som konsekventa frågetider, godkända väntetider och borttagningsintervall levereras. Faktorer att överväga kan innefatta:

- **Modellera egenskaper storlek och data** -Imortmodeller... fullständigt måste läsas in i minnet för att tillåta förfrågningar till eller uppdateras. LC-/DQ-datauppsättningar kan kräva betydande processortid och eventuellt betydande minne för att utvärdera komplexa åtgärder eller RLS-regler. Minne- och processorstorlek och LC-/DQ-frågedataflöde är begränsat av kapacitetsstorleken.
- **Samtidiga active modeller** -olika imortmodeller... samtidiga frågor efter att leverera bästa svarstider och prestanda när de finns kvar i minnet. Det bör finnas tillräckligt med minne för att vara värd för alla mycket frågade modeller, med ytterligare minne för att möjliggöra deras uppdateringar.
- **Importera modelluppdatering** -uppdateringstyp (fullständig eller inkrementell), varaktighet och komplexiteten i Power Query-frågor och beräknade tabellkolumn logik kan påverka minne och särskilt processoranvändning. Samtidiga uppdateringar är begränsade av kapacitetsstorlek (1,5 x serverdelens v-kärnor, avrundas uppåt).
- **Samtidiga frågor** – många samtidiga frågor kan resultera i svarar inte rapporterna när du processor- eller LC/DQ anslutningar överskrider kapacitetsgränsen. Detta gäller särskilt för rapportsidor som innehåller många visuella objekt.
- **Dataflöden och sidnumrerade rapporter** -kapaciteten kan konfigureras för att stödja dataflöden och sidnumrerade rapporter med var och en kräver ett konfigurerbart hur stor procentandel av kapacitet. Minne allokeras dynamiskt till dataflöden, men tilldelas statiskt sidnumrerade rapporter.

Förutom de här faktorerna kan kapacitetsadministratörer överväga att skapa flera kapaciteter. Flera kapaciteter möjliggör isolering av arbetsbelastningar och kan konfigureras för att säkerställa att prioritetsarbetsbelastningar har garanterade resurser. Till exempel kan två kapaciteter skapas för att avgränsa affärskritiska arbetsbelastningar från självbetjänade BI (SSBI) arbetsbelastningar. Affärskritisk kapacitet kan användas för att isolera stora företagsmodeller vilket ger dem garanterade resurser med redigeringsåtkomst beviljad endast till IT-avdelningen. SSBI-kapaciteten kan användas som värd för ett växande antal mindre modeller med åtkomst beviljad till affärsanalytiker. SSBI-kapaciteten kan ibland uppleva väntetider för frågor eller uppdateringar som är acceptabla.

Framöver kan kapacitetsadministratörer balansera arbetsytor i kapaciteter genom att flytta innehåll mellan arbetsytor eller arbetsytor mellan kapaciteter, och genom att skala upp eller ner kapaciteter. I allmänhet till värden större modeller du skala upp och högre samtidighet kan du skala ut.

Kom ihåg att köpa en licens som ger klienten v-kärnor. Köp av en **P3**-prenumeration kan användas för att skapa en eller upp till fyra Premium-kapaciteter, d.v.s. 1 x P3 eller 2 x P2 eller 4 x P1. Dessutom före uppskalning av en P2-kapacitet till en P3-kapacitet kan hänsyn tas till uppdelningen av v-kärnor för att skapa två P1-kapaciteter.

## <a name="testing-approaches"></a>Testa metoder

När en kapacitetsstorlek avgörs kan testning utföras genom att skapa en kontrollerad miljö. Ett praktiskt och ekonomiskt alternativ är att skapa en Azure-kapacitet (A SKU:er), notera att en P1-kapacitet har samma storlek som en A4-kapacitet, och P2- och P3-kapaciteter har samma storlek som A5- och A6-kapaciteten respektive. Azure-funktionerna kan skapas snabbt och debiteras per timme. Så när testningen är klar, kan de enkelt tas bort om du vill sluta ha kostnader.

Testinnehållet kan läggas till arbetsytor som skapats på Azure-kapacitet och sedan kan en enskild användare köra rapporter för att generera en realistisk och representativ arbetsbelastning för frågor. Om det finns importmodeller, ska en uppdatering för varje modell också utföras. Övervakningsverktyg kan sedan användas för att granska alla mått för att förstå resursanvändning.

Det är viktigt att testerna är repeterbara. Testerna ska köras flera gånger och de ska leverera ungefär samma resultat varje gång. Ett medeltal av de här resultaten kan användas för att extrapolera och beräkna en arbetsbelastning under sanna produktionsvillkor.

För att generera ett belastningstest, överväg att utveckla ett belastningstestprogram för att simulera en realistisk arbetsbelastning. Information om hur du gör det ligger utanför omfånget för den här artikeln. Ytterligare information, inklusive ett kodexempel, referera till den [läsa in testning Power BI-program med Visual Studio belastningstest](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webbseminarium.

## <a name="acknowledgements"></a>Bekräftelser

Den här artikeln är skriven av Peter Myers, Data Platform MVP och oberoende BI-expert med [bitvis lösningar](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Scenarier för Premium-kapacitet](service-premium-capacity-scenarios.md)   
  
Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

||||||