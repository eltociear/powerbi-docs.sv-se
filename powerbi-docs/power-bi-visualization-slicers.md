---
title: "Utsnitt i Power BI (självstudie)"
description: "Självstudie: Utsnitt i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/05/2018
ms.author: v-thepet
LocalizationGroup: Visualizations
ms.openlocfilehash: cfa4c0f17c67a036b7d01744da1b5247345c493a
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="slicers-in-power-bi-tutorial"></a>Utsnitt i Power BI (självstudie)
En säljchef vill kunna titta på flera mått för hela divisionen och för varje enskild distriktschef. Hon skulle kunna skapa en separat rapport för varje chef eller använda ett utsnitt. Ett utsnitt begränsar den del av datauppsättningen som visas i andra visualiseringar i en rapport. Utsnitt är ett annat sätt att filtrera.

I den här självstudien används kostnadsfria [Exempel på detaljhandelsanalys](sample-retail-analysis.md) för att gå igenom hur du skapar och formaterar ett utsnitt och använder det för att filtrera en rapport. Du kommer att upptäcka nya sätt att formatera och använda utsnitt. 

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

## <a name="create-a-slicer"></a>Skapa ett utsnitt

I den här självstudien används ett listutsnitt. Numeriska datatyper och datum/tid-datatyper kan ha intervallutsnitt. I [Använda det numeriska intervallutsnittet i Power BI Desktop](desktop-slicer-numeric-range.md) och följande video finns mer information om hur du skapar och använder intervallutsnitt.
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>

1. Öppna [Exemplet detaljhandelsanalys](sample-retail-analysis.md) i [redigeringsvyn](service-interact-with-a-report-in-editing-view.md) och [lägg till en ny rapportsida](power-bi-report-add-page.md) i Power BI Desktop eller Power BI-tjänsten.
2. Skapa en ny visualisering genom att välja **Distriktchef** under Distrikt i fönstret Fält.
    
    ![nytt diagram](media/power-bi-visualization-slicers/1-new-vis.png)
    
3. Konvertera den nya visualiseringen till ett utsnitt genom att välja ikonen **Utsnitt** ![Ikonen Utsnitt](media/power-bi-visualization-slicers/slicer-icon.png) i fönstret Visualiseringar. 
    
    ![konvertera till utsnitt](media/power-bi-visualization-slicers/2-slicer.png)

Du kan också skapa ett nytt utsnitt genom att välja ikonen Utsnitt och sedan fylla i det genom att välja eller dra ett datafält till rutan Fält.

>[!TIP]
>Du kan sortera listutsnittsobjekt efter datavärden. Sortera utsnittsobjekt i omvänd alfabetisk ordning genom att välja ellipsen (...) i det övre högra hörnet i utsnittet och välja **Sortera efter Distriktchef**. Inställningen är stigande alfabetisk ordning som standard, men växlar mellan stigande och fallande ordning. 

## <a name="format-the-slicer"></a>Formatera utsnittet
Använd visuell formatering i utsnittet Distriktchef.
1. Visa formateringskontrollerna genom att välja ikonen Format ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) i fönstret Visualiseringar när utsnittet är markerat. 
    
    ![formatering](media/power-bi-visualization-slicers/3-format.png)
    
2. Klicka på pilarna bredvid varje kategori om du vill visa och redigera alternativen. 

