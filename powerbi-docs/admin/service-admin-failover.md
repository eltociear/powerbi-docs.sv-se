---
title: Vanliga frågor och svar om hög tillgänglighet, redundans och haveriberedskap i Power BI
description: Få reda på hur Power BI-tjänsten ger hög tillgänglighet och verksamhetskontinuitet och haveriberedskap till användarna.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 3dd50d4f57b3146135cde5e91062ed3b2a0eecc1
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83128537"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Vanliga frågor och svar om hög tillgänglighet, redundans och haveriberedskap i Power BI

Den här artikeln beskriver hur Power BI-tjänsten ger hög tillgänglighet och verksamhetskontinuitet och haveriberedskap till användarna. När du har läst den här artikeln bör du ha en bättre förståelse av hur hög tillgänglighet uppnås, under vilka omständigheter Power BI utför en redundansväxling och vad du kan förvänta dig av tjänsten när den växlar över.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Vad betyder hög tillgänglighet för Power BI?

Power BI är en fullständigt hanterad programvara som en tjänst (SaaS).  Microsoft utformar och driver den så att den är motståndskraftig mot infrastrukturfel och användarna alltid kan komma åt deras rapporter.  Tjänsten stöds av ett [99,9 % serviceavtal](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>Vad är Power BI-redundans?

Power BI har flera instanser av varje komponent i Azure-datacenter (så kallade regioner) för att garantera verksamhetskontinuitet. Om det är avbrott eller finns ett problem som gör så att Power BI är otillgänglig eller inte fungerar i en region växlar Power BI alla komponenter i den regionen till en backup-instans. Redundansväxlingen återställer tillgängligheten och funktionaliteten i Power BI-tjänstinstansen i en ny region (normalt inom samma geografiska plats, som anges i [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

En redundansväxlad Power BI-tjänstinstans stöder bara _läsåtgärder_, vilket betyder att följande åtgärder inte stöds vid redundansväxling: uppdateringar, rapportpublicering, instrumentpanel- eller rapportändringar och andra åtgärder som kräver ändringar av Power BI-metadata (till exempel infoga kommentar i en rapport).  Läsåtgärder, till exempel visning av instrumentpaneler och rapporter (som inte baseras på Direct Query eller Live Connect för lokala datakällor) fortsätter att fungera normalt.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Hur synkroniseras backup-instanser med mina data?

Alla komponenter i Power BI-tjänsten synkroniserar regelbundet sina backup-instanser. Vi riktar in oss på en 15-minuters tidpunktssynkronisering för allt innehåll som laddats upp till eller ändrats i Power BI. Vid redundans använder Power BI [geo-redundant replikering för Azure Storage](/azure/storage/common/storage-redundancy-grs) och [geo-redundant replikering för Azure SQL](/azure/sql-database/sql-database-active-geo-replication) för att garantera att backup-instanser finns i andra regioner och kan användas vid redundansväxling.

## <a name="where-are-the-failover-clusters-located"></a>Var finns redundansklustren?

Backup-instanser finns inom samma geografiska region (geo) som du har valt när organisationen registrerade sig för Power BI, förutom där det noteras i [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). En geo kan innehålla flera regioner, och Microsoft kan replikera data i någon av regionerna inom en viss geo för dataåterhämtning. Microsoft replikerar inte och flyttar inte kundinformation utanför geo-regionen. En mappning av geo-regioner som tillhandahålls av Power BI och regionerna inom dem finns i [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-failover"></a>Hur bestämmer sig Microsoft för redundansväxling?

Det finns två olika system som anger när en redundansväxling kan krävas:

- Våra externa och interna övervakningsavsökningar anger brist på tillgänglighet eller oförmåga att fungera korrekt. Sådana indikationer kan baseras på avbrott som identifierats i Power BI-komponenter eller en eller flera av tjänsterna som Power BI är beroende av i en region.
- Det centrala driftsteamet på Microsoft Azure informerar oss om ett kritiskt avbrott i en region.

I båda fallen fattar Power BI-ledningen beslutet att redundansväxla. Själva beslutet är inte automatiskt. När beslutet har fattats sker redundansväxlingen automatiskt.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Hur vet jag att Power BI är i redundansläge?

Ett meddelande publiceras på Power BI-supportsidan ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). Meddelandet innehåller de stora åtgärder som inte är tillgängliga under redundansen, som publicera, uppdatera, skapa instrumentpanel, duplicera instrumentpanel och ändra behörighet.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Hur lång tid tar det för Power BI att redundansväxla?

När det har fastställts att en redundansväxling krävs tar det cirka 15 minuter innan Power BI fungerar igen. Tiden för att fastställa att en redundansväxling krävs varierar beroende på vilket scenario som slutat fungera. 

När en redundansväxling har utförts använder Power BI Azure Storage GEO-replikering för att utföra redundansväxlingen. Sådana replikeringar har vanligtvis en återställningstid på 15 minuter, men [Azure Storage garanterar inte denna tidsram](https://docs.microsoft.com/azure/storage/common/storage-redundancy) i ett serviceavtal, och därför kan inte heller Power BI garantera någon tidsram. 


## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>När återgår min Power BI-instans till den ursprungliga regionen?

Power BI-tjänstinstanser återgår till sin ursprungliga region när problemet som orsakade redundansen har åtgärdats. Se Power BI-supportsidan: När problemet har lösts tar Power BI-teamet bort meddelandet som beskriver redundansen. Då bör alla åtgärder fungera normalt.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Ansvarar jag för min Power BI-lösnings tillgänglighet?

Om den Power BI-lösning som används i organisationen involverar något av följande element måste du vidta vissa åtgärder för att garantera att lösningen behåller sin höga tillgänglighet:

- Om organisationen använder Power BI Premium måste du se till att Premium-kapaciteten har en storlek som uppfyller belastningsbehoven för din distribution.  I dokumentet [Power BI Premium Planning and Deployment](https://aka.ms/Premium-Capacity-Planning-Deployment) (Planering och distribution av Power BI Premium) och [Power BI Premium Capacity Metrics-appen](service-admin-premium-monitor-capacity.md) kan du få hjälp att planera och uppfylla det här kravet. Vi lägger regelbundet till nya funktioner i måttappen och administratörsportalen i Power BI som hjälp.
- Om organisationen har åtkomst till datakällor med hjälp av den lokala datagatewayen måste du konfigurera gatewayen [enligt beskrivningen i den här artikeln](/data-integration/gateway/service-gateway-high-availability-clusters) för att stödja hög tillgänglighet. Följ den här vägledningen oavsett om du uppdaterar rapporter i importläge eller om du använder data eller datamodeller med hjälp av DirectQuery eller Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>Fungerar gatewayer i redundansläge?

Nej. Data som krävs från lokala datakällor (alla rapporter och instrumentpaneler som baseras på Direct Query och Live Connect) fungerar inte vid redundans. Men gatewaykonfigurationen ändras inte: När Power BI-instansen återgår till dess ursprungliga tillstånd återgår gatewayer till normala funktioner.
