---
title: Minneshantering och -optimering för Power BI Premiumkapacitet
description: Läs mer om minneshantering och -optimering för Power BI Premiumkapacitet.
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-admin
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d7cebbd569d16192f4acfa1c96394130731efa17
ms.sourcegitcommit: d4d36b6b200f2693b545e4a3e66d94c77a3cfafb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57014586"
---
# <a name="microsoft-power-bi-premium-capacity-resource-management-and-optimization"></a>Resurshantering och -optimering för Microsoft Power BI Premium-kapacitet

Den här artikeln beskriver hur Power BI Premium hanterar resurser. Artikeln innehåller även exempel och felsökningsförslag. En översikt finns i [Vad är Power BI Premium?](service-premium.md).

## <a name="premium-capacity-memory-management"></a>Minneshantering för Premium-kapacitet

 Premium-kapacitetens minne förbrukas av:

* De datamängder som läses in i minnet
* Uppdatering av datamängd (både schemalagd och på begäran)
* Arbetsbelastningar som kapaciteten har stöd för
* Rapportfrågor

När en begäran skickas ut mot en publicerad datauppsättning i din kapacitet, läses den datauppsättningen in från beständig lagring (det kallas även avbildningsinläsning). Att hålla datauppsättningen inläst i minnet hjälper att ge snabba svar på framtida frågor mot den här datauppsättningen. Utöver det minne som behövs för att hålla datamängden inläst i minnet förbrukar rapportfrågor och uppdateringar av datamängden ytterligare minne.

### <a name="dataset-memory-estimation"></a>Beräkning av datauppsättningsminne

När du försöker läsa in en datamängd i minnet beräknar Power BI mängden minne som den datamängden kommer att kräva för att slutföra det begärda kommandot. Datamängder i minnet brukar vara större i storlek än när de sparas till disken. Under uppdatering av en datauppsättning, kräver Power BI minst dubbelt så mycket minne som när datamängden är inaktiv.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Överansträngd kapacitet, avlägsning och inläsning av datauppsättningar

Power BI Premium ger dig möjligheten att *överutnyttja* din kapacitet. Du kan till exempel publicera fler datamängder än vad kapaciteten rymmer. Om de publicerade datamängderna behöver mer minne än vad som får plats i kapaciteten lagras vissa av datamängderna separat i beständig lagring. Den beständiga lagringen är en del av de 100 TB med lagring som är kopplade till var och en av dina kapaciteter.

Vilka datamängder finns då i minnet, och vad händer med de andra datamängderna? När en begäran skickas till en datamängd, läses den in i minnet (avbildningsinläsning), som vi sade tidigare. Begäran kan vara en rapportfråga eller en uppdateringsåtgärd. Men eftersom du kan överutnyttja kapaciteten kan den även drabbas av minnesbelastning. När en kapacitet drabbas av minnesbelastning *avlägsnar* noden en eller flera datamängder från minnet. Datamängder som är inaktiva (utan frågor/uppdateringsåtgärder som körs för tillfället) avlägsnas först. Avlägsnandeordern baseras sedan på ett mått på ”minst nyligen använd” (LRU, Least Recently Used). Om nya kommandon utfärdas till den avlägsnade datamängden försöker tjänsten att läsa in datamängden i minnet, vilket eventuellt avlägsnar andra datamängder. Det här beteendet tillåter ett mer effektivt utnyttjande genom att låta kapaciteten hantera många fler datauppsättningar än vad som ryms i minnet.

Att läsa in en datauppsättning i minnet är en förhållandevis kostsam åtgärd. Beroende på datamängdens storlek kan det ta mellan några sekunder för små datamängder till tiotals sekunder eller till och med minuter för stora datamängder, till exempel sådana som är på ca 10 GB. Premium-kapaciteten försöker att minimera antalet gånger som kapaciteten behöver läsas in genom att hålla den minst senast använda datauppsättningen i minnet så länge som möjligt. När mer minne krävs, behöver vissa datauppsättningar avlägsnas och systemet försöker då välja den som har minst påverkan på användarupplevelsen. När mer minne krävs, behöver vissa datauppsättningar avlägsnas och systemet försöker då välja den som har minst påverkan på användarupplevelsen. Till exempel undviker systemet att ta bort datamängder som har använts aktivt under de senaste minuterna. Det är troligt att frågor körs mot dessa datamängder igen mycket snart.

Själva avlägsningsprocessen är en snabb åtgärd. Om datauppsättningen inte används aktivt vid tidpunkten för avlägsning, kommer användaren inte att kunna märka någon större påverkan från avlägsningen. Om för många datamängder är aktiva samtidigt och det inte finns tillräckligt med minne för de alla kan dock många avlägsnanden ske. För många aktiva datamängder kan leda till en situation med ”nedskräpning”, där datamängder konstant avlägsnas och läses in igen och användare kan uppleva en tydlig nedgång i svarstider och prestanda.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Minneskrav vid uppdatering av datauppsättningar konkurrerar med minneskrav för en aktiv datauppsättning

Datauppsättningar kan uppdateras enligt ett schema eller på begäran av användare. Som det beskrevs tidigare krävs det minst dubbelt så mycket minne för fullständiga uppdateringar som minnesstorleken för de inlästa och inaktiva datamängderna. Innan uppdateringen startar så görs en bedömning av minneskravet för en uppdatering. Om det totala minneskravet är större än det tillgängliga minnet i kapaciteten, avlägsnas vissa datauppsättningar. Borttagning baseras alltså på LRU.

