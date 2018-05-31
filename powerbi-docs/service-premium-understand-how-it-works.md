---
title: Minneshantering och -optimering för Power BI Premiumkapacitet
description: Läs mer om minneshantering och -optimering för Power BI Premiumkapacitet.
ms.date: 04/30/2018
ms.topic: article
ms.service: powerbi
ms.author: susuresh
ms.reviewer: susuresh
author: suds001
manager: kfile
ms.openlocfilehash: 4b849d1fa86ebe8c75f915e549326c80ff1e51ef
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2018
ms.locfileid: "33916963"
---
# <a name="power-bi-premium-capacity-resource-management-and-optimization"></a>Resurshantering och -optimering för Power BI Premiumkapacitet

Den här artikeln beskriver hur Power BI Premium-tjänsten hanterar resurser och ger tips om hur du planerar och optimerar din lösning.

## <a name="premium-capacity-memory-management"></a>Minneshantering för Premium-kapacitet

 Premium-kapacitetens minne förbrukas av:

* Minne som används av inlästa datauppsättningar
* Minne som används av uppdatering av datauppsättningen (både schemalagd och på begäran)
* Minne som används av rapportfrågor

När en begäran skickas ut mot en publicerad datauppsättning i din kapacitet, läses den datauppsättningen in från beständig lagring (det kallas även avbildningsinläsning). Att hålla datauppsättningen inläst i minnet hjälper att ge snabba svar på framtida frågor mot den här datauppsättningen. Utöver det minne som behövs för att hålla datauppsättningen inläst i minnet, förbrukar även rapportfrågor och uppdateringar av datauppsättningen ytterligare minne.

### <a name="dataset-memory-estimation"></a>Beräkning av datauppsättningsminne

När du försöker läsa in en datauppsättning i minnet, beräknar Power BI mängden minne som den datauppsättningen kommer att kräva för att slutföra det begärda kommandot. Datauppsättningar i minnet brukar vara större i storlek än när de sparas till disken. Under uppdatering av en datauppsättning, kräver minneskapaciteten minst dubbelt så mycket minne som när den är inaktiv.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Överansträngd kapacitet, avlägsning och inläsning av datauppsättningar

Power BI Premium ger dig möjligheten att överutnyttja din kapacitet. Du kan till exempel publicera fler datauppsättningar än kapacitetsminnet rymmer. Om de publicerade datauppsättningarna i kapaciteten behöver mer minne än vad som får plats i kapacitet, kommer vissa av datauppsättningarna att lagras separat i en beständig lagring. Den beständiga lagringen är en del av 100 TB lagring som är kopplade till var och en av dina kapaciteter.

Så, vilka datauppsättningar finns i minnet och vad händer med de andra datauppsättningarna? När en begäran skickas till en datamängd, läses den in i minnet (avbildningsinläsning), som vi sade tidigare. Begäran kan vara en rapportfråga eller en uppdateringsåtgärd.

Eftersom du kan överutnyttja din kapacitet, kan den även drabbas av minnesbelastning. När kapaciteten står inför minnesbelastning (eftersom en ny datauppsättning måste läsas in eller frågor om några inlästa datauppsättningar ökar minneskravet), *avlägsnar noden en eller flera datauppsättningar* som använder kapacitetsminnet. Datauppsättningar som är inaktiva (dvs. det finns ingen fråge-/uppdateringsåtgärd som körs för tillfället) avlägsnas först och borttagningsordningen sker på minst senast använda-basis (LRU). Om nya kommandon utfärdas till den avlägsnade datauppsättningen, försöker tjänsten att läsa in den i minnet, vilket eventuellt avlägsnar andra datauppsättningar. Det här beteendet tillåter ett mer effektivt utnyttjande genom att låta kapaciteten hantera många fler datauppsättningar än vad som ryms i minnet.

Att läsa in en datauppsättning i minnet är en förhållandevis kostsam åtgärd. Beroende på datauppsättningens storlek, kan det ta mellan några sekunder för små datauppsättningar till tiotals sekunder eller till och med minuter för stora datauppsättningar, till exempel sådana ~10 GB. Premium-kapaciteten försöker att minimera antalet gånger som kapaciteten behöver läsas in genom att hålla den minst senast använda datauppsättningen i minnet så länge som möjligt. När mer minne krävs, behöver vissa datauppsättningar avlägsnas och systemet försöker då välja den som har minst påverkan på användarupplevelsen. När mer minne krävs, behöver vissa datauppsättningar avlägsnas och systemet försöker då välja den som har minst påverkan på användarupplevelsen. Till exempel undviker systemet att avlägsna datauppsättningar som aktivt använts inom de senaste minuterna, eftersom det är troligt att de kommer att frågas igen inom kort.

Själva avlägsningsprocessen är en snabb åtgärd. Om datauppsättningen inte används aktivt vid tidpunkten för avlägsning, kommer användaren inte att kunna märka någon större påverkan från avlägsningen. Om för många datauppsättningar är aktiva samtidigt och det inte finns tillräckligt med minne för de alla, kan dock många avlägsningar ske. Det här kan leda till en situation med förslöing, där datauppsättningar konstant avlägsnas och läses in igen och användare kan uppleva en tydlig nedgång i svarstider och prestanda.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Minneskrav vid uppdatering av datauppsättningar konkurrerar med minneskrav för en aktiv datauppsättning

