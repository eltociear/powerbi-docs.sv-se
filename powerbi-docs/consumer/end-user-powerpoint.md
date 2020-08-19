---
title: Exportera hela rapporter till PowerPoint
description: Läs hur du exporterar en Power BI-rapport till PowerPoint.
author: mihart
ms.reviewer: mihart
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 07/01/2020
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 2cffd2b9913773e7f29d1afa960209ddeddd3583
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160428"
---
# <a name="export-reports-to-powerpoint"></a>Exportera rapporter till PowerPoint

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]


Med tjänsten Power BI (app.powerbi.com) kan du publicera din rapport till Microsoft PowerPoint och enkelt att skapa ett bildspel baserat på din Power BI-rapport. När du exporterar till PowerPoint, inträffar följande:

* Varje sida i Power BI-rapporten blir en enskild bild i PowerPoint.
* Varje sida i Power BI-rapporten exporteras som en högupplöst bild i PowerPoint.
* Du kan bevara filtren och utsnitten du har lagt till i rapporten.
* En länk skapas i PowerPoint som länkar till Power BI-rapporten.

Att få din **Power BI-rapport** exporterad till **PowerPoint** går snabbt. Följ stegen som beskrivs i nästa avsnitt.

Du kan också kopiera ett visuellt objekt i taget från Power BI-tjänsten och klistra in det i PowerPoint (eller något annat program som stöder inklistring). Välj ikonen för **Kopiera som bild** för att kopiera det visuella objektet till Urklipp. Öppna sedan PowerPoint och klistra in det visuella objektet. Mer information finns i [Kopiera visuella objekt som statiska bilder](../visuals/power-bi-visualization-copy-paste.md).

![Välj ikonen Kopiera som bild](media/end-user-powerpoint/power-bi-copy.png)

## <a name="export-your-power-bi-report-to-powerpoint"></a>Exportera en Power BI-rapport till PowerPoint
Välj en rapport i **Power BI-tjänsten** för att visa den på arbetsytan. Du kan även välja en rapport från **Start**, **Appar** eller någon annan container i navigeringsfönstret.

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

När den rapport som du vill exportera till PowerPoint visas på arbetsytan, väljer du **Arkiv** > **Exportera till PowerPoint** på menyraden.

![Välj Exportera från menyfältet](media/end-user-powerpoint/power-bi-export.png)

Ett popup-fönster visas där du kan välja **Aktuella värden** eller **Standardvärden**. Med **Aktuella värden** exporteras rapporten i det aktuella tillståndet, vilket innefattar alla aktiva ändringar som du gjort i utsnitts- och filtervärden.  De flesta användare väljer det här alternativet. Om du har bläddrat, så inkluderar inte **Aktuella värden** det visuella objektets bläddringstillstånd, utan exporterar i stället den översta datadelen. Du kan också välja **Standardvärden**, vilket exporterar rapporten i dess ursprungliga tillstånd, som den hade när *designern* delade den. Inga ändringar som du har gjort av originaltillståndet tas med.

![Välj vad som ska exporteras](media/end-user-powerpoint/power-bi-current-values.png)
 
Det finns också en kryssruta för att välja om dolda flikar i en rapport ska exporteras eller inte. Markera den här kryssrutan om du bara vill exportera rapportflikar som är synliga för dig i webbläsaren. Om du föredrar att få med alla dolda flikar i exporten lämnar du kryssrutan avmarkerad. Om kryssrutan är nedtonad finns inga dolda flikar i rapporten. Ett exempel på en dold flik är en knappbeskrivningsflik. [Anpassade knappbeskrivningar](../create-reports/desktop-tooltips.md) skapas av *rapportdesigners* och visas inte som rapportflikar för *konsumenter* i Power BI-tjänsten. 

Välj **Exportera** för att fortsätta när du har gjort dina val. Du ser en meddelandebanderoll i det övre högra hörnet i Power BI-tjänstens webbläsarfönster att rapporten exporteras till PowerPoint. 



![Meddelande om att export till PowerPoint pågår](media/end-user-powerpoint/power-bi-export-progress.png)

Det kan ta några minuter att exportera. Faktorer som kan påverka den tid som krävs är rapportens struktur och den aktuella belastningen på Power BI-tjänsten. Du kan fortsätta att arbeta i Power BI medan rapporten exporteras.

När det är klart, ändras meddelandebanderollen så att du vet att Power BI-tjänsten har slutfört exportåtgärden. Filen är sedan tillgänglig där din webbläsare visar hämtade filer. I följande bild, visas den som en nedladdningsbanderoll längst ned i webbläsarfönstret.

![webbläsarmeddelande, längst ned på skärmen](media/end-user-powerpoint/power-bi-browsers.png)

Det är allt. Du kan ladda ned filen, öppna den med PowerPoint och ändra eller förbättra den på samma sätt som andra PowerPoint-presentationer.

