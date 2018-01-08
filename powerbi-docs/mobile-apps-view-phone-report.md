---
title: "Visa Power BI-rapporter som är optimerade för din telefon"
description: "Läs mer om att interagera med rapportsidor som har optimerats för visning i Power BI-appar."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: maggies
ms.openlocfilehash: f3e02da2c0e793f3eb334c39852f5cd23534ad3f
ms.sourcegitcommit: 54da95f184dd0f7bb59bb0bc8775a1d93129b195
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/08/2017
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Visa Power BI-rapporter som är optimerade för din telefon
När du skapar en Power BI-rapport i Power BI Desktop kan du också skapa en version av [rapporten som optimeras för visning i Power BI-appen på en telefon](desktop-create-phone-report.md).

När du öppnar en Power BI-rapport på en telefon identifierar Power BI om rapporten har optimerats för telefon och öppnar automatiskt den optimerade rapporten i stående läge.

![Rapport i stående läge](media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Om det inte finns någon telefonoptimerad rapport kommer rapporten öppnas i ett icke-optimerat liggande läge. Rapporten öppnas i icke-optimerat läge med den ursprungliga rapportlayouten om du vrider din telefon åt sidan, även om den ursprungligen är telefonoptimerad. Om du enbart optimerar vissa sidor kommer läsarna att se ett meddelande i stående vy som visar att rapporten är tillgänglig i liggande vy.

![Rapportsidan är inte optimerad](media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Alla andra funktioner i Power BI-rapporter fungerar fortfarande i telefon-optimerade rapporter. Läs mer om funktioner i:

* [Rapporter på iPhone](mobile-reports-in-the-mobile-apps.md). 
* [Rapporter på Android-telefoner](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrera rapportsidan på en telefon
Om en telefonoptimerad rapport har filter definierade, kan du använda dessa filter när du visar rapporten på en telefon. 

1. Tryck på filterikonen ![Telefonfilterikon](media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) längst ned på sidan. 
2. Använda grundläggande eller avancerad filtrering för att se resultatet som du är intresserad av.
   
    ![Avancerat filter för rapport på telefon](media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Korsmarkera visuella objekt
Korsmarkering i telefonrapporter fungerar på samma sätt som i Power BI-tjänsten och rapporter på telefonen i liggande läge: När du väljer data i ett visuellt objekt markeras relaterade data i andra visuella objekt på sidan.

Läs mer om [filtrering och markering i Power BI](power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Välj visuella objekt
I rapporter på telefonen markeras det visuella objektet när du väljer det, vilket neutraliserar gester på arbetsytan.

Du kan bläddra i det visuella objektet när det är markerat. Om du vill avmarkera ett visuellt objekt är det bara att trycka var som helst utanför det.

## <a name="open-visuals-in-focus-mode"></a>Öppna visuella objekt i fokusläge
Telefonrapporter har dessutom ett fokusläge så att du kan få en större vy över ett specifikt visuellt objekt och utforska det och rapporten.

* Knacka på ellipsen i en telefonrapport (**...** ) i det övre högra hörnet i ett visuellt objekt > **Expandera till fokusläge**.
  
    ![Expandera till fokusläge](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Vad du gör i fokusläget överförs till rapportarbetsytan och vice versa och ger en sömlös utforskningsupplevelse. Om du markerar ett värde i ett visuellt objekt och sedan går tillbaka till hela rapporten kommer rapporten att filtreras till det värde som du markerade i det visuella objektet.

Vissa åtgärder kan endast utföras i fokusläge på grund av skärmens storlek:

* **Ändra detaljnivån** i informationen som visas i ett visuellt objekt. Läs mer om att ändra detaljnivån [nedåt och uppåt](mobile-apps-view-phone-report.md#drill-down-in-a-visual) i en telefonrapport nedan.
* **Sortera** värdena i det visuella objektet.
* **Återställa**: Rensa de utforskningssteg du har tagit på ett visuellt objekt och återgå till de definitioner som gällde när rapporten skapades.
  
    Tryck på ellipsen (**...**) > **Återställ** för att rensa all utforskningsaktivitet från ett visuellt objekt.
  
    ![Återställ](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Återställ är tillgängligt på rapportnivå, för alla visuella objekt eller för det aktuella visuella objektet, vilket tar bort all utforskning från det valda visuella objektet.   

## <a name="drill-down-in-a-visual"></a>Öka detaljnivån i ett visuellt objekt
Om hierarkinivåerna har definierats i ett visuellt objekt kan du öka detaljnivån för informationen i ett visuellt objekt och sedan återgå. Du kan[ öka detaljnivån](power-bi-visualization-drill-down.md) i antingen Power BI-tjänsten eller Power BI Desktop. Gå nedåt fungerar bara i telefonoptimerade Power BI-rapporter när du visar dem på en telefon. 

1. Knacka på ellipsen i en telefonrapport (**...** ) i det övre högra hörnet > **Expandera till fokusläge**.
   
    ![Expandera till fokusläge](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    I det här exemplet visar staplarna värden för delstater.
2. Tryck på utforskningsikonen ![Utforskningsikonen](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) i det nedre vänstra hörnet.
   
    ![Utforskningsläge](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Tryck på **Visa nästa nivå** eller **Expandera till nästa nivå**.
   
    ![Expandera till nästa nivå](media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Nu visar staplarna värden för städer.
   
    ![Utökade nivåer](media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Om du trycker på pilen i det övre vänstra hörnet återgår du till telefonrapporten med värden som fortfarande expanderas för den lägre nivån.
   
    ![Fortfarande expanderad till den lägre nivån](media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Om du vill gå tillbaka upp till den ursprungliga nivån, tryck på ellipsen (**...** ) igen > **Återställ**.
   
    ![Återställ](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="next-steps"></a>Nästa steg
* [Skapa rapporter som är optimerade för Power BI-telefonappar](desktop-create-phone-report.md)
* [Skapa en telefonvy av en instrumentpanel i Power BI](service-create-dashboard-mobile-phone-view.md)
* [Skapa dynamiska visuella objekt som optimerats för alla storlekar](desktop-create-responsive-visuals.md)
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

