---
title: Använda ett relativt datumutsnitt eller filter i Power BI
description: Lär dig hur du använder ett utsnitt eller filter till att begränsa relativa datumintervall i Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: f63a56ea350d089b82eb7a18470e1bcc439d1151
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866528"
---
# <a name="creating-a-relative-date-slicer-and-filter-in-power-bi"></a>Skapa ett relativt datumutsnitt eller filter i Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Med ett **relativt datumutsnitt** eller **relativt datumfilter** kan du använda tidsbaserade filter på kolumner i datamodellen. Du kan till exempel använda ett **relativt datumutsnitt** för att bara visa försäljningsdata inom de senaste 30 dagarna (eller månad, kalendermånad och så vidare). När du uppdaterar data tillämpas den relativa tidsperioden automatiskt.

![Skärmbild av en rapport med en pil som pekar på ett relativt datumutsnitt.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

För att dela en rapport med en Power BI-kollega krävs att du både har individuella Power BI Pro-licenser eller att rapporten har sparats med Premium-kapacitet.

## <a name="create-the-relative-date-range-slicer"></a>Skapa relativt datumutsnitt

Du kan använda utsnittet relativt datum precis som andra utsnitt. Skapa ett **utsnitt** för rapporten och välj sedan ett datumvärde för värdet **Fält**. I följande bild har vi valt fältet *OrderDate*.

![Skärmbild av fönstret Visualiseringar med pilar som pekar på visualiseringen av utsnittet och källan för Fält.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Välj utsnittet på arbetsytan och sedan cirkumflex i det övre högra hörnet av visualiseringen av utsnittet. Om det finns datumdata för det visuella objektet visas alternativen för **Relativt** på menyn.

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

## <a name="create-the-relative-date-range-filter"></a>Skapa relativt datumfilter

Du kan också skapa ett filter för relativt datumintervall för rapportsidan eller hela rapporten. För att göra detta drar du ett datumfält till källan **Sidnivåfilter** eller **Rapportnivåfilter** i fönstret **Fält**:

![Skärmbild av fältet OrderDate som dras till källan för sidnivåfilter.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

När det väl ligger på plats kan du ändra det relativa datumintervallet. Det är samma tillvägagångssätt som när du anpassar det **relativa datumutsnittet**. Välj **Relativt datumfilter** från listrutan **Filtertyp**.

![Skärmbild som visar listrutan Filtertyp och muspekaren på Relativ datumfiltrering.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

När du har valt **Relativ datumfiltrering** visas tre områden för redigering, med en numerisk ruta i mitten, precis som för utsnittet.

![Skärmbild av Rapportnivåfilter med pilar som pekar på Visa objekt för värdealternativet.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Följande begränsningar och överväganden kan användas för utsnitt och filter **relativt datumintervall**.

* Datamodeller i **Power BI** omfattar inte tidszonsinformation. Modeller kan lagra tidpunkter, men det finns inget som indikerar vilken tidszonen de befinner sig i.

* Utsnitt och filter baseras alltid på tiden i UTC. Om du skapar ett filter i en rapport och skickar rapporten till en kollega i en annan tidszon så kommer ni båda att se samma data. Om ni inte befinner er i tidszonen UTC så måste ni justera för tidsförskjutningen.

* Du kan konvertera data som hämtats i en lokal tidszon till UTC med hjälp av **Frågeredigeraren**.

## <a name="next-steps"></a>Nästa steg

- [Använda ett relativt datumutsnitt eller filter i Power BI](desktop-slicer-filter-date-range.md)
- [Utsnitt i Power BI](power-bi-visualization-slicers.md)
