---
title: Punktdiagram, bubbeldiagram och punktritningsdiagram i Power BI
description: Punktdiagram, punktritningsdiagram och bubbeldiagram i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 26dd55f1084d62f9506b02c5852f0396adba305a
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290324"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Punktdiagram, bubbeldiagram och punktritningsdiagram i Power BI
Ett punktdiagram har alltid två värdeaxlar som visar en uppsättning numeriska data längs en vågrät axel och en annan uppsättning numeriska värden längs en lodrät axel. Diagrammet visar punkter i skärningspunkten för ett numeriskt X- och Y-värde och kombinerar dessa värden till separata datapunkter. Dessa datapunkter kan vara jämnt eller ojämnt fördelade på den horisontala axeln, beroende på datan.

Ett bubbeldiagram ersätter datapunkterna med bubblor, med en *bubbelstorlek* som motsvarar ytterligare en dimension av informationen.

![exempel på bubbeldiagram](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Punktritningsdiagram liknar bubbeldiagram och punktdiagram, med den skillnaden att du kan rita numeriska data eller kategoridata utmed X-axeln. 

![exempel på bubbeldiagram](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Du kan ange antalet datapunkter upp till 10 000.  

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>När du vill använda ett punktdiagram eller bubbeldiagram
### <a name="scatter-charts-are-a-great-choice"></a>Punktdiagram är ett bra alternativ:
* för att visa relationer mellan 2 (punktdiagram) eller 3 (bubbeldiagram) **numeriska** värden.
* för att rita två grupper med värden som en serie xy-koordinater.
* i stället för ett linjediagram när du vill ändra skalan på den horisontala axeln    
* för att aktivera den vågräta axeln i en logaritmisk skala.
* för att visa arbetsbladets data som inkluderar par eller grupperade uppsättningar med värden. Du kan justera oberoende skalor av axlar för att visa mer information om grupperade värden i punktdiagrammet.
* för att visa mönster i stora mängder data, till exempel genom att visa linjära eller icke-linjära trender, kluster och avvikare.
* för att jämföra ett stort antal datapunkter utan hänsyn till tid.  Ju mer data som inkluderas i ett punktdiagram, desto bättre jämförelser kan du göra.

### <a name="bubble-charts-are-a-great-choice"></a>Bubbeldiagram är ett bra alternativ:
* m dina data har 3 dataserier som alla innehåller en uppsättning med värden.
* för att presentera finansiella data.  Olika bubbelstorlekar är användbara för att visuellt betona specifika värden.
* att använda med kvadranter.

### <a name="dot-plot-charts-are-a-great-choice-in-place-of-a-scatter-or-bubble"></a>Punktritningsdiagram är ett bra alternativ till punktdiagram eller bubbeldiagram:
* om du vill inkludera kategoridata utmed X-axeln

## <a name="create-a-scatter-chart"></a>Skapa ett punktdiagram
Titta på det här videoklippet och se Skapa ett punktdiagram och följ stegen nedan för att skapa en egen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Dessa anvisningar använder sig av Exempel på detaljhandelsanalys. Om du vill följa med kan du [hämta exemplet](../sample-datasets.md) för Power BI-tjänsten (app.powerbi.com) eller Power BI Desktop.   

1. Öppna rapporten i redigeringsvyn och välj den gula plusikonen för att skapa en tom rapportsida.
 
2. Välj följande fält från fönstret Fält:
   - **Försäljning** > **Försäljning efter kvm**
   - **Försäljning** > **Total försäljningsvarians %**
   - **Distrikt** > **Distrikt**

     ![](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

     Om du inte använder Power BI-tjänsten, se till att du öppnar rapporten i [Redigeringsvyn](../service-interact-with-a-report-in-editing-view.md).

3. Konvertera till ett punktdiagram. På panelen Visualiseringar väljer du ytdiagramsikonen.

   ![](media/power-bi-visualization-scatter/power-bi-scatter-new.png).

4. Dra **Distrikt** från **Information** till **Förklaring**. Nu visas ett punktdiagram som visar **Total försäljningsvarians %** längs Y-axeln och **Försäljning per kvadratmeter** längs X-axeln. Datapunkternas färger representerar distrikt:

    ![](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Nu ska vi lägga till en tredje dimension.

## <a name="create-a-bubble-chart"></a>Skapa ett bubbeldiagram

1. Från fönstret **Fält** drar du **Försäljning** > **Försäljning detta år** > **Värdet** till området **Storlek**. Datapunkterna expanderar till storlekar som motsvarar försäljningsvärdet.
   
   ![punkter blir bubblor](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

2. Håll muspekaren över en bubbla. Storleken på bubblan reflekterar **försäljning detta år**.
   
    ![visning av knappbeskrivningar](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

3. Om du vill ange antalet datapunkter som ska visas i bubbeldiagrammet går du till **formateringsavsnittet** i fönstret **Visualiseringar**, expanderar kortet **Allmänt** och justerar **Datavolym**. Du kan ange en största datavolym på upp till 10 000. För högre volymer föreslår vi att du först testar så att prestanda inte försämras. 

    ![Datavolym](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png) 

   Eftersom fler datapunkter kan innebära en längre inläsningstid, bör du testa dina rapporter på webben och mobilt för att säkerställa att prestandan matchar dina användares förväntningar om du väljer att publicera rapporter med gränser i den högre änden av skalan. 

4. Du kan [formatera visualiseringens färger, etiketter, rubriker, bakgrund med mera](service-getting-started-with-color-formatting-and-axis-properties.md). Överväg att lägga till markörformer på varje linje för att [förbättra tillgängligheten](../desktop-accessibility.md). Med olika markörformer för varje linje är det enklare för rapportanvändare att skilja linjer (eller områden) från varandra. Välj markörform genom att expandera kortet **Former** och välja en markörform.

      ![Markörform](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

   Du kan också ändra markörformen till en romb, triangel eller kvadrat:

   ![Kvadratisk markör](media/power-bi-visualization-scatter/pbi_scatter_chart_hover_square.png)

## <a name="create-a-dot-plot"></a>Skapa en punktritning
Om du vill skapa en punktritning ersätter du det numeriska X-axelfältet med ett kategorifält.

Ta bort **försäljning per kvm** från fönstret **X-axel** och ersätt med **Distrikt > DM**.
   
![ny punktritning](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)


## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

### <a name="your-scatter-chart-has-only-one-data-point"></a>**Ditt punktdiagram har endast en datapunkt**
Har du skapat ett punktdiagram där du bara ser en datapunkt som samlar alla värdena på X- och Y-axlarna?  Eller samlar diagrammet alla värden längs en enda vågrät eller lodrät linje?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Lös problemet genom att lägga till ett fält i området **Information** som talar om för Power BI hur värdena ska grupperas. Fältet måste vara unikt för varje punkt som du vill rita, till exempel ett enkelt radnummer eller ett ID-fält.

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Eller om du inte har detta i dina data, skapa ett fält som tillsammans sammanfogar X- och Y-värden till något unikt för varje plats:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Skapa ett nytt fält genom att [använda Power BI Desktop frågeredigeraren för att lägga till en indexkolumn](../desktop-add-custom-column.md) i din datauppsättning.  Lägg sedan till den här kolumnen till området **Information** i din visualisering.

## <a name="next-steps"></a>Nästa steg

[Punktdiagram med hög densitet](desktop-high-density-scatter-charts.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

