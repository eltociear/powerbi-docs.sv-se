---
title: Öppna en rapport i Läsvyn eller Redigeringsvyn i Power BI-tjänsten
description: Öppna en Power BI-rapport i Läsvyn eller Redigeringsvyn
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/01/2018
ms.author: mihart
ms.openlocfilehash: 17921d1fe28a1b4c0640748123efe4b70982b18d
ms.sourcegitcommit: ae4d771b883b654358a6a94dd784ea9bdf3d3aa3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/28/2018
---
# <a name="open-a-report-in-power-bi-service-apppowerbicom"></a>Öppna en rapport i Power BI-tjänsten (app.powerbi.com)
Rapporter finns tillgängliga i Power BI-tjänsten, Power BI Desktop, Power BI-mobil och Power BI Embedded. Den här artikeln behandlar att öppna rapporter i ***Power BI-tjänsten***.

I Power BI-tjänsten finns det två lägen för att visa och interagera med rapporter: [Läsvyn och Redigeringsvyn](service-reading-view-and-editing-view.md). Läsvyn är tillgänglig för alla användare och har speciellt skapats för rapport*konsumenter*, medan Redigeringsvyn endast finns tillgänglig för rapport*skapare* och -ägare. 

## <a name="open-a-report-from-a-workspace-via-the-reports-content-view-list"></a>Öppna en rapport från en arbetsyta (via innehållsvylistan **Rapporter**)

1. Starta i en arbetsyta och välj fliken **rapporter** för att visa alla rapporter på den arbetsytan.  
   
   ![Rapportfliken på en arbetsyta](media/service-report-open/power-bi-open-report.png)
2. Välj rapportnamnet för att öppna den i Läsvy.  
   
    ![rapport i Läsvyn](media/service-report-open/power-bi-reading-view.png)
3. Det finns [så mycket du kan göra i läsvy](service-reading-view-and-editing-view.md).  Den här exempelrapporten har flera sidor så börja utforska genom att välja varje flik längst ned i rapportarbetsytan. 

## <a name="open-a-report-from-a-dashboard"></a>Öppna en rapport från en instrumentpanel
Det finns många andra sätt att öppna en rapport. Du kan till exempel starta på en instrumentpanel och välj en panel som skapades från en rapport.  Om du väljer panelen så öppnas rapporten i läsvy. Om du vill följa med, [öppna exempelinstrumentpanelen Försäljning och marknadsföring](sample-datasets.md).

1. Öppna en instrumentpanel och välj en panel.

   Om du väljer en panel som [skapades med Frågor och svar](service-dashboard-pin-tile-from-q-and-a.md), visas Frågor och svar-skärmen. Om du väljer en panel som [skapades med instrumentpanelens **Lägg till panel**-widget](service-dashboard-add-widget.md), öppnar du guiden för att redigera den widgeten.  

2.  I det här exemplet har vi valt kolumndiagramspanelen Totalt antal enheter hittills i år...

    ![instrumentpanel med vald panel](media/service-report-open/power-bi-dashboard.png)

3.  Den associerade rapporten öppnas i Läsvy. Du märker att vi är på sidan kategori hittills i år. Det är den rapportsidan som innehåller kolumndiagrammet som vi valt från instrumentpanelen.

    ![öppen rapport i Läsvyn](media/service-report-open/power-bi-report.png)

4. Stanna i Läsvy eller välj **Redigera rapporten** för att öppna rapporten i Redigeringsvyn. Kom ihåg att endast de som har redigeringsbehörighet för rapporten kan öppna den i Redigeringsvyn.

    ![Rapportredigeraren med ikonen Redigera rapport](media/service-report-open/power-bi-edit-report.png)

## <a name="create-a-brand-new-report-from-a-dataset"></a>Skapa en ny rapport från en datauppsättning
Ett annat sätt att öppna en rapport är från en datauppsättning. När du startar från en datauppsättning, kommer rapportens arbetsyta att vara tom så den här metoden rekommenderas för rapport*skapare* som vill skapa en ny rapport utifrån en datauppsättning som de äger. Precis som i exemplet ovan, kan du följa med genom att hämta [exempelappen Försäljning och marknadsföring](sample-datasets.md).

1. Starta i arbetsytan som innehåller den datauppsättning som du vill använda som grund för en rapport.

   ![vänster navigeringsfält visar apparbetsytor](media/service-report-open/power-bi-workspace.png)

2. Välj fliken **Datauppsättningar** för att visa listan över alla datauppsättningar i den arbetsytan. Det här kallas innehållsvylistan **Datauppsättningar**.
   
   ![lista över datauppsättningar](media/service-report-open/power-bi-dataset.png)

1. Hitta datauppsättningen och välj ikonen **Skapa rapport** för att öppna datauppsättningen i Redigeringsvyn. Om du inte har redigeringsbehörighet för en datauppsättning, kommer du inte att kunna öppna den. 
   
    ![datauppsättning med ikonen Skapa rapport](media/service-report-open/power-bi-create-report.png)

3. Datauppsättningen öppnas i rapportredigeraren. Datafälten visas till höger och väntar bara på att du ska börja utforska och skapa visualiseringar. 

   ![rapportarbetsytan](media/service-report-open/power-bi-blank-canvas.png)

##  <a name="still-more-ways-to-open-a-report"></a>Ännu fler sätt att öppna en rapport
När du börjar bli mer bekväm med att använda Power BI-tjänsten, kommer du att lista ut de arbetsflöden som fungerar bäst för dig. Några andra sätt att komma åt rapporter:
- Från det vänstra navigeringsfönstret med **Favoriter**, **Senaste**, **Appar** och **Delas med mig**. 
- Med [Visa relaterade](service-related-content.md)
- I ett e-postmeddelande när någon [delar med dig](service-share-reports.md) eller [ställer in en avisering](service-set-data-alerts.md).    
- Från ditt [Meddelandecenter](service-notification-center.md)    
- och mycket mer

## <a name="next-steps"></a>Nästa steg
Läs mer om [rapporter i Power BI](service-reports.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)  

