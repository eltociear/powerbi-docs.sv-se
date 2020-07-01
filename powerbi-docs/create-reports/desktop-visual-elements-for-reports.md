---
title: Använd visuella element för att förbättra Power BI-rapporter
description: Använd visuella element, till exempel skrivbordsunderlägg och visuella rubriker för att förbättra rapporter
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 14ba601460a5ed025e24ff34539cf2f9bff93507
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240364"
---
# <a name="use-visual-elements-to-enhance-power-bi-reports"></a>Använd visuella element för att förbättra Power BI-rapporter

Med **Power BI Desktop** kan du använda visuella element, till exempel skrivbordsunderlägg och förbättrade visuella rubriker för visuella objekt för att förbättra utseendet på dina rapporter.

![Lägg till skrivbordsunderlägg och små visuella rubriker för att förbättra rapporter](media/desktop-visual-elements-for-reports/visual-elements-for-reports_01.png)

Från och med juli 2018-versionen av **Power BI Desktop** kan du lägga till förbättringar för att använda i dina rapporter och göra dina analyser och rapporter ännu mer tilltalande än innan. De förbättringar som beskrivs i den här artikeln inkluderar följande: 

* Använd **skrivbordsunderlägg** i dina rapporter så att din bakgrund kan förbättra eller förstärka de element i din berättelse som du vill förmedla med dina data
* Använd förbättrade **visuella rubriker** för enskilda visualiseringar för att skapa perfekt justerade visuella objekt på rapportarbetsytan. 

Följande avsnitt beskriver hur du använder dessa förbättringar och hur du tillämpar dem på dina rapporter.

## <a name="using-wallpaper-in-power-bi-reports"></a>Använd skrivbordsunderlägg i Power BI-rapporter

Du kan formatera det grå området utanför din rapportsida med **skrivbordsunderlägg**. Följande bild har en pil som klargör var skrivbordsunderläggsområdet gäller. 

![Skrivbordsunderlägget täcker det grå området runt en rapport](media/desktop-visual-elements-for-reports/visual-elements-for-reports_02.png)

Du kan antingen ställa in skrivbordsunderlägg per rapportsida eller ha samma skrivbordsunderlägg för varje sida i din rapport. Om du vill ange skrivbordsunderlägg trycker eller klickar du på ikonen **formatering** när inget visuellt objekt har valts i din rapport och **skrivbordsunderlägg** visas i fönstret.

![Skrivbordsunderläggsområdet i formateringsfönstret](media/desktop-visual-elements-for-reports/visual-elements-for-reports_03.png)

Du kan välja en färg som ska användas som **skrivbordsunderlägg** genom att välja listrutan **Färg** eller så kan du välja knappen **Lägg till bild** för att välja en bild att använda som skrivbordsunderlägg. Du kan också använda transparens för ditt skrivbordsunderlägg, oavsett om det är en färg eller en bild, med hjälp av skjutreglaget **Transparens**.

Det är bra att tänka på följande definitioner som hör till **skrivbordsunderlägg**:

* Det grå området utanför ditt rapportområde är **skrivbordsunderlägg**-området
* Området på arbetsytan där du kan placera visuella objekt kallas för rapport**sidan** och kan ändras i **Format-fönstret** med hjälp av listmenyn **Sidbakgrund**.

Rapport**sidan** är alltid i förgrunden (jämfört med skrivbordsunderlägget), samtidigt som **skrivbordsunderlägget** ligger bakom den och det element på rapportsidan som är längst bak. När du använder genomskinlighet för sidan har de visuella objekten i din rapport också transparensen tillämpat, vilket låter ditt skrivbordsunderlägg visas i bakgrunden genom dina visuella objekt.

För alla nya rapporter är standardinställningarna följande:

* Rapport**sidan** är inställd på **vit** och dess transparens är inställd på **100 %**
* **Skrivbordsunderlägget** är inställt på **vit** och dess transparens är inställd på **0 %**

När du ställer in din sidas bakgrund till mer än 50 % transparens så visas en prickad linje medan du skapar eller redigerar din rapporten för att visa gränsen för rapportens arbetsyta. 

![Transparens större än 50 % resulterar i en prickad kantlinje](media/desktop-visual-elements-for-reports/visual-elements-for-reports_04.png)

Det är viktigt att notera att den prickade gränsen *endast* visas när du redigerar rapporten och *inte* visas för personer som ser din publicerade rapport, till exempel när den visas i **Power BI-tjänsten**.

