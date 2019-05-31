---
title: Ändra hur visuella objekt interagerar i en rapport
description: Dokumentation om hur du ställer in visuella interaktioner i en Microsoft Power BI-tjänstrapport och en Power BI Desktop-rapport.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/11/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 6f739992ed282ada92b1049df09a8b5d4b3938a9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406035"
---
# <a name="change-how-visuals-interact-in-a-power-bi-report"></a>Ändra hur visuella objekt interagerar i en Power BI-rapport
Om du har redigeringsbehörighet för en rapport kan du använda **Visuella interaktioner** för att ändra hur visualiseringar på en rapportsida påverkar varandra. 

Som standard kan visualiseringar på en rapportsida användas för korsfilter och korsmarkeringar i andra visualiseringar på sidan.
Du kan till exempel välja ett tillstånd i en kartvisualisering som visar kolumndiagrammet och filtrerar linjediagrammet till de data som gäller för detta tillstånd.
Se [Om filtrering och markering](power-bi-reports-filters-and-highlighting.md). Om du har en visualisering som stöder [detaljgranskning](consumer/end-user-drill.md) så har detaljgranskning av en visualisering som standard ingen inverkan på andra visualiseringar på rapportsidan. Båda de här standardbeteendena kan åsidosättas och interaktioner kan anges per visualisering.

Den här artikeln visar hur du använder **Visuella interaktioner** i Power BI-tjänsten [Redigeringsvyn](service-interact-with-a-report-in-editing-view.md) och i Power BI Desktop. Om en rapport har delats med dig kan du inte ändra inställningarna för visuella interaktioner.

> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visualiseringar.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Välj en visualisering för att aktivera den.  
2. Visa alternativen för **Visuella interaktioner**.
    - Välj listrutan på menyraden för rapportering i Power BI-tjänsten.

       ![Listrutan Visuella interaktioner](media/service-reports-visual-interactions/power-bi-visual-interaction.png)

    - På skrivbordet väljer du **Format > Interaktioner**.

        ![välj Format och Interaktioner](media/service-reports-visual-interactions/pbi-visual-interaction-desktop.png)

3. Välj **Redigera interaktioner** för att aktivera kontroller för visualiseringsinteraktioner. Power BI lägger till ikoner för korsfiltrering och korsmarkering i alla andra visualiseringar på rapportsidan.
   
    ![rapport med Visuella interaktioner aktiverat](media/service-reports-visual-interactions/power-bi-icons-on.png)
3. Bestäm vilken effekt den valda visualiseringen ska ha på de andra visualiseringarna.  Du kan också upprepa detta för alla andra visualiseringar på rapportsidan.
   
   * Om du vill korsfiltrera visualiseringen väljer du ikonen **Filter** ![filterikon](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Om du vill korsmarkera visualiseringen väljer du ikonen **Markera** ![ikonen Markera](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Om den inte ska ha någon effekt väljer du ikonen **Ingen inverkan** ![ikonen Ingen inverkan](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).

4. Om du vill aktivera detaljgranskningskontroller väljer du **Att gå in på detalj filtrerar andra visuella objekt**.  Nu när du ökar detaljnivån i en visualisering ändras de andra visualiseringarna på rapportsidan för att återspegla din aktuella detaljgranskningsmarkering. 

   ![video om aktivering av detaljnivåkontroller](media/service-reports-visual-interactions/drill2.gif)

