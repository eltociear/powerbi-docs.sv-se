---
title: Filter och markeringar i Power BI-rapporter
description: Om filter och markeringar i Power BI-rapporter
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 708d57f6092029b3c82412336b54fce1ae0ca441
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83280758"
---
# <a name="filters-and-highlighting-in-power-bi-reports"></a>Filter och markeringar i Power BI-rapporter
 Den här artikeln ger en introduktion till filtrering och markering i Power BI-tjänsten. Upplevelsen är nästan exakt samma som i Power BI Desktop. *Filter* ta bort allt utan de data som du vill fokusera på. *Markering* är inte samma sak som filtrering. Data tas inte bort. I stället markeras en delmängd av synliga data; de data som inte markeras förblir synliga men nedtonade.

Det finns många olika metoder för att filtrera och markera rapporter i Power BI. Att ta med all denna information i en artikel skulle bli förvirrande, så vi har delat upp det så här:

* Introduktion till filter och markeringar, vilket är den artikel du läser nu.
* Hur du [skapa och använder filter i redigeringsvyn](power-bi-report-add-filter.md) i rapporter i Power BI Desktop och Power BI-tjänsten. När du har redigeringsbehörighet för en rapport, kan du skapa, ändra och ta bort filter i rapporter.
* Hur visuellt objekt [filtrerar och markerar i en rapport som delas med dig](../consumer/end-user-interactions.md) eller i rapportens läsvy i Power BI-tjänsten. Vad du kan göra är mer begränsat, men du har fortfarande tillgång till en mängd olika filtrerings- och markeringsalternativ.  
* En detaljerad genomgång av [de filtrerings- och markeringskontroller som är tillgängliga i redigeringsvyn](power-bi-report-add-filter.md) i Power BI Desktop och Power BI-tjänsten. I artikeln finns en detaljerad genomgång av typer av filter såsom datum och tid, numeriskt samt text. Den omfattar även skillnaderna mellan grundläggande och avancerade alternativ.
* Nu när du har lärt dig hur filter och markeringar fungerar som standard, [kan du lära dig hur man ändrar hur visualiseringar på en sida kan filtrera och markera varandra](service-reports-visual-interactions.md)

**Visste du att?** Power BI har en ny filterupplevelse. Läs mer om [den nya filterupplevelsen i Power BI-rapporter](power-bi-report-filter.md).

![Ny filterupplevelse](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading.png)


## <a name="intro-to-the-filters-pane"></a>Introduktion till fönstret Filter

Du kan använda filter i fönstret **filter** eller genom att [göra urval i utsnitt](../visuals/power-bi-visualization-slicers.md) direkt i själva rapporten. I fönstret Filter visas de tabeller och fält som används i rapporten och de filter som har tillämpats, i förekommande fall. 

![Fönstret Filter](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Det finns fyra typer av filter.

- **sidfilter** gäller för alla visuella objekt på rapportsidan     
- **visuellt filter** gäller för ett enskilt visuellt objekt på en rapportsida. Du kan bara se filter på visuell nivå om du har valt en visualisering på rapportarbetsytan.    
- **rapportfilter** gäller för alla sidor i rapporten    
- **filter för visning av detaljerad information** gäller för en enda entitet i en rapport    

Du kan söka på sidor, visuella objekt och rapportfilter i läs- eller redigeringsläge för att hitta och välja värdet du letar efter. 

![Söka i ett filter](media/power-bi-reports-filters-and-highlighting/power-bi-search-filter.png)

Om filtret har ordet **alla** bredvid det innebär det att alla värden i fältet ingår i filtret.  Som exempel kan vi av **Chain(All) (Kedja(alla))** på skärmbilden nedan avläsa att den här rapportsidan innehåller data om alla butikskedjorna.  Å andra sidan berättar filtret på rapportnivå för **Räkenskapsår 2013 eller 2014** att rapporten bara innehåller data för räkenskapsåren 2013 och 2014.

## <a name="filters-in-reading-or-editing-view"></a>Filter i läs- eller redigeringsvyn
Det finns två lägen för att interagera med rapporter: [Läsvy och Redigeringsvy](../consumer/end-user-reading-view.md). Vilka filtreringsfunktioner som är tillgängliga beror på vilket läge du befinner dig i.

* Du kan lägga till rapportfilter, sidfilter, filter för visning av detaljerad information och visuella filter i redigeringsvyn. När du sparar rapporten sparas filtren med rapporten, även om du har öppnat den i en mobilapp. De som tittar på rapporten i läsvyn kan interagera med de filter som du har lagt till, men inte lägga till nya filter.
* I läsvyn kan du interagera med alla filter som redan finns i rapporten och spara dina val. Du kan inte lägga till nya filter.

### <a name="filters-in-reading-view"></a>Filter i läsvyn
Om du bara har åtkomst till en rapport i läsvyn ser fönstret Filter ut ungefär så här:

![Filter i läsvyn](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Så den här sidan i rapporten har sex filter på sidnivå och ett på rapportnivå.

Varje visuellt objekt kan ha filter för alla fält i det visuella objektet och en rapportskapare kan lägga till fler. I bilden nedan har bubbeldiagrammet sex filter.

![Filter på visuell nivå](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

I läsvyn kan du utforska data genom att ändra befintliga filter. De ändringar du gör sparas med rapporten, även om du har öppnat rapporten i en mobilapp. Läs mer i [guiden om panelen för rapportfilter](../consumer/end-user-report-filter.md)

När du avslutar rapporten sparas dina filter. Om du vill ångra din filtrering och återgå till standardfiltreringen, standardsegmenteringen, standarddetaljnivån och standardsorteringen som rapportförfattaren konfigurerat väljer du **Återställ till standard** från den översta menyraden.

![Återställ till standardikon](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

### <a name="filters-in-editing-view"></a>Filter i redigeringsvyn
När du har ägarbehörighet för en rapport och öppnar den i redigeringsvyn ser du att **Filter** bara är ett av flera tillgängliga fönster för redigering.

![Fönstret Filter i redigeringsvyn](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Precis som i läsvyn ser vi att den här sidan i rapporten har sex filter på sidnivå och ett på rapportnivå. Och genom att välja bubbeldiagrammet ser vi att den har sex filter på visuell nivå.

Vi kan göra mer med filter och markeringar i redigeringsvyn. Främst kan vi lägga till nya filter. Lär dig hur du kan [lägga till ett filter i en rapport](power-bi-report-add-filter.md) och mycket mer.

## <a name="ad-hoc-highlighting"></a>Ad hoc-markering
Markera ett värde eller en axeletikett i ett visuellt objekt för att markera andra visuella objekt på sidan. Om du vill ta bort markeringen markerar du värdet igen markerar valfritt tomt utrymme i samma visuella objekt. Markering är ett roligt sätt att snabbt utforska påverkan av dina data. Mer information om att finjustera den här typen av korsmarkering finns i [Visuella interaktioner](service-reports-visual-interactions.md).

![Korsmarkering](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)


## <a name="next-steps"></a>Nästa steg

[Den nya filterupplevelsen i Power BI-rapporter](power-bi-report-filter.md)

[Lägga till ett filter i en rapport (i redigeringsvyn)](power-bi-report-add-filter.md)

[Ta en titt på rapportfiltren](../consumer/end-user-report-filter.md)

[Ändra hur en rapports visuella objekt korsfiltrerar och korsmarkerar varandra](../consumer/end-user-interactions.md)

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
