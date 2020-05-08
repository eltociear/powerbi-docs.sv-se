---
title: Vägledning till att hämta data i sidnumrerade rapporter
description: Vägledning till att skapa datakällor och datamängder sidnumrerade Power BI-rapporter.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377660"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Vägledning till att hämta data i sidnumrerade rapporter

Den här artikeln är avsedd för rapportförfattare som skapar [sidnumrerade rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den innehåller rekommendationer som hjälper dig att utforma en effektiv datahämtning.

## <a name="data-source-types"></a>Typer av datakälla

Sidnumrerade rapporter har inbyggt stöd för både relationsbaserade och analytiska datakällor. De här källorna kategoriseras sedan ytterligare som antingen molnbaserade eller lokala. För lokala datakällor, oavsett om de finns lokalt eller i en virtuell dator, behövs en datagateway så att Power BI kan ansluta. Power BI kan ansluta direkt till molnbaserade datakällor via en internetanslutning.

Om du kan välja typen av data källa (vilket du kanske kan om det är ett nytt projekt) rekommenderar vi att du använder molnbaserade datakällor. Sidnumrerade rapporter kan ansluta med lägre nätverkslatens, särskilt när datakällan finns i samma region som Power BI-klienten. Du kan även ansluta till sådana källor via enkel inloggning (SSO). Det innebär att rapportanvändarens identitet kan skickas vidare till datakällan, så att du kan tillämpa behörigheter på radnivå för respektive användare. SSO stöds för närvarande inte för lokala datakällor (vilket innebär att SQL Server Analysis Services inte kan tillämpa behörigheter på radnivå för respektive användare).

> [!NOTE]
> Även om det för närvarande inte går att ansluta till lokala databaser via SSO så kan du ändå tillämpa behörigheter på radnivå. Det gör du genom att skicka det inbyggda fältet **UserID** till en frågeparameter för datamängden. Datakällan måste lagra UPN-värden (User Principal Name) på ett sätt så att frågeresultaten kan filtreras på rätt sätt.
>
> Anta till exempel att alla säljare lagras som en rad i tabellen **Salesperson**.  Tabellen har kolumner för UPN och säljarens region. När en fråga körs filtreras tabellen efter rapportanvändarens UPN, och den kopplas till säljfakta via en inre koppling. På så sätt filtrerar frågan i praktiken säljfaktaraderna till de som gäller säljarens region.

### <a name="relational-data-sources"></a>Relationsdatakällor

I allmänhet passar relationsdatakällor bra för verksamhetsrapporter som säljfakturor. De passar också bra för rapporter där du behöver hämta mycket stora datamängder (fler än 10 000 rader). Relationsdatakällor kan också definiera lagrade procedurer som kan köras av rapportdatamängder. Lagrade procedurer medför flera fördelar:

- Parametrisering
- Inkapsling av programmeringslogik, vilket möjliggör mer komplexa dataförberedelser (som temporära tabeller, markörer eller skalära användardefinierade funktioner)
- Bättre hanterbarhet, så att du enkelt kan uppdatera logiken i lagrade procedurer. I vissa fall kan du göra det utan att behöva ändra och publicera om den sidnumrerade rapporten (förutsatt att kolumnnamn och datatyper är oförändrade).
- Bättre prestanda eftersom körningsplanerna cachelagras
- Återanvändning av lagrade procedurer i flera rapporter

I Power BI Report Builder kan du använda relationsfrågedesignern och skapa frågeuttryck grafiskt, men bara för Microsoft-datakällor.

### <a name="analytic-data-sources"></a>Analytiska datakällor

Analytiska datakällor passar bra för både verksamhetsrapporter och analytiska rapporter, och du kan snabbt få sammanfattade frågeresultat även över mycket stora datavolymer. Modellmått och KPI:er kan kapsla in komplicerade affärsregler i sammanfattningarna. De här datakällorna passar däremot inte lika bra för rapporter där du behöver hämta mycket stora datamängder (fler än 10 000 rader).

Du kan välja mellan två olika frågedesigners i Power BI Report Builder: Frågedesignern Analysis Services DAX och Analysis Services MDX. Du kan använda dessa designers för datakällor med Power BI-datamängder samt valfri SQL Server Analysis Services- eller Azure Analysis Services-modell, vare sig tabellbaserad eller flerdimensionell.

Vi rekommenderar att du använder DAX-frågedesignern om den uppfyller dina frågebehov. Om modellen inte definierar de mått du behöver måste du byta till frågeläge. I det här läget kan du anpassa frågeuttrycket genom att lägga till uttryck (för att uppnå sammanfattningen).

I MDX-frågedesignern måste modellen innehålla mått. Den har två funktioner som inte stöds i DAX-frågedesignern. Mer specifikt kan du göra följande:

- Definiera beräknade medlemmar på frågenivå (i MDX).
- Konfigurera dataregioner för att begära [serveraggregeringar](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) i icke-detaljerade grupper. Om rapporten måste presentera sammanfattningar av semiadditiva eller icke-additiva mått (som tidsberäkningar eller distinkta antal) är det förmodligen mer effektivt att använda serveraggregeringar än att hämta rader med lägre detaljnivå och låta rapporten beräkna sammanfattningarna.

## <a name="query-result-size"></a>Frågeresultatets storlek

I allmänhet är det bra att bara hämta de data som krävs i rapporten. Du bör alltså inte hämta kolumner och rader som inte behövs i rapporten.

Du kan begränsa antalet rader genom att alltid använda de mest restriktiva filtren och definiera aggregeringsfrågor. Aggregeringsfrågor grupperar och sammanfattar källdata så att du hämtar mer detaljerade resultat. Tänk dig till exempel att rapporten ska presentera en sammanfattning av säljarnas försäljning. I stället för att hämta alla försäljningsorderrader skapar du en datamängdsfråga som grupperar per säljare och sammanfattar försäljningen för varje grupp.

## <a name="expression-based-fields"></a>Uttrycksbaserade fält

Du kan utöka en rapport datamängd med fält baserade på uttryck. Om din datamängd till exempel innehåller kunders förnamn och efternamn kanske du vill ha ett fält som sammanfogar de två fälten och bildar kundens fullständiga namn. När du ska göra det har du två alternativ. Du kan:

- Skapa ett _beräknat fält_, som är ett datamängdsfält baserat på ett uttryck.
- Mata in ett uttryck direkt i datamängdsfrågan (på datakällans inbyggda språk), vilket ger ett vanligt datamängdsfält.

Vi rekommenderar det senare alternativet när det är möjligt. Det finns två bra orsaker till varför det är bättre att mata in uttryck direkt i din datamängdsfråga:

- Datakällan kan vara optimerad för att utvärdera uttrycket effektivare än Power BI (det här gäller särskilt för relationsdatabaser).
- Rapportprestanda förbättras eftersom Power BI inte behöver materialisera beräknade fält innan rapporten återges. Beräknade fält kan göra rapportens återgivningstid märkbart längre när datamängder hämtar ett stort antal rader.

## <a name="field-names"></a>Fältnamn

När du skapar en datamängd namnges fälten automatiskt efter frågekolumnerna. De här namnen kanske inte är användarvänliga eller intuitiva. Det kan också vara så att källans frågekolumnnamn innehåller tecken som inte tillåts för objekt-id:n i RDL (Report Definition Language), som blanksteg och symboler. I så fall ersätts de förbjudna tecknen med ett understreck (_).

Vi rekommenderar att du först kontrollerar att alla fält namn är användarvänliga, koncisa men ändå meningsfulla. I annat fall rekommenderar vi att du byter namn på dem _innan_ du börjar utforma rapporten. Det beror på att namnändringar inte automatiskt sprids till uttrycken som används i rapportlayouten. Om du väljer att byta namn på ett fält efter att du har börjat skapa rapporten måste du söka efter och uppdatera alla uttryck där fältnamnet används.

## <a name="filter-vs-parameter"></a>Filter och parametrar

Det är troligt att din sidnumrerade rapport innehåller rapportparametrar. Rapportparametrar används ofta till att uppmana rapportanvändaren att filtrera rapporten. Som författare av en sidnumrerad rapport har du två sätt att uppnå rapportfiltrering. Du kan mappa en rapportparameter till:

- Ett _filter_ för datamängden, och då används rapportparametervärdena till att filtrera de data som redan hämtats av datamängden.
- En _parameter_ för datamängden, och då matas rapportparametervärdena in i den interna frågan som skickas till datakällan.

> [!NOTE]
> Alla rapportdatamängder cachelagras _per session_ i upp till 10 minuter _efter den senaste användningen_. Du kan återanvända en datamängd när du skickar nya parametervärden (filtrering), återger rapporten i ett annat format eller interagerar med rapportdesignen på något sätt, som att växla synlighet eller sortering.

Tänk dig sedan exemplet med en försäljningsrapport som har en enda rapportparameter för att filtrera rapporten på ett enda år. Datamängden hämtar försäljningen för _alla år_. Det beror på att rapportparametern mappar till datamängdsfiltren. Rapporten visar data för det begärda året, som är en delmängd av data i datamängden. När rapportanvändaren ändrar rapportparametern till ett annat år och sedan visar rapporten behöver inte Power BI hämta någon datakälla. I stället används ett annat filter på datamängden som redan cachelagrats. När datamängden har cachelagrats går det snabbt att tillämpa filter.

Tänk dig nu en annan rapportdesign. Den här gången mappar rapportdesignen rapportparametern för försäljningsår till en datamängdsparameter. På så sätt infogar Power BI årsvärdet i den interna frågan så att datamängden bara hämtar data för det året. Varje gång rapportanvändaren ändrar årsvärdet i rapportparametern och sedan visar rapporten så hämtar datamängden ett nytt frågeresultat för det aktuella året.

Båda designmetoderna kan filtrera rapportdata och båda designerna kan fungera bra i dina rapportmodeller. Om designen ska optimeras måste du dock ta hänsyn till de förväntade datavolymerna, volatiliteten och rapportanvändarnas förväntade beteende.

Vi rekommenderar _datamängdsfiltrering_ om du förväntar dig att olika delmängder av datamängdsraderna kommer återanvändas många gånger (vilket sparar återgivningstid eftersom du inte behöver hämta nya data). I det här scenariot accepterar du kostnaden för att hämta en större datamängd eftersom den kommer att återanvändas flera gånger. Det här passar bra för frågor som tar lång tid att generera. Men var försiktig, cachelagring av stora datamängder per användare kan påverka prestanda och dataflödeskapacitet.

Vi rekommenderar _parametrisering av datamängden_ när du förväntar dig att det är osannolikt att en annan delmängd av datamängdsraderna kommer att efterfrågas, eller när antalet datamängdsrader som ska filtreras sannolikt är mycket stort (och är ineffektivt att cachelagra). Den här designmetoden fungerar också bra när datalagret är flyktigt. I det här fallet hämtar du aktuella data varje gång värdet för en rapportparameter ändras.

## <a name="non-native-data-sources"></a>Icke-interna datakällor

Om du behöver utveckla sidnumrerade rapporter som baseras på datakällor som inte [stöds internt i de sidnumrerade rapporterna](../paginated-reports/paginated-reports-data-sources.md) kan du först utveckla en Power BI Desktop-datamodell. På så sätt kan du ansluta till fler än 100 [Power BI-datakällor](../power-bi-data-sources.md). När du har publicerat till Power BI-tjänsten kan du sedan utveckla en sidnumrerad rapport som ansluter till Power BI-datamängden.

## <a name="data-integration"></a>Dataintegrering

Om du behöver kombinera data från flera datakällor har du två alternativ:

- **Kombinera rapportdatamängder**: Om datakällorna [stöds internt i sidnumrerade rapporter](../paginated-reports/paginated-reports-data-sources.md) kan du överväga att skapa beräknade fält som använder Report Builder-funktionerna [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) eller [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function).
- **Utveckla en Power BI Desktop-modell**: Det är förmodligen mer effektivt att utveckla en datamodell i Power BI Desktop. Du kan använda Power Query till att kombinera frågor baserat på alla [datakällor som stöds](../power-bi-data-sources.md). När du har publicerat till Power BI-tjänsten kan du sedan utveckla en sidnumrerad rapport som ansluter till Power BI-datamängden.

## <a name="sql-server-complex-data-types"></a>Komplexa SQL Server-datatyper

Eftersom SQL Server är en lokal datakälla måste Power BI ansluta via en gateway. Gatewayen har dock inget stöd för att hämta data för komplexa datatyper. Komplexa datatyper är bland annat inbyggda typer som [rumsliga datatyper](/sql/relational-databases/spatial/spatial-data-sql-server) (GEOMETRY och GEOGRAPHY) och [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). De kan även innehålla användardefinierade typer som implementeras via en sammansättningsklass i Microsoft.NET Framework CLR (Common Language Runtime).

För att kunna rita ut rumsliga data och tillhörande analyser i kartvisualiseringen krävs rumsliga SQL Server-data. Du kan därför inte arbeta med kartvisualiseringar när SQL Server är datakällan. Det fungerar däremot om datakällan är Azure SQL Database eftersom Power BI inte ansluter via en gateway.

## <a name="data-related-images"></a>Datarelaterade bilder

Du kan använda bilder till att lägga till logotyper och andra bilder i din rapportlayout. När bilderna relaterar till rader som hämtas av en rapportdatamängd har du två alternativ:

- Bilddata kan eventuellt också hämtas från datakällan (om de redan finns lagrade i en tabell).
- När bilderna lagras på en webbserver kan du använda ett dynamiskt uttryck och skapa en sökväg till bildadresen.

Mer information och förslag finns i [guiden till bilder i sidnumrerade rapporter](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Redundant datahämtning

Ibland kan dina rapporter hämta redundanta data. Det här kan inträffa när du tar bort datamängdsfrågefält eller om rapporten har datamängder som inte används. Undvik sådana situationer eftersom de leder till en onödigt hög belastning på dina datakällor, nätverket och resurserna i Power BI-kapaciteten.

### <a name="deleted-query-fields"></a>Borttagna frågefält

På sidan **Fält** i fönstret **Egenskaper för datamängd** kan du ta bort _frågefält_ från datamängden (frågefält mappas till kolumner som hämtas av datamängdsfrågan). Report Builder tar dock inte bort motsvarande kolumner från datamängdsfrågan.

Om du behöver ta bort frågefält från datamängden rekommenderar vi att du tar bort motsvarande kolumner från datamängdsfrågan. Report Builder tar automatiskt bort överflödiga frågefält. Om du skulle ta bort ett frågefält ska du även se till att ändra datamängdens frågeuttryck och ta bort kolumnerna.

### <a name="unused-datasets"></a>Datamängder som inte används

När du kör en rapport utvärderas alla datamängder, även om de inte är kopplade till rapportobjekt. Därför ska du se till att ta bort alla datamängder som använts till test och utveckling innan du publicerar en rapport.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Datakällor som stöds i sidnumrerade Power BI-rapporter](../paginated-reports/paginated-reports-data-sources.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
