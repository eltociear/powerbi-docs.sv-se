---
title: Förstå hur visuella objekt interagerar i en rapport
description: Dokumentation för Power BI-slutanvändare som förklarar hur visuella objekt interagerar på en rapportsida.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 406f1f6428d5ce26401720220eaffe32314a9bbd
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280430"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Hur visuella objekt korsfiltrerar varandra i en Power BI-rapport
En av de viktigaste funktionerna i Power BI är det sätt på vilket alla visuella objekt på en rapportsida är sammankopplade. Om du väljer en datapunkt på ett av de visuella objekten kan alla andra visuella objekt på sidan som innehåller dessa data ändras, baserat på det valet. 

![video med interaktion av visuella objekt](media/end-user-interactions/interactions.gif)

Som standard kan visualiseringar på en rapportsida användas för korsfilter, korsmarkeringar och granskning i andra visualiseringar på sidan. Du kan till exempel välja ett tillstånd i en kartvisualisering som visar kolumndiagrammet och filtrerar linjediagrammet till de data som gäller för detta tillstånd.

Se [Om filtrering och markering](../power-bi-reports-filters-and-highlighting.md). Om du har en visualisering som stöder [detaljgranskning](../power-bi-visualization-drill-down.md) så har detaljgranskning av en visualisering som standard ingen inverkan på andra visualiseringar på rapportsidan. 

Exakt hur visuella objekt på en sida interagerar anges av rapport-*designern*. Designers har alternativ för att aktivera eller inaktivera visuella interaktioner och att ändra standardbeteenden för korsfiltrering, korsmarkering och granskning.
  
> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visualiseringar.  

### <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](../power-bi-how-to-report-filter.md)
