---
title: Vägledning för sammansatta modeller i Power BI Desktop
description: Vägledning för att utveckla sammansatta modeller.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 528fc40427a1cb242d9154028d1a7c6617c8a14e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279697"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Vägledning för sammansatta modeller i Power BI Desktop

Den här artikeln vänder sig till datamodellerare som utvecklar sammansatta Power BI-modeller. Det beskriver användningsfall för sammansatta modeller och ger dig designvägledning. Mer specifikt är avsikten med vägledningen att hjälpa dig att avgöra om en sammansatt modell är lämplig för din lösning. Om så är fallet hjälper den här artikeln dig även att utforma en optimal modell.

> [!NOTE]
> Artikeln innehåller inte någon introduktion till sammansatta modeller. Om du inte är helt bekant med sammansatta modeller så rekommenderar vi att du först läser artikeln [Använda sammansatta modeller i Power BI Desktop](../transform-model/desktop-composite-models.md).
>
> Eftersom sammansatta modeller består av minst en DirectQuery-källa är det också viktigt att du har en grundlig förståelse av [modellrelationer](../transform-model/desktop-relationships-understand.md), [DirectQuery-modeller](../connect-data/desktop-directquery-about.md) och [DirectQuery-modelldesign](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Användningsfall för sammansatta modeller

Närhelst det är möjligt är det bästa att utveckla en modell i importläge. Det här läget erbjuder största möjliga designflexibilitet och bästa prestanda.

Utmaningar som har att göra med stora data volymer eller rapportering om data i nästan realtid kan dock inte lösas med importmodeller. I båda de här fallen kan du överväga en DirectQuery-modell, förutsatt att dina data lagras i en enskild datakälla som [stöds av DirectQuery-läget](../connect-data/power-bi-data-sources.md).

Dessutom kan du överväga att utveckla en sammansatt modell i följande situationer.

- Din modell kan vara en DirectQuery-modell, men du vill öka dess prestanda. I en sammansatt modell kan du förbättra prestanda genom att konfigurera lämplig lagring för respektive tabell. Du kan också lägga till [sammansättningar](../transform-model/desktop-aggregations.md). Båda dessa optimeringar diskuteras längre fram i den här artikeln.
- Du vill kombinera en DirectQuery-modell med ytterligare data som måste importeras till modellen. Importerade data kan läsas in från en annan datakälla eller från beräknade tabeller.
- Du vill kombinera två eller flera DirectQuery-datakällor i en enda modell.

> [!NOTE]
> Sammansatta modeller kan inte kombinera live-anslutningskällor eller analytiska DirectQuery-databaskällor. Live-anslutningskällor kan vara [externa värdbaserade modeller](../connect-data/service-datasets-understand.md#external-hosted-models) och Power BI-datamängder. Analytiska DirectQuery-databaskällor kan vara SAP Business Warehouse och SAP HANA.

## <a name="optimize-model-design"></a>Optimera modelldesignen

Du kan optimera en sammansatt modell genom att konfigurera [lagringslägen](../transform-model/desktop-storage-mode.md) för tabeller och genom att lägga till [sammansättningar](../transform-model/desktop-aggregations.md).

### <a name="table-storage-mode"></a>Tabelllagringsmodell

I en sammansatt modell kan du konfigurera lagringsläget för varje enskild tabell (med undantag för beräknade tabeller):

- **DirectQuery**: Vi rekommenderar att du konfigurerar det här läget för tabeller som representerar stora datavolymer eller som måste leverera resultat i nästintill realtid. Data kommer aldrig att importeras till dessa tabeller. Dessa tabeller är vanligtvis tabeller av faktatyp som används för sammanfattningar.
- **Import**: Vi rekommenderar att du konfigurerar det här läget för tabeller av dimensionstyp som används för filtrering och gruppering. I själva verket är detta det enda alternativet för tabeller som baseras på källor som inte stöds i DirectQuery-läge. Beräknade tabeller är alltid importtabeller.
- **Dubbla**: Vi rekommenderar att du konfigurerar det här läget för tabeller av dimensionstyp, i lägen när det är möjligt att de frågas tillsammans med DirectQuery-tabeller av faktatyp från samma källa.

Det finns flera möjliga scenarier när Power BI skickar frågor till en sammansatt modell:

- **Endast import- eller dubblettabeller frågas**: Alla data hämtas från modellcachen. Den levererar snabbast möjliga prestanda. Det här scenariot är vanligt för tabeller av dimensionstyp som frågas av filter eller visuella utsnittsobjekt.
- **Frågar dubblettabeller eller DirectQuery-tabeller från samma källa**: Alla data hämtas genom att en eller flera interna frågor skickas till DirectQuery-källan. Den ger snabbast möjliga prestanda, särskilt när källtabellerna innehåller lämpliga index. Det här scenariot är vanligt för frågor som relaterar tabeller av dubbel dimensionstyp och DirectQuery-tabeller av faktatyp. Dessa frågor är _interna_, så alla en-till-en-relationer eller en-till-många-relationer utvärderas som [starka relationer](../transform-model/desktop-relationships-understand.md#strong-relationships).
- **Alla andra frågor**: Dessa frågor omfattar externa relationer. Detta beror på att en importtabell relaterar till en DirectQuery-tabell, eller på att en dubblettabell relaterar till en DirectQuery-tabell från en annan källa, i vilket fall den beter sig som en importtabell. Alla relationer utvärderas som [svaga relationer](../transform-model/desktop-relationships-understand.md#weak-relationships). Det innebär också att grupperingar som tillämpas på icke-DirectQuery-tabeller måste skickas till DirectQuery-källan som en virtuell tabell. I det här fallet kan den interna frågan vara ineffektiv, särskilt när det gäller stora gruppuppsättningar. Dessutom kan den potentiellt exponera känsliga data i den interna frågan.

Sammanfattningsvis rekommenderar vi att du gör följande:

- Överväg noga om en sammansatt modell är rätt lösning. Samtidigt som den tillåter integration på modellnivå av olika datakällor, så introducerar den också designkomplexitet, vilket kan medföra vissa följder
- Ställ in lagringsläget på **DirectQuery** när en tabell är av faktatyp och lagrar stora datavolymer, eller måste leverera resultat i nästintill realtid
- Ange lagringsläget till **Dubbelt** när en tabell är av dimensionstyp, och den kommer då att frågas tillsammans med **DirectQuery**-tabeller av faktatyp baserade på samma källa
- Konfigurera lämpliga uppdateringsfrekvenser för att behålla modellcachen för dubblettabeller (och eventuella beroende beräknade tabeller) som synkroniseras med källdatabaserna
- Sträva efter att säkerställa datakällornas dataintegritet (inklusive modellcachen). Svaga relationer eliminerar rader när relaterade kolumnvärden inte matchar
- Optimera DirectQuery-datakällor med lämpliga index för effektiva kopplingar, filtrering och gruppering
- Läs inte in känsliga data till import- eller dubblettabeller om det finns risk för att en intern fråga fångas upp. Mer information finns i [Använda sammansatta modeller i Power BI Desktop (säkerhetsaspekter)](../transform-model/desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Sammansättningar

Du kan lägga till sammansättningar i DirectQuery-tabeller i den sammansatta modellen. Sammansättningarna cachelagras i modellen, och de fungerar som importtabeller (även om de inte kan användas som en modelltabell). Syftet med dem är att förbättra prestandan för frågor med högre kornighet. Mer information finns i [Aggregeringar i Power BI Desktop](../transform-model/desktop-aggregations.md).

Vi rekommenderar att en sammansättningstabellerna följer denna grundläggande regel: Antalet rader ska vara mindre än i den underliggande tabellen med en faktor på minst 10. Om den underliggande tabellen exempelvis innehåller 1 miljard rader, så får sammansättningstabellen inte överskrida 100 miljoner rader. Den här regeln säkerställer att det finns en tillräckliga prestanda i förhållande till kostnaden för att skapa och underhålla sammansättningstabellen.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Använda sammansatta modeller i Power BI Desktop](../transform-model/desktop-composite-models.md)
- [Modellrelationer i Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [DirectQuery-modeller i Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [Använda DirectQuery i Power BI Desktop](../connect-data/desktop-use-directquery.md)
- [Felsöka DirectQuery-modeller i Power BI Desktop](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI-datakällor](../connect-data/power-bi-data-sources.md)
- [Lagringsläge i Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Sammansättningar i Power BI Desktop](../transform-model/desktop-aggregations.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
