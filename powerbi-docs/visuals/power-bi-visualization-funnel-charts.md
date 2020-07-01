---
title: Trattdiagram
description: Trattdiagram i Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: b0680df9a75d42f637632916bfd648943ba7517b
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85235834"
---
# <a name="create-and-use-funnel-charts"></a>Skapa och använda trattdiagram

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Med ett trattdiagram kan du visualisera en linjär process med intilliggande steg. Till exempel en försäljningstratt som spårar kunderna genom stadier: Lead \> kvalificerat lead \> potentiell kund \> avtal \> avslut.  Trattens form ger en översikt över processens tillstånd.

Varje steg i trattens motsvarar en procentandel av det totala antalet. I de flesta fallen är ett trattdiagram format som en tratt, där det första stadiet är störst och varje följande steg är mindre än det föregående.  En päronformad tratt kan också vara användbar – den kan identifiera ett problem i processen.  Men vanligtvis är det första stadiet, ”intaget”, det största.

![exempel på blå tratt](media/power-bi-visualization-funnel-charts/funnelplain.png)

> [!NOTE]
> För att dela en rapport med en Power BI-kollega krävs att du både har individuella Power BI Pro-licenser eller att rapporten har sparats med Premium-kapacitet.    

## <a name="when-to-use-a-funnel-chart"></a>När du ska använda ett trattdiagram
Trattdiagram är ett bra alternativ:

* När data är sekventiella och går genom minst 4 steg.
* När antalet ”objekt” i det första steget förväntas vara större än antalet i det sista steget.
* Om du vill beräkna potential (intäkter, försäljning, erbjudanden osv) i etapper.
* Om du vill beräkna och spåra konvertering och kvarhållning.
* Om du vill avslöja flaskhalsar i en linjär process.
* Om du vill spåra arbetsflödet i en kundvagn.
* Om du vill spåra förloppet och resultaten a en klickbaserad reklam-/marknadsföringskampanj.

## <a name="working-with-funnel-charts"></a>Arbeta med trattdiagram
Trattdiagram:

* Kan sorteras.
* Stöd för multipler.
* Kan markeras och korsfiltreras mot andra visualiseringar på samma rapportsida.
* Kan användas för markera och korsfiltrera andra visualiseringar på samma rapportsida.
   > [!NOTE]
   > Se hur Will skapar ett trattdiagram med exemplet på försäljning och marknadsföring i den här videon. Följ sedan stegen under videon för att prova själv med hjälp av PBIX-filen Exempel på Affärsmöjlighetsanalys
   > 
   > 
## <a name="prerequisite"></a>Förutsättning

De här självstudierna använder sig av [PBIX-filen Exempel på Affärsmöjlighetsanalys](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix
).

1. Välj **Arkiv** > **Öppna** uppe till vänster på menyraden
   
2. Hitta din kopia av **PBIX-filen Exempel på Affärsmöjlighetsanalys**

1. Öppna **PBIX-filen Exempel på Affärsmöjlighetsanalys** i rapportvyn ![Skärmbild av rapportvisningsikonen.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Välj ![Skärmbild av den gula fliken.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) för att lägga till en ny sida.


## <a name="create-a-basic-funnel-chart"></a>Skapa ett enkelt trattdiagram
Se hur Will skapar ett trattdiagram med exemplet på försäljning och marknadsföring i den här videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Nu kan du skapa ett eget trattdiagram som visar antalet möjligheter i varje försäljningsstadium.

1. Börja med en tom rapportsida och välj fältet **SalesStage** \> **Försäljningssteg**.
   
    ![välj försäljningsfas](media/power-bi-visualization-funnel-charts/funnelselectfield-new.png)

1. Välj trattikonen ![trattdiagramikon](media/power-bi-visualization-funnel-charts/power-bi-funnel-icon.png) för att konvertera kolumndiagrammet till ett trattdiagram.

2. I fönstret **Fält** väljer du **Fakta** \> **Antal affärsmöjligheter**.
   
    ![skapa trattdiagram](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. Håll muspekaren över en stapel för att visa en mängd information.
   
   * Stegets namn
   * Antalet affärsmöjligheter som finns i det här steget just nu
   * Övergripande konverteringstakt (% av leads) 
   * Steget-till-steg (kallas även förlusttakt) som är % av det föregående steget (i det här fallet förslagssteg/lösningssteg)
     
     ![information om förslagsfält](media/power-bi-visualization-funnel-charts/funnelhover-new.png)

6. [Spara rapporten](../create-reports/service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Markering och korsfiltrering
Information om hur du använder filterfönstret finns i [Lägg till ett filter i en rapport](../create-reports/power-bi-report-add-filter.md).

Om du markerar ett fält i trattdiagrammet korsfiltreras de övriga visualiseringarna på rapportsidan, och vice versa. Följ med och lägg till ytterligare några visuella objekt på rapportsidan som innehåller trattdiagrammet.

1. Välj fältet **Förslag** i trattdiagrammet. Detta korsmarkerar de övriga visualiseringarna på sidan. Använd CTRL för att välja flera.
   
   ![kort video som visar visuella interaktioner](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. För att hantera hur diagram korsmarkeras och korsfiltrerar varandra, se [Visualiseringsinteraktioner i en Power BI-rapport](../create-reports/service-reports-visual-interactions.md)

## <a name="next-steps"></a>Nästa steg

[Mätare i Power BI](power-bi-visualization-radial-gauge-charts.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)



