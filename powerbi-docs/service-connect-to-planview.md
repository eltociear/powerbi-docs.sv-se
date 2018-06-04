---
title: Anslut till Planview Enterprise med Power BI
description: Planview Enterprise för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4641fc0c36ad7fb64cc5da08ee8eda180f4ccc31
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34240499"
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Anslut till Planview Enterprise med Power BI
Med innehållspaketet Planview Enterprise för Power BI kan du visualisera dina resurs- och arbetshanteringsdata på ett helt nytt sätt direkt i Power BI. Använd autentiseringsuppgifterna för Planview Enterprise för att se utgifter i din investeringsportfölj interaktivt, förstå var du överstiger och understiger din budget och veta hur dina projekt överensstämmer med företagets strategiska prioriteringar. Du kan också utöka den ursprungliga instrumentpanelen och rapporterna för att skaffa dig de insikter som är viktigast för dig.

[Anslut till Planview Enterprise-innehållspaketet i Power BI](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>Du måste vara en Planview Enterprise-användare med funktionen Reporting Portal Viewer aktiverad på din roll om du vill importera dina Planview Enterprise-data till Power BI. Se ytterligare krav nedan.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-planview/get.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
    ![](media/service-connect-to-planview/services.png)
3. På Power BI-sidan väljer du **Planview Enterprise**och väljer sedan **Hämta**:  
    ![](media/service-connect-to-planview/planview.png)
4. Ange Planview Enterprise-URL:en i textrutan för den Planview Enterprise-server som du vill använda. I textrutan för Planview Enterprise-databas anger du namnet på din databas för Planview Enterprise och sedan Nästa.  
    ![](media/service-connect-to-planview/params.png)
5. I listan över autentiseringsmetoder, väljer du **Basic** om det inte redan är valt. Ange **Användarnamn** och **Lösenord** för ditt konto och välj **Logga In**.  
   ![](media/service-connect-to-planview/creds.png)
6. I den vänstra rutan, väljer du Planview Enterprise från listan över instrumentpaneler.  
     Power BI importerar Planview Enterprise-data till instrumentpanelen. Observera att data kan ta lite tid att läsa in.  
    ![](media/service-connect-to-planview/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="system-requirements"></a>Systemkrav
Du måste vara en Planview Enterprise-användare med funktionen Reporting Portal Viewer aktiverad på din roll om du vill importera dina Planview Enterprise-data till Power BI. Se ytterligare krav nedan.

Den här proceduren förutsätter att du redan har loggat in på startsidan för Microsoft Power BI med ett Power BI-konto. Om du inte har ett Power BI-konto, skapar du ett nytt kostnadsfritt Power BI-konto på Power BI-startsidan och klickar sedan på hämta data.

## <a name="next-steps"></a>Nästa steg:

[Kom igång med Power BI](service-get-started.md)

[Hämta data för Power BI](service-get-data.md)