Om nödvändig minneskapacitet inte är tillgänglig trots avlägsning, sätts uppdateringen i kö för återförsök. Tjänsten försöker igen tills den lyckas eller en ny uppdateringsåtgärd startar.

Om en interaktiv fråga utfärdas till en datauppsättning i kapaciteten och det inte finns tillräckligt med minne på grund av en pågående uppdatering, misslyckas den begäran och behöver göras om av användaren.

### <a name="workloads"></a>Arbetsbelastningar

Som standard stöder kapaciteter för **Power BI Premium** och **Power BI Embedded** endast den arbetsbelastning som är associerad med Power BI-frågor som körs i molnet. Vi erbjuder nu stöd för förhandsversioner av två ytterligare arbetsbelastningar: **Sidnumrerade rapporter** och **dataflöden**. Om de är aktiverade kan de här arbetsbelastningarna påverka minnesanvändningen i din kapacitet. 

## <a name="cpu-resource-management-in-premium-capacity"></a>Processorresurshantering i premium-kapaciteten

Det finns två primära användare av processorresurser:

* Frågor från rapporter
* Uppdatera (bearbetning)

### <a name="queries-from-reports"></a>Frågor från rapporter

Rapportfrågor förbrukar processorresurser in din kapacitet. Rapporter med ineffektiva frågor eller många samtidiga användare kan förbruka stora mängder processorresurser. Din befintliga kapacitet räcker kanske inte till för att hantera belastningen.

### <a name="refresh-parallelization-policy"></a>Princip för uppdateringsparallellisering

Minnet är inte den enda resurs som kan begränsa uppdatering av datamängder. Antalet v-kärnor på en server kan också vara en faktor. Eftersom varje uppdateringsåtgärd kräver ett visst antal v-kärnor finns det en gräns för hur många uppdateringar som kan köras parallellt. Gränsen per SKU beskrivs i följande tabell. Ytterligare uppdateringar som sträcker sig utöver dessa gränser ställs i kö.

 | SKU | Virtuella kärnor för serverdel | Modellen uppdateringsparallellitet |
 | --- | --- | --- |
 | A1  | 0.5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0.5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Om dina uppdateringar fördröjs kontrollerar du antalet parallella uppdateringar som stöds av din kapacitet.

## <a name="example-scenarios"></a>Exempelscenarier

Här är några vanliga scenarier och de åtgärder som vidtas av tjänsten:

**Tjugo schemalagda uppdateringar har skickats på samma gång**. Power BI försöker starta de första *x* uppdateringarna samtidigt. Värdet för *x* fastställs av principen för uppdateringsparallellisering för den SKU:n. Om Power BI inte kan hämta tillräckligt med minne genom att avlägsna inaktiva datauppsättningar (datauppsättningar som inte använts nyligen), kommer inte alla *x* uppdateringar att starta på samma gång. Uppdateringar som inte kan starta ställs i kö tills de kan starta.

**Två uppdateringar körs på samma gång och det finns bara tillräckligt med minne för att slutföra en av dem**. Det som kan slutföras startar. Den andra försöks igen senare.

**Stort antal datamängder tar emot frågor medan flera datamängder uppdateras**. Om det inte finns tillräckligt med minne försöker Power BI stoppa aktiva uppdateringar för att prioritera interaktiva frågor. Detta minskar uppdateringsprestandan.

**Datamängden kräver för mycket minne för att uppdateras på den aktuella kapacitetsstorleken**. Uppdateringen misslyckas. Inga försök görs att hämta mer minne genom avlägsning.

**Uppdatering av en enda datamängd som ger en stor minnestopp**. Om toppen är större än den mängd minne som kan hämtas genom att avlägsna inaktiva datamängder försöks uppdateringen senare tills det finns tillräckligt med minne för att hantera toppen.

**Frågan körs för en datamängd som inte kan hämta tillräckligt med minne genom att avlägsna alla inaktiva datamängder och uppdateringar**. Dessa frågor misslyckas. För den här typen av arbetsbelastningskrav bör du köpa en högre kapacitet.

## <a name="troubleshooting-and-testing"></a>Felsökning och testning

Om rapporter är långsam eller inte svarar, kan du börja genom att testa för en användare i din rapport. Öka sedan antalet samtidiga användare för att hitta gränsen. I många fall kan en justering av DAX-frågorna avsevärt ändra prestanda för dina rapporter. Frågejusteringar ökar även antalet samtidiga användare som stöds av kapaciteten. [Övervaka din kapacitet](service-admin-premium-monitor-capacity.md) för att identifiera potentiella prestandaproblem.

Använd Power BI Embedded-kapaciteten i Azure för att testa olika SKU:er och fastställa bästa Premium SKU för din förväntade arbetsbelastning. Power BI Embedded A4 SKU är lika med P1, A5 = P2 och A6 = P3. I Azure kan du enkelt växla mellan SKU:er genom att skala uppåt och nedåt i Azure-portalen. När du hittar den SKU som passar bäst för din arbetsbelastning och är klar med testning, kan du ta bort SKU:n.

I vissa fall kan du få mycket information om problemet om du öppnar en Power BI Desktop-fil (.pbix) för modellen på din dator och kontrollerar minnes- och processorförbrukning. Det hjälper inte för mycket stora modeller, men för vissa mindre modeller, kan du försöka öppna, uppdatera och fråga modellen från din dator. Kontrollera modellstorlek, minne och processorer som används när du öppnar modellen. Försök uppdatera och fråga. Använd aktivitetshanteraren för att kontrollera processor- och minnesförbrukning för den lokala filen. Ibland kan dessa mått på själva datorn visa att en lägre premium-kapacitet som P1 / P2 kanske inte fungerar för din lösning.

