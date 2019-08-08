---
title: Bästa praxis för Power BI-prestanda
description: Den här artikeln innehåller anvisningar för att skapa snabba och tillförlitliga rapporter i Power BI
author: MarkMcGeeAtAquent
ms.author: kfile
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/30/2018
LocalizationGroup: Reports
ms.openlocfilehash: bddd653b5ac8b49a38a69ae79baf2f96824444ed
ms.sourcegitcommit: 805d52e57a935ac4ce9413d4bc5b31423d33c5b1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68665341"
---
# <a name="power-bi-performance-best-practices"></a>Bästa praxis för Power BI-prestanda

Den här artikeln erbjuder anvisningar för att skapa snabba och tillförlitliga rapporter i Power BI.  

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Använd filter för att begränsa rapportens visuella information om du bara vill visa det som krävs 

Ju mer data som ett visuellt objekt måste visa, desto längre tid kommer det att ta att läsa in det visuella objektet. Även om denna princip verkar uppenbar, är den lätt att glömma. Exempel: anta att du har en stor datauppsättning. Förutom denna datauppsättning skapar du en rapport med en tabell av tabellen. Slutanvändare använder utsnitt på sidan för att komma åt de rader som de vill – vanligtvis är de bara intresserade av några dussin rader.

Ett vanligt fel är att lämna standardvyn för tabellen ofiltrerad – dvs. alla 100M+ rader. Data för dessa rader läses in i minnet och dekomprimeras vid varje uppdatering. Den här bearbetningen skapar enorma minnesbelastningar. Lösning: använd filtret ”Top N” för att minska det maximala antalet objekt som visas i tabellen. Du kan ange det maximala antalet objekt till ett högre antal än användarna behöver, till exempel 10 000. Upplevelsen ändras inte för slutanvändarna, men minnesanvändningen minskar markant. Och även prestandan förbättras.

Vi rekommenderar ett liknande tillvägagångssätt som ovanstående för alla visuella objekt på dina rapporter. Fråga dig själv, behövs alla data i den här visuella informationen? Finns det sätt att filtrera mängden data som visas i det visuella objektet med minimal påverkan på slutanvändarens upplevelse? Speciellt tabeller kan vara väldigt kostsamma.

## <a name="limit-visuals-on-report-pages"></a>Begränsa visuell information på rapportsidorna

Principen ovan gäller likvärdigt för all visuell information på en viss rapport. Vi rekommenderar att du begränsar den visuella informationen på en rapport till endast det som är nödvändigt. Detaljerade sidor är ett bra sätt att ge mer information utan att belasta rapporten med mer visuell information.  

## <a name="optimize-your-model"></a>Optimera din modell

Några metodtips:

- Ta bort oanvända tabeller eller kolumner om det är möjligt. 
- Undvik olika antal i fält med hög kardinalitet – dvs. miljontals distinkta värden.  
- Vidta åtgärder för att undvika fält med onödig precision och hög kardinalitet. Du kan till exempel dela upp mycket unika datetime-värden i separata kolumner – till exempel månad, år, datum, osv. Om det är möjligt kan du använda avrundning i fält med hög precision för att minska kardinaliteten (till exempel 13,29889 -> 13,3).
- Använd heltal i stället för strängar där det är möjligt.
- Var försiktig med DAX-funktioner. De behöver testa varje rad i en tabell, till exempel RANKX. I värsta fall kan dessa funktioner öka körtiden och minneskraven exponentiellt när tabellstorleken ökar linjärt.
- När du ansluter till datakällor via DirectQuery, överväg att indexera kolumner som ofta filtreras eller delas igen. Indexeringen ger en kraftig förbättring av rapportens svarstid.  

Mer information om hur du optimerar datakällor för DirectQuery finns i [DirectQuery i SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/).

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery och live-anslutning: förstå underliggande datakällas prestanda

När det gäller DirectQuery eller live-anslutning skickar Power BI frågor i realtid till den underliggande datakällan när användare besöker en Power BI-rapport. Rapporten visas när datakällan returnerar frågedata. Det innebär att rapportens prestanda till stor del är beroende av den underliggande datakällans prestanda.

I dessa fall är det viktigt att förstå den underliggande datakällans prestanda. Olika datakällor har olika verktyg för att förstå frågeprestanda. Till exempel har SQL Server och SQL Azure verktyget Query Store, som innehåller en historik över frågor och deras körningsstatistik.

Testa vad användarna kommer att göra i Power BI Desktop när du distribuerar Power BI-rapporter som bygger på DirectQuery och live-anslutning. Om det tar lång tid att läsa in rapporten i Power BI Desktop kommer det sannolikt att ta lång tid att läsa in den även i tjänsten för dina slutanvändare. 

