---
title: Anslut till Projectplace med Power BI
description: "Projectplace för Power BI"
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
ms.openlocfilehash: 3327c193828dcdc28c2dd5b93c56615fdb367c70
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-projectplace-by-planview-with-power-bi"></a>Anslut till Projectplace av Planview med Power BI
Med innehållspaketet Projectplace av Planview, kan du visualisera data från dina samarbetsprojekt på helt nya sätt direkt i Power BI. Använd dina Projectplace-inloggningsuppgifter för att interaktivt visa viktig projektstatistik, ta reda på vilka dina mest aktiva och produktiva gruppmedlemmar är och identifiera kort och aktiviteter för projekt i ditt Projectplace-konto som är i risk. Du kan också utöka den ursprungliga instrumentpanelen och rapporterna för att skaffa dig de insikter som är viktigast för dig.

[Anslut till Projectplace-innehållspaketet i Power BI](https://app.powerbi.com/getdata/services/projectplace)

>[!NOTE]
>Du måste vara en Projectplace-användare om du vill importera dina Projectplace-data till Power BI. Se ytterligare krav nedan.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-projectplace/get.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
    ![](media/service-connect-to-projectplace/services.png)
3. På Power BI-sidan väljer du **Projectplace av Planview**och väljer sedan **hämta**:  
   
    ![](media/service-connect-to-projectplace/projectplace.png)
4. I textrutan för OData-flödets URL, anger du URL:en för det Projectplace OData-flöde som du vill använda, enligt följande bild:
   
    ![](media/service-connect-to-projectplace/params.png)
5. I listan över autentiseringsmetoder, väljer du **OAuth** om det inte redan är valt. Klicka på **logga in** och följ inloggningsflödet.  
   
   ![](media/service-connect-to-projectplace/creds.png)
6. I den vänstra rutan, väljer du **Projectplace** från listan över instrumentpaneler. Power BI importerar Projectplace-data till instrumentpanelen. Observera att data kan ta lite tid att läsa in.  
   
    Instrumentpanelen innehåller rutor som visar data från din Projectplace-databas. Följande bild visar ett exempel på en Projectplace-standardinstrumentpanel i Power BI.
   
    ![](media/service-connect-to-projectplace/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="system-requirements"></a>Systemkrav
Du måste vara en Projectplace-användare om du vill importera dina Projectplace-data till Power BI. Den här proceduren förutsätter att du redan har loggat in på startsidan för Microsoft Power BI med ett Power BI-konto. Om du inte har ett Power BI-konto, skapar du ett nytt kostnadsfritt Power BI-konto på Power BI-startsidan och klickar sedan på hämta data.

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

