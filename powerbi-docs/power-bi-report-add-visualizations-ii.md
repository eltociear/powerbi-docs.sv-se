---
title: "Del 2, Lägga till visualiseringar i en Power BI-rapport (självstudier)"
description: "Självstudier: Del 2, Lägga till visualiseringar i en Power BI-rapport"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/23/2018
ms.author: mihart
ms.openlocfilehash: 40d6ee1f1448856b444201532caffd4b8c904c85
ms.sourcegitcommit: c3be4de522874fd73fe6854333b379b85619b907
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/24/2018
---
# <a name="part-2-add-visualizations-to-a-power-bi-report-tutorial"></a>Del 2, Lägga till visualiseringar i en Power BI-rapport (självstudier)
I [del 1](power-bi-report-add-visualizations-ii.md) skapade du en grundläggande visualisering genom att markera kryssrutorna bredvid fältnamnen.  I del 2 får du lära dig hur du använder dra och släpp och drar nytta av panelerna **Fält** och **Visualiseringar** för att skapa och modifiera visualiseringar.

### <a name="prerequisites"></a>Förutsättningar
- [Del 1](power-bi-report-add-visualizations-ii.md)
- Power BI-tjänsten – visualiseringar kan läggas till i rapporter med Power BI-tjänsten eller Power BI Desktop. Den här självstudien använder Power BI-tjänsten. 
- Exempel på detaljhandelsanalys

## <a name="create-a-new-visualization"></a>Skapa en ny visualisering
I de här självstudierna tar vi hjälp av vår Retail Analysis-datauppsättning för att skapa några viktiga visualiseringar.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Öppna en rapport och lägg till en ny tom sida.
1. Öppna arbetsytan där du sparade Exempel på detaljhandelsanalys. Välj **Exempel på detaljhandelsanalys** för att öppna rapporten i läsvyn.
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-report.png)
2. Välj **Redigera rapport** för att öppna rapporten i redigeringsvyn.
   
   ![](media/power-bi-report-add-visualizations-ii/editreport1.png)
3. [Lägg till en ny sida](power-bi-report-add-page.md) genom att välj den gula plus-ikonen längst ned på arbetsytan.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_addreportpage.png)

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Lägg till en visualisering som tittar på det här årets försäljning jämfört med föregående års.
1. I tabellen **Försäljning** väljer du **This Year Sales (Årets försäljning)** > **Värde** och **Last Year Sales (Förra årets försäljning)**. Power BI skapar ett kolumndiagram.  Detta är något som är intressant och vi vill veta mer om. Hur ser den månadsvisa försäljningen ut?  
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_4bnew.png)
2. Dra **Månad** från tabellen Tid till **Axel**-området.  
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_5newnew.png)
3. [Ändra visualiseringen](power-bi-report-change-visualization-type.md) till ett ytdiagram.  Det finns många visualiseringstyper att välja bland – titta närmare på [beskrivningarna för var och en, tipsen om bästa praxis och självstudierna](power-bi-visualization-types-for-reports-and-q-and-a.md) för hjälp med att bestämma vilken typ som ska användas. På panelen Visualiseringar väljer du ytdiagramsikonen.
4. Sortera visualiseringen genom att välja ellipserna och därefter **Sortera efter månad**.
5. [Ändra storlek på visualiseringen](power-bi-visualization-move-and-resize.md) genom att välja visualiseringen, ta tag i en av konturens cirklar och dra. Gör den tillräckligt bred för att eliminera rullningslisten och tillräckligt liten för att ge oss tillräckligt med utrymme för att lägga till ytterligare en visualisering.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Spara rapporten](service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Lägga till en kartvisualisering som visar försäljningen efter plats
1. I tabellen **Butik** väljer du **Territorium**. Power BI identifierar att Territorium är en plats och skapar en kartvisualisering.  
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_8newnew.png)
2. Dra **Totalt antal butiker** till området Storlek.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-add-visual-to-a-reportnew.png)
3. Lägg till en förklaring.  Om du vill visa dina data efter butiksnamn, drar du **Kedja** i till förklaringsområdet.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-add-visual-to-a-report-3new.png)

## <a name="next-steps"></a>Nästa steg
* Mer information om fältpanelen finns i [Rapportredigeraren... ta en rundtur](service-the-report-editor-take-a-tour.md).   
* Information om hur du filtrerar och markerar dina visualiseringar finns i [Filter och markeringar i Power BI-rapporter](power-bi-reports-filters-and-highlighting.md).  
* Du hittar mer i [Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md).  
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

