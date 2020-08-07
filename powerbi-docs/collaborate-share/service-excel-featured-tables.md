---
title: Använda aktuella Power BI-tabeller i Excel (förhandsversion)
description: I Excel kan du hitta data från aktuella tabeller i Power BI-datauppsättningar i galleriet datatyper.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 099e3aa11662232c5362895e93f0433620ce2ba9
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768896"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Använda aktuella Power BI-tabeller i Excel (förhandsversion)

*Aktuella tabeller* är ett sätt att länka data i Excel till data i Power BI. De gör det enklare att lägga till företagsdata i dina Excel-kalkylblad. Du hittar data från aktuella tabeller i Power BI-datamängder i galleriet Datatyper i Excel. Den här artikeln förklarar hur det går till.

Skapar du datamängder i Power BI? Läs om att [ställa in aktuella tabeller i Power BI Desktop](service-create-excel-featured-tables.md).

> [!NOTE]
> I Excel kan du också analysera data från valfri Power BI-datamängd som du har åtkomst till i Power BI. Mer information finns i avsnittet [Andra sätt att komma åt Power BI-datamängder från Excel](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel) i artikeln ”Analysera i Excel för Power BI”.
> 

## <a name="the-excel-data-types-gallery"></a>Galleriet Datatyper i Excel
Utvalda tabeller i Power BI-datauppsättningar visas som *datatyper* på fliken **Data** i galleriet **Datatyper** i Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Skärmbild som visar galleriet Datatyper på menyfliken Data i Excel.":::

När du expanderar galleriet visas generiska datatyper som **Stocks** (Aktier) och **Geography** (Geografi), samt de tio främsta **organisationsdatatyperna** du har tillgång till – aktuella tabeller från Power BI-mängder.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Skärmbild som visar galleriet Datatyper i Excel.":::

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>Söka efter Power BI-data i galleriet Datatyper

När du ska söka efter data i en utvald Power BI-tabell väljer du en cell eller ett område i Excel-bladet som innehåller ett värde som matchar värdet i en utvald tabell. Välj pilen **Mer** bredvid galleriet Datatyper.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Skärmbild som visar ikonen Mer i galleriet Datatyper i Excel.":::

Om du ser tabellen du letar efter väljer du den. Annars väljer du **Mer från organisationen**. Excel söker igenom alla utvalda tabeller som du har åtkomst till, och söker efter en matchning.

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="Skärmbild som visar hur du väljer Från organisationen (förhandsversion).":::
 
Excel visar alla möjliga tabeller. I rutan **Dataväljare** skriver du i rutan **Filter** för att begränsa alternativen. Välj den matchande tabellen.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Skärmbild som visar organisationsdata i Excel – tabellen för datatypen Suppliers (Leverantörer).":::
 
Om Excel hittar matchande rader med hög tillförlitlighet länkas cellerna genast till dessa rader. Ikonen för länkat objekt anger att cellerna är länkade till raderna i Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Skärmbild som visar ikonen för länkat objekt.":::

Om en cell har mer än en möjlig matchande rad visas ett frågetecken för cellen och fönstret **Dataväljare** öppnas. I följande exempel valde vi området B3:B9 och sedan den aktuella Power BI-tabellen **Store**. Alla rader hade matchningar utom cell B9, ”508 - Pasadena Lindseys”. **Dataväljaren** visar två möjliga matchningar, samma värde i två olika tabeller.

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Skärmbild som visar fönstret Dataväljare i Excel.":::
 
Alternativet för organisationsdata kan returnera rader från flera utvalda tabeller. I Excel grupperas de potentiellt matchande raderna enligt den datatyp de kom från. Excel sorterar datatyperna baserat på deras starkast möjliga matchande rad. Använd piltangenterna för att komprimera och expandera datatyperna till matchande rader.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Skärmbild som visar fönstret Dataväljare i Excel, med flera möjligheter.":::
 
För varje förslag väljer du radnamnet i **Dataväljare** om du vill se mer information på raden så att du kan välja rätt rad. När du har hittat den trycker du på **Välj** för att länka raden till cellen i Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Skärmbild som visar information om dataväljaren.":::

## <a name="explore-related-data"></a>Utforska relaterade data

Nu när du har skapat anslutningen mellan värdena i Excel-arket och data i den aktuella Power BI-tabellen kan du utforska dina data. Använd dina data till att skapa bättre Excel-rapporter.

