---
title: Dela en filtrerad Power BI-rapport med medarbetare
description: Lär dig hur du filtrerar en Power BI-rapport och delar den med medarbetare i organisationen.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 05bdb9ccca7715b74cb18462f215f7d1bf640526
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279778"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>Dela en filtrerad Power BI-rapport med dina medarbetare
*Dela* är ett bra sätt att ge ett fåtal användare åtkomst till dina instrumentpaneler och rapporter. Power BI erbjuder också [flera andra sätt att samarbeta och distribuera dina rapporter på](service-how-to-collaborate-distribute-dashboards-reports.md).

För att kunna dela måste både du och mottagaren ha en [Power BI Pro-licens](service-features-license-type.md), annars måste innehållet finnas i en [Premium-kapacitet](service-premium.md). 

Du kan dela en rapport med kollegor i samma e-post-domän som du, från de flesta platser i Power BI-tjänsten: dina favoriter, senaste, delad med (om ägaren tillåter det), min arbetsyta eller andra arbetsytor. När du delar en rapport kan medarbetare som du delar med se den och interagera med den, men de kan inte redigera den. De ser samma data som visas i rapporten såvida inte [Säkerhet på radnivå (RLS)](service-admin-rls.md) tillämpas. 

Hur gör du om du vill dela en filtrerad version av en rapport? Kanske en rapport som endast visar data för en viss ort, säljare eller år. Prova att skapa en anpassad URL. Rapporten filtreras när mottagarna öppnar den första gången. De kan ta bort filtret genom att ändra URL:en.

## <a name="filter-and-share-a-report"></a>Filtrera och dela en rapport

1. Öppna rapporten i [redigeringsvyn](consumer/end-user-reading-view.md), använd filtret och spara rapporten.
   
   I det här exemplet filtrerar vi [Exempel på detaljhandelsanalys](sample-tutorial-connect-to-the-samples.md) till att endast visa värden där **Område** är lika med **NC**.
   
   ![Rapportfilterfönstret](media/service-share-reports/power-bi-filter-report2.png)
2. Lägg till följande i slutet av rapportsidans URL:
   
   ?filter=*tabellnamn*/*fältnamn* eq *värde*
   
    Fältet måste vara av typen **sträng**. Värdet för *tabellnamn* eller *fältnamn* kan inte innehålla blanksteg.
   
   I vårt exempel är namnet på tabellen **Butik**, namnet på fältet är **Område** och värdet som vi vill filtrera på är **NC**:
   
    ?filter=Butik/Område eq 'NC'
   
   ![Filtrerad rapport-URL](media/service-share-reports/power-bi-filter-url3.png)
   
   Webbläsaren lägger till specialtecken som motsvarar snedstreck, blanksteg och apostrofer, så resultatet blir:
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. [Dela rapporten](service-share-dashboards.md) men avmarkera kryssrutan **Skicka e-postmeddelande till mottagare**. 

    ![Dialogrutan Dela rapport](media/service-share-reports/power-bi-share-report-dialog.png)

4. Skicka en länk med filtret som du skapade tidigare.

## <a name="next-steps"></a>Nästa steg
* Har du feedback till oss? Gå till [Power BI Community-webbplatsen](https://community.powerbi.com/) med dina förslag.
* [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Dela en instrumentpanel](service-share-dashboards.md)
* Har du fler frågor? [Testa Power BI Community](http://community.powerbi.com/).

