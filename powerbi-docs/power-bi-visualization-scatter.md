---
title: "Punktdiagram i Power BI (Självstudier)"
description: "Självstudier: Punktdiagram i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: PVcfPoVE3Ys
qualityfocus: identified
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: c1801db4135d6d97a940e593de37ca2886194b53
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="scatter-charts-and-bubble-charts-in-power-bi-tutorial"></a>Punktdiagram och bubbeldiagram i Power BI (självstudier)
Ett punktdiagram har alltid två värdeaxlar som visar en uppsättning numeriska data längs en vågrät axel och en annan uppsättning numeriska värden längs en lodrät axel. Diagrammet visar punkter i skärningspunkten för ett numeriskt X- och Y-värde och kombinerar dessa värden till separata datapunkter. Dessa datapunkter kan vara jämnt eller ojämnt fördelade på den horisontala axeln, beroende på datan.

Ett bubbeldiagram ersätter datapunkterna med bubblor, med en *bubbelstorlek* som motsvarar en dimension av datan.

![](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>När du vill använda ett punktdiagram eller bubbeldiagram
### <a name="scatter-charts-are-a-great-choice"></a>Punktdiagram är ett bra alternativ:
* för att visa relationer mellan 2 (punktdiagram) eller 3 (bubbeldiagram) **numeriska** värden.
* Så här skapar du ett punktdiagram av två grupper med värden som en serie xy-koordinater.
* i stället för ett linjediagram när du vill ändra skalan på den horisontala axeln    
* för att aktivera den vågräta axeln i en logaritmisk skala.
* för att visa arbetsbladets data som inkluderar par eller grupperade uppsättningar med värden. Du kan justera oberoende skalor av axlar för att visa mer information om grupperade värden i punktdiagrammet.
* för att visa mönster i stora mängder data, till exempel genom att visa linjära eller icke-linjära trender, kluster och avvikare.
* jämföra ett stort antal datapunkter utan hänsyn till tid. Ju mer data som inkluderas i en punktdiagram, desto bättre jämförelser.

### <a name="bubble-charts-are-a-great-choice"></a>Bubbeldiagram är ett bra alternativ:
* m dina data har 3 dataserier som alla innehåller en uppsättning med värden.
* för att presentera finansiella data.  Olika bubbelstorlekar är användbara för att visuellt betona specifika värden.
* att använda med kvadranter.

## <a name="create-a-scatter-chart"></a>Skapa ett punktdiagram
<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Öppna Exemplet detaljhandelsanalys i [redigeringsvyn](service-interact-with-a-report-in-editing-view.md) och [lägg till en ny rapportsida](power-bi-report-add-page.md).
2. Gå till fönstret fält, välj **Försäljning** > **Försäljning per kvadratmeter** och **Försäljning** > **Totalförsäljningsvarians i %**.
3. I fältpanelen, väljer du **Distrikt > Distrikt**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_pre_convert.png)
4. Konvertera till ett punktdiagram. På panelen Visualiseringar väljer du ytdiagramsikonen.
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_icon.png).
5. Dra **Distrikt** från **Information** till **Förklaring**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_new.png)

Nu har vi ett punktdiagram som visar totalförsäljningsvarians i % längs Y-axeln och visar försäljning per kvadratmeter längs X-axeln.  Datapunkternas färger representerar distrikt.  Nu ska vi lägga till en tredje dimension.

## <a name="create-a-bubble-chart"></a>Skapa ett bubbeldiagram
1. Dra **Försäljning** > **Försäljning detta år** > **Värdet** till området **Storlek** i fönstret Fält. 
   
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_size.png)
2. Håll muspekaren över en bubbla.  Storleken på bubblan reflekterar **försäljning detta år**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)
3. Du kan också [formatera visualiseringsfärger, etiketter, rubriker, bakgrund med mera](service-getting-started-with-color-formatting-and-axis-properties.md).

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
### <a name="your-scatter-chart-has-only-one-data-point"></a>**Ditt punktdiagram har endast en datapunkt**
Har du skapat ett punktdiagram där du bara ser en datapunkt som samlar alla värdena på X- och Y-axlarna?  Eller samlar diagrammet alla värden längs en enda vågrät eller lodrät linje?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Lös problemet genom att lägga till ett fält i området **Information** som talar om för Power BI hur värdena ska grupperas. Fältet måste vara unikt för varje punkt som du vill rita.  
Som ett enkel radnummer eller ID-fält:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Eller om du inte har detta i dina data, skapa ett fält som tillsammans sammanfogar X- och Y-värden till något unikt för varje plats:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Skapa ett nytt fält genom att [använda Power BI Desktop frågeredigeraren för att lägga till en indexkolumn](desktop-add-custom-column.md) i din datauppsättning.  Lägg sedan till den här kolumnen till området **Information** i din visualisering.

## <a name="next-steps"></a>Nästa steg
 [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Testa – det är kostnadsfritt!](https://powerbi.com/)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

