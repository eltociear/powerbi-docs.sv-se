---
title: Använda ett relativt datumutsnitt eller filter i Power BI Desktop
description: Lär dig hur du använder ett utsnitt eller filter för att begränsa relativa datumintervall i Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/28/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 3d8057c4d35294dd5e83638b721169e4d54d2adf
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374531"
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi"></a>Använda ett relativt datumutsnitt och filter i Power BI
Med ett **relativt datumutsnitt** eller **relativt datumfilter** kan du använda tidsbaserade filter på kolumner i datamodellen. Du kan till exempel använda ett **relativt datumutsnitt** för att endast visa försäljningsdata inom de senaste 30 dagarna (eller månad, kalendermånad och så vidare). När du uppdaterar data tillämpas den relativa tidsperioden automatiskt.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

## <a name="using-the-relative-date-range-slicer"></a>Använda relativt datumutsnitt
Du kan använda utsnittet relativt datum precis som andra utsnitt. Skapa ett **utsnitt** för rapporten och välj sedan ett datumvärde för värdet **Fält**. I följande bild har *BeställningsDatum* markerats.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Välj utsnittet på arbetsytan och sedan cirkumflex i det övre högra hörnet av utsnittet visual. Om det visuella objektet innehåller datuminformation, menyn visas alternativet för **relativa**. 

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Välj *Relativt* för det relativa datumutsnittet.

Sedan kan du välja inställningarna. För den första listrutan i det *relativa datumutsnittet* har du följande alternativ:

* Sista
* Nästa
* Detta

Dessa val visas i följande bild.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

Med nästa inställning (i mitten) i *relativt datumutsnitt* kan du ange ett värde för att definiera det relativa datumintervallet.

Du kan välja datummåttet i den tredje inställningen. Du har följande val:

* Dagar
* Veckor
* Veckor (kalender)
* Månader
* Månader (kalender)
* År
* År (kalender)

Dessa val visas i följande bild.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

Om du väljer *Månader* från listan och anger 2 i mitteninställningen, skulle följande hända: Om dagens datum är 20 juli visas data i det visuella objektet för de föregående två månaderna, från och med 20 maj till och med 20 juli (dagens datum).

Som jämförelse visas data från 1 maj till och med 30 juni (de sista två fullständiga kalendermånaderna) om du väljer *Månader (kalender)* .

## <a name="using-the-relative-date-range-filter"></a>Använda relativt datumfilter
Du kan också skapa ett filter för relativt datumintervall för rapportsidan eller hela rapporten. Om du vill göra detta, drar du ett datumfält till områdena **Sidonivåfiltrer** eller **Rapportnivåfilter** områden i fönstret **Fält** enligt följande bild.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Därefter kan du ändra det relativa datumintervallet på ett likande sätt som du anpassar ett **relativt datumutsnitt**. Välj **Relativt datumfilter** från listrutan **Filtertyp**.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

När du har valt **Relativt datumfilter** visas tre områden för att redigera det, inklusive en numerisk ruta i mitten, precis som för utsnitt.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

Så enkelt är det att använda relativa datumbegränsningar i dina rapporter.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Följande begränsningar och överväganden kan användas för utsnitt och filter **relativt datumintervall**.

* Datamodeller i **Power BI** inkluderar inte tidszonsinformation. Modeller kan lagra tidpunkter, men det finns inget som indikerar vilken tidszonen de befinner sig i.
* Utsnitt och filter baseras alltid på tiden i UTC, så om du konfigurerar ett filter i en rapport och skickar det till en kollega i en annan tidszon visar båda samma data. Men om du inte befinner dig i tidszonen UTC kan du se data för andra tider än du har förväntat dig.
* Data som hämtats i en lokal tidszon kan konverteras till UTC med hjälp av **frågeredigeraren**.

