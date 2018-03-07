---
title: "Använda ett relativt datumutsnitt eller filter i Power BI Desktop"
description: "Lär dig hur du använder ett utsnitt eller filter för att begränsa relativa datumintervall i Power BI Desktop"
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
ms.date: 12/05/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 0432998e44cdb1bf95a41225b73d805ec2a2379f
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi-desktop"></a>Använda ett relativt datumutsnitt och filter i Power BI Desktop
Med ett **relativt datumutsnitt** eller **relativt datumfilter** kan du använda tidsbaserade filter på kolumner i datamodellen. Du kan till exempel använda ett **relativt datumutsnitt** för att endast visa försäljningsdata inom de senaste 30 dagarna (eller månad, år och så vidare). När du uppdaterar data tillämpas den relativa tidsperioden automatiskt.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_01.png)

## <a name="using-the-relative-date-range-slicer"></a>Använda relativt datumutsnitt
Du kan använda utsnittet relativt datum precis som andra utsnitt. Skapa ett **utsnitt** för rapporten och välj sedan ett datum som värde för värdet **Fält**. I följande bild har *BeställningsDatum* markerats.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_02.png)

Välj cirkumflex i det övre högra hörnet på **utsnittet relativt datum** för att visa en meny.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_03.png)

Välj *Relativt* för det relativa datumutsnittet.

Sedan kan du välja inställningarna. För den första listrutan i det *relativa datumutsnittet* kan du välja mellan följande alternativ:

* Sista
* Nästa
* Detta

Dessa val visas i följande bild.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_04.png)

Med inställningen nästa (i mitten) i det *relativt datumutsnittet* kan du ange ett värde för att definiera det relativa datumintervallet.

Med den tredje inställningen kan du välja datummåttet och välja mellan följande alternativ:

* Dagar
* Veckor
* Veckor (kalender)
* Månader
* Månader (kalender)
* År
* År (kalender)

Dessa val visas i följande bild.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_05.png)

Välj till exempel *månader* från listan och anger 2 i den mellersta inställningen. Följande händer: om dagens datum är 20 juli visas data i det visuella objektet för de föregående två månaderna, från och med 20 maj till och med 20 juli (dagens datum).

Som jämförelse visas data från 1 maj till och med 30 juni (de sista två fullständiga kalendermånaderna) om du väljer *Månader (kalender)*.

## <a name="using-the-relative-date-range-filter"></a>Använda relativt datumfilter
Du kan också skapa ett filter för relativt datumintervall för rapportsidan eller hela rapporten. Om du vill göra detta, drar du ett datumfält till områdena **Sidonivåfiltrer** eller **Rapportnivåfilter** områden i fönstret **Fält** enligt följande bild.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_06.png)

Därefter kan du ändra det relativa datumintervallet på samma sätt som du anpassar ett **relativt datumutsnitt**. Välj **Relativt datumfilter** från listrutan **Filtertyp**.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_07.png)

När du har valt **Relativt datumfilter** visas tre områden för att redigera det, inklusive en numerisk ruta i mitten, precis som för utsnitt.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_08.png)

Så enkelt är det att använda relativa datumbegränsningar i dina rapporter.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Följande begränsningar och överväganden kan användas för utsnitt och filter **relativt datumintervall**.

* Datamodeller i **Power BI** inkluderar inte tidszonsinformation. Modeller kan lagra tidpunkter, men det finns inget som indikerar vilken tidszonen de befinner sig i.
* Utsnitt och filter baseras alltid på tiden i UTC, så om du konfigurerar ett filter i en rapport och skickar det till en kollega i en annan tidszon visar båda samma data. Men om du inte befinner dig i tidszonen UTC kan du se data för andra tider än du har förväntat dig.
* Data som hämtats i en lokal tidszon kan konverteras till UTC med hjälp av **frågeredigeraren**.

