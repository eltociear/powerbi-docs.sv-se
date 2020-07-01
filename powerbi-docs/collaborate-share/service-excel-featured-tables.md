---
title: Använda aktuella Power BI-tabeller i Excel (förhandsversion)
description: I Excel kan du hitta data från aktuella tabeller i Power BI-datauppsättningar i galleriet datatyper.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226369"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Använda aktuella Power BI-tabeller i Excel (förhandsversion)

I Excel kan du hitta data från aktuella tabeller i Power BI-datauppsättningar i galleriet datatyper. Med aktuella tabeller blir det enklare att lägga till företagsdata i dina Excel-blad. Genom att använda Power BI-certifierade och förbättrade datauppsättningsfunktioner kan organisationer göra det möjligt för fler användare att hitta och använda relevanta data som kan uppdateras för att fatta bättre beslut. Läs mer om att använda [Excel-datatyper från Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) i Excel-dokumentationen.

Galleriet med datatyper visar bara aktuella tabeller som en modellerare har granskat i Power BI-datauppsättningar. Du kan också bläddra i en datauppsättning i Excel som du har åtkomst till i Power BI. I Excel väljer du alternativet **Power BI-datauppsättningar** under **Hämta data** på menyfliken **Data**.

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Åtkomst Power BI-data via galleriet för datatyper i Excel
Aktuella tabeller i Power BI-datauppsättningar visas i galleriet Excel-datatyper på menyfliken Data.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Menyfliken Excel-data":::

När galleriet är expanderat visar galleriet de viktigaste tillgängliga datatyperna.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Galleri för Excel-datatyper":::
 
Om du vill söka efter data i en aktuell Power BI-tabell väljer du en cell eller ett intervall i ditt Excel-blad.

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="Markera en cell":::
 
Välj alternativet **Organisationsdata** från galleriet för att söka efter data i aktuella tabeller i certifierade datauppsättningar som du har åtkomst till.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Excel-organisationsdata":::
 
Välj en viss datatyp om du vet vilken typ av data du söker efter eller om du inte hittar matchande rader med alternativet organisationsdata.

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="Välj en datatyp":::
 
När du söker, om en matchande rad med hög exakthet hittas länkas cellen direkt till raden. Ikonen länkat objekt anger att cellen är länkad till raden i Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Ikonen länkat objekt":::

Om en cell har flera möjliga matchande rader visas ett dataväljarfönster. I cellen visas frågetecknet som öppnar dataväljarfönstret på den raden. Här är ett exempel när användaren har valt ett intervall från A2:A7 och sökte i en Power BI-funktionstabell.

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="Flera möjliga matchande rader":::

I **dataväljarfönstret** visas de potentiellt matchande raderna.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Dataväljarfönstret i Excel":::
 
Alternativet organisationsdata kan returnera rader från flera datatyper. I Excel grupperas de potentiellt matchande raderna enligt den datatyp de kom från. Excel sorterar datatyperna baserat på deras starkast möjliga matchande rad. Använd piltangenterna för att komprimera och expandera datatyperna till matchande rader.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Dataväljarfönstret i Excel":::
 
För varje rad väljer du radnamn om du vill se mer information på raden så att du kan välja rätt rad. När du har hittat en rad trycker du på **Välj** för att länka raden till cellen i Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="Information om dataväljare":::
 
När en rad markeras länkas cellen till raden och dess värde med värdet för fältet **Radetikett** i den aktuella Power BI-tabellen. 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Länkat objekt i Excel":::
 
Om du väljer ikonen **Länkad cell** visas ett kort med data från alla fält och beräknade fält i den aktuella tabellen. Kortets rubrik visar värdet för radetikettfältet i den aktuella tabellen.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Information om länkat objekt":::

Välj ikonen **Infoga data** för att lägga till fältvärden i rutnätet.

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="Infoga data"::: 

Välj ett fältnamn i listan med fält för att lägga till värdet i rutnätet.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Välj ett fältnamn":::

Fältvärdet placeras i den angränsande cellen. Cellformeln refererar till den länkade cellen och fältnamnet så att du kan använda data i Excel-funktioner.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel-cellformel":::
 
När du formaterar data som en Excel-tabell expanderar du tabellen och anger kolumnrubriken så att den matchar fältnamnet. Rader som är länkade till samma datatyper fylls också med deras respektive värden.

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="Fältet är kolumnnamnet"::: 

## <a name="cell-formulas"></a>Cellformler

När du använder en Excel-tabell kan du referera till den länkade tabellkolumnen och sedan lägga till datafält med hjälp av referensen `.` (punkt).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Referens för Excel-period":::

