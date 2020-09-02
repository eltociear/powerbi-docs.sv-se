---
title: 'Självstudie: Kom igång med att skapa i Power BI-tjänsten'
description: Kom igång med Power BI-tjänsten online (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/08/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: d40bda8ef6469e5dc826d36db3cc21cfe72f0da6
ms.sourcegitcommit: 70a892df1a0c196db58bf9165b3aa31b26bbe149
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2020
ms.locfileid: "89092393"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Självstudie: Kom igång med att skapa i Power BI-tjänsten
Den här självstudien är en introduktion till några av funktionerna i *Power BI-tjänsten*. I självstudien ansluter du till data, skapar en rapport och en instrumentpanel och ställer frågor om dina data. Du kan göra mycket mer i Power BI-tjänsten. Den här självstudien är bara en aptitretare. Om du vill förstå hur Power BI-tjänsten passar ihop med andra Power BI-erbjudanden rekommenderar vi att du läser [Vad är Power BI](power-bi-overview.md).

Är du *rapportläsare* snarare än rapportskapare? [Navigera i Power BI-tjänsten](../consumer/end-user-experience.md) är ett bra ställe att börja.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Skärmbild av instrumentpanelen Financial Sample.":::

I den här självstudien går du igenom följande steg:

> [!div class="checklist"]
> * Logga in på ditt Power BI-onlinekonto, eller registrera dig om du inte har ett konto.
> * Öppna Power BI-tjänsten.
> * Hämta några data och öppna dem i rapportvyn.
> * Använd dessa data för att skapa visualiseringar och spara dem som en rapport.
> * Skapa en instrumentpanel genom att fästa paneler från rapporten.
> * Lägg till ytterligare visualiseringar på instrumentpanelen med verktyget för frågor och svar på naturligt språk.
> * Ändra storlek på, ordna om och redigera information för panelerna på instrumentpanelen.
> * Rensa resurser genom att ta bort datamängden, rapporten och instrumentpanelen.

## <a name="sign-up-for-the-power-bi-service"></a>Registrera dig för Power BI-tjänsten
Du behöver en Power BI Pro-licens för att skapa innehåll i Power BI. Om du inte har något Power BI-konto [registrerar du dig för en kostnadsfri Power BI Pro-utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

## <a name="step-1-get-data"></a>Steg 1: Hämta data

När du vill skapa en Power BI-rapport börjar du ofta i Power BI Desktop. Power BI Desktop ger mer kraft. Du kan transformera, forma och modellera data innan du börjar designa rapporten. Den här gången börjar vi dock från början med att skapa en rapport i Power BI-tjänsten.

I den här självstudien hämtar vi data från en enkel Microsoft Excel-fil. Vill du hänga på? [Ladda ned filen Financial Sample](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Börja med att öppna Power BI-tjänsten (app.powerbi.com) i webbläsaren. 

    Har du inte något konto? Inga problem – du kan [registrera dig för en kostnadsfri utvärderingsversion av Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web)

1. Välj **Min arbetsyta** i navigeringsfönstret.

1. I **Min arbetsyta** väljer du **Ny** > **Ladda upp en fil**.

    Sidan **Hämta data** öppnas.   

3. I avsnittet **Skapa nytt innehåll** ser du till att **Filer** är valt och väljer sedan den plats där du skapade Excel-filen.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Skärmbild av fönstret Skapa nytt innehåll > Filer.":::

5. Bläddra till filen på datorn och välj **Öppna**.

5. I den här självstudien väljer vi **Importera** för att lägga till Excel-filen som en datauppsättning som vi sedan kan använda för att skapa rapporter och instrumentpaneler. Om du väljer **Ladda upp** laddas hela Excel-arbetsboken upp till Power BI, där du kan öppna och redigera den i Excel Online.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Skärmbild av valet av Importera.":::
6. När datamängden är redo väljer du **Fler alternativ (...)** intill datamängden Financial Sample och väljer sedan **Skapa rapport**.
1. Öppna rapportredigeraren. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Skärmbild av Allt innehåll > Skapa rapport.":::

    Rapportarbetsytan är tom. På höger sida visas fönstren **Filter**, **Visualiseringar** och **Fält**.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Skärmbild av en tom rapportarbetsyta.":::

    > [!TIP]
    > Välj den globala navigeringsknappen i det övre vänstra hörnet för att dölja navigeringsfönstret. På så sätt får arbetsyta mer plats.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Den globala navigeringsknappen.":::
    >

7. Du är för närvarande i redigeringsvyn. Observera alternativet **Läsvy** i menyraden. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Skärmbild av alternativet Läsvy.":::

    I redigeringsvyn kan du ändra rapporter eftersom du är *ägare* till och *skapare* av rapporten. När du delar rapporten med kollegor kan de ofta bara interagera med rapporten i läsvyn. De är *konsumenter* av rapporter i din **Min arbetsyta**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Steg 2: Skapa ett diagram i en rapport
Nu när du har anslutit till dina data kan du börja utforska omgivningarna. När du har hittat något intressant kan du spara den på rapportarbetsytan. Sedan kan du fästa den på en instrumentpanel för att övervaka den och se hur den ändras med tiden. Men en sak i taget.
    
1. I rapportredigeraren börjar du i fönstret **Fält** till höger på sidan för att skapa en visualisering. Välj fältet **Gross Sales** (Bruttoförsäljning) och sedan fältet **Date** (Datum).
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Skärmbild av listan Fält.":::

    Power BI analyserar informationen och skapar en visualisering för kolumndiagram. 

    > [!NOTE]
    > Om du valde fältet **Date** först i stället för **Gross Sales** visas en tabell. Det gör inget! Vi ska ändra visualiseringen i nästa steg.

    Intill vissa fält finns sigmasymboler eftersom Power BI identifierade att de innehåller numeriska värden.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Fält med sigmasymboler.":::

2. Vi växlar till ett annat sätt att visa dessa data. Linjediagram är bra visuella objekt för att visa värden över tid. Välj ikonen för **linjediagram** i fönstret **Visualiseringar**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Skärmbild av rapportredigeraren med linjediagram valt.":::

3. Det här diagrammet ser intressant ut så vi *fäster* det på en instrumentpanel. Hovra över visualiseringen och välj fästikonen.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Ögonblicksbild av ikonen Fäst.":::

4. Eftersom den här rapporten är ny uppmanas du att spara den innan du kan fästa en visualisering på instrumentpanelen. Ge rapporten ett namn (till exempel *Financial Sample report*) och **Spara** sedan. 

    Nu tittar du på rapporten i läsvyn. 

6. Välj ikonen **Fäst** igen.
 
5. Välj **Ny instrumentpanel** och ge den till exempel namnet *Financial Sample dashboard*. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Skärmbild av namngivning av instrumentpanelen.":::
  
    Ett meddelande (nära det övre högra hörnet) anger att visualiseringen har lagts till som en panel på instrumentpanelen.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Skärmbild av dialogrutan Fäst på instrumentpanelen.":::

    Nu när du har fäst visualiseringen lagras den på instrumentpanelen. Data hålls uppdaterade så att du snabbt kan spåra det senaste värdet. Om du däremot ändrar visualiseringstypen i rapporten ändras inte visualiseringen på instrumentpanelen.

7. Välj **Gå till instrumentpanelen** för att se den nya instrumentpanelen med linjediagrammet som du fäste som en panel på instrumentpanelen. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Skärmbild av instrumentpanel med en fäst visualisering.":::
   
8. Välj den nya panelen på instrumentpanelen. Power BI visar rapporten i läsvyn.

1. Du kan gå tillbaka till redigeringsvyn genom att välja **Fler alternativ** (...) i menyraden > **Redigera**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Skärmbild av val av Redigera för att redigera rapporten.":::

    När du är i redigeringsvyn kan du fortsätta att utforska och fästa paneler.

## <a name="step-3-explore-with-qa"></a>Steg 3: Utforska med frågor och svar

Om du vill utforska dina data snabbt kan du prova med att ställa en fråga i rutan Frågor och svar. Med Frågor och svar kan du ställa frågor på naturligt språk om dina data. På en instrumentpanel finns rutan Frågor och svar längst upp (**Ställ en fråga om dina data**) under menyraden. I en rapport finns den i den översta menyraden (**Ställ en fråga**).

1. Om du vill gå tillbaka till instrumentpanelen väljer du **Min arbetsyta** i det svarta **Power BI**-rubrikfältet.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Skärmbild av Gå tillbaka till Min arbetsyta.":::

1. I **Min arbetsyta** väljer du din instrumentpanel.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Skärmbild av val av din instrumentpanel.":::

1. Välj **Ställ en fråga om dina data**. Frågor och svar visar automatiskt ett antal förslag. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Skärmbild av arbetsyta för vanliga frågor och svar.":::

    > [!NOTE]
    > Om du inte kan se förslagen aktiverar du **Nya frågor och svar-upplevelsen**.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Skärmbild av aktivering av den nya upplevelsen för vanliga frågor och svar.":::

1. Några förslag returnerar ett enskilt värde. Välj exempelvis **what is the average cog** (vad är genomsnittligt cog).

    Frågor och svar söker efter svar och visar dem i form av en *kortvisualisering*.

3. Välj **Fäst visuellt objekt** och fäst den här visualiseringen på instrumentpanelen Financial Sample.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Skärmbild av det visuella objekt som fästs.":::

1. Gå tillbaka till Vanliga frågor och svar och välj **Visa alla förslag**.
1. Välj **total profit by country** (total vinst per land). 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Skärmbild av total vinst per land.":::

1. Fäst kartan på instrumentpanelen Financial Sample också.

1. På instrumentpanelen väljer du den karta som du just fäste. Ser du hur det gör att Vanliga frågor och svar öppnas igen? 
1. Placera markören efter *by country* (efter land) i rutan Frågor och svar och skriv *as bar* (som stapel). Power BI skapar ett stapeldiagram med resultatet.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Skärmbild av en visualisering av ett stapeldiagram.":::

1. Fäst stapeldiagrammet på instrumentpanelen Financial Sample också.

4. Välj **Avsluta frågor och svar** för att återgå till instrumentpanelen, där du kan se de nya panelerna du skapade. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Skärmbild av instrumentpanel med visuella objekt för Vanliga frågor och svar som fästs.":::

   Du kan se att panelen fortfarande är en karta, trots att du ändrade kartan till ett linjediagram i Vanliga frågor och svar. Det beror på att panelen var en karta när du fäste den. 

## <a name="step-4-reposition-tiles"></a>Steg 4: Flytta paneler

Vi kan ordna om panelerna så att vi kan utnyttja instrumentpanelens utrymme på ett bättre sätt.

1. Dra i det nedre högra hörnet av panelen med linjediagrammet *Bruttoförsäljning* uppåt tills den fäster på plats i samma höjd som panelen Försäljning och släpp sedan panelen.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Skärmbild av ändring av storleken på panelen.":::

    Nu har de två panelerna samma höjd.

1. Välj **Fler alternativ (...)** för panelen Average of COGS (Genomsnitt för COGS) > **Redigera information**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Skärmbild av menyn Fler alternativ för en panel.":::

1. I rutan **Rubrik** skriver du *Average Cost of Goods Sold* > **Tillämpa**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Skärmbild av dialogrutan Redigera information.":::

1. Ordna om de andra visuella objekten så att de passar ihop.

    Det ser bättre ut.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Skärmbild av omorganiserad instrumentpanel.":::


## <a name="clean-up-resources"></a>Rensa resurser
Nu när du är klar med självstudien kan du ta bort datauppsättningen, rapporten och instrumentpanelen. 

1. Välj **Min arbetsyta** i det svarta **Power BI**-rubrikfältet.
2. Välj **Fler alternativ (...)** intill datamängden Financial Sample > **Ta bort**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Skärmbild av borttagning av datamängden.":::

    En varning visas om att **Alla rapporter och instrumentpanelsflikar som innehåller data från den här datamängden kommer också att tas bort**.

4. Välj **Ta bort**.

## <a name="next-steps"></a>Nästa steg

Utforska de här samlingarna med Microsoft Learn-innehåll för Power BI:

- [Lär dig Power BI](https://docs.microsoft.com/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
- [Bli Power BI-dataanalytiker](https://docs.microsoft.com/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)
