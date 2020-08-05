---
title: Använda externa verktyg i Power BI (förhandsversion)
description: Utöka användningen av Power BI Desktop med externa verktyg
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/29/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 69929ff48428ebf73044c296eabc419f8e442b3b
ms.sourcegitcommit: 00c0b24d5e80009d18cec6da4fee8a9611bcba04
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411967"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Använda externa verktyg i Power BI Desktop (förhandsversion)

Från och med Power BI Desktop-versionen från juli 2020 kan du använda externa verktyg och därmed tillhandahålla ytterligare funktioner och värde till Power BI Desktop. Med stöd för externa verktyg kan du utnyttja de flesta community-verktygen för Analysis Services för BI-proffs, t. ex. optimering och redigering av DAX-frågor/-uttryck och programlivscykelshantering (ALM).

Menyfliksområdet **Externa verktyg** i Power BI Desktop innehåller knappar för externa verktyg som har installerats på datorn och registrerats med Power BI Desktop. Externa verktyg som startas från Power BI Desktop ansluts automatiskt till den Analysis Services-motor som fungerar som en del av Power BI Desktop, vilket ger en sömlös upplevelse för användarna.

![Menyfliksområdet för externa verktyg i Power BI Desktop](media/desktop-external-tools/desktop-external-tools-01.png)

Dessa aktuella externa verktyg innehåller följande, med länkar till verktygens installationsplats. Varje externt verktyg stöda av sina respektive verktygsskapare:

