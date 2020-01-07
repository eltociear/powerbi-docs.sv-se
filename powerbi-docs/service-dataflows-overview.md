---
title: Lär dig mer om dataflöden i Power BI
description: Lär dig hur dataflöden fungerar i Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/01/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 28be15b1f62f410c14faaa5d3e8c36060596c466
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "73872593"
---
# <a name="self-service-data-prep-in-power-bi"></a>Dataförberedelser med självbetjäning i Power BI

Allt eftersom att datavolymerna fortsätter att växa, ökar utmaningen att omvandla dessa data till välstrukturerad och användbar information. Vi vill ha data som är redo för analys, samt kunna uppdatera visuella objekt, rapporter och instrumentpaneler så att vi kan snabbt kan omvandla våra datavolymer till åtgärdsinriktade insikter. Med **dataförberedelser med självbetjäning** för stordata i Power BI kan du gå från data till Power BI-insikter med bara några klick.

![Använda dataflöden i Power BI](media/service-dataflows-overview/powerbi-dataflows_01.png)

Power BI introducerar **dataflöden** som hjälper organisationer att samla data från olika källor och förbereda den för modellering. Analytiker kan enkelt skapa dataflöden, med välbekanta självbetjäningsverktyg. Dataflöden används för att mata in, transformera, integrera och utöka stordata genom att definiera anslutningar till datakällor, ETL-logik, uppdateringsscheman med mera. Dessutom innebär den nya modelldrivna beräkningsmotorn som ingår i dataflöden att processen för förberedelse av data blir mer hanterbar, mer deterministisk och mindre besvärlig för dataanalytiker och rapportskapare. På liknande sätt som kalkylblad hanterar omberäkningar för alla berörda formler, hanterar dataflöden ändringar i en entitet eller ett dataelement åt dig, automatiserar uppdateringar och underlättar det som brukade vara tidskrävande logikkontroller även för grundläggande datauppdateringar. Med dataflöden kan uppgifter som tidigare krävde övervakning av dataforskare (vilket tog många timmar eller dagar), nu hanteras med några få klick av analytiker och rapportskapare. 