## <a name="directquery-best-practices"></a>Metodtips för DirectQuery

I följande avsnitt beskrivs allmänna metodtips för att ansluta via DirectQuery.
  
### <a name="db-design-guidance"></a>Riktlinjer för DB-design

- Push-överför beräknade kolumner och mått till källan om det går. Ju närmare källan, desto större sannolikhet att få bra prestanda.
- Optimera! Förstå körningsplaner för dina frågor, lägg till index för kolumner som ofta filtreras och så vidare.

### <a name="modeling-guidance"></a>Vägledning för modellering

- Starta i Power BI Desktop.
- Undvik komplexa frågor i Frågeredigeraren.
- Använd inte relativ datumfiltrering i Frågeredigeraren.  
- Håll åtgärderna enkla från början och öka komplexiteten inkrementellt.
- Undvik relationer på beräknade kolumner och kolumner med unik identifierare.
- Försök att ange ”Anta referensintegritet” för relationer – i många fall kan den här inställningen förbättra frågeprestanda avsevärt.  

### <a name="general"></a>Allmän

- Använd filter först.
- Överväg att stänga av interaktionen mellan olika visuella objekt, vilket minskar frågebelastningen när användare korsmarkerar.
- Begränsa antalet visuella informationer och data per visuell information enligt beskrivningen ovan.
- Aktivering av säkerhet på radnivå kan medföra stora förändringar i prestanda. Se till att testa de olika radnivåernas säkerhetsroller som användarna kommer att anta.
- Det finns tidsgränser på frågenivå som krävs av tjänsten för att säkerställa att tidskrävande frågor inte kan monopolisera systemresurser. Frågor som tar längre tid än 225 sekunder når tidsgränsen och resulterar i ett fel på visualiseringsnivå.

## <a name="understand-dashboards-and-query-caches"></a>Förstå instrumentpaneler och frågecacher

Visuella objekt som har fästs på instrumentpaneler betjänas av frågecachen när instrumentpanelen läses in. När du besöker en rapport görs frågorna således direkt till datakällan – antingen Power BI-tjänsten (vid import) eller den datakälla som du anger (när det gäller DirectQuery eller live-anslutning).  

> [!NOTE]
> När du fäster live-rapportpaneler till en instrumentpanel kan de inte hanteras från frågecachen – de fungerar i stället som rapporter och skapar frågor för serverdelskärnor direkt.

Som namnet antyder får du bättre och mer konsekvent prestanda om du hämtar data från frågecachen än om du förlitar dig på datakällan. Ett sätt att dra nytta av den här funktionen är att låta instrumentpaneler vara första landningssidan för dina användare. Fäst visuella objekt som används och begärs ofta till instrumentpanelerna. På så sätt blir instrumentpanelerna en värdefull ”första försvarslinje” vilket ger kontinuerlig prestanda med mindre belastning på kapaciteten. Användare kan fortfarande klicka fram till rapporten för att få reda på fler detaljer.  
 

För DirectQuery och live-anslutning kan frågecachen uppdateras regelbundet genom att fråga datakällan. Som standard sker detta varje timme, även om detta kan konfigureras i datauppsättningens inställningar. Varje uppdatering av frågecache skickar frågor till den underliggande datakällan för att uppdatera cachen. Antalet frågor som genereras beror på hur många visuella objekt som har fästs på de instrumentpaneler som förlitar sig på datakällan. Observera att frågor genereras för varje säkerhetskontext om säkerhet på radnivå är aktiverad. Om du till exempel har två olika roller som kategoriserar användarna, och de har två olika vyer av data, genererar Power BI två uppsättningar av frågor under uppdatering av frågecachen. 

## <a name="understand-custom-visual-performance"></a>Förstå anpassad visuell prestanda 

Se till att placera varje anpassad visuell information inom dess tempo för att försäkra hög prestanda. Anpassad visuell information som är dåligt optimerad kan påverka hela rapportens prestanda. 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>Ta reda på mer om frågeprestanda med SQL Profiler och Power BI Desktop

För en mer grundlig genomgång av vilken visuell information som tar upp mest tid och resurser, kan du ansluta SQL Profiler till Power BI Desktop för att hämta en fullständig överblick över frågeprestandan.

> [!NOTE]
> Power BI Desktop stöder anslutning till en diagnostikport. Diagnostikporten gör att andra verktyg kan ansluta och utföra spårningar för att ställa diagnoser. *Det finns inte stöd för att göra ändringar i modellen! Ändringar i modellen kan leda till skador och förlorade data.*

Instruktioner följer nedan:
  
