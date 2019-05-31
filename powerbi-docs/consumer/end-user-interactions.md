---
title: Förstå hur visuella objekt interagerar i en rapport
description: Dokumentation för Power BI-slutanvändare som förklarar hur visuella objekt interagerar på en rapportsida.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413163"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hur visuella objekt korsfiltrerar varandra i en Power BI-rapport
En av de viktigaste funktionerna i Power BI är det sätt på vilket alla visuella objekt på en rapportsida är sammankopplade. Om du väljer en datapunkt på ett av de visuella objekten kan alla andra visuella objekt på sidan som innehåller dessa data ändras, baserat på det valet. 

![video med interaktion av visuella objekt](media/end-user-interactions/interactions.gif)

Som standard, väljer en datapunkt i en visualisering på en rapportsida att korsfiltrera, korsmarkering, och öka detaljnivån i andra visualiseringar på sidan. 

Detta kan vara användbart att identifiera hur ett värde i dina data som bidrar till en annan. Till exempel att välja segmentet i diagrammet, visar bidrag från segmentet i varje kolumn i totalt antal enheter efter månad diagram och den har filtrerats linjediagrammet till höger.

![Bild av visuella objekt interagerar](media/end-user-interactions/power-bi-interactions.png)

Se [Om filtrering och markering](../power-bi-reports-filters-and-highlighting.md). 

Exakt hur visuella objekt på en sida interagerar anges av rapport-*designern*. Designers har alternativ för att aktivera eller inaktivera visuella interaktioner och att ändra standardbeteenden för korsfiltrering, korsmarkering och granskning. 
  
> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visualiseringar.  

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- Om din rapport har en visualisering som stöder [Detaljgranskning](../power-bi-visualization-drill-down.md), som standard att gå en visualisering har ingen inverkan på de övriga visualiseringarna på rapportsidan.     
- Om du använder visualA för att interagera med visualB tillämpas visuell nivå filter från visualA på visualB.

## <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](../power-bi-how-to-report-filter.md)
