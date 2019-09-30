---
title: Förstå hur visuella objekt interagerar i en rapport
description: Dokumentation för Power BI-slutanvändare som förklarar hur visuella objekt interagerar på en rapportsida.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256280"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hur visuella objekt korsfiltrerar varandra i en Power BI-rapport
En av de viktigaste funktionerna i Power BI är det sätt på vilket alla visuella objekt på en rapportsida är sammankopplade. Om du väljer en datapunkt på ett av de visuella objekten kan alla andra visuella objekt på sidan som innehåller dessa data ändras, baserat på det valet. 

![video med interaktion av visuella objekt](media/end-user-interactions/interactions.gif)

När en datapunkt väljs i en visualisering på en rapportsida sker som standard korsfiltrering, korsmarkering och detaljgranskning av de andra visualiseringarna på sidan. 

Detta kan vara användbart för att identifiera hur ett värde i dina data bidrar till ett annat. Om du till exempel väljer segmentet Moderering i ringdiagrammet markeras bidraget från det segmentet till varje kolumn i diagrammet Totalt antal enheter efter månad, och linjediagrammet till höger har filtrerats.

![bild med interaktion av visuella objekt](media/end-user-interactions/power-bi-interactions.png)

Se [Om filtrering och markering](../power-bi-reports-filters-and-highlighting.md). 

Exakt hur visuella objekt på en sida interagerar anges av rapport-*designern*. Designers har alternativ för att aktivera eller inaktivera visuella interaktioner och att ändra standardbeteenden för korsfiltrering, korsmarkering och granskning. 
  
> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visualiseringar.  

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- Om din rapport har en visualisering som stöder [detaljgranskning](../power-bi-visualization-drill-down.md) så har detaljgranskning av en visualisering som standard ingen inverkan på andra visualiseringar på rapportsidan.     
- Om du använder visuellt objekt A för att interagera med visuellt objekt B tillämpas filter på visuell nivå från visuellt objekt A på visuellt objekt B.

## <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](../power-bi-how-to-report-filter.md)
