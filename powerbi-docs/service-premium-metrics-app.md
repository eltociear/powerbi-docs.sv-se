---
title: Måttappen för Power BI Premium
description: Lär dig hur du använder måttappen i Power BI Premium för att hantera och felsöka Premium-kapaciteten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/06/2020
LocalizationGroup: Premium
ms.openlocfilehash: c15576ac6ab9b20a3492341c05d2f9d8eb42e107
ms.sourcegitcommit: 2b93c1cc29aaf199ab7441a04c8e5ae49ffca5d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80813062"
---
# <a name="power-bi-premium-metrics-app"></a>Måttappen för Power BI Premium

Du kan använda **Power BI Premium-måttappen** för att hantera hälsan och kapaciteten för din Power BI Premium-prenumeration. Med appen använder administratörer appens **Hälsocenter för kapacitet** för att se och hantera indikatorer som övervakar hälsan för Premium-kapaciteten. Måttappen består av landningssidan, som heter **Hälsocenter för kapacitet** och information om tre viktiga mått:

* Aktivt minne
* Fråga väntar
* Uppdateringen väntar

![Måttappen för Power BI Premium](media/service-premium-metrics-app/premium-metrics-app-00.png)

I följande avsnitt beskrivs landningssidan och de tre måttrapportsidorna i detalj. 

