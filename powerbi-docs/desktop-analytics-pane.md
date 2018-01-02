---
title: "Använda Analytics-fönstret i Power BI Desktop"
description: "Skapa dynamiska referenslinjer för visuella objekt i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: add95532f645c143aea0f58200f9e3b1467320d0
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="using-the-analytics-pane-in-power-bi-desktop"></a>Använda Analytics-fönstret i Power BI Desktop
Med fönstret **Analytics** i **Power BI Desktop** kan du lägga till dynamiska *referenslinjer* i visuella objekt och ange fokus för viktiga trender eller analyser. Fönstret **Analytics** finns i området **Visualiseringar** i Power BI Desktop, med start från augusti 2016-versionen (version 2.37.4464.321 eller senare), som visas nedan.

![](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Fönstret **Analytics** visas bara när du markerar ett visuellt objekt på arbetsytan för Power BI Desktop.
> 
> 

## <a name="enable-forecasting-preview"></a>Aktivera prognostisering (förhandsversion)
I september 2016-versionen för **Power BI Desktop** (version 2.39.4526.362 eller senare) kan du också utföra *prognostisering* från fönstret **Analytics**. Du måste aktivera denna förhandsversionsfunktion genom att gå till **Arkiv > Alternativ och inställningar > Alternativ** och sedan välja **Förhandsversionsfunktioner** i det vänstra fönstret. Markera kryssrutan bredvid **Prognostisering** för att aktivera funktionen enligt följande bild. Du måste starta om **Power BI Desktop** för att ändringarna ska börja gälla.

![](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="using-the-analytics-pane"></a>Använda fönstret Analytics
I fönstret **Analytics** kan du skapa följande typer av dynamiska referenslinjer (alla rader är inte tillgängliga för alla typer av visuella objekt):

* X-axel konstant linje
* Y-axel konstant linje
* Minimilinje
* Maxlinje
* Medellinje
* Medianlinje
* Percentillinje

Följande avsnitt visar hur du kan använda fönstret **Analytics** och dynamiska referenslinjer i dina visualiseringar.

Följ dessa steg om du vill visa tillgängliga dynamiska referenslinjer för ett visuellt objekt:

1. Välj eller skapa ett visuellt objekt och välj sedan ikonen **Analytics** i avsnittet **Visualiseringar**.
   
   ![](media/desktop-analytics-pane/analytics-pane_2.png)
2. Välj nedåtpilen för den typ av linje som du vill skapa för att visa dess alternativ. I det här fallet väljer vi **Medellinje**.
   
   ![](media/desktop-analytics-pane/analytics-pane_3.png)
3. Om du vill skapa en ny linje väljer du **+ Lägg till**. Du kan sedan ange ett namn på linjen genom att dubbelklicka på textrutan och sedan skriva ditt namn.
   
   Det finns många typer av alternativ för linjer, till exempel att välja *färg*, *genomskinlighet*, *stil* och *position* (i förhållande till det visuella objektets dataelement), samt om du vill inkludera etiketten. Du kan dessutom välja vilka **Mått** i det visuella objektet som du vill att linjen ska baseras på genom att markera listrutan **Mått**, som fylls i automatiskt med dataelement från det visuella objektet. I det här fallet väljer vi *Väder*  som mått, märker den *Genomsnittligt väder* och anpassar några av de andra alternativen enligt nedan.
   
   ![](media/desktop-analytics-pane/analytics-pane_4.png)
4. Om du vill visa dataetiketten flyttar du skjutreglaget **Dataetikett** till På. När du gör detta får du en mängd ytterligare alternativ för din dataetikett, enligt nedanstående bild.
   
   ![](media/desktop-analytics-pane/analytics-pane_5.png)
5. Observera siffran som visas bredvid objektet **Medellinje** i fönstret **Analytics**. Det anger hur många dynamiska linjer som det för närvarande finns i ditt visuella objekt, samt vilken typ de är. Om vi lägger till en **Maxlinje** för *Levnadskostnader* kan du se att fönstret **Analytics** nu visar att vi också har en **Maxlinje** för den dynamiska referenslinje som tillämpas på det visuella objektet.
   
   ![](media/desktop-analytics-pane/analytics-pane_6.png)

Om det visuella objekt som du har valt inte kan ha dynamiska referenslinjer (i det här fallet **Karta**), visas följande när du väljer fönstret **Analytics**.

![](media/desktop-analytics-pane/analytics-pane_7.png)

Det finns många typer av intressanta analyser som du kan lyfta fram genom att skapa dynamiska referenslinjer i fönstret **Analytics**.

Vi planerar fler funktioner, inklusive fler visuella objekt som kan ha dynamiska referenslinjer, så håll ögonen öppna efter nyheter.

## <a name="apply-forecasting"></a>Tillämpa prognostisering
Du kan använda funktionen **Prognos** genom att välja ett visuellt objekt och sedan expandera avsnittet **Prognos** i fönstret **Analytics**. Du kan ange många olika inmatningar för att ändra prognostiseringen, t.ex. *Prognoslängd*, *Konfidensintervall* med mera. Följande bild visar en grundlinje för det visuella objektet med prognostisering tillämpad, men du kan använda din fantasi (och testa funktionen för *prognostisering* på olika sätt) för att se hur den kan användas på dina modeller.

![](media/desktop-analytics-pane/analytics-pane_8.png)

## <a name="limitations"></a>Begränsningar
Möjligheten att använda dynamiska referenslinjer beror på vilken typ av visuellt objekt som används. I följande lista visas vilka dynamiska linjer som är tillgängliga för de olika visuella objekten:

Alla dynamiska linjer är tillgängliga i följande visuella objekt:

* Ytdiagram
* Linjediagram
* Punktdiagram
* Grupperat stående stapeldiagram
* Grupperat liggande stapeldiagram

Följande visuella objekt kan bara använda en *konstant linje* från fönstret **Analytics**:

* Staplad yta
* Liggande stapel
* Stående stapel
* 100 % liggande stapeldiagram
* 100 % stående stapeldiagram

För följande visuella objekt är *trendlinjen* för närvarande det enda alternativet:

* Ej staplad linje
* Grupperat stående stapeldiagram

Slutligen går det för närvarande inte att använda icke-kartesiska visuella objekt med dynamiska linjer från fönstret **Analytics**, till exempel:

* Matris
* Cirkeldiagram
* Ring
* Tabell

## <a name="next-steps"></a>Nästa steg
Det finns olika typer av saker som du kan göra med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Nyheter i Power BI Desktop](desktop-latest-update.md)
* [Ladda ned Power BI Desktop](desktop-get-the-desktop.md)
* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datatyper i Power BI Desktop](desktop-data-types.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)    

