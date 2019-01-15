---
title: Självstudier – Utsnitt i Power BI
description: Utsnitt i Power BI
author: v-thepet
manager: kvivek
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 10/25/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e2c9daf54ec18b53655043cd4a472674ee5123be
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295981"
---
# <a name="slicers-in-power-bi"></a>Utsnitt i Power BI
Du vill att rapportens läsare ska kunna se övergripande försäljningsmått, men också att de ska kunna lyfta fram prestanda för enskilda distriktschefer och olika tidsramar. Du kan skapa separata rapporter eller jämförande diagram, eller så kan du använda utsnitt. Ett utsnitt är en alternativ filtreringsmetod som begränsar den del av datauppsättningen som visas i övriga visualiseringar i en rapport. 

I den här självstudien används kostnadsfria [Exempel på detaljhandelsanalys](../sample-retail-analysis.md) för att visa hur du kan skapa, formatera och använda utsnitt för listor och datumutsnitt. Du kommer att upptäcka nya sätt att formatera och använda utsnitt. 

![utsnitt](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>När ska du använda ett utsnitt
Utsnitt är ett bra val när du vill:

* Visa vanliga eller viktiga filter på rapportarbetsytan för enklare åtkomst.
* Göra det lättare att se det aktuella filtrerade tillståndet utan att öppna listrutan. 
* Filtrera efter kolumner som är onödiga och dolda i datatabellerna.
* Skapa mer fokuserade rapporter genom att placera utsnitt bredvid viktiga visuella objekt.

Power BI-utsnitt har följande begränsningar:

- Utsnitt stöder inte indatafält.
- Utsnitt går inte att fästa på en instrumentpanel.
- Det stöds inte att gå in på detaljnivå för utsnitt.
- Utsnitt stöder inte visuella nivåfilter.

## <a name="create-slicers"></a>Skapa utsnitt

Om du vill skapa ett nytt utsnitt kan du välja utsnittsikonen och sedan välja datafältet att filtrera efter (eller dra den till rutan **Fält** i fönstret **Visualiseringar**). Du kan också välja eller dra datafältet först och skapa en visualisering och sedan välja utsnittsikonen och ändra visualiseringen till ett utsnitt. Olika datatyper skapar olika utsnittstyper med olika effekter och alternativ. 

Första gången du ändrar en rapport aktiveras knappen **Återställ till standard**. Det här är en påminnelse om att du har ändrat de ursprungliga rapportinställningarna. Om du navigerar bort från rapporten sparas ändringen (den är beständig). När du återvänder till rapporten behöver du inte göra ändringarna igen.  Om du i stället vill återställa rapporten till rapportförfattarens standardinställningar väljer du knappen **Återställ till standard** från den översta menyraden.

![Knappen Återgå till standard](media/power-bi-visualization-slicers/power-bi-reset-to-default.png)

> [!NOTE]
> Om knappen **Återställ till standard** fortfarande är inaktiverad beror det på att rapportförfattaren har inaktiverat funktionen för rapporten, eller så innehåller rapporten ett anpassat visuellt objekt. Hovra bara över knappen så visas en knappbeskrivning med en förklaring. 

**Skapa ett nytt utsnitt och filtrera data efter Distriktschef**

1. Öppna [Exempel på detaljhandelsanalys](../sample-retail-analysis.md) i Power BI Desktop eller Power BI-tjänsten. (Välj **Redigera rapport** högst upp till vänster i Power BI-tjänsten.)
2. Skapa ett nytt utsnitt genom att välja ikonen **Utsnitt**![utsnittsikon](media/power-bi-visualization-slicers/slicer-icon.png) i fönstret **Visualiseringar** på sidan **Översikt**. 
3. När du har valt det nya utsnittet fyller du det genom att välja **Distriktschef** under **Distrikt** i fönstret **Fält**. Det nya utsnittet är en lista med markeringsrutor framför namnen. 
    
    ![nytt utsnitt](media/power-bi-visualization-slicers/2-slicer.png)
    
4. Ändra storlek och dra utsnittet och andra element på arbetsytan så att du frigör utrymme för utsnittet. Observera att utsnittsobjekten klipps av om du gör utsnittet för litet. 
5. Välj namn för utsnittet och notera effekterna på sidans övriga visualiseringar. Avmarkera namnen och välj mer än ett namn genom att hålla ned **Ctrl**-tangenten. Om du väljer alla namn har det samma effekt som om du inte hade valt något namn. 

>[!TIP]
>Utsnittsobjekten i listan sorteras som standard i stigande alfanumerisk ordning. Om du vill ändra sorteringsordningen till fallande väljer du ellipsen (**...**) i utsnittets övre högra hörn och väljer **Sortera efter distriktschef** i listrutan. 

**Skapa ett nytt utsnitt och filtrera data efter datumintervall**

1. Om du vill skapa en ny visualisering släpper du **Tid** i fönstret Fält och drar **Månad** (eller **Datum** i Power BI-tjänsten) till rutan **Värden** i fönstret Visualiseringar.
2. Konvertera den nya visualiseringen till ett utsnitt genom att markera den nya visualiseringen och välja ikonen **Utsnitt**. Den här utsnittet är ett skjutreglage med ifyllt datumintervall.
    
    ![nytt intervallutsnitt](media/power-bi-visualization-slicers/2a-date-slicer.png)
    
4. Ändra storlek och dra utsnittet och andra element på arbetsytan så att du frigör utrymme för utsnittet. Observera att skjutreglaget anpassas efter utsnittets storlek, men det försvinner och datumen klipps bort om du gör utsnittet för litet. 
4. Välj olika datumintervall med skjutreglaget eller välj ett datumfält så att du kan skriva in ett värde eller öppna en kalender om du vill göra med precisa val. Observera effekterna på de övriga visualiseringarna på sidan.
    
    >[!NOTE]
    >Numeriska datatyper och datum-/tiddatatyper producerar skjutreglageutsnitt som standard. Från och med Power BI-uppdateringen i februari 2018 fäster skjutreglage för heltalsdata nu till helstalsvärden istället för att visa decimaler. 

>[!TIP]
>Även om datafältet **Månad** som standard ger ett **Mellan**-skjutreglageutsnitt, så kan du ändra det till andra utsnittstyper och urvalsalternativ. Om du vill ändra utsnittstyp för ett markerat utsnitt hovrar du över utsnittets övre högra område, släpper cirkumflexet som visas och väljer något av de andra alternativen, t.ex. **Lista** eller **Före**. Observera hur utsnittsalternativen och urvalsalternativen ändras. 

Mer information om hur du skapar utsnitt för datum och numeriska intervall finns i följande video och [Använda utsnittet för numeriska intervall i Power BI Desktop](../desktop-slicer-numeric-range.md).
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 

## <a name="control-which-page-visuals-are-affected-by-slicers"></a>Kontrollera vilka visuella objekt på sidan som påverkas av utsnitten
Normalt påverkar utsnitt på rapportsidorna alla övriga visualiseringar på sidan, inklusive varandra. När du väljer värden i listan och datumskjutreglagen som du just har skapat kan du se vilken inverkan de har på de övriga visualiseringarna. Filtrerade data utgör en skärningspunkt för de värden som du har valt i båda utsnitten. 

Du kan använda **Visuella interaktioner** om du vill förhindra att vissa sidvisualiseringar påverkas av andra. Diagrammet ”Total försäljningsvarians per FiscalMonth och distriktschef” hanteraren” på sidan **Översikt** visar övergripande jämförelsedata för distriktschefer per månad, vilket du vill alltid ska visas. Du kan använda **Visuella interaktioner** för att förhindra att utsnittsurval filtrerar det här diagrammet. 

1. Gör följande när du har valt utsnittet Distriktschef:
    - Välj menyn **Format** under **Visuella verktyg** i Power BI Desktop och välj sedan **Redigera interaktioner**.
    - I Power BI-tjänsten öppnar du listrutan **Visuella interaktioner** på menyraden och aktiverar **Redigera interaktioner**. 
   
   Filterkontroller ![filterkontroller](media/power-bi-visualization-slicers/filter-controls.png) visas ovanför alla andra visuella objekt på sidan. Alla **filter**ikoner är markerade initialt.
   
2. Välj ikonen **Ingen** ovanför diagrammet **Total försäljningsavvikelse efter FiscalMonth och distriktschef**, vilket förhindrar att utsnittet filtrerar det. 
3. Välj utsnittet **Månad** och sedan återigen ikonen **Ingen** ovanför diagrammet **Total försäljningsavvikelse efter FiscalMonth och distriktschef**, vilket förhindrar att utsnittet filtrerar det. När du nu väljer namn och datumintervall i utsnitten så förändras inte diagrammet Total försäljningsavvikelse efter FiscalMonth och distriktschef. 

Mer information om hur du redigerar interaktioner finns i [Visuella interaktioner i en Power BI-rapport](../service-reports-visual-interactions.md).

## <a name="sync-and-use-slicers-on-other-pages"></a>Synkronisera och använda utsnitt på andra sidor
Från och med Power BI-uppdateringen från februari 2018 kan du synkronisera ett utsnitt och använda det på några eller alla sidor i en rapport. 

I den aktuella rapporten innehåller sidan **Månatlig distriktsförsäljning** även utsnittet **Distriktschef**, men det är inte synkroniserat med det som du skapade på sidan **Översikt** (de två utsnitten kan ha olika objekturval). Sidan **Nya butiker** har bara ett **Butiksnamn**-utsnitt. Du kan synkronisera ditt nya **Distriktchef**-utsnitt till dessa sidor, så att utsnittsurvalen på en enskild sida påverkar visualiseringarna på alla tre sidorna. 

1. Välj **Synkronisera utsnitt** på **Visa**-menyn i Power BI Desktop (eller aktivera **Synkronisera utsnittsfönstret** i Power BI-tjänsten). Fönstret **Synkronisera utsnitt** visas. 
2. Välj utsnittet **Distriktschef** på sidan **Översikt**. Observera att sidan **Månatlig distriktsförsäljning** redan har markerats i kolumnen **Synlig**, eftersom det även finns ett Distriktschef-utsnitt på sidan, som dock inte har markerats i kolumnen **Synkronisera**. 
    
    ![synkronisera utsnitt](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
3. Välj sidan **Nya butiker** och sidan **Månatlig distriktsförsäljning** i kolumnen **Synkronisera** så att utsnittet **Översikt** kan synkroniseras till dessa sidor. 
    
3. Välj sidan **Nya butiker** i kolumnen **Synlig** och låt sidan **Månatlig distriktsförsäljning** vara markerad. 
4. Observera vilka effekterna blir när du synkroniserar utsnittet och gör det synligt på de övriga sidorna. Utsnittet **Distriktschef** på sidan **Månatlig distriktsförsäljning** visar samma val som på sidan **Översikt**. Urvalen i utsnittet **Distriktschef** på sidan **Nya butiker** påverkar de urval som är tillgängliga i utsnittet **Arkivnamn**. 
    
    >[!TIP]
    >Även om utsnittet till att börja med visas på de synkroniserade sidorna med samma storlek och placering som på den ursprungliga sidan, så kan du flytta, ändra storlek på och formatera synkroniserade utsnitt på de olika sidorna oberoende av varandra. 

>[!NOTE]
>Om du synkroniserar ett utsnitt till en sida, men inte gör det synligt på sidan, så filtrerar fortfarande de utsnittsurval som gjorts på de övriga sidorna informationen på sidan.
 
## <a name="format-slicers"></a>Formatutsnitt
Olika formateringsalternativ är tillgängliga beroende på vilken utsnittstyp det rör sig om. Med hjälp av **vågrät** orientering **dynamisk** layout och **objekt**färger kan du skapa knappar och paneler istället för standardlistobjekt och ändra storlek på utsnittsobjekt så att de passar olika skärmstorlekar och layouter.  

1. Visa formateringskontrollerna genom att välja ikonen **Format**-ikonen ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) i fönstret **Visualiseringar** när utsnittet **Distriktschef** har markerats på någon sida. 
    
    ![formatering](media/power-bi-visualization-slicers/3-format.png)
    
2. Välj listrutepilarna bredvid respektive kategori om du vill visa och redigera motsvarande alternativ. 

### <a name="general-options"></a>Allmänna alternativ
1. Välj rött under **Konturfärg** och ändra **Konturtjocklek** till ”2”. Då ställer du in färg och tjocklek för konturer eller understrykningar för rubrik och objekt, när det är aktiverat. 
2. **Lodrät** är standard under **Orientering**. Välj **Vågrät** om du vill skapa ett utsnitt med vågrätt ordnade paneler eller knappar, och rullningspilar om du vill få åtkomst till objekt som inte passar in i utsnittet.
    
    ![vågrät](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Aktivera **Dynamisk** layout om du vill ändra utsnittsobjektens storlek och placering beroende på skärmvy och utsnittsstorlek. Dynamisk layout för listutsnitt finns bara i vågrät orientering och förhindrar objekten från att beskäras på mindre skärmar. När det gäller intervallskjutreglage ändrar dynamisk formatering skjutreglagets format och ger möjlighet till mer flexibel storleksändring. Båda typerna av utsnitt bli filterikoner vid mycket små storlekar. 
    
    ![dynamisk](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >Ändringar av dynamisk layout kan åsidosätta specifik rubrik- och objektformatering som du anger. 
    
4. Ange utsnittets position och storlek med numerisk precision under **X-position**, **Y-position**, **Bredd** och **Höjd**, eller flytta och ändra storlek på utsnittet direkt på arbetsytan. Experimentera med olika objektstorlekar och arrangemang, och observera hur den dynamiska formateringen ändras.  

    ![vågräta knappar](media/power-bi-visualization-slicers/6-buttons.png)

Mer information om vågrät orientering och dynamisk layout finns i [Skapa ett dynamiskt utsnitt som du kan ändra storlek på i Power BI](../power-bi-slicer-filter-responsive.md).

### <a name="selection-controls-options-list-slicers-only"></a>Markeringsalternativ (endast listutsnitt)
1. **Visa Markera alla** har inställningen **Av** som standard. Ändra inställningen till **På** om du vill lägga till ett **Markera alla**-objekt i utsnittet som markerar eller avmarkerar alla objekt när det växlas. När alla objekt har markerats kan du avmarkera ett objekt genom att klicka eller trycka på det, vilket ger ett filter av ”är-inte”-typ. 
    
    ![markera alla](media/power-bi-visualization-slicers/7-select-all.png)
    
2. **Markera enstaka** har inställningen **På** som standard. Du kan markera ett objekt genom att klicka eller trycka på det och markera flera objekt genom att hålla ned **Ctrl**-tangenten och klicka eller trycka på dem. Ändra **Markera enstaka** till **Av** om du vill att det ska gå att markera flera objekt utan att hålla ned **Ctrl**-tangenten. Du avmarkerar ett objekt genom att klicka eller trycka på det igen. 

### <a name="header-options"></a>Rubrikalternativ
**Rubrik** har inställningen **På** som standard och datafältsnamnet visas överst i utsnittet. 
1. Formatera rubriktexten med **Teckenfärg** röd, **Textstorlek** 14 pt och **Teckensnittsfamilj** Arial Black. 
2. Välj **Endast nederkant** under **Kontur** om du vill skapa en understrykning med den storlek och färg du anger under alternativet **Allmänt**. 

### <a name="item-options-list-slicers-only"></a>Objektalternativ (endast listutsnitt)
1. Formatera objekttext och -bakgrund med **Teckenfärg** svart, **Bakgrund** ljusröd, **Textstorlek** 10 pt och **Teckensnittsfamilj** Arial. 
2. Välj **Ram** under **Kontur** om du vill rita en kantlinje runt varje objekt med den storlek och färg du anger under alternativet **Allmänt**. 
    
    ![formaterat](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Med **Orientering > Vågrät** visas avmarkerade objekt med valda text- och bakgrundsfärger, medan markerade objekt använder systemstandard, vanligtvis svarta bakgrunder med vit text.
    >- Med **Orientering > Lodrät** visas objekt alltid med angivna färger, och markeringsrutor är alltid svarta när de är markerade. 

### <a name="datenumeric-inputs-and-slider-options-range-slider-slicers-only"></a>Datum/numeriskt indata och skjutreglagealternativ (endast intervallskjutreglage för utsnitt)
- Alternativ för datum/numeriska indata är desamma som **Objekt**-alternativen för listutsnitt, med undantag för att det inte finns någon **Disposition** eller understrykning.
- Med skjutreglagealternativen kan du ange intervallskjutreglagets färg eller ställa in skjutreglaget på **Av**, vilket endast möjliggör numeriska indata.

### <a name="other-formatting-options"></a>Andra formateringsalternativ
De andra formateringsalternativen är inaktiverade som standard. När de ändras till **På**: 
- **Titel:** En titel (utöver och oberoende av rubriken) läggs till och formateras högst upp i utsnittet. 
- **Bakgrund:** En bakgrundsfärg läggs till i det övergripande utsnittet och dess transparens anges.
- **Lås höjd/bredd:** Utsnittets form behålls om dess storlek ändras.
- **Kantlinje:** En kantlinje på 1 bildpunkt läggs till runt utsnittet och dess färg anges. (Den här utsnittskantlinjen är separat från och påverkas inte av de allmänna konturinställningarna.) 

## <a name="next-steps"></a>Nästa steg
[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Tabeller i Power BI](power-bi-visualization-tables.md)

