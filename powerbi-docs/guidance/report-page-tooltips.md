---
title: Utöka visuella objekt med knappbeskrivningar för rapportsida
description: Vägledning för att arbeta med knappbeskrivningar för rapportsidor.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: b7256a04ccdca107ef0cd8e24af8b3170a3d68cc
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74834734"
---
# <a name="extending-visuals-with-report-page-tooltips"></a>Utöka visuella objekt med knappbeskrivningar för rapportsida

Den här artikeln är avsedd för rapportförfattare som skapar Power BI-rapporter. Den innehåller förslag och rekommendationer när du skapar [knappbeskrivningar för rapportsidor](../desktop-tooltips.md).

## <a name="suggestions"></a>Förslag

Med knappbeskrivningar på rapportsidorna kan du ge användarna en bättre upplevelse. Knappbeskrivningarna gör att rapportanvändarna snabbt och effektivt kan få djupare insikter om ett visuellt objekt. Du kan koppla knappbeskrivningar till olika typer av rapportobjekt:

- **Visuella objekt:** Du kan konfigurera vilka enskilda visuella objekt som ska visa knappbeskrivningen. För varje visuellt objekt kan du ställa in att ingen knappbeskrivning ska visas, att objektets standardbeskrivning ska visas (konfigureras i fönstret med fält för objektet) eller att en beskrivning som gäller för hela sidan ska visas.
- **Visuella rubriker:** Du kan konfigurera att vissa visuella objekt ska visa en beskrivning för hela sidan. Rapportanvändarna kan visa sidbeskrivningen genom att hovra med markören över ikonen för den visuella rubriken. Se till att du informerar användarna om den här ikonen.

> [!NOTE]
> Visuella rapportobjekt kan bara visa sidbeskrivningar när filtren för knappbeskrivningssidan är kompatibla med det visuella objektets design. Ett visuellt objekt som grupperas efter _produkt_ är till exempel kompatibelt med en knappbeskrivningssida som filtrerar efter _produkt_.
>
> Sidbeskrivningar är inte interaktiva. Om du vill att rapportanvändarna ska kunna interagera skapar du en [sida med visning av detaljerad information](../desktop-drillthrough.md) istället.
>
> Anpassade visuella objekt saknar stöd för sidbeskrivningar.

Här är några olika designförslag:

- [Annat perspektiv](#different-perspective)
- [Lägg till information](#add-detail)
- [Lägg till hjälp](#add-help)

### <a name="different-perspective"></a>Annat perspektiv

En sidbeskrivning kan visualisera samma data som det visuella källobjektet. Du kan ordna det här genom att använda samma visuella objekt och pivoteringsgrupper, eller genom att använda andra visuella typer. Sidbeskrivningar kan också ha andra filter än de som används för det visuella källobjektet.

I det här exemplet ser du vad som händer när rapportanvändaren hovrar med markören över värdet **EnabledUsers**. Filterkontexten för värdet är Yammer i november 2018.

![Ett visuellt matrisobjekt visar ett rutnät med värden grupperade efter år och månad på raderna. Rapportanvändaren har hovrat över ett enskilt värde. En sidbeskrivning visas.](media/report-page-tooltips/suggestion-different-perspective.png)

En sidbeskrivning visas. Den visar ett annat visuellt dataobjekt (ett linjediagram och grupperat stående stapeldiagram) med ett kontrasterande tidsfilter. Observera att filterkontexten för datapunkten är november 2018. Sidbeskrivningen visar ändå trenden för _tolv hela månader_.

### <a name="add-detail"></a>Lägg till information

En sidbeskrivning kan visa ytterligare information och lägga till sammanhang.

I det här exemplet ser du vad som händer när rapportanvändaren hovrar med markören över värdet **Average of Violation Points**, för postnumret 98022.

![Ett visuellt tabellobjekt visar ett rutnät med värden, och tabellen innehåller tre kolumner. En sidbeskrivning visas.](media/report-page-tooltips/suggestion-add-details.png)

En sidbeskrivning visas. Den visar specifika attribut och statistik för postnumret 98022.

### <a name="add-help"></a>Lägg till hjälp

Du kan konfigurera visuella rubriker så att de visar sidbeskrivningar. Du kan lägga till hjälpinnehåll i en sidbeskrivning med hjälp av RTF-formaterade textrutor. Du kan även lägga till bilder och former.

Det är värt att notera att även knappar, bilder, textrutor och former kan visa sidbeskrivningar via en visuell rubrik.

I det här exemplet ser du vad som händer när rapportanvändaren hovrar med markören över ikonen för den visuella rubriken.

![En rapportanvändare har hovrat med markören över ikonen för den visuella rubriken (frågetecknet). En RTF-formaterad beskrivning visas.](media/report-page-tooltips/suggestion-add-help.png)

En sidbeskrivning visas. Den visar RTF-formaterad text som beskriver måtten i det visuella objektet. Beskrivningen innehåller även en form (en linje).

## <a name="recommendations"></a>Rekommendationer

Här är några bra tips när du skapar rapporter:

- **Sidstorlek:** Använd gärna små sidbeskrivningar. Du kan använda det inbyggda alternativet **Knappbeskrivning** (320 bildpunkter bred, 240 bildpunkter hög). Du kan också ange egna dimensioner. Tänk på att inte göra sidan för stor, då kan de visuella objekten på källsidan täckas över.
- **Sidvisning:** Ställ in sidvisningen i rapportdesignern på **Faktisk storlek** (standardvärdet är **Anpassa till sida**). Då visas den faktiska sidstorlek du ställer in.
- **Format:** Använd gärna samma tema och format för sidbeskrivningen som för rapporten i övrigt. Då känner användarna att det är en och samma rapport. Du kan också skapa ett särskilt format för alla beskrivningar och sedan använda det för samtliga sidbeskrivningar.
- **Beskrivningsfilter:** Tilldela filter till sidbeskrivningen så att du kan förhandsgranska ett realistiskt resultat när du designar den. Glöm inte att ta bort de här filtren innan du publicerar rapporten.
- **Synlighet för sidorna:** Gör alltid beskrivningssidor dolda, användarna ska inte navigera direkt till dem.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Skapa knappbeskrivningar baserat på rapportsidor i Power BI Desktop](../desktop-tooltips.md)
- [Anpassa knappbeskrivningar i Power BI Desktop](../desktop-custom-tooltips.md)
- Videon Guy in a Cube: [Knappbeskrivningar i Power BI-rapporter – så skapar du dem i Power BI Desktop](https://www.youtube.com/watch?v=URTA7JZsAtw)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
