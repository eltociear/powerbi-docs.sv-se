---
title: "Använda Power BI-exempel, självstudier."
description: "Självstudier: Använda Power BI-exempel"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 03/08/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: d92edce9ae1332c4a0c73be5db93201c9b87dc86
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2018
---
# <a name="the-power-bi-samples-a-tutorial"></a>Power BI-exempel, självstudier
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

Vi rekommenderar att du börjar med artikeln [Exempel på datauppsättningar för Power BI](sample-datasets.md). I den här artikeln får du lära dig allt om exemplen. Hur du hämtar dem, var du sparar dem, hur du använder dem och några av de budskap som varje exempel kan förmedla. Sedan, när du har ett grepp om grunderna, kan gå tillbaka till de här självstudierna.   

## <a name="about-this-tutorial"></a>Om självstudierna
I de här självstudierna lär du dig hur du importerar exemplen på innehållspaket, lägger till dem i Power BI-tjänsten och öppnar innehållet. Ett *innehållspaket* är en typ av exempel där datauppsättningen har paketerats med en instrumentpanel och en rapport. Exemplen på innehållspaket är tillgängliga i Power BI med hjälp av **Hämta data**.

> [!NOTE]
> De här självstudierna handlar om Power BI-tjänsten och inte Power BI Desktop.
> 
> 

Innehållspaketet för *Exempel på detaljhandelsanalys* som används i de här självstudierna består av en instrumentpanel, en rapport och en datauppsättning.
Om du vill bekanta dig med det här specifika innehållspaketet och dess scenario, kan du [ta en titt på exemplet på detaljhandelsanalys](sample-retail-analysis.md) innan du börjar.

## <a name="get-data-in-this-case-get-a-sample-content-pack"></a>Hämta data (i det här fallet, hämta ett exempel på ett innehållspaket)
1. Öppna Power BI-tjänsten och logga in (app.powerbi.com).
2. Välj en arbetsyta och skapa en ny instrumentpanel.  
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-create-dashboard2.png)
3. Döp den till **Exempel på detaljhandelsanalys**.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-name-dashboard.png)
4. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret. Om du inte ser **Hämta data** kan du expandera navigeringsfönstret genom att välja ![](media/sample-tutorial-connect-to-the-samples/expand-nav.png).
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_getdata.png)
5. Välj **Exempel**.  
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_samplesdownload.png)
6. Välj *Exempel på detaljhandelsanalys* och sedan **Anslut**.   
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-exactly-was-imported"></a>Vad exakt importerades?
När du arbetar med exemplen på innehållspaket och väljer **Anslut**, hämtar Power BI en kopia av det aktuella innehållspaketet och lagrar det åt dig i molnet. Eftersom den person som skapade innehållspaketet inkluderade en datauppsättning, en rapport och en instrumentpanel – är det det som du får när du klickar på **Anslut**.

1. Power BI skapar den nya instrumentpanelen och visar den på fliken **Instrumentpaneler**. Den gula asterisken visar att den är ny.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dashboard.png)
2. Öppna fliken **Rapporter**.  Här visas en ny rapport med namnet *Exempel på detaljhandelsanalys*.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Titta närmare på fliken **Datauppsättningar**.  Där finns även en ny datauppsättning.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Utforska ditt nya innehåll
Utforska nu instrumentpanelen, datauppsättningen och rapporten på egen hand. Det finns många olika sätt för att navigera till dina instrumentpaneler, rapporter och datauppsättningar och bara ett av dessa sätt beskrivs nedan.  

> [!TIP]
> Vill du ha lite stöd på vägen först?  Prova [rundturen i exemplet för detaljhandelsanalys](sample-retail-analysis.md) för en stegvis genomgång av det här exemplet.
> 
> 

1. Gå tillbaka till fliken **Instrumentpaneler** och markera instrumentpanelen *Exempel på detaljhandelsanalys* för att öppna den.    
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards.png)
2. Instrumentpanelen öppnas.  Den innehåller många olika visualiseringspaneler.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)
3. Välj en av panelerna för att öppna den underliggande rapporten.  I det här exemplet ska vi välja ytdiagrammet (indikeras med rosa på föregående bild). Rapporten öppnas på den sida som innehåller ytdiagrammet.
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Om panelen hade skapats med hjälp av [Power BI:s frågor och svar](power-bi-q-and-a.md), skulle sidan Frågor och svar öppnats i stället.
   > 
   > 
4. Tillbaka på din flik **Datauppsättningar** har du flera alternativ för att utforska din datauppsättning.  Du kommer inte att kunna öppna den och se alla rader och kolumner (som du kan i Power BI Desktop eller Excel).  När någon delar ett innehållspaket med kollegor vill de vanligtvis dela med sig av vissa insikter och inte ge dem direkt åtkomst till specifika data. Men det betyder inte att du inte kan utforska datauppsättningen.  
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon2.png)
   
   * Ett sätt att utforska datauppsättningen är genom att skapa egna visualiseringar och rapporter från grunden.  Välj diagramikonen ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) för att öppna datauppsättningen i rapportredigeringsvyn.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)
   * Ett annat sätt att utforska datauppsättningen är att köra [Quick Insights](service-insights.md). Välj ellipserna (...) och välj **Hämta insikter**. När insikterna är klara väljer du **Visa insikter**.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="next-steps"></a>Nästa steg
[Grundläggande begrepp för Power BI](service-basic-concepts.md)

[Exempel för Power BI-tjänsten](sample-datasets.md)

[Datakällor för Power BI](service-get-data.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

