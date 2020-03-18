---
title: Datamängdslägen i Power BI-tjänsten
description: 'Förstå Power BI-tjänstens datamängdslägen: Import, DirectQuery och Sammansatt.'
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: be8716cebb091dafcc927b4bd1ecd0942ad88b47
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79208067"
---
# <a name="dataset-modes-in-the-power-bi-service"></a>Datamängdslägen i Power BI-tjänsten

Den här artikeln innehåller en teknisk förklaring av Power BI:s datamängdslägen. Den avser datamängder som representerar en direktanslutning till en externt värdbaserad Analysis Services-modell, och även för modeller som utvecklas i Power BI Desktop. Artikeln beskriver motiveringen för varje läge och möjlig påverkan på Power BI-kapacitetens resurser.

De tre datamängdslägena är:

- [Import](#import-mode)
- [DirectQuery](#directquery-mode)
- [Sammansatt](#composite-mode)

## <a name="import-mode"></a>Import-läge

Läget _Import_ är det vanligaste läget för att utveckla modeller. Det här läget ger mycket snabba resultat tack vare att frågorna sker i minnet. Det ger också designflexibilitet till modellerare och stöd för vissa Power BI-tjänstfunktioner (Frågor och svar, Snabbinsikter etc.). Tack vare dessa fördelar är detta standardläget när du skapar en ny Power BI Desktop-lösning.

Det är viktigt att känna till att importerade data alltid lagras på disk. När du har ställt en fråga eller uppdaterat, måste datan läsas in helt i minnet för Power BI-kapaciteten. När det sedan finns i minnet ger importmodellerna mycket snabba frågeresultat. Det är också viktigt att känna till att det inte finns någon metod där en importmodell delvis läses in i minnet.

När de uppdateras, komprimeras data och optimeras och sparas sedan till disk av VertiPaq-lagringsmotorn. När du har läst in från disk till minne är det möjligt att se 10x-komprimering. Därför kan du förvänta dig att 10 GB källdata kan komprimeras till ungefär 1 GB i storlek. Lagringsutrymmets storlek på disken kan ge en 20 % minskning av den komprimerade storleken. (Skillnaden i storlek kan fastställas genom att jämföra filstorleken för Power BI Desktop med aktivitetshanterarens minnesanvändning för filen.)

Designflexibilitet kan ske på tre sätt. Datamodellerare kan:

- Integrera data genom att cachelagra data från dataflöden och externa datakällor, oavsett typ av datakälla eller format
- Utnyttja hela uppsättningen funktioner för [Power Query-formelspråket](/powerquery-m/) (kallas informellt för M) när frågor för förberedelse av data skapas
- Använd hela uppsättningen av funktioner för [dataanalysuttryck (DAX)](/dax/) när modellen med affärslogik förbättras. Det finns stöd för beräknade kolumner, beräknade tabeller och mått.

Såsom visas på följande bild kan en importmodell integrera data från en rad olika typer av datakällor som stöds.

![En importmodell kan integrera data från olika typer av externa datakällor](media/service-dataset-modes-understand/import-model.png)

Även om det finns övertygande fördelar med importmodeller, finns det också nackdelar:

- Hela modellen måste läsas in i minnet innan Power BI kan fråga modellen, vilket kan belasta tillgängliga kapacitetsresurser allt eftersom antalet och storleken på importmodellerna växer
- Modelldata är endast så aktuella som den senaste uppdateringen och importmodellerna måste därför helst uppdateras enligt ett schema
- En fullständig uppdatering tar bort alla data från alla tabeller och läser in dem igen från datakällan. Detta kan vara väldigt dyrt med tanke på tid och resurser för Power BI-tjänsten och datakällan/datakällorna.

    > [!NOTE]
    > Power BI kan göra stegvisa uppdateringar för att undvika att hela tabeller trunkeras och måste läsas in på nytt. Den här funktionen stöds dock bara när datamängden finns i arbetsytor på Premium-kapaciteter. Mer information finns i artikeln [Inkrementell uppdatering i Power BI Premium](service-premium-incremental-refresh.md).

Från ett resursperspektiv för Power BI-tjänsten, kräver importmodeller:

- Tillräckligt med minne för att kunna läsa in modellen när den efterfrågas eller uppdateras
- Bearbetning av resurser och ytterligare minnesresurser för att uppdatera data

## <a name="directquery-mode"></a>DirectQuery-läge

_DirectQuery_-läget är ett alternativ till importläget. Modeller som utvecklats i DirectQuery-läget importerar inte data. I stället består de bara av metadata som definierar modellstrukturen. När frågor görs till modellen används interna frågor till att hämta data från den underliggande datakällan.

![En DirectQuery-modell utfärdar interna frågor till den underliggande datakällan](media/service-dataset-modes-understand/direct-query-model.png)

Det finns två huvudsakliga skäl till att utveckla en DirectQuery-modell:

- När datavolymerna är för stora – även när [dataförminskningsmetoder](guidance/import-modeling-data-reduction.md) tillämpas – för att läsa in i en modell eller uppdatera på ett praktiskt sätt
- När rapporter och instrumentpaneler behöver leverera data ”nära realtid”, utöver vad som kan uppnås inom gränserna för schemalagd uppdatering. (Schemalagda uppdateringsgränser är åtta gånger per dag för delad kapacitet och 48 gånger per dag för en Premium-kapacitet.)

Det finns flera fördelar med DirectQuery-modeller:

- Storleksgränser för importmodeller gäller inte
- Modellerna kräver inte någon uppdatering
- Rapportanvändarna ser senaste data när de interagerar med rapportfilter och utsnitt. Dessutom kan rapportanvändarna uppdatera hela rapporten för att hämta aktuella data.
- Rapporter i realtid kan utvecklas med hjälp av funktionen [Automatisk siduppdatering](desktop-automatic-page-refresh.md)
- Paneler på instrumentpanelen som är baserade på DirectQuery-modeller, kan uppdateras automatiskt så ofta som var 15:e minut

Det finns dock flera nackdelar och begränsningar med DirectQuery-modeller:

- Modellen måste baseras på en enda datakälla som stöds. Därför måste all dataintegrering redan finnas i datakällan. Datakällor som stöds är relationella och analytiska system, med stöd för många populära datalager.

    > [!TIP]
    > Många datakällor från Microsoft stöds. Bland Microsoft-datakällorna finns SQL Server, Azure Data Bricks, Azure HDInsight Spark (Beta), Azure SQL Database och Azure SQL Data Warehouse. Mer information finns i artikeln [Datakällor som stöds av DirectQuery i Power BI](desktop-directquery-data-sources.md).

- Prestandan kan vara långsam, vilket kan påverka Power BI-tjänsten negativt. Det här problemet kan uppstå eftersom vissa frågor är processorintensiva för Power BI-tjänsten. Det kan också bero på att datakällan inte är optimerad för de frågor som Power BI skickar.
- Power Query-frågor måste vara vikbara. Detta krav innebär att Power Query-logiken inte kan vara alltför komplex. Dessutom måste logiken vara begränsad till M-uttryck och funktioner som kan transponeras till interna frågor som kan tolkas av datakällan.
- DAX-formler är begränsade till att endast använda funktioner som kan transponeras till interna frågor som kan tolkas av datakällan. Det finns inte heller något stöd för beräknade tabeller eller för funktioner i DAX-tidsinformation.
- Frågor som ställs av modellen frågor som kräver hämtning av över en miljon rader kommer att misslyckas
- Rapporter och instrumentpaneler med flera visuella objekt kan visa inkonsekventa resultat, särskilt när datakällan är temporär
- Funktioner för Frågor och svar och Snabbinsikter stöds inte

Ur ett resursperspektiv för Power BI-tjänsten, kräver DirectQuery-modeller:

- Minimalt minne för att läsa in modellen (endast metadata) när den efterfrågas
- Ibland måste Power BI-tjänsten använda betydande processorresurser för att generera och bearbeta frågor som skickas till datakällan. När den här situationen uppstår kan det påverka dataflödet, särskilt när flera användare frågar modellen samtidigt.

Mer information finns i [Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md).

## <a name="composite-mode"></a>Sammansatt läge

_Sammansatt_ läge kan blanda import- och DirectQuery-lägen eller integrera flera DirectQuery-datakällor. Modeller som utvecklats i sammansatt läge kan konfigurera lagringsläget för varje modelltabell. Läget stöder även beräknade tabeller (definieras med DAX).

Tabellagringsläget kan konfigureras som Import, DirectQuery eller Dubbel. En tabell som har konfigurerats som dubbelt lagringsläge har både Import och DirectQuery. Det innebär att Power BI-tjänsten kan fastställa det effektivaste läget som ska användas för varje fråga.

![En sammansatt modell är en kombination av lagringslägena Import och DirectQuery, konfigurerade på tabellnivå](media/service-dataset-modes-understand/composite-model.png)

Sammansatta modeller strävar efter att leverera det bästa från Import- och DirectQuery-lägena. När de har konfigurerats korrekt kombinerar de hög frågeprestanda i minnesinterna modeller med möjlighet att hämta data nära realtid från datakällor.

Datamodellerare som utvecklar sammansatta modeller kommer troligen att konfigurera tabeller av dimensionstyp i lagringslägena Import eller Dubbel och tabeller av faktatyp i DirectQuery-läget. Mer information om tabellroller för modeller finns i [Förstå star-schemat och dess betydelse för Power BI](guidance/star-schema.md).

Anta exempelvis att du har en modell med tabellen **Produkt** av dimensionstyp i dubbelt läge och tabellen **Försäljning** av faktatyp i DirectQuery-läget. Det kan gå snabbare och vara effektivare att ställa frågor till tabellen **Produkt** från internminnet för att återge ett rapportutsnitt. Det går också att ställa frågor till tabellen **Försäljning** i DirectQuery-läget med den relaterade tabellen **Produkt**. Den senare frågan skulle kunna generera en enda effektiv intern SQL-fråga som slår samman tabellerna **Produkt** och **Försäljning** och filtrerar med utsnittsvärdena.

För sammansatta modeller beror i allmänhet de fördelar och nackdelar som är kopplade till import och DirectQuery på hur varje tabell har konfigurerats.

Mer information finns i [Använda sammansatta modeller i Power BI Desktop](desktop-composite-models.md).

## <a name="next-steps"></a>Nästa steg

- [Datamängder i Power BI-tjänsten](service-dataset-modes-understand.md)
- [Lagringsläge i Power BI Desktop](desktop-storage-mode.md)
- [Använd DirectQuery i Power BI](desktop-directquery-about.md)
- [Använda sammansatta modeller i Power BI Desktop](desktop-composite-models.md)
- Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
