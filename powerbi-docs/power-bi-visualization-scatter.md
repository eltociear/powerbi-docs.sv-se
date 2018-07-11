---
title: Punktdiagram i Power BI
description: Punktdiagram i Power BI
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/28/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8931bc773f0543cc8687c1a8f9f63681109247e2
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600214"
---
# <a name="scatter-charts-and-bubble-charts-in-power-bi"></a>Punktdiagram och bubbeldiagram i Power BI
Ett punktdiagram har alltid två värdeaxlar som visar en uppsättning numeriska data längs en vågrät axel och en annan uppsättning numeriska värden längs en lodrät axel. Diagrammet visar punkter i skärningspunkten för ett numeriskt X- och Y-värde och kombinerar dessa värden till separata datapunkter. Dessa datapunkter kan vara jämnt eller ojämnt fördelade på den horisontala axeln, beroende på datan.

Ett bubbeldiagram ersätter datapunkterna med bubblor, med en *bubbelstorlek* som motsvarar en dimension av datan.

![](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Du kan ange antalet datapunkter  

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

## <a name="create-a-scatter-chart"></a>Skapa ett punktdiagram
Titta på det här videoklippet och se Skapa ett punktdiagram och följ stegen nedan för att skapa en egen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Dessa anvisningar använder sig av Exempel på detaljhandelsanalys. Om du vill följa med kan du [hämta exemplet](sample-datasets.md) för Power BI-tjänsten (app.powerbi.com) eller Power BI Desktop.   

1. Välj den gula plusikonen för att skapa en [tom rapportsida ](power-bi-report-add-page.md).
 
2. Välj följande fält från fönstret Fält:
   - **Försäljning** > **Försäljning efter kvm**
   - **Försäljning** > **Total försäljningsvarians %**
   - **Distrikt** > **Distrikt**

     ![](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

     Om du inte använder Power BI-tjänsten, se till att du öppnar rapporten i [Redigeringsvyn](service-interact-with-a-report-in-editing-view.md).

3. Konvertera till ett punktdiagram. På panelen Visualiseringar väljer du ytdiagramsikonen.

   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_icon.png).

4. Dra **Distrikt** från **Information** till **Förklaring**. Nu visas ett punktdiagram som visar **Total försäljningsvarians %** längs Y-axeln och **Försäljning per kvadratmeter** längs X-axeln. Datapunkternas färger representerar distrikt:

    ![](media/power-bi-visualization-scatter/power-bi-scatter.png)

Nu ska vi lägga till en tredje dimension.

## <a name="create-a-bubble-chart"></a>Skapa ett bubbeldiagram

1. Från fönstret **Fält** drar du **Försäljning** > **Försäljning detta år** > **Värdet** till området **Storlek**. Datapunkterna expanderar till storlekar som motsvarar försäljningsvärdet.
   
   ![](media/power-bi-visualization-scatter/power-bi-bubble.png)

2. Håll muspekaren över en bubbla. Storleken på bubblan reflekterar **försäljning detta år**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

3. Om du vill ange antalet datapunkter som ska visas i bubbeldiagrammet går du till **Format**-avsnittet i fönstret **Visualiseringar**, expanderar kortet **Allmänt** och justerar **Datavolym**. Du kan ange en största datavolym på upp till 10 000. För högre volymer föreslår vi att du först testar så att prestanda inte försämras. 

    ![Datavolym](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png) 

   > [!NOTE]
   > Eftersom fler datapunkter kan innebära en längre inläsningstid, bör du testa dina rapporter på webben och mobilt för att säkerställa att prestandan matchar dina användares förväntningar om du väljer att publicera rapporter med gränser i den högre änden av skalan. Tänk på att du bör testa resultaten för olika formfaktorer för att säkerställa bra prestanda för datapunkter med höga nummer.

4. Du kan [formatera visualiseringens färger, etiketter, rubriker, bakgrund med mera](service-getting-started-with-color-formatting-and-axis-properties.md). Överväg att lägga till markörformer på varje linje för att [förbättra tillgängligheten](desktop-accessibility.md). Med olika markörformer för varje linje är det enklare för rapportanvändare att skilja linjer (eller områden) från varandra. Välj markörform genom att expandera kortet **Former** och välja en markörform.

      ![Markörform](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

   Du kan också ändra markörformen till en romb, triangel eller kvadrat:

   ![Kvadratisk markör](media/power-bi-visualization-scatter/pbi_scatter_chart_hover_square.png)


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

[Registrera dig för en kostnadsfri utvärderingsversion](https://powerbi.microsoft.com/get-started/)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

