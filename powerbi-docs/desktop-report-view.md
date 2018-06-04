---
title: Rapportvy i Power BI Desktop
description: Rapportvy i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5026de163aa870c042fe4c3a13b6ff3fbf8849f0
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34290808"
---
# <a name="report-view-in-power-bi-desktop"></a>Rapportvy i Power BI Desktop
Om du har arbetat med Power BI, vet du hur enkelt det är att skapa rapporter som ger dynamisk perspektiv och insikter om dina data. Power BI har också fler avancerade funktioner i Power BI Desktop. Du kan använda Power BI Desktop för att skapa avancerade frågor, blandade data från flera källor, skapa relationer mellan tabeller och mycket mer.

Power BI Desktop innehåller **Rapportvyn** där du kan skapa ett obegränsat antal rapportsidor med visuella objekt. Rapportvyn ger praktiskt taget samma designupplevelse som rapportens redigeringsvy i Power BI-tjänsten. Du kan flytta runt visuella objekt, kopiera och klistra in, sammanfoga och så vidare.

Skillnaden mellan dessa är att när du använder Power BI Desktop kan du arbeta med dina frågor och modellera dina data så att dina data ger de bästa insikterna i dina rapporter. Du kan spara Power BI Desktop-filen var du vill, oavsett om det är en lokal hårddisk eller till molnet.

## <a name="lets-take-a-look"></a>Låt oss ta en titt!
När du läser in data i Power BI Desktop, ser du **Rapportvisningen** med en tom arbetsyta.

![](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Du kan växla mellan **Rapportvy**, **Datavy** och **Relationsvy** genom att välja ikonerna i det vänstra navigationsfältet:

![](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

När du har lagt till vissa data kan du lägga till fält i ett nytt visuellt objekt i arbetsytan.

![](media/desktop-report-view/pbid_reportview_addvis.gif)

Om du vill ändra typen av visualisering, kan du välja detta från gruppen **Visuella objekt** i menyfliksområdet eller högerklicka och välja en annan typ från ikonen **Ändra typen av visualisering**.

![](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Se till att experimentera med olika typer av visuella objekt. Det är viktigt att ditt visuella objekt förmedlar dina data tydligt.
> 
> 

En rapport har minst en tom sida från början. Sidor visas i fönstret navigator till vänster om arbetsytan. Du kan lägga till alla typer av grafik på en sida, men det är viktigt att inte överdriva. För många visuella objekt på en sida gör det svårt att hitta rätt information. Du kan lägga till nya sidor i rapporten. Klicka bara på **Ny sida** i menyfliksområdet.

![](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Om du vill ta bort en sida klickar du på **X** på sidans flik längst ned i rapporten.

![](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Rapporter och visuella objekt går inte att fästa på en instrumentpanel från Power BI Desktop. För att göra det måste du [Publicera från Power BI Desktop](desktop-upload-desktop-files.md) till Power BI-platsen.

## <a name="hide-report-pages"></a>Dölja rapportsidor

När du skapar en rapport har du även möjlighet att dölja sidor i den. Detta kan vara användbart om du behöver skapa underliggande data eller visuella objekt i en rapport, men inte vill att dessa sidor ska vara synliga för andra, t.ex. när du skapar tabeller eller stödjande visuella objekt som används på andra rapportsidor. Det finns många andra kreativa orsaker till att du kanske vill skapa en rapportsida och sedan dölja den från en rapport som du vill publicera. 

Det är lätt att dölja en rapportsida. Du högerklickar helt enkelt på rapportsidans flik och väljer **Dölj** på den meny som visas.

![](media/desktop-report-view/report-view_05.png)

Det finns vissa saker du bör tänka på när du döljer en rapportsida:

* Du kan fortfarande se en dold rapportvy i **Power BI Desktop**, även om sidans rubrik är nedtonad. I följande bild döljs sida 4.

    ![](media/desktop-report-view/report-view_06.png)

* Du *kan inte* se en dold rapportsida när du visar rapporten i **Power BI-tjänsten**.

* Att dölja en rapportsida är *inte* en säkerhetsåtgärd. Användare kan fortfarande använda sidan, och dess innehåll är fortfarande tillgängligt när du visar detaljerad information eller använder andra metoder.

* När en sida är dold i visningsläge, så visas inga navigeringspilar.

