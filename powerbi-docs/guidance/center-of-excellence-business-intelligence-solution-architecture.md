---
title: BI-lösningsarkitektur i Center of Excellence
description: Lär dig vad du bör tänka på när du designar och utvecklar en robust BI-plattform.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 81dda3c2bc3558ba68a16ee3f3070e748f76f15b
ms.sourcegitcommit: 561f6de3e4621d9d439dd54fab458ddca78ace2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "85940352"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>BI-lösningsarkitektur i Center of Excellence

Den här artikeln vänder sig till IT-experter och IT-chefer. Du lär dig mer om BI-lösningsarkitekturen i COE och de olika tekniker som används. Tekniker inkluderar Azure, Power BI och Excel. De kan utnyttjas tillsammans för att ge en skalbar och datadriven BI-molnplattform.

Att designa en robust BI-plattform kan liknas vid att bygga en bro som förbinder transformerade och berikade källdata med datakonsumenter. Designen av en sådan komplex struktur kräver ett tekniskt tänkesätt men kan vara en av de mest kreativa och inspirerande IT-arkitekturer som du kan utforma.

Plattformen måste stödja specifika krav. Närmare bestämt måste den skalas och prestera enligt förväntningarna från företagstjänster och datakonsumenter. Samtidigt måste den vara helt säker. Och den ska vara tillräckligt motståndskraftig för att anpassas efter förändringar, eftersom nya data och ämnesområden garanterat måste föras online framöver.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="En bild som visar ett diagram av en BI-plattformsarkitektur, från datakällor till datainmatning, stordata, datalager, informationslager, rapportering och maskininlärning.":::

## <a name="frameworks"></a>Ramverk

På Microsoft införde vi redan från början en systemliknande metod genom att investera i ramverksutveckling. Tekniska och affärsmässiga processramverk ökar åter användningen av design och logik och ger ett enhetligt resultat. De erbjuder även flexibilitet i arkitekturen genom att utnyttja många tekniker, och de effektiviserar och minskar tekniskt merarbete tack vare upprepningsbara processer.

Vi har lärt oss att väldesignade ramverk ger bättre insyn i dataursprung, påverkansanalys, underhåll av affärslogik, hantering av taxonomier och effektivisering av styrning. Utvecklingen blev dessutom snabbare, och samarbetet mellan stora team blev mer responsivt och effektivt.

Vi beskriver flera av våra ramverk i den här artikeln.

## <a name="data-models"></a>Datamodeller

Datamodeller ger dig kontroll över hur data struktureras och används. För företagstjänster och datakonsumenter är datamodeller gränssnittet gentemot BI-plattformen.

En BI-plattform kan leverera tre olika typer av modeller:

- Företagsmodeller
- BI-modeller
- Maskininlärningsmodeller (ML)

### <a name="enterprise-models"></a>Företagsmodeller

**Företagsmodeller** skapas och underhålls av IT-arkitekter. De kallas ibland dimensionella modeller eller ”data marts”. Data lagras vanligtvis i relationsformat som dimensions- och faktatabeller. Dessa tabeller lagrar rensade och berikade data som samlats från flera system, och de utgör en auktoritativ källa för rapportering och analys.

Företagsmodeller levererar en konsekvent och enskild datakälla för rapportering och BI. De skapas en gång och delas som en företagsstandard. Styrningsprinciper säkerställer att data skyddas, så att åtkomsten till känsliga datamängder – till exempel kundinformation eller ekonomi – begränsas enligt behov. De tillämpar namngivningskonventioner som garanterar konsekvens, vilket ytterligare upprättar trovärdigheten för data och kvalitet.

På en BI-molnplattform kan företagsmodeller distribueras till en [Synapse SQL-pool i Azure Synapse](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse). Synapse SQL-poolen blir då den enda versionen av sanningen, som organisationen kan räkna med för snabba och robusta insikter.

### <a name="bi-models"></a>BI-modeller

**BI-modeller** representerar ett semantiskt lager ovanpå företagsmodeller. De skapas och underhålls av BI-utvecklare och företagsanvändare. BI-utvecklare skapar BI-kärnmodeller som hämtar data från företagsmodeller. Företagsanvändare kan skapa oberoende modeller i mindre skala, eller så kan de utöka BI-kärnmodeller med avdelningskällor eller externa källor. BI-modeller fokuserar ofta på ett enda ämnesområde och delas ofta bland många parter.

Affärsfunktioner möjliggörs inte endast av data, utan av BI-modeller som beskriver begrepp, relationer, regler och standarder. På så sätt representerar de intuitiva och lättförståeliga strukturer som definierar datarelationer och kapslar in affärsregler som beräkningar. De kan även framtvinga detaljerade databehörigheter och därmed se till att rätt personer får åtkomst till rätt data. En viktig punkt är att de påskyndar frågeprestanda och ger mycket responsiva interaktiva analyser – till och med över terabyte med data. Precis som företagsmodeller antar BI-modeller namngivningskonventioner som säkerställer konsekvens.

