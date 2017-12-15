---
title: "Ändra hur visuella objekt interagerar i en rapport"
description: "Dokumentation för hur du ställer in visuella interaktioner i en Microsoft Power BI-rapport."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 126bd40e98a88138a2732155f9792d65666e52c7
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Visualiseringsinteraktioner i en Power BI-rapport
Som standard kan visualiseringar på en rapportsida användas för korsfilter och korsmarkeringar i andra visualiseringar på sidan.
Du kan till exempel välja ett tillstånd i en kartvisualisering som visar kolumndiagrammet och filtrerar linjediagrammet till de data som gäller för detta tillstånd.
Se [Om filtrering och markering](power-bi-reports-filters-and-highlighting.md).

Du kan ändra den här standardfunktionen med kontrollen **Visuell interaktion**. Visuella interaktioner är endast tillgängliga i [redigeringsvyn](service-interact-with-a-report-in-editing-view.md). Om en rapport har delats med dig har du inte åtkomst till visuella interaktioner.

> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visualiseringar.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Välj en visualisering för att aktivera den.  
2. Aktivera **Visuella interaktioner** genom att välja det i det översta menyfältet. Lägg märke till ikonerna för filter och markering som visas när du hovrar över andra visualiseringar på rapportsidan.
   
    ![](media/service-reports-visual-interactions/pbi-visual-interaction-icon.png)
3. Bestäm vilken effekt den valda visualiseringen ska ha på de andra visualiseringarna.  
   
   * Om den ska korsfiltrera den andra visualiseringen väljer du ikonen **Filter**![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Om den ska korsmarkera visualiseringen väljer du ikonen **Markera**![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Om den inte ska ha någon effekt väljer du ikonen **Ingen inverkan**![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).
4. Du kan också upprepa detta för alla andra visualiseringar på rapportsidan.

### <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](power-bi-how-to-report-filter.md)

[Filtrera och markera i rapporter](power-bi-reports-filters-and-highlighting.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

