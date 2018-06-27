---
title: Hur du lägger till en hyperlänk till en tabell
description: Hyperlänkar i tabeller
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/22/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d696a7492f1295f2e2c9b39088b0eacdb66b15ca
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34310186"
---
# <a name="hyperlinks-in-tables"></a>Hyperlänkar i tabeller
I det här ämnet lär du dig hur du använder Power BI Desktop för att skapa hyperlänkar. När hyperlänkarna har skapats använder du Desktop eller Power BI-tjänsten för att lägga till dem till dina rapporttabeller och -matriser. 

![](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> **OBS**: Hyperlänkarna i [paneler på instrumentpaneler](service-dashboard-edit-tile.md) och [textrutor på instrumentpaneler](service-dashboard-add-widget.md) kan skapas i farten med Power BI-tjänsten. Hyperlänkar i [textrutor i rapporter](service-add-hyperlink-to-text-box.md) kan skapa i farten med Power BI-tjänsten och Power BI Desktop.
> 
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Skapa en hyperlänk i en tabell eller matris med Power BI Desktop
Hyperlänkar i tabeller och matriser kan skapas i Power BI Desktop, men inte från Power BI-tjänsten. Hyperlänkar kan även skapas i Excel Power Pivot innan arbetsboken importeras till Power BI. Båda metoderna beskrivs nedan.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Skapa en tabell- eller en matrishyperlänk i Power BI Desktop
Proceduren för att lägga till en hyperlänk beror på om du har importerat dina data eller anslutit dem med hjälp av DirectQuery. Båda scenarierna beskrivs nedan.

### <a name="for-data-imported-into-power-bi"></a>För data som importerats till Power BI
1. Om hyperlänken inte redan finns som ett fält i datauppsättningen, använder du Desktop för att lägga till den som en [anpassad kolumn](desktop-common-query-tasks.md).
2. I datavyn väljer du kolumnen och på fliken **Modellering** väljer du listrutan för **Datakategori**.
   
    ![](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Välj **Webbadress**.
4. Växla till rapportvyn och skapa en tabell eller matris med hjälp av fältet som kategoriserats som en webbadress. Hyperlänkarna är blå och understrukna.
   
    ![](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)
5. Om du inte vill visa en lång URL i en tabell, kan du visa en hyperlänkikon ![](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) i stället. Observera att du inte kan visa ikoner i matriser.
   
   * Välj diagrammet för att aktivera det.
   * Välj färgrollerikonen ![](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) för att öppna formateringsfönstret.
   * Expandera **Värden**, leta upp **URL-ikonen** och **aktivera** den.
6. (Valfritt) [Publicera rapporten från Desktop till Power BI-tjänsten](guided-learning/publishingandsharing.yml?tutorial-step=2) och öppna rapporten i Power BI-tjänsten. Hyperlänkarna fungerar där också.

### <a name="for-data-connected-with-directquery"></a>För data anslutna med DirectQuery
Du kan inte skapa en ny kolumn i DirectQuery-läge.  Men om dina data redan innehåller URL:er, kan du förvandla dem till hyperlänkar.

1. Skapa en tabell med ett fält som innehåller URL:er i rapportvyn.
2. Markera kolumnen och välj listrutan för **Datakategori** på fliken **Modellering**.
3. Välj **Webbadress**. Hyperlänkarna är blå och understrukna.
4. (Valfritt) [Publicera rapporten från Desktop till Power BI-tjänsten](guided-learning/publishingandsharing.yml?tutorial-step=2) och öppna rapporten i Power BI-tjänsten. Hyperlänkarna fungerar där också.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Skapa en tabell- eller en matrishyperlänk i Excel Power Pivot
Ett annat sätt för att lägga till hyperlänkar till dina Power BI-tabeller och -matriser är att skapa hyperlänkarna i datauppsättningen innan du importerar/ansluter till datauppsättningen från Power BI. I det här exemplet används en Excel-arbetsbok.

1. Öppna arbetsboken i Excel.
2. Välj fliken **PowerPivot** och sedan **Hantera**.
   
   ![](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
3. När PowerPivot öppnas väljer du fliken **Avancerat**.
   
   ![](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Placera markören i den kolumn som innehåller de URL:er som du vill förvandla till hyperlänkar i Power BI-tabeller.
   
   > **OBS**: URL-adresserna måste börja med **http://, https://** eller **www**.
   > 
   > 
5. I gruppen **Rapporteringsegenskaper** väljer du listrutan **Datakategori** och sedan **Webbadress**. 
   
   ![](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)
6. Anslut till eller importera den här arbetsboken från Power BI-tjänsten eller Power BI Desktop.
7. Skapa en tabellvisualisering som innehåller URL-fältet.
   
   ![](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
F: Kan jag använda en anpassad URL som en hyperlänk i en tabell eller matris?    
S: Nej. Du kan använda en länkikon. Om du behöver anpassad text för hyperlänkarna och listan över URL:er är kort kan du använda en textruta i stället.


## <a name="next-steps"></a>Nästa steg
[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