### <a name="view-related-data-in-a-card"></a>Visa relaterade data på ett kort 
 
Välj ikonen **Kort** i cellen om du vill visa ett kort med data från fält och beräknade fält i den aktuella tabellen. Kortets rubrik visar värdet för radetikettfältet i den aktuella tabellen.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Skärmbild som visar information om länkade objekt.":::

### <a name="insert-related-data-from-power-bi"></a>Infoga relaterade data från Power BI 

Välj ikonen för **infogade data** och välj sedan ett fältnamn i listan med fält för att lägga till dess värde i rutnätet.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Skärmbild som visar hur du väljer ett fältnamn.":::

Fältvärdet eller fältvärdena placeras i intilliggande celler. Cellformeln refererar till den länkade cellen och fältnamnet så att du kan använda data i Excel-funktioner.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Skärmbild som visar en formel i en cell i Excel.":::

### <a name="use-cell-formulas"></a>Använda cellformler

Du kan referera till den länkade tabellkolumnen i en Excel-tabell och sedan lägga till datafält med referensen `.` (punkt).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Skärmbild som visar en Excel-punktreferens.":::

På samma sätt kan du referera till cellen du står i och använda referensen `.` (period) till att hämta fält.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Skärmbild som visar en cellpunktsreferens.":::

### <a name="show-a-card-change-or-convert-to-text"></a>Visa ett kort, ändra eller konvertera till text

Länkade celler har lagt till snabbmenyalternativ. Högerklicka på en cell. Förutom de vanliga alternativen finns alternativ som:

- **Visa kortet för en datatyp**.
- **Datatyp** > **Konvertera till text**.
- **Datatyp** > **Ändra**.
- **Uppdatera**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Skärmbild som visar hur du högerklickar och konverterar till text.":::
 
**Konvertera till text** tar bort länken till raden i den aktuella Power BI-tabellen. Det är viktigt att texten i cellen är radetikettvärdet i den länkade cellen. Om du har länkat en cell till en rad som du inte har tänkt dig väljer du **Ångra** i Excel för att återställa de inledande cellvärdena.
 
## <a name="data-caching-and-refresh"></a>Cachelagring av data och uppdatering

När Excel länkar en cell till en rad i en aktuell Power BI-tabell hämtas och sparas alla fältvärden i Excel-filen. Alla som du delar filen med kan referera till något av fälten utan att begära data från Power BI.  

Använd knappen **Uppdatera alla** i menyfliksområdet **Data** för att uppdatera data i länkade celler. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Skärmbild som visar Uppdatera allt.":::
 
Du kan också uppdatera enskilda celler. Högerklicka på cellen och välj **Datatyper** > **Uppdatera**.

## <a name="licensing"></a>Licensiering

Galleriet för Excel-datatyper och anslutna upplevelser för aktuella Power BI-tabeller är bara tillgängligt för Excel E5- och G5-kunder. 

## <a name="security"></a>Säkerhet

Du kan bara se aktuella tabeller från datauppsättningar som du har behörighet till i Power BI. När du uppdaterar data måste du ha behörighet att komma åt datauppsättningen i Power BI för att hämta raderna. Du behöver [behörigheten Skapa eller Skriva för datamängen](../connect-data/service-datasets-build-permissions.md) i Power BI.
 
Excel cachelagrar data som returneras för hela raden. Alla som du delar Excel-filen med kan se data för alla fält i alla länkade celler.

Om en Power BI-datauppsättning har säkerhet på radnivå eller om en etikett för Microsoft Information Protection-känslighet används ingår inte aktuella tabeller från den datauppsättningen i galleriet för Excel-datatyper. Detta är en begränsning som gäller för förhandsversionen.

## <a name="administrative-control"></a>Administrativ kontroll

