---
title: Tabellvisualiseringar i Power BI-rapporter och instrumentpaneler
description: Självstudier för att arbeta med tabellvisualiseringar i Power BI-rapporter och instrumentpaneler, inklusive hur du ändrar kolumnbredder.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c94fd3ce58cefdb9e3cc7749b6486ab9bb0577cb
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50101472"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tabeller i Power BI-rapporter och instrumentpaneler
En tabell är ett rutnät som innehåller relaterade data i en logisk serie med rader och kolumner. Det kan också innehålla rubriker och en rad för summor. Tabeller fungerar bra med kvantitativa jämförelser där du tittar på många värden för en enskild kategori. I den här tabellen visas till exempel 5 olika mått för **Kategori**.

![](media/power-bi-visualization-tables/table.png)

Skapa tabeller i rapporter och markera flera element i tabellen med andra visuella objekt på samma rapportsida.  Dessutom kan du välja rader, kolumner och även enskilda celler och korsmarkeringar. Du kan kopiera enskilda celler och markeringar av flera celler och klistra in dem i andra program.

## <a name="when-to-use-a-table"></a>När du ska en tabell
Tabeller är ett bra alternativ:

* för att visa och jämföra detaljerade data och exakta värden (istället för visuella representationer)
* för att visa data i tabellformat
* att visa numeriska data efter kategorier   

> [!NOTE]
> Om en tabell har för många värden, bör du omvandla den till en matris och/eller ändra detaljnivån. Det högsta antalet datapunkter som går att visa i en tabell är 3 500.

## <a name="prerequisites"></a>Förutsättningar
- Power BI-tjänsten eller Power BI Desktop
- Exempel på detaljhandelsanalys

## <a name="create-a-table"></a>Skapa en tabell
Vi ska skapa tabellen som visas ovan för att visa försäljningsvärden efter kategori för objektet. Om du vill följa med, loggar du in i Power BI-tjänsten och väljer **Hämta data\> Exempel \> Exempel på detaljhandelsanalys > Anslut** och välj **Gå till instrumentpanel**. För att skapa en visualisering krävs behörighet att redigera datauppsättningen och rapporten. Som tur är kan alla Power BI-exemplen redigeras. Om en rapport har delats med dig, kan du inte skapa visualiseringar i rapporten.

1. I det vänstra navigeringsfönstret väljer du **Arbetsytor > Min arbetsyta**.    
2. Välj fliken Datauppsättningar och rulla till Exempel på detaljhandelsanalys som du precis la till.  Välj ikonen **Skapa rapport**.

    ![pekar på rapportikon](media/power-bi-visualization-tables/power-bi-create-report.png)
2. I rapportredigeraren väljer du **Objekt** > **Kategori**.  Power BI skapar automatiskt en tabell som listar alla kategorier.

    ![resultatet av att lägga till kategori](media/power-bi-visualization-tables/power-bi-table1.png)
3. Välj **Försäljning > Genomsnittligt enhetspris** och **Försäljning > Senaste årets försäljning** och **Försäljning > Försäljning detta år** och välja alla 3 alternativ (värde, mål, status).   
4. Identifiera **Värden** i fönstret visualiseringar och dra och släpp värdena tills ordningen på diagramkolumnerna matchar den första bilden på den här sidan.  Dina värden bör se ut så här.

    ![Värden](media/power-bi-visualization-tables/power-bi-table2.png)