## <a name="open-the-powerpoint-file"></a>Öppna PowerPoint-filen
När du öppnar PowerPoint-filen som Power BI exporterade, hittar du en del häftiga och användbara element. Ta en titt på följande bild och kolla sedan de numrerade elementen som beskriver några av de smarta funktionerna. Sidor i PowerPoint skapas alltid i 9:16 standardstorlek, oavsett ursprungliga sidstorlekar eller dimensioner i Power BI-rapporten.

![PowerPoint öppnas](media/end-user-powerpoint/power-bi-powerpoint-numbered.png)

1. Den första sidan i presentationen innehåller namnet på rapporten och en länk så att du kan **visa i Power BI** den rapport som presentationen bygger på.
2. Du får också lite användbar information om rapporten. **Senaste datauppdatering** visar datum och tid som den senaste rapporten baseras på. **Laddades ned** visar datum och tid då Power BI-rapporten exporterades till en PowerPoint-fil. Tiden för**Hämtad** motsvarar exportens tidpunkt enligt din dators tidszon.


3. Varje rapportsida är en separat bild som visas i navigeringsfönstret. 
4. Din publicerade rapport återges på det språk som dina Power BI-inställningar anger, eller i annat fall på det språk som anges i webbläsarens språkinställningar. Om du vill se eller ange din språkinställning, klicka på kugghjulsikonen ![kugghjulsikon](media/end-user-powerpoint/power-bi-settings-icon.png) > **Inställningar** > **Allmänt** > **Språk**. Mer information finns i [Språk och länder eller regioner som stöds för Power BI](../fundamentals/supported-languages-countries-regions.md).


När du visar en specifik bild, ser du att varje rapportsida är en oberoende bild. Du kan inte rulla i PowerPoint eftersom varje bild är en statisk bild.

![Skärmbild som visar varje visuella objekt som en separat bild](media/end-user-powerpoint/power-bi-images.png)

Det är nu upp till dig vad du vill göra med PowerPoint-presentationen eller någon av de högupplösta bilderna.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
Det finns några överväganden och begränsningar som du bör tänka på när du arbetar med funktionen **exportera till PowerPoint**.
 

* Om du inte ser alternativet **Exportera** kontrollerar du att du har aktiverat ”Nytt utseende” och att du visar en rapport (inte en instrumentpanel).

    ![Skärmbild av växling till det nya utseendet](media/end-user-powerpoint/power-bi-new-look.png)

* [URL-filter](../collaborate-share/service-url-filters.md) respekteras för närvarande inte när du väljer **Aktuella värden** för exporten.

* Om rapporten använder ett anpassat teckensnitt när du exporterar till PowerPoint, så ersätts det teckensnittet med ett standardteckensnitt.

* Följande visuella typer stöds inte och kommer inte att exporteras till PowerPoint:
   - [Anpassade visuella objekt som inte har certifierats](../developer/visuals/power-bi-custom-visuals-certified.md)) stöds inte. 
   - Det [visuella ESRI ArcGIS-objektet](../visuals/power-bi-visualizations-arcgis.md) stöds inte
   - Visuella R- och Python-objekt stöds inte.
   - Bakgrundsbilder beskärs med diagrammets markeringsområdet. Vi rekommenderar att du tar bort bakgrundsbilder innan du exporterar till PowerPoint.

* Vissa rapporter kan inte exporteras. Dessa omfattar:
    - Om du delar en instrumentpanel med någon utanför organisationen och därmed, en användare som inte är i din Power BI-klient, kommer den användaren inte att kunna exportera delade instrumentpanelers associerade rapporter till PowerPoint. Så om du är aaron@contoso.com kan du dela med david@cohowinery.com. Men david@cohowinery.com kan inte exportera de associerade rapporterna till PowerPoint.
    - Rapporter med fler än 50 rapportsidor. Endast de första 50 sidorna exporteras.
    - Rapporter som exporteras till äldre versioner av PowerPoint.
    - Rapporter som tar längre tid än en timma att bearbeta. 
    - Rapportsidor som det tar längre tid än 6 minuter att läsa in. 

* Om menyobjektet **exportera till PowerPoint** inte finns i Power BI-tjänsten, beror det förmodligen på att din klientadministratör har inaktiverat funktionen. Kontakta din klientadministratör för mer information.
* Power BI-tjänsten använder det språk du har i din Power BI-språkinställning som språk för PowerPoint-exporten. Om du vill se eller ange din språkinställning, klicka på kugghjulsikonen ![kugghjulsikon](media/end-user-powerpoint/power-bi-settings-icon.png) > **Inställningar** > **Allmänt** > **Språk**.



## <a name="next-steps"></a>Nästa steg
[Kopiera visuella objekt som statiska bilder](../visuals/power-bi-visualization-copy-paste.md)    
[Skriva ut en rapport](end-user-print.md)
