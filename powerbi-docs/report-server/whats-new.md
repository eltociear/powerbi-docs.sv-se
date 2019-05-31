---
title: Nyheter i Power BI-rapportserver
description: Läs mer om nyheterna i Power BI-rapportserver. Detta omfattar de viktiga funktionsområdena och uppdateras när nya objekt släpps.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 364795a25aaffb92afc4a7148c9bf6b3f88d2ac8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187312"
---
# <a name="whats-new-in-power-bi-report-server"></a>Nyheter i Power BI-rapportserver

Läs mer om nyheter i Power BI-rapportservern och Power BI Desktop optimerad för Power BI-rapportservern. Den här artikeln omfattar de viktiga funktionsområdena och uppdateras när nya objekt släpps.

Relaterad information om nyheter i Power BI finns i:

* [Nyheter i Power BI-tjänsten](../service-whats-new.md)
* [Nyheter i Power BI Desktop](../desktop-latest-update.md)
* [Nyheter i mobilapparna för Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="may-2019-power-bi-desktop-for-power-bi-report-server"></a>Maj 2019: Power BI Desktop för Power BI-rapportserver

Se den [Power BI Report Server maj 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) blogginlägget för mer information om de nya funktionerna.

Här följer några av höjdpunkterna för versionen:

### <a name="performance-analyzer"></a>Analysera prestanda 

Om rapporten går långsammare än förväntat, försöker du analysera prestanda i Power BI Desktop. När du startar den skapar en loggfil med information om varje åtgärd som du gör i rapporten. Läs mer om den [Performance Analyzer](../desktop-performance-analyzer.md).

### <a name="new-modeling-view"></a>Ny modellering vy

I den nya vyn modellering i Power BI Desktop kan du visa och arbeta med komplexa datauppsättningar som innehåller många tabeller. Höjdpunkter omfattar flera diagram layouter och massredigering av kolumner, mått och tabeller. Läs mer om [modellering visa](../desktop-modeling-view.md).

### <a name="accessible-visual-interaction"></a>Tillgängliga visuell interaktion

Du kan nu åtkomst datapunkter i många av de inbyggda visuella objekt med tangentbordsnavigering. Läs mer om [hjälpmedel i Power BI-rapporter](../desktop-accessibility.md).

### <a name="conditional-formatting-titles-and-web-url-actions"></a>Villkorsstyrd formatering rubriker och åtgärder för webb-URL

Power BI-rapporter är interaktiva. Det klokt att rubriker i en rapport skulle vara dynamisk, så att det aktuella tillståndet för rapporten. Du kan använda samma uttryck-bunden formatering för att göra det dynamiska URL: er för dina knappar, former och bilder. Läs mer om [uttrycksbaserade rubriker](../desktop-conditional-format-visual-titles.md).

### <a name="cross-highlight-by-axis-labels"></a>Korsmarkera av axeletiketter

Välj kategori axeletiketter i ett visuellt objekt att korsmarkera andra element på en sida, precis som du skulle välja datapunkter i ett visuellt objekt. Läs mer om [korsmarkering](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

### <a name="all-the-new-features"></a>Alla nya funktioner

Här är listan över alla nya funktioner:

### <a name="reporting"></a>Rapportering

- Korsmarkera på en enda punkt i linjediagram 
- Automatiskt radbyte på rubriker 
- Uppdatera standard visuell interaktion till korsfiltrera ¬
- Avrundade hörn för visuella kantlinjer 
- Enda väljer utsnitt  
- Termisk karta stöd för Bing maps  
- Korsmarkera av axeletiketter  
- Standardknappbeskrivningen formatering  
- Statisk Webb-URL: en som har stöd för knappar, former och bilder  
- Sidan alternativ för textjustering   
- Val av förbättringar i fältfönstret  
- Tillgängliga visuell interaktion  
- Villkorsstyrd formatering för visuella rubriker  
- Villkorsstyrd formatering för åtgärder för webb-URL: en för knappar, former och bilder
- Prestanda analyzer fönstret
- Tabeller och matriser tangentbordsnavigering
- Rad data etikettkontrollen position
- KPI visual indikator storlek textkontroll

### <a name="analytics"></a>Analys

- Visa datum som en hierarki som är nu allmänt tillgänglig  

### <a name="modeling"></a>Modellering

- Ny modellering vy som är nu allmänt tillgänglig
- Nya DAX-funktioner
- Uppdatera till ALLSELECTED DAX-funktionen
- Inaktivera automatisk datumtabeller för nya rapporter

## <a name="may-2019-power-bi-report-server"></a>Maj 2019: Power BI-rapportserver

### <a name="support-for-trusted-visuals"></a>Stöd för betrodda visuella objekt

Vi har lagt till stöd för betrodda visuella Power BI Report Server. Vi stöder för närvarande Mapbox och PowerOn visuella objekt. ESRI, Visio och PowerApps stöds inte för den här versionen.)

### <a name="improved-security-features"></a>Förbättrade säkerhetsfunktioner

**RestrictedResourceMimeTypeForUpload**, där administratörer kan använda för att ange en kommaavgränsad lista över utestängda mime-typer, till exempel text/html.

## <a name="january-2019"></a>Januari 2019

Stöd för dessa funktioner i Power BI-rapporter:

[**Säkerhet på radnivå**](row-level-security-report-server.md) Konfiguration av säkerhet på radnivå (RLS) med Power BI-rapportserver kan begränsa dataåtkomst för givna användare. Filter begränsar åtkomst till data på radnivå och du kan definiera filter inom roller.

[**Expandera eller komprimera på matrisens radrubriker** ](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Vi har lagt till möjligheten att expandera eller komprimera enskilda radrubriker, en av de mest efterfrågade visuella funktionerna.

[**Kopiera och klistra in mellan pbix-filer**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Du kan kopiera visuella objekt mellan pbix-filer, antingen från snabbmenyn för det visuella objektet eller med standardkortkommandot Ctrl + C och klistra in dem i en annan rapport med Ctrl + V.

[**Smarta justeringsstödlinjer**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Du ser smarta justeringsstödlinjer när du flyttar objekt på rapportsidan, precis som i PowerPoint, så att du kan justera allt på sidan. Du ser smarta stödlinjer när du drar eller ändrar storlek på något på sidan. När du flyttar ett objekt nära ett annat fästs det på en plats i linje med det andra objektet.

**Hjälpmedelsfunktioner** För många hjälpmedelsfunktioner att lista: till exempel [fältlista med stöd för hjälpmedel](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Fältlistrutan är helt åtkomlig. Du kan navigera i rutan med enbart tangentbordet och en skärmläsare och använda snabbmenyn för att lägga till fält på rapportsidan.

#### <a name="custom-visuals"></a>Anpassade visuella objekt

- Den API-version som levereras med den här versionen är 2.3.

### <a name="administrator-settings"></a>Administratörsinställningar

Administratörer kan ange följande egenskaper i de avancerade SSMS-egenskaperna för servergruppen:

**AllowedResourceExtensionsForUpload** Ange tillägg av resurser som kan laddas upp till rapportservern. Filnamnstillägg för inbyggda filtyper som &ast;.rdl och &ast;.pbix behöver inte inkluderas. Standardvärdet är ”&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx”. 

**SupportedHyperlinkSchemes** Anger att en kommaavgränsad lista över URI-scheman som är tillåtna måste definieras i hyperlänkåtgärder som tillåts att återges eller ”&ast;” för att aktivera alla hyperlänkscheman. Till exempel skulle inställningen ”http,https” tillåta hyperlänkar till ”https://www. contoso.com”, men ta bort hyperlänkar till ”mailto:bill@contoso.com” eller ”javascript:window.open(”www.contoso.com”, ”_tomt”)”. Standardvärdet är ”&ast;”.

## <a name="august-2018"></a>Augusti 2018

I augusti 2018 har många nya funktioner lagts till i versionen av Power BI Desktop som är optimerad för Power BI-rapportservern. Här visas funktionerna indelade efter område:

- [Rapportering](#reporting)
- [Analys](#analytics)
- [Modellering](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Höjdpunkter i augusti 2018-versionen

I den långa listan över nya funktioner är de här funktionerna särskilt intressanta. Se vårt [blogginlägg](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/) för mer information.

#### <a name="report-theming"></a>Rapportteman

Rapportteman har lagts till augusti 2018-versionen av Power BI-rapportservern som gör att du snabbt kan färglägga hela rapporten så att den matchar ett tema eller en varumärkesprofil. När du importerar ett tema uppdateras alla dina diagram automatiskt för att använda temafärgerna, och du kan få åtkomst till temafärgerna från färgpaletten. Du kan ladda upp en temafil med alternativet **Importera tema** under knappen **Växla tema**.

En temafil är en JSON-fil som innehåller alla de färger som du vill att vi ska använda i din rapport tillsammans med eventuell standardformatering som du vill använda för visuella objekt.
Här är ett enkelt exempel på ett JSON-tema som bara uppdaterar standardfärgerna för rapporten:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Villkorsstyrd formatering av ett annat fält

Möjligheten att formatera en kolumn med ett annat fält i modellen är en av de stora förbättringarna av villkorsstyrd formatering.

#### <a name="conditional-formatting-by-values"></a>Villkorsstyrd formatering efter värden

En annan ny typ av villkorsstyrd formatering är värdet **Formatera efter fält**. Med värdet Formatera efter fält kan du använda ett mått eller en kolumn som anger en färg, antingen via en hexadecimal kod eller ett namn, och tillämpa den färgen på bakgrunden eller teckenfärgen.

#### <a name="report-page-tooltips"></a>Knappbeskrivningar för rapportsida

Funktionen för knappbeskrivningar för rapportsida ingår i augusti 2018-uppdateringen av Power BI-rapportserver. Med den här funktionen kan du utforma en rapportsida som ska användas som en anpassad knappbeskrivning för andra visuella objekt i rapporten.

#### <a name="log-axis-improvements"></a>Förbättringar av loggaxel

Vi har avsevärt förbättrat loggaxel i kartesiska diagram. Du bör nu kunna välja logaritmisk skala för den numeriska axeln i alla kartesiska diagram, inklusive kombinationsdiagram, när du har data som är helt positiva eller helt negativa.

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO Direct Query

SAP HANA SSO Direct Query-stöd med Kerberos är nu tillgängligt för Power BI-rapporter.

>[!Note]
>Det här scenariot stöds endast när SAP HANA behandlas som en relationsdatakälla med rapporter som du har skapat i Power BI Desktop.  Aktivera detta i Power BI Desktop i DirectQuery-menyn under Alternativ genom att markera ”Behandla SAP HANA som en relationskälla” och klicka på OK.

#### <a name="custom-visuals"></a>Anpassade visuella objekt

- Den API-versionen som levereras med den här versionen är 1.13.0.

- Nu kan anpassade visuella objekt återställas till en tidigare version som är kompatibel med den aktuella versionen av server-API (om tillgängligt).

### <a name="reporting"></a>Rapportering 

- [Rapportteman](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Knappar för att utlösa åtgärder](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Linjeformat för kombinationsdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Förbättrad standardsortering för visuella objekt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Numeriskt utsnitt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Synkronisering av avancerade snitt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Förbättringar av loggaxel](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Dataetikettsalternativ för trattdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Ange bredd på penseldrag till noll](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Stöd för hög kontrast med rapporter](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Radiekontroll i ringdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Positionskontroll för informationsetiketter i cirkel- och ringdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Formatera dataetiketter separat för varje mått i ett kombinationsdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Nytt visuellt sidhuvud med bättre flexibilitet och formatering](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Formatering av skrivbordsunderlägg](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Knappbeskrivningar för tabell och matris](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Inaktivera knappbeskrivningar för visuella objekt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Hjälpmedel för utsnitt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Förbättringar av formateringsinstrumentpanelen](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Stegvis linjesupport för linje- och kombinationsdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Sortera upplevelseförbättringar](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Skriva ut rapporter via Exportera till PDF (i Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Skapa bokmärkesgrupper](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Omräkning av utsnitt](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Knappbeskrivningar för rapportsida](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Analys

- [Ny DAX-funktion: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Mät visning av detaljerad information](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Villkorsstyrd formatering av ett annat fält](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Villkorsstyrd formatering efter värden](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modellering

- [Filtrera och sortera i datavyn](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Förbättrad nationella formatering av nationella inställningar](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Datakategorier för mått](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [DAX-statistikfunktioner](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>Maj 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Fjärrkonfigurera iOS-mobilappar för Power BI för rapportservrar

Som IT-administratör kan du nu använda din organisations MDM-verktyg för att fjärrkonfigurera åtkomsten från iOS-mobilappen för Power BI till en rapportserver. Mer information finns i avsnittet om [hur du fjärrkonfigurerar åtkomsten från iOS-mobilappen för Power BI till en rapportserver](configure-powerbi-mobile-apps-remote.md).

## <a name="march-2018"></a>Mars 2018

I mars 2018 har många nya funktioner lagts till i versionen av Power BI Desktop som är optimerad för Power BI-rapportservern. Här visas funktionerna indelade efter område:

- [Visuella objekt](#visuals-updates)
- [Rapportering](#reporting)
- [Analys](#analytics)
- [Prestanda](#performance)
- [Rapportserver](#report-server)
- [Övrigt](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Höjdpunkter i mars 2018-versionen

I den långa listan över nya funktioner är de här funktionerna särskilt intressanta.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Regelbaserad villkorsstyrd formatering för tabeller och matriser](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Skapa regler för att villkorligt ange färg på bakgrunden eller teckenfärg för en kolumn baserat på särskild affärslogik i din tabell eller matris.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Visa och dölja sidor](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Du kanske vill att läsarna ska ha åtkomst till din rapport, men vissa av sidorna är inte riktigt klara. Nu kan du dölja dem tills du är färdig med dem. Eller så kan du dölja sidor från den normala navigeringen och låta läsarna navigera till dem via bokmärken eller genom att visa mer detaljerad information.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Skapa bokmärken](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Du kan använda bokmärken för att skapa en berättelse med data i din rapport.

- [Korsmarkering för bokmärken](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): Bokmärken sparar och visar det korsmarkerade tillståndet för rapportsidan vid tidpunkten då du skapade bokmärket.
- [Ökad flexibilitet för bokmärken](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): Bokmärken återspeglar egenskaperna som du anger i din rapport och påverkar endast de visuella objekt som du väljer.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Välja flera datapunkter över flera diagram](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Välj flera datapunkter i flera diagram och tillämpa korsfiltrering på hela sidan.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Synkronisera utsnitt över flera sidor i en rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Ett utsnitt kan tillämpas på en, två eller fler sidor i en rapport.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Snabbmått](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Skapa nya mått baserat på befintliga mått och numeriska kolumner i en tabell.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Vid visning av detaljerad information filtreras andra visuella objekt](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

När du visar mer detaljerad information i en viss kategori i ett visuellt objekt kan du låta alla visuella objekt på sidan filtreras på samma kategori.

### <a name="visuals-updates"></a>Uppdateringar av visuella objekt

- [Celljustering för tabeller och matriser](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Visningsenheter och precisionskontroll för tabell- och matriskolumner](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Spill av dataetiketter för visualiseringar för fält- och kolumndiagram](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Kontrollera bakgrundsfärg för dataetiketter för kartesisk visuell information och visuell information för kartor](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Utfyllnadskontroll för fält/kolumn](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Öka området som används för axeletiketter i diagram](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Punktdiagram från x- och y-axelgrupperingar](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Högdensitetssampling för kartor baserat på latitud och longitud](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Dynamiska utsnitt](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Lägga till ett ankardatum för ett relativt datumutsnitt](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Rapportering

- [Inaktivera sidhuvudet för visuella objekt i läsläge för en rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Rapportalternativ för långsamma datakällor](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Förbättrad standardplacering av visuella objekt](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Styra sorteringen av visuella objekt med markeringsfönstret](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Låsa objekt i rapporten](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Sök formaterings- och analysfönster](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Rutan fältegenskaper och fältbeskrivningar](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Analys

- [UTCNOW() och UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Markera anpassad datumtabell](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Detaljgranska andra visuella objekt](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formatering på cellnivå för flerdimensionella AS-modeller för flerradskort](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Prestanda

- [Prestandaförbättringar för filtrering](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Prestandaförbättringar för DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Prestandaförbättringar för öppna och spara](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Förbättringar av “visa objekt utan data”](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Rapportserver

#### <a name="export-to-accessible-pdf"></a>Exportera till tillgänglig PDF

När du exporterar en sidnumrerad rapport till PDF kan du nu exportera till en tillgänglig/taggad PDF-fil. Den är större men enklare för skärmläsare och andra hjälpmedel att läsa och navigera. Du aktiverar tillgänglig PDF genom att ange enhetsinformationsinställningen **AccessiblePDF** till **True**. Se [Enhetsinformationsinställningar för PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) och [Ändra enhetsinformationsinställningar](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Övriga förbättringar

- [Förbättringar av Lägg till kolumn från exempel](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Snabblänk för konsulttjänster](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Förbättrad felrapportering](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Visa tidigare fel som har inträffat](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Oktober 2017

### <a name="power-bi-report-data-sources"></a>Rapportdatakällor i Power BI

Power BI-rapporterna i Power BI-rapportserver kan ansluta till en mängd olika datakällor. Du kan importera data och schemalägga datauppdateringar, eller fråga efter det direkt med DirectQuery eller en live-anslutning till SQL Server Analysis Services. Se listan med datakällor som stöder schemalagd uppdatering och de som stöder DirectQuery i ”Power BI:s rapportdatakällor i Power BI-rapportserver”.

### <a name="scheduled-data-refresh-for-imported-data"></a>Schemalagd datauppdatering för importerade data

I Power BI-rapportserver kan du ställa in schemalagda datauppdateringar för att dina data ska vara uppdaterade i Power BI-rapporter med en inbäddad modell i stället för en live-anslutning eller DirectQuery. Med en inbäddad modell importerar du data, så den är inte ansluten till den ursprungliga datakällan. Den måste uppdateras för att hålla data uppdaterade och det gör man med en schemalagd uppdatering. Läs mer om ”schemalagd uppdatering för Power BI-rapporter i Power BI-rapportserver”.

### <a name="editing-power-bi-reports-from-the-server"></a>Redigera Power BI-rapporter från servern

Du kan öppna och redigera Power BI-rapportfiler (.pbix) från servern, men du kommer tillbaka till den ursprungliga fil som du överförde.  Det innebär att **om datan har uppdaterats av servern kommer den inte uppdateras när du först öppnar filen**. Du måste uppdatera den lokalt manuellt för att se ändringen.

### <a name="large-file-uploaddownload"></a>Uppladdning/nedladdning av stora filer

Du kan ladda upp filer upp till 2 GB i storlek, även om den här gränsen som standard är 1 GB i rapportserverinställningarna i SQL Server Management Studio (SSMS).  De här filerna lagras i databasen på samma sätt som för SharePoint och det krävs ingen särskild konfiguration för SQL Server-katalogen.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Åtkomst till delade datauppsättningar som OData-flöden

Du kan komma åt delade datauppsättningar från Power BI Desktop med ett OData-flöde. Mer information finns i [Åtkomst till delade datauppsättningar som OData-flöden i Power BI-rapportserver](access-dataset-odata.md).

### <a name="scale-out"></a>Utskalning

Den här versionen stöder utskalning. Använd en belastningsutjämnare och ange servertillhörighet för bästa möjliga resultat. Observera att scenariot ännu inte har optimerats för utskalning, så du kommer eventuellt se att modeller replikeras över flera noder. Scenariot fungerar utan nätverkslastbalanseraren och fästsessioner. Dock visas inte bara en överanvändning av minnet i noderna när modellen blir inläst N gånger, utan prestandan kommer att bli långsammare mellan anslutningarna eftersom modellen strömmas när den når en ny nod mellan begärandena.  

### <a name="administrator-settings"></a>Administratörsinställningar

Administratörer kan ange följande egenskaper i de avancerade SSMS-egenskaperna för servergruppen:

* EnableCustomVisuals: Sant/falskt
* EnablePowerBIReportEmbeddedModels: Sant/falskt
* EnablePowerBIReportExportData: Sant/falskt
* MaxFileSizeMb: Standard är nu 1 000
* ModelCleanupCycleMinutes: Hur ofta den kontrollerar att modeller tas bort från minnet
* ModelExpirationMinutes: Hur lång tid det tar innan modellen upphör att gälla och tas bort, baserat på senaste användning
* ScheduleRefreshTimeoutMinutes: Hur länge datauppdateringen kan ta för en modell. Som standard är detta två timmar.  Det finns ingen fast övre gräns.

**Konfigurationsfilen rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>Utvecklings-API

Utvecklings-API:n (REST API) som introducerades för SSRS 2017 har utökats för Power BI-rapportservern så att den fungerar med både Excel- och .pbix-filer. Ett användningsområde kan vara att programmässigt ladda ned filer från servern, uppdatera dem och sedan publicera dem igen. Detta är det enda sättet för att exempelvis uppdatera Excel-arbetsböcker med PowerPivot-modeller.

Observera att det finns en ny separat API för stora filer som kommer att uppdateras i Power BI-rapportserverversionen för Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) och minnesfotavtryck för Power BI-rapportserver

Power BI-rapportservern är nu värd för SQL Server Analysis Services (SSAS) internt. Det är inte specifikt för schemalagd uppdatering. Att vara värd för SSAS kan avsevärt utöka minnesfotavtrycket för rapportservern. Konfigurationsfilen AS.ini är tillgänglig för servernoderna, så om du är bekant med SSAS kan du behöva uppdatera inställningarna, inklusive exempelvis maximal minnesgräns och diskcachelagring. Se [Serveregenskaper i Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) för mer information.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Visa och interagera med Excel-arbetsböcker

Excel och Power BI innehåller en uppsättning verktyg som är unik i branschen. Tillsammans innebär de att affärsanalytiker enklare kan samla, utforma, analysera och utforska data visuellt. Förutom att kunna se Power BI-rapporter i webbportalen kan företagsanvändarna nu göra detsamma med Excel-arbetsböcker i Power BI-rapportservern, vilket ger dem en enda plats där de publicerar och ser sitt självbetjänade Microsoft BI-innehåll.

Vi har publicerat en [genomgång för hur du lägger till Office Online Server (OOS) i förhandsvisningsmiljön för Power BI-rapportservern](excel-oos.md). Kunder med ett volymlicensieringskonto kan ladda ned OOS från Volume License Service Center utan kostnad med skrivskyddade funktioner. När konfigurationen är klar kan användarna se och interagera med Excel-arbetsböcker som:

* Inte har några externa datakällberoenden
* Har en live-anslutning till en extern datakälla för SQL Server Analysis Services
* Har en PowerPivot-datamodell

### <a name="support-for-new-table-and-matrix-visuals"></a>Stöd för nya visuella tabell- och matrisobjekt

Power BI-rapportserver har nu stöd för den nya Power BI-tabellen och visuella matrisobjekt. Om du vill skapa rapporter med dessa visuella objekt behöver du en uppdaterad version av Power BI Desktop för oktober 2017-versionen. Den kan inte installeras sida vid sida med Power BI Desktop (juni 2017). Om du vill ladda ned den senaste versionen av Power BI Desktop går du till [nedladdningssidan för Power BI-rapportserver](https://powerbi.microsoft.com/report-server/) och väljer **Avancerade alternativ för nedladdning**.

## <a name="june-2017"></a>Juni 2017

* Power BI-rapportserver görs allmänt tillgänglig (GA).

## <a name="may-2017"></a>Maj 2017

* Förhandsvisningen av Power BI-rapportserver blir tillgänglig
* Möjlighet att publicera Power BI-rapporter lokalt
  * stöd för anpassade visuella objekt
  * Stöd för **live-anslutningar med Analysis Services** för fler datakällor är på gång.
  * Power BI-mobilappen uppdateras för att kunna visa Power BI-rapporter som finns i Power BI-rapportserver
* Förbättrat samarbete i rapporter med kommentarer

## <a name="next-steps"></a>Nästa steg

Kontrollera dessa källor för att hålla dig uppdaterad om nya funktioner i Power BI-rapportservern.

* [Microsoft Power BI-bloggen](https://powerbi.microsoft.com/blog/)
* [SQL Server Reporting Services team-bloggen](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [YouTube-kanalen Guy in a Cube ](https://aka.ms/guyinacube)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
