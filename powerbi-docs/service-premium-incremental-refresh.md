---
title: Inkrementell uppdatering i Power BI Premium
description: Lär dig hur du kan använda mycket stora datamängder i Power BI Premium-tjänsten.
author: christianwade
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/19/2018
ms.author: chwade
LocalizationGroup: Premium
ms.openlocfilehash: 97ac445401554bf384bc1b61574534383fa2020f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292279"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Inkrementell uppdatering i Power BI Premium

Inkrementell uppdatering gör det möjligt att använda mycket stora datamängder i Power BI Premium-tjänsten, vilket medför följande fördelar:

- **Snabbare uppdateringar.** Endast de data som har ändrats behöver uppdateras. Exempelvis kan en uppdatering göras på de senaste fem dagarna i en datamängd som spänner över 10 år.

- **Mer tillförlitliga uppdateringar.** Exempelvis krävs inte långvariga anslutningar till instabila källsystem.

- **Mindre resursanvändning.** När färre data behöver uppdateras minskar den totala förbrukningen av minne och andra resurser.

## <a name="how-to-use-incremental-refresh"></a>Så här använder du inkrementell uppdatering

Principerna för inkrementell uppdatering definieras i Power BI Desktop och tillämpas när de har publicerats till Power BI-tjänsten.

Börja genom att aktivera inkrementell uppdatering i förhandsversionsfunktionerna.

