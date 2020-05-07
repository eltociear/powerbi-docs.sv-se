---
title: Inaktivera uppdatering av Power Query i bakgrunden
description: Vägledning om när du bör inaktivera uppdatering av Power Query i bakgrunden.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75623071"
---
# <a name="disable-power-query-background-refresh"></a>Inaktivera uppdatering av Power Query i bakgrunden

Den här artikeln är avsedd för importdatamodellerare som arbetar med Power BI Desktop.

När Power Query importerar data cachelagrar det även som standard upp till 1 000 rader med förhandsgranskningsdata för varje fråga. Förhandsgranskningsdata hjälper till att visa en snabb förhandsgranskning av källdata och transformeringsresultat för varje steg i dina frågor. De lagras separat på disk, inte i Power BI Desktop-filen.

När din Power BI Desktop-fil innehåller många frågor kan hämtning och lagring av förhandsgranskningsdata dock öka den tid det tar att slutföra en uppdatering.

## <a name="recommendation"></a>Rekommendation

Du får snabbare uppdateringar genom att ange Power BI Desktop-filen till att uppdatera förhandsgranskningscachen _i bakgrunden_. I Power BI Desktop aktiverar du detta genom att välja _Arkiv > Alternativ och inställningar > Alternativ_ och sedan välja sidan _Datainläsning_. Sedan kan du aktivera alternativet **Tillåt att förhandsgranskningen av data laddas ned i bakgrunden**. Observera att det här alternativet endast kan anges för den aktuella filen.

![Alternativ för bakgrundsdata i Power BI Desktop](media/power-query-background-refresh/power-query-options-background-data.png)

Om uppdatering i bakgrunden aktiveras kan det göra så att förhandsgranskningsdata blir inaktuella. Om detta sker får du ett meddelande från Power Query-redigeraren med följande varning:

![Varning från Power Query-redigeraren om föråldrade förhandsgranskningsdata](media/power-query-background-refresh/power-query-preview-data-old.png)

Det går alltid att uppdatera förhandsgranskningscachen. Du kan uppdatera den för en enskild fråga eller för alla frågor med hjälp av kommandot **Uppdatera förhandsgranskning**. Det finns i menyfliksområdet **Start** i fönstret för Power Query-redigeraren.

![Kommandon i Power Query-redigeraren för att uppdatera förhandsgranskningsdata](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Dokumentation om Power Query](/power-query/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