På en BI-molnplattform kan BI-utvecklare distribuera BI-modeller till [Azure Analysis Services](/azure/analysis-services/) eller [Power BI Premium-kapaciteter](../admin/service-premium-what-is.md#dedicated-capacities). Vi rekommenderar att du distribuerar till Power BI när det används som rapporterings- och analyslager. Dessa produkter stöder olika lagringslägen, vilket gör att datamodellstabeller kan cachelagra sina data eller använda [DirectQuery](directquery-model-guidance.md), en teknik som skickar frågor till den underliggande datakällan. DirectQuery är ett idealiskt lagringsläge när modelltabeller representerar stora datavolymer eller om det finns behov av att leverera resultat i nära realtid. De två lagringslägena kan kombineras: [Sammansatta modeller](composite-model-guidance.md) kombinerar tabeller som använder olika lagringslägen till en enda modell.

För modeller som det körs många frågor till kan [Azure Load Balancer](/azure/load-balancer/load-balancer-overview) användas för att fördela frågebelastningen jämnt bland modellrepliker. Detta gör även att du kan skapa program och skapa BI-modeller med hög tillgänglighet.

<!-- For more information on BI models, see [BI modeling and processing in the COE](https://TODO/).-->

### <a name="machine-learning-models"></a>Maskininlärningsmodeller

[**Maskininlärningsmodeller (ML)** ](/windows/ai/windows-ml/what-is-a-machine-learning-model) skapas och underhålls av dataforskare. De utvecklas främst från råa källor i datasjön.

Tränade ML-modeller kan avslöja mönster i dina data. I många fall kan dessa mönster användas för att göra förutsägelser som kan användas för att berika data. Till exempel kan köpbeteenden användas till att förutsäga kundomsättning eller segmentera kunder. Förutsägelseresultat kan läggas till i företagsmodeller för att möjliggöra analys per kundsegment.

På en BI-molnplattform kan du använda [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) för att träna, distribuera, automatisera, hantera och spåra ML-modeller.

## <a name="data-warehouse"></a>Informationslager

I hjärtat hos en BI-plattform finns informationslagret, som är värd för dina företagsmodeller. Det är en källa till sanktionerade data – som registersystem och hubb – som betjänar företagsmodeller för rapportering, BI och dataforskning.

Många affärstjänster, däribland verksamhetsspecifika program (LOB), kan förlita sig på informationslagret som en auktoritativ och styrd källa till företagskunskaper.

Hos Microsoft hanteras vårt informationslager på [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) och Azure Synapse Analytics.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="En bild visar Azure Synapse Analytics som ansluter till Azure Data Lake Storage Gen2.":::

- **ADLS Gen2** gör Azure Storage till grunden för att skapa företagsdatasjöar i Azure. Det är utformat för att betjäna flera petabyte med information samtidigt som dataflöden på hundratals gigabit upprätthålls. Det erbjuder även lagringskapacitet och transaktioner till låga kostnader. Dessutom stöder det Hadoop-kompatibel åtkomst, vilket gör att du kan hantera och komma åt data precis som med ett Hadoop Distributed File System (HDFS). Faktum är att [Azure HDInsight](/azure/hdinsight/), [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) och Azure Synapse Analytics kan komma åt data som lagras i ADLS Gen2. På en BI-plattform är det därför ett bra val att lagra råa källdata, halvbehandlade eller mellanlagrade data samt produktionsfärdiga data. Vi använder den för att lagra alla våra affärsdata.
- **Azure Synapse Analytics** är en analystjänst som sammanför informationslager i företagsklass och stordataanalys. Det ger dig friheten att fråga efter data på dina villkor, med hjälp av antingen serverlösa resurser på begäran eller etablerade resurser – i stor skala. Synapse SQL, en komponent i Azure Synapse Analytics, stöder fullständig T-SQL-baserad analys. Det är därför utmärkt som värd för företagsmodeller som omfattar dina dimensions- och faktatabeller. Tabeller kan effektivt läsas in från ADLS Gen2 med enkla [PolyBase T-SQL](/sql/relational-databases/polybase/polybase-guide)-frågor. Då får du kraften från [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) för att köra analys med höga prestanda.

### <a name="business-rules-engine-framework"></a>Business Rules Engine-ramverket

Vi har utvecklat ett **Business Rules Engine-ramverk** (BRE) för att katalogisera affärslogik som kan implementeras i informationslagerskiktet. En BRE kan betyda många saker, men när det gäller informationslager är den användbar för att skapa beräknade kolumner i relationstabeller. Dessa beräknade kolumner representeras vanligtvis som matematiska beräkningar eller uttryck med hjälp av villkorliga uttryck.

Avsikten är att separera affärslogik från BI-kärnkod. Traditionellt brukar affärsregler hårdkodas i lagrade SQL-procedurer, vilket ofta gör att det krävs mycket underhållsarbete när affärsbehoven förändras. I en BRE definieras affärsregler en gång och används flera gånger när de tillämpas på olika informationslagerentiteter. Om beräkningslogiken behöver ändras behöver den bara uppdateras på ett ställe, inte i flera lagrade procedurer. Det finns till fördel: BRE-ramverk främjar transparens och insyn i den implementerade affärslogiken, som kan tillgängliggöras via en uppsättning rapporter som skapar självuppdaterande dokumentation.

## <a name="data-sources"></a>Datakällor

Informationslager kan konsolidera data från i stort sett alla datakällor. De skapas mestadels ovanpå LOB-datakällor, vilka ofta är relationsdatabaser som lagrar ämnesspecifik information för försäljning, marknadsföring, ekonomi och så vidare. Dessa databaser kan vara molnbaserade eller kan hanteras lokalt. Andra datakällor kan vara filbaserade, särskilt webbloggar eller IOT-data som hämtas från enheter. Dessutom kan data hämtas från SaaS-leverantörer (programvara som en tjänst).

Vissa av våra interna system på Microsoft skickar driftsdata direkt till ADLS Gen2 med hjälp av RAW-filformat. Utöver vår datasjö omfattar andra källsystem relationella LOB-program, Excel-arbetsböcker, andra filbaserade källor samt huvuddatahantering (MDM, Master Data Management) och anpassade datalagringsplatser. MDM-lagringsplatser gör att vi kan hantera våra huvuddata för att säkerställa auktoritativa, standardiserade och validerade versioner av data.

## <a name="data-ingestion"></a>Datainhämtning

Med jämna mellanrum och enligt verksamhetens aktivitet matas data in från källsystemen och läses in i informationslagret. Det kan vara en gång om dagen eller oftare. Datainmatning handlar om att extrahera, transformera och läsa in data. Eller kanske sker det åt andra hållet: extrahera, läsa in och sedan transformera data. Skillnaden handlar om den plats där transformeringen sker. Transformeringar används för att rensa, anpassa, integrera och standardisera data. Mer information finns i [Extrahering, transformering och inläsning (ETL)](/azure/architecture/data-guide/relational-data/etl).

Det slutgiltiga målet är att läsa in rätt data i din företagsmodell så snabbt och effektivt som möjligt.

På Microsoft använder vi [Azure Data Factory](/azure/data-factory/introduction) (ADF). Tjänsterna används för att schemalägga och dirigera datavalideringar, transformeringar och massinläsningar från externa källsystem till vår datasjö. Detta hanteras av anpassade ramverk för bearbetning av data parallellt och i stor skala. Dessutom vidtas omfattande loggning för att stödja felsökning och prestandaövervakning samt för att utlösa aviseringsmeddelanden när vissa villkor uppfylls.

Under tiden utför [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) – en Apache Spark-baserad analysplattform som är optimerad för Azure-plattformen för molntjänster – transformeringar särskilt för dataforskning. Den skapar och kör även ML-modeller med hjälp av Python-anteckningsböcker. Poäng från dessa ML-modeller läses in i datalagret för att integrera förutsägelser med företagsprogram och rapporter. Eftersom Azure Databricks kommer åt datasjöfilerna direkt eliminerar eller minimerar det behovet av att kopiera eller införskaffa data.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="En bild visar Azure Data Factory som hämtar data och orkestrerar datapipelines med Azure Databricks via Azure Data Lake Storage Gen2.":::

### <a name="ingestion-framework"></a>Datainmatningsramverk

Vi har utvecklat ett **datainmatningsramverk** som en uppsättning konfigurationstabeller och procedurer. Det stöder en datadriven metod för att förvärva stora mängder data vid hög hastighet och med minimal kod. I korthet förenklar detta ramverk datahämtningsprocessen för inläsning av informationslagret.

Ramverket använder konfigurationstabeller som lagrar information gällande datakälla och datamål, till exempel källtyp, server, databas, schema och tabellrelaterad information. Den här designmetoden innebär att vi inte behöver utveckla specifika ADF-pipelines eller [SSIS-paket (SQL Server Integration Services)](/sql/integration-services/sql-server-integration-services). I stället skrivs procedurer på det språk vi väljer för att skapa ADF-pipelines som genereras och körs dynamiskt vid körning. Datainsamling blir därför en konfigurationsaktivitet som enkelt kan operationaliseras. Traditionellt sett skulle det krävas omfattande utvecklingsresurser för att skapa hårdkodade ADF- eller SSIS-paket.

Datainmatningsramverket utformades även i syfte att förenkla processen med att hantera ändringar i överordnade källscheman. Det är enkelt att uppdatera konfigurationsdata – manuellt eller automatiskt – när schemaändringar identifieras för att samla in nyligen tillagda attribut i källsystemet.

### <a name="orchestration-framework"></a>Orkestreringsramverk

Vi har utvecklat ett **orkestreringsramverk** för att operationalisera och orkestrera våra datapipelines. Det använder en datadriven design som är beroende av en uppsättning konfigurationstabeller. Dessa tabeller lagrar metadata som beskriver pipelineberoenden samt hur källdata ska mappas till måldatastrukturer. Investeringen i utvecklingen av detta anpassningsbara ramverk har gett avkastning – det finns inte längre något behov av att hårdkoda varje dataflytt.

## <a name="data-storage"></a>Datalagring

En datasjö kan lagra stora mängder rådata för senare användning tillsammans med mellanlagring av datatransformationer.

På Microsoft använder vi ADLS Gen2 som vår enda sanningskälla. Den lagrar rådata samt mellanlagrade data och produktionsfärdiga data. Den erbjuder en mycket skalbar och kostnadseffektiv datasjölösning för stordataanalys. Genom att kombinera kraften hos ett högpresterande filsystem med massiv skalning är den optimerad för arbetsbelastningar för dataanalys, vilket påskyndar tiden till insikter.

ADLS Gen2 ger det bästa av två världar: det är blob-lagring och en namnrymd för högpresterande filsystem som vi konfigurerar med detaljerade åtkomstbehörigheter.

Förfinade data lagras sedan i en relationsdatabas för att leverera ett högpresterande, mycket skalbart datalager för företagsmodeller med säkerhet, styrning och hanterbarhet. Ämnesspecifika ”data marts” lagras i Azure Synapse Analytics, som läses in med Azure Databricks- eller PolyBase T-SQL-frågor.

## <a name="data-consumption"></a>Dataförbrukning

I rapporteringslagret förbrukar företagstjänster företagsdata från informationslagret. De får även åtkomst till data direkt i datasjön för ad hoc-analys eller dataforskningsuppgifter.

Detaljerade behörigheter framtvingas i alla lager: i datasjön, företagsmodellerna och BI-modellerna. Behörigheterna säkerställer att datakonsumenter endast kan se de data som de har behörighet att komma åt.

Hos Microsoft använder vi Power BI-rapporter och instrumentpaneler samt [sidnumrerade Power BI-rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md). Vissa rapporter och ad hoc-analyser görs i Excel, särskilt vad gäller ekonomisk rapportering.

Vi publicerar dataordlistor, som innehåller referensinformation om våra datamodeller. De görs tillgängliga för våra användare så att de kan identifiera information om vår BI-plattform. I ordlistorna dokumenteras modelldesigner med beskrivningar av entiteter, format, struktur, dataursprung, relationer och beräkningar. Vi använder [Azure Data Catalog](/azure/data-catalog/overview) för att göra så att våra datakällor enkelt kan identifieras och förstås.

Vanligtvis skiljs dataförbrukningsmönster åt baserat på roll:

- **Dataanalytiker** ansluter direkt till BI-kärnmodeller. När BI-kärnmodeller innehåller alla data och all logik de behöver använder de live-anslutningar för att skapa Power BI-rapporter och instrumentpaneler. När de behöver utöka modellerna med avdelningsdata skapar de [sammansatta Power BI-modeller](composite-model-guidance.md). Om det finns ett behov av rapporter i kalkylbladsformat använder de Excel för att skapa rapporter baserade på BI-kärnmodeller eller BI-avdelningsmodeller.
- **BI-utvecklare** och författare av operativa rapporter ansluter direkt till företagsmodeller. De använder Power BI Desktop för att skapa analytiska rapporter med live-anslutning. De kan även skriva BI-rapporter av operationstyp som sidnumrerade Power BI-rapporter; de skriver interna SQL-frågor för att få åtkomst till data från Azure Synapse Analytics-företagsmodeller med hjälp av T-SQL eller Power BI-modeller via DAX eller MDX.
- **Dataforskare** ansluter direkt till datasjön. De använder Azure Databricks och Python-anteckningsböcker för att utveckla ML-modeller, som ofta är experimentella och kräver särskilda kunskaper för produktionsanvändning.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="En bild som visar användningen av Azure Synapse Analytics med Power BI och Azure Machine Learning.":::

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Enterprise BI i Azure med Azure Synapse Analytics](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