5. Fäst tabellen på instrumentpanelen genom att välja häftstift-ikonen  

     ![häftstift](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formatera tabellen
Du kan formatera en tabell på många sätt och vi beskriver endast några här. Ett bra sätt att lära dig om de andra formateringsalternativen är att öppna fönstret formatering (färgrollerikonen ![färgroller](media/power-bi-visualization-tables/power-bi-format.png)) och utforska.

* Försök att formatera tabellrutnätet. Här vi har lagt till ett blått lodrätt rutnät, lagt till utrymme i raderna, ökat kantlinjen och ändra textstorleken något.

    ![Rutnätskort](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![tabell som visar resultat](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* För kolumnrubrikerna har vi ändrat bakgrundsfärgen, lagt till en kantlinje och ökat teckenstorleken. 

    ![Kolumnrubrikskort](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![rubrikformatering in tabell](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Du kan även formatera enskilda kolumner och kolumnrubriker. Starta genom att utvidga **Fältformatering** och markera den kolumn som ska formateras från listrutan. Med Fältformatering kan du, beroende på kolumnvärdena, t.ex. ange visningsenheter, teckensnittsfärg, antal decimaler, bakgrund, justering och mycket mer. När du har justerat inställningarna kan du ange om dessa inställningar även ska tillämpas på rubrik och summarad.

    ![Fältformatering för årets försäljning](media/power-bi-visualization-tables/power-bi-field-formatting.png)

* Här är vår slutliga tabell efter ytterligare lite formatering. Eftersom det finns så många formateringsalternativ är det bästa sättet att lära dig är att börja med standardformateringen, öppna formateringsfönstret ![](media/power-bi-visualization-tables/power-bi-format.png) och börja utforska. 

    ![tabell med all formatering hittills](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Villkorsstyrd formatering
En typ av formatering kallas *villkorsstyrd formatering* och denna tillämpas på fälten i **Värden** i fönstret **Visualiseringar** i Power BI-tjänsten eller Desktop. 

Med villkorsstyrd formatering för tabeller kan du specificera anpassade cellbakgrundsfärger och teckenfärg baserat på cellvärden, inklusive toningar. 

1. I fönstret **Visuella objekt** i Power BI Desktop väljer du nedpilen bredvid värdet i brunnen **Värden** som du vill formatera (eller högerklicka på fältet). Du kan endast hantera villkorsstyrd formatering för fälten i området **Värden** i brunnen **Fält**.

    ![sökväg till Skalor för bakgrundsfärg](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Välj **Skalor för bakgrundsfärg**. I dialogrutan som visas kan du konfigurera färgen, samt *minimi-* och *max*värden. Om du väljer rutan **Avvikande** kan du konfigurera ett valfritt *Centrumvärde*.

    ![Skärmen Skalor för bakgrundsfärg](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Vi kan lägga till anpassad formatering våra värden för Genomsnittligt enhetspris. Välj **Divergerande**, lägg till färger och välj **OK**. 

    ![tabell som visar avvikande färger](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Lägg till ett nytt fält i tabellen som innehåller både positiva och negativa värden.  Välj **Försäljning > Total försäljningsvarians**. 

    ![visar ett nytt fält till höger](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Lägg till datastapeln villkorsstyrd formatering genom att välja nedåtpilen bredvid **Total försäljningsvarians** och välja **Villkorsstyrd formatering > Datastaplar**.

    ![sökväg till Datastaplar](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. I dialogrutan som visas, ange färger för **Positiv stapel**, **Negativ stapel**, markera bredvid **Visa endast liggande** och gör eventuella andra ändringar.

    ![markeringen för Visa endast liggande](media/power-bi-visualization-tables/power-bi-data-bars.png)

    När du väljer **OK** ersätter datastaplar de numeriska värdena i tabellen, vilket gör den lättare att söka igenom.

    ![samma tabell men med staplar i sista kolumnen](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Om du vill ta bort villkorlig formatering från en visualisering, bara högerklickar du på fältet igen och väljer **ta bort villkorsstyrd formatering**.

> [!TIP]
> Villkorsstyrd formatering är också tillgängligt från fönstret formatering (rollerikonen). Välj värdet att formatera och växla sedan **färgskalor** eller **datastaplar** till **På** för att använda standardinställningarna eller, om du vill anpassa inställningarna, välj **Avancerade kontroller**.
> 
## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Kopiera värden från Power BI-tabeller så att du kan använda dem i andra program

Din tabell eller matris kan ha innehåll som du vill använda i andra program som Dynamics CRM eller Excel eller t.o.m. i andra Power BI-rapporter. Genom att högerklicka i Power BI kan du kopiera en cell eller ett cellurval till Urklipp och klistra in informationen i det andra programmet.


* Om du vill kopiera en enskild cells värde markerar du cellen, högerklickar och väljer **Kopiera värde**. Med det oformaterade cellvärdet i Urklipp kan du nu klistra in det i ett annat program.

    ![kopieringsalternativ](media/power-bi-visualization-tables/power-bi-copy-value.png)

* Om du vill kopiera mer än en enskild cell markerar du ett cellområde eller markerar en eller flera celler med hjälp av CTRL. Kopian inkluderar kolumn- och radrubrikerna.

    ![kopieringsalternativ](media/power-bi-visualization-tables/power-bi-copy-selection.png)

    Kopian inkluderar kolumn- och radrubrikerna.

    ![klistra in i Excel](media/power-bi-visualization-tables/power-bi-paste-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Justera kolumnbredden i en tabell
Power BI trunkerar ibland en kolumnrubrik i en rapport eller på en instrumentpanel. Om du vill visa hela kolumnnamnet håller du muspekaren över utrymmet till höger om rubriken för att visa dubbelpilarna, markera och dra.

![närbild på storleksändring av kolumn](media/power-bi-visualization-tables/resizetable.gif)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* Om du lägger till kolumnformatering kan du bara välja ett justeringsalternativ per kolumn: automatisk justering, vänsterjustering, centrering eller högerjustering. Oftast innehåller en kolumn antingen text eller tal, inte en blandning av både text och tal. Om en kolumn innehåller både tal och text vänsterjusteras texten och talen högerjusteras om du väljer **automatisk justering**. Det här beteendet används med ”vänster till höger”-språk.   

## <a name="next-steps"></a>Nästa steg

[Trädkartor i Power BI](power-bi-visualization-treemaps.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)