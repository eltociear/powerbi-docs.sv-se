---
title: Använda den förbättrade beräkningsmotorn med dataflöden
description: Lär dig hur du använder den förbättrade beräkningsmotorn i Power BI Premium med data flöden
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e126451bf016bf4e9dcce7b7a4df51db9ed20386
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83320525"
---
# <a name="the-enhanced-compute-engine"></a>Den förbättrade beräkningsmotorn

Med den förbättrade beräkningsmotorn i Power BI kan Power BI Premium-prenumeranter använda sin kapacitet till att optimera användningen av dataflöden. Den förbättrade beräkningsmotorn har följande fördelar:

* Den minskar drastiskt hur lång tid det tar att uppdatera långvariga ETL-steg över beräknade entiteter, till exempel åtgärder som *join*, *distinct*, *filter* och *group by*
* Kör DirectQuery-frågor över entiteter (februari 2020)

I följande avsnitt beskrivs hur du aktiverar den förbättrade beräkningsmotorn och vi besvarar några vanliga frågor.


## <a name="using-the-enhanced-compute-engine"></a>Använda den förbättrade beräkningsmotorn

Du aktiverar den förbättrade beräkningsmotorn på sidan **Kapacitetsinställningar** i Power BI-tjänsten, i avsnittet **Dataflöden**. Den förbättrade beräkningsmotorn är **Av** som standard. Du aktiverar den genom att föra reglaget till **På** som i den här bilden, och sedan spara inställningarna. 

![Aktivera den förbättrade beräkningsmotorn](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

När du har aktiverat den förbättrade beräkningsmotorn återgår du till dataflödena. Du bör se bättre prestanda för alla beräknade enheter som utför komplexa åtgärder, som *join* eller *group by*, för dataflöden som skapats från befintliga länkade entiteter i samma kapacitet. 

Du får ut mesta möjliga av beräkningsmotorn om du delar upp ETL-fasen i två separata dataflöden på följande sätt:

* **Dataflöde 1** – det här dataflödet ska bara handla om att mata in allt som behövs från en datakälla och placera det i dataflöde 2.
* **Dataflöde 2** – utför alla ETL-åtgärder i det här andra dataflödet, men se till att du refererar till dataflöde 1 som ska ligga i samma kapacitet. Se också till att du utför vikbara åtgärder (filter, group by, distinct, join) först, innan övriga åtgärder, så att beräkningsmotorn används.

## <a name="common-questions-and-answers"></a>Vanliga frågor och svar

**Fråga:** Jag har aktiverat den förbättrade beräkningsmotorn, men mina uppdateringar går långsammare. Varför?

**Svar:** Om du aktiverar den förbättrade beräkningsmotorn finns det två möjliga förklaringar till att uppdateringarna går långsammare:

 - När den förbättrade beräkningsmotorn är aktiverad krävs det en del minne för att den ska fungera korrekt. Därför gör att mängden minne som är tillgängligt för uppdateringar minskar, vilket ökar risken för att uppdatering ska placeras i kö. Det här minskar också antalet dataflöden som kan uppdateras samtidigt. Du kan lösa det här problemet när du aktiverar den förbättrade beräkningsmotorn genom att öka mängden minne som är tilldelat till dataflöden, så att det fortfarande finns lika mycket minne tillgängligt för samtidiga uppdateringar av dataflöden.

 - En annan anledning till att uppdateringar kan ta längre tid är att beräkningsmotorn bara fungerar ovanpå befintliga entiteter. Om ditt dataflöde refererar till en datakälla som inte är ett dataflöde märker du ingen förbättring. Prestanda förbättras inte, för i vissa stordatascenarier skulle den initiala läsningen från en datakälla ta längre tid eftersom data måste skickas till den förbättrade beräkningsmotorn.  

**Fråga:** Jag ser inte reglaget för den förbättrade beräkningsmotorn. Varför?

**Svar:** Den förbättrade beräkningsmotorn lanseras stegvis i regioner runt om i världen. Vi väntar oss att det ska finnas stöd för samtliga regioner i slutet av 2020.

**Fråga:** Vilka datatyper stöds för beräkningsmotorn?

**Svar:** Den förbättrade beräkningsmotorn och dataflöden har för närvarande stöd för följande datatyper. Om ditt dataflöde inte använder någon av följande datatyper uppstår ett fel under uppdateringen:

* Datum/tid
* Decimaltal
* Text
* Heltal
* Datum/tid/zon
* Sant/falskt
* Datum
* Tid

## <a name="next-steps"></a>Nästa steg

I den här artikeln ges information om hur du använder den förbättrade beräkningsmotorn för dataflöden. Följande artiklar kan också vara till hjälp:

* [Dataförberedelser med självbetjäning för dataflöden](service-dataflows-overview.md)
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Resurser för utvecklare för Power BI-dataflöden](service-dataflows-developer-resources.md)

Mer information om Power Query och schemalagd uppdatering finns i följande artiklar:
* [Frågeöversikt i Power BI Desktop](desktop-query-overview.md)
* [Konfigurera schemalagd uppdatering](../connect-data/refresh-scheduled-refresh.md)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)
