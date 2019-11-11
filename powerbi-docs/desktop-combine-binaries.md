---
title: Kombinera filer (binära) i Power BI Desktop
description: Kombinera enkelt datakällor med filer (binära) i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 03a6e044a55613d40a1cf195d6a0ad3b44a9f012
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876560"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Kombinera filer (binära) i Power BI Desktop
Ett kraftfullt sätt att importera data till **Power BI Desktop** är att kombinera flera filer som har samma schema i en logisk tabell. Den här bekväma och populära metoden blivit ännu enklare och omfattande, vilket beskrivs i den här artikeln.

Om du vill börja kombinera filer från samma mapp väljer du **Hämta data > Arkiv > Mapp**.

![](media/desktop-combine-binaries/combine-binaries_1.png)


## <a name="combine-files-behavior"></a>Beteende för att kombinera filer
Du kan **kombinera filer (binärfiler)** genom att välja **kombinera filer**, på menyfliken **Start** i **Frågeredigeraren** eller i själva kolumnen.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

Transformeringen **kombinera filer** fungerar på följande sätt:

* Transformeringen **kombinera filer** analyserar varje indatafil och avgör rätt filformat att använda, till exempel *text*, *Excel-arbetsbok* eller *JSON*-fil.
* Med transformeringen kan du välja ett specifikt objekt att extrahera från den första filen, till exempel en *Excel-arbetsbok*.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* **Kombinera filer** utför automatiskt följande frågor:
  
  * Den skapar en exempelfråga som utför alla nödvändiga uppackningssteg i en enda fil.
  * Den skapar en *funktionsfråga* som organiserar parametrar i filen/binära indata i *exempelfrågan*. Exempelfrågan och funktionsfrågan är kopplade, vilket innebär att ändringar i exempelfrågan reflekteras i funktionsfrågan.
  * Den tillämpar *funktionsfrågan* på den ursprungliga frågan med binärfilerna för indata (till exempel *mappen* fråga). Funktionsfrågan tillämpas för binära inmatningar på varje rad och expanderar resulterande dataextrahering som toppkolumner.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Omfattningen av ditt val i en Excel-arbetsbok påverkar beteendet för att kombinera binärfiler. Du kan till exempel välja ett specifikt kalkylblad för att kombinera det kalkylbladet eller välja roten för att kombinera den fullständiga filen. När du väljer en mapp kombineras filerna som hittas i den mappen. 


Med beteendet för **kombinera filer** kan du enkelt kombinera alla filer i en angiven mapp så länge de har samma filtyp och struktur (t.ex. samma kolumner).

Dessutom kan du lätt kan använda ytterligare omvandlings- eller extraheringssteg genom att ändra den automatiskt skapade *exempelfrågan*, utan att behöva bekymra dig om att ändra eller skapa ytterligare steg i *funktionsfrågan*. Ändringar i *exempelfrågan* skapas automatiskt i den länkade *funktionsfrågan*.

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till CSV-filer i Power BI Desktop](desktop-connect-csv.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

