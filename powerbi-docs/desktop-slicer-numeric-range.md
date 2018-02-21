---
title: "Använd numeriska intervallutsnitt i Power BI Desktop"
description: "Lär dig hur du använder ett utsnitt för att begränsa till numeriska intervall i Power BI Desktop"
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
ms.date: 02/05/2018
ms.author: davidi
ms.openlocfilehash: 6d63236254906619f7244db9f57af162a19a70d6
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Använd numeriska intervallutsnitt i Power BI Desktop
Med **numeriska intervallutsnitt** kan du använda alla typer av filter på en numerisk kolumn i datamodellen. Du kan välja att filtrera **mellan** siffror som är **mindre än eller lika** med ett tal eller **större än eller lika** med ett tal. Detta kan låta enkelt men det är ett kraftfullt sätt att filtrera dina data.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>Använda numeriskt intervallutsnitt
Du kan använda det numeriska intervallutsnittet precis som andra utsnitt. Skapa ett **utsnitt** för rapporten och välj sedan ett numeriskt värde för värdet **Fält**. I följande bild har *Enhetspris* markerats.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

Välj cirkumflex i det övre högra hörnet på **utsnittet numeriskt intervall** för att visa en meny.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

För det numeriska intervallet kan du välja följande tre alternativ:

* Mellan
* Mindre än eller lika med
* Större än eller lika med

När du väljer **Mellan** på menyn visas ett skjutreglage för att filtrera numeriska värden som faller mellan dessa siffror. Förutom att använda skjutreglaget kan du klicka på någon ruta och skriva in värdena. Detta är praktiskt när du vill använda specifika heltal men skjutreglagets granularitet gör det svårt att identifiera ett exakt värde.

I följande bild, filtreras rapportsidan för *enhetspris* i intervallet 500 till 1 500.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

När vi väljer **mindre än eller lika med** försvinner den vänstra (lägre värde) referensen för skjutreglaget och vi kan bara justera den övre gränsen för skjutreglaget. I följande bild ställer vi in skjutreglaget på 497,17.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

Till sist väljer vi **Större än eller lika med** så att den högra (större) referensen försvinner och vi kan justera det lägre värdet som på följande bild. Nu visas enbart objekt med ett *enhetspris* som är större än eller lika med 750,56 i den visuella informationen på sidan.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer-preview"></a>Fäst till heltal med utsnitt med numeriska intervall (förhandsgranskning)

Från och med lanseringen av **Power BI Desktop** i februari 2018 fixeras dina numeriska intervallutsnitt till heltal. Detta gör att ditt utsnitt korrekt justeras som heltal. Fixering till heltal gäller inte för decimalfilter.


## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Följande begränsningar och överväganden kan användas för utsnittet **numeriskt intervall**

* Utsnittet **numeriska intervall** filtrerar för närvarande varje underliggande rad i data, inte vilket aggregerat värde som helst. Till exempel, om fältet *Beloppet* används, filtreras varje transaktion som bygger på *Säljbelopp*, och inte summan av *Säljbelopp* för varje datapunkt i det visuella objektet.
* Det fungerar för närvarande inte med mått
* För närvarande är utsnittet **numeriska intervall** endast tillgängligt i **Power BI Desktop**. Om en rapport som använder utsnittet **numeriska intervall** publiceras till **Power BI-tjänsten**, kommer filtret fortfarande att användas, men visas som ett utsnitt i listan.

