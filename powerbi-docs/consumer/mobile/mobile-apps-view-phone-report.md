---
title: Visa Power BI-rapporter som är optimerade för din telefon
description: Läs mer om att interagera med rapportsidor som har optimerats för visning i Power BI-appar.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: painbar
ms.openlocfilehash: 380057c2c65db3ea659adc39d692d8955201483b
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565133"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Visa Power BI-rapporter som är optimerade för din telefon

Gäller för:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android-telefon](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone-telefoner |Android-telefoner |

När du visar en Power BI-rapport på din telefon kontrollerar Power BI om rapporten har optimerats för telefoner. Om så är fallet öppnar Power BI automatiskt den optimerade rapporten i stående vy.

![Rapport i stående läge](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Om det inte finns någon telefonoptimerad rapport kommer rapporten öppnas i ett icke-optimerat liggande läge. Rapporten öppnas i icke-optimerat läge med den ursprungliga rapportlayouten om du vrider din telefon åt sidan, även om den ursprungligen är telefonoptimerad. Om du enbart optimerar vissa sidor kommer läsarna att se ett meddelande i stående vy som visar att rapporten är tillgänglig i liggande vy.

![Rapportsidan är inte optimerad](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Alla andra funktioner i Power BI-rapporter fungerar fortfarande i telefon-optimerade rapporter. Läs mer om funktioner i:

* [Rapporter på iPhone](mobile-reports-in-the-mobile-apps.md). 
* [Rapporter på Android-telefoner](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrera rapportsidan på en telefon
Om en telefonoptimerad rapport har filter definierade, kan du använda dessa filter när du visar rapporten på en telefon. Rapporten öppnas på din telefon filtrerad enligt de värden som filtreras i rapporten på webben. Ett meddelande om att det finns aktiva filter på sidan visas. Du kan ändra filtren på din telefon.

1. Tryck på filterikonen ![Telefonfilterikon](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) längst ned på sidan.

2. Använda grundläggande eller avancerad filtrering för att se resultatet som du är intresserad av.
   
    ![Avancerat filter för rapport på telefon](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.png)

## <a name="cross-highlight-visuals"></a>Korsmarkera visuella objekt
Korsmarkering av visuella objekt i stående vy fungerar på samma sätt som i Power BI-tjänsten och på telefoner i liggande vy: När du väljer data i ett visuellt objekt markeras relaterade data i övriga visuella objekt på samma sida.

Läs mer om [filtrering och markering i Power BI](../../create-reports/power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Välj visuella objekt
I rapporter på telefonen markeras det visuella objektet när du väljer det, vilket neutraliserar gester på arbetsytan.

Du kan bläddra i det visuella objektet när det är markerat. Om du vill avmarkera ett visuellt objekt är det bara att trycka var som helst utanför det.

## <a name="open-visuals-in-focus-mode"></a>Öppna visuella objekt i fokusläge
Telefonrapporter erbjuder även ett fokusläge: Du får en större vy av ett enda visuellt objekt och kan enklare utforskar det.

* Knacka på ellipsen i en telefonrapport ( **...** ) i det övre högra hörnet i ett visuellt objekt > **Expandera till fokusläge**.
  
    ![Expandera till fokusläge](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Det du gör i fokusläget överförs till rapportarbetsytan och vice versa. Om du till exempel markerar ett värde i ett visuellt objekt och sedan går tillbaka till hela rapporten filtreras rapporten till det värde som du markerade i det visuella objektet.

Vissa åtgärder kan endast utföras i fokusläge på grund av skärmens storlek:

* **Ändra detaljnivån** i informationen som visas i ett visuellt objekt. Läs mer om att ändra detaljnivån [nedåt och uppåt](mobile-apps-view-phone-report.md#drill-down-in-a-visual) i en telefonrapport nedan.
* **Sortera** värdena i det visuella objektet.
* **Återställa**: Rensa de utforskningssteg du har genomfört för ett visuellt objekt och återgå till de definitioner som gällde när rapporten skapades.
  
    Tryck på ellipsen ( **...** ) > **Återställ** för att rensa all utforskningsaktivitet från ett visuellt objekt.
  
    ![Återställ](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Återställ är tillgängligt på rapportnivå, där utforskning rensas från alla visuella objekt, och på nivå för visuellt objekt, där utforskning rensas från det markerade visuella objektet.   

## <a name="drill-down-in-a-visual"></a>Öka detaljnivån i ett visuellt objekt
Om hierarkinivåerna har definierats i ett visuellt objekt kan du öka detaljnivån för informationen i ett visuellt objekt och sedan återgå. Du kan[ öka detaljnivån](../end-user-drill.md) i antingen Power BI-tjänsten eller Power BI Desktop.

Det finns några typer av detaljnivåökning:

### <a name="drill-down-on-a-value"></a>Öka detaljnivå för ett värde
1. Lång tryckning (tryck och håll) på en datapunkt i ett visuellt objekt.
2. En knappbeskrivning visas, och om hierarkin är definierad visar knappbeskrivningens sidfot pil för att öka eller minska detaljnivån.
3. Tryck på nedåtpilen för att öka detaljnivån

    ![Tryck på öka detaljnivån](media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Tryck på uppåtpilen för att minska detaljnivån.

### <a name="drill-to-next-level"></a>Ändra till nästa detaljnivå
1. Knacka på ellipsen i en telefonrapport ( **...** ) i det övre högra hörnet > **Expandera till fokusläge**.
   
    ![Expandera till fokusläge](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    I det här exemplet visar staplarna värden för delstater.
2. Tryck på utforskningsikonen ![Utforskningsikonen](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) nere till vänster.
   
    ![Utforskningsläge](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Tryck på **Visa nästa nivå** eller **Expandera till nästa nivå**.
   
    ![Expandera till nästa nivå](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Nu visar staplarna värden för städer.
   
    ![Utökade nivåer](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Om du trycker på pilen i det övre vänstra hörnet återgår du till telefonrapporten med värden som fortfarande expanderas för den lägre nivån.
   
    ![Fortfarande expanderad till den lägre nivån](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Om du vill gå tillbaka upp till den ursprungliga nivån, tryck på ellipsen ( **...** ) igen > **Återställ**.
   
    ![Återställ](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Detaljgranska från ett värde
Detaljgranska ansluter värden på en rapportsida till andra rapportsidor. När du detaljgranskar från en datapunkt till en annan rapportsida används datapunktsvärdena för att filtrera den detaljgranskade sidan, eller så kommer den att vara i kontexten för valda data.
Rapportförfattarna kan [definiera detaljgranskning](https://docs.microsoft.com/power-bi/desktop-drillthrough) när de skapar rapporten.

1. Lång tryckning (tryck och håll) på en datapunkt i ett visuellt objekt.
2. En knappbeskrivning visas, och om detaljgranskning är definierad visar knappbeskrivningens sidfot pil för detaljgranskning.
3. Tryck på pilen för att detaljgranska

    ![Tryck på detaljgranska](media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Välj vilken rapportsida du vill detaljgranska

    ![Välj rapportsida](media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Använd knappen Tillbaka i apphuvudet för att gå tillbaka till den sida som du började från.


## <a name="next-steps"></a>Nästa steg
* [Skapa rapporter som är optimerade för Power BI-mobilapparna](../../create-reports/desktop-create-phone-report.md)
* [Skapa en telefonvy av en instrumentpanel i Power BI](../../create-reports/service-create-dashboard-mobile-phone-view.md)
* [Skapa dynamiska visuella objekt som optimerats för alla storlekar](../../visuals/power-bi-report-visualizations.md)
* Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
