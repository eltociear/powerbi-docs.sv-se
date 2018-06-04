---
title: Använd numeriska intervallutsnitt i Power BI Desktop
description: Lär dig hur du använder ett utsnitt för att begränsa till numeriska intervall i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1e380a6821db7207d14e719fa5e070af38196b97
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34286944"
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Använd numeriska intervallutsnitt i Power BI Desktop
Med **numeriska intervallutsnitt** kan du använda alla typer av filter på en numerisk kolumn i datamodellen. Du kan välja att filtrera **mellan** siffror som är **mindre än eller lika** med ett tal eller **större än eller lika** med ett tal. Detta kan låta enkelt men det är ett kraftfullt sätt att filtrera dina data.

![Visuellt objekt med numeriskt intervallutsnitt](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="using-the-numeric-range-slicer"></a>Använda numeriskt intervallutsnitt
Du kan använda det numeriska intervallutsnittet precis som andra utsnitt. Skapa ett **utsnitt** för rapporten och välj sedan ett numeriskt värde för värdet **Fält**. I följande bild har fältet *LineTotal* markerats.

![Skapa ett numeriskt intervallutsnitt](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Välj nedåtpilslänken i det övre högra hörnet på det **numeriska intervallutsnittet** för att visa en meny.

![Meny för numeriskt intervallutsnitt](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

För det numeriska intervallet kan du välja följande tre alternativ:

* Mellan
* Mindre än eller lika med
* Större än eller lika med

När du väljer **Mellan** på menyn visas ett skjutreglage för att filtrera numeriska värden som faller mellan dessa siffror. Förutom att använda skjutreglaget kan du klicka på någon ruta och skriva in värdena. Det här är praktiskt när du vill använda specifika tal men skjutreglagets kornighet gör det svårt att identifiera ett exakt värde.

I följande bild filtreras rapportsidan för *LineTotal* i intervallet 2 500,00 till 6 000,00.

![Numeriskt intervallutsnitt med Mellan](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

När vi väljer **mindre än eller lika med** försvinner den vänstra (lägre värde) referensen för skjutreglaget och vi kan bara justera den övre gränsen för skjutreglaget. I följande bild ställer vi in max för skjutreglaget på 5928,19.

![Numeriskt intervallutsnitt med Mindre än](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Till sist väljer vi **Större än eller lika med** så att den högra (större) referensen försvinner och vi kan justera det lägre värdet som på följande bild. Nu visas enbart objekt med ett *LineTotal* som är större än eller lika med 4902,99 i den visuella informationen på sidan.

![Numeriskt intervallutsnitt med Större än](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Fäst till heltal med utsnitt med numeriska intervall

Ett numeriskt intervallutsnitt fästs till heltal såvida det inte är ett decimalintervall. Detta gör att ditt utsnitt korrekt justeras som heltal. 


## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Följande begränsningar och överväganden kan användas för utsnittet **numeriskt intervall**:

* Utsnittet **numeriska intervall** filtrerar för närvarande varje underliggande rad i data, inte vilket aggregerat värde som helst. Till exempel, om fältet *Beloppet* används, filtreras varje transaktion som bygger på *Säljbelopp*, och inte summan av *Säljbelopp* för varje datapunkt i det visuella objektet.
* Det fungerar för närvarande inte med mått.
