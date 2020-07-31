---
title: Dela direkt till Teams från Power BI-tjänsten
description: Du kan dela instrumentpaneler och rapporter i Power BI direkt till Microsoft Teams från Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 6305a41188c4416b62d5432823bb30946e5e524d
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254086"
---
# <a name="share-directly-to-teams-from-the-power-bi-service"></a>Dela direkt till Teams från Power BI-tjänsten

Du kan dela instrumentpaneler, rapporter och visuella objekt i Power BI direkt till Microsoft Teams från Power BI-tjänsten. Med funktionen **Dela till Teams** kan du snabbt starta konversationer när du visar rapporter och instrumentpaneler i Power BI-tjänsten.

Information om hur Power BI och Teams fungerar tillsammans, inklusive vilka krav du måste uppfylla, finns i [Samarbeta i Microsoft Teams med Power BI](service-collaborate-microsoft-teams.md).

## <a name="share-power-bi-content-to-teams"></a>Dela Power BI-innehåll till Teams

Följ dessa steg om du vill dela länkar till rapporter, instrumentpaneler och visuella objekt i Power BI-tjänsten till kanaler och chattar i Microsoft Teams.

1. Välj något av följande alternativ:

   * **Dela till Teams** i åtgärdsfältet för en instrumentpanel eller rapport:

       ![Skärmbild som visar knappen Dela till Teams i åtgärdsfältet.](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Dela till Teams** på snabbmenyn för ett enskilt visuellt objekt:
    
      ![Skärmbild som visar knappen Dela till Teams på snabbmenyn för ett visuellt objekt.](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. I dialogrutan **Dela till Microsoft Teams** väljer du den kanal eller de personer som du vill skicka länken till. Lägg till ett meddelande om du vill. Du kan bli ombedd att logga in på Microsoft Teams först.

    ![Skärmbild som visar dialogrutan Dela till Microsoft Teams med information och ett meddelande.](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. Välj **Dela** för att skicka länken.
    
1. Länken läggs till i befintliga konversationer eller startar en ny chatt.

    ![Skärmbild som visar en Microsoft Teams-konversation med en länk till ett Power BI-objekt.](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. Välj länken för att öppna objektet i Power BI-tjänsten.

1. Om du använde snabbmenyn för ett specifikt visuellt objekt, markeras det visuella objektet när rapporten öppnas.

    ![Skärmbild som visar en öppen Power BI-rapport med ett markerat visuellt objekt.](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>Kända problem och begränsningar

- Användare utan någon Power BI-licens eller behörighet att visa rapporten ser meddelandet Innehållet inte är tillgängligt.
- **Dela till Teams**-knapparna kanske inte fungerar om webbläsaren använder strikta sekretessinställningar. Använd alternativet **Upplever du problem? Försök öppna i ett nytt fönster** om dialogrutan inte öppnas på rätt sätt.
- **Dela till Teams** innehåller inte en länkförhandsgranskning.
- Länkförhandsgranskningar och **Dela till Teams** ger inte användare behörighet att visa objektet. Behörigheter måste hanteras separat.
- Knappen **Dela till Teams** är inte tillgänglig på snabbmenyer för visuella objekt om rapportskaparen väljer inställningen **Av** för **Fler alternativ** för det visuella objektet.
- Läs avsnittet [Kända problem och begränsningar](service-collaborate-microsoft-teams.md#known-issues-and-limitations) i artikeln ”Samarbeta i Microsoft Teams” för information om andra problem.

## <a name="next-steps"></a>Nästa steg

- [Samarbeta i Microsoft Teams med Power BI](service-collaborate-microsoft-teams.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/).
