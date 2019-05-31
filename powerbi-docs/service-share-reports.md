---
title: Filtrera en rapport och dela den med kollegor – Power BI
description: Lär dig hur du filtrerar en Power BI-rapport och delar den med medarbetare i organisationen.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770699"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>Filtrera en Power BI-rapport och dela den med medarbetare
*Dela* är ett bra sätt att ge ett fåtal användare åtkomst till dina instrumentpaneler och rapporter. Hur gör du om du vill dela en filtrerad version av en rapport? Kanske en rapport som endast visar data för en viss ort, säljare eller år. Försök filtrera en rapport och dela den eller skapa en anpassad URL. Rapporten filtreras när mottagarna öppnar den första gången. De kan ta bort filtret genom att ändra URL:en. 

Power BI erbjuder också [flera andra sätt att samarbeta och distribuera dina rapporter på](service-how-to-collaborate-distribute-dashboards-reports.md). För att kunna dela måste både du och mottagaren ha en [Power BI Pro-licens](service-features-license-type.md), annars måste innehållet finnas i en [Premium-kapacitet](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Två sätt att filtrera en rapport

### <a name="set-a-filter"></a>Ange ett filter

Öppna rapporten i [redigeringsvyn](consumer/end-user-reading-view.md), använd filtret och spara rapporten.
   
I det här exemplet filtrerar vi [Exempel på detaljhandelsanalys](sample-tutorial-connect-to-the-samples.md) till att endast visa värden där **Område** är lika med **NC**.
   
![Rapportfilterfönstret](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Skapa ett filter i URL: en

Lägg till följande i slutet av rapportsidans URL:
   
?filter=*tabellnamn*/*fältnamn* eq *värde*
   
Fältet måste vara av typen tal, datum/tid eller sträng. Värdet för *tabellnamn* eller *fältnamn* kan inte innehålla blanksteg.
   
I vårt exempel är namnet på tabellen **Butik**, namnet på fältet är **Område** och värdet som vi vill filtrera på är **NC**:
   
?filter=Butik/Område eq 'NC'
   
![Filtrerad rapport-URL](media/service-share-reports/power-bi-filter-url3.png)
   
Webbläsaren lägger till specialtecken som motsvarar snedstreck, blanksteg och apostrofer, så resultatet blir:
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Finns i artikeln [filtrera en rapport med parametrar för frågesträngen i Webbadressen](service-url-filters.md) för mycket mer detaljerad information.

## <a name="share-the-filtered-report"></a>Dela en filtrerad rapport

1. När du [dela rapporten](service-share-dashboards.md), avmarkera de **skicka e-postavisering till mottagarna** markerar du kryssrutan.

    ![Dialogrutan Dela rapport](media/service-share-reports/power-bi-share-report-dialog.png)

4. Skicka en länk med filtret som du skapade tidigare.

## <a name="next-steps"></a>Nästa steg
* Har du feedback till oss? Gå till [Power BI Community-webbplatsen](https://community.powerbi.com/) med dina förslag.
* [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Dela en instrumentpanel](service-share-dashboards.md)
* Har du fler frågor? [Testa Power BI Community](http://community.powerbi.com/).

