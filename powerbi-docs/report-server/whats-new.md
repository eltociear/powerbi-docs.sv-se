---
title: Nyheter i Power BI-rapportserver
description: Läs mer om nyheterna i Power BI-rapportserver. Den här artikeln omfattar de viktiga funktionsområdena och uppdateras när nya objekt släpps.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: af737472b85dcfa05935aefa9ddd7a6fcbb746f2
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214371"
---
# <a name="whats-new-in-power-bi-report-server"></a>Nyheter i Power BI-rapportserver

Läs om nyheterna i Power BI-rapportserver och Power BI Desktop optimerat för Power BI-rapportserver. Den här artikeln omfattar de viktiga funktionsområdena och uppdateras med varje ny utgåva. Du kan läsa mer om nyheterna i Power BI-rapportserver i [ändringsloggen för Power BI-rapportserver](changelog.md).

Ladda ned [Power BI-rapportserver och Power BI Desktop optimerat för Power BI-rapportserver](https://powerbi.microsoft.com/report-server/).

## <a name="may-2020"></a>Maj 2020

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimerat för Power BI-rapportserver

Bland de viktigaste nyheterna i den här uppdateringen är hierarkiska utsnitt, visualisering av nedbrytningsträd och frågediagnostik. Det här är en fullständig lista över nya och uppdaterade funktioner. Mer information finns i [blogginlägget om Power BI-rapportserver från maj 2020](https://powerbi.microsoft.com/blog/power-bi-report-server-may-2020-feature-summary/). 

#### <a name="reporting"></a>Rapportering

- Hierarkiskt utsnitt
- Nya åtgärdstyper för knappar:

    - Sidnavigering
    - Visa detaljerad information

- Nu har knappar stöd för fyllningsbilder
- Sortering i flera kolumner för tabeller
- Dubbla axlar för linjediagram
- Rektangelmarkering för visualiseringar
- Villkorsstyrd formatering för summor och delsummor i tabeller och matriser
- Dialogrutan Anpassa tema
- Identifiering av villkorsstyrd formatering
- Nedbrytningsträd
- Uppdateringar av filterruta:

    - Ny upplevelse för filterruta
    - Sökning i filterfönster
    
#### <a name="modeling"></a>Modellering

- Nya DAX-funktioner:

    - FirstNonBlankValue
    - LastNonBlankValue
    - Coalesce

- DAX-standardavgränsare

#### <a name="visualizations"></a>Visualiseringar

- Nya visualiseringsikoner
- Bakgrundsskuggor i visualiseringar

#### <a name="data-preparation"></a>Förberedelse av data

- Frågediagnostik

#### <a name="other"></a>Annat

- Använda standardautentiseringsuppgifter för systemet för webbproxy

### <a name="power-bi-report-server"></a>Power BI-rapportserver

#### <a name="power-bi-visuals-api"></a>API för visuella Power BI-objekt

API-versionen som levereras med den här versionen är 3.2.

## <a name="january-2020"></a>Januari 2020

Mer information finns i blogginlägget om Power BI-rapportserver från januari 2020.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimerat för Power BI-rapportserver

Den här versionen innehåller många nya funktioner, som villkorsstyrd formatering för knappar, dataprofileringsförbättringar och fler formateringsinställningar för KPI:er och visuella tabellobjekt. Här följer en sammanfattning av uppdateringarna:

**Rapportering**

- Ange tabellkolumn eller matrisvärde som en anpassad URL
- Inställningar för visuell KPI-formatering
- Uppdateringar av filterfönsterfunktionen

**Analys**

- Knappar för villkorsstyrd formatering
- Läsa in mer för analys av insikter
- Ny DAX-funktion: Kvartal

**Förberedelse av data**

- Förbättringar av dataprofilering

**Övrigt**

- Nytt filformat: .pbids
- Prestandaförbättringar för modelleringsåtgärder

**Rapportering**

*Ange en tabellkolumn eller ett matrisvärde som en anpassad URL*

Du kan ange en tabellkolumn eller ett matrisvärde som en anpassad URL. Du hittar det här nya alternativet under kortet för villkorsstyrd formatering i formateringsfönstret.

*Inställningar för visuell KPI-formatering*

I och med den här månadens version så har KPI:er nya formateringsalternativ:

- Indikatortextformatering (teckensnittsfamilj, färg och justering)
- Trendaxeltransparens
- Mål- och avståndstextformat (etikettext, teckensnittsfamilj, färg och storlek)
- Avståndstextformat (etikettext, positiv riktning, teckensnittsfamilj, färg och storlek)
- Lägga till en datumetikett med formatering (teckensnittsfamilj, färg och storlek)

Du kan ange vissa av de här formateringsalternativen med villkorsstyrd formatering:

- Indikatorteckensnittsfärg
- Målteckensnittsfärg och färg för målavståndsteckensnitt
- Färgerna för bra/dålig/neutral status
- Datumteckensnittsfärg

*Uppdateringar av filterfönsterfunktionen*

Som en del av den allmänna tillgängligheten för den [senaste versionens](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane) nya filterfunktion har vi effektiviserat processen att överföra aktuella rapporter till det nya fönstret. När du öppnar Power BI-rapportserver för första gången visas en dialogruta för automatisk uppdatering av filterfönstret. Dessa uppdateringar inkluderar även banderoller i rapportservern när rapporterna måste migreras till den nya funktionen.

**Analys**

*Villkorsstyrd formatering för knappar*

Alla de här uppdateringarna för villkorsstyrd formatering är knapprelaterade. Nu kan du ange formatering för följande egenskaper dynamiskt:

- Teckenfärg för knapptext
- Knapptext
- Ikonlinjefärg
- Konturfärg
- Fyllningsfärg
- Knappbeskrivning (under åtgärdskortet)

*Läsa in mer för analys av insikter*

När du kör analysfunktionen för att hitta insikter i dina data, som att exempelvis förklara ökning, så körs maskininlärningsmodellerna endast under en viss fastställd tidsperiod, så att du får insikterna inom rimlig tid. Om det är mycket data att analysera så kan du nu välja att fortsätta att köra analysen efter den första tidsgränsen.

*Ny DAX-funktion: Kvartal*

Den här månaden har vi den nya DAX-funktionen Kvartal. Funktionen Kvartal returnerar det kvartal som motsvarar det angivna datumet.

**Förberedelse av data**

*Förbättringar av dataprofilering*

Den här månaden introducerar vi ett par betydande förbättringar av Power Query-redigerarens dataprofileringsfunktioner:

- Flera grupperingsalternativ för kolumnprofilsfönstervärdets visuella distributionsobjekt, särskilt efter kolumntyp, förutom de befintliga "efter värde"-kriterierna.
- Text: Efter textlängd (antal tecken).
- Tal: Efter tecken (positivt/negativt) och paritet (jämn/udda).
- Datum/DateTime: Per år, månad, dag, vecka, veckodag, fm/em-tid och timma.
- Och mera för andra datatyper, t.ex. logiska sant/falskt.

*Filtrera alternativ*

Du kan redan utnyttja flera typspecifika grupperingskriterier i distributions fönstret för Kolumnprofiler. Nu kan du också filtrera inifrån bildtexterna för vart och ett av värdena i distributionsdiagrammet när du använder gruppvillkor. I fönstret Dataprofiler för en Datum/DateTime-kolumn kan du t.ex. undanta alla värden som infaller under en viss månad.

**Övrigt**

*Nytt filformat: .pbids*

Den här månaden släpper vi ett nytt filformat, .pbids, med vilket du kan effektivisera funktionen Hämta data för din organisations rapportskapare. Vi rekommenderar att administratörer skapar dessa filer för de anslutningar som används ofta.

När en rapportskapare öppnar en .pbids-fil, så visas en autentiseringsuppmaning i Power BI Desktop för anslutning till den datakälla som anges i filen. Sedan väljer användaren de tabeller som ska läsas in i modellen. De kan också behöva välja databasen om någon sådan inte har angetts i filen. Därifrån kan rapportskaparen börja skapa visualiseringar.

Mer information och exempel finns i avsnittet [Använda .pbids-filer för att hämta data](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) i artikeln "Datakällor i Power BI Desktop".

*Prestandaförbättringar för modelleringsåtgärder*

Vi har gjort en prestandaförbättring i Analysis Services-motorn, så att modelleringsåtgärderna, som att lägga till mått eller beräknade kolumner eller skapa relationer, kan genomföras snabbare. Hur stora förbättringar du ser beror på modellen, men vi har sett tjugofaldiga prestandaförbättringar för vissa kunder när det gäller åtgärder som att öppna en fil eller lägga till ett mått.

Detta är allt när det gäller januariversionen 2020 av Power BI-rapportserver. Fortsätt att skicka feedback och glöm inte att [rösta på de funktioner som du vill se i Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Power BI-rapportserver

#### <a name="export-to-excel-from-power-bi-reports"></a>Exportera till Excel från Power BI-rapporter

Att exportera till Excel från en Power BI-rapport i Power BI-rapportserver fungerar nu på samma sätt som när du exporterar till Excel från en Power BI-rapport i Power BI-tjänsten. Du kan exportera direkt till Excels .xlsx-format, och exportgränsen ligger på 150 000 rader.

#### <a name="azure-sql-managed-instance-support"></a>Support för Azure SQL-hanterad instans

Nu kan du vara värd för en databaskatalog som används för Power BI-rapportserver i en Azure SQL-hanterad instans (MI) som finns i en virtuell dator eller i ditt datacenter. Stödet är begränsat till att använda databasautentiseringsuppgifter för anslutningen till SQL MI.

#### <a name="power-bi-premium-dataset-support"></a>Power BI Premium-datamängdssupport

Du kan ansluta till Power BI-datamängder med Microsoft Report Builder eller SQL Server Data Tools (SSDT). Sedan kan du publicera dessa rapporter till Power BI-rapportserver med hjälp av en SQL Server Analysis Services-anslutning. Användarna måste använda ett lagrat Windows-användarnamn och lösenord för att kunna aktivera scenariot.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>AltText-stöd (alternativ text) för rapportelement

När du redigerar rapporter kan du använda knappbeskrivningar för att ange text för varje element i rapporten. Skärmläsartekniker kan använda dessa knappbeskrivningar.

#### <a name="azure-active-directory-application-proxy-support"></a>Support för Azure Active Directory-programproxy

Med Azure Active Directory-programproxy behöver du inte längre hantera din egen webbprogramproxy när du ska tillåta säker åtkomst via webben eller mobilappar. Mer information finns i [Fjärråtkomst till lokala program via Azure Active Directory-programproxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="custom-headers"></a>Anpassade rubriker

Anger rubrikvärden för alla URL:er som matchar det angivna regex-mönstret. Användare kan uppdatera det anpassade rubrikvärdet med giltig XML och ange rubrikvärden för de valda begärans-URL:erna. Administratörer kan lägga till ett valfritt antal rubriker i XML-filen. Mer information finns i [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) i Reporting Services-artikeln **Serveregenskaper, sidan Avancerat**.

#### <a name="transparent-database-encryption"></a>Transparent databaskryptering

Power BI-rapportserver stöder nu transparent databaskryptering för Power BI-rapportserverns databaskatalog för Enterprise- och Standard-utgåvorna.

#### <a name="power-bi-visuals-api"></a>API för visuella Power BI-objekt

Den API-version som levereras med den här versionen är 2.6.0.

#### <a name="microsoft-report-builder-update"></a>Microsoft Report Builder-uppdatering

Den nyligen utgivna versionen av Report Builder är helt kompatibel med Reporting Services-versionerna från 2016, 2017 och 2019. Den är också kompatibel med alla släppta versioner av Power BI-rapportserver som stöds.

## <a name="september-2019"></a>September 2019

Se inlägget om [Power BI-rapportserver september 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) för information om alla nya funktioner.

September 2019-uppdateringen av Power BI-rapportserver är fullspäckad med Power BI-rapportfunktioner. Här följer några höjdpunkter:

- **Filter på visuellt objekt-nivå för utsnitt** Du kan lägga till ett filter på visuellt objekt-nivå i utsnitt. Det fungerar på samma sätt som vilket annat filter på visuellt objekt-nivå som helst och filtrerar bara själva utsnittet och inga andra visuella objekt. Filtret är användbart för att filtrera bort tomma värden eller om du vill använda måttfilter.
- **Ikonuppsättningar för tabell och matris** Med KPI-ikoner kan du ange regler för att visa olika uppsättningar av ikoner i din tabell och matris, liknande ikonuppsättningar i Excel.
- **Gruppering av visuella objekt** Nu kan du gruppera visuella objekt, former, textrutor, bilder och knappar på en rapportsida precis som i PowerPoint. När du grupperar objekt kan du flytta och ändra storlek på dem alla. Med gruppering blir det enklare att arbeta i en rapport med många objekt i flera lager på varje sida.
- **Nya standardteman** För att följa de nya JSON-alternativen för teman uppdaterar vi teman tillgängliga för rapporter och ändrar standardtemat för nya rapporter. Det nya temat är både mer i linje med Microsofts designspråk och följer bästa designmetoder för visuella objekt. 
- **Uppdaterad fönsterdesign** Vi har uppdaterat mycket av vårt gränssnitt. Vi har uppdaterat alla fönster, sidfoten och vyväxlaren till en ljusare färg, uppdaterat avståndet och introducerat nya ikoner. Den nya designen är det första steget mot att uppdatera hela gränssnittet.

Här är hela listan över funktioner. 

### <a name="reporting"></a>Rapportering

- Uppdaterad fönsterdesign
- Filter för utsnitt för visuellt objekt
- Sortering i prestandaanalyseraren
- Knappbeskrivning för det visuella objektets rubrik
- Total anpassning av etiketter för tabeller och matriser
- Stöd för synkroniserade utsnitt för hierarkiutsnitt
- Konsekvent teckenstorlek för flera visuella objekt
- Ikonuppsättningar för tabeller och matriser
- Procentstöd för villkorsstyrd formatering efter regler
- Ny filterruta är nu allmänt tillgänglig
- Stöd för datafärger vid användning av uppspelningsaxel i punktdiagram
- Prestandaförbättringar vid användning av relativt datum och listrutor för utsnitt
- Gruppering av visuella objekt
- Färg- och textklasser i teman
- Nya standardteman

### <a name="analytics"></a>Analys

- Anpassade formatsträngar
- Uppdaterade alternativ för villkorsstyrd formatering

    - Bakgrund och rubrikfärger för visuellt objekt
    - Kortfärger
    - Fyllning och färger för mätare
    - Alternativtext
    - Färg på kantlinje

- Varningar för villkorsstyrd formatering
- Förbättrad ökad detaljnivå
- Nya DAX-uttryck: REMOVEFILTERS och CONVERT
- Ny DAX-jämförelseoperator, ==

### <a name="data-preparation"></a>Förberedelse av data

- Förbättringar av M Intellisense
- Ny transformering: Dela kolumn efter positioner
- Kopiera till urklipp från dataprofilering


## <a name="may-2019"></a>Maj 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop för Power BI-rapportservern

Se inlägget om [Power BI-rapportserver maj 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) för information om alla nya funktioner.

Här följer några höjdpunkter:

#### <a name="performance-analyzer"></a>Prestandaanalys 

Om din rapport körs långsammare än förväntat provar du Prestandaanalys i Power BI Desktop. När du startar den skapas en loggfil med information om varje åtgärd du utför i rapporten. Läs mer om [Prestandaanalys](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Ny modelleringsvy

I den nya Modelleringsvyn i Power BI Desktop kan du visa och arbeta med komplexa datauppsättningar som innehåller många tabeller. Höjdpunkterna omfattar flera diagramlayouter och massredigering av kolumner, mått och tabeller. Läs mer om [Modelleringsvyn](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Tillgänglig visuell interaktion

Nu kan du komma åt datapunkter på många av de inbyggda visuella objekten med hjälp av tangentbordsnavigering. Läs mer om [tillgänglighet i Power BI-rapporter](../create-reports/desktop-accessibility-overview.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Rubriker för villkorsstyrd formatering och webb-URL-åtgärder

Power BI-rapporter är interaktiva. Det är logiskt att rubriker i en rapport är dynamiska, för att spegla den aktuella statusen för rapporten. Du kan använda samma uttrycksbunden formatering för att göra URL:erna för dina knappar, former och bilder dynamiska. Läs mer om [uttrycksbaserade rubriker](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Korsmarkera enligt axeletiketter

Välj axelkategorietiketterna i ett visuellt objekt för att korsmarkera de andra elementen på en sida, precis som du skulle välja datapunkterna i ett visuellt objekt. Läs mer om [korsmarkering](../create-reports/power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Alla nya funktioner

Här är listan över alla nya funktioner:

#### <a name="reporting"></a>Rapportering

- Korsmarkera på en enskild punkt i linjediagram 
- Automatiskt radbyte i rubriker 
- Uppdatera standard visuell interaktion till korsfiltrering
- Avrundade hörn för visuella kantlinjer 
- Välj enskilt utsnitt  
- Stöd för termisk karta för Bing-kartor  
- Korsmarkera enligt axeletiketter  
- Standardformatering för knappbeskrivning  
- Statiskt webb-URL-stöd för knappar, former och bilder  
- Alternativ för sidjustering   
- Förbättringar av markeringspanelen  
- Tillgänglig visuell interaktion  
- Villkorsstyrd formatering av visuella objekts rubriker  
- Villkorsstyrd formatering av webbadressåtgärder för knappar, former och bilder
- Fönstret Prestandaanalys
- Tangentbordsnavigering i tabeller och matriser
- Kontroll över etiketters position i raddata
- Kontroll över textstorleken i visuella KPI-indikeringar

#### <a name="analytics"></a>Analys

- Visa datum som en hierarki är nu allmänt tillgängligt  

#### <a name="modeling"></a>Modellering

- Ny modelleringsvy är nu allmänt tillgänglig
- Nya DAX-funktioner
- Uppdatering av funktionen ALLSELECTED DAX
- Inaktivera automatisk datering av tabeller i nya rapporter

### <a name="power-bi-report-server"></a>Power BI-rapportserver

#### <a name="support-for-trusted-visuals"></a>Stöd för betrodda visuella objekt

Vi har lagt till stöd för betrodda visuella objekt i Power BI-rapportserver. För närvarande stöds visuella Mapbox- och PowerOn-objekt. ESRI, Visio och PowerApps stöds inte för den här versionen.)

#### <a name="improved-security-features"></a>Förbättrade säkerhetsfunktioner

**RestrictedResourceMimeTypeForUpload**, som administratörer kan använda för att ange en kommaavgränsad lista över förbjudna mime-typer, till exempel text/html.

## <a name="january-2019"></a>Januari 2019

Stöd för dessa funktioner i Power BI-rapporter:

[**Säkerhet på radnivå**](row-level-security-report-server.md) Konfiguration av säkerhet på radnivå (RLS) med Power BI-rapportserver kan begränsa dataåtkomst för givna användare. Filter begränsar åtkomst till data på radnivå och du kan definiera filter inom roller.

[**Expandera eller komprimera på matrisens radrubriker**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Vi har lagt till möjligheten att expandera eller komprimera enskilda radrubriker, en av de mest efterfrågade visuella funktionerna.

[**Kopiera och klistra in mellan pbix-filer**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Du kan kopiera visuella objekt mellan pbix-filer, antingen från snabbmenyn för det visuella objektet eller med standardkortkommandot Ctrl + C och klistra in dem i en annan rapport med Ctrl + V.

[**Smarta justeringsstödlinjer**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Du ser smarta justeringsstödlinjer när du flyttar objekt på rapportsidan, precis som i PowerPoint, så att du kan justera allt på sidan. Du ser smarta stödlinjer när du drar eller ändrar storlek på något på sidan. När du flyttar ett objekt nära ett annat fästs det på en plats i linje med det andra objektet.

**Hjälpmedelsfunktioner** För många hjälpmedelsfunktioner att lista: till exempel [fältlista med stöd för hjälpmedel](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Fältlistrutan är helt åtkomlig. Du kan navigera i rutan med enbart tangentbordet och en skärmläsare och använda snabbmenyn för att lägga till fält på rapportsidan.

#### <a name="power-bi-visuals"></a>Visuella objekt för Power BI

- Den API-version som levereras med den här versionen är 2.3.0.

### <a name="administrator-settings"></a>Administratörsinställningar

Administratörer kan ange följande egenskaper i de avancerade SSMS-egenskaperna för servergruppen:

**AllowedResourceExtensionsForUpload** Ange tillägg av resurser som kan laddas upp till rapportservern. Filnamnstillägg för inbyggda filtyper som &ast;.rdl och &ast;.pbix behöver inte inkluderas. Standardvärdet är ”&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx”. 

**SupportedHyperlinkSchemes** Anger att en kommaavgränsad lista över URI-scheman som är tillåtna måste definieras i hyperlänkåtgärder som tillåts att återges eller ”&ast;” för att aktivera alla hyperlänkscheman. Inställningen ”http,https” skulle exempelvis tillåta hyperlänkar till ”https://www. contoso.com”, men ta bort hyperlänkar till ”mailto:bill@contoso.com” eller ”javascript:window.open(”www.contoso.com”, ”_tomt”)”. Standardvärdet är ”&ast;”.

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

#### <a name="power-bi-visuals"></a>Visuella objekt för Power BI

- Den API-versionen som levereras med den här versionen är 1.13.0.

- Nu kan visuella Power BI-objekt återställas till en tidigare version som är kompatibel med den aktuella versionen av server-API (om tillgängligt).

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

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Regelbaserad villkorsstyrd formatering för tabeller och matriser](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Skapa regler för att villkorligt ange färg på bakgrunden eller teckenfärg för en kolumn baserat på särskild affärslogik i din tabell eller matris.

#### <a name="show-and-hide-pages"></a>[Visa och dölja sidor](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Du kanske vill att läsarna ska ha åtkomst till din rapport, men vissa av sidorna är inte riktigt klara. Nu kan du dölja dem tills du är färdig med dem. Eller så kan du dölja sidor från den normala navigeringen och låta läsarna navigera till dem via bokmärken eller genom att visa mer detaljerad information.

#### <a name="bookmarking"></a>[Skapa bokmärken](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Du kan använda bokmärken för att skapa en berättelse med data i din rapport.

- [Korsmarkering för bokmärken](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): Bokmärken sparar och visar det korsmarkerade tillståndet för rapportsidan vid tidpunkten då du skapade bokmärket.
- [Ökad flexibilitet för bokmärken](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): Bokmärken återspeglar egenskaperna som du anger i din rapport och påverkar endast de visuella objekt som du väljer.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Välja flera datapunkter över flera diagram](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Välj flera datapunkter i flera diagram och tillämpa korsfiltrering på hela sidan.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Synkronisera utsnitt över flera sidor i en rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Ett utsnitt kan tillämpas på en, två eller fler sidor i en rapport.

#### <a name="quick-measures"></a>[Snabbmått](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Skapa nya mått baserat på befintliga mått och numeriska kolumner i en tabell.

#### <a name="drilling-down-filters-other-visuals"></a>[Vid visning av detaljerad information filtreras andra visuella objekt](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

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

Du kan öppna och redigera Power BI-rapportfiler (.pbix) från servern, men du kommer tillbaka till den ursprungliga fil som du överförde. **Om data har uppdaterats av servern så uppdateras de inte när du först öppnar filen första gången**. Du måste uppdatera den lokalt manuellt för att se ändringen.

### <a name="large-file-uploaddownload"></a>Uppladdning/nedladdning av stora filer

Du kan ladda upp filer upp till 2 GB i storlek, även om den här gränsen som standard är 1 GB i rapportserverinställningarna i SQL Server Management Studio (SSMS).  De här filerna lagras i databasen på samma sätt som för SharePoint och det krävs ingen särskild konfiguration för SQL Server-katalogen.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Åtkomst till delade datauppsättningar som OData-flöden

Du kan komma åt delade datauppsättningar från Power BI Desktop med ett OData-flöde. Mer information finns i [Åtkomst till delade datauppsättningar som OData-flöden i Power BI-rapportserver](access-dataset-odata.md).

### <a name="scale-out"></a>Utskalning

Den här versionen stöder utskalning. Använd en belastningsutjämnare och ange servertillhörighet för bästa möjliga resultat. Scenariot har ännu inte optimerats för utskalning, så du kan eventuellt komma att se modeller replikeras över flera noder. Scenariot fungerar utan nätverkslastbalanseraren och fästsessioner. Dock visas inte bara en överanvändning av minnet i noderna när modellen läses in N gånger, utan prestandan blir långsammare mellan anslutningarna eftersom modellen strömmas när den når en ny nod mellan begärandena.  

### <a name="administrator-settings"></a>Administratörsinställningar

Administratörer kan ange följande egenskaper i de avancerade SSMS-egenskaperna för servergruppen:

- EnableCustomVisuals: Sant/falskt
- EnablePowerBIReportEmbeddedModels: Sant/falskt
- EnablePowerBIReportExportData: Sant/falskt
- MaxFileSizeMb: Standard är nu 1 000
- ModelCleanupCycleMinutes: Hur ofta den kontrollerar att modeller tas bort från minnet
- ModelExpirationMinutes: Hur lång tid det tar innan modellen upphör att gälla och tas bort, baserat på senaste användning
- ScheduleRefreshTimeoutMinutes: Hur länge datauppdateringen kan ta för en modell. Standardvärdet är två timmar.  Det finns ingen fast övre gräns.

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

Det finns ett nytt separat API för stora filer som kommer att uppdateras i Power BI-rapportserverversionen för Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) och minnesfotavtryck för Power BI-rapportserver

Power BI-rapportservern är nu värd för SQL Server Analysis Services (SSAS) internt. Det är inte specifikt för schemalagd uppdatering. Att vara värd för SSAS kan avsevärt utöka minnesfotavtrycket för rapportservern. Konfigurationsfilen AS.ini är tillgänglig för servernoderna, så om du är bekant med SSAS kan du behöva uppdatera inställningarna, inklusive exempelvis maximal minnesgräns och diskcachelagring. Se [Serveregenskaper i Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) för mer information.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Visa och interagera med Excel-arbetsböcker

Excel och Power BI innehåller en uppsättning verktyg som är unik i branschen. Tillsammans innebär de att affärsanalytiker enklare kan samla, utforma, analysera och utforska data visuellt. Förutom att kunna se Power BI-rapporter i webbportalen kan företagsanvändarna nu göra detsamma med Excel-arbetsböcker i Power BI-rapportservern, vilket ger dem en enda plats där de publicerar och ser sitt självbetjänade Microsoft BI-innehåll.

Vi har publicerat en [genomgång för hur du lägger till Office Online Server (OOS) i förhandsvisningsmiljön för Power BI-rapportservern](excel-oos.md). Kunder med ett volymlicensieringskonto kan ladda ned OOS från Volume License Service Center utan kostnad med skrivskyddade funktioner. När konfigurationen är klar kan användarna se och interagera med Excel-arbetsböcker som:

- Inte har några externa datakällberoenden
- Har en live-anslutning till en extern datakälla för SQL Server Analysis Services
- Har en PowerPivot-datamodell

### <a name="support-for-new-table-and-matrix-visuals"></a>Stöd för nya visuella tabell- och matrisobjekt

Power BI-rapportserver har nu stöd för den nya Power BI-tabellen och visuella matrisobjekt. Om du vill skapa rapporter med dessa visuella objekt behöver du en uppdaterad version av Power BI Desktop för oktober 2017-versionen. Den kan inte installeras sida vid sida med Power BI Desktop (juni 2017). Om du vill ladda ned den senaste versionen av Power BI Desktop går du till [nedladdningssidan för Power BI-rapportserver](https://powerbi.microsoft.com/report-server/) och väljer **Avancerade alternativ för nedladdning**.

## <a name="june-2017"></a>Juni 2017

- Power BI-rapportserver görs allmänt tillgänglig (GA).

## <a name="may-2017"></a>Maj 2017

- Förhandsvisningen av Power BI-rapportserver blir tillgänglig
- Möjlighet att publicera Power BI-rapporter lokalt
  - stöd för visuella Power BI-objekt
  - Stöd för **live-anslutningar med Analysis Services* – fler datakällor är på gång.
  - Power BI-mobilappen uppdateras för att kunna visa Power BI-rapporter som finns i Power BI-rapportserver
- Förbättrat samarbete i rapporter med kommentarer

## <a name="next-steps"></a>Nästa steg

Kontrollera dessa källor för att hålla dig uppdaterad om nya funktioner i Power BI-rapportservern.

- [Microsoft Power BI-bloggen](https://powerbi.microsoft.com/blog/)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
