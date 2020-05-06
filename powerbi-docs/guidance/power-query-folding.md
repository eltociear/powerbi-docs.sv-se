---
title: Vägledning om frågedelegering i Power BI Desktop
description: Vägledning om att åstadkomma Power Query-frågedelegering i Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75622145"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Vägledning om frågedelegering i Power BI Desktop

Den här artikeln vänder sig till datamodellerare som utvecklar modeller i Power BI Desktop. Den innehåller rekommendationer om när och hur du kan åstadkomma Power Query-frågedelegering.

_Frågedelegering_ är möjligheten för en Power Query-fråga att generera ett enda frågeuttryck som hämtar och transformerar källdata. Mer information finns i [Power Query-frågedelegering](/power-query/power-query-folding).

## <a name="guidance"></a>Vägledning

Vägledningen om frågedelegering är olika beroende på modelläget.

Power Query-frågan måste uppnå frågedelegering för **DirectQuery** eller tabeller med **dubbelt** lagringsläge.

För en tabell av typen **Import** kan det vara möjligt att uppnå frågedelegering. När frågan baseras på en relationskälla, och om en enda SELECT-instruktion kan konstrueras, får du _bästa möjliga prestanda för datauppdateringen_ genom att säkerställa att frågedelegering verkligen sker. Om Power Query-kombinationsmotorn fortfarande måste bearbeta transformationer bör du minimera den mängd arbete den måste utföra, särskilt för stora datamängder.

I följande punktlista ges specifik vägledning.

- **Delegera så mycket bearbetning till datakällan som möjligt**: Om inte alla steg i en Power Query-fråga kan delegeras ska du identifiera vilket steg det är som förhindrar frågedelegering. Om det går kan du flytta senare steg till en tidigare position i sekvensen så att de omfattas av frågedelegeringen. Observera att Power Query-kombinationsmotorn kan vara tillräckligt smart för att ordna om frågestegen när den genererar källfrågan.

    För en relationsdatakälla gäller att om det steg som förhindrar frågedelegeringen kan utföras i en enda SELECT-instruktion, eller i procedurlogiken för en lagrad procedur, så bör du överväga att använda en intern SQL-fråga enligt nedanstående beskrivning.

- **Använd en intern SQL-fråga**: När en Power Query-fråga hämtar data från en relationskälla går det att använda en intern SQL-fråga för vissa källor. Frågan kan faktiskt vara valfri giltig instruktion, även att köra en lagrad procedur. Om instruktionen genererar flera resultatuppsättningar returneras bara den första. Parametrar kan deklareras i instruktionen, och vi rekommenderar att du använder M-funktionen [Value.NativeQuery](/powerquery-m/value-nativequery). Den här funktionen har utformats för att på ett säkert och smidigt sätt skicka parametervärden. Det är viktigt att du förstår att Power Query-kombinationsmotorn inte kan delegera efterföljande frågesteg. Därför bör du inkludera all transformeringslogik, eller så mycket som möjligt, i den interna frågeinstruktionen.

    Det finns två viktiga saker att tänka på när du använder interna SQL-frågor:

    - För en DirectQuery-modelltabell måste frågan vara en SELECT-instruktion, och den kan inte använda vanliga tabelluttryck (CTE) eller en lagrad procedur.
    - Inkrementell uppdatering kan inte använda en intern SQL-fråga. Detta skulle tvinga Power Query-kombinationsmotorn att hämta alla källrader och sedan använda filter för att fastställa inkrementella ändringar.

    > [!IMPORTANT]
    > En intern SQL-fråga kan göra mer än att bara hämta data. Du kan köra valfri giltig instruktion (eventuellt flera gånger), även sådana som ändrar eller tar bort data. Det är viktigt att du använder principen om minsta behörighet så att det konto som används för åtkomst till databasen bara har läsbehörighet till nödvändiga data.

- **Förbered och transformera data i källan**: När du upptäcker att vissa Power Query-frågesteg inte kan delegeras kan du kanske utföra transformeringarna i datakällan. Transformeringarna kan uppnås genom att du skriver en databasvy som logiskt transformerar källdata. Det kan även gå att fysiskt förbereda och materialisera data innan Power BI kör frågor mot dem. Ett relationsbaserat informationslager är ett utmärkt exempel på förberedda data, eftersom det vanligtvis består av förintegrerade källor till organisationsdata.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- Konceptartikel om [frågedelegering](/power-query/power-query-folding) i Power Query
- [Inkrementell uppdatering i Power BI Premium](../service-premium-incremental-refresh.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
