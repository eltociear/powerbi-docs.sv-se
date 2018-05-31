---
title: Grundläggande ytdiagram
description: Grundläggande ytdiagram.
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 62d518b923d541ee937f485da946ae08b20fa386
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33811815"
---
# <a name="basic-area-chart"></a>Grundläggande ytdiagram
Det grundläggande ytdiagrammet (även känt som överlappande områdesdiagram) baseras på linjediagrammet. Området mellan axel och linje fylls med färger för att illustrera volym. 

Ytdiagrammet framhäver omfattningen av förändring över tid och kan användas för att uppmärksamma totalvärdet över en trend. Data som representerar vinst över tid kan till exempel ritas i ett ytdiagram för att betona den totala vinsten.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>När ska du använda ett grundläggande ytdiagram
Grundläggande ytdiagram är ett bra val:

* för att se och jämföra volymtrenden över tidsserier 
* för enskilda serier som representerar en fysiskt kvantifierbar uppsättning

### <a name="prerequisites"></a>Förutsättningar
 - Power BI-tjänsten
 - Exempel på detaljhandelsanalys

Om du vill följa med, loggar du in i Power BI och väljer **Hämta data\> Exempel \> Exempel på detaljhandelsanalys > Anslut** och välj **Gå till instrumentpanel**. 

## <a name="create-a-basic-area-chart"></a>Skapa ett grundläggande ytdiagram
 

1. Välj **Totalt antal butiker** från instrumentpanelen ”Exempel på detaljhandelsanalys” för att öppna rapporten ”Exempel på detaljhandelsanalys”.
2. Välj **Redigera rapport** för att öppna rapporten i redigeringsvyn.
3. Lägg till en ny rapportsida genom att välja den gula plus-ikonen (+) längst ned på rapporten.
4. Skapa ett ytdiagram som visar årets försäljning och förra årets försäljning per månad.
   
   a. Från Fält-fönstret, väljer du **Försäljning \> Förra årets försäljning** och **Årets försäljning > Värde**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Omvandla diagrammet till ett grundläggande ytdiagram genom att välja ytdiagramikonen från fönstret Visualiseringar.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Välj **Tid \> Månad** för att lägga till det i **Axel**-brunnen.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Om du vill visa diagrammet efter månad, väljer du ellipserna (övre högra hörnet av visualiseringen) och väljer **sortera efter månad**.

## <a name="highlighting-and-cross-filtering"></a>Markering och korsfiltrering
Information om hur du använder Filter-fönstret finns i [Lägg till ett filter i en rapport](power-bi-report-add-filter.md).

Om du vill fokusera på ett visst område i ditt diagrammet, väljer du det området eller dess översta kant.  Till skillnad från andra visualiseringstyper så korsfiltreras inte andra visualiseringar på rapportsidan om du markerar ett grundläggande ytdiagram och det finns andra visualiseringar på samma sida. Ytdiagram är dock ett mål för korsfiltrering som utlösts av andra visualiseringar på rapportsidan. Läs mer i [Visuella interaktioner i rapporter](service-reports-visual-interactions.md)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* Grundläggande ytdiagram är inte effektiva för att jämföra värden på grund av ocklusion av överlappande områden. Power BI använder genomskinlighet för att ange överlappande områden. Dock fungerar det bara bra med två eller tre olika områden. När du behöver jämföra trender med fler än tre mått, kan du testa att använda linjediagram. När du behöver jämföra volym med fler än tre mått, kan du testa att använda en trädkarta.

## <a name="next-steps"></a>Nästa steg
[Rapporter i Power BI](service-reports.md)  
[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)  
[Power BI – grundläggande begrepp](service-basic-concepts.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

