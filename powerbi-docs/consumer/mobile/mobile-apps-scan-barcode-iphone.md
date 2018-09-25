---
title: Skanna en streckkod med en iPhone från Power BI-mobilappen
description: Skanna streckkoder ute i världen och gå direkt till filtrerad BI-information i Power BI-mobilappen.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: d221cfdc849a18ba934ebacaf58ef40999ac0117
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46543323"
---
# <a name="scan-a-barcode-with-your-iphone-from-the-power-bi-mobile-app"></a>Skanna en streckkod med din iPhone från Power BI-mobilappen
Skanna streckkoder ute i världen och gå direkt till filtrerad BI-information i Power BI-mobilappen.

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Anta att en kollega har [taggat ett streckkodsfält i en rapport i Power BI Desktop](../../desktop-mobile-barcodes.md) och delat rapporten med dig. 

När du då skannar en produktstreckkod med skannern i Power BI-appen på din iPhone, ser du rapporten (eller listan med rapporter) med den streckkoden. Du kan öppna den rapporten på din iPhone, filtrerat till den streckkoden.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Skanna en streckkod med Power BI-skannern
1. I Power BI-mobilappen öppnar du den huvudsakliga navigeringsmenyn ![](media/mobile-apps-scan-barcode-iphone/pbi_iph_navmenu.png) i det övre vänstra hörnet. 
2. Skrolla ned till **skanner** och välj den. 
   
    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)
3. Du måste godkänna Power BI-appen för att använda kameran om din kamera inte är aktiverad. Det här är ett engångsgodkännande. 
4. Peka skannern på en streckkod på en produkt. 
   
    Du får upp en lista över rapporter som är associerade med den streckkoden.
5. Tryck på rapportnamnet för att öppna den på din iPhone, automatiskt filtrerat till den streckkoden.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrera efter andra streckkoder i en rapport
När du tittar på en rapport som filtreras efter en streckkod på din iPhone, kanske du vill filtrera samma rapport efter en annan streckkod.

* Om streckkodsikonen har ett filter ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), är filtret aktivt och rapporten filtreras redan efter en streckkod. 
* Om ikonen inte har ett filter ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), är inte filtret aktivt och rapporten filtreras inte efter en streckkod. 

Oavsett vilket, trycker du på ikonen om du vill öppna en liten meny med en flytande skanner.

* Fokusera skannern på det nya objektet för att ändra rapportens filter till ett annat streckkodsvärde. 
* Välj **rensa streckkodsfilter** för att gå tillbaka till den ofiltrerade rapporten.
* Välj **filtrera efter senaste streckkoder** för att ändra rapportfiltret till en av de streckkoder som du har skannat i den aktuella sessionen.

## <a name="issues-with-scanning-a-barcode"></a>Problem med att skanna en streckkod
Här följer några meddelanden som kan visas när du skannar en streckkod på en produkt.

### <a name="couldnt-filter-report"></a>”Det gick inte att filtrera rapporten...”
Rapporten du valt att filtrera, baseras på en datamodell som inte innehåller det här streckkodsvärdet. Till exempel ingår inte produkten mineralvatten i rapporten.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Alla/vissa av visualiseringarna i rapporten innehåller inte något värde
Streckkodsvärdet du skannade finns i din modell men alla/vissa av visualiseringarna i rapporten innehåller inte det här värdet och filtrering returnerar därför ett tomt tillstånd. Testa att titta i andra rapportsidor eller redigera dina rapporter i Power BI Desktop så de innehåller det här värdet 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>”Det verkar som om du inte har några rapporter som kan filtreras efter streckkoder.”
Det innebär inte att du inte har några streckkodsaktiverade rapporter. Streckkodsskannern kan bara filtrera rapporter som har en kolumn som har markerats som **streckkod**.  

Kontrollera att du eller rapportens ägare har taggat en kolumn som **streckkod** i Power BI Desktop. Läs mer om att [tagga ett streckkodsfält i Power BI Desktop](../../desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>”Det gick inte att filtrera rapporten – det verkar som att den här streckkoden inte finns i rapportdata.”
Rapporten du valt att filtrera, baseras på en datamodell som inte innehåller det här streckkodsvärdet. Till exempel ingår inte produkten mineralvatten i rapporten. Du kan skanna en annan produkt, välja en annan rapport (om det finns fler än en rapport) eller visa rapporten ofiltrerad. 

## <a name="next-steps"></a>Nästa steg
* [Tagga ett streckkodsfält i Power BI Desktop](../../desktop-mobile-barcodes.md)
* [Paneler på instrumentpanelen i Power BI](../end-user-tiles.md)
* [Instrumentpaneler i Power BI](../end-user-dashboards.md)

