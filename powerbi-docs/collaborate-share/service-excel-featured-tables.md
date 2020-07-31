---
title: Använda aktuella Power BI-tabeller i Excel (förhandsversion)
description: I Excel kan du hitta data från aktuella tabeller i Power BI-datauppsättningar i galleriet datatyper.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00fba391a6ad92f1e3edaf0e2af9691452724f6e
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251654"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Använda aktuella Power BI-tabeller i Excel (förhandsversion)

Galleriet Datatyper i Excel innehåller data från *utvalda tabeller* i Power BI-datauppsättningar. Med aktuella tabeller blir det enklare att lägga till företagsdata i dina Excel-blad. Stegen för att använda Power BI-data i Excel-blad ser ut så här:

- En Power BI-datamodellerare [höjer upp eller certifierar en datauppsättning i Power BI](../connect-data/service-datasets-promote.md).
- Datamodelleraren [identifierar utvalda tabeller](service-create-excel-featured-tables.md) i datauppsättningen och sparar datauppsättningen till Power BI-tjänsten.
- Resten av organisationen kan ansluta till de utvalda tabellerna i Excel och få relevanta och uppdaterbara data. I Excel kallas dessa tabeller för *datatyper* och finns i galleriet Datatyper.

> [!NOTE]
> I Excel kan du också hämta data från valfri datauppsättning som du har åtkomst till i Power BI. Gå till menyfliken **Data** och välj **Hämta data** > **Från Power BI (Microsoft)** .
> :::image type="content" source="media/service-excel-featured-tables/excel-get-data-power-bi.png" alt-text="Skärmbild som visar alternativet för att hämta data från Power BI på menyfliken Data.":::

## <a name="the-excel-data-types-gallery"></a>Galleriet Datatyper i Excel
Utvalda tabeller i Power BI-datauppsättningar visas som *datatyper* på fliken **Data** i galleriet **Datatyper** i Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Skärmbild som visar galleriet Datatyper på menyfliken Data i Excel.":::

När galleriet är expanderat visas de generiska datatyperna, t.ex. **Stocks** (Aktier) och **Geography** (Geografi), plus de tio främsta **organisationsdatatyper** som du har åtkomst till – utvalda tabeller från Power BI-datauppsättningar.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Skärmbild som visar galleriet Datatyper i Excel.":::

## <a name="format-a-range-of-cells-as-a-table-optional"></a>Formatera ett cellområde som en tabell (valfritt)

 Innan du börjar rekommenderar vi att du formaterar dina data som en Excel-tabell. På så sätt kommer ändringar som du gör i en rad att tillämpas på de andra raderna i tabellen. 

1. Lägg till en kolumnrubrik. 
2. Markera sedan en cell i dina data och tryck på CTRL + T. 
3. Markera **Min tabell har rubriker** > **OK**.

    :::image type="content" source="media/service-excel-featured-tables/excel-format-table.png" alt-text="Skärmbild som visar hur du konverterar ett område till en tabell.":::

## <a name="search-for-power-bi-data-in-the-excel-data-types-gallery"></a>Söka efter Power BI-data i galleriet Datatyper i Excel

När du ska söka efter data i en utvald Power BI-tabell väljer du en cell eller ett område i Excel-bladet som innehåller ett värde som matchar värdet i en utvald tabell. Välj **Organisation**. Excel söker igenom alla utvalda tabeller som du har åtkomst till, och söker efter en matchning.

:::image type="content" source="media/service-excel-featured-tables/excel-table-organization.png" alt-text="Skärmbild som visar hur du väljer en cell eller ett cellområde.":::
 
Om du vet vilken tabell du letar efter väljer du **Från din organisation (förhandsversion)** i galleriet och väljer den.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data-table.png" alt-text="Skärmbild som visar organisationsdata i Excel – tabellen för datatypen Suppliers (Leverantörer).":::
 
Om Excel hittar matchande rader med hög tillförlitlighet när du söker, länkas cellerna genast till dessa rader. Ikonen för länkat objekt anger att cellerna är länkade till raderna i Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Skärmbild som visar ikonen för länkat objekt.":::

Om en cell har mer än en möjlig matchande rad visas ett frågetecken för cellen och fönstret **Dataväljare** öppnas. I följande exempel valde användaren området B2:B10 och sökte efter en utvald Power BI-tabell. Alla rader hade matchningar utom cell B5, ”Ma Maison”. **Dataväljaren** visar två möjliga matchningar.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Skärmbild som visar fönstret Dataväljare i Excel.":::
 
Alternativet för organisationsdata kan returnera rader från flera utvalda tabeller. I Excel grupperas de potentiellt matchande raderna enligt den datatyp de kom från. Excel sorterar datatyperna baserat på deras starkast möjliga matchande rad. Använd piltangenterna för att komprimera och expandera datatyperna till matchande rader.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Skärmbild som visar fönstret Dataväljare i Excel, med flera möjligheter.":::
 
För varje rad väljer du radnamn om du vill se mer information på raden så att du kan välja rätt rad. När du har hittat den trycker du på **Välj** för att länka raden till cellen i Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Skärmbild som visar information om dataväljaren.":::
 
Om du väljer ikonen för **kort** i cellen visas ett kort med data från fält och beräknade fält i den utvalda tabellen. Kortets rubrik visar värdet för radetikettfältet i den aktuella tabellen.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Skärmbild som visar information om länkade objekt.":::

