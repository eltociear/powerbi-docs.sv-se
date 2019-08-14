---
title: Använda ett relativt datumutsnitt eller filter i Power BI Desktop
description: Lär dig hur du använder ett utsnitt eller filter för att begränsa relativa datumintervall i Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: e1dfda3c759d225019cc50d36cfe746976bd797a
ms.sourcegitcommit: cc4b18d55b2dca8fdb1bef00f53a0a808c41432a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68867075"
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi-desktop"></a>Använda ett relativt datumutsnitt och filter i Power BI Desktop

Med ett **relativt datumutsnitt** eller **relativt datumfilter** kan du använda tidsbaserade filter på kolumner i datamodellen. Du kan till exempel använda ett **relativt datumutsnitt** för att bara visa försäljningsdata inom de senaste 30 dagarna (eller månad, kalendermånad och så vidare). När du uppdaterar data tillämpas den relativa tidsperioden automatiskt.

![Skärmbild av en rapport, med en pil som pekar på ett relativt datumutsnitt.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

## <a name="use-the-relative-date-range-slicer"></a>Använd relativt datumutsnitt

Du kan använda utsnittet relativt datum precis som andra utsnitt. Skapa ett **utsnitt** för rapporten och välj sedan ett datumvärde för värdet **Fält**. I följande bild har vi valt fältet *OrderDate*.

![Skärmbild av fönstret Visualiseringar med pilar som pekar på visualiseringen av utsnittet och källan för Fält.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Välj utsnittet på arbetsytan och sedan cirkumflex i det övre högra hörnet av visualiseringen av utsnittet. Om det finns datumdata för det visuella objektet så visas alternativen för **Relativt** på menyn.

![Skärmbild av visualiseringen av utsnittet med en markering runt cirkumflexet och en pil som pekar på Relativt.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Välj *Relativt* för det relativa datumutsnittet.

Sedan kan du välja inställningarna.

För den första inställningen i det *relativa datumutsnittet* finns följande alternativ:

![Skärmbild av konfigurationsalternativ för Relativt, med den första inställningen markerad.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Sista

* Nästa

* Den här

Med den andra inställningen (i mitten) i *det relativa datumutsnittet* kan du ange ett värde för att definiera det relativa datumintervallet.

![Skärmbild av konfigurationsalternativen för Relativt, med den andra inställningen markerad.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04a.png)

Du kan välja datummåttet i den tredje inställningen. Du har följande val:

![Skärmbild av konfigurationsalternativen för Relativt, med den tredje inställningen markerad.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

* Dagar

* Veckor

* Veckor (kalender)

* Månader

* Månader (kalender)

* År

* År (kalender)

Om du till exempel väljer **Månader** i listan och anger *2* i den mellersta inställningen får du följande resultat:

* om dagens datum är 20 juli

* data i det visuella objektet för utsnittet kommer innehålla data för de föregående två månaderna

* från och med 21 maj och till och med 20 juli (dagens datum)

Som jämförelse visas data från 1 maj till och med 30 juni (de sista två fullständiga kalendermånaderna) om du väljer *Månader (kalender)* .

## <a name="using-the-relative-date-range-filter"></a>Använda relativt datumfilter

Du kan också skapa ett filter för relativt datumintervall för rapportsidan eller hela rapporten. För att göra detta drar du ett datumfält till källan **Sidnivåfilter** eller **Rapportnivåfilter** i fönstret **Fält**:

![Skärmbild av fältet OrderDate som dras till källan för sidnivåfilter.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

När det väl ligger på plats kan du ändra det relativa datumintervallet. Det är samma tillvägagångssätt som när du anpassar det **relativa datumutsnittet**. Välj **Relativt datumfilter** från listrutan **Filtertyp**.

![Skärmbild som visar listrutan Filtertyp och muspekaren på Relativ datumfiltrering.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

När du har valt **Relativ datumfiltrering** visas tre områden för redigering, med en numerisk ruta i mitten, precis som för utsnittet.

![Skärmbild av Rapportnivåfilter med pilar som pekar på Visa objekt för värdealternativet.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Följande begränsningar och överväganden kan användas för utsnitt och filter **relativt datumintervall**.

* Datamodeller i **Power BI** omfattar inte tidszonsinformation. Modeller kan lagra tidpunkter, men det finns inget som indikerar vilken tidszonen de befinner sig i.

* Utsnitt och filter baseras alltid på tiden i UTC. Om du skapar ett filter i en rapport och skickar rapporten till en kollega i en annan tidszon så kommer ni båda att se samma data. Om ni inte befinner er i UTC-tidszonen så måste ni justera för tidsförskjutningen.

* Du kan konvertera data som hämtats i en lokal tidszon till UTC med hjälp av **Frågeredigeraren**.

## <a name="next-steps"></a>Nästa steg

Lär dig [använda gruppering i Power BI Desktop](../desktop-grouping-and-binning.md).