> [!IMPORTANT]
> Om din Power BI Premium-kapacitet har hög resursanvändning, som medför prestanda- och tillförlitlighetsproblem, kan du få e-postmeddelanden för att identifiera och lösa problemet. Mer information finns i [meddelanden om kapacitet och tillförlitlighet](service-interruption-notifications.md#capacity-and-reliability-notifications).

## <a name="premium-capacity-health-center"></a>Hälsocenter för Premiumkapacitet

När du öppnar **Power BI Premium-måttappen** visas **Hälsocenter för kapacitet** som ger en översikt över hälsan hos din Power BI Premium-kapacitet.

![Hälsocenter för kapacitet i Premium-måttappen](media/service-premium-metrics-app/premium-metrics-app-01.png)

Från landningssidan kan du välja den Power BI Premium-kapacitet som du vill visa om din organisation har flera Premium-prenumerationer. Om du vill visa en Premium-kapacitet markerar du listrutan längst upp på sidan med namnet **Välj en kapacitet för att se dess mått**.

De tre KPI:erna visar det aktuella hälsotillståndet för den valda Premium-kapaciteten, baserat på de inställningar som tillämpas på var och en av de tre KPI:erna. 

Om du vill visa information om varje KPI väljer du knappen **Utforska** längst ned i varje KPI:s visuella objekt och dess informationssida visas. I följande avsnitt beskrivs varje KPI och den information som sidan innehåller.

## <a name="the-active-memory-metric"></a>Måttet aktivt minne

Måttet **Aktivt minne** är en del av *kapacitetsplanerings*kategorin, som är en godkänd hälsoindikator för att utvärdera kapacitetens resursanvändning för användning, så att du kan justera kapaciteten efter behov för att planera kapacitetens skalning. 

![KPI:et aktivt minne](media/service-premium-metrics-app/premium-metrics-app-02.png)

**Aktivt minne** är det minne som används för att bearbeta datauppsättningar som för närvarande används och som därför inte tas bort när minnet behövs. Det aktiva minnesmåttet anger om din kapacitet kan hantera ytterligare belastning, eller redan är nära eller över sin kapacitet, kapacitetens aktuella belastning. Det aktiva minnet som används för närvarande innebär att mindre minne är tillgängligt för att stödja ytterligare uppdateringar och frågor. 

KPI:et för **aktivt minne** mäter hur många gånger kapacitetens aktiva minne har överskridit tröskelvärdet på 70 % 50 gånger (markören har angetts till 30 % av de senaste sju dagarna), vilket betyder att kapaciteten närmar sig en punkt då användarna kan börja uppleva prestandaproblem med frågor.

Den mätare som visas i det här avsnittet visar att under de senaste sju dagarna från den tidpunkt då rapporten senast uppdaterades har kapaciteten överskridit tröskelvärdet på 70 % fyra gånger, delat med varje timbucket. Det högsta värdet för mätaren, 168, motsvarar de senaste sju dagarna, i timmar.

Om du vill lära dig mer om KPI:et för aktivt minne klickar du på knappen **Utforska** för att se en rapportsida som tillhandahåller särskilda visualiseringar av detaljerade mått, tillsammans med en felsökningsguide i den högra kolumnen på sidan. 

Det finns två scenarier, som du kan visa på rapportsidan genom att välja **scenario 1** eller **scenario 2** på sidan. 

![Informationssidan för aktivt minne](media/service-premium-metrics-app/premium-metrics-app-03.png)

Felsökningsguiderna, som är associerade med varje scenario, ger detaljerade förklaringar om vad måtten betyder, så att du bättre kan förstå kapacitetens status och vad som kan göras för att åtgärda eventuella problem. 

De två scenarierna beskrivs i följande avsnitt.

### <a name="scenario-one---current-load-is-too-high"></a>Scenariot ett – den aktuella belastningen är för hög 

För att avgöra om det finns tillräckligt med minne för att slutföra arbetsbelastningarna, se det första visuella objektet på sidan: **A: Förbrukade minnesprocent**, vilket visar det minne som används av datauppsättningar som bearbetas aktivt och därför inte kan avlägsnas.

Larmtröskelvärdet, som är den röda streckade linjen, markerar incidenter med 90 % minnesanvändning.

Varningströskelvärdet, som är den gula streckade linjen, markerar incidenter med 70 % minnesanvändning. 

Den svarta streckade linjen indikerar minnesanvändningstrendlinjen, baserat på den aktuella kapacitetens minnesanvändning under diagrammets tidslinje.

Höga förekomster av aktivt minne över larmtröskeln (röd streckad linje) och minnestrendlinjen (svart prickad linje) indikerar minneskapacitetstrycket, vilket kan hindra ytterligare datauppsättningar från att läsas in i minnet under den tiden. 

När du ser sådana fall bör du titta noggrant på de andra diagrammen på sidan för att bättre fastställa vilket och varför så mycket minne ofta används och hur du ska belastningsutjämna eller optimera, eller om det behövs, skala upp kapaciteten. 

Det andra visuella objektet på sidan, **B: Inaktiverade aktiva datauppsättningar i timmar** visar antalet datauppsättningar som har lästs in i minnet, i timbuckets. 

Det tredje visuella objektet, **C: Varför data uppsättningar finns i minnet** är en tabell med en lista över datauppsättningen efter arbetsytans namn, datauppsättningens namn, datauppsättningarnas okomprimerade storlek i minnet, förklaring av orsaken till att den läses in i minnet (till exempel, den uppdateras eller efterfrågas eller båda).

#### <a name="diagnosing-scenario-one"></a>Diagnostisera scenario ett

Konsekvent hög aktiv minnesanvändning kan leda till tvingande datauppsättningar som aktivt används för att avlägsnas eller kan förhindra att nya datauppsättningar kan läsas in. Följande steg kan hjälpa dig att diagnostisera problem

1. Titta på diagrammet *A: Procent förbrukat minne*

    **a.** Om diagram A visar att larmtröskeln (90 %) överskrids många gånger och/eller flera timmar i följd, så har din kapacitet ont om minne för ofta. I diagrammet nedan kan vi se att varningströskelvärdet (70 %) överskreds fyra gånger.

    ![Diagram a, procent förbrukat minne](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** Diagrammet med rubriken *B: Inlästa datauppsättningar per timme* visar det maximala antalet unika data uppsättningar som lästs in i minnet efter timbuckets. Om du markerar ett fält i det visuella objektet filtreras orsakerna till att datauppsättningarna är i minnesvisualiseringen.  

    ![Diagram b, förbrukat minne per timme](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** Se tabellen **Varför data uppsättningar finns i minnet** för att se en lista över datauppsättningar som lästs in i minnet. Sortera efter *datauppsättningens storlek (MB)* för att markera datauppsättningarna som tar upp mest minne. Kapacitetsåtgärder klassificeras som antingen *interaktiva* eller *bakgrund*. Interaktiva åtgärder omfattar renderingsbegäranden och svarar på användarinteraktioner (filtrering, frågor och svar frågor, o.s.v.). Totalt antal frågor och totala uppdateringar ger en uppfattning om huruvida det finns interaktiva (frågor) tunga eller bakgrundsåtgärder (uppdateringar) som utförs på datauppsättningen. Det är viktigt att förstå att interaktiva åtgärder alltid prioriteras över bakgrundsåtgärder för att ge bästa möjliga användarupplevelse. Om det inte finns tillräckligt med resurser, läggs bakgrundsåtgärder till i en kö för bearbetning när resurser frigörs. Bakgrundsåtgärder, som uppdateringar av datauppsättningen och AI-funktioner, kan stoppas mitt i process av Power BI-tjänsten och läggs till i en kö.
    
    ![tabell c, lista över datauppsättningar](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Lösningar för scenario ett

Du kan utföra följande steg för att åtgärda de problem som är kopplade till scenario ett:

1. **Skala upp kapaciteten** – om du skalar upp kapaciteten till nästa SKU blir dubbelt så mycket minne tillgängligt som med den aktuella SKU:n, vilket minskar minnesbelastningen som kapaciteten.

2. **Flytta datauppsättningar till en annan kapacitet** – om du har en annan kapacitet som har mer tillgängligt minne kan du flytta arbetsytorna som innehåller de större datauppsättningarna till den kapaciteten.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Scenario två – framtida belastning kommer att överskrida gränserna

För att avgöra om det finns tillräckligt med minne för att slutföra arbetsbelastningarna, se det **A: Förbrukade minnesprocent**, som visas överst på sidan, visar det minne som används av datauppsättningar som bearbetas aktivt och därför inte kan avlägsnas. Den svarta streckade linjen visar trender. I en kapacitet som upplever minnesbelastning visar samma visuella objekt tydligt aktivt minne som trendlinje (svart streckad linje), vilket innebär att det inte går att läsa in ytterligare datauppsättningar i minnet vid den här tidpunkten. Trendlinjen, den svarta streckade linjen, visar trenden för tillväxt baserat på de sju dagarnas data. 

![Informationssidan för aktivt minne](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnostisera scenario två

Om du vill diagnostisera scenario två kontrollerar du om trendlinjen visar en uppåtgående trend för varnings- eller larmtröskelvärden. 

1. Titta på **diagram A:**

    ![Diagram över förbrukat minne](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Om diagrammet visar en uppåtgående lutning betyder det att minnesförbrukningen har ökat under de senaste sju dagarna.

    **b.** Bedöm den aktuella tillväxten och förutsäg när trendlinjen kommer att korsa varningströskelvärdet (den gula streckade linjen).

    **c.** Fortsätt att kontrollera trendlinjen minst varannan dag för att se om trenden fortsätter.

#### <a name="remedies-for-scenario-two"></a>Lösningar för scenario två

Du kan utföra följande steg för att åtgärda de problem som är kopplade till scenario två:

1. **Skala upp kapaciteten** – om du skalar upp kapaciteten till nästa SKU blir dubbelt så mycket minne tillgängligt som med den aktuella SKU:n, vilket minskar minnesbelastningen som för närvarande berör kapaciteten.

2. **Flytta datauppsättningar till en annan kapacitet** – om du har en annan kapacitet som har mer tillgängligt minne kan du flytta arbetsytorna som innehåller de större datauppsättningarna till den kapaciteten.


## <a name="the-query-waits-metric"></a>Frågan inväntar mått

Kategorin **Frågor** anger om användare kan uppleva rapportvisualiseringar som svarar långsamt eller som slutar svara. **Frågan väntar** är den tid som frågan tar för att starta körningen från den tidpunkt då den utlöstes. Detta KPI mäter om 25 % eller fler av de valda kapacitetsfrågorna väntar 100 millisekunder eller längre på att köras. Frågan väntar när det inte finns tillräckligt med ledigt CPU för att köra alla väntande frågor. 

![Mätaren frågan väntar](media/service-premium-metrics-app/premium-metrics-app-09.png)

Mätaren i det här visuella objektet visar att under de senaste sju dagarna från den tidpunkt då rapporten senast uppdaterades väntade 17,32 % av frågorna i mer än 100 millisekunder. 

Om du vill veta mer om KPI:et Frågan väntar klickar du på knappen **Utforska** för att visa en rapportsida med visualisering av relevanta mått och en felsökningsguide i den högra kolumnen på sidan. Felsökningsguiden har två scenarier, som ger detaljerade förklaringar av måttet, status för kapaciteten och vad du kan göra för att åtgärda problemet.

Vi diskuterar varje scenario där frågan väntar i tur och följd i följande avsnitt.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Scenario ett – långvariga frågor förbrukar CPU

I scenario ett använder långvariga frågor för mycket CPU. 

Du kan undersöka om dålig rapportprestanda orsakas av en överbelastad kapacitet eller på grund av en dåligt utformad datauppsättning eller rapport. Det finns flera orsaker till varför en fråga kan köras under en längre period, vilket definieras som att ta mer än 10 sekunder att slutföra körningen. Datauppsättningens storlek och komplexitet, samt frågans komplexitet är bara några exempel på vad som kan orsaka en tidskrävande fråga. 

På rapportsidan visas följande visuella objekt: 

* Den översta tabellen med namnet **A: Höga väntetider** visar datauppsättningarna med väntande frågor. 
* **B: Tidsfördelningar för varje timme med högväntetid** visar fördelningen av höga väntetider. 
* Diagrammet med rubriken **C: Antal långvariga frågor per timme** visar antalet tidskrävande frågor som har körts delat med varje timbucket.
* Det sista visuella objektet, tabell **D: Långvariga frågor**, listar tidskrävande frågor och deras statistik.

![Sidan med detaljerad information om väntande frågor](media/service-premium-metrics-app/premium-metrics-app-10.png)

Det finns åtgärder som du kan vidta för att diagnostisera och åtgärda problem med svarstider för frågor. Dessa beskrivs härnäst.

#### <a name="diagnosing-scenario-one"></a>Diagnostisera scenario ett

Först kan du avgöra om tidskrävande frågor inträffar när dina frågor väntar. 

![Tabell med hög väntetid](media/service-premium-metrics-app/premium-metrics-app-11.png)

Titta på **diagram B**, som visar antalet frågor som väntar mer än 100 ms. Välj en av kolumnerna som visar ett stort antal väntande frågor.

![Hög väntetidsfördelning](media/service-premium-metrics-app/premium-metrics-app-12.png)

När du klickar på en kolumn med lång väntetid filtreras **diagram C** för att visa antalet långvariga frågor som körs under den tiden, vilket visas i följande bild:

![Antal långvariga frågor per timme](media/service-premium-metrics-app/premium-metrics-app-13.png)

Dessutom har **diagram D** också filtrerats för att visa de frågor som har varit tidskrävande under den valda tidsperioden.

![Långvariga frågor](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Lösningar för scenario ett

Här följer några åtgärder som du kan vidta för att åtgärda problem med scenariot:

1. **Kör PerfAnalyzer för att optimera rapporter och data uppsättningar** – prestandaanalysverktyget för rapporter visar resultatet av alla interaktioner på en sida, inklusive hur lång tid varje visuellt objekt tar att uppdatera och var tidsförbrukningen sker.

2. **Skala upp kapaciteten** – skalning av kapaciteten till nästa SKU ger dubbelt så mycket CPU vilket lättar på CPU-trycket som kan vara orsaken till att frågorna tar längre tid.

3. **Flytta datauppsättningar till en annan kapacitet** – om du har en annan kapacitet som har mer tillgängligt minne kan du flytta arbetsytorna som innehåller de större datauppsättningarna till den kapaciteten.

### <a name="scenario-two---too-many-queries"></a>Scenario två – för många frågor

För många frågor körs i scenario två.

När antalet frågor överskrider gränserna för kapaciteten placeras frågorna i en kö tills resurserna är tillgängliga för att köra dem. Om storleken på kön blir för stor kan frågorna i kön vänta upp till 100 millisekunder.

![Scenario två](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnostisera scenario två

Från **tabell A** väljer du en datauppsättning som har en hög procentandel väntetid.

![tabell med hög väntetid](media/service-premium-metrics-app/premium-metrics-app-16.png)

När du har valt en datauppsättning med hög väntetid filtreras **diagram B** för att visa väntetidsfördelningar för frågor på den datauppsättningen under de senaste sju dagarna. Välj sedan en av kolumnerna från **diagram B**.

![fördelningsdiagram för hög väntetid per timme](media/service-premium-metrics-app/premium-metrics-app-17.png)

**Diagram C** filtreras sedan för att visa kölängden vid den tidpunkt som valts från diagram B.

![längd på frågekö per timme](media/service-premium-metrics-app/premium-metrics-app-18.png)

Om köns längd har överskridit tröskelvärdet 20 är det troligt att frågorna i den valda datauppsättningen fördröjs på grund av att för många frågor försöker köras samtidigt.

![Tabell för frågekörningar](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Lösningar för scenario två

Du kan utföra följande steg för att åtgärda de problem som är kopplade till scenario två:

1. **Skala upp kapaciteten** – om du skalar upp kapaciteten till nästa SKU blir dubbelt så mycket minne tillgängligt som med den aktuella SKU:n, vilket minskar minnesbelastningen som för närvarande berör kapaciteten.

2. **Flytta datauppsättningar till en annan kapacitet** – om du har en annan kapacitet som har mer tillgängligt minne kan du flytta arbetsytorna som innehåller de större datauppsättningarna till den kapaciteten.


## <a name="the-refresh-waits-metric"></a>Måttet uppdatering väntar

Måttet **Uppdatering väntar** ger insikter om när användare kan rapportera data som är gamla eller inaktuella. **Uppdatering väntar** är den tid som en datauppdatering väntar på att starta körningen, från den tidpunkt då den utlöstes på begäran eller schemalades för körning. Detta KPI mäter om 10 % eller fler väntande uppdateringsbegäranden väntar 10 minuter eller längre. Väntetider inträffar vanligt vis när det inte finns tillräckligt med ledigt minne eller CPU.

![Mätaren uppdatering väntar](media/service-premium-metrics-app/premium-metrics-app-20.png)

Den här mätaren visar att 3,18 % av uppdateringarna väntade i över 10 minuter under de senaste sju dagarna. 

Om du vill veta mer om KPI:et **Uppdatering väntar** klickar du på knappen **Utforska** som visar en sida med mått och en felsökningsguide i den högra kolumnen på rapportsidan. Guiden innehåller detaljerade förklaringar om måtten på sidan och hjälper dig att förstå kapacitetens status och vad du kan göra för att undvika eventuella problem.

![Utforska måttet uppdatering väntar](media/service-premium-metrics-app/premium-metrics-app-21.png)

Det finns två förklarade scenarier som du kan visa på rapportsidan genom att välja scenario 1 eller scenario 2 på sidan. Vi diskuterar varje scenario i tur och följd i följande avsnitt.

### <a name="scenario-one---not-enough-memory"></a>Scenariot ett – inte tillräckligt med minne

I scenario ett finns det inte tillräckligt med minne för att läsa in datauppsättningen. Det finns två situationer som leder till att en uppdatering begränsas under förhållanden med lågt minne:

1. Det finns inte tillräckligt med minne för att läsa in datauppsättningen.
2. Uppdateringen avbröts på grund av en åtgärd med högre prioritet. 

Prioriteten för att läsa in datauppsättningar är följande:

1. Interaktiv fråga
2. Rapport på begäran
3. Schemalagd uppdatering

Om det inte finns tillräckligt med minne för att läsa in en datauppsättning för en interaktiv fråga stoppas schemalagda uppdateringar och deras datauppsättningar tas bort från minnet tills tillräckligt med minne blir tillgängligt. Om det inte frigör tillräckligt med minne stoppas uppdateringar på begäran och deras datauppsättningar inaktiveras.

#### <a name="diagnosing-scenario-one"></a>Diagnostisera scenario ett

För att diagnostisera scenario ett bör du först avgöra om begränsningen beror på otillräckligt minne. Gör följande.

1.    Välj den datauppsättning som du är intresserad av från **tabell A** genom att klicka på den: 

    ![Tabell A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. När en datauppsättning har valts i **tabell A** filtreras **diagram B** så att väntetiden visas.

    ![Diagram B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. **Diagram C** filtreras sedan för att visa eventuella begränsningar som förklaras i nästa steg. 

2. Titta på resultaten i det nu filtrerade **diagrammet C**. Om diagrammet visar begränsningar på grund av minnesbrist vid den tidpunkt då datauppsättningen väntade, väntade datauppsättningen på grund av lågt minne.

    ![Diagram C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Slutligen kontrollerar du **diagram D** som visar vilka typer av uppdateringar som har inträffat, schemalagt jämfört med på begäran. Eventuella uppdateringar som inträffar på begäran kan vara orsaken till begränsningen.

    ![Diagram D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Lösningar för scenario ett

Du kan utföra följande steg för att åtgärda de problem som är kopplade till scenario ett:

1. **Skala upp kapaciteten** – om du skalar upp kapaciteten till nästa SKU blir dubbelt så mycket minne tillgängligt som med den aktuella SKU:n, vilket minskar CPU- och minnesbelastningen som för närvarande berör kapaciteten.

2. **Flytta datauppsättningar till en annan kapacitet** – om väntetiden beror på minnesbelastning och du har en annan kapacitet som har mer tillgängligt minne kan du flytta arbetsytorna som innehåller de större datauppsättningarna till den kapaciteten.

3. **Sprida ut schemalagda uppdateringar** – om du sprider ut uppdateringarna undviker du att för många uppdateringar försöker köra samtidigt.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Scenario 2 – inte tillräckligt med CPU för uppdatering

I scenario två finns det inte tillräckligt med ledigt CPU för att genomföra uppdateringen. 

För dedikerade kapaciteter begränsar Power BI antalet uppdateringar som kan ske samtidigt. Det här antalet är lika med antalet serverdelskärnor x 1,5. Till exempel kan en dedikerad P1-kapacitet som har fyra serverdelskärnor köra 6 uppdateringar samtidigt. När det maximala antalet samtidiga uppdateringar har nåtts väntar andra uppdateringar tills en pågående uppdatering har slutförts.

![Scenario två för uppdatering](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnostisera scenario två

För att diagnostisera scenario två bör du först avgöra om begränsningen beror på att den maximala samtidigheten för uppdateringar körs. Gör följande.

1.    Välj den datauppsättning som du är intresserad av från **tabell A** genom att klicka på den: 

    ![Tabell A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. När en datauppsättning har valts i **tabell A** filtreras **diagram B** så att väntetiden visas.

    ![Diagram B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. **Diagram C** filtreras sedan för att visa eventuella begränsningar som förklaras i nästa steg. 

2. Titta på resultaten i det nu filtrerade **diagrammet C**. Om diagrammet visar *maximal samtidighet* vid den tidpunkt då datauppsättningen väntade, väntade datauppsättningen på grund av otillräckligt CPU.

    ![Diagram C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Slutligen kontrollerar du **diagram D** som visar vilka typer av uppdateringar som har inträffat, schemalagt jämfört med på begäran. Eventuella uppdateringar som inträffar på begäran kan vara orsaken till begränsningen.

    ![Diagram D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Lösningar för scenario två

1. **Skala upp kapaciteten** – om du skalar upp kapaciteten till nästa SKU blir dubbelt så mycket minne och dubbelt så många samtidiga uppdateringar tillgängligt som med den aktuella SKU:n, vilket minskar CPU- och minnesbelastningen som för närvarande berör kapaciteten.

2. **Flytta datauppsättningar till en annan kapacitet** – om väntetiden beror på maximal samtidighet och du har en annan kapacitet som har tillgänglig samtidighet kan du flytta arbetsytorna som innehåller de större datauppsättningarna till den kapaciteten.

3. **Sprida ut schemalagda uppdateringar** – om du sprider ut uppdateringarna undviker du att för många uppdateringar försöker köra samtidigt.



## <a name="next-steps"></a>Nästa steg

* [Vad är Power BI Premium?](service-premium-what-is.md)
* [Viktig information om Power BI Premium](service-premium-release-notes.md)
* [Microsoft Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)
* [Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)
* [Aktivering av utökad Pro-utvärderingsversion](service-extended-pro-trial.md)
* [Vanliga frågor och svar om Power BI Embedded](developer/embedded/embedded-faq.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)