> [!NOTE]
> Om du använder mörka bakgrunder för skrivbordsunderlägg och använder en vit eller en väldigt ljus textfärg måste du ha i åtanke att funktionen **Exportera till PDF** inte tar med skrivbordsunderlägg vid exporten. Det betyder att en export med vit text kommer att vara praktiskt taget osynlig i den exporterade PDF-filen. Mer information om [Exportera till PDF](desktop-export-to-pdf.md) finns i avsnittet **Exportera till PDF**.


## <a name="using-improved-visual-headers-in-power-bi-reports"></a>Använd förbättrade visuella rubriker i Power BI-rapporter

Från och med juli 2018-versionen av **Power BI Desktop**, har rubrikerna för visuella objekt i rapporter förbättrats avsevärt. De primära förbättringarna är att rubriken har kopplats bort från det visuella objektet så att placeringen kan justeras beroende på dina layout- och placeringspreferenser och rubriken visas nu i det visuella objektet istället för flytande ovanför. 

Som standard visas rubriken inuti det visuella objektet i linje med rubriken. I följande bild kan du se sidhuvudet (fäst-ikonen, expandera-ikonen och ellips-ikonen) inom det visuella objektet och justerat till höger, längs samma vågräta position som det visuella objektets rubrik.

![Visuella rubriker kan nu finnas i ett visuellt objekt eller flyttas](media/desktop-visual-elements-for-reports/visual-elements-for-reports_05.png)

Om ditt visuella objekt inte har en rubrik, flyter rubriken ovanför det visuella objektet justerad till höger, enligt följande bild. 

![Visuella rubriker flyter ovanpå visuella objekt om det inte finns någon rubrik](media/desktop-visual-elements-for-reports/visual-elements-for-reports_07.png)

Om ditt visuella objekt placeras högst upp i din rapport, fäster sidhuvudet för det visuella objektet istället längst ner på det visuella objektet. 

![Visuella rubriker fäster längst ned när de gränsar till toppen på rapporten](media/desktop-visual-elements-for-reports/visual-elements-for-reports_08.png)

Varje visuellt objekt har också ett kort i **Formatering**-avsnittet i **Visualiseringar**-fönstret som kallas **Sidhuvud för visuellt objekt**. I det kortet så kan du justera alla typer av egenskaper för sidhuvudet för visuella objekt

![Varje visuellt objekt har ett kort för sidhuvudet för visuella objekt i Formatering-fönstret](media/desktop-visual-elements-for-reports/visual-elements-for-reports_09.png)

> [!NOTE]
> Synligheten för knappar påverkar inte din rapport när du skapar eller redigerar rapporten. Du måste publicera rapporten och visa den i läsläge för att se effekten. Det här beteendet garanterar att de många alternativen i rubriker för visuella objektrubriker är viktiga när du redigerar, särskilt varningsikoner som informerar om problem när du redigerar.

För rapporter som bara visas i **Power BI-tjänsten**, kan du justera användningen av visuella rubriker genom att gå till **Min arbetsyta > Rapporter** och sedan välja ikonen **Inställningar**. Där ser du inställningar för rapporten som du valde **Inställningar** för och du kan justera inställningarna därifrån, enligt följande bild.

![Inställningarna i Power BI-tjänsten för att använda förbättrade visuella rubriker](media/desktop-visual-elements-for-reports/visual-elements-for-reports_10.png)

### <a name="enabling-improved-visual-headers-for-existing-reports"></a>Aktivera förbättrade visuella rubriker för befintliga rapporter

Det nya sidhuvudet för visuella objekt är standardbeteendet för alla nya rapporter. För befintliga rapporter måste det här beteendet aktiveras i **Power BI Desktop** genom att gå till **Arkiv > Alternativ och inställningar > Alternativ** och sedan aktivera kryssrutan **Använd det moderna sidhuvudet för visuella objekt med uppdaterade formatalternativ** i **Rapportinställningar**.

![Befintliga rapporter måste markera kryssrutan Alternativ för att använda förbättrade visuella rubriker](media/desktop-visual-elements-for-reports/visual-elements-for-reports_06.png)


## <a name="next-steps"></a>Nästa steg
För mer information om **Power BI Desktop**, och hur du kommer igång, ta en titt i följande artiklar.

* [Vad är Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datakällor i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   
