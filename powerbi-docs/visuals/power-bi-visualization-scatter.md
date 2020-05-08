---
title: Punktdiagram, bubbeldiagram och punktritningsdiagram i Power BI
description: Punktdiagram, punktritningsdiagram och bubbeldiagram i Power BI
author: mihart
ms.reviewer: amac
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/21/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e7160505a720b6629067d7b1486f0dd227efd862
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80273327"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Punktdiagram, bubbeldiagram och punktritningsdiagram i Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Ett punktdiagram har alltid två värdeaxlar som visar en uppsättning numeriska data längs en vågrät axel och en annan uppsättning numeriska värden längs en lodrät axel. Diagrammet visar punkter i skärningspunkten för ett numeriskt X- och Y-värde och kombinerar dessa värden till separata datapunkter. Power BI kan distribuera dessa datapunkter jämnt eller ojämnt på den vågräta axeln. Det beror på de data som diagrammet representerar.

Titta på det här videoklippet och se Skapa ett punktdiagram och följ stegen nedan för att skapa en egen.
   > [!NOTE]
   > Den här videon använder en äldre version av Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

Du kan ange antalet datapunkter upp till 10 000.  

## <a name="when-to-use-a-scatter-chart-bubble-chart-or-a-dot-plot-chart"></a>När ska du använda punktdiagram, bubbeldiagram och punktritningsdiagram?

### <a name="scatter-and-bubble-charts"></a>Punktdiagram och bubbeldiagram

Ett punktdiagram visar relationen mellan två numeriska värden. Ett bubbeldiagram ersätter datapunkterna med bubblor, där *bubbelstorleken* motsvarar en ytterligare, tredje datadimension.

