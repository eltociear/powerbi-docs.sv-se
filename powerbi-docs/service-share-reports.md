---
title: Filtrera och dela en Power BI-rapport
description: Lär dig hur du filtrerar en Power BI-rapport och delar den med medarbetare i organisationen.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 16041ebc9ba293ab166178e008b12277d94e89c3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76894917"
---
# <a name="filter-and-share-a-power-bi-report"></a>Filtrera och dela en Power BI-rapport
*Dela* är ett bra sätt att ge ett fåtal användare åtkomst till dina instrumentpaneler och rapporter. Hur gör du om du vill dela en filtrerad version av en rapport? Kanske du vill att rapporten ska visa endast data för en viss ort, säljare eller år. Den här artikeln förklarar hur du filtrerar en rapport och delar den filtrerade versionen av rapporten. Ett annat sätt att dela en filtrerad rapport är att [lägga till frågeparametrar till rapportens URL](service-url-filters.md). I båda fallen filtreras rapporten när mottagarna öppnar den för första gången. De kan rensa filtervalen i rapporten.

![Filtrerad rapport](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI erbjuder också [andra sätt att samarbeta och distribuera dina rapporter på](service-how-to-collaborate-distribute-dashboards-reports.md). För att kunna dela måste både du och mottagaren ha en [Power BI Pro-licens](service-features-license-type.md), annars måste innehållet finnas i en [Premium-kapacitet](service-premium-what-is.md). 

## <a name="follow-along-with-sample-data"></a>Följ med via exempeldata

Den här artikeln använder exempelappen Marknadsföring och försäljning. Vill du testa? 

1. Installera exempelappen [Marknadsföring och försäljning](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Välj appen och välj **Utforska app**.

   ![Utforska exempeldata](media/service-share-reports/power-bi-sample-explore-data.png)

3. Välj pennikonen för att öppna arbetsytan som du installerade med appen.

    ![Appens redigeringspenna](media/service-share-reports/power-bi-edit-pencil-app.png)

4. I innehållslistan i arbetsytan väljer du **Rapporter**och väljer sedan rapporten **PBIX-filen Exempel på försäljning och marknadsföring**.

    ![Öppna exempelrapport](media/service-share-reports/power-bi-open-sample-report.png)

    Nu är du redo att börja testa.

## <a name="set-a-filter-in-the-report"></a>Ställ in ett filter i rapporten

Lägga till ett rapport i [redigeringsvyn](consumer/end-user-reading-view.md) och lägga till ett filter.

I det här exemplet ska vi filtrera kategorin YTD i exempelappen Marknadsföring och försäljning för att endast visa värden där **Region** är lika med **Central**. 
 
![Rapportfilterfönstret](media/service-share-reports/power-bi-share-report-filter.png)

Spara rapporten.

## <a name="share-the-filtered-report"></a>Dela en filtrerad rapport

1. Välj **Dela**.

   ![Välj Dela](media/service-share-reports/power-bi-share.png)

2. Rensa **Skicka e-postmeddelande till mottagare**, så att du kan skicka en filtrerad länk i stället. Välj **Dela rapport med aktuella filter och utsnitt** och välj **Dela**.

    ![Dela rapport med filter](media/service-share-reports/power-bi-share-with-filters.png)

4. Välj **Dela** igen.

   ![Välj Dela](media/service-share-reports/power-bi-share.png)

5. Välj fliken **Åtkomst** och välj sedan **Hantera delade rapportvyer**.

    ![Hantera delade rapportvyer](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Högerklicka på den URL som du vill använda och välj **Kopiera länk**.

    ![Kopiera filtrerad länk](media/service-share-reports/power-bi-copy-filtered-link.png)

7. När du delar den här länken visas den filtrerade rapporten för mottagarna. 


## <a name="next-steps"></a>Nästa steg
* [Olika sätt att dela ditt arbete i Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Dela en instrumentpanel](service-share-dashboards.md)
* Fler frågor? [Testa Power BI Community](https://community.powerbi.com/).
* Har du feedback till oss? Gå till [Power BI Community-webbplatsen](https://community.powerbi.com/) med dina förslag.

