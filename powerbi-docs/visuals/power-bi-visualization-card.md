---
title: Kortvisualiseringar (även kallat stor sifferpanel)
description: Skapa en kortvisualisering i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b15d285774f0b6735fbc5df0ca2d00a81b944012
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829951"
---
# <a name="card-visualizations"></a>Kortvisualiseringar
Ett enda tal kan ibland vara det viktigaste du vill spåra i Power BI-instrumentpanelen eller -rapporten, till exempel total försäljning, marknadsandel år för år eller totala affärsmöjligheter. Den här typen av visualisering kallas ett *kort*. Som nästan alla ursprungliga Power BI-visualiseringar, kan kort skapas med hjälp av rapportredigeraren eller Frågor och svar.

![kortvisualisering](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Skapa ett kort med hjälp av rapportredigeraren
Dessa anvisningar använder sig av Exempel på detaljhandelsanalys. Om du vill följa med kan du [hämta exemplet](../sample-datasets.md) för Power BI-tjänsten (app.powerbi.com) eller Power BI Desktop.   

1. Börja med en tom rapportsida och välj fältet **Butik** \> **Antal öppna butiker**. Om du använder Power BI-tjänsten måste du öppna rapporten i [redigeringsvyn](../service-interact-with-a-report-in-editing-view.md).

    Power BI skapar ett stapeldiagram med ditt tal.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. I fönstret Visualiseringar väljer du färgrollerikonen.

   ![](media/power-bi-visualization-card/power-bi-templates.png)
6. Hovra över kortet och välj stiftikonen ![](media/power-bi-visualization-card/pbi_pintile.png) för att lägga till visualiseringen på instrumentpanelen.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Fäst panelen på en befintlig eller ny instrumentpanel.

   * Befintlig instrumentpanel: välj instrumentpanelens namn i listrutan.
   * Ny instrumentpanel: Skriv instrumentpanelens namn.
8. Välj **Fäst**.

   Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.

   ![](media/power-bi-visualization-card/power-bi-success2.png)
9. Välj **Gå till instrumentpanelen**. Där kan du [redigera och flytta](../service-dashboard-edit-tile.md) den fästa visualiseringen.


## <a name="create-a-card-from-the-qa-question-box"></a>Skapa ett kort från frågerutan för frågor och svar
Att använda frågerutan för frågor och svar är den enklaste metoden för att skapa ett kort. Frågerutan för frågor och svar är tillgänglig i Power BI-tjänsten från en instrumentpanel eller rapport samt i rapportvyn Desktop. Stegen nedan beskriver hur du skapar ett kort från en instrumentpanel i Power BI-tjänsten. Om du vill skapa ett kort med Frågor och svar i Power BI Desktop [, följer du nedanstående instruktioner](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA) för Frågor och svar-förhandsgranskning för Desktop-rapporter.

1. Skapa en [instrumentpanel](../service-dashboards.md) och [hämta data](../service-get-data.md). Det här exemplet använder sig av [exemplet affärsmöjlighetsanalys](../sample-opportunity-analysis.md).

1. Börja skriva vad du vill veta om dina data i frågerutan överst på instrumentpanelen. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

> [!TIP]
> Gå till redigeringsvyn i Power BI-tjänsterapporten och välj **Ställ en fråga** på den översta menyraden. I en Power BI Desktop-rapport letar du upp ett öppet utrymme i en rapport och dubbelklickar för att öppna en frågeruta.

3. Skriv till exempel ”antal affärsmöjligheter” i frågerutan.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   Frågerutan hjälper dig med förslag och rättelser och visar slutligen det totala antalet.  
4. Välj stiftikonen ![](media/power-bi-visualization-card/pbi_pintile.png) i det övre högra hörnet för att lägga till kortet på en instrumentpanel.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. Fäst kortet, som en panel, på en befintlig eller ny instrumentpanel.

   * Befintlig instrumentpanel: välj instrumentpanelens namn i listrutan. Dina val begränsas till instrumentpanelerna inom den aktuella arbetsytan.
   * Ny instrumentpanel: ange namnet på den nya instrumentpanelen så läggs den till din aktuella arbetsyta.
6. Välj **fäst**.

   Genom ett meddelande (nära det övre högra hörnet) får du reda på att visualiseringen har lagts till, som en panel, på instrumentpanelen.  

   ![](media/power-bi-visualization-card/power-bi-success2.png)
7. Välj **gå till instrumentpanel** för att se den nya panelen. Där kan du [byta namn på, ändra storlek, lägga till en hyperlänk och flytta panelen och mer](../service-dashboard-edit-tile.md) på din instrumentpanel.

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- Om du inte ser någon frågeruta, kontakta din system- eller klientadministratör.    
- Om du använder Desktop och Frågor och svar inte öppnas när du dubbelklickar på ett tomt utrymme i en rapport, kan du behöva aktivera funktionen.  Välj **Fil > Alternativ och inställningar > Alternativ > Förhandsversionsfunktioner > Frågor och svar** och starta om Desktop.

## <a name="format-a-card"></a>Formatera ett kort
Du har många alternativ för att ändra etiketter, text, färg med mera. Det bästa sättet att lära dig är att skapa ett kort och sedan utforska formateringsfönstret. Här följer några tillgängliga formateringsalternativ. 

1. Börja genom att välja färgrollerikonen för att öppna formateringsfönstret. 

    ![kort med färgroller markerad](media/power-bi-visualization-card/power-bi-format-card.png)
2. Expandera **Dataetikett** och ändra färg, storlek och teckensnittsfamilj. Om du har tusentals butiker, kan du använda **Visningsenheter** för att visa antal butiker med tusentalsavgränsare och kontrollera antalet decimaler också. Till exempel 125,8K i stället för 125 832,00.

3.  Expandera **Kategorietikett** och ändra storlek och färg.

    ![mörkblå färg vald](media/power-bi-visualization-card/power-bi-card-format.png)

4. Expandera **Bakgrund** och flytta skjutreglaget till På.  Nu kan du ändra bakgrundsfärgen och transparensen.

    ![skjutreglaget är satt till PÅ](media/power-bi-visualization-card/power-bi-format-color.png)

5. Fortsätt att utforska formateringsalternativen tills kortet är exakt som du vill. 

    ![Kort när all formatering är klar](media/power-bi-visualization-card/power-bi-formatted.png)

## <a name="next-steps"></a>Nästa steg
[Kombinationsdiagram i Power BI](power-bi-visualization-combo-chart.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
