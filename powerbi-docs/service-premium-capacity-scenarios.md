---
title: Scenarier för Microsoft Power BI Premium-kapacitet
description: Beskriver vanliga scenarier för Power BI Premium-kapacitet.
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
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565365"
---
# <a name="premium-capacity-scenarios"></a>Scenarier för Premium-kapacitet

Den här artikeln beskriver verkliga scenarier där Power BI premium-kapaciteter har implementerats. Vanliga problem och utmaningar är också beskrivs hur du identifierar problem, och hjälpa dig att lösa dem:

- [Uppdatera datauppsättningar kontinuerligt](#keeping-datasets-up-to-date)
- [Identifiera datauppsättningar som svarar långsamt](#identifying-slow-responding-datasets)
- [Identifiera orsaker till att datauppsättningar sporadiskt svarar långsamt](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Avgöra om det finns tillräckligt med minne](#determining-whether-there-is-enough-memory)
- [Avgöra om det finns tillräckligt med processor](#determining-whether-there-is-enough-cpu)

Stegen, tillsammans med diagram och tabell exempel är från den **Power BI Premium-kapacitet app** att en Power BI-administratör har åtkomst till.

## <a name="keeping-datasets-up-to-date"></a>Uppdatera datauppsättningar kontinuerligt

I det här scenariot utlöstes en undersökning när användare klagat över att rapportdata ibland verkade vara gamla eller ”inaktiva”.

I appen interagerar administratören med det visuella objektet för **Uppdateringar**, och sorterar datauppsättningar via statistiken för **Maximal väntetid** i fallande ordning. Det här visuella objektet hjälper dem att avslöja datauppsättningar som har de längsta väntetider, grupperade efter namn på arbetsyta.

![Uppdateringar av datauppsättningen sorterade efter fallande maximal väntetid, grupperade efter arbetsyta](media/service-premium-capacity-scenarios/dataset-refreshes.png)

I den **per timme uppdatera vänta Genomsnittstid** kan de se att vänta uppdateringstider konsekvent högsta cirka 4 PM varje dag.

![Uppdateringsväntetider är regelbundet som högst vid kl 16](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Det finns flera förklaringar till dessa resultat:

- För många uppdateringsförsök kan uppstå på samma gång, som överskrider de gränser som definierats av noden kapacitet. I det här fallet sex samtidiga uppdateringar på en P1 med standard minnesallokering.

- Datauppsättningar som ska uppdateras kan vara för stort för att passa tillgängligt minne (vilket kräver minst 2 x minne som krävs för fullständig uppdatering).
- Ineffektiv Power Query-logik kan resulterar i en topp av minnesanvändning under uppdateringen av datauppsättningen. På en upptagen kapacitet, kan den här topp ibland nå fysiska gränsen, misslyckas uppdateringen och potentiellt påverkar andra rapportåtgärder vyn på kapaciteten.
- Ofta efterfrågade datauppsättningar som måste vara kvar i minnet kan påverka andra datauppsättningar förmåga att uppdatera på grund av begränsad tillgängligt minne.

För att undersöka, kan Power BI-administratör söka efter:

- Lite tillgängligt minne vid tidpunkten för data uppdateras när tillgängligt minne är mindre än 2 ggr storleken på datauppsättningen uppdateras.
- Datauppsättningar inte som uppdateras och inte i minnet innan du uppdaterar har startats att visa interaktiva trafik under tung uppdateringstider. Om du vill se vilka datauppsättningar läses in i minnet vid en given tidpunkt, en Power BI-administratör kan titta på området datauppsättningar i **datauppsättningar** fliken i appen. Administratören kan sedan korsfiltrera till en viss tid genom att klicka på någon av staplarna i den **per timme läsa in datauppsättningen räknar**. En lokal topp som visas i bilden nedan, anger en timme när flera datauppsättningar lästes in i minnet, vilket kan försena början av schemalagda uppdateringar.
- Ökad datauppsättning borttagna tar placera när uppdateringar är schemalagda att starta. Borttagna kan betyda att det orsakades hög minnesbelastning katalogen för många olika interaktiva rapporter före tidpunkten för uppdatering. Det visuella objektet **Antal borttagna datauppsättningar och minnesförbrukning per timme** kan innehålla toppar i borttagningar.

Följande bild visar en lokal topp i inlästa datauppsättningar, vilket tyder på interaktiva frågor fördröjde starten av uppdateringarna. Att välja en tidsperiod i det visuella objektet **Inlästa datauppsättningar per timme** kommer att korsfiltrera det visuella objektet **Datauppsättningens storlek**.

![En lokal topp i inlästa datauppsättningar tyder på att interaktiva frågor fördröjde starten av uppdateringarna](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

Power BI-administratören kan försöka att lösa problemet genom att utföra åtgärder för att säkerställa att det finns tillräckligt med minne för datauppdateringarna genom att börja med att:

- Kontakta datauppsättning ägare och ber dem att sprida ut och utrymme ut data, uppdatera scheman.
- Minska datamängden paneler frågebelastningen genom att ta bort onödiga instrumentpaneler eller instrumentpanel, särskilt de som Framtvinga säkerhet på radnivå.
- Snabba uppdateringar genom att optimera Power Query-logik. Förbättra modellering beräknade kolumner eller tabeller. Minska datauppsättningens storlek eller konfigurera större datauppsättningar för att utföra inkrementella datauppdatering.

## <a name="identifying-slow-responding-datasets"></a>Identifiera långsamma svarar datauppsättningar

I det här scenariot kan en undersökning började när användare klagat att vissa rapporter tog för lång tid att öppna, och ibland skulle lägger.

I appen kan Power BI-administratören använda det visuella objektet **Frågevaraktigheter** för att fastställa de sämst presterande datauppsättningarna genom att sortera datauppsättningar efter fallande **Genomsnittlig varaktighet**. Det här visuella objektet visar också antal frågor för datauppsättningen, så du kan se hur ofta datauppsättningarna efterfrågas.

![Sämst presterande datauppsättningar](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

Administratören kan referera till den **fråga Varaktighetsfördelning** visuellt objekt, som visar en övergripande fördelning av bucketgrupperade frågeprestanda (< = 30ms, 0-100 MS) för den filtrera tidsperioden. I allmänhet anses frågor som tar en sekund eller mindre som dynamiska av de flesta användare. Frågor som tar längre tid tenderar att skapa en uppfattning av dålig prestanda.

Det visuella objektet **Frågevaraktighetsfördelning per timme** låter Power BI-administratören identifiera entimmesperioder när kapacitetsprestanda kan ha uppfattats som dålig. Ju större fältsegment som representerar frågevaraktigheter över en sekund, desto större risk att användare kommer att uppfatta sämre prestanda.

Det visuella objektet är interaktivt och när ett segment av fältet är markerat, korsfiltrerats motsvarande visuell tabell för **Frågevaraktigheter** på rapportsidan för att visa de datauppsättningar som den representerar. Den här korsfiltreringen tillåter Power BI-administratörer att enkelt identifiera vilka datauppsättningar som svarar långsamt.

Följande bild visar ett visuellt objekt filtrerat efter **Frågevaraktighetsfördelning per timme**, som fokuserar på sämst presterande datauppsättningar i buckets om en timma. 

![Visuella objekt för filtrerade frågevaraktighetsfördelning per timme visar de sämst presterande datauppsättningarna](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

När sämre prestanda datauppsättningen i timespan specifika timmen identifieras kan Power BI-administratör undersöka om sämre prestanda beror på en överbelastade kapacitet, eller på grund av ett dåligt utformat datauppsättningen eller rapporten. De kan referera till den **vänta Frågetider** visual och sortera datauppsättningar efter fallande genomsnittlig fråga väntetid. Om en stor del av frågor väntar troligen en höga krav på datauppsättningen orsaken för många frågan väntar. Om den genomsnittliga frågan väntetid är betydande (> 100 ms), kan det vara värt att granska datauppsättningen och rapporten för att se om optimeringar kan göras. Till exempel få färre visuella objekt på rapportsidor eller en optimering för DAX-uttryck.

![Det visuella objektet Frågeväntetider hjälper till att avslöja dåligt presterande datauppsättningar](media/service-premium-capacity-scenarios/query-wait-times.png)

Det finns flera anledningar för frågan vänta tid bygger upp i datauppsättningar:

- En icke-optimal Modelldesign, måttuttryck eller även rapportdesign - alla förhållanden som kan bidra till tidskrävande frågor som förbrukar hög CPU. Detta gör att nya frågor får vänta tills CPU-trådar bli tillgängliga och kan skapa en konvojeffekt (tänkt trafikstockning), som ofta ses under toppar vid kontorstider. Sidan **Frågan väntar** blir den viktigaste resursen för att avgöra om datauppsättningar har höga genomsnittliga frågeväntetider.
- Ett stort antal samtidiga kapacitetsanvändare (hundratals) använder samma rapport eller datauppsättning. Även välutformade datauppsättningar kan prestera dåligt så att en samtidighetströskel överskrids. Detta anges vanligtvis av en enda datauppsättning som visar ett avsevärt högre värde för frågan räknar än andra datauppsättningar show (till exempel 300 K frågor för en datauppsättning jämfört med < 30K frågor för alla andra datauppsättningar). På vissa peka frågan väntar för den här datauppsättningen kommer att börja skicka, vilket kan ses i den **fråga varaktigheter** visual.
- Många olika datauppsättningar som efterfrågas samtidigt orsakar minnesförslöing eftersom datauppsättningar ofta pendlar mellan att ha minne eller inte. Detta leder till att användare upplever långsam prestanda när datauppsättningen läses in i minnet. För att bekräfta, Power BI-administratör kan referera till den **per timme datauppsättning borttagna och minnesförbrukning** visuellt objekt, vilket kan innebära att ett stort antal datauppsättningar inlästa i minnet är flera gånger avlägsnas.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identifiera orsaker för sporadiskt långsam svarar datauppsättningar

I det här scenariot började en undersökning när användare beskrivs att visuella rapportobjekt ibland har svarar långsamt eller gick svarar, men ibland de befann sig bra dynamiskt.

I appen användes avsnittet **Frågevaraktigheter** för att hitta den orsakande datauppsättningen på följande sätt:

- I det visuella objektet **Frågevaraktigheter** filtrerade administratören datauppsättning för datauppsättning (med start på de översta datauppsättningarna som efterfrågats) och undersökte de korsfiltrerade staplarna i det visuella objektet **Frågevaraktighetsfördelning per timme**.
- När ett enda fält för en timmes visade betydande förändringar i förhållandet mellan alla varaktighet frågegrupper jämfört med andra timslångt staplar för datauppsättningen (till exempel förhållanden mellan färgerna som ändrar drastiskt), det innebär att den här datauppsättningen visas sporadiska ändras prestanda.
- Entimmesstaplarna visar en oregelbunden del av ineffektiva frågor, och angav ett tidsspann där datauppsättningen påverkades av en störande angränsande effekt, orsakad av andra datauppsättningars aktiviteter.

Bilden nedan visar en timme den 30 januari där det har inträffat en betydande minskning av prestanda för en datauppsättning, vilket anges av storleken på ”(3,10s]” för bucketen för körningsvaraktighet. Klicka på en timme verktygsfältet visar datauppsättningar inlästa i minnet under den tiden kan visa möjliga datauppsättningar som orsakar störningar från angränsande effekten.

![Fältet visar sämsta prestanda med en stor del](media/service-premium-capacity-scenarios/worst-performing-queries.png)

När timespan problematiska identifieras (till exempel under 30 januari i bilden ovan) Power BI-administratör kan ta bort alla filter för datauppsättningen och sedan filtrera enbart av den timespan att avgöra vilka datauppsättningar frågades aktivt under den här tiden. Orsaken datauppsättningen för effekten resursfördelningen är vanligtvis översta efterfrågade datauppsättning eller en med flest genomsnittliga frågevaraktigheten.

En lösning på problemet kan vara att distribuera orsakande datauppsättningar över olika arbetsytor på olika Premium-kapaciteter eller i delad kapacitet om datauppsättningens storlek, konsumtionskrav och datauppdateringsmönster stöds.

Omvänt kan också gälla. Power BI-administratören kan identifiera när en datauppsättnings frågeprestanda drastiskt förbättras och leta reda på vad som försvann. Om viss information saknas vid denna tidpunkt, kan detta hjälpa till att peka på vad som orsakar problemet.

## <a name="determining-whether-there-is-enough-memory"></a>Avgör om det finns tillräckligt med minne

För att avgöra om det finns tillräckligt mycket minne för kapaciteten för att slutföra sina arbetsbelastningar, kan Power BI-administratörer referera till det visuella objektet **Procent förbrukat minne** i fliken **Datauppsättningar** i appen. **Allt** minne (totalt) representerar det minne som förbrukas av datauppsättningar som är inlästa i minnet, oavsett om de aktivt efterfrågas eller bearbetas. **Aktivt** minne representerar det minne som förbrukats av datauppsättningar som bearbetas aktivt.

I en felfri kapacitet ser det visuella objektet ut så här och visar ett gap mellan Allt (totalt) och Aktivt minne:

![En felfri kapacitet visar ett gap mellan Allt (totalt) och Aktivt minne](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

I en kapacitet som upplever minnesbelastning visar samma visuella objekt tydligt aktiva minne och det totala minnet konvergerar, vilket innebär att det går inte att läsa in ytterligare datauppsättningar i minnet sedan. I det här fallet kan Power BI-administratören klicka på **Kapacitetsomstart** (i **Avancerade alternativ** i området för kapacitetsinställningar i administratörsportalen). Omstart av kapaciteten leder till att alla datauppsättningar rensas från minnet så att de kan läsas in i minnet igen såsom krävs (av frågor eller datauppdatering).

![**Aktivt** minne slås samman med **Allt** minne](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Avgör om det finns tillräckligt med CPU

I allmänhet ska en kapacitets genomsnittliga CPU-användning vara mindre än 80 %. Överskrids detta värde innebär det att kapaciteten närmar sig processormättnad.

Effekterna av processormättnad uttrycks av åtgärder som tar längre tid än de ska på grund av den kapacitet som utför många CPU kontexter växlar eftersom den försöker bearbeta alla åtgärder. Detta anges i en Premium-kapacitet med ett stort antal samtidiga frågor av hög fråga väntetider. En följd av höga frågeväntetider är långsammare svarstider än vanligt. Power BI-administratören kan enkelt identifiera när processorn är mättad genom att visa det visuella objektet **Väntetidsfördelningar per timme**. Periodiska toppar av frågeväntetider indikerar potentiell processormättnad.

![Periodiska toppar av frågeväntetider indikerar potentiell processormättnad](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Ett liknande mönster kan ibland identifieras i bakgrundsåtgärder om de bidrar till processormättnad. En Power BI-administratör kan söka efter en regelbunden topp i uppdateringstider för en specifik datauppsättning, vilket kan tyda på processormättnad vid tidpunkten (förmodligen på grund av andra pågående datauppsättningen uppdateras och/eller interaktiva frågor). I det här fallet avslöjar vyn **System** i appen inte nödvändigtvis att processorn är på 100 %. Vyn **System** visas enligt medelvärde per timme, men processorn kan bli mättad i flera minuter av tunga åtgärder som dyker upp som toppar i väntetider.

Det finns flera olika nyanser för att se effekten av processormättnad. Antalet frågor som väntar är viktigt, frågeväntetid sker alltid i viss omfattning utan att orsaka uppenbar prestandaförsämring. Vissa datauppsättningar (med längre genomsnittlig frågetid, vilket indikerar komplexitet eller storlek) är mer benägna att orsaka effekterna av processormättnad än andra. För att enkelt identifiera dessa datauppsättningar, kan Power BI-administratören söka efter ändringar i färgsammansättning av staplarna i det visuella objektet **Väntetidsfördelningar per timma**. Efter att ha upptäckt ett avvikande fält, kan de leta efter de datauppsättningar som hade frågeväntetid under denna tid och också titta på genomsnittlig frågeväntetid jämfört med genomsnittlig frågevaraktighet. När de här två måtten är av samma storlek och frågearbetsbelastningen för datauppsättningen är icke-trivial, är det troligt att datauppsättningen påverkas av otillräcklig processor.

Detta kan vara särskilt tydligt när en datauppsättning som används i korta ökningar av hög frekvens frågor av flera användare (till exempel i en utbildning-session), vilket resulterar i processormättnad under varje burst. I det här fallet kan betydande frågeväntetider för den här datauppsättningen uppstå och påverka andra datauppsättningar i kapacitet (störande angränsande effekt).

I vissa fall kan Power BI-administratörer begära att datauppsättningens ägare skapar en mindre föränderlig frågearbetsbelastning genom att skapa en instrumentpanel (som frågar med jämna mellanrum vid alla uppdateringar av datauppsättning efter cachelagrade paneler) i stället för en rapport. Detta kan förhindra toppar när instrumentpanelen läses in. Den här lösningen kanske inte alltid är möjlig för alla verksamhetskrav, men den kan vara ett effektivt sätt att undvika processormättnad, utan att göra ändringar på datauppsättningen.

## <a name="acknowledgements"></a>Bekräftelser

Den här artikeln är skriven av Peter Myers, Data Platform MVP och oberoende BI-expert med [bitvis lösningar](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Övervaka Premium-kapaciteter med appen](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Övervaka kapaciteter i Admin portal](service-admin-premium-monitor-portal.md)   

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

||||||