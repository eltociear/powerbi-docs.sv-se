---
title: Använda sammanhängande parametrar i sidnumrerade rapporter
description: Vägledning för att utforma sidnumrerade rapporter med hjälp av sammanhängande parametrar.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 35a62923ba69520c1197e7bb80114a22ec1d9a20
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214090"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Använda sammanhängande parametrar i sidnumrerade rapporter

Den här artikeln är avsedd för rapportförfattare som skapar [sidnumrerade rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den innehåller scenarier för att utforma sammanhängande parametrar. Sammanhängande parametrar är rapportparametrar med beroenden. När en rapportanvändare väljer ett parametervärde (eller -värden) används det för att ange tillgängliga värden för en annan parameter.

> [!NOTE]
> En introduktion till sammanhängande parametrar och hur du konfigurerar dem, tas inte upp i den här artikeln. Om du inte är helt bekant med sammanhängande parametrar rekommenderar vi att du först läser [Lägga till sammanhängande parametrar till en rapport (Report Builder och SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Designscenarier

Det finns två designscenarier när man använder sammanhängande parametrar. De kan användas effektivt för att:

- Filtrera _stora uppsättningar_ med poster
- Presentera _relevanta_ poster

### <a name="example-database"></a>Exempeldatabas

Exemplen som presenteras i den här artikeln baseras på en Azure SQL Database. Databasen registrerar försäljningsåtgärder och innehåller olika tabeller som lagrar åter försäljare, produkter och försäljnings order.

En tabell med namnet **Reseller** (Återförsäljare) lagrar en post för varje återförsäljare och innehåller många tusentals poster. Tabellen **Reseller** (Återförsäljare) innehåller följande kolumner:

- ResellerCode (Återförsäljarkod) (heltal)
- ResellerName (Återförsäljarnamn)
- Land/Region
- State-Province (Delstat-provins)
- Stad
- Postnummer

Det finns en tabell med namnet **Sales** (Försäljning) också. Den lagrar poster från försäljningsorder och har en sekundärnyckelrelation till tabellen **Reseller** (Återförsäljare) i kolumnen **ResellerCode** (Återförsäljarkod).

### <a name="example-requirement"></a>Exempelkrav

Det krävs att man utvecklar en profilrapport för återförsäljare. Rapporten måste vara utformad för att visa information för en enskild återförsäljare. Det är inte lämpligt att låta rapportanvändaren ange en återförsäljarkod, eftersom de sällan kommer ihåg dem.

## <a name="filter-large-sets-of-items"></a>Filtrera stora uppsättningar med poster

Vi tar en titt på tre exempel för att hjälpa dig att begränsa stora mängder tillgängliga poster, t. ex. återförsäljare. De är:

- [Filtrera efter relaterade kolumner](#filter-by-related-columns)
- [Filtrera efter en grupperad kolumn](#filter-by-a-grouping-column)
- [Filtrera efter sökmönster](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrera efter relaterade kolumner

I det här exemplet interagerar rapportanvändaren med fem rapportparametrar. Användaren måste välja land/region, delstat/provins, ort och sedan postnummer. En slutgiltig parameter listar sedan återförsäljare som finns på den geografiska platsen.

![Skärmbild av Power BI-parametrar för sidnumrerade rapporter som visar filtrering efter relaterade kolumner.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Så här kan du utveckla de sammanhängande parametrarna:

1. Skapa de fem rapportparametrarna, sorterade i rätt ordning.
2. Skapa datamängden **CountryRegion** (Land/region) som hämtar distinkta värden för land/region med hjälp av följande frågeuttryck:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Skapa datamängden **StateProvince** (Delstat/provins) som hämtar distinkta delstats-/provinsvärden för det valda landet/den valda regionen med följande frågeuttryck:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Skapa datamängden **City** (Ort) som hämtar distinkta ortvärden för det valda landet/den valda regionen med följande frågeuttryck:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Fortsätt det här mönstret för att skapa datamängden **PostalCode** (Postnummer).
6. Skapa datamängden **Reseller** (Återförsäljare) för att hämta alla återförsäljare för de valda geografiska värdena med följande frågeuttryck:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. För varje datamängd förutom den första mappar du frågeparametrar till motsvarande rapportparametrar.

> [!NOTE]
> Alla frågeparametrar (prefix med @-symbolen) som visas i dessa exempel kan bäddas in i SELECT-uttryck eller skickas till lagrade procedurer.
>
> I allmänhet är lagrade procedurer ett bättre tillvägagångssätt för design. Det beror på att deras frågeplaner cachelagras för snabbare körning och låter dig utveckla mer avancerad logik när det behövs. De stöds dock för närvarande inte för gateway-relationella datakällor, vilket innebär SQL Server, Oracle och Teradata.
>
> Slutligen bör du alltid se till att lämpliga index finns för att stödja effektiv datahämtning. Annars kan rapportparametrarna bli långsamma att fylla i och databasen kan bli överbelastad. Mer information om SQL Server-indexering finns i [SQL Server-indexarkitektur och designguide](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017).

### <a name="filter-by-a-grouping-column"></a>Filtrera efter en grupperad kolumn

I det här exemplet interagerar rapportanvändaren med en rapportparameter för att välja den första bokstaven i återförsäljarens namn. En andra parameter visar sedan återförsäljare när namnet börjar med den valda bokstaven.

![Skärmbild av Power BI-parametrar för sidnumrerade rapporter som visar filtrering efter en grupperingskolumn.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Så här kan du utveckla de sammanhängande parametrarna:

1. Skapa rapportparametrarna **ReportGroup** (Rapportgrupp) och **Reseller** (Återförsäljare), sorterade i rätt ordning.
2. Skapa datamängden **ReportGroup** (Rapportgrupp) för att hämta de första bokstäverna som används av alla återförsäljare med följande frågeuttryck:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Skapa datamängden **Reseller** (Återförsäljare) för att hämta alla återförsäljare som börjar på den valda bokstaven med följande frågeuttryck:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Mappa frågeparametern för datamängden **Reseller** (Återförsäljare) till motsvarande rapportparameter.

Det är mer effektivt att lägga till den grupperande kolumnen i tabellen **Reseller** (Återförsäljare). När det är beständigt och indexerat ger det bäst resultat. Mer information finns i [Ange beräknade kolumner i en tabell](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Den här tekniken kan ge ännu större potential. Överväg följande skript som lägger till en ny grupperande kolumn för att filtrera återförsäljare efter _fördefinierade band med bokstäver_. Det skapar också ett index för att effektivt hämta de data som krävs av rapportparametrarna.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrera efter sökmönster

I det här exemplet interagerar rapportanvändaren med en rapportparameter för att ange ett sökmönster. En andra parameter visar sedan återförsäljare när namnet innehåller mönstret.

![Skärmbild av Power BI-parametrar för sidnumrerade rapporter som visar filtrering efter ett sökmönster.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Så här kan du utveckla de sammanhängande parametrarna:

1. Skapa rapportparametrarna **Search** (Sök) och **Reseller** (Återförsäljare), sorterade i rätt ordning.
2. Skapa datamängden **Reseller** (Återförsäljare) för att hämta alla återförsäljare som innehåller söktexten med följande frågeuttryck:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Mappa frågeparametern för datamängden **Reseller** (Återförsäljare) till motsvarande rapportparameter.

> [!TIP]
> Du kan förbättra den här designen om du vill ha mer kontroll för dina rapportanvändare. Den låter dem definiera egna mönstermatchningsvärden. Till exempel kan sökvärdet ”red" filtrera efter återförsäljare med namn som _börjar_ med tecknen ”red”.
>
> Mer information finns i [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

Så här kan du låta rapportanvändare definiera egna mönster.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Många som inte är experter på databaser känner dock inte till jokertecknet procentandel (%). De känner i stället till asterisken (*). Genom att ändra WHERE-satsen kan du låta dem använda det här specialtecknet.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Presentera relevanta poster

I det här scenariot kan du använda faktauppgifter för att begränsa antalet tillgängliga värden. Rapportanvändare visas med objekt där aktivitet har registrerats.

I det här exemplet interagerar rapportanvändaren med tre rapportparametrar. De första två anger ett datumintervall för försäljningsorder. Den tredje parametern visar sedan återförsäljare där ordrar har skapats under den tidsperioden.

![Skärmbild av Power BI-parametrar för sidnumrerade rapporter som visar tre rapportparametrar: Start Order Date (Orderns startdatum) ,End Order Date (Orderns slutdatum) och Reseller (Återförsäljare).](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Så här kan du utveckla de sammanhängande parametrarna:

1. Skapa rapportparametrarna **OrderDateStart** (Orderns startdatum), **OrderDateEnd** (Orderns slutdatum) och **Reseller** (Återförsäljare), sorterade i rätt ordning.
2. Skapa datamängden **Reseller** (Återförsäljare) för att hämta alla återförsäljare som har skapat ordrar under datumperioden med följande frågeuttryck:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att du utformar dina rapporter med sammanhängande parametrar när det är möjligt. Det beror på att de:

- Ger intuitiva och användbara upplevelser för dina rapportanvändare
- Är effektiva, eftersom de hämtar mindre uppsättningar av tillgängliga värden

Se till att optimera dina datakällor genom att:

- Använda lagrade procedurer, närhelst det är möjligt
- Lägga till lämpliga index för effektiv datahämtning
- Materialisera kolumnvärden – och till och med rader – för att undvika kostsamma utvärderingar av frågetid

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Rapportparametrar i Power BI Report Builder](../paginated-reports/report-builder-parameters.md)
- [Lägga till sammanhängande parametrar i en rapport (Report Builder och SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