![Alternativ – förhandsversionsfunktioner](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Filtrera stora datamängder i Power BI Desktop

Det går inte alltid att använda stora datamängder i Power BI Desktop eftersom de ofta begränsas av de resurser som är tillgängliga på användarens dator. Därför filtreras oftast sådana datamängder när de importeras, så att de kan användas i Power BI Desktop. Detta är oberoende av huruvida inkrementell uppdatering används eller inte.

#### <a name="rangestart-and-rangeend-parameters"></a>Parametrarna RangeStart och RangeEnd

För att du ska kunna använda inkrementell uppdatering i Power BI-tjänsten krävs filtrering med datum/tid-parametrar i Power Query med de reserverade, skiftlägeskänsliga namnen **RangeStart** och **RangeEnd**.

Efter publicering åsidosätts parametervärdena automatiskt av Power BI-tjänsten. Du behöver inte ange dem i inställningarna för datauppsättningen i tjänsten.

Det är viktigt att filtret skickas till källsystemet när frågor skickas för uppdateringsåtgärder. Att skicka ned filtrering innebär att datakällan ska ha stöd för ”frågepartitionering”. De flesta datakällor som stöder SQL-frågor har stöd för frågepartitionering. Datakällor såsom flata filer, blobar samt webb- och OData-flöden har vanligtvis inte stöd. Med tanke på de olika nivåerna av stöd för frågepartitionering för varje given datakälla rekommenderar vi att du kontrollerar att filterlogiken ingår i källfrågorna. I fall där filtret inte stöds av datakällans serverdel kan den inte skickas ned. I sådana fall kompenserar kombinationsprogrammotorn och tillämpar filtret lokalt, vilket kan kräva att den fullständiga datamängden hämtas från datakällan. Detta kan göra så att inkrementell uppdatering går mycket långsamt, och processen kan få slut på resurser i Power BI-tjänsten eller i den lokala datagatewayen om den används.

Filtret kommer att användas för att partitionera data i intervall i Power BI-tjänsten. Det är inte avsett att stödja uppdatering av den filtrerade datumkolumnen. En uppdatering tolkas som en infogning och en borttagning (inte en uppdatering). Om borttagningen inträffar i det historiska intervallet och inte det inkrementella intervallet hämtas den inte. Detta kan orsaka datauppdateringsfel på grund av konflikter med partitionsnyckel.

Välj **Hantera parametrar** i Power Query Editor och definiera parametrarna med standardvärden.

![Hantera parametrar](media/service-premium-incremental-refresh/manage-parameters.png)

När parametrarna har definierats kan du tillämpa filtret genom att välja menyalternativet **Anpassat filter** för en kolumn.

![Anpassat filter](media/service-premium-incremental-refresh/custom-filter.png)

Se till att raderna filtreras där kolumnvärdet *infaller efter eller är lika med* **RangeStart** och där det infaller *före* **RangeEnd**.

![Filtrera rader](media/service-premium-incremental-refresh/filter-rows.png)

> [!TIP]
> Datatypen för parametrarna måste vara datum/tid, men de kan konverteras så att de uppfyller datakällans krav. Följande Power Query-funktion konverterar till exempel ett datum/tid-värde så att det liknar en surrogatnyckel i heltalsform med formatet *ååååmmdd*, vilket är vanligt för informationslager. Funktionen kan anropas i filtersteget.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Välj **Close and Apply** (Stäng och använd) i Power Query Editor. Du bör ha en delmängd data i Power BI Desktop.

### <a name="define-the-refresh-policy"></a>Definiera uppdateringsprincipen

Inkrementell uppdatering är tillgängligt på snabbmenyn för tabeller, förutom för Live-anslutningsmodeller.

![Uppdateringsprincip](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Dialogrutan Inkrementell uppdatering

Dialogrutan Inkrementell uppdatering visas. Aktivera dialogrutan med hjälp av växlingsknappen.

![Uppdatera informationen](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Om Power Query-uttrycket för tabellen inte refererar till parametrarna med reserverade namn, är växlingsknappen inaktiverad.

Rubriktexten förklarar följande:

- Inkrementell uppdatering stöds endast för arbetsytor med Premium-kapacitet. Uppdateringsprinciper definieras i Power BI Desktop och tillämpas genom uppdateringsåtgärder i tjänsten.

- Om du laddar ned PBIX-filen som innehåller en princip för inkrementell uppdatering från Power BI-tjänsten, kommer den inte att öppnas i Power BI Desktop. Snart kommer du inte längre att kunna ladda ned den över huvud taget. Även om det kan finnas stöd för detta längre fram bör du ha i åtanke att dessa datamängder kan bli så stora att det är opraktiskt att ladda ned och öppna dem på en vanlig skrivbordsdator.

#### <a name="refresh-ranges"></a>Uppdateringsintervall

I följande exempel definieras en uppdateringsprincip för att lagra data i fem fullständiga kalenderår plus data för det aktuella året fram till det aktuella datumet och stegvis uppdatera 10 dagars data. Den första uppdateringsåtgärden läser in historiska data. Efterföljande uppdateringar är inkrementella och (om de har schemalagts att köras dagligen) utför följande åtgärder.

- Lägg till en ny dag med data.

- Uppdatera tio dagar fram till det aktuella datumet.

- Ta bort kalenderår som är äldre än fem år räknat från det aktuella datumet. Om det aktuella datumet exempelvis är den 1 januari 2019 tas år 2013 bort.

Den första uppdateringen i Power BI-tjänsten kan ta längre tid eftersom alla fem fullständiga kalenderår importeras. Efterföljande uppdateringar slutförs på en bråkdel av tiden.

![Uppdateringsintervall](media/service-premium-incremental-refresh/refresh-ranges.png)

**Definitionen av dessa intervall kanske är allt du behöver. I så fall kan du gå direkt till publiceringssteget nedan. De ytterligare nedrullningsbara avsnitten beskriver avancerade funktioner.**

### <a name="advanced-policy-options"></a>Avancerade principalternativ

#### <a name="detect-data-changes"></a>Identifiera dataförändringar

Inkrementell uppdatering av 10 dagar är förstås mycket effektivare än en fullständig uppdatering av fem år. Men, det kan bli ännu bättre. Om du markerar kryssrutan **Identifiera dataförändringar** kan du välja en datum/tid-kolumn som ska användas för att identifiera och uppdatera endast de dagar då data har ändrats. Detta förutsätter att den här typen av kolumn finns i källsystemet, vilket är vanligt för granskningsändamål. **Det får inte vara samma kolumn som används för att partitionera data med parametrarna RangeStart/RangeEnd.** Maxvärdet i den här kolumnen utvärderas för varje period i det inkrementella intervallet. Om det inte har ändrats sedan den senaste uppdateringen behöver perioden inte uppdateras. I exemplet kan detta ytterligare minska antalet dagar som uppdateras inkrementellt från tio till kanske bara två.

![Identifiera ändringar](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> Den aktuella designen kräver att kolumnen som identifierar dataförändringar är beständig och att den cachelagras i minnet. Överväg att använda någon av följande tekniker för att minska kardinalitet och minnesförbrukning.
>
> Spara endast maxvärdet i den här kolumnen vid tidpunkten för uppdateringen, t.ex. genom att använda en Power Query-funktion.
>
> Minska precisionen till en godtagbar nivå beroende på dina krav på uppdateringsfrekvens.
>
> Vi planerar att lägga till stöd för definition av anpassade frågor för identifiering av dataförändringar längre fram. På så sätt behöver inte kolumnvärdet sparas över huvud taget.

#### <a name="only-refresh-complete-periods"></a>Uppdatera endast fullständiga perioder

Anta att din uppdatering är schemalagd att köras 04:00 varje morgon. Om data matas in i källsystemet under dessa fyra timmar kanske du inte vill att de ska registreras. Icke fullständiga dagar saknar relevans med vissa affärsmått, t.ex. antalet fat per dag inom olje- och gasindustrin.

Ett annat exempel är när data uppdateras från ett ekonomisystem där data för den föregående månaden godkänns på kalenderdag tolv i månaden. Du kan ange det inkrementella intervallet till en månad och schemalägga körningen av uppdateringen på den tolfte dagen i månaden. Om du väljer det här alternativet uppdateras exempelvis data från januari den 12 februari.

![Fullständiga perioder](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> Uppdateringsåtgärder i tjänsten körs enligt UTC-tid. Detta kan avgöra det effektiva datumet och påverka fullständiga perioder. Vi planerar att lägga till möjligheten att åsidosätta det effektiva datumet för uppdateringsåtgärder.

## <a name="publish-to-the-service"></a>Publicera till tjänsten

Eftersom inkrementell uppdatering är en exklusiv Premium-funktion krävs Premium-kapacitet för att du ska kunna välja en arbetsyta i publiceringsdialogrutan.

![Publicera till tjänsten](media/service-premium-incremental-refresh/publish.png)

Nu kan du uppdatera modellen. Den första uppdateringen kan ta längre tid eftersom historiska data importeras. Efterföljande uppdateringar går vanligtvis mycket snabbare eftersom de använder inkrementell uppdatering.

## <a name="query-timeouts"></a>Timeout för frågor

Artikeln [Felsöka uppdateringsscenarier](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) förklarar hur timeouter kan uppstå i samband med uppdateringsåtgärder i Power BI-tjänsten. Frågor kan också begränsas av datakällans standardvärde för timeout. De flesta relationskällor stöder åsidosättning av timeouter i M-uttrycket. Exempelvis använder uttrycket nedan [SQL Server-funktionen data-access](https://msdn.microsoft.com/query-bi/m/sql-database) för att ange värdet till två timmar. Varje period som definieras av principintervallen skickar en fråga som tar hänsyn till kommandots timeout-inställning.

```
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```
