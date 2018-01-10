---
title: "Skapa en Power BI-instrumentpanel från en rapport"
description: "Skapa en Power BI-instrumentpanel från en rapport"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/09/2017
ms.author: mihart
ms.openlocfilehash: 67cc9508d71fa29303d09e8901294a2d6b7f8a56
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Skapa en Power BI-instrumentpanel från en rapport
Du har läst [Instrumentpaneler i Power BI](service-dashboards.md) och nu är det dags att du skapar en egen. Det finns många olika sätt för att skapa en instrumentpanel – från en rapport, från början, från en datauppsättning, genom att duplicera en befintlig instrumentpanel, med mera.  Det här avsnittet och videon visar hur du skapar en ny instrumentpanel genom att fästa visualiseringar från en befintlig rapport.

> **OBS**: Instrumentpaneler är en funktion i Power BI-tjänsten, inte i Power BI Desktop. Instrumentpaneler kan inte skapas i Power BI Mobile, men de kan [visas och delas](mobile-apps-view-dashboard.md).
> 
> 

![](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Video: Skapa en instrumentpanel genom att fästa visuella objekt och bilder från en rapport.
Titta på när Amanda skapar en ny instrumentpanel genom att fästa visualiseringar från en rapport. Prova sedan själv med hjälp av Exempel på anskaffningsanalys genom att följa stegen under videon.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importera en datauppsättning med en rapport
Vi ska importera ett av Power BI:s exempel på datauppsättningar och använda det för att skapa vår nya instrumentpanel. Exemplet vi ska använda är en Excel-arbetsbok med två PowerView-blad. När Power BI importerar arbetsboken, läggs en datauppsättning och en rapport till på din arbetsyta.  Rapporten skapas automatiskt från PowerView-bladen.

1. [Välj den här länken](http://go.microsoft.com/fwlink/?LinkId=529784) för att hämta och spara Excel-filen Exempel på anskaffningsanalys. Vi rekommenderar att du sparar den i din OneDrive för företag.
2. Öppna Power BI-tjänsten i din webbläsare (app.powerbi.com).
3. Välj en befintlig arbetsyta eller skapa en ny app-arbetsyta.
4. Välj **Hämta data** i det vänstra navigeringsfältet.
   
    ![](media/service-dashboard-create/power-bi-get-data3.png)
5. Välj **Filer**.
   
   ![](media/service-dashboard-create/power-bi-select-files.png)
6. Gå till den plats där du sparade Excel-filen Exempel på anskaffningsanalys. Markera den och välj **Anslut**.
   
   ![](media/service-dashboard-create/power-bi-connectnew.png)
7. För den här övningen väljer vi **Importera**.
   
    ![](media/service-dashboard-create/power-bi-import.png)
8. När meddelandet om slutförd import visas, väljer du **x** för att stänga det.
   
   ![](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>Öppna rapporten och fästa några paneler på en instrumentpanel
1. Stanna kvar på samma arbetsyta och välj fliken **Rapporter**. Den nyligen importerade rapporten visas med en gul asterisk. Välj rapportens namn för att öppna den.
   
    ![](media/service-dashboard-create/power-bi-reports.png)
2. Öppna rapporten i [Läsvy](service-reading-view-and-editing-view.md). Observera att den har två flikar längst ned: Rabattanalys och Utgiftsöversikt. Varje flik representerar en sida i rapporten.
   
    ![](media/service-dashboard-create/power-bi-reading-view.png)
3. Hovra över en visualisering för att visa de tillgängliga alternativen. Välj stiftikonen ![](media/service-dashboard-create/power-bi-pin-icon.png) för att lägga till en visualisering på en instrumentpanel.
   
    ![](media/service-dashboard-create/power-bi-hover.png)
4. Eftersom vi skapar en ny instrumentpanel, markerar du alternativet **Ny instrumentpanel** och ge den ett namn. 
   
   ![](media/service-dashboard-create/power-bi-pin-tile.png)
5. När du väljer **Fäst**, skapar Power BI den nya instrumentpanelen på den aktuella arbetsytan. När meddelandet **Fäst på instrumentpanelen** visas, väljer du **Gå till instrumentpanelen**. Om du uppmanas att spara rapporten väljer du **Spara**.
   
     ![](media/service-dashboard-create/power-bi-pin-success.png)
6. Power BI öppnar den nya instrumentpanelen och där visas en panel – den visualisering som vi nyss fäste på den. 
   
   ![](media/service-dashboard-create/power-bi-pinned.png)
7. Välj panelen för att återgå till rapporten. Fäst några fler paneler på den nya instrumentpanelen. Den här gången när fönstret **Fäst på instrumentpanelen** visas, väljer du **Befintlig instrumentpanel**.  
   
   ![](media/service-dashboard-create/power-bi-existing-dashboard.png)

Grattis – du har skapat din första instrumentpanel! Nu när du har en instrumentpanel finns det så mycket mer du kan göra.  Försök med något av de föreslagna **nästa stegen** nedan, eller börja leka lite och utforska på egen hand.   

## <a name="next-steps"></a>Nästa steg
* [Redigera och flytta paneler](service-dashboard-edit-tile.md)
* [Allt om panelerna på instrumentpanelen](service-dashboard-tiles.md)
* [Dela din instrumentpanel genom att skapa en app](service-create-distribute-apps.md)
* [Power BI – grundläggande begrepp](service-basic-concepts.md)
* [Instrumentpaneler i Power BI](service-dashboards.md)
* [Tips för att designa en bra instrumentpanel](service-dashboards-design-tips.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