Data lagras som entiteter i [**Common Data Service**](https://docs.microsoft.com/powerapps/common-data-model/overview) i Azure Data Lake Storage Gen2. Du skapar och hanterar dataflöden på arbetsytor med hjälp av Power BI-tjänsten.  
 
**Dataflöden** är utformade att använda **Common Data Service**, en standardiserad, modulär och utökningsbar samling av datascheman som publicerats av Microsoft och som gör det enklare för dig att skapa, använda och analysera data. Med den här modellen kan du gå från datakällor till Power BI-instrumentpaneler utan problem.

Du kan använda dataflöden till att mata in data från en stor och växande uppsättning med lokala och molnbaserade datakällor, inklusive Dynamics 365, Salesforce, Azure SQL Database, Excel, SharePoint med flera.

Du kan därefter mappa data till standardentiteter i Common Data Service, ändra och utöka befintliga entiteter, samt skapa anpassade entiteter. Avancerade användare kan skapa helt anpassade dataflöden som använder självbetjäning utan kod eller med lite kod och inbyggd Power Query-redigering. Detta liknar den Power Query-upplevelse som miljontals användare av Power BI Desktop och Excel redan känner till.  

När du har skapat ett dataflöde kan du använda Power BI Desktop och Power BI-tjänsten till att skapa datamängder, rapporter, instrumentpaneler och appar som använder Common Data Service för att ge dig mer information om din verksamhet. 

Dataflödets uppdateringsschema hanteras direkt från arbetsytan där ditt dataflöde skapades, precis som dina datamängder. 

## <a name="how-dataflows-work"></a>Så här fungerar dataflöden

Här följer några exempel på hur du kan använda dataflöden:

* Organisationer kan mappa sina data till standardentiteter i Common Data Service eller skapa egna anpassade entiteter. Dessa entiteter kan sedan användas som byggblock när man vill skapa rapporter, instrumentpaneler och appar som fungerar direkt. Därefter kan de distribueras till användarna i organisationen. 

* Med den omfattande samlingen dataanslutningar för Microsoft kan organisationer ansluta sina egna datakällor till dataflöden, och använda Power Query till att mappa data från dess ursprung till Power BI. När dessa data har importerats av ett dataflöde (och uppdaterats med en angiven frekvens), kan entiteterna i dataflödet användas i Power BI Desktop-programmet för att skapa rapporter och instrumentpaneler. 

## <a name="how-to-use-dataflows"></a>Så här använder du dataflöden

I föregående avsnitt beskrevs några olika sätt som dataflöden kan användas på för att snabbt skapa kraftfulla analyser i Power BI. I det här avsnittet får du en genomgång av hur snabbt du kan skapa insikter med hjälp av dataflöden i en organisation, få en snabb överblick över hur BI-tekniker kan skapa sina egna dataflöden, samt anpassa insikter för sin egen organisation.

> [!NOTE]
> Du måste ha ett betalt Power BI-konto för att kunna använda dataflöden, till exempel ett Power BI Pro- eller Power BI Premium-konto, men du debiteras inte separat för användning av dataflöden. 

### <a name="extend-the-common-data-model-for-your-business-needs"></a>Utöka den gemensamma datamodellen för dina affärsbehov
För organisationer som vill utöka sin Common Data Service, kan dataflöden underlätta för Business Intelligence-personal vid anpassning av standardentiteter eller när man skapar nya. Den här självbetjäningsmetoden för att anpassa datamodellen kan sedan användas med dataflöden för att skapa appar och Power BI-instrumentpaneler som är skräddarsydda för organisationen.

### <a name="define-dataflows-programmatically"></a>Definiera dataflöden programmässigt
Du kanske också vill utveckla dina egna programmässiga lösningar och skapa dataflöden. Med offentliga API:er och möjligheten att programmässigt skapa anpassade definitionsfiler (model.json) för dataflödet, kan du skapa en anpassad lösning som passar din organisations unika data och analysbehov. 

Med offentliga API:er kan utvecklare enkelt och smidigt interagera med Power BI och dataflöden.

### <a name="extend-your-capabilities-with-azure"></a>Utöka dina möjligheter med Azure
Azure Data Lake Storage Gen2 ingår i varje betald Power BI-prenumeration (10 GB per användare, 100 TB per P1-nod). Det är därför enkelt att komma igång med dataförberedelserna med självbetjäning i Azure Data Lake. 

Power BI kan konfigureras till att lagra dataflödesdata på din organisations Azure Data Lake Storage Gen2-konto. När Power BI är anslutet till en Azure-prenumeration kan datautvecklare och dataforskare använda sig av kraftfulla Azure-produkter, som t.ex. Azure Machine Learning, Azure Databricks, Azure Data Factory med flera.

Power BI kan också ansluta till mappar med schematiserade data i Common Data Service-format, som lagras på din organisations Azure Data Lake Storage-konto. Dessa mappar kan skapas av tjänster, som exempelvis Azure-datatjänster. Genom att ansluta till dessa mappar kan analytiker sömlöst arbeta med dessa data i Power BI. 

Läs mer om Azure Data Lake Storage Gen2 och dataflödesintegration, inklusive hur du skapar dataflöden som finns i din organisations Azure Data Lake i [dataflöden och Azure Data Lake-integration (förhandsversion)](service-dataflows-azure-data-lake-integration.md).

## <a name="dataflow-capabilities-on-power-bi-premium"></a>Dataflödesfunktioner i Power BI Premium

För att dataflödesfunktioner och arbetsbelastningar ska fungera i en Power BI Premium-prenumeration, måste dataflödets arbetsbelastning för Premium-kapaciteten vara aktiverad. I följande tabell beskrivs dataflödesfunktioner och deras kapacitet när du använder ett Power BI Pro-konto, samt hur det skiljer sig mot att använda Power BI Premium.


|Dataflödesfunktioner | Power BI Pro |   Power BI Premium |
|---------|---------|---------|
|Schemalagd uppdatering| 8 per dag|  48|
|Totalt lagringsutrymme| 10 GB/användare  |100 TB/nod|
|Dataflödesredigering med Power Query Online|    +   |+|
|Hantering av dataflöden i Power BI|   +|  +|
|Dataanslutning för dataflöden i Power BI Desktop|  +|  +|
|Integrering med Azure|    +|  +|
|Beräknade entiteter (i lageromvandlingar via M) | |   +|
|Nya anslutningsappar|    +|  +|
|Inkrementell uppdatering av dataflöden|  |   +|
|Körs med Power BI Premium-kapacitet / parallellkörning av transformeringar|   |   +|
|Länkade entiteter för dataflöden| |        +|
|Standardiserat schema / inbyggt stöd för Common Data Service|  +|  +|

Mer information om hur du aktiverar dataflödesarbetsbelastningar för premiumkapacitet finns i [Konfigurera arbetsbelastningar i en Premium-kapacitet](service-admin-premium-workloads.md). Dataflödets arbetsbelastningar är inte tillgängliga i multi-geo-kapaciteter.

## <a name="summary-of-self-service-data-prep-for-big-data-in-power-bi"></a>Sammanfattning av dataförberedelser med självbetjäning för stordata i Power BI
Som nämnts tidigare i den här artikeln finns det många scenarier och exempel där **dataflöden** kan ge dig bättre kontroll – och snabbare insikter – från dina affärsdata. Med hjälp av en standarddatamodell (schema) som definieras av Common Data Service, kan du med dataflöden importera dina viktiga affärsdata och ha datan redo för modellering och skapande av BI-insikter på kortare tid ... vilket tidigare brukade ta månader eller ännu längre tid att åstadkomma. 

Genom att lagra affärsdata i ett standardiserat format från **Common Data Service**, kan BI-experter (eller utvecklare) skapa appar som genererar snabba, enkla och automatiska visuella objekt och rapporter. De innefattar, men är inte begränsade till att:


* Mappa dina data till standardentiteter i Common Data Service för att samla data och använda välkända metoder till att skapa färdiga insikter
* Skapa dina egna anpassade entiteter för att samla data från hela organisationen 
* Använda och uppdatera **externa data** som en del av ett dataflöde och aktivera import av dessa data i analyssyfte
* Kom igång med dataflöden för utvecklare


## <a name="next-steps"></a>Nästa steg

I den här artikeln finns en översikt över dataförberedelser för självbetjäning för stordata i Power BI och de många användningssätt som finns. Följande artiklar går in mer i detalj på vanliga användningsscenarier för dataflöden. 

* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden](service-dataflows-developer-resources.md)
* [Dataflöden och Azure Data Lake-integrering](service-dataflows-azure-data-lake-integration.md)

Mer information om Power Query och schemalagd uppdatering finns i följande artiklar:
* [Frågeöversikt i Power BI Desktop](desktop-query-overview.md)
* [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)

