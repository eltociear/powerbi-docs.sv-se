---
title: Köra R-skript i Power BI Desktop
description: Köra R-skript i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 188669525a210afc516cc9740d5d7e7c5682ea93
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514715"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Kör R-skript i Power BI Desktop
Du kan köra R-skript direkt i **Power BI Desktop** och importera de resulterande datauppsättningarna i en Power BI Desktop-datamodell.

## <a name="install-r"></a>Installera R
För att köra R-skript i Power BI Desktop måste du installera **R** på den lokala datorn. Du kan hämta och installera **R** kostnadsfritt från flera platser, inklusive [nedladdningssidan för Revolution Open](https://mran.revolutionanalytics.com/download/) och [CRAN Repository](https://cran.r-project.org/bin/windows/base/). Den aktuella versionen av R-skript i Power BI Desktop stöder Unicode-tecken som blanksteg (tomma tecken) i installationssökvägen.

## <a name="run-r-scripts"></a>Kör R-skript
Du kan köra R-skript och skapa en datamodell där du kan skapa rapporter och dela dem på Power BI-tjänsten med några steg i Power BI Desktop. R-skript i Power BI Desktop stöder nu talformat som innehåller decimaler (.) eller kommatecken (,).

### <a name="prepare-an-r-script"></a>Förbereda ett R-skript
Om du vill köra ett R-skript i Power BI Desktop, skapa skriptet i din lokala R-utvecklingsmiljö och kontrollera att den har körts.

Kontrollera att skriptet har körts i en ny och oförändrad arbetsyta för att köra skriptet i Power BI Desktop. Det innebär att alla paket och beroenden måste läsas in och köras uttryckligen. Du kan använda *source()* för att köra beroende skript.

När du förbereder och kör ett R-skript i Power BI Desktop, finns det några begränsningar:

* Endast dataramar importeras, se till att de data som du vill importera i Power BI representeras i en dataram
* Kolumner som har skrivits som komplexa eller vektor importeras inte och ersätts med felvärden i den skapade tabellen
* Värden som saknas översätts till NULL-värden i Power BI Desktop
* Alla R-skript som körs längre än 30 minuters avbryts
* Interaktiva anrop i R-skriptet som väntar på indata från användaren avbryter körningen av skriptet
* När du ställer in arbetskatalogen i R-skriptet *måste* du definiera en fullständig sökväg till arbetskatalogen i stället för en relativ sökväg

### <a name="run-your-r-script-and-import-data"></a>Kör R-skriptet och importera data
1. Anslutningsappen för R-skript i Power BI Desktop finns i **Hämta data**. Om du vill köra R-skriptet väljer du **Hämta data &gt; Mer...** och sedan **Övrigt &gt; R-skript** enligt följande bild:
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Om R har installerats på den lokala datorn, väljs den senast installerade versionen som R-motor. Det är bara att kopiera skriptet i skriptfönstret och välja **OK**.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Om R inte har installerats, eller inte kan identifieras, eller om det finns flera installationer på din lokala dator, expandera **R installationsinställningar** för att visa installationsalternativ, eller välj på vilken installation du vill köra R-skriptet.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Om R har installerats och inte identifierats kan du uttryckligen ange dess plats i textrutan som visas när du expanderar **R-installationsinställningar**. I bilden ovan, anges sökvägen *C:\Program Files\R\R-3.2.0* uttryckligen i textrutan.
   
   Inställningar för R finns centralt i avsnittet R-skript i dialogrutan Alternativ. Välj **Arkiv > Alternativ och inställningar** och sedan **Alternativ > R-skriptning** för att ange dina installationsinställningar för R. Om det finns flera installationer av R visas en rullgardinsmeny där du kan välja vilken installation du vill använda.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Välj **OK** att köra R-skriptet. När skriptet har körts kan du välja vilka resulterande dataramar du vill lägga till i Power BI-modellen.

### <a name="refresh"></a>Uppdatera
Du kan uppdatera ett R-skript i Power BI Desktop. När du uppdaterar ett R-skript, körs Power BI Desktop R-skriptet igen i Power BI Desktop-miljön.

## <a name="next-steps"></a>Nästa steg
Ta en titt på följande extra information om R i Power BI.

* [Skapa visuella R-objekt i Power BI Desktop](desktop-r-visuals.md)
* [Använd en extern R IDE med Power BI](desktop-r-ide.md)

