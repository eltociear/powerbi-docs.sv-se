---
title: Cachelagring av frågor i Power BI Premium
description: Cachelagring av frågor i Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/16/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: e45773784fbe97f8521ad071c03e86dcbddddbeb
ms.sourcegitcommit: 4689766f08f5285deac50bec595d57c3a398fff5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68329127"
---
# <a name="query-caching-in-power-bi-premium"></a>Cachelagring av frågor i Power BI Premium

Organisationer med Power BI Premium kan dra nytta av *cachelagring av frågor* för snabbare rapporter som är associerade med en datauppsättning. Med cachelagring av frågor instrueras Premium-kapaciteten att använda den lokala cachelagringstjänsten för att bibehålla frågeresultat, så att inte den underliggande datakällan beräknar dessa resultat.

> [!IMPORTANT]
> Cachelagring av frågor är endast tillgängligt i Power BI Premium. Det är inte tillämpligt för LiveConnect-datauppsättningar som använder Azure Analysis Services eller SQL Server Analysis Services.

Cachelagrade frågeresultat är specifika för användar- och datauppsättningskontext och respekterar alltid säkerhetsregler. För närvarande utför tjänsten endast cachelagring av frågor för den första sidan som du hamnar på. Med andra ord cachelagras inte frågor när du interagerar med rapporten. Frågecachen respekterar [personliga bokmärken](consumer/end-user-bookmarks.md#personal-bookmarks) och [beständiga filter](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/). Därmed cachelagras frågor som genereras av en anpassad rapport. [Paneler på instrumentpaneler](service-dashboard-tiles.md) som tillhandahålls av samma frågor drar också fördel när frågan har cachelagrats. Prestanda drar särskilt fördel när en datauppsättning används ofta och sällan behöver uppdateras. Cachelagring av frågor kan också minska belastningen på Premium-kapaciteten genom att minska det totala antalet frågor.

Du styr funktionssättet för cachelagring av frågor på sidan **Inställningar** för datauppsättningen i Power BI-tjänsten. Det finns två möjliga inställningar:

- **Av**: Använd inte cachelagring av frågor för den här datauppsättningen.

- **På**: Använd cachelagring av frågor för den här datauppsättningen.

![Dialogrutan Cachelagring av frågor](media/power-bi-query-caching/power-bi-query-caching.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

- När du ändrar inställningar för cachelagring från **På** till **Av** tas alla frågeresultat för datauppsättningen som sparats tidigare bort från kapacitetscachen. Du kan inaktivera cachelagring explicit eller genom att återgå till inställningen Kapacitetsstandard som en administratör har ställt in på **Av**. Om du inaktiverar det kan det medföra en kort fördröjning nästa gång en rapport kör frågor mot den här datauppsättningen. Fördröjningen orsakas av att de rapportfrågorna körs på begäran och inte använder sparade resultat. Datauppsättningen som krävs kan dessutom behöva läsas in i minnet innan den kan användas för frågor.
- När frågesyntaxen uppdateras måste Power BI köra frågor mot de underliggande datamodellerna för att hämta de senaste resultaten. Om ett stort antal datamängder har cachelagring av frågor aktiverat och Premium-kapaciteten är hårt belastad kan viss prestandaförsämring ske under cacheuppdatering. Försämringen beror på den ökade volymen av frågor som körs.

## <a name="next-steps"></a>Nästa steg

[Vad är Power BI Premium?](service-premium-what-is.md)

