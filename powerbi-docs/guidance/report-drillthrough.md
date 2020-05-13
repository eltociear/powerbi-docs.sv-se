---
title: Använd detaljerad information för rapportsidor
description: Vägledning för att arbeta med detaljerad information på rapportsidor.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: 853f6d7f5cd6696be55edeea101bc0ca51922ad3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278087"
---
# <a name="use-report-page-drillthrough"></a>Använd detaljerad information för rapportsidor

Den här artikeln är avsedd för rapportförfattare som skapar Power BI-rapporter. Den innehåller förslag och rekommendationer när du skapar [visning av detaljerad information på rapportsidor](../create-reports/desktop-drillthrough.md).

Vi rekommenderar att du utformar dina rapporter så att användare kan följa det här flödet:

1. Visa en rapportsida.
2. Hitta ett visuellt element att analysera mer ingående.
3. Högerklicka på det visuella elementet för att visa mer detaljerad information.
4. Utföra kompletterande analys.
5. Återgå till den ursprungliga rapportsidan.

## <a name="suggestions"></a>Förslag

Vi rekommenderar att du överväger två typer av visning av mer detaljerad information:

- [Större djup](#additional-depth)
- [Bredare perspektiv](#broader-perspective)

### <a name="additional-depth"></a>Större djup

När du visar en resultatsammanfattning på rapportsidan så kan sidan med mer detaljerad information visa information på transaktionsnivå för användarna. Med den här designmetoden kan användarna visa underliggande transaktioner där det är relevant.

I det här exemplet ser du vad som händer när en rapportanvändare visar detaljerad information från en månatlig sammanfattning av försäljningen. Sidan med mer detaljerad information innehåller en detaljerad lista med beställningar för en viss månad.

![I ett matrisobjekt med rubriken ”Sales Summary” grupperas försäljningen per år och månad på raderna och per land i kolumnerna. Dessutom visas en sida med mer detaljerad information.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Bredare perspektiv

En sida med mer detaljerad information kan visa motsatsen till större djup. Det här passar bra när du vill ge ett helhetsperspektiv.

I det här exemplet ser du vad som händer när en rapportanvändare visar detaljerad information från ett postnummer. Sidan med detaljerad information visar allmän information om postnumret.

![Ett visuellt tabellobjekt har tre kolumner: Postnummer, genomsnittligt antal överträdelser och genomsnittligt betyg. Dessutom visas en sida med mer detaljerad information.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Rekommendationer

Här är några bra tips när du skapar rapporter:

- **Format:** Använd gärna samma tema och format för sidan med detaljerad information som för rapporten i övrigt. Då känner användarna att det är en och samma rapport.
- **Filter för visning av detaljerad information:** Ställ in filter för detaljerad information så att du kan förhandsgranska ett realistiskt resultat när du utformar sidan. Glöm inte att ta bort de här filtren innan du publicerar rapporten.
- **Ytterligare funktioner:** En sida med detaljerad information fungerar precis som andra rapportsidor. Du kan till och med utöka den med fler interaktiva funktioner som utsnitt och filter.
- **Tomma värden:** Undvik att lägga till visuella objekt som kan visa tomma värden eller som genererar fel när filter för detaljerad information används.
- **Synlighet för sidorna:** Överväg att dölja sidor med detaljerad information. Om du bestämmer dig för att låta sidor med detaljerad information vara synliga måste du lägga till en knapp som gör att användaren kan rensa alla tidigare angivna detaljfilter. Tilldela ett [bokmärke](../create-reports/desktop-bookmarks.md) till knappen. Bokmärket ska konfigureras för att ta bort alla filter.
- **Tillbaka-knapp:** När du tilldelar ett filter för detaljerad information läggs en [tillbaka-knapp](../create-reports/desktop-buttons.md) till automatiskt. Behåll den gärna. På så sätt kan rapportanvändarna enkelt gå tillbaka till ursprungssidan.
- **Identifiering:** Gör det enklare att upptäcka detaljsidan genom att ställa in rubriktext eller lägga till instruktioner i en textruta. Du kan också designa ett överlägg enligt beskrivningen i [det här blogginlägget](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> Du kan även konfigurera visning av detaljerad information i sidnumrerade Power BI-rapporter. Det gör du genom att lägga till länkar till Power BI-rapporter. Länkar kan definiera [adressparametrar](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Använd detaljinformation i Power BI Desktop](../create-reports/desktop-drillthrough.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
