---
title: Förstå hur visuella objekt interagerar i en rapport
description: Dokumentation för Power BI-slutanvändare som förklarar hur visuella objekt interagerar på en rapportsida.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fb7bf439cdf2f7ebd6058aba6b147f800b9cf258
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79113047"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hur visuella objekt korsfiltrerar varandra i en Power BI-rapport

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

En av de viktigaste funktionerna i Power BI är det sätt på vilket alla visuella objekt på en rapportsida är sammankopplade. Om du väljer en datapunkt på ett av de visuella objekten kan alla andra visuella objekt på sidan som innehåller dessa data ändras, baserat på det valet. 

![video med interaktion av visuella objekt](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Hur visuella objekt interagerar med varandra

När en datapunkt väljs i ett visuellt objekt på en rapportsida sker som standard korsfiltrering eller korsmarkering av de andra visuella objekten på sidan. Exakt hur visuella objekt på en sida interagerar anges av rapport-*designern*. *Designers* har alternativ för att aktivera eller inaktivera visuella interaktioner och att ändra standardbeteenden för korsfiltrering, korsmarkering och [detaljgranskning](end-user-drill.md). 

Om du inte har kommit i kontakt med hierarkier eller granskning tidigare kan du lära dig allt om dem genom att läsa artikeln om [detaljgranskning i Power BI](end-user-drill.md). 

### <a name="cross-filtering-and-cross-highlighting"></a>Korsfiltrering och korsmarkering

Korsfiltrering och korsmarkering kan vara användbart för att identifiera hur ett värde i dina data bidrar till ett annat. Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visuella objekt.  

Vi definierar de här termerna när vi tittar på rapportsidorna nedan. Ringdiagrammet "Total kategorivolym efter segment" har två värden: "Måttlighet" och "Bekvämlighet". 

![Rapportsida](media/end-user-interactions/power-bi-interactions-before.png)

1. Nu ska vi se vad som händer när vi väljer **Måttlighet**.

    ![Rapportsidan efter att segmentet Måttlighet i ringdiagrammet har valts](media/end-user-interactions/power-bi-interactions-after.png)

2. **Korsfiltrering** tar bort data som inte är aktuella. Om du väljer **Måttlighet** i ringdiagrammet korsfiltreras linjediagrammet. Linjediagrammet visar nu endast datapunkter för segmentet Måttlighet. 

3. **Korsmarkering** behåller alla ursprungliga datapunkter men tonar ned den del som inte gäller för ditt val. Om du väljer **Måttlighet** i ringdiagrammet korsmarkeras kolumndiagrammet. Kolumndiagrammet tonar ned alla data som gäller för segmentet Bekvämlighet och markerar alla data som gäller för segmentet Måttlighet. 


## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- Om din rapport har ett visuellt objekt som stöder [detaljgranskning](end-user-drill.md) så har detaljgranskning av ett visuellt objekt som standard ingen inverkan på andra visuella objekt på rapportsidan. Emellertid kan *rapportdesignern* ändra det här beteendet, så kontrollera dina visuella objekt för att se om **filter för utökad detaljnivå för andra visuella objekt** har aktiverats av *rapportdesignern*.
    
- Filter på visuell nivå behålls vid korsfiltrering och korsmarkering av andra visuella objekt på rapportsidan. Om filter på visuell nivå tillämpas på Visuellt objekt A av rapportdesignern eller av dig, och om du använder Visuellt objekt A för att interagera med Visuellt objekt B, tillämpas därför filter på visuell nivå från Visuellt objekt A på Visuellt objekt B.

    ![Rapportsidan efter att segmentet Måttlighet i ringdiagrammet har valts](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](../power-bi-how-to-report-filter.md)    


[Om filtrering och markering](end-user-report-filter.md). 
