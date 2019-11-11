---
title: Förstå hur visuella objekt interagerar i en rapport
description: Dokumentation för Power BI-slutanvändare som förklarar hur visuella objekt interagerar på en rapportsida.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 28e6cea55b02fabddd0b2f118631a09c0344b66f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863098"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hur visuella objekt korsfiltrerar varandra i en Power BI-rapport
En av de viktigaste funktionerna i Power BI är det sätt på vilket alla visuella objekt på en rapportsida är sammankopplade. Om du väljer en datapunkt på ett av de visuella objekten kan alla andra visuella objekt på sidan som innehåller dessa data ändras, baserat på det valet. 

![video med interaktion av visuella objekt](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Hur visuella objekt interagerar med varandra

När en datapunkt väljs i ett visuellt objekt på en rapportsida sker som standard korsfiltrering eller korsmarkering av de andra visuella objekten på sidan. Exakt hur visuella objekt på en sida interagerar anges av rapport-*designern*. *Designers* har alternativ för att aktivera eller inaktivera visuella interaktioner och att ändra standardbeteenden för korsfiltrering, korsmarkering och [detaljgranskning](end-user-drill.md). 

Om du inte har kommit i kontakt med hierarkier eller granskning tidigare kan du lära dig allt om dem genom att läsa artikeln om [detaljgranskning i Power BI](end-user-drill.md). 

Korsfiltrering och korsmarkering kan vara användbart för att identifiera hur ett värde i dina data bidrar till ett annat. Om du till exempel väljer segmentet Moderering i ringdiagrammet markeras bidraget från det segmentet till varje kolumn i diagrammet Totalt antal enheter efter månad, och linjediagrammet filtreras.

![bild med interaktion av visuella objekt](media/end-user-interactions/power-bi-interactions.png)

Se [Om filtrering och markering](end-user-report-filter.md). 


  
> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visuella objekt.  

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- Om din rapport har ett visuellt objekt som stöder [detaljgranskning](end-user-drill.md) så har detaljgranskning av ett visuellt objekt som standard ingen inverkan på andra visuella objekt på rapportsidan.     
- Om du använder visuellt objekt A för att interagera med visuellt objekt B tillämpas filter på visuell nivå från visuellt objekt A på visuellt objekt B.

## <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](../power-bi-how-to-report-filter.md)
