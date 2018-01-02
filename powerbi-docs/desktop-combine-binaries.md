---
title: "Kombinera binärfiler i Power BI Desktop"
description: "Kombinera binära datakällor enkelt i Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 0909056569bb353a720ddd4e8563a37542b90cca
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="combine-binaries-in-power-bi-desktop"></a>Kombinera binärfiler i Power BI Desktop
Ett kraftfullt sätt att importera data till **Power BI Desktop** är att kombinera flera filer som har samma schema i en logisk tabell. I och med versionen av **Power BI Desktop** från november 2016 (och senare versioner) har den här bekväma och populära metoden blivit ännu enklare och omfattande, vilket beskrivs i den här artikeln.

Om du vill börja kombinera binärfiler från samma mapp väljer du **Hämta data > Arkiv > Mapp**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-binaries-behavior"></a>Beteende för tidigare kombinerade binärfiler
I versionen **Power BI Desktop** före November 2016 kunde du kombinera vissa filtyper med omvandlingen **kombinera binärfiler**, men det fanns vissa begränsningar:

* Transformationer beaktades inte för varje enskild fil innan de komprimerades i en tabell. Av den anledningen var du ofta tvungen att kombinera filer och därefter filtrera ut *rubrikvärden* genom att filtrera rader som del av redigeringsprocessen.
* Transformationen **Kombinera binärfiler** fungerade endast för *text-* eller *CSV*-filer och fungerade inte på andra filformat som stöds, till exempel Excel-arbetsböcker och JSON-filer.

Kunderna har begärt en mer intuitiv användning av åtgärden **Kombinera binärfiler**, så vi har förbättrat transformationen.

## <a name="current-combine-binaries-behavior"></a>Den aktuella versionen av kombinera binärfiler
**Power BI Desktop** hanterar nu **Kombinera binärfiler** mer effektivt. Du startar genom att välja **Kombinera binärfiler**, antingen från den **Start**-menyflik i **frågeredigeraren**, eller från själva kolumnen.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

Transformeringen **kombinera binärfiler** fungerar nu på följande sätt:

* Transformeringen **kombinera binärfiler** analyserar varje indatafil och avgör rätt filformat att använda, till exempel *text*, *Excel-arbetsbok* eller *JSON*-fil.
* Med transformeringen kan du välja ett specifikt objekt att extrahera från den första filen, till exempel en *Excel-arbetsbok*.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* **Kombinera binärfiler** gör följande automatiskt:
  
  * Den skapar en exempelfråga som utför alla nödvändiga uppackningssteg i en enda fil.
  * Den skapar en *funktionsfråga* som organiserar parametrar i filen/binära indata i *exempelfrågan*. Exempelfrågan och funktionsfrågan är kopplade, vilket innebär att ändringar i exempelfrågan reflekteras i funktionsfrågan.
  * Den tillämpar *funktionsfrågan* på den ursprungliga frågan med binärfilerna för indata (till exempel *mappen* fråga). Funktionsfrågan tillämpas för binära inmatningar på varje rad och expanderar resulterande dataextrahering som toppkolumner.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Med det nya beteendet för **kombinera binärfiler** kan du enkelt kombinera alla binärfiler i en angiven mapp så länge de har samma filtyp och struktur (samma kolumner).

Dessutom kan du lätt kan använda ytterligare omvandlings- eller extraheringssteg genom att ändra den automatiskt skapade *exempelfrågan*, utan att behöva bekymra dig om att ändra eller skapa ytterligare steg i *funktionsfrågan*. Ändringar i *exempelfrågan* skapas automatiskt i den länkade *funktionsfrågan*.

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till CSV-filer i Power BI Desktop](desktop-connect-csv.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

