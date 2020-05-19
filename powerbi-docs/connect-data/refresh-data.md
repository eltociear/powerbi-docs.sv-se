---
title: Datauppdatering i Power BI
description: Den här artikeln beskriver datauppdateringsfunktionerna i Power BI och deras beroenden på en konceptuell nivå.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 50d0cb1d31a6ec20db69c1b06aaf64f3eed727a2
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83310014"
---
# <a name="data-refresh-in-power-bi"></a>Datauppdatering i Power BI

Med Power BI kan du gå från data till insikt snabbt men du måste se till att data i dina Power BI-rapporter och -instrumentpaneler är aktuella. Att veta hur data ska uppdateras är ofta avgörande i att leverera korrekta resultat.

Den här artikeln beskriver datauppdateringsfunktionerna i Power BI och deras beroenden på en konceptuell nivå. Här ges också metodtips och andra tips på hur du undviker vanliga uppdateringsproblem. Innehållet lägger grunden så att du kan förstå hur datauppdatering fungerar. För riktade stegvisa instruktioner för att konfigurera datauppdatering kan du se självstudierna och instruktionsguiderna i avsnittet Nästa steg i slutet av den här artikeln.

## <a name="understanding-data-refresh"></a>Förstå datauppdatering

När du uppdaterar data måste Power BI fråga de underliggande datakällorna, möjligen läsa in källdata i en datauppsättning och sedan uppdatera visualiseringar i dina rapporter eller instrumentpaneler som förlitar sig på den uppdaterade datauppsättningen. Hela processen består av flera faser, beroende på datauppsättningarnas lagringslägen, enligt beskrivningen i följande avsnitt.

För att förstå hur Power BI uppdaterar dina datauppsättningar, rapporter och instrumentpaneler måste du känna till följande koncept:

- **Lagringsmodeller och datauppsättningstyper**: De lagringslägen och datauppsättningstyper som Power BI stöder har olika uppdateringskrav. Du kan välja mellan att importera data på nytt till Power BI för att se ändringar som har skett eller köra frågor på data direkt vid källan.
- **Power BI-uppdateringstyper**: Oavsett datauppsättningens egenskaper kan de olika uppdateringstyperna hjälpa dig att förstå var Power BI kan tillbringa sin tid under en uppdatering. Och genom att kombinera de här uppgifterna med egenskaperna för lagringsläge kan du förstå exakt vad Power BI utför när du väljer **Uppdatera nu** för en datauppsättning.

### <a name="storage-modes-and-dataset-types"></a>Lagringslägen och datauppsättningstyper

En Power BI-datauppsättning kan fungera i någon av följande lägen för att komma åt data från flera olika datakällor. Mer information finns i [lagringsläget i Power BI Desktop](../transform-model/desktop-storage-mode.md).

- Import-läge
- DirectQuery-läge
- LiveConnect-läge
- Push-läge

I följande diagram visas de olika dataflödena, utifrån lagringsläge. Den viktigaste punkten är att bara datauppsättningar i Import-läge kräver en källdatauppdatering. De kräver uppdatering eftersom det bara är den här typen av datauppsättning som importerar data från dess datakällor, och de importerade data kan uppdateras regelbundet och ad hoc. DirectQuery-datauppsättningar och datauppsättningar i LiveConnect-läge för Analysis Services importerar inte data. De frågar den underliggande datakällan med varje användaråtgärd. Datauppsättningar i push-läge kommer inte åt några datakällor direkt utan förväntar sig att du skickar data till Power BI. Kraven för datauppsättningsuppdatering varierar efter vilken lagringstyp/datauppsättningstyp som används.

