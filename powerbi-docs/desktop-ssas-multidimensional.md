---
title: Analysis Services flerdimensionella data i Power BI Desktop
description: Analysis Services flerdimensionella data i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7a25a9cc220dcb9f4620b7fb77e6bac264a47256
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514749"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Ansluta till SSAS flerdimensionella modeller i Power BI Desktop
Med Power BI Desktop kan du komma åt **SSAS flerdimensionella modeller**, vilket vanligtvis kallas **SSAS MD**.

Om du vill ansluta till en **SSAS MD**-databas går du till **Hämta data&gt; och väljer databasen &gt; SQL Server Analysis Services-databas** enligt följande bild:

![](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

**SSAS flerdimensionella modeller** i Live-anslutningsläge stöds i båda Power BI-tjänsten och i Power BI Desktop. Du kan också publicera och ladda upp rapporter som använder **SSAS flerdimensionella modeller** i Live-läge till Power BI-tjänsten.

## <a name="capabilities-and-features-of-ssas-md"></a>Funktioner i SSAS MD
I följande avsnitt beskrivs funktionerna i Power BI och SSAS MD-anslutningar.

### <a name="tabular-metadata-of-multidimensional-models"></a>Tabellmetadata för flerdimensionella modeller
Följande tabell visar förhållandet mellan flerdimensionella objekt och tabellmetadata som returneras till Power BI Desktop. Power BI frågar modellen om tabellmetadata. Baserat på de metadata som returneras körs lämpliga DAX-frågor mot Analysis Services när du skapar ett visuellt objekt, till exempel en tabell, en matris, ett diagram eller ett utsnitt.

| BISM-flerdimentionellt objekt | Tabellmetadata |
| --- | --- |
| Kub |Modell |
| Kubdimension |Tabell |
| Dimensionsattribut (nycklar), namn |Kolumner |
| Måttgrupp |Tabell |
| Mått |Mått |
| Åtgärder utan kopplad måttgrupp |I tabell som kallas *Mått* |
| Måttgrupp -> Relation till kubdimension |Relation |
| Perspektiv |Perspektiv |
| KPI |KPI |
| Hierarkier, användare/överordnad-underordnad |Hierarkier |

### <a name="measures-measure-groups-and-kpis"></a>Mått, måttgrupper och KPI:er
Måttgrupper i en flerdimensionell kub visas i Power BI som tabeller med tecknet ∑ bredvid dem i fönstret **Fält**. Beräknade mått som inte har en associerad måttgrupp är grupperade under en särskild tabell med namnet *Åtgärder* i tabellmetadatan.

I en flerdimensionell modell kan du definiera en uppsättning åtgärder eller KPI:er i en kub ska finnas i en *visningsmapp*, vilket kan underlätta komplexa modeller. Power BI identifierar visa mappar i tabellmetadata och visar mått och KPI: er i visningsmapparna. KPI:er i flerdimensionella databaser stöder *Värde*, *Mål*, *Statusgrafik* och *Trendgrafik*.

### <a name="dimension-attribute-type"></a>Typ av dimensionsattribut
Flerdimensionella modeller stöder också associerade dimensionsattribut med specifika typer av dimensionsattribut. Till exempel en **Geografi**-dimension där dimensionsattributen *Stad*, *Region*, *Land* och *Postnummer* har lämpliga geografityper som är associerade med dem som exponeras i tabellmetadata. Till exempel känner Power BI igen metadata och låter dig skapa visuella kartobjekt. Du kan identifiera dessa associationer med hjälp av *kart*ikonen bredvid element i rutan **Fält** i Power BI.

Power BI kan också återge bilder när du anger ett fält som innehåller URL:er (Uniform Resource Locator) för avbildningar. Du kan ange fälten som *ImageURL*-typ i SQL Server Data Tools (eller senare i Power BI) och dess typinformation har angetts för Power BI i tabellmetadata. Power BI kan hämta dessa bilder från URL:en och visa dem i visuella objekt.

### <a name="parent-child-hierarchies"></a>Hierarkier, överordnad-underordnad
Flerdimensionella modeller stöder överordnade-underordnade hierarkier som presenteras som en *hierarki* i tabellmetadata. Varje nivå i överordnad-underordnad-hierarkin visas som en dold kolumn i tabellmetadata. Nyckelattributet för den överordnade-underordnade dimensionen exponeras inte i tabellmetadata.

### <a name="dimension-calculated-members"></a>Dimensionsberäknade medlemmar
Flerdimensionella modeller stöder olika typer av *beräknade medlemmar*. De två vanligaste typerna av beräknade medlemmar är följande:

* Beräknade medlemmar på attributhierarkier och inte på samma nivå som *Alla*
* Beräknade medlemmar på användarhierarkier

Flerdimensionella modeller exponerar *beräknade medlemmar på attributhierarkier* som värden för en kolumn. Det finns några fler alternativ och begränsningar vid exponering av den här typen av beräknad medlem:

* Dimensionen kan ha en valfri *UnknownMember*
* Ett attribut som innehåller beräknade medlemmar får inte vara nyckelattributet för dimensionen, såvida det inte är det enda attributet för dimensionen
* Ett attribut som innehåller beräknade medlemmar får inte vara ett överordnat-underordnat attribut

Beräknade medlemmar i användarhierarkier visas inte i Power BI. Istället kommer du att kunna ansluta till en kub som innehåller beräknade medlemmar på användarhierarkier, men du kan inte se beräknade medlemmar om de inte uppfyller de begränsningar som nämns i den föregående punktlistan.

### <a name="security"></a>Säkerhet
Flerdimensionella modeller stöder säkerhet på dimensions- och cellnivå med hjälp av *roller*. När du ansluter till en kub med Power BI autentiseras och utvärderas du för lämpliga behörigheter. När en användare har tillämpat *dimensionsäkerhet* kan respektive dimensionsmedlemmar inte ses av användaren i Power BI. Men när en användares behörighet för *cellsäkerhet* har definierats, där vissa celler är begränsade, kan den användaren inte ansluta till kuben med Power BI.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Det finns vissa begränsningar med att använda **SSAS MD**:

* Servrar måste köra SQL Server 2012 SP1 CU4 eller senare versioner av Analysis Services för att Power BI Desktop SSAS MD-anslutningsappen ska fungera korrekt
* *Åtgärder* och *namngivna uppsättningar* exponeras inte för Power BI, men du kan fortfarande ansluta till kuber som också innehåller *åtgärder* eller *namngivna uppsättningar* och skapa visuella objekt och rapporter.
* Det kan hända att du stöter på ett problem där Power BI visar metadata för en SSAS-modell, men du inte kan hämta data från modellen. Det här problemet kan uppstå om 32-bitarsversionen av MSOLAP-providern är installerad på datorn i stället för 64-bitarsversionen. Du kan ofta åtgärda problemet genom att installera 64-bitarsversionen.
* Du kan inte skapa åtgärder på ”rapportnivå” när du skapar en rapport som är live-ansluten till en flerdimensionell SSAS-modell. De enda åtgärder som är tillgängliga är de som definierats i MD-modellen.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Funktioner som stöds av SSAS MD i Power BI Desktop
Följande funktioner i SSAS MD stöds i Power BI Desktop:

* Användning av följande element stöds i den här versionen av **SSAS MD** (du kan hämta [mer information](https://msdn.microsoft.com/library/jj969574.aspx) om dessa funktioner):
  * Visningsmappar
  * KPI-trender
  * Standardmedlemmar
  * Dimensionsattribut
  * Dimensionen beräknade medlemmar (måste vara en verklig medlem när dimensionen har fler än ett attribut, det kan inte vara nyckelattributet för dimensionen om det är det enda attributet och det kan inte vara ett överordnat-underordnat attribut)
  * Typer av dimensionsattribut
  * Hierarkier
  * Åtgärder (med eller utan måttgrupper)
  * Åtgärder som variant
  * KPI:er
  * ImageUrls
  * Dimensionssäkerhet

## <a name="troubleshooting"></a>Felsökning 
I följande lista beskrivs alla kända problem vid anslutning till SQL Server Analysis Services (SSAS). 

* **Fel: Det gick inte att läsa in modellschemat** – det här felet inträffar vanligtvis när användaren som ansluter till Analysis Services inte har åtkomst till databasen eller kuben.
