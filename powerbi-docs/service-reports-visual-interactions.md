---
title: Ändra hur visuella objekt interagerar i en rapport
description: Dokumentation om hur du ställer in visuella interaktioner i en Microsoft Power BI-tjänstrapport och en Power BI Desktop-rapport.
author: mihart
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/11/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 2485d9120b10b41d193189de383a1a92b15378d5
ms.sourcegitcommit: 0d7ad791a2d2bef45d5d60e38e0af4c9fc22187b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74011055"
---
# <a name="change-how-visuals-interact-in-a-power-bi-report"></a>Ändra hur visuella objekt interagerar i en Power BI-rapport
Om du har redigeringsbehörighet för en rapport kan du använda **Visuella interaktioner** för att ändra hur visualiseringar på en rapportsida påverkar varandra. 

## <a name="introduction-to-visual-interactions"></a>Introduktion till visuella interaktioner
Som standard kan visualiseringar på en rapportsida användas för korsfilter och korsmarkeringar i andra visualiseringar på sidan.
Du kan till exempel välja ett tillstånd i en kartvisualisering som visar kolumndiagrammet och filtrerar linjediagrammet till de data som gäller för detta tillstånd.
Se [Om filtrering och markering](power-bi-reports-filters-and-highlighting.md). Om du har en visualisering som stöder [detaljgranskning](consumer/end-user-drill.md) så har detaljgranskning av en visualisering som standard ingen inverkan på andra visualiseringar på rapportsidan. Båda de här standardbeteendena kan åsidosättas och interaktioner kan anges per visualisering.

Den här artikeln visar hur du använder **visuella interaktioner** i Power BI Desktop. Processen är likadan i Power BI-tjänstens [Redigeringsvy](service-interact-with-a-report-in-editing-view.md). Om du bara har åtkomst till läsvyn eller om rapporten har delats med dig, kan du inte ändra inställningarna för visuella interaktioner.

Termerna *korsfiltrera* och *korsmarkera* används för att särskilja det beteende som beskrivs här från vad som händer när du använder fönstret **Filter** till att *filtrera* och *markera* visualiseringar.  

> [!NOTE]
> I den här videon används äldre versioner av Power BI Desktop och Power BI-tjänsten. 
>
>

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


## <a name="enable-the-visual-interaction-controls"></a>Aktivera kontroller för visuell interaktion
Om du har redigeringsbehörighet i en rapport kan du aktivera de visuella interaktionskontrollerna och sedan anpassa hur visualiseringarna på rapportsidan filtrerar och markerar varandra. 

1. Välj en visualisering för att aktivera den.  
2. Visa alternativen för **Visuella interaktioner**.
    

    - På skrivbordet väljer du **Format > Interaktioner**.

        ![välj Format och Interaktioner](media/service-reports-visual-interactions/power-bi-interaction.png)

    - Öppna rapporten i redigeringsvyn i Power BI-tjänsten och välj listrutan i rapportens menyrad.

        ![Listrutan Visuella interaktioner](media/service-reports-visual-interactions/power-bi-service.png)

3. Välj **Redigera interaktioner** för att se kontrollerna för visualiseringsinteraktion. Power BI lägger till ikoner för filtrering och markering i alla andra visualiseringar på rapportsidan. Nu kan du ändra hur den valda visualiseringen interagerar med andra visualiseringar på rapportsidan.
   
    ![rapport med Visuella interaktioner aktiverat](media/service-reports-visual-interactions/power-bi-turn-on.png)


## <a name="change-the-interaction-behavior"></a>Ändra interaktionsbeteende
Bekanta dig med hur visualiseringarna interagerar genom att välja en visualisering i taget på rapportsidan.  Välj en datapunkt, en stapel eller en figur och se hur det påverkar de andra visualiseringarna. Om du inte får önskat beteende kan du ändra interaktionerna. Ändringarna sparas i rapporten så du och dina rapportanvändare får samma visuella interaktionsupplevelse.


Bestäm vilken effekt den **valda visualiseringen** ska ha på de andra visualiseringarna.  Du kan också upprepa detta för alla andra visualiseringar på rapportsidan.
   
   * Om du vill korsfiltrera visualiseringen väljer du ikonen **Filter** ![filterikon](media/service-reports-visual-interactions/power-bi-filter-icon.png).
   * Om du vill korsmarkera visualiseringen väljer du ikonen **Markera** ![ikonen Markera](media/service-reports-visual-interactions/power-bi-highlight-icon.png).
   * Om den inte ska ha någon effekt väljer du ikonen **Ingen inverkan** ![ikonen Ingen inverkan](media/service-reports-visual-interactions/power-bi-no-impact.png).

## <a name="change-the-interactions-of-drillable-visualizations"></a>Ändra interaktioner för visualiseringar som går att detaljgranska
[Vissa Power BI-visualiseringar kan detaljgranskas](consumer/end-user-drill.md). När du ökar detaljnivån i en visualisering påverkar det som standard inte andra visualiseringar på rapportsidan. Men du kan ändra detta. 

1. Välj det visuella objektet för att aktivera det. 

> [!TIP]
> Prova själv med [PBIX-filen Exempel på personalfrågor](https://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix). Där finns ett stapeldiagram med ökad detaljnivå på fliken **Nya anställningar**.
>


2. I menyraden väljer du **Format** > **Att gå in på detalj filtrerar andra visuella objekt**.  Nu när du ökar detaljnivån i en visualisering ändras de andra visualiseringarna på rapportsidan för att återspegla din aktuella detaljgranskningsmarkering. 

    ![aktivera att gå in på detalj filtrerar andra visuella objekt](media/service-reports-visual-interactions/power-bi-drill.png).
    
## <a name="next-steps"></a>Nästa steg
[Filtrera och markera i Power BI-rapporter](power-bi-reports-filters-and-highlighting.md)