---
title: Använda DirectQuery med dataflöden i Power BI (förhandsversion)
description: Lär dig hur du använder DirectQuery med dataflöden i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 469b8b13f77c56f9371ae8c1c81dcb94278c62e0
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83794000"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Använda DirectQuery med dataflöden i Power BI (förhandsversion)

Du kan använda DirectQuery för att ansluta direkt till dataflöden, vilket gör att du kan ansluta direkt till ditt dataflöde utan att importera dess data. 

Att använda DirectQuery med dataflöden innebär följande förbättringar för dina Power BI- och dataflödesprocesser:

* **Du behöver inte ha separata uppdateringsscheman** – DirectQuery ansluter direkt till ett dataflöde, vilket gör att du inte behöver skapa en importerad datamängd. När du använder DirectQuery med dina dataflöden behöver du inte längre separata uppdateringsscheman för dataflödet och datauppsättningen för att säkerställa att data är synkroniserade.

* **Filtrering av data** – DirectQuery är användbart när du arbetar med en filtrerad vy av data i ett dataflöde. Om du vill filtrera data, och arbeta med en mindre delmängd av data i ditt dataflöde, kan du använda DirectQuery (och beräkningsmotorn) för att filtrera dataflödesdata och arbeta med den filtrerade delmängd du behöver.


## <a name="using-directquery-for-dataflows"></a>Använda DirectQuery för dataflöden

Att använda DirectQuery med dataflöden är en förhandsgranskningsfunktion som är tillgänglig från och med maj 2020-versionen av Power BI Desktop. 

Det finns också krav för att använda DirectQuery med dataflöden:

* Ditt dataflöde måste finnas i en Power BI Premium-aktiverad arbetsyta
* **Beräkningsmotorn** måste vara aktiverad. Läs mer om [den förbättrade beräkningsmotorn](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Aktivera DirectQuery för dataflöden

För att dataflödet ska vara tillgängligt för DirectQuery måste den förbättrade beräkningsmotorn vara i sitt optimerade tillstånd. Om du vill aktivera DirectQuery för dataflöden, anger du det nya alternativet **Förbättrade inställningar för beräkningsmotor** till **på**. Följande bild visar när inställningen är korrekt vald.

![Aktivera den förbättrade beräkningsmotorn för dataflöden](media/service-dataflows-directquery/dataflows-directquery-01.png)

När du har tillämpat den inställningen uppdaterar du dataflödet så att optimeringen börjar gälla. 


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Det finns några kända begränsningar med DirectQuery och dataflöden, som beskrivs i följande lista.

* DirectQuery för dataflöden fungerar inte med funktionen **enhanced metadata preview** (förbättrad metadataförhandsgranskning) aktiverad. Detta undantag förväntas tas bort i en kommande månatlig version av Power BI Desktop.

* Under förhandsversionsperioden för funktionen kan tidsgränser nås eller prestandaproblem uppstå för vissa kunder när de använder DirectQuery med dataflöden. Sådana problem håller på att åtgärdas under förhandsversionsperioden.

* Sammansatta/blandade modeller som har import- och DirectQuery-datakällor stöds inte för närvarande.

* Stora dataflöden kan få timeout-problem vid visning av visualiseringar. Den här begränsningen förväntas försvinna när funktionen blir allmänt tillgänglig. Under tiden bör stora dataflöden som kan stöta på timeout-problem använda importläget.

* Anslutningsappen för dataflöden visar ogiltiga autentiseringsuppgifter under inställningarna för datakälla om du använder DirectQuery. Detta påverkar inte beteendet och datamängden kommer att fungera som den ska. Det här problemet kommer att tas bort när vi närmar oss allmän tillgänglighet.



## <a name="next-steps"></a>Nästa steg

Följande artiklar är användbara för ytterligare information och scenarier när du använder dataflöden:

* [Dataförberedelser med självbetjäning för dataflöden](service-dataflows-overview.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden](service-dataflows-developer-resources.md)
* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Läs mer om Common Data Model-schemat och -entiteter på GitHub](https://github.com/Microsoft/CDM)

Relaterade artiklar i Power BI Desktop:

* [Ansluta till datauppsättningar i Power BI-tjänsten från Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Frågeöversikt i Power BI Desktop](desktop-query-overview.md)

Relaterade artiklar för Power BI-tjänsten:
* [Konfigurera schemalagd uppdatering](../connect-data/refresh-scheduled-refresh.md)