![Skärmbild av ett exempel på ett bubbeldiagram.](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Punktdiagram är ett bra alternativ:

* för att visa relationer mellan två numeriska värden

* för att rita två grupper med siffror som en serie med X- och Y-koordinater

* för användning i stället för ett linjediagram när du vill ändra skalan på den vågräta axeln

* för att aktivera den vågräta axeln i en logaritmisk skala

* för att visa arbetsbladsdata som inkluderar par eller grupperade uppsättningar med värden

    > [!TIP]
    > Du kan justera oberoende skalor av axlar för att visa mer information om grupperade värden i punktdiagrammet.

* för att visa mönster i stora mängder data, till exempel genom att visa linjära eller icke-linjära trender, kluster och extremvärden

* för att jämföra ett stort antal datapunkter utan hänsyn till tid.  Ju mer data som inkluderas i ett punktdiagram, desto bättre jämförelser kan du göra.

Förutom vad punktdiagram kan hjälpa till med, är även bubbeldiagram ett bra alternativ:

* om dina data har tre dataserier som alla innehåller en uppsättning med värden

* för att presentera finansiella data.  Olika bubbelstorlekar är användbara för att visuellt betona specifika värden.

* för att använda med kvadranter.

### <a name="dot-plot-charts"></a>Punktritningsdiagram

Punktritningsdiagram liknar bubbeldiagram och punktdiagram men används istället till att rita numeriska data eller kategoridata utmed X-axeln.

![Skärmbild av ett punktritningsdiagram.](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

De är ett bra val om du vill inkludera kategoridata utmed X-axeln.

## <a name="prerequisites"></a>Förutsättningar

De här självstudierna använder sig av [PBIX-filen Exempel på detaljhandelsanalys](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Välj **Arkiv** > **Öppna** uppe till vänster på menyraden
   
2. Leta reda på kopian av **PBIX-filen Exempel för detaljhandelsanalys**

1. Öppna **PBIX-filen Exempel för detaljhandelsanalys** i rapportvyn ![Skärmbild av rapportvisningsikonen.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Välj ![Skärmbild av den gula fliken.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) för att lägga till en ny sida.


## <a name="create-a-scatter-chart"></a>Skapa ett punktdiagram

1. Börja på en tom rapportsida och välj följande fält i fönstret **Fält**:

    * **Försäljning** > **Försäljning efter kvm**

    * **Försäljning** > **Total försäljningsvarians %**

    * **Distrikt** > **Distrikt**

    ![Skärmbild av det grupperade kolumndiagrammet, visualiseringsfönstret och fältfönstret med de fält som du har valt framhävda.](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

1. I fönstret **Visualiseringar** väljer du ![Skärmbild av punktdiagramsikonen.](media/power-bi-visualization-scatter/power-bi-scatter-chart-icon.png) för att konvertera det grupperade kolumndiagrammet till ett punktdiagram.

   ![Skärmbild av hur det grupperade kolumndiagrammet blir ett punktdiagram.](media/power-bi-visualization-scatter/power-bi-scatter-new.png)

1. Dra **Distrikt** från **Information** till **Förklaring**.

    Power BI visar ett punktdiagram med **Total försäljningsvarians %** längs Y-axeln och **Försäljning per kvadratmeter** längs X-axeln. Datapunkternas färger representerar distrikt:

    ![Skärmbild av punktdiagrammet.](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Nu ska vi lägga till en tredje dimension.

## <a name="create-a-bubble-chart"></a>Skapa ett bubbeldiagram

1. Från fönstret **Fält** drar du **Försäljning** > **Försäljning detta år** > **Värdet** till området **Storlek**. Datapunkterna expanderar till storlekar som motsvarar försäljningsvärdet.

   ![Skärmbild av hur punktdiagrammet bli ett bubbeldiagram genom att lägga till Valerys försäljning till området Storlek.](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

1. Håll muspekaren över en bubbla. Storleken på bubblan reflekterar **försäljning detta år**.

    ![visning av knappbeskrivningar](media/power-bi-visualization-scatter/pbi-scatter-chart-hover.png)

1. Om du vill ange antalet datapunkter som ska visas i bubbeldiagrammet går du till **Format**-avsnittet i fönstret **Visualiseringar**, expanderar **Allmänt** och justerar **Datavolym**.

    ![Skärmbild av visualiseringsfönstret med formatikonen och listrutan Allmänt med alternativet Datavolym framhävt.](media/power-bi-visualization-scatter/pbi-scatter-data-volume.png)

    Du kan ange en största datavolym på upp till 10 000. För högre volymer föreslår vi att du först testar så att prestanda inte försämras.

    > [!NOTE]
    > Fler datapunkter kan medföra längre inläsningstid. Om du väljer att publicera rapporter med gränser i den högre änden av skalan, ska du vara noga med att även testa dina rapporter på webben och mobilt. Du vill få bekräftat att diagrammets prestanda matchar dina användares förväntningar.

1. Fortsätt att formatera visualiseringens färger, etiketter, rubriker, bakgrund med mera. Överväg att lägga till markörformer på varje linje för att [förbättra tillgängligheten](../desktop-accessibility.md). Välj markörform genom att expandera kortet **Former** och välja **Markörform** och sedan välja en form.

    ![Skärmbild av listrutan Former med alternativen för Markörform framhävda.](media/power-bi-visualization-scatter/pbi-scatter-marker.png)

    Ändra markörformen till en romb, triangel eller kvadrat. Med olika markörformer för varje linje är det enklare för rapportanvändare att skilja linjer (eller områden) från varandra.

1. Öppna fönstret Analytics ![Skärmbild av ikonen för fönstret Analytics.](media/power-bi-visualization-scatter/power-bi-analytics.png) för att lägga till ytterligare information i visualiseringen.  
    - Lägg till en medianlinje. Välj **Medianlinje** > **Lägg till**. Som standard lägger Power BI till en medianlinje för *Försäljning efter kvm*. Detta är inte särskilt användbart eftersom vi kan se att det finns 10 datapunkter och vi vet att medianen kommer att skapas med fem datapunkter på varje sida. Växla i stället **Mått** till *Total försäljningsvarians %* .  

        ![Skärmbild av bubbeldiagram med medianlinje tillagd.](media/power-bi-visualization-scatter/power-bi-analytics-median.png)

    - Lägg till symmetrifyllning för att visa vilka punkter som har ett högre värde för x-axelns mått jämfört med y-axelns mått och vice versa. När du aktiverar symmetrifyllning i fönstret Analytics visas Power BI-bakgrunden i punktdiagrammet symmetriskt baserat på den aktuella axelns övre och nedre gränser. Det här är ett snabbt sätt att identifiera vilken axel som mäter en datapunkt som prioriteras, särskilt när du har ett annat axelintervall för x- och y-axeln.

        a. Ändra fältet **Total försäljningsvarians %** till **Bruttomarginal förra året %**

        ![Skärmbild av bubbeldiagram med medianlinje tillagd.](media/power-bi-visualization-scatter/power-bi-format-symmetry.png)

        b. Lägg till **Symmetrifyllning** i fönstret Analytics. Vi kan se via skuggningen att Hosiery (Trikå) (den gröna bubblan i det rosa skuggade området) är den enda kategorin som prioriterar bruttomarginal i stället för försäljning per butikskvadratmeter. 

        ![Skärmbild av bubbeldiagram med symmetrifyllning tillagd.](media/power-bi-visualization-scatter/power-bi-symmetry.png)

    - Fortsätt att utforska fönstret Analytics för att upptäcka intressanta insikter i dina data. 

        ![Skärmbild av bubbeldiagram med symmetrifyllning tillagd.](media/power-bi-visualization-scatter/power-bi-analytics-example.png)

## <a name="create-a-dot-plot-chart"></a>Skapa ett punktritningsdiagram

Om du vill skapa ett punktritningsdiagram ersätter du det numeriska **X-axelfältet** med ett kategorifält.

Ta bort **försäljning per kvm** från fönstret **X-axel** och ersätt det med **Distrikt** > **Distriktschef**.

![Skärmbild av ett nytt punktritningsdiagram.](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

### <a name="your-scatter-chart-has-only-one-data-point"></a>Ditt punktdiagram har endast en datapunkt

Har du skapat ett punktdiagram där du bara ser en datapunkt som aggregerar alla värdena på X- och Y-axlarna?  Eller samlar diagrammet alla värden längs en enda vågrät eller lodrät linje?

![Skärmbild av ett punktdiagram med en datapunkt.](media/power-bi-visualization-scatter/pbi-scatter-tshoot1.png)

Lös problemet genom att lägga till ett fält i området **Information** som talar om för Power BI hur värdena ska grupperas. Fältet måste vara unikt för varje punkt som du vill rita. Ett enkelt radnummer eller ID-fält räcker bra.

![Skärmbild av ett punktdiagram med RowNum tillagt i området Information.](media/power-bi-visualization-scatter/pbi-scatter-tshoot.png)

Om du inte har detta i dina data, skapa ett fält som tillsammans sammanfogar X- och Y-värden till något unikt för varje punkt:

![Skärmbild av ett punktdiagram med TempTime tillagt i området Information.](media/power-bi-visualization-scatter/pbi-scatter-tshoot2.png)

Skapa ett nytt fält genom att [använda Power BI Desktop frågeredigeraren för att lägga till en indexkolumn](../desktop-add-custom-column.md) i din datauppsättning. Lägg sedan till den här kolumnen till området **Information** i din visualisering.

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Högdensitetssampling i Power BI-punktdiagram](desktop-high-density-scatter-charts.md)
* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Tips för att sortera och distribuera datapunkter i Power BI-rapporter](../guidance/report-tips-sort-distribute-data-plots.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