* [Tabular Editor](https://tabulareditor.com/)
* [DAX Studio](https://daxstudio.org)
* [ALM Toolkit](http://alm-toolkit.com)


Följande avsnitt omfattar de åtgärder som stöds av externa verktyg, en lista över aktuella verktyg som ingår i Power BI Desktop och anvisningar om hur du registrerar ytterligare verktyg.

## <a name="supported-write-operations"></a>Skrivåtgärder som stöds

Du kan ansluta externa verktyg till Power BI Desktop-datamängden (Analysis Services-modellen) för att redigera följande objekt. Redigering av Power BI Desktop-mallfiler (PBIT) stöds inte.

* [Mått](https://docs.microsoft.com/analysis-services/tabular-models/measures-ssas-tabular) för beräkningar
* [Beräkningsgrupper](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups) för beräkningsåteranvändning i komplexa modeller
* [Perspektiv](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular) för att definiera fokuserade verksamhetsdomänspecifika vyer över datamängdens metadata

Det kan gå att hantera metadataöversättningar med hjälp av externa verktyg, men denna funktion stöds för närvarande inte i den här förhandsversionen. Om den aktuella användarens språkvariant är ett översatt språk, fungerar inte redigeringsobjekt i fältlistan korrekt med den aktuella versionen av Power BI Desktop. 

Alla datamängdsmetadata för [tabellobjektsmodellen](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) kan nås i skrivskyddat syfte, men objekt som inte omfattas av listan som beskrivs i artikeln [Tabellobjektsmodell](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) stöds ännu inte för redigering i Power BI Desktop Analysis Services-instansen.


## <a name="featured-external-tools"></a>Aktuella externa verktyg

Följande community-verktyg med öppen källkod fungerar med Power BI Desktop. De stöds av respektive verktygsskapare. Varje verktygs respektive installationsprogram registreras med Power BI Desktop vid installationen:

* Tabellredigeringsprogram
* DAX Studio
* ALM-verktygssats

Låt oss ta en titt på vart och ett dessa verktyg i tur och ordning.

### <a name="tabular-editor"></a>Tabellredigeringsprogram

Du kan installera [tabellredigeringsprogrammet](https://tabulareditor.com/) från följande länk: [Webbplats för tabellredigeringsprogram](https://tabulareditor.com/)

Med tabellredigeringsprogrammet kan BI-proffs enkelt bygga, underhålla och hantera tabellmodeller med ett intuitivt och enkelt redigeringsprogram. I en hierarkisk vy visas alla objekt i din tabellmodell, ordnade i mappar med stöd för flervalsegenskapsredigering och DAX-syntaxmarkering.

![Skärmbild av tabellredigeringsprogrammet](media/desktop-external-tools/desktop-external-tools-02.png)

Tabellredigeringsprogrammets källkod finns på följande GitHub-lagringsplats: [Tabellredigeringsprogrammet på GitHub](https://github.com/otykier/TabularEditor)

Huvudskapare av tabellredigeringsprogrammet är [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876).


### <a name="dax-studio"></a>DAX Studio

Du kan installera [DAX Studio](https://daxstudio.org) via följande länk: [DAX Studio-webbplatsen](https://daxstudio.org)

DAX Studio ett välkänt verktyg med öppen källkod för DAX-redigering, diagnostik, prestandajustering och analys. Dess funktioner omfattar objektbläddring, integrerad spårning, analys av frågekörning med detaljerad statistik, DAX-syntax och formatering. Följande bild visar en Dax Studio-skärm. 

![Skärmbild av DAX Studio](media/desktop-external-tools/desktop-external-tools-03.png)

DAX Studios källkod finns på följande GitHub-lagringsplats: [DAX Studio på GitHub](https://github.com/DaxStudio/DaxStudio)

Den huvudförfattare för DAX Studio är [Darren Gosbell](https://www.linkedin.com/in/darrengosbell).

### <a name="alm-toolkit"></a>ALM-verktygssats

Du kan installera [ALM-verktygssatsen](http://alm-toolkit.com) via följande länk: [Webbplats för ALM-verktygssatsen](http://alm-toolkit.com)

ALM-verktygssatsen är ett verktyg för schemajämförelse med öppen källkod för Power BI-datamängder som används för ALM-scenarier (Application Lifecycle Management). Med verktygssatsen kan du genomföra distributioner i flera miljöer och bevara historiska data med stegvis uppdatering. Med ALM-verktygssatsen kan du differentiera och sammanfoga metadatafiler, grenar och lagringsplatser. Du kan också återanvända vanliga definitioner i olika datamängder.

![Skärmbild av ALM-verktygssatsen](media/desktop-external-tools/desktop-external-tools-04.png)

ALM-verktygssatsens källkod finns på följande GitHub-lagringsplats: [ALM-verktygssatsen på GitHub](https://github.com/microsoft/analysis-services)

ALM-verktygssatsens huvudförfattare är [Christian Wade](https://www.linkedin.com/in/christianwade1).


## <a name="how-to-register-external-tools"></a>Så här registrerar du externa verktyg

Om du vill registrera andra externa verktyg med Power BI Desktop, så skapa en JSON-fil med följande innehåll:

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

I det följande visas JSON-filens lista med element:
 
* **name:** Ge verktyget ett namn. Det visas som en knappbeskrivning i menyfliksområdet med externa verktyg i Power BI Desktop.
* **description:** (valfritt) Ge en beskrivning som visas som en knappbeskrivning för knappen Externa verktyg i menyfliksområdet i Power BI Desktop.
* **path:** Ange den fullständigt kvalificerade sökvägen till verktygets körbara fil.
* **argument:** (valfritt) Tillhandahåll en sträng med kommandoradsargument med vilka verktygsfilen kan startas. Du kan använda vilken som helst av följande platshållare:
    * **%server%:** Ersätts med den lokala instansens servernamn och portnummer för Analysis Services Tabular för importerade datamodeller/DirectQuery-datamodeller.
    * **%database%:** Ersätts med databasnamnet för den värdbaserade modellen i den lokala instansen av Analysis Services Tabular för importerade datamodeller/DirectQuery-datamodeller.
* **iconData:** Tillhandahåll bilddata som återges som en knappikon i menyfliksområdet Externa verktyg i Power BI Desktop. Strängen måste formateras enligt syntaxen för data-URI:er utan prefixet "data:".
 
Ge filen namnet `"<tool name>.pbitool.json"` och placera den i följande mapp:

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

För 64-bitars miljöer placerar du filerna i följande mapp:

* **Programfiler (x86)\Common Files\Microsoft Shared\Power BI Desktop\External tools**

Filer på denna angivna plats med tillägget **.pbitool.json** läses in av Power BI Desktop vid start.

## <a name="disabling-external-tools-using-the-registry"></a>Inaktivera externa verktyg med registret

Externa verktyg kan inaktiveras med **grupprinciper** eller genom att redigera registret, vilket liknar processen att inaktivera **anpassade visuella objekt**.

    Registry key: *Software\Policies\Microsoft\Power BI Desktop\*

    Registry value: *EnableExternalTools*

Med värdet 1 (decimal) kan du använda externa verktyg i Power BI, vilket är standardvärdet.

Med värdet 0 (decimal) kan du inaktivera användningen av externa verktyg i Power BI.


## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använda visning av detaljerad information mellan rapporter i Power BI-rapporter](desktop-cross-report-drill-through.md)
* [Använda utsnitt i Power BI Desktop](../visuals/power-bi-visualization-slicers.md)


