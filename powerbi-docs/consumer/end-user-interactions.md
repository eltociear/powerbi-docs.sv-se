---
title: Ändra hur visuella objekt interagerar i en rapport
description: Dokumentation om hur du ställer in visuella interaktioner i en Microsoft Power BI-tjänstrapport och en Power BI Desktop-rapport.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: a70d5ac5265f88a6e407815ecb0fb6ac23e24416
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565439"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Visualiseringsinteraktioner i en Power BI-rapport
Om du har redigeringsbehörighet för en rapport kan du använda **Visuella interaktioner** för att ändra hur visualiseringar på en rapportsida påverkar varandra. 

Som standard kan visualiseringar på en rapportsida användas för korsfilter och korsmarkeringar i andra visualiseringar på sidan.
Du kan till exempel välja ett tillstånd i en kartvisualisering som visar kolumndiagrammet och filtrerar linjediagrammet till de data som gäller för detta tillstånd.
Se [Om filtrering och markering](../power-bi-reports-filters-and-highlighting.md). Om du har en visualisering som stöder [detaljgranskning](end-user-drill.md) så har detaljgranskning av en visualisering som standard ingen inverkan på andra visualiseringar på rapportsidan. Båda de här standardbeteendena kan åsidosättas och interaktioner kan anges per visualisering.

Den här artikeln visar hur du använder **Visuella interaktioner** i Power BI-tjänsten [Redigeringsvyn](../service-interact-with-a-report-in-editing-view.md) och i Power BI Desktop. Om en rapport har delats med dig kan du inte ändra inställningarna för visuella interaktioner.

> [!NOTE]
> Termerna *Korsfilter* och *Korsmarkering* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att filtrera och markera visualiseringar.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Välj en visualisering för att aktivera den.  
2. Visa alternativen för **Visuella interaktioner**.
    - Välj listrutan på menyraden för rapportering i Power BI-tjänsten.

       ![Listrutan Visuella interaktioner](./media/end-user-interactions/power-bi-visual-interaction.png)

    - På skrivbordet väljer du **Format > Interaktioner**.

        ![välj Format och Interaktioner](./media/end-user-interactions/pbi-visual-interaction-desktop.png)

3. Välj **Redigera interaktioner** för att aktivera kontroller för visualiseringsinteraktioner. Power BI lägger till ikoner för korsfiltrering och korsmarkering i alla andra visualiseringar på rapportsidan.
   
    ![rapport med Visuella interaktioner aktiverat](./media/end-user-interactions/power-bi-icons-on.png)
3. Bestäm vilken effekt den valda visualiseringen ska ha på de andra visualiseringarna.  Du kan också upprepa detta för alla andra visualiseringar på rapportsidan.
   
   * Om du vill korsfiltrera visualiseringen väljer du ikonen **Filter** ![filterikon](./media/end-user-interactions/pbi-filter-icon-outlined.png).
   * Om du vill korsmarkera visualiseringen väljer du ikonen **Markera** ![ikonen Markera](./media/end-user-interactions/pbi-highlight-icon-outlined.png).
   * Om den inte ska ha någon effekt väljer du ikonen **Ingen inverkan** ![ikonen Ingen inverkan](./media/end-user-interactions/pbi-noimpact-icon-outlined.png).

4. Om du vill aktivera detaljgranskningskontroller väljer du **Att gå in på detalj filtrerar andra visuella objekt**.  Nu när du ökar detaljnivån i en visualisering ändras de andra visualiseringarna på rapportsidan för att återspegla din aktuella detaljgranskningsmarkering. 

   ![video om aktivering av detaljnivåkontroller](./media/end-user-interactions/drill2.gif)

### <a name="next-steps"></a>Nästa steg
[Så här använder du rapportfilter](end-user-report-filter.md)

[Filtrera och markera i rapporter](../power-bi-reports-filters-and-highlighting.md)

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

