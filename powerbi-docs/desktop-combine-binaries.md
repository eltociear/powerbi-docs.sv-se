---
title: Kombinera filer (binära) i Power BI Desktop
description: Kombinera enkelt datakällor med filer (binära) i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161146"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Kombinera filer (binära) i Power BI Desktop

Här är en kraftfull metod för att importera data till **Power BI Desktop**: Om du har flera filer med samma schema kombinerar du dem till en enda logisk tabell. Den här populära tekniken har gjorts bekvämare och mer omfattande.

Om du vill börja kombinera filer från samma mapp väljer du **Hämta data**, väljer **Arkiv** > **Mapp** och väljer sedan **Anslut**.

![Anslut till mappfilen, dialogrutan Hämta data, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Ange mappsökvägen, välj **OK**och välj sedan **Transformera data** för att se mappens filer i Power Query-redigeraren.

## <a name="combine-files-behavior"></a>Beteende för att kombinera filer

Om du vill kombinera binära filer i Power Query-redigeraren väljer du **Innehåll** (den första kolumnetiketten) och väljer **Start** > **Kombinera filer**. Eller så kan du bara välja ikonen **Kombinera filer** bredvid **Innehåll**.

![Kommandot Kombinera filer, Power Query-redigeraren, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

Transformeringen *kombinera filer* fungerar på följande sätt:

* Transformeringen att kombinera filer analyserar varje indatafil för att fastställa vilket filformat som ska använda, till exempel *text*, *Excel-arbetsbok* eller *JSON*-fil.
* Med transformeringen kan du välja ett specifikt objekt att extrahera från den första filen, till exempel en Excel-arbetsbok.
  
  ![Dialogrutan Kombinera filer, Power Query-redigeraren, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* Transformeringen att kombinera filer vidtar sedan följande åtgärder automatiskt:
  
  * Den skapar en exempelfråga som utför alla nödvändiga uppackningssteg i en enda fil.
  * Den skapar en *funktionsfråga* som organiserar parametrar i filen/binära indata i *exempelfrågan*. Exempelfrågan och funktionsfrågan är kopplade, vilket innebär att ändringar i exempelfrågan reflekteras i funktionsfrågan.
  * Använder *funktionsfrågan* till den ursprungliga frågan med inmatade binärfiler, till exempel *Mapp*-frågan. Den använder funktionsfrågan för binära indata på varje rad och utökar sedan den resulterande dataextraheringen som kolumner på den översta nivån.

    ![Resultat av transformeringen att kombinera filer, Power Query-redigeraren, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Omfattningen av ditt val i en Excel-arbetsbok påverkar beteendet för att kombinera binärfiler. Du kan till exempel välja ett specifikt kalkylblad för att kombinera det kalkylbladet eller välja roten för att kombinera den fullständiga filen. När du väljer en mapp kombineras filerna som hittas i den mappen. 

Med beteendet för kombinera filer kan du enkelt kombinera alla filer i en angiven mapp om de har samma filtyp och struktur (t.ex. samma kolumner).

Dessutom kan du lätt kan använda ytterligare omvandlings- eller extraheringssteg genom att ändra den automatiskt skapade exempelfrågan, utan att behöva bekymra dig om att ändra eller skapa ytterligare steg i funktionsfrågan. Ändringar i exempelfrågan skapas automatiskt i den länkade funktionsfrågan.

## <a name="next-steps"></a>Nästa steg

Du kan ansluta till en mängd olika typer av data med Power BI Desktop. Mer information om datakällor finns i följande resurser:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till CSV-filer i Power BI Desktop](desktop-connect-csv.md)
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
