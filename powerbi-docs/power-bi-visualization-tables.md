---
title: Tabellvisualiseringar i Power BI-rapporter och instrumentpaneler (självstudier)
description: Självstudier för att arbeta med tabellvisualiseringar i Power BI-rapporter och instrumentpaneler, inklusive hur du ändrar kolumnbredder.
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
featuredvideoid: ''
qualityfocus: ''
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/11/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: a36e2afcda7c741c871b07c526ab010f77290a3b
ms.sourcegitcommit: df94efc51f261113fa90ebdf3fe68dd149cc4936
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/18/2018
---
# <a name="working-with-tables-in-power-bi-reports-and-dashboards-tutorial"></a>Arbeta med tabeller i Power BI-rapporter och instrumentpaneler (självstudier)
En tabell är ett rutnät som innehåller relaterade data i en logisk serie med rader och kolumner. Det kan också innehålla rubriker och en rad för summor. Tabeller fungerar bra med kvantitativa jämförelser där du tittar på många värden för en enskild kategori. I den här tabellen visas till exempel 5 olika mått för **Kategori**.

![](media/power-bi-visualization-tables/table.png)

## <a name="when-to-use-a-table"></a>När du ska en tabell
Tabeller är ett bra alternativ:

* för att visa och jämföra detaljerade data och exakta värden (istället för visuella representationer)
* för att visa data i tabellformat
* att visa numeriska data efter kategorier   

> [!NOTE]
> Om en tabell har för många värden, bör du omvandla den till en matris och/eller ändra detaljnivån.
> 
> 
## <a name="prerequisites"></a>Förutsättningar
 - Power BI-tjänsten eller Power BI Desktop
 - Exempel på detaljhandelsanalys


## <a name="create-a-table"></a>Skapa en tabell
Vi ska skapa tabellen som visas ovan för att visa försäljningsvärden efter kategori för objektet. Om du vill följa med, loggar du in i Power BI-tjänsten och väljer **Hämta data\> Exempel \> Exempel på detaljhandelsanalys > Anslut** och välj **Gå till instrumentpanel. För att skapa en visualisering krävs behörighet att redigera datauppsättningen och rapporten. Som tur är kan alla Power BI-exemplen redigeras. Om en rapport har delats med dig, kan du inte skapa visualiseringar i rapporten.

1. I det vänstra navigeringsfönstret väljer du **Arbetsytor > Min arbetsyta**.    
2. Välj fliken Datauppsättningar och rulla till Exempel på detaljhandelsanalys som du precis la till.  Välj ikonen **Skapa rapport**.
   
    ![](media/power-bi-visualization-tables/power-bi-create-report.png)
2. I rapportredigeraren väljer du **Objekt** > **Kategori**.  Power BI skapar automatiskt en tabell som listar alla kategorier.
   
    ![](media/power-bi-visualization-tables/power-bi-table1.png)
3. Välj **Försäljning > Genomsnittligt enhetspris** och **Försäljning > Senaste årets försäljning** och **Försäljning > Försäljning detta år** och välja alla 3 alternativ (värde, mål, status).   
4. Identifiera **Värden** i fönstret visualiseringar och dra och släpp värdena tills ordningen på diagramkolumnerna matchar den första bilden på den här sidan.  Dina värden bör se ut så här.
   
    ![](media/power-bi-visualization-tables/power-bi-table2.png)
5. Fäst tabellen på instrumentpanelen genom att välja häftstift-ikonen  
   
     ![](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formatera tabellen
Det finns många sätt att formatera en tabell och vi presenterar endast några av dem här. Ett bra sätt att lära dig om de andra formateringsalternativen är att öppna fönstret formatering (roller-ikonen ![](media/power-bi-visualization-tables/power-bi-format.png)) och utforska.

* Försök att formatera tabellrutnätet. Här vi har lagt till ett blått lodrätt rutnät, lagt till utrymme i raderna, ökat kantlinjen och ändra textstorleken något.
  
    ![](media/power-bi-visualization-tables/power-bi-table-gridnew.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* För kolumnrubrikerna har vi ändrat bakgrundsfärgen, lagt till en kantlinje och ökat teckenstorleken. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

  
    ![](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Du kan även formatera enskilda kolumner och kolumnrubriker. Starta genom att utvidga **Fältformatering** och markera den kolumn som ska formateras från listrutan. Med Fältformatering kan du, beroende på kolumnvärdena, t.ex. ange visningsenheter, teckensnittsfärg, antal decimaler, bakgrund, justering och mycket mer. När du har justerat inställningarna kan du ange om dessa inställningar även ska tillämpas på rubrik och summarad.

    ![](media/power-bi-visualization-tables/power-bi-field-formatting.png)

* Här är vår slutliga tabell efter ytterligare lite formatering. Eftersom det finns så många formateringsalternativ är det bästa sättet att lära dig är att börja med standardformateringen, öppna formateringsfönstret ![](media/power-bi-visualization-tables/power-bi-format.png) och börja utforska. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Villkorsstyrd formatering
En typ av formatering kallas *villkorsstyrd formatering* och denna tillämpas på fälten i **Värden** i fönstret **Visualiseringar** i Power BI-tjänsten eller Desktop. 

Med villkorsstyrd formatering för tabeller kan du specificera anpassade cellbakgrundsfärger och teckenfärg baserat på cellvärden, inklusive toningar. 

1. I fönstret **Visuella objekt** i Power BI Desktop väljer du nedpilen bredvid värdet i brunnen **Värden** som du vill formatera (eller högerklicka på fältet). Du kan endast hantera villkorsstyrd formatering för fälten i området **Värden** i brunnen **Fält**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Välj **Skalor för bakgrundsfärg**. I dialogrutan som visas kan du konfigurera färgen, samt *minimi-* och *max*värden. Om du väljer rutan **Avvikande** kan du konfigurera ett valfritt *Centrumvärde*.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)
   
    Vi kan lägga till anpassad formatering våra värden för Genomsnittligt enhetspris. Välj **Divergerande**, lägg till färger och välj **OK**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Lägg till ett nytt fält i tabellen som innehåller både positiva och negativa värden.  Välj **Försäljning > Total försäljningsvarians**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Lägg till datastapeln villkorsstyrd formatering genom att välja nedåtpilen bredvid **Total försäljningsvarians** och välja **Villkorsstyrd formatering > Datastaplar**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. I dialogrutan som visas, ange färger för **Positiv stapel**, **Negativ stapel**, markera bredvid **Visa endast liggande** och gör eventuella andra ändringar.
   
    ![](media/power-bi-visualization-tables/power-bi-data-bars.png)
   
    När du väljer **OK** ersätter datastaplar de numeriska värdena i tabellen, vilket gör den lättare att söka igenom.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Om du vill ta bort villkorlig formatering från en visualisering, bara högerklickar du på fältet igen och väljer **ta bort villkorsstyrd formatering**.

> [!TIP]
> Villkorsstyrd formatering är också tillgängligt från fönstret formatering (rollerikonen). Välj värdet att formatera och växla sedan **färgskalor** eller **datastaplar** till På för att använda standardinställningarna eller, om du vill anpassa inställningarna, välj **Avancerade kontroller**.
> 
> 

## <a name="adjust-the-column-width-of-a-table"></a>Justera kolumnbredden i en tabell
Power BI trunkerar ibland en kolumnrubrik i en rapport eller på en instrumentpanel. Om du vill visa hela kolumnnamnet håller du muspekaren över utrymmet till höger om rubriken för att visa dubbelpilarna, markera och dra.

![](media/power-bi-visualization-tables/resizetable.gif)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