### <a name="general-options"></a>Allmänna alternativ
1. Välj rött under **Konturfärg** och ändra **Konturtjocklek** till ”2”. Då ställer du in färg och tjocklek för konturer eller understrykningar för rubrik och objekt, när det är aktiverat. 
2. Under Orientering är Lodrätt standard, som skapar ett lodrätt listutsnitt med markeringsrutor före objekten. Välj **Vågrätt** om du vill skapa ett utsnitt med vågrätt ordnade objekt. Vågrät orientering kan ge olika placering av text, knappar eller paneler, beroende på utsnittets storlek, form och objektformatering. 
    
    ![vågrät](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Aktivera **Dynamisk** layout, som ändrar storlek och placering för vågräta utsnittsobjekt för att matcha utsnittets storlek och form. Om utsnittet är mycket litet blir det en filterikon. 
    
    ![dynamisk](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >Ändringar av dynamisk layout kan åsidosätta specifik rubrik- och objektformatering som du anger. 
    
4. Ange utsnittets position och storlek med numerisk precision under **X-position**, **Y-position**, **Bredd** och **Höjd**, eller flytta och ändra storlek på utsnittet direkt på arbetsytan, för att skapa olika objektstorlekar och -placeringar, till exempel en vågrät rad med knappar. 

    ![vågräta knappar](media/power-bi-visualization-slicers/6-buttons.png)

Mer information om vågrät orientering och dynamisk formatering finns i [Skapa ett dynamiskt utsnitt som du kan ändra storlek på i Power BI](power-bi-slicer-filter-responsive.md).

### <a name="selection-controls-options"></a>Alternativ för valkontroller
1. Visa Markera alla är inaktiverat som standard. Ändra det till **På** om du vill lägga till ett Markera alla-objekt i utsnittet som markerar eller avmarkerar alla objekt när det växlas. När alla objekt har markerats kan du avmarkera ett objekt genom att klicka på det, vilket ger ett filter av ”är-inte”-typ. 
    
    ![markera alla](media/power-bi-visualization-slicers/7-select-all.png)
    
2. Markera enstaka är aktiverat som standard. Du kan markera ett objekt genom att klicka på det och markera flera objekt genom att hålla ned CTRL-tangenten och klicka på dem. Ändra Markera enstaka till **Av** om du vill att det ska gå att markera flera objekt utan att hålla ned CTRL-tangenten. Du avmarkerar ett objekt genom att klicka på det igen. 

### <a name="header-options"></a>Rubrikalternativ
Rubriken är aktiverad som standard, och datafältnamnet visas överst i utsnittet. 
1. Formatera rubriktexten med **Teckenfärg** röd, **Textstorlek** 14 pt och **Teckensnittsfamilj** Arial Black. 
2. Välj **Endast nederkant** under Kontur för att skapa en understrykning med den storlek och färg du anger under Allmänna alternativ. 

### <a name="item-options"></a>Objektalternativ
1. Formatera objekttext och -bakgrund med **Teckenfärg** svart, **Bakgrund** ljusröd, **Textstorlek** 10 pt och **Teckensnittsfamilj** Arial. 
2. Välj **Ram** under Kontur för att rita en kantlinje runt varje objekt med den storlek och färg du anger under Allmänna alternativ. 
    
    ![formaterat](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Med vågrät orientering visas avmarkerade objekt med valda text- och bakgrundsfärger, medan markerade objekt använder systemstandard, vanligtvis svarta bakgrunder med vit text. 
    >- Med lodrät orientering visas objekt alltid med angivna färger, och markeringsrutor är alltid svarta när de är markerade. 

### <a name="other-formatting-options"></a>Andra formateringsalternativ
De andra formateringsalternativen är inaktiverade som standard. När de ändras till **På**: 
- **Titel:** En titel (utöver och oberoende av rubriken) läggs till och formateras högst upp i utsnittet. 
- **Bakgrund:** En bakgrundsfärg läggs till i det övergripande utsnittet och dess transparens anges.
- **Lås höjd/bredd:** Utsnittets form behålls om dess storlek ändras.
- **Kantlinje:** En kantlinje på 1 bildpunkt läggs till runt utsnittet och dess färg anges. (Den här utsnittskantlinjen är separat från och påverkas inte av de allmänna konturinställningarna.) 

## <a name="sync-and-use-the-slicer-on-other-pages"></a>Synkronisera och använda utsnittet på andra sidor
Från och med Power BI-uppdateringen från februari 2018 kan du synkronisera ett utsnitt och använda det på några eller alla sidor i en rapport. 
1. Med utsnittet Distriktchef markerat går du till menyn Visa och väljer **Synkronisera utsnitt** i Power BI Desktop eller aktiverar **Synkronisera utsnittsfönstret** i Power BI-tjänsten. Fönstret Synkronisera utsnitt visas. 
    
    ![synkronisera utsnitt](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
2. I den första kolumnen väljer du **Översikt** och eventuella andra sidor som du vill att utsnittet ska synkroniseras till, eller klickar på **Lägg till i alla** om du vill att utsnittet ska synkroniseras till alla rapportsidor.  
3. I nästa kolumn väljer du **Översikt** och eventuella andra sidor där du vill att utsnittet ska visas. 
4. Växla till sidan **Översikt** och observera utsnittet och dess påverkan på de andra visuella objekten på sidan. 
    - Markera och avmarkera olika objekt och observera hur de andra visuella objekten på sidan ändras. Markerade objekt på en sida visas på alla synkroniserade sidor.
    - Ändra storlek, form, position och/eller formatering för utsnittet på sidan Översikt. Utsnittets formatering på andra synkroniserade sidor ändras inte. 

### <a name="control-which-page-visuals-are-affected-by-the-slicer"></a>Kontrollera vilka visuella objekt på sidan som påverkas av utsnittet
Som standard påverkar ett utsnitt på en rapportsida alla andra visualiseringar på den sidan. Använd **Visuella interaktioner** om du vill förhindra att vissa sidvisualiseringar påverkas.

1. Gör följande på sidan **Översikt**, med utsnittet markerat:
    - I Power BI Desktop klickar du på menyn Format under Visuella verktyg och väljer **Redigera interaktioner**.
    - I Power BI-tjänsten öppnar du listrutan **Visuella interaktioner** på menyraden och aktiverar **Redigera interaktioner**. 
    
    Filterkontroller visas ovanför alla andra visuella objekt på sidan. ![filterkontroller](media/power-bi-visualization-slicers/filter-controls.png)
    
2. Välj ikonen **Ingen** ovanför ett visuellt objekt om du vill att utsnittet ska sluta filtrera det. Välj ikonen **Filter** om du vill att utsnittet ska börja filtrera det visuella objektet igen. 

Mer information om hur du redigerar interaktioner finns i [Visuella interaktioner i en Power BI-rapport](service-reports-visual-interactions.md).

## <a name="next-steps"></a>Nästa steg
[Testa – det är kostnadsfritt!](https://powerbi.com/)

Har du förslag på hur vi kan förbättra Power BI? [Skicka in en idé](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

[Lägga till en visualisering till en rapport](power-bi-report-add-visualizations-i.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

