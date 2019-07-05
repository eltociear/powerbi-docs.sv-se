---
title: Anpassa egenskaper för X-axeln och Y-axeln
description: Anpassa egenskaper för X-axeln och Y-axeln
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3bfe84acdf73fcb5ace791c9a84943262d0f73ab
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390053"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Anpassa egenskaper för X-axeln och Y-axeln

I den här kursen lär du dig många olika sätt att anpassa X-axeln och Y-axeln i visuella objekt. Inte alla visuella objekt har axlar. Cirkeldiagram har till exempel inte axlar. Och anpassningsalternativen varierar från ett visuellt objekt till ett annat. Det finns alltför många alternativ för att vi ska kunna ta upp alla i en enda artikel, så vi tar en titt på några av de mest använda axelanpassningarna så att du kan vänja dig vid att använda panelen för **visuell formatering** i arbetsytan för Power BI-rapporter.  

> [!NOTE]
> Det här avsnittet gäller för både Power BI-tjänsten och Power BI Desktop. Dessa anpassningar, som är tillgängliga när **Format** (rollerikonen ![Skärmbild av rollerikonen.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) är markerad, är också tillgängliga i Power BI Desktop.

Se hur Amanda anpassar sina X- och Y-axlar. Hon kommer att demonstrera de olika sätten att styra sammanlänkning vid minskning och ökning av detaljnivån.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Förutsättningar

- Power BI-tjänsten

- Rapporten Exempel på detaljhandelsanalys

## <a name="customize-visualization-x--and-y-axes-in-reports"></a>Anpassa X- och Y-axlar för visualiseringar i rapporter

Om du vill följa med loggar du in till [Power BI-tjänsten](https://app.powerbi.com) och öppnar rapporten [Exempel på detaljhandelsanalys](../sample-datasets.md) i vyn [Redigera rapport](../service-interact-with-a-report-in-editing-view.md).

### <a name="create-a-stacked-column-chart-visualization"></a>Skapa en visualisering av ett staplat kolumndiagram

Du måste skapa din visualisering innan du kan anpassa den.

1. Visa **Min arbetsyta** i Power BI-tjänsten.

1. Bläddra nedåt och välj **Exempel på detaljhandelsanalys** från listan över **datamängder**.

1. På panelen **Visualiseringar** väljer du ikonen för staplat kolumndiagram.

    ![Skärmbild av fönstret Visualiseringar och ett tomt staplat kolumndiagram](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stacked-column-chart.png)

1. Välj **Tid** > **FiscalMonth** (Räkenskapsmånad) för att ange X-axelns värden i fönstret **Fält**.

1. För att ställa in Y-axelvärdena på panelen **Fält**, väljer du **Försäljning** > **Senaste årets försäljning** och **Försäljning** > **Försäljning detta år** > **Värde**.

    ![Skärmbild av det ifyllda staplade kolumndiagrammet.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

### <a name="customize-the-x-axis"></a>Anpassa X-axeln

Nu kan du anpassa din X-axel.

1. I fönstret **Visualiseringar** väljer du **Format** (rollerikonen) ![Skärmbild av rollerikonen.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) för att visa anpassningsalternativen.

1. Alternativ för att expandera X-axlarna.

   ![Skärmbild av X-axelns alternativ.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)

1. Flytta skjutreglaget för **X-axeln** till läget **På**.

    ![Skärmbild av skjutreglaget i läge På.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Du kanske vill inaktivera X-axeln för att spara utrymme för mer data.

1. Formatera textfärg, storlek och teckensnitt:

    - **Färg**: Välj svart

    - **Textstorlek**: Ange *14*

    - **Teckensnittsfamilj**: Välj **Arial Black**

1. Dra alternativet **Rubrik** till **På** för att visa namnet på X-axeln. I det här fallet är det **FiscalMonth** (Räkenskapsmånad).

1. Formatera rubrikens textfärg, storlek och teckensnitt:

    - **Rubrikfärg**: Välj orange

    - **Axelrubrik**: Ange *Räkenskapsmånad*

    - **Storlek för rubriktext** : Ange *21*

När du är klar med anpassningarna ser det staplade kolumndiagrammet ut ungefär så här:

![Skärmbild av det anpassade staplade kolumndiagrammet.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

Spara de ändringar som du har gjort och gå vidare till nästa avsnitt.

Om du vill återställa alla ändringar, väljer du **Återgå till standard** längst ned i anpassningsfönstret **X-axel**.

### <a name="customize-the-y-axis"></a>Anpassa Y-axeln

Nu ska du anpassa Y-axeln.

1. Alternativ för att expandera Y-axeln.

   ![Skärmbild av Y-axelns alternativ.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

1. Flytta skjutreglaget för **Y-axeln** till läget **På**.  

    ![Skärmbild av skjutreglaget i läge På.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Du kan vilja stänga av Y-axeln för att spara utrymme för mer data.

1. Ange Y-axelns **Position** som **Höger**.

1. Formatera textfärg, storlek och teckensnitt:

    - **Färg**: Välj svart

    - **Textstorlek**: Ange *14*

    - **Teckensnittsfamilj**: Välj **Arial Black**

1. Ställ in **Visningsenheter** på **Miljoner** och **Decimaler för värdet** på *0*.

1. För det här visuella objektet förbättras inte visualiseringen av en rubrik för Y-axeln, så vi **inaktiverar** **Rubrik**.  

1. Nu ska vi få stödlinjerna att stå ut genom att ändra färgen och öka bredden på dem:

    - **Färg**: Välj mörkgrå

    - **Linjebredd**: Ange *2*

Efter dessa anpassningar bör ditt stående stapeldiagram se ut ungefär så här:

![Skärmbild av diagrammet med anpassad Y-axel.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Anpassa visualiseringar med dubbla Y-axlar

Först måste du skapa ett kombinationsdiagram som visar hur antalet butiker påverkar försäljningen. Det här är samma diagram som har skapats i [självstudierna om kombinationsdiagram](power-bi-visualization-combo-chart.md). Sedan ska du formatera de två Y-axlarna.

### <a name="create-a-chart-with-two-y-axes"></a>Skapa ett diagram med två Y-axlar

1. Skapa ett nytt linjediagram som spårar **Försäljning >Bruttomarginal %** förra året per **Tid > bokföringsmånad**.

    ![Skärmbild av det nya linjediagrammet.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

    > [!NOTE]
    > För hjälp med att sortera efter månad, läs vidare under [Sortera med andra kriterier](../consumer/end-user-change-sort.md#other).

    I januari var bruttomarginalprocenten 35 % med en topp i april på 45 % varefter den sjönk i juli och nådde ytterligare en topp i augusti. Ser vi ett liknande mönster för försäljningen föregående år och det här året?

1. Lägg till **This Year Sales (Årets försäljning) > Värde** och **Last Years Sales (Förra årets försäljning)** till linjediagrammet.

    ![Skärmbild av linjediagrammet med nya data tillagda.](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)

    Skalan för **Bruttomarginal förra året i %** (den blå linjen som löper längs med stödlinjen för **0M %** ) är mycket mindre än skalan för **Försäljning**, vilket gör det svårt att jämföra. Och Y-axelns etikettprocenttal är märkliga.

1. Konvertera linjediagrammet till ett linje- och staplat kolumndiagram om du vill göra det visuella objektet lättare att läsa och tolka.

   ![Skärmbild av fönstret Visualiseringar med linje- och det staplade kolumndiagrammet framhävt.](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

1. Dra **Gross Margin% Last Year (Bruttomarginal % förra året)** från **Kolumnvärde** till **Radvärden**.

    ![Skärmbild av linje- och det staplade kolumndiagrammet med alla tre värden tydligt representerade.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)

    Nu har du det staplade kolumndiagram som du skapade i det första avsnittet med ett linjediagram lagt över det. Du kan också använda vad du lärde dig ovan för att formatera axlarnas teckenfärg och storlek.

   ![Skärmbild av det anpassade linje- och staplade kolumndiagrammet.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

   Power BI skapar två Y-axlar, vilket gör att datamängderna kan skalas på olika sätt. Den vänstra mäter försäljningen i dollar och den högra procentandelen.

### <a name="format-the-secondary-y-axis"></a>Formatera den sekundära Y-axeln

1. I fönstret **Visualiseringar** väljer du rollerikonen för att visa formatalternativen.

1. Alternativ för att expandera Y-axeln.

1. Rulla nedåt tills du hittar alternativet **Visa sekundär**. Kontrollera att det är **På**.

   ![Skärmbild av alternativet Visa sekundär.](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

1. (Valfritt) Anpassa två axlar. Om du växlar **Position** för axelns kolumn eller radaxeln. Det går de två axlarna att växla sidor.

### <a name="add-titles-to-both-axes"></a>Lägga till rubriker på axlarna

Med ett så komplicerat visuellt objekt hjälper det att lägga till axelrubriker.  Med rubriker blir det lättare för dina kollegor att förstå vad du försöker berätta med ditt visuella objekt.

1. Växla **Rubrik** till **På** för **Y-axeln (kolumn)** och **X-axeln (rad)** .

1. Ange **Stil** till **Visa enbart rubrik** för båda.

   ![Skärmbild av alternativen Rubrik och Stil.](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)

1. Kombinationsdiagrammet visar nu dubbla axlar, båda med rubriker.

   ![Skärmbild av det anpassade diagrammet med dubbla y-axlar.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

Mer information finns i [Tips för färgformatering i Power BI](service-tips-and-tricks-for-color-formatting.md).

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

Om X-axeln kategoriseras av rapportägaren som av datumtyp, kommer alternativet **Typ** att visas och du kan välja mellan kontinuerlig eller kategorisk.

## <a name="next-steps"></a>Nästa steg

- [Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

- [Anpassa visualiseringens rubriker, bakgrunder och förklaringar](power-bi-visualization-customize-title-background-and-legend.md)

- [Komma igång med färgformatering och axelegenskaper](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Grundläggande begrepp för Power BI-tjänstens användare](../consumer/end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