På samma sätt som du använder en cell kan du referera till cellen och använda referensen `.` (period) för att hämta fält.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Cellperiodreferens":::
 
## <a name="data-caching-and-refresh"></a>Cachelagring av data och uppdatering

När Excel länkar en cell till en rad i en aktuell Power BI-tabell hämtas och sparas alla fältvärden i Excel-filen. Alla som du delar filen med kan referera till något av fälten utan att begära data från Power BI.  

Använd knappen **Uppdatera alla** i menyfliksområdet **Data** för att uppdatera data i länkade celler. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Uppdatera alla":::
 
Du kan också uppdatera enskilda celler. Högerklicka på cellen och välj **Datatyper** > **Uppdatera**.

## <a name="show-a-card-change-or-convert-to-text"></a>Visa ett kort, ändra eller konvertera till text

Länkade celler har lagt till snabbmenyalternativ. Högerklicka på en cell > välj **Datatyp** >  

- **Visa kort**
- **Uppdatera**
- **Ändra** 
- **Konvertera till text**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Högerklicka, konvertera till text":::
 
**Konvertera till text** tar bort länken till raden i den aktuella Power BI-tabellen. Det är viktigt att texten i cellen är radetikettvärdet i den länkade cellen. Om du har länkat en cell till en rad som du inte har tänkt dig väljer du **Ångra** i Excel för att återställa de inledande cellvärdena.

## <a name="licensing"></a>Licensiering
Galleriet för Excel-datatyper och anslutna upplevelser för aktuella Power BI-tabeller är bara tillgängligt för Excel E5- och G5-kunder. 

## <a name="security"></a>Säkerhet

Du kan bara se aktuella tabeller från datauppsättningar som du har behörighet till i Power BI. När du uppdaterar data måste du ha behörighet att komma åt datauppsättningen i Power BI för att hämta raderna. Detta kräver kompilerings- eller skrivrättigheter till datauppsättningen. Excel cachelagrar data som returneras för hela raden. Alla som du delar Excel-filen med kan se data för alla fält i alla länkade celler.

Om en Power BI-datauppsättning har säkerhet på radnivå eller om en etikett för Microsoft Information Protection-känslighet används ingår inte aktuella tabeller från den datauppsättningen i galleriet för Excel-datatyper. Detta är en begränsning som gäller för förhandsversionen.

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Organisera en aktuell tabell i Power BI Desktop
Galleriet Excel-datatyper visar aktuella tabeller i datauppsättningar som laddats upp till Power BI-tjänsten. Använd Power BI Desktop för att granska aktuella tabeller i datamodellen och ladda upp dem till Power BI-tjänsten.

### <a name="turn-on-the-featured-table-preview"></a>Aktivera förhandsgranskning av aktuell tabell

1. I Power BI Desktop väljer du **Arkiv** > **Alternativ och inställningar** > **Alternativ** > **Förhandsvisningsfunktioner**.
2. Markera kryssrutan **Aktuella tabeller**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Förhandsvisning av alternativet aktuella tabeller":::

### <a name="select-a-table"></a>Välj en tabell

1. Gå till modellvy i Power BI Desktop

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Modellvy":::
 
2. Välj en tabell och ställ in **Är aktuell tabell** på **Ja**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Ställ in Är aktuell tabell på Ja":::

4. Ange de obligatoriska fälten i **Konfigurera den här aktuella tabellen**:

    - En **Beskrivning**:
    - Fältvärdet **radetikett** används i Excel så att användarna enkelt kan identifiera raden. Den visas som cellvärdet för en länkad cell i **dataväljarfönstret** och på kortet **Information**. 
    - **Nyckelkolumnen** fältvärde innehåller det unika ID:t för raden. Med det här värdet kan Excel länka en cell till en viss rad i tabellen.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Konfigurera aktuell tabell":::

När du har publicerat eller importerat datauppsättningen till Power BI-tjänsten visas den aktuella tabellen i galleriet Excel-datatyper.

- Excel cachelagrar listan med datatyper så att du måste starta om Excel för att se nyligen publicerade aktuella tabeller.
- Vissa datauppsättningar stöds inte i förhandsversionen och aktuella tabeller som definierats i dessa datauppsättningar visas inte i Excel. Se Överväganden och begränsningar för mer information.

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

- Excel visar bara aktuella tabeller som lagras i de nya Power BI-arbetsytorna. Aktuella tabeller som lagras i de klassiska arbetsytorna eller min arbetsyta visas inte som datatyper i Excel. Du kan [Uppgradera klassiska arbetsytor till de nya arbetsytorna](service-upgrade-workspaces.md) i Power BI.

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

- Har du några frågor? [Prova Power BI Community](https://community.powerbi.com/)