Power BI-administratörer kan styra vem i organisationen som kan använda aktuella tabeller i galleriet för Excel-datatyper. Mer information finns i [aktuella tabellinställningar](../admin/service-admin-portal.md#featured-tables-settings) i administratörsportalartikeln. 
 
### <a name="auditing"></a>Granskning

Administrationsgranskningsloggar visar följande händelser för aktuella tabeller:

- **AnalyzedByExternalApplication**: Ger administratörer insyn i vilka användare som har åtkomst till vilka aktuella tabeller.
- **UpdateFeaturedTables**: Ger administratörer insyn i vilka användare som publicerar och uppdaterar aktuella tabeller.

En fullständig lista över granskningslogghändelser finns i [Spåra användaraktiviteter i Power BI](../admin/service-admin-auditing.md).

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Här följer begränsningar för den inledande förhandsversionen:

- Integreringen är tillgänglig i Excel Insiders-versioner.
- Galleriet Excel-datatyper innehåller aktuella tabeller för användare med rätt licens i Power BI Desktop och Power BI-tjänsten. Stöd för Power BI-tjänsten är kanske inte tillgängligt vid starten av förhandsgranskningen men kommer att läggas till.
- Aktuella tabeller i Power BI-datauppsättningar som använder följande funktioner visas inte i Excel: 

    - Datauppsättningar med säkerhet på radnivå.
    - Datauppsättningar med Microsoft Information Protection.
    - DirectQuery-datauppsättningar.
    - Datauppsättningar med en live-anslutning.

- Excel visar endast data i kolumner och beräknade kolumner i den aktuella tabellen. Följande har inte angetts i den första förhandsgranskningen:

    - Mått som definierats i funktionstabellen.
    - Mått som definierats för relaterade tabeller och införstådda mått som beräknas utifrån relationer.

- Excel visar bara utvalda tabeller (*datatyper*) som lagras i de nya Power BI-arbetsytorna. Aktuella tabeller som lagras i de klassiska arbetsytorna eller min arbetsyta visas inte som datatyper i Excel. Du kan [Uppgradera klassiska arbetsytor till de nya arbetsytorna](service-upgrade-workspaces.md) i Power BI.

Datatyp-upplevelsen i Excel liknar en sökfunktion. Det tar ett cellvärde från Excel-bladet och söker efter matchande rader i aktuella Power BI-tabeller. Sökfunktionen har följande beteenden:

- När du använder knappen **Organisationsdata** till att sköa gäller sökningen i Excel endast aktuella tabeller i Power BI-datamängder.
- Radmatchning baseras på textkolumner i den aktuella tabellen. Den använder samma indexering som funktionen vanliga frågor och svar i Power BI som är optimerad för sökning på engelska. Att söka på andra språk kanske inte leder till exakta matchningar. Numeriska kolumner beaktas inte för matchning.
- Matchning baseras på exakta matchningar och prefixmatchningar för enskilda sökvillkor. En cells värde delas baserat på blanksteg eller andra blankstegstecken som tabbar. Varje ord anses därefter vara en sökterm. En rads textfältvärden jämförs med varje sökterm för exakt matchning och prefix-matchning. En prefixmatchning returneras om radens textfält börjar med söktermen. Om en cell till exempel innehåller "Orange County" är "Orange" och "County" distinkta söktermer. 

    - Rader med textkolumner vars värden exakt matchar "Orange" eller "County" returneras. 
    - Rader med textkolumner vars värden börjar med "Orange" eller "County" returneras. 
    - Det är viktigt att rader som innehåller "Orange" eller "County", men inte börjar med dem, inte returneras.

- Power BI returnerar högst 100 radförslag för varje cell.
- Det går inte att ställa in eller uppdatera den aktuella tabellen i XMLA-slutpunkten
- Excel-filer med en datamodell kan användas för att publicera aktuella tabeller. Läs in data i Power BI Desktop och publicera den aktuella tabellen.
- Om du ändrar tabellnamn, radetikett eller nyckelkolumn kan den aktuella tabellen påverka Excel-användare med länkade celler till rader i tabellen. 
- Excel visar när data hämtades från Power BI-datauppsättningen. Det här behöver inte vara tidpunkten då data uppdaterades i Power BI, eller tiden för den senaste datapunkten i datauppsättningen. Anta till exempel att en datauppsättning i Power BI uppdaterats för en vecka sedan men att underliggande källdata var en vecka gamla när uppdateringen skedde. Faktiska data är då två veckor gamla, men i Excel ser hämtningstiden ut som tidpunkten när data hämtades till Excel.

## <a name="next-steps"></a>Nästa steg

- [Definiera utvalda tabeller i Power BI Desktop](service-create-excel-featured-tables.md)
- Mer information om [hur du använder Excel-datatyper från Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) finns i Excel-dokumentationen.
- Har du några frågor? [Prova Power BI Community](https://community.powerbi.com/)