1. **Installera SQL Server Profiler och kör Power BI Desktop**

   SQL Server Profiler är tillgänglig som en del av SQL Server Management Studio.

2. **Fastställ vilken port som används av Power BI Desktop**

   Kör kommandotolken eller PowerShell med administratörsbehörighet. Och använd netstat för att hitta den port som Power BI Desktop använder för analys:

   `> netstat -b -n`

   Utdata ska vara en lista över program och deras öppna portar, till exempel:  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   Sök efter den port som används av msmdsrv.exe och skriv ner den för senare användning. I det här fallet använder du port 55786.
3. **Anslut SQL Server Profiler till Power BI Desktop**

   - Starta SQL Server Profiler från menyn **Start**
   - **Fil** > **Nytt spår**
   - Servertyp: Analysis Services
   - Servernamn: localhost: [portnumret hittas ovan]
   - På nästa skärm väljer du **Kör**
   - SQL Profiler är nu aktivt och profilerar aktivt de frågor som Power BI Desktop skickar. 
   - Medan frågorna körs, kan du se deras respektive varaktighet och CPU-tider – med den här informationen kan du fastställa vilka frågor som är flaskhalsarna.  

Via SQL Profiler kan du identifiera de frågor som upptar längst CPU-tid. Det är troligtvis dessa frågor som orsakar prestandaflaskhalsar. Fokusera på de visuella objekten som kör dessa frågor för fortsatt optimering.

## <a name="gateway-best-practices"></a>Metodtips för gateway

Den lokala datagatewayen är ett bra verktyg för att ansluta Power BI-tjänsten till dina lokala data. Med dålig planering kan den samtidigt bli en flaskhals för rapportprestanda. Detta gäller särskilt för datauppsättningar för DirectQuery/live-anslutning, där alla frågor och svar på frågor passerar gatewayen. Här följer några rekommendationer för att säkerställa högpresterande gatewayer: 

- **Använda Enterprise-läget**, i motsats till det personliga läget.
- **Rekommenderade maskinvaruspecifikationer för gatewayen** – åtta CPU-kärnor, 16 GB RAM-minne.
- **Konfigurera övervakning** – Ställ in prestandaövervakning på gatewaydatorn för att förstå om gatewayen överbelastas och blir en flaskhals. Mer information finns i [Felsökning av den lokala datagatewayen](service-gateway-onprem-tshoot.md).
- **Skala upp eller ut** – Om gatewayen verkligen blir en flaskhals överväg då att skala upp (d.v.s. flytta gatewayen till en kraftfullare dator med flera processor och mer RAM-minne) eller skala ut (till exempel dela upp datauppsättningar på olika gatewayer). 
- **Separera import kontra DirectQuery** – Om du skalat ut, överväg att separera de gatewayer som ansvarar för att importera jämfört med de som ansvarar för DirectQuery.

## <a name="network-latency"></a>Svarstid för nätverk

Nätverksfördröjningen kan påverka rapportprestandan genom att öka den tid som krävs för begäranden att nå Power BI-tjänsten och för svar som ska levereras. Klienter i Power BI tilldelas en specifik region. Du kan visa din klients ”hemregion” genom att gå till powerbi.com och välja **?** överst till höger och sedan **Om Power BI**. När användare från en klient ansluter till Power BI-tjänsten, dirigeras deras begäranden alltid till den här regionen. När begäranden når Power BI-tjänsten kan tjänsten sedan skicka ytterligare begäranden, till exempel till den underliggande datakällan eller gatewayen, som också påverkas av nätverkssvarstiden.

Verktyg som [Azure-hastighetstest](http://azurespeedtest.azurewebsites.net/) ger en indikation om nätverksfördröjningen mellan klienten och Azure-regionen. Sträva generellt mot att hålla datakällor, gatewayer och Power BI-klustret så nära som möjligt för att minimera effekten av nätverksfördröjningen. Om nätverksfördröjning är ett problem försöker du hitta gatewayer och datakällor som är närmare Power BI-klustret genom att placera dem på virtuella datorer.

För att ytterligare förbättra nätverksfördröjningen kan du använda [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/). Det innebär en möjlighet att skapa snabbare och mer tillförlitliga nätverksanslutningar mellan klienter och Azure-datacenter.

## <a name="next-steps"></a>Nästa steg

- [Planera en distribution med Power BI Enterprise](https://aka.ms/pbienterprisedeploy), med allomfattande vägledning för storskaliga distributioner av Power BI
- [DirectQuery i SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] Skapa snabba och tillförlitliga rapporter i Power BI](https://www.youtube.com/watch?v=GhiJABR7XX0)
- [[YouTube] Power BI Enterprise-distributioner](https://www.youtube.com/watch?v=K-zEWICvICM)
