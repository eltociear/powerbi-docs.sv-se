---
title: Bädda in en ny Power App i en Power BI-rapport
description: Bädda in en app som använder samma datakälla och kan filtreras som andra rapportobjekt
author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 03/17/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3be5f9efe3a6e18ba46f6990b09952d37b967e16
ms.sourcegitcommit: 646d2de454a2897dc52cbc02b7743aaa021bac04
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525946"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Självstudie: Bädda in ett visuellt objekt från Power Apps i en Power BI-rapport

I den här självstudien använder du visuella objekt i Power Apps för att skapa en ny app som är inbäddad i en exempelrapport i Power BI. Appen samverkar med andra visuella objekt i rapporten.

Om du inte har någon Power Apps-prenumeration kan du [skapa ett kostnadsfritt konto](https://web.powerapps.com/signup?redirect=marketing&email=) innan du börjar.

I de här självstudierna får du lära dig att
> [!div class="checklist"]
> * Lägga till ett visuellt Power Apps-objekt i en Power BI-rapport
> * Arbeta i Power Apps för att skapa en ny app som använder data från Power BI-rapporten
> * Visa och interagera med det visuella objektet från Power Apps i rapporten

## <a name="prerequisites"></a>Förutsättningar

* Någon av webbläsarna [Google Chrome](https://www.google.com/chrome/browser/) eller [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* En [Power BI-prenumeration](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi) med rapporten [Exempel på affärsmöjlighetsanalys](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample) installerad
* Kunskap om hur du [skapar appar i Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) och hur du [redigerar Power BI-rapporter](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)



## <a name="create-a-new-app"></a>Skapa en ny app
När du lägger till det visuella Power Apps-objektet i din rapport startas PowerApps Studio med en anslutning för realtidsdata mellan PowerApps och Power BI.

1. Öppna rapporten Exempel för affärsmöjlighetsanalys och välj sidan *Kommande affärsmöjligheter*. 


2. Flytta och ändra storlek på några av panelerna i rapporten så att det nya visuella objektet får plats.

    ![Flytta och ändra rapportpaneler](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. I fönstret Visualiseringar väljer du ikonen Power Apps och ändrar sedan storleken på det visuella objektet så att det passar det utrymme du har gjort.

    ![Visualiseringsfönstret med PowerApps-ikonen vald](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. I panelen **Fält** väljer du **Namn**, **Produktkod** och **Försäljningsfas**. 

    ![välj fält](media/power-bi-visualization-powerapp/power-bi-fields.jpg)

4. På det visuella objektet från Power Apps väljer du den Power Apps-miljö där du vill skapa appen och väljer sedan **Skapa ny**.

    ![Skapa ny app](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    I Power Apps Studio ser du att en grundläggande app har skapats, med ett *galleri* som visar något av de fält du valt i Power BI.

    ![Power Apps öppnas](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Ändra storlek på galleriet så att det bara upptar ena halvan av skärmen. 

6. Välj **Screen1** i det vänstra fönstret och ange ”LightBlue” för egenskapen **Fyllning** (så att den visas bättre i rapporten).

    ![färgpalett](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Gör lite utrymme för en etikettkontroll. 

    ![ändra galleriets dimensioner](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. Under **Galleri**infogar du en textetikettskontroll.

   ![etikettkontroll](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Dra etiketten till slutet av ditt visuella objekt. Ange egenskapen **Text** som `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Nu visas det totala antalet affärsmöjligheter i datauppsättningen.

    ![App med storleksförändrat galleri](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![Appen med etiketten uppdaterad](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Spara appen med namnet ”App för affärsmöjligheter”. 

    ![spara appen](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Visar appen i rapporten
Appen finns nu tillgänglig i Power BI-rapporten och samverkar med andra visuella objekt eftersom den delar samma datakälla.

![App i Power BI-rapport](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

Välj **Jan** i utsnittet i Power BI-rapporten. Då filtreras hela rapporten, inklusive data i appen.

![filtrerad rapport](media/power-bi-visualization-powerapp/power-bi-last.png)

Observera att antalet affärsmöjligheter i appen matchar antalet i det övre vänstra hörnet i rapporten. Du kan välja andra objekt i rapporten, så uppdateras data i appen.


## <a name="clean-up-resources"></a>Rensa resurser
Om du inte vill använda rapporten Exempel på affärsmöjlighetsanalys längre kan du ta bort instrumentpanelen, rapporter och datauppsättningen.


## <a name="next-steps"></a>Nästa steg
[Visuella frågor och svar](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[Självstudie: Bädda in ett visuellt objekt från Power Apps i en Power BI-rapport](https://docs.microsoft.com/powerapps/maker/canvas-apps/powerapps-custom-visual)