Datauppsättningar kan uppdateras enligt ett schema eller på begäran av användare. Som det beskrevs tidigare så krävs det minst dubbelt så mycket minne för fullständiga uppdateringar som minnesstorleken för de inlästa och inaktiva datauppsättningarna. Innan uppdateringen startar så görs en bedömning av minneskravet för en uppdatering. Om det totala minneskravet är större än det tillgängliga minnet i kapaciteten, avlägsnas vissa datauppsättningar. Kandidater för avlägsning väljs efter minst nyligen använda datauppsättningar, dvs. tjänsten försöker behålla så många nyligen använda datauppsättningar som möjligt i minnet.

Om nödvändig minneskapacitet inte är tillgänglig trots avlägsning, sätts uppdateringen i kö för återförsök. Tjänsten försöker igen tills den lyckas eller en ny uppdateringsåtgärd startar.

Om en interaktiv fråga utfärdas till en datauppsättning i kapaciteten och det inte finns tillräckligt med minne på grund av en pågående uppdatering, misslyckas den begäran och behöver göras om av användaren.

## <a name="cpu-resource-management-in-premium-capacity"></a>Processorresurshantering i premium-kapaciteten

Det finns två primära användare av processorresurser:

- Frågor från rapporter
- Uppdatera (bearbetning)

### <a name="queries-from-reports"></a>Frågor från rapporter

Rapportfrågor använder processorresurser av din kapacitet. Om din rapport har några frågor som är ineffektiva eller om du har många samtidiga användare, kan det ta upp mycket processorresurser och din befintliga kapaciteten kanske inte räcker till för att hantera belastningen.

### <a name="refresh-parallelization-policy"></a>Princip för uppdateringsparallellisering

Minnet är inte den enda resursen som kan begränsa uppdatering av datauppsättningar. Antalet v-kärnor på en server kan också vara en faktor. Eftersom varje uppdateringsåtgärd kräver ett visst antal v-kärnor, finns det en gräns för hur många uppdateringar som kan köras parallellt. Gränsen per SKU beskrivs i följande tabell. Ytterligare uppdateringar som sträcker sig utöver dessa gränser ställs i kö.

 | SKU  | Virtuella kärnor för serverdel  | Modellen uppdateringsparallellitet   |
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
> Om din uppdateringar blir fördröjda, kontrollerar du antalet parallella uppdateringar som stöds av din kapacitet.

## <a name="example-scenarios"></a>Exempelscenarier

Följande beskriver några vanliga scenarier och de åtgärder som vidtas av tjänsten:

 **Tjugo schemalagda uppdateringar har skickats på samma gång** – Power BI försöker starta de första *x* uppdateringarna samtidigt. Värdet för *x* fastställs av principen för uppdateringsparallellisering för den SKU:n. Om Power BI inte kan hämta tillräckligt med minne genom att avlägsna inaktiva datauppsättningar (datauppsättningar som inte använts nyligen), kommer inte alla *x* uppdateringar att starta på samma gång. Uppdateringar som inte går att starta, ställs i kö tills de kan starta.

 **Två uppdateringar körs på samma gång och det finns bara tillräckligt med minne för att slutföra** – den som kan slutföras startar. Den andra försöks igen senare.

 **Stora antal datauppsättningar frågas medan flera datauppsättningar uppdateras** – om det inte finns tillräckligt med minne tillgängligt, försöker Power BI att stoppa aktiva uppdateringar för att prioritera interaktiva frågor. Detta minskar uppdateringsprestandan.

 **DataSet kräver för mycket minne för att uppdateras på den aktuella kapacitetsstorleken** – uppdateringen misslyckas. Inga försök görs att hämta mer minne genom avlägsning.

 **Uppdatering av en enskild datauppsättning som ger en stor minnestopp** – om toppen är större än mängden minne som kan hämtas genom att avlägsna inaktiva datauppsättningar, försöks uppdateringen senare tills det finns tillräckligt med minne för att hantera toppen.

 **Frågan körs för en datauppsättning som inte kan hämta tillräckligt med minne genom att avlägsna alla inaktiva datauppsättningar och uppdateringar** – dessa frågor misslyckas. För den här typen av arbetsbelastningskrav bör du köpa en högre kapacitet.

## <a name="troubleshooting-and-testing"></a>Felsökning och testning

Om rapporter är långsam eller inte svarar, kan du börja genom att testa för en användare i din rapport. Öka sedan antalet samtidiga användare för att hitta gränsen. I många fall kan en finjustering av din DAX (rapportfrågor) drastiskt ändra prestandan i dina rapporter (och öka antalet samtidiga användare som stöds av din kapacitet).

Använd Power BI Embedded-kapaciteten i Azure för att testa olika SKU:er och fastställa bästa Premium SKU för din förväntade arbetsbelastning. Power BI Embedded A4 SKU är lika med P1, A5 = P2 och A6 = P3. I Azure kan du enkelt växla mellan SKU:er genom att skala uppåt och nedåt i Azure-portalen. När du hittar den SKU som passar bäst för din arbetsbelastning och är klar med testning, kan du ta bort SKU:n.

I vissa fall kan det hjälpa att veta mycket om problemet om du öppnar en PBIX-fil för modellen på din dator och kontrollera minnes- och processorförbrukning. Det hjälper inte för mycket stora modeller, men för vissa mindre modeller, kan du försöka öppna, uppdatera och fråga modellen från din dator. Kontrollera modellstorlek, minne och processorer som används när du öppnar modellen. Försök uppdatera och fråga. Använd aktivitetshanteraren för att kontrollera processor- och minnesförbrukning för den lokala PBIX-filen). Ibland kan dessa mått på själva datorn visa att en lägre premium-kapacitet som P1 / P2 kanske inte fungerar för din lösning.
