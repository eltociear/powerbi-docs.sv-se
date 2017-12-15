---
title: Ansluta till MailChimp med Power BI
description: "MailChimp för Power BI"
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 2781dc7088824cb00f5dcd174fbfc3677c0f13a6
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-mailchimp-with-power-bi"></a>Ansluta till MailChimp med Power BI
Power BI-innehållspaket hämtar data från ditt MailChimp-konto och genererar en instrumentpanel, en uppsättning rapporter och en datauppsättning för att utforska dina data. Dra in analyser för att skapa [MailChimp-instrumentpaneler](https://powerbi.microsoft.com/integrations/mailchimp) och snabbt identifiera trender för dina kampanjer, rapporter och enskilda prenumeranter. Data har ställts in till att uppdateras varje dag för att säkerställa att de data som du övervakar är uppdaterade.

Anslut till [MailChimp-innehållspaket](https://app.powerbi.com/getdata/services/mailchimp) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-mailchimp/pbi_getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-mailchimp/pbi_getservices.png)
3. Välj **MailChimp** \> **Hämta**.
   
   ![](media/service-connect-to-mailchimp/mailchimp.png)
4. Som Autentiseringsmetod väljer du **oAuth2** \> **Logga in**.
   
    När du uppmanas till det anger du autentiseringsuppgifter för MailChimp och följer autentiseringsprocessen.
   
    Första gången du ansluter uppmanas du att ge Power BI skrivskyddad åtkomst till ditt konto. Välj **Tillåt** för att starta importen, vilket kan ta några minuter beroende på mängden data i ditt konto.
   
    ![](media/service-connect-to-mailchimp/allow.png)
5. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Detta är standardinstrumentpanelen som skapas i Power BI för att visa dina data. Du kan ändra den här instrumentpanelen för att visa dina data på det sätt som du vill.
   
   ![](media/service-connect-to-mailchimp/pbi_mailchimpnewdash.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