Välj ikonen för **infogade data** och välj sedan ett fältnamn i listan med fält för att lägga till dess värde i rutnätet.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Skärmbild som visar hur du väljer ett fältnamn.":::

Fältvärdet eller fältvärdena placeras i intilliggande celler. Cellformeln refererar till den länkade cellen och fältnamnet så att du kan använda data i Excel-funktioner.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Skärmbild som visar en formel i en cell i Excel.":::

## <a name="cell-formulas"></a>Cellformler

När du använder en Excel-tabell kan du referera till den länkade tabellkolumnen och sedan lägga till datafält med hjälp av referensen `.` (punkt).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Skärmbild som visar en Excel-punktreferens.":::

På samma sätt som du använder en cell kan du referera till cellen och använda referensen `.` (period) för att hämta fält.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Skärmbild som visar en cellpunktsreferens.":::
 
## <a name="data-caching-and-refresh"></a>Cachelagring av data och uppdatering

När Excel länkar en cell till en rad i en aktuell Power BI-tabell hämtas och sparas alla fältvärden i Excel-filen. Alla som du delar filen med kan referera till något av fälten utan att begära data från Power BI.  

Använd knappen **Uppdatera alla** i menyfliksområdet **Data** för att uppdatera data i länkade celler. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Skärmbild som visar Uppdatera allt.":::
 
Du kan också uppdatera enskilda celler. Högerklicka på cellen och välj **Datatyper** > **Uppdatera**.

## <a name="show-a-card-change-or-convert-to-text"></a>Visa ett kort, ändra eller konvertera till text

Länkade celler har lagt till snabbmenyalternativ. Högerklicka på en cell. Förutom de vanliga alternativen finns alternativ som:

- **Visa kortet för en datatyp**.
- **Uppdatera**.
- **Ändra**.
- **Konvertera till text**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Skärmbild som visar hur du högerklickar och konverterar till text.":::
 
**Konvertera till text** tar bort länken till raden i den aktuella Power BI-tabellen. Det är viktigt att texten i cellen är radetikettvärdet i den länkade cellen. Om du har länkat en cell till en rad som du inte har tänkt dig väljer du **Ångra** i Excel för att återställa de inledande cellvärdena.

## <a name="licensing"></a>Licensiering

Galleriet för Excel-datatyper och anslutna upplevelser för aktuella Power BI-tabeller är bara tillgängligt för Excel E5- och G5-kunder. 

## <a name="security"></a>Säkerhet

Du kan bara se aktuella tabeller från datauppsättningar som du har behörighet till i Power BI. När du uppdaterar data måste du ha behörighet att komma åt datauppsättningen i Power BI för att hämta raderna. Detta kräver kompilerings- eller skrivrättigheter till datauppsättningen. Excel cachelagrar data som returneras för hela raden. Alla som du delar Excel-filen med kan se data för alla fält i alla länkade celler.

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

- När du använder knappen **Organisationsdata** för att söka, söker Excel bara efter aktuella tabeller i certifierade datauppsättningar.
- Radmatchning baseras på textkolumner i den aktuella tabellen. Den använder samma indexering som funktionen vanliga frågor och svar i Power BI som är optimerad för sökning på engelska. Att söka på andra språk kanske inte leder till exakta matchningar. Numeriska kolumner beaktas inte för matchning.
- Matchning baseras på exakta matchningar och prefixmatchningar för enskilda sökvillkor. En cells värde delas baserat på blanksteg eller andra blankstegstecken som tabbar. Varje ord anses därefter vara en sökterm. En rads textfältvärden jämförs med varje sökterm för exakt matchning och prefix-matchning. En prefixmatchning returneras om radens textfält börjar med söktermen. Om en cell till exempel innehåller "Orange County" är "Orange" och "County" distinkta söktermer. 

    - Rader med textkolumner vars värde exakt matchar "Orange" eller "County" returneras. 
    - Rader med textkolumner vars värde börjar med "Orange" eller "County" returneras. 
    - Det är viktigt att rader som innehåller "Orange" eller "County", men inte börjar med dem, inte returneras.

- Power BI returnerar högst 100 radförslag för varje cell.
- Det går inte att ställa in eller uppdatera den aktuella tabellen i XMLA-slutpunkten
- Excel-filer med en datamodell kan användas för att publicera aktuella tabeller. Läs in data i Power BI Desktop och publicera den aktuella tabellen.
- Om du ändrar tabellnamn, radetikett eller nyckelkolumn kan den aktuella tabellen påverka Excel-användare med länkade celler till rader i tabellen. 
- Excel visar när data hämtades från Power BI-datauppsättningen. Detta är inte nödvändigtvis tidpunkten då data har uppdaterats i Power BI, eller tiden för den senaste datapunkten i en datauppsättning. Anta till exempel att en datauppsättning i Power BI uppdaterats för en vecka sedan men att underliggande källdata var en vecka gamla när uppdateringen skedde. Faktiska data skulle vara 2 veckor gamla men Excel visar data som hämtats som datum/tid då de hämtades till Excel.

## <a name="next-steps"></a>Nästa steg

- [Definiera utvalda tabeller i Power BI Desktop](service-create-excel-featured-tables.md)
- Mer information om [hur du använder Excel-datatyper från Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) finns i Excel-dokumentationen.
- Har du några frågor? [Prova Power BI Community](https://community.powerbi.com/)

