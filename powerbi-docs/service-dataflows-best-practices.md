---
title: Metodtips för Power BI-dataflöden
description: Metodtips för Power BI-dataflöden
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c5aeb74277379b46398dc709f5deda1d10dc0926
ms.sourcegitcommit: 7eb74b060de080152c190ac7eb6b64767f8d6626
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/11/2019
ms.locfileid: "70919554"
---
# <a name="dataflows-best-practice"></a>Metodtips för dataflöden

Den här artikeln innehåller metodtips för att utforma rapporter i Power BI. Du kan använda den här vägledningen för att lära dig hur du skapar dataflöden och tillämpa dessa metoder på din egen data flöden.

> [!NOTE]
> Rekommendationerna i den här artikeln är riktlinjer. För varje metodtips i den här artikeln kan det finnas giltiga skäl att avvika från vägledningen. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Dela inmatning och transformering för att använda den förbättrade motorn

När du skapar dataflöden kanske du frestas att skapa ett enda dataflöde med alla enheter, transformeringar, kopplingar och förbättringar på en och samma plats. För mindre datauppsättningar kan ett enda flöde vara lämpligt. Men när du hanterar större datavolymer kan det ibland uppstå begränsningar eller minnesgränser när du utför kopplingar eller vissa transformeringar. För att lösa dessa problem har en förbättrad motor lanserats för Power BI Premium-användare som använder mycket större datauppsättningar. Den förbättrade beräkningsmotorn fungerar enbart mot länkade eller beräknade entiteter. Om du skapar ett separat dataflöde för inmatning och ett länkat dataflöde för att utföra alla komplexa sammanslagningar och transformeringar kan detta gynnas av den förbättrade motorn.

Att dela upp dataflöden är också fördelaktigt för att diagnostisera och felsöka uppdateringsproblem, särskilt när du arbetar med källor som har nätverksbegränsningar.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Utför åtgärder som kan använda den förbättrade beräkningsmotorn

Se till att du använder den förbättrade beräkningsmotorn genom att kontrollera att du först utför kopplingar och filtrertransformationer i en beräknad entitet innan du utför andra typer av transformationer.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Dela dataflöden vid anslutning till SharePoint

När du arbetar med SharePoint och ansluter till flera filer kan sporadiska problem uppstå. SharePoint begränsar begäranden för att bibehålla sin pålitlighet och svarskapacitet. Därför kan det vara lockande att hämta alla filer i ett enda dataflöde när du ansluter till Excel-filer från SharePoint. Om du hämtar fler än 20 filer kan du skapa två eller fler dataflöden för att dela upp uppdateringsbelastningen och lösa SharePoint-begränsningen.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Undvik schemalagd uppdatering för länkade entiteter på samma arbetsyta

Om du regelbundet är utelåst från dina dataflöden som innehåller länkade entiteter kan det bero på att motsvarande och beroende dataflöden i samma arbetsyta är låsta under dataflödesuppdateringen. Denna låsning säkerställer transaktionens exakthet och att både dataflöden har uppdaterats men kan hindra dig från att redigera. 

Om du ställer in ett separat schema för det länkade dataflödet kan dataflöden uppdateras i onödan och hindra dig från att redigera dataflödet. Det finns två rekommendationer för att undvika det här problemet: 

* Undvik att ange ett uppdateringsschema för ett länkat dataflöde på samma arbetsyta som källdataflödet
* Om du vill konfigurera ett uppdateringsschema separat och vill undvika låsningsbeteendet kan du avgränsa dataflödet i en separat arbetsyta.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Skapa en separat arbetsyta för inmatning, transformering

För att ge åtkomst till underliggande data från dataflöden till många användare utan att ge åtkomst till det underliggande källsystemets rådata skapar du en separat arbetsyta som innehåller alla data som du behöver dela och tilldelar behörigheter. Det finns för närvarande inte stöd för enskilda dataflödesbehörigheter.

### <a name="ensure-capacity-is-in-the-same-region"></a>Se till att kapaciteten finns i samma region

Data flöden stöder för närvarande inte flera geografiska områden. Premium-kapaciteten måste skapas i samma region som Power BI-klienten.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Skilj lokala källor från molnkällor

Utöver de föregående metodtipsen kan du skapa ett separat dataflöde för varje typ av källa, till exempel lokalt, moln, SQL Server, Spark, Dynamics och så vidare. Vi rekommenderar starkt att du delar ditt dataflöde efter typ av datakälla. En sådan delning efter källtyp underlättar snabb felsökning och förhindrar interna gränser när du uppdaterar din dataflöden.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Dela dataflöden i en separat kapacitet

Om du har nätverksbegränsningar eller fel ofta uppstår i dina dataflöden på grund av minnebegränsningar kan du dela dina dataflöden eller skala upp din Premium-kapacitet så att du får mer minne.

## <a name="next-steps"></a>Nästa steg

Den här artikeln tillhandahåller information om netodtips för dataflöden. För mer information om dataflöden kan följande artiklar vara till hjälp:

* [Dataförberedelser med självbetjäning för dataflöden](service-dataflows-overview.md)
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)

Information om CDM-utveckling och självstudieresurser finns i följande:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappar](https://go.microsoft.com/fwlink/?linkid=2045304)
* [CDM-modellfildefinition](https://go.microsoft.com/fwlink/?linkid=2045521)


Mer information om Power Query och schemalagd uppdatering finns i följande artiklar:
* [Frågeöversikt i Power BI Desktop](desktop-query-overview.md)
* [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md)
