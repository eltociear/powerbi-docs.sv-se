---
title: Använda fönstret Analytics i Power BI Desktop
description: Skapa dynamiska referenslinjer för visuella objekt i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 71fbdfda6675585d861b1447ce3d37e83b660825
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349550"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Använda fönstret Analytics i Power BI Desktop

Med fönstret **Analytics** i Power BI Desktop kan du lägga till *dynamiska referenslinjer* i visuella objekt och ange fokus för viktiga trender eller insikter. Ikonen och fönstret **Analytics** finns i området **Visualiseringar** i Power BI Desktop.

![Fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Fönstret **Analytics** visas bara när du markerar ett visuellt objekt på arbetsytan för Power BI Desktop.

## <a name="search-within-the-analytics-pane"></a>Söka i fönstret Analytics

Sedan lanseringen av Power BI Desktop i februari 2018 (version 2.55.5010.201 eller senare), kan du söka i fönstret **Analytics** som ingår i fönstret **Visualiseringar**. Sökrutan visas när du väljer ikonen **Analytics**.

![Sökruta, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Använda fönstret Analytics

I fönstret **Analytics** kan du skapa följande typer av dynamiska referenslinjer:

* X-axel konstant linje
* Y-axel konstant linje
* Minimilinje
* Maxlinje
* Medellinje
* Medianlinje
* Percentillinje
* Symmetrifyllning

> [!NOTE]
> Alla rader är inte tillgängliga för alla typer av visuella objekt.

Följande avsnitt visar hur du kan använda fönstret **Analytics** och dynamiska referenslinjer i dina visualiseringar.

Följ dessa steg om du vill visa tillgängliga dynamiska referensrader för någon visualisering:

1. Välj eller skapa ett visuellt objekt och välj sedan ikonen **Analytics** i avsnittet **Visualiseringar**.

    ![Visa analys av ett visuellt objekt, fönstret Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Välj den typ av linje som du vill skapa för att se dess alternativ. I det här fallet väljer vi **Medellinje**.

    ![Medellinje, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Om du vill skapa en ny linje väljer du **+&nbsp;Lägg till**. Därefter kan du namnge linjen. Dubbelklicka på textrutan och ange namnet.

    Nu har du alla typer av alternativ för din linje. Du kan ange dess **Färg**, **Transparens** i procent, **Linjeformat** och **Position** (jämfört med det visuella objektets dataelement). Du kan också välja om du vill inkludera en **Dataetikett**. Ange måttet för det visuella objektet som linjen ska baseras på genom att välja listrutan **Mått**, som fylls i automatiskt med dataelement från det visuella objektet. Här väljer vi **Kultur** som mått, märker den *Medelvärde för kultur* och anpassar några av de andra alternativen.

    ![Medellinje för kultur, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Om du vill att dataetiketten ska synas ändrar du **Dataetikett** från **Av** till **På**. När du gör detta får du en mängd ytterligare alternativ för din dataetikett.

    ![Inställningar för dataetikett, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Observera siffran som visas bredvid objektet **Genomsnittlig rad** objektet i fönstret **Analytics**. Det anger hur många dynamiska linjer som det för närvarande finns i ditt visuella objekt, samt vilken typ de är. När vi lägger till en **Maxlinje** i **Affordability** ser vi att fönstret **Analytics** nu visar att vi också har en **Maxlinje** för den dynamiska referenslinje som tillämpas på det visuella objektet.

    ![Summor för maxlinje och medellinje, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Om det visuella objekt som du har valt inte kan ha dynamiska referenslinjer (i det här fallet **Karta**), visas nedanstående meddelande när du väljer fönstret **Analytics**.

![Ej tillgänglig analys för ett visuellt kartobjekt, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

Du kan lyfta fram många intressanta insikter genom att skapa dynamiska referenslinjer i fönstret **Analytics**.

Vi planerar fler funktioner, inklusive fler visuella objekt som kan ha dynamiska referenslinjer. Kom tillbaka ofta för att se vad som är nytt.

## <a name="apply-forecasting"></a>Tillämpa prognostisering

Om du har tidsdata i din datakälla kan du använda funktionen för *prognostisering*. Välj ett visuellt objekt och expandera sedan avsnittet **Prognos** i fönstret **Analytics**. Du kan ange olika inmatningar för att ändra prognostiseringen, t.ex. **Prognoslängd** och **Konfidensintervall**. Följande bild visar ett grundläggande visuellt linjeobjekt med prognostisering tillämpad. Använd din fantasi (och testa olika prognoser) för att se hur det kan se ut för dina modeller.

![Funktionen Prognos, fönstret Analytics, Visualiseringar, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> Prognosfunktionen är bara tillgänglig för visuella linjeobjekt.

## <a name="limitations"></a>Begränsningar

Möjligheten att använda dynamiska referenslinjer beror på vilken typ av visuellt objekt som används. I följande listor beskrivs dessa begränsningar mer specifikt.

Du kan använda *X-axel konstant linje*, *Y-axel konstant linje* och *Symmetrifyllning* på följande visuella objekt:

* Punktdiagram

Användningen av *konstant linje*, *minimilinje*, *maxlinje*, *medellinje*, *medianlinje* och *percentillinje* är tillgänglig för följande visuella objekt:

* Ytdiagram
* Grupperat liggande stapeldiagram
* Grupperat stående stapeldiagram
* Linjediagram
* Punktdiagram

Följande visuella objekt kan bara använda en *konstant linje* från fönstret **Analytics**:

* Staplat ytdiagram
* Liggande stapeldiagram
* Stående stapeldiagram
* Vattenfallsdiagram
* 100 % liggande stapeldiagram
* 100 % stående stapeldiagram

Följande visuella objekt kan använda en *trendlinje* om det finns tidsdata:

* Ytdiagram
* Grupperat stående stapeldiagram
* Linjediagram
* Linjediagram och grupperat stående stapeldiagram

Slutligen kan du för närvarande inte använda några dynamiska linjer i många visuella objekt, inklusive (men inte begränsat till):

* Tratt
* Linjediagram och grupperat stående stapeldiagram
* Linjediagram och stående stapeldiagram
* Banddiagram
* Icke-kartesianska visuella objekt, t.ex. ringdiagram, mätare, matris, cirkeldiagram och tabell

*Percentilraden* är bara tillgänglig när du använder importerade data i Power BI Desktop, eller när du är liveansluten till en modell på en server som kör **Analysis Service 2016** eller senare, **Azure Analysis Services** eller en datamängd i Power BI-tjänsten.

## <a name="next-steps"></a>Nästa steg

Du kan göra många olika saker med Power BI Desktop. Läs följande resurser för mer information om dess möjligheter:

* [Nyheter i Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Hämta Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)
* [Vad är Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datatyper i Power BI Desktop](../connect-data/desktop-data-types.md)
* [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Utföra vanliga uppgifter i Power BI Desktop](desktop-common-query-tasks.md)