![Lagringslägen och datauppsättningstyper](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Datauppsättningar i Import-läge

Power BI importerar data från den ursprungliga datakällan till datauppsättningen. Frågor för Power BI-rapporter och -instrumentpaneler som skickas till datauppsättningen returnerar resultat från de importerade tabellerna och kolumnerna. Du kan se en sådan datauppsättning som en tidpunktskopia. Eftersom Power BI kopierar data måste du uppdatera datauppsättningen så att den hämtar ändringar från de underliggande datakällorna.

Eftersom Power BI fångar data, kan storleken på en datauppsättning i Import-läge vara betydande. Se följande tabell för maximala datauppsättningsstorlekar per kapacitet. Håll dig betydligt under maxgränsen för datauppsättningsstorlekar för att undvika uppdateringsproblem som kan inträffa om datauppsättningarna kräver mer än maximalt tillgängliga resurser under en uppdatering.

| Kapacitetstyp | Maximal datauppsättningsstorlek |
| --- | --- |
| Delad, A1, A2 eller A3 | 1 GB |
| A4 eller P1 | 3 GB |
| A5 eller P2 | 6 GB |
| A6 eller P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>Datauppsättningar i DirectQuery-/LiveConnect-läge

Power BI importerar inte data via anslutningar som fungerar i DirectQuery-/LiveConnect-läge. I stället returnerar datauppsättningen resultat från den underliggande datakällan när en rapport eller instrumentpanel frågar datauppsättningen. Power BI omvandlar och vidarebefordrar frågorna till datakällan.

Trots att DirectQuery-läget och LiveConnect-läget liknar varandra på så sätt att Power BI vidarebefordrar frågorna till källan är det viktigt att notera att Power BI inte måste omvandla frågor i LiveConnect-läge. Frågorna går direkt till den Analysis Services-instans som är värd för databasen utan att förbruka resurser på delad kapacitet eller en Premium-kapacitet.

Eftersom Power BI inte importerar data behöver du inte köra en datauppdatering. Men Power BI utför fortfarande paneluppdateringar och möjligen rapportuppdateringar, som beskrivs i nästa avsnitt om uppdateringstyper. En panel är ett visuellt rapportobjekt fäst på en instrumentpanel och paneluppdateringar på instrumentpanelen sker ungefär varje timme så att de senaste resultaten visas på panelerna. Du kan ändra schemat i datauppsättningsinställningarna, som på skärmbilden nedan, eller tvinga fram en instrumentpanelsuppdatering manuellt med hjälp av alternativet **Uppdatera nu**.

![Uppdateringsschema](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> Avsnittet **Schemalagd cacheminnesuppdatering** på fliken **Datauppsättningar** är inte tillgänglig för datauppsättningar i Import-läge. Dessa datauppsättningar kräver inte en separat paneluppdatering eftersom Power BI uppdaterar panelerna automatiskt under varje schemalagd datauppdatering eller datauppdatering på begäran.

#### <a name="push-datasets"></a>Push-datauppsättningar

Push-datauppsättningar innehåller inte någon formell definition av en datakälla, så de kräver inte att du utför en datauppdatering i Power BI. Du uppdaterar dem genom att skicka data till datauppsättningen via en extern tjänst eller process, till exempel Azure Stream Analytics. Det här är en vanlig metod för realtidsanalys med Power BI. Power BI utför fortfarande cacheuppdateringar för paneler som används utöver en push-datauppsättning. En detaljerad genomgång finns i [Självstudie: Stream Analytics och Power BI: En instrumentpanel för analys i realtid för strömmande data](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> Push-läget har flera begränsningar som finns dokumenterade i [Power BI REST API-begränsningar](../developer/automation/api-rest-api-limitations.md).

### <a name="power-bi-refresh-types"></a>Power BI-uppdateringstyper

En Power BI-uppdatering kan bestå av flera uppdateringstyper, till exempel datauppdatering, OneDrive-uppdatering, uppdatering av frågecacheminnen, paneluppdatering och uppdatering av visuella rapportobjekt. Power BI avgör vilka uppdateringssteg som krävs för en viss datauppsättning automatiskt men du bör veta hur de bidrar till en uppdaterings komplexitet och varaktighet. En snabbguide finns i följande tabell.

| Lagringsläge | Datauppdatering | OneDrive-uppdatering | Frågecacheminnen | Paneluppdatering | Visuella rapportobjekt |
| --- | --- | --- | --- | --- | --- |
| Importera | Schemalagt och på begäran | Ja, för anslutna datauppsättningar | Om det har aktiverats på Premium-kapacitet | Automatiskt och på begäran | Nej |
| DirectQuery | Ej tillämpligt | Ja, för anslutna datauppsättningar | Om det har aktiverats på Premium-kapacitet | Automatiskt och på begäran | Nej |
| LiveConnect | Ej tillämpligt | Ja, för anslutna datauppsättningar | Om det har aktiverats på Premium-kapacitet | Automatiskt och på begäran | Ja |
| Push | Ej tillämpligt | Ej tillämpligt | Inte praktiskt | Automatiskt och på begäran | Nej |
| | | | | | |

#### <a name="data-refresh"></a>Datauppdatering

För Power BI-användare innebär uppdatering av data normalt att importera data från de ursprungliga datakällorna till en datauppsättning, antingen utifrån ett uppdateringsschema eller på begäran. Du kan utföra flera datauppsättningsuppdateringar dagligen, vilket kan vara nödvändigt om de underliggande källdata ändras ofta. Power BI begränsar datauppsättningar på delad kapacitet till åtta dagliga uppdateringar. Om datauppsättningen ligger i en Premium-kapacitet kan du schemalägga upp till 48 uppdateringar per dag i inställningarna för datamängden. Mer information finns i [Konfigurera schemalagd uppdatering](#configure-scheduled-refresh) senare i den här artikeln. Datauppsättningar på en Premium-kapacitet med [XMLA-slutpunkten ](../admin/service-premium-connect-tools.md) inställd på läs-/skrivbehörighet för obegränsade uppdateringsåtgärder när de konfigureras programmässigt med TMSL eller PowerShell.

Det är också viktigt att påpeka att begränsningen för dagliga uppdateringar i delade kapaciteter gäller för antalet schemalagda uppdateringar och API-uppdateringar tillsammans. Du kan också utlösa en uppdatering på begäran genom att välja **Uppdatera nu** i datamängdens meny, som i den här bilden. Uppdateringar på begäran räknas inte mot uppdateringsgränsen. Observera också att datamängder i Premium-kapaciteter inte har några begränsningar för API-uppdateringar. Om du vill skapa en egen uppdateringsläsning via REST-API:et för Power BI ska du läsa [Datamängder – Uppdatera datamängd](/rest/api/power-bi/datasets/refreshdataset).

![Uppdatera nu](media/refresh-data/refresh-now.png)

> [!NOTE]
> Datauppdateringar måste slutföras inom 2 timmar i delade kapaciteter. Om datauppsättningarna kräver längre uppdateringsåtgärder kan du flytta datauppsättningen till en Premium-kapacitet. På Premium är den maximala uppdateringsvaraktigheten 5 timmar.

#### <a name="onedrive-refresh"></a>OneDrive-uppdatering

Om du har skapat datauppsättningar och rapporter utifrån en Power BI Desktop-fil, Excel-arbetsbok eller en CSV-fil med kommaavgränsade värden (.csv) på OneDrive eller SharePoint Online utför Power BI en annan typ av uppdatering, en så kallad OneDrive-uppdatering. Mer information finns i [Hämta data från filer för Power BI](service-get-data-from-files.md).

Till skillnad från en datauppsättningsuppdatering där Power BI importerar data från en datakälla till en datauppsättning synkroniseras datauppsättningar och rapporter med sina källfiler vid OneDrive-uppdateringen. Som standard kontrollerar Power BI varje timme om en datauppsättning som är ansluten till en fil på OneDrive eller SharePoint Online kräver synkronisering.

> [!IMPORTANT]
> Var försiktig när du utför filhantering på OneDrive. När du anger en OneDrive-fil som data källa refererar Power BI till filens objekt-ID när den utför uppdateringen, vilket kan orsaka problem i vissa scenarier. Tänk dig ett scenario där du har en huvudfil, _A_, och en produktionskopia av filen _B_, och du konfigurerar OneDrive-uppdatering för fil B. Om du sedan _kopiera_ fil A över fil B tar kopiering åtgärden bort den gamla filen B och skapar en ny fil B med ett annat objekt-ID, vilket avbryter OneDrive-uppdateringen. I stället bör du ladda upp och ersätta fil B, så att du behåller samma objekt-ID.

Om du flyttar filen till en annan plats (till exempel genom att dra och släppa) fortsätter uppdateringen att fungera eftersom PBI fortfarande känner till fileID. Men om du kopierar filen till en annan plats skapas en ny instans av filen och en ny fileID. Det innebär att din Power BI-filreferens inte längre är giltig och att uppdateringen kommer att misslyckas.

Se OneDrive-fliken i uppdateringshistoriken om du vill granska tidigare synkroniseringscykler. På följande skärmbild visas en slutförd synkroniseringscykel för en exempeldatauppsättning.

![Uppdateringshistorik](media/refresh-data/refresh-history.png)

Som skärmbilden ovan visar har Power BI identifierat den här OneDrive-uppdateringen som en **schemalagd** uppdatering men det går inte att konfigurera uppdateringsintervallet. Du kan bara inaktivera OneDrive-uppdatering i datauppsättningens inställningar. Det är användbart att inaktivera uppdatering om du inte vill att dina datauppsättningar och rapporter i Power BI ska plocka upp några ändringar från källfilerna automatiskt.

Observera att datauppsättningens inställningssida bara visar avsnitten **OneDrive-autentiseringsuppgifter** och **OneDrive-uppdatering** om datauppsättningen är ansluten till en fil på OneDrive eller SharePoint Online, som på följande skärmbild. Datauppsättningar som inte är anslutna till källfil på OneDrive eller SharePoint Online visas inte i de här avsnitten.

![OneDrive-autentiseringsuppgifter och OneDrive-uppdatering](media/refresh-data/onedrive-credentials-refresh.png)

Om du inte inaktiverar OneDrive-uppdatering kan du fortfarande synkronisera datauppsättningen på begäran genom att välja **Uppdatera nu** i datauppsättningsmenyn. Som en del av på begäran-uppdateringen kontrollerar Power BI om källfilen på OneDrive eller SharePoint Online är nyare än datauppsättningen i Power BI och synkroniserar datauppsättningen om så är fallet. I **Uppdateringshistorik** listas aktiviteterna som på begäran-uppdateringar på **OneDrive**-fliken.

Tänk på att OneDrive-uppdatering inte hämta data från de ursprungliga datakällorna. OneDrive-uppdateringen uppdaterar bara resurserna i Power BI med metadata och data från .pbix-, .xlsx- eller .csv-filen, som följande diagram visar. För att säkerställa att datauppsättningen har den senaste informationen från datakällorna utlöser Power BI även en datauppdatering som en del av en på begäran-uppdatering. Du kan verifiera det här i **Uppdateringshistorik** om du växlar till fliken **Schemalagd**.

![Diagram över OneDrive-uppdatering](media/refresh-data/onedrive-refresh-diagram.png)

Om du håller OneDrive-uppdatering aktiverad för en OneDrive- eller SharePoint Online-ansluten datauppsättning och vill utföra datauppdatering schemalagt ser du till att konfigurera schemat så att Power BI utför datauppdateringen efter OneDrive-uppdateringen. Om du till exempel har skapat en egen tjänst eller process för att uppdatera källfilen på OneDrive eller SharePoint Online kl. 01:00 varje natt kan du konfigurera schemalagd uppdatering kl. 02:30 för att ge Power BI tillräckligt med tid att slutföra OneDrive-uppdateringen innan datauppdateringen startas.

#### <a name="refresh-of-query-caches"></a>Uppdatering av frågecacheminnen

Om datauppsättningen finns på en Premium-kapacitet kanske du kan förbättra prestandan för associerade rapporter och instrumentpaneler genom att aktivera frågecachelagring, som på följande skärmbild. Med cachelagring av frågor instrueras Premium-kapaciteten att använda den lokala cachelagringstjänsten för att bibehålla frågeresultat, så att inte den underliggande datakällan beräknar dessa resultat. Mer information finns i [Cachelagring av frågor i Power BI Premium](power-bi-query-caching.md).

![Cachelagring av frågor](media/refresh-data/query-caching.png)

Men efter en datauppdatering är tidigare cachelagrade frågeresultat inte längre giltiga. Power BI ignorerar de här cachelagrade resultaten och måste återskapa dem. Därför kanske frågecachelagring inte är så fördelaktigt för rapporter och instrumentpaneler som är associerade med datauppsättningar som du uppdaterar mycket ofta, till exempel 48 gånger per dag.

#### <a name="tile-refresh"></a>Paneluppdatering

Power BI har ett cacheminne för varje visuellt panelobjekt på dina instrumentpaneler och uppdaterar proaktivt panelcacheminnen när data ändras. Med andra ord sker paneluppdateringen automatiskt efter en datauppdatering. Det här gäller för både schemalagda uppdateringar och på begäran-uppdateringar. Du kan också tvinga fram en uppdatering av panelen genom att välja **Fler alternativ** (...) uppe till höger på instrumentpanelen och välja **Uppdatera instrumentpanel**.

![Uppdatera panelerna på instrumentpanelen](media/refresh-data/refresh-dashboard-tiles.png)

Eftersom paneluppdatering sker automatiskt kan du se den som en inbyggd del av datauppdatering. Bland mycket annat kanske du märker att uppdateringsvaraktigheten ökar med antalet paneler. Paneluppdateringen kan vara tidskrävande.

Som standard har Power BI ett cacheminne för varje panel men om du använder dynamisk säkerhet för att begränsa dataåtkomst utifrån användarroller, som beskrivs i artikeln om [säkerhet på radnivå (RLS) med Power BI](../admin/service-admin-rls.md), måste Power BI sedan ha ett cacheminne för varje roll och varje panel. Antalet panelcacheminnen multipliceras med antalet roller.

Situationen kan bli ännu mer komplicerad om datauppsättningen använder en liveanslutning till en Analysis Services-datamodell med RLS, som understryks i självstudien [Dynamisk säkerhet på radnivå med Analysis Services-tabellmodell](desktop-tutorial-row-level-security-onprem-ssas-tabular.md). I så fall måste Power BI underhålla och uppdatera ett cacheminne för varje panel och varje användare som någonsin har visat instrumentpanelen. Det är inte ovanligt att paneluppdateringsdelen av en sådan datauppdatering vida överstiger den tid det tar att hämta data från källan. Mer information om paneluppdateringar finns i [Felsöka panelfel](refresh-troubleshooting-tile-errors.md).

#### <a name="refresh-of-report-visuals"></a>Uppdatering av visuella rapportobjekt

Den här uppdateringsprocessen är mindre viktig eftersom den bara är relevant för liveanslutningar till Analysis Services. För de här anslutningarna cachelagrar Power BI det senaste tillståndet för de visuella rapportobjekten, så att när du visar rapporten igen behöver Power BI inte fråga Analysis Services-tabellmodellen. När du interagerar med rapporten, till exempel genom att ändra ett rapportfilter, frågar Power BI tabellmodellen och uppdaterar visuella rapportobjekt automatiskt. Om du misstänker att en rapport visar inaktuella data kan du också välja knappen Uppdatera för rapporten för att utlösa en uppdatering av alla visuella rapportobjekt, som följande skärmbild visar.

![Uppdatera visuella rapportobjekt](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Granska datainfrastrukturberoenden

Oavsett lagringslägen kan ingen datauppdatering lyckas om inte de underliggande datakällorna är tillgängliga. Det finns tre huvudscenarier för dataåtkomst:

- En datauppsättning använder datakällor som finns lokalt
- En datauppsättning använder datakällor i molnet
- En datauppsättning använder data från både lokala och molnbaserade källor

### <a name="connecting-to-on-premises-data-sources"></a>Ansluta till lokala datakällor

Om din datauppsättning använder en datakälla som Power BI inte kan komma åt via en direkt nätverksanslutning måste du konfigurera en gatewayanslutning för den här datauppsättningen innan du kan aktivera ett uppdateringsschema eller utföra en datauppdatering på begäran. Mer information om datagatewayer och hur de fungerar finns i [Vad är lokala datagatewayer?](service-gateway-onprem.md)

Du har följande alternativ:

- Välja en företagsdatagateway med den nödvändiga datakällsdefinitionen
- Distribuera en personlig gateway

> [!NOTE]
> Du hittar en lista över datakälltyper som kräver en datagateway i artikeln [Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md).

#### <a name="using-an-enterprise-data-gateway"></a>Använda en företagsdatagateway

Microsoft rekommenderar att använda en företagsdatagateway istället för en personlig gateway för att ansluta en datauppsättning till en lokal datakälla. Se till att gatewayen är korrekt konfigurerad, vilket betyder att gatewayen måste ha de senaste uppdateringarna och alla nödvändiga datakällsdefinitioner. En datakällsdefinition ger Power BI anslutningsinformationen för en viss källa, inklusive anslutningsslutpunkter, autentiseringsläge och autentiseringsuppgifter. Mer information om hantering av datakällor på en gateway finns i [Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md).

Att ansluta en datauppsättning till en företagsgateway är relativt enkelt om du är gatewayadministratör. Med administratörsbehörigheter kan du direkt uppdatera gatewayen och lägga till saknade datakällor, om det behövs. I själva verket kan du lägga till en saknad datakälla till gatewayen direkt från inställningssidan för datauppsättningen. Expandera växlingsknappen för att visa datakällorna och välja länken **Lägg till i gateway**, som på följande skärmbild. Om du å andra sidan inte är gatewayadministratör måste du kontakta en gatewayadministratör för att lägga till den datakällsdefinition som krävs.

> [!NOTE]
> Endast gatewayadministratörer kan lägga till datakällor till en gateway. Se även till att gatewayadministratören lägger till ditt användar konto i listan över användare med behörighet att använda datakällan. På sidan för datamängdsinställningar kan du endast välja en företagsgateway med en matchande datakälla som du har behörighet att använda.

![Lägg till i gateway](media/refresh-data/add-to-gateway.png)

Kontrollera att du mappar rätt datakällsdefinition till datakällan. Som skärmbilden ovan visar kan gatewayadministratörer skapa flera definitioner på en och samma gateway som ansluter till samma datakälla, var och en med olika autentiseringsuppgifter. I exemplet som visas skulle en datauppsättningsägare på säljavdelningen välja datakällsdefinitionen AdventureWorksProducts-Sales medan en datauppsättningsägare på supportavdelningen skulle mappa datauppsättningen till datakällsdefinitionen AdventureWorksProducts-Support. Om namnen på datakällsdefinitionen inte är intuitiva så kontaktar du gatewayadministratören för att förtydliga vilken definition som ska väljas.

> [!NOTE]
> En datauppsättning kan bara använda en enda gatewayanslutning. Med andra ord går det inte att komma åt lokala datakällor på flera gatewayanslutningar. Därför måste du lägga till alla nödvändiga datakällsdefinitioner till samma gateway.

#### <a name="deploying-a-personal-data-gateway"></a>Distribuera en personlig datagateway

Om du inte har någon åtkomst till en företagsdatagateway och du är den enda personen som hanterar datauppsättningar så att du inte behöver dela datakällor med andra kan du distribuera en datagateway i personligt läge. I avsnittet **Gateway-anslutning**, under **Du har ingen personlig gateway installerad** väljer du **Installera nu**. Den personliga gatewayen har flera begränsningar som beskrivs i [Lokal datagateway (personligt läge)](service-gateway-personal-mode.md).

Till skillnad från en företagsdatagateway behöver du inte lägga till datakällsdefinitioner till en personlig gateway. Istället kan du hantera datakällskonfigurationen med hjälp av avsnittet **Autentiseringsuppgifter för datakälla** i inställningarna för datauppsättningen, som följande skärmbild visar.

![Konfigurera autentiseringsuppgifter för datakälla för gateway](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> Den personliga datagatewayen stöder inte datauppsättningar i DirectQuery-/LiveConnect-läge. Du kan på inställningssidan för datauppsättningen uppmanas att installera den, men om du bara har en personlig gateway kan du inte konfigurera en gatewayanslutning. Se till att du har en företagsdatagateway för att stödja de här typerna av datauppsättningar.

### <a name="accessing-cloud-data-sources"></a>Åtkomst till molndatakällor

Datauppsättningar som använder molndatakällor, till exempel Azure SQL DB, kräver inte en datagateway om Power BI kan upprätta en direkt nätverksanslutning till källan. Därmed kan du hantera konfigurationen av de här datakällorna med hjälp av avsnittet **Autentiseringsuppgifter för datakälla** i datauppsättningens inställningar. Som följande skärmbild visar behöver du inte konfigurera en gatewayanslutning.

![Konfigurera autentiseringsuppgifter för datakälla utan en gateway](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Åtkomst till lokala och molnbaserade källor i samma källfråga

En datauppsättning kan hämta data från flera källor och de här källorna kan finnas lokalt eller i molnet. Men en datauppsättning kan bara använda en enda gatewayanslutning, som nämnt tidigare. Molndatakällor kräver inte nödvändigtvis en gateway men det krävs en gateway om en datauppsättning ansluter till både lokala och molnbaserade källor i en enda kombinationsprogramfråga. I det här scenariot måste Power BI använda en gateway även för molndatakällor. Följande diagram visar hur en sådan datauppsättning kommer åt dess datakällor.

![Molnbaserade och lokala datakällor](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Om en datauppsättning separerar kombinationsprogramfrågor för att ansluta till lokala och molnbaserade källor använder Power BI en gatewayanslutning för att nå de lokala källorna och en direkt nätverksanslutning till molnkällorna. Om en kombinationsprogramfråga slår samman eller lägger till från lokala och molnbaserade källor växlar Power BI till en gatewayanslutning även för molnkällorna.

Power BI-datauppsättningar förlitar sig på Power Query för att få åtkomst till och hämta källdata. Följande kombinationprogramlista visar ett grundläggande exempel på en fråga som slår samman data från en lokal källa och en molnkälla.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Det finns två alternativ för att konfigurera en datagateway för att stödja sammanslagning eller tillägg av data från lokala och molnbaserade källor:

- Lägg till en datakällsdefinition för molnkällan till datagatewayen utöver de lokala datakällorna.
- Aktivera kryssrutan **Tillåt att användarens molndatakällor uppdateras via det här gatewayklustret**.

![Uppdatera via gatewaykluster](media/refresh-data/refresh-gateway-cluster.png)

Om du aktiverar kryssrutan **Tillåt att användarens molndatakällor uppdateras via det här gatewayklustret i gatewaykonfigurationen**, som på skärmbilden ovan, kan Power BI använda konfigurationen som användaren definierade för molnkällan under **Autentiseringsuppgifter för datakälla** i datauppsättningens inställningar. Det kan underlätta gatewaykonfigurationen. Om du, å andra sidan, vill ha större kontroll över anslutningarna som gatewayen upprättar bör du inte aktivera kryssrutan. I så fall måste du lägga till en explicit datakällsdefinition för varje molnkälla du vill stödja för din gateway. Det går också att aktivera kryssrutan och lägga till explicita datakällsdefinitioner för dina molntjänster till en gateway. I så fall använder gatewayen datakällsdefinitionerna för alla matchande källor.

### <a name="configuring-query-parameters"></a>Konfigurera frågeparametrar

Kombinationsprogram- eller M-frågorna du skapar med hjälp av Power Query kan variera i komplexitet från enkla steg till parametriserade konstruktioner. I följande lista visas ett litet exempel på en kombinationsprogramfråga som använder två parametrar, _SchemaName_ och _TableName_ för att få åtkomst till en viss tabell i en AdventureWorks-databas.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> Frågeparametrar stöds bara för datauppsättningar i Import-läge. DirectQuery-/LiveConnect-läge stöder inte frågeparameterdefinitioner.

För att säkerställa att en parametriserad datauppsättning har åtkomst till korrekta data måste du konfigurera parametrarna för kombinationsprogramfrågan i datauppsättningens inställningar. Du kan även uppdatera parametrarna programmässigt med hjälp av [Power BI REST API:et](/rest/api/power-bi/datasets/updateparametersingroup). På följande skärmbild visas användargränssnittet för att konfigurera frågeparametrarna för en datauppsättning som använder kombinationsprogramfrågan ovan.

![Konfigurera frågeparametrar](media/refresh-data/configure-query-parameters.png)




## <a name="refresh-and-dynamic-data-sources"></a>Uppdatera dynamiska datakällor
 
En *dynamisk datakälla* är en datakälla där viss eller all information som krävs för att ansluta inte kan fastställas förrän Power Query kör sin fråga, eftersom data genereras i kod eller returneras från en annan datakälla. Exempel: instansnamnet och databasen för en SQL Server-databas, sökvägen till en CSV-fil. eller en webbtjänst-URL. 
 
I de flesta fall kan Power BI datamängder som använder dynamiska datakällor inte uppdateras i Power BI-tjänsten. Det finns några undantag där dynamiska datakällor kan uppdateras i Power BI-tjänsten, t.ex. när du använder RelativePath och frågealternativen med funktionen Web.Contents M. Frågor som refererar till Power Query parametrar kan också uppdateras.
 
Du kan ta reda på om din dynamiska datakälla kan uppdateras genom att öppna dialogrutan **Inställningar för datakälla** i **Power Query-redigeraren** och sedan välja **Datakällor i den aktuella filen**. Leta efter följande varningsmeddelande i det fönster som visas, så som visas i följande bild:
 
    Some data sources may not be listed because of hand-authored queries.

![Indikator för dynamisk datakälla](media/refresh-data/dynamic-data-source.png)

Om den varningen finns i dialogrutan **Inställningar för datakälla** som visas, så innebär det att det finns en dynamisk datakälla som inte kan uppdateras i Power BI-tjänsten.

## <a name="configure-scheduled-refresh"></a>Konfigurera schemalagd uppdatering

Att upprätta anslutning mellan Power BI och datakällor är den överlägset mest utmanande uppgiften i att konfigurera en datauppdatering. De återstående stegen är relativt enkla och omfattar att ställa in uppdateringsschemat och aktivera aviseringar och misslyckad uppdatering. Stegvisa instruktioner finns i instruktionsguiden [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md).

### <a name="setting-a-refresh-schedule"></a>Ställa in ett uppdateringsschema

Du definierar frekvens och tidpunkter för att uppdatera en datauppsättning i avsnittet **Schemalagd uppdatering**. Som tidigare nämnt kan du konfigurera upp till åtta dagliga tider om din datauppsättning finns på delad kapacitet eller 48 tider på Power BI Premium. På följande skärmbild visas ett uppdateringsschema med tolvtimmarsintervall.

![Konfigurera schemalagd uppdatering](media/refresh-data/configure-scheduled-refresh.png)

När du har konfigurerat ett uppdateringsschema informeras du av inställningssidan för datauppsättningen om nästa uppdateringstid, som på skärmbilden ovan. Om du vill uppdatera datan tidigare, till exempel för att testa din gateway och konfigurationen av datakällan, utför du en uppdatering på begäran med alternativet **Uppdatera nu** i datamängdsmenyn i navigeringsfönstret. Uppdateringar på begäran påverkar inte nästa schemalagda uppdateringstid.

Observera också att den konfigurerade uppdateringstiden kanske inte är en exakt tid när Power BI startar nästa schemalagda process. Power BI startar schemalagda uppdateringar efter bästa förmåga. Målet är att starta uppdateringen inom 15 minuter efter den schemalagda tiden men en fördröjning på upp till en timme kan förekomma om tjänsten inte kan allokera de nödvändiga resurserna snabbare.

> [!NOTE]
> Power BI inaktiverar ditt uppdateringsschema efter fyra upprepade fel eller när tjänsten upptäcker ett oåterkalleligt fel som kräver en konfigurationsuppdatering, till exempel ogiltiga eller utgångna autentiseringsuppgifter. Det går inte att ändra tröskelvärdet för upprepade fel.

### <a name="getting-refresh-failure-notifications"></a>Få aviseringar om misslyckad uppdatering

Som standard skickar Power BI aviseringar om misslyckad uppdatering via e-post till datauppsättningens ägare så att ägaren kan agera i god tid om det uppstår uppdateringsproblem. Power BI skickar också en avisering till dig när tjänsten inaktiverar ditt schema på grund av upprepade fel. Microsoft rekommenderar att du lämnar kryssrutan **Skicka ett e-postmeddelande om uppdateringsfel** aktiverad.

Det är även en bra idé att ange ytterligare mottagare med hjälp av textrutan **Skicka e-post till dessa användare när uppdateringen misslyckas**. De angivna mottagarna får meddelanden om uppdateringsfel utöver datamängdens ägare. Det kan vara en kollega som tar hand om dina datamängder när du är på semester. Det kan även vara e-postaliaset för det supportteam som tar hand om uppdateringsproblem för din avdelning eller organisation. Det är användbart att skicka meddelanden om uppdateringsfel till andra utöver datamängdens ägare, så att problem uppmärksammas och åtgärdas i god tid.

Observera att Power BI inte bara skickar aviseringar om misslyckad uppdatering utan även när tjänsten pausar en schemalagd uppdatering på grund av inaktivitet. Efter två månader, när ingen användare har besökt någon instrumentpanel eller rapport som bygger på datauppsättningen, ser Power BI datauppsättningen som inaktiv. I så fall skickar Power BI ett e-postmeddelande till datauppsättningens ägare som anger att tjänsten har pausat uppdateringsschemat för datauppsättningen. Se följande skärmbild för ett exempel på en sådan avisering.

![E-post för pausad uppdatering](media/refresh-data/email-paused-refresh.png)

Om du vill återuppta schemalagd uppdatering går du till en rapport eller instrumentpanel som skapats med hjälp av den här datauppsättningen eller uppdaterar datauppsättningen manuellt med hjälp av alternativet **Uppdatera nu**.

### <a name="checking-refresh-status-and-history"></a>Kontrollera uppdateringsstatus och historik

Utöver aviseringar om fel är det en bra idé att kontrollera dina datauppsättningar med jämna mellanrum för att hitta uppdateringsfel. Ett snabbt sätt är att visa listan över datauppsättningar på en arbetsyta. För datauppsättningar med fel visas en liten varningsikon. Välj varningsikonen för att få mer information, som på följande skärmbild. Mer information om felsökning av specifika fel finns i [Felsökning av uppdateringsscenarier](refresh-troubleshooting-refresh-scenarios.md).

![Uppdateringsstatusvarning](media/refresh-data/refresh-status-warning.png)

Varningsikonen hjälper till att visa aktuella datauppsättningsproblem, men det är också en bra idé att kontrollera uppdateringshistoriken ibland. Som namnet antyder kan du med uppdateringshistoriken granska de tidigare synkroniseringscyklernas status som lyckade eller misslyckade. Till exempel kan en gatewayadministratör ha uppdaterat en utgången uppsättning med databasautentiseringsuppgifter. Som du kan se på följande skärmbild visar uppdateringshistoriken när en berörd uppdatering började fungera igen.

![Meddelanden för uppdateringshistorik](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> Du hittar en länk för att visa uppdateringshistoriken i inställningarna för datauppsättningen. Du kan även hämta uppdateringshistoriken programmässigt med hjälp av [Power BI REST API:et](/rest/api/power-bi/datasets/getrefreshhistoryingroup). Genom att använda en anpassad lösning kan du övervaka uppdateringshistoriken för flera datauppsättningar på ett centraliserat sätt.

## <a name="automatic-page-refresh"></a>Automatisk siduppdatering

Automatisk siduppdatering används på nivån för rapportsidan och innebär att rapportförfattarna kan ange ett uppdateringsintervall för visuella objekt på sidor som bara är aktivt när sidan används. Automatisk siduppdatering är endast tillgängligt för DirectQuery-datakällor. Det lägsta uppdateringsintervallet beror på vilken typ av arbetsyta som rapporten publiceras på, samt kapacitetsadministratörens inställningar för Premium-arbetsytor och [inbäddade arbetsytor](../developer/embedded/embedding.md).

Läs mer om automatisk siduppdatering i artikeln [om automatisk siduppdatering](../create-reports/desktop-automatic-page-refresh.md).

## <a name="best-practices"></a>Metodtips

Att kontrollera uppdateringshistoriken för dina datauppsättningar regelbundet är en av de viktigaste rekommenderade metoderna du kan använda för att säkerställa att dina rapporter och instrumentpaneler använder aktuella data. Om du upptäcker problem ska du åtgärda dem snabbt och följa upp med datakällsägare och gatewayadministratörer om det behövs.

Dessutom kan du överväga följande rekommendationer för att upprätta och upprätthålla tillförlitliga datauppdateringsprocesser för dina datauppsättningar:

- Schemalägg dina uppdateringar på tider med lägre belastning, särskilt om datauppsättningarna finns på Power BI Premium. Om du distribuerar uppdateringscyklerna för dina datauppsättningar i ett bredare tidsfönster kan du undvika toppar som annars kan överanstränga tillgängliga resurser. Fördröjd start av en uppdateringscykel är en indikator på resursöverbelastning. Om en Premium-kapacitet är helt slut kan Power BI till och med hoppa över en uppdateringscykel.
- Ha uppdateringsgränser i åtanke. Om källdata ändras ofta eller datavolymen är betydande kan du använda DirectQuery-/LiveConnect-läge istället för Import-läge om den ökade belastningen vid källan och påverkan på frågeprestanda är acceptabel. Undvik att ständigt uppdatera en datauppsättning i Import-läge. Men DirectQuery-/LiveConnect-läge har flera begränsningar, till exempel en gräns på en miljon rader för att returnera data och en tidsgräns på 225 sekunder för att köra frågor, enligt beskrivningen i [Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md). De här begränsningarna kan kräva att du använder Import-läget ändå. För mycket stora datavolymer kan du använda [aggregeringar i Power BI](../transform-model/desktop-aggregations.md).
- Verifiera att datauppsättningens uppdateringstid inte överstiger den maximala uppdateringsvaraktigheten. Använd Power BI Desktop för att kontrollera uppdateringsvaraktigheten. Om det tar mer än två timmar bör du överväga att flytta datauppsättningen till Power BI Premium. Datauppsättningen kanske inte kan uppdaterades på delad kapacitet. Du kan även överväga att använda [Inkrementell uppdatering i Power BI Premium](../admin/service-premium-incremental-refresh.md) för datauppsättningar som är större än 1 GB eller tar flera timmar att uppdatera.
- Optimera datauppsättningarna så att bara de tabeller och kolumner inkluderas som dina rapporter och instrumentpaneler använder. Optimera dina kombinationsprogramfrågor och undvik om möjligt dynamiska datakällsdefinitioner och dyra DAX-beräkningar. Undvik specifikt DAX-funktioner som testar varje rad i en tabell på grund av den höga minnesanvändningen och omkostnaden för bearbetning.
- Använd samma sekretessinställningar som i Power BI Desktop för att se till att Power BI kan generera effektiva källfrågor. Tänk på att Power BI Desktop inte publicerar sekretessinställningar. Du måste manuellt tillämpa inställningarna igen i datakällsdefinitionerna efter publiceringen av datauppsättningen.
- Begränsa antalet visuella objekt på dina instrumentpaneler, särskilt om du använder [säkerhet på radnivå (RLS)](../admin/service-admin-rls.md). Enligt beskrivningen tidigare i den här artikeln kan ett för stort antal paneler på instrumentpanelen ge en betydande ökning av uppdateringsvaraktigheten.
- Använd en tillförlitlig distribution av företagsdatagateway för att ansluta dina datauppsättningar till lokala datakällor. Om du märker gatewayrelaterade uppdateringsfel, till exempel otillgänglig eller överbelastad gateway, följer du upp med gatewayadministratöer om att lägga till ytterligare gatewayer i ett befintligt kluster eller distribuera ett nytt kluster (skala upp eller skala ut).
- Använda separata datagatewayer för Import-datauppsättningar och DirectQuery-/LiveConnect-datauppsättningar så att data som importeras under schemalagd uppdatering inte påverkar prestanda för rapporter och instrumentpaneler på DirectQuery-/LiveConnect-datauppsättningar, som frågar datakällor med varje användarinteraktion.
- Se till att Power BI kan skicka aviseringar om misslyckad uppdatering till din postlåda. Skräppostfilter kan blockera e-postmeddelanden eller flytta dem till en separat mapp där du kanske inte märker dem direkt.


## <a name="next-steps"></a>Nästa steg

[Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md)  
[Verktyg vid felsökning av uppdateringsproblem](service-gateway-onprem-tshoot.md)  
[Felsökning av uppdateringsscenarier](refresh-troubleshooting-refresh-scenarios.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
