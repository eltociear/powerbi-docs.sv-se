---
title: Använda naturligt språk vid import, Live Connect och Direct Query
description: I den här artikeln tittar vi på hur Frågor och svar-funktionen fungerar med de olika typerna av datakällor som är tillgängliga i Power BI. Vi tittar också närmare på begreppen indexering och cachelagring.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mohaali
ms.openlocfilehash: 85ecc5adc55daee86922c39e417db1cac5ba4a52
ms.sourcegitcommit: 0f807d3c74e5202b6e6a95fad49f2787928b9613
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706221"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>Använda naturligt språk vid import, Live Connect och Direct Query

Med hjälp av Frågor och svar-funktionen i Power BI kan du snabbt få svar från dina data genom att med hjälp av naturligt språk ställa frågor om dessa data. Den här artikeln beskriver hur indexering och cachelagring används för att förbättra prestandan för varje konfiguration med stöd.

## <a name="what-data-sources-are-supported-in-qa"></a>Vilka datakällor kan användas i Frågor och svar?

Frågor och svar kan användas i följande konfigurationer:

- Importläge
- Live Connect-läge – med lokala SQL Server Analysis Services, Azure Analysis Services eller Power BI-datamängder
- Direct Query – Azure Synapse, Azure SQL och SQL Server 2019. Även om andra källor kan fungera i Direct Query-läge finns det inte officiellt stöd för dessa källor.

Som standard är Frågor och svar aktiverat i en rapport om du använder det visuella objektet Frågor och svar. En prompt visas om du använder Direct Query eller Live Connect. Du kan uttryckligen aktivera/inaktivera funktionerna med naturligt språk för en rapport genom att gå till alternativen.

![Alternativ för Frågor och Svar i Desktop](media/qna-desktop-options.png)

Mer information finns i [Begränsningar för Power BI Frågor och svar](q-and-a-limitations.md).

## <a name="how-does-indexing-work-with-qa"></a>Hur fungerar indexeringen med Frågor och svar?

När du aktiverar Frågor och svar skapas ett index för att snabbt ge feedback i realtid till användaren och för att hjälpa till att tolka användarens frågor. Det kan ta lite tid att skapa indexet som har följande element och begränsningar.

- Alla kolumnnamn och tabeller infogas i indexet, såvida det inte uttryckligen har inaktiverats i Frågor och svar-verktyget.
- Alla textvärden med mindre än 100 tecken indexeras. Textvärden med fler än 100 tecken indexeras inte. 
- Frågor och svar lagrar maximalt 5 miljoner unika värden i indexet. Om du överskrider det här tröskelvärdet innehåller indexet inte alla potentiella värden, vilket kan minska noggrannheten i de resultat du får från Frågor och svar.
- Om ett fel inträffar under indexeringen behålls indexet i ett ofullständigt tillstånd och återskapas vid nästa uppdatering, enligt beskrivningen i nästa avsnitt.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>Hur ofta uppdateras och cachelagras indexet?

I Power BI Desktop skapas indexet när du använder Frågor och svar. En liten ikon visas som låter dig veta att indexet skapas. Under den här tiden kan det ta lite tid att läsa Frågor och svar-objektet, inklusive förslag.

I Power BI-tjänsten återskapas indexet vid publicering/ompublicering och uppdatering. Frågor och svar-indexet skapas inte alltid automatiskt och skapas ibland på begäran för att optimera uppdateringar av datamängderna. För Direct Query indexeras data högst en gång per dag för att minska påverkan på Direct Query-källan.

## <a name="next-steps"></a>Nästa steg

Du kan integrera naturligt språk i dina rapporter på flera olika sätt. Mer information finns i de här artiklarna:

* [Visuella frågor och svar](../visuals/power-bi-visualization-q-and-a.md)
* [Frågor och svar – metodtips](q-and-a-best-practices.md)
