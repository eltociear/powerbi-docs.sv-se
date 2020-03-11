---
title: Undvik tomma sidor när du skriver ut sidnumrerade rapporter
description: Vägledning för att utforma sidnumrerade rapporter och undvika tomma sidor vid utskrift.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 349459b95a815a52665e50687554f81f90a9c81b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920860"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Undvik tomma sidor när du skriver ut sidnumrerade rapporter

Den här artikeln är avsedd för rapportförfattare som utformar [sidnumrerade rapporter](../paginated-reports/paginated-reports-report-builder-power-bi.md) i Power BI. Den innehåller rekommendationer som hjälper dig att undvika tomma sidor när rapporten exporteras till ett hårt sidformat – t.ex. PDF eller Microsoft Word – eller när den skrivs ut.

## <a name="page-setup"></a>Utskriftsformat

Egenskaperna för rapportens sidstorlek avgör sidorientering, mått och marginaler. Öppna rapportegenskaperna genom att:

- Använda rapportens **egenskapssida**: Högerklicka på det mörkgrå området utanför rapportarbetsytan och sedan välja _Rapportegenskaper_.
- Använda fönstret [**Egenskaper**](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): Klicka på det mörkgrå området utanför rapportarbetsytan för att välja rapportobjektet. Kontrollera att fönstret **Egenskaper** är öppet.

På sidan **Utskriftsformat** på rapportens **egenskapssida** finns ett gränssnitt där du kan se och uppdatera egenskaperna för utskriftsformatet.

![Bilden visar fönstret Rapportegenskaper, med sidan Utskriftsformat markerad.](media/report-paginated-blank-page/report-page-setup-properties.png)

Kontrollera att alla egenskaper för sidstorlek är korrekt konfigurerade:

|Egenskap|Rekommendation|
|---------|---------|
|Sidenheter|Välj relevanta enheter – tum eller centimeter.|
|Orientering|Välj rätt alternativ – stående eller liggande.|
|Pappersstorlek|Välj en pappersstorlek, eller ange anpassade värden för bredd och höjd.|
|Marginaler|Ange lämpliga värden för vänster-, höger-, topp- och bottenmarginalerna.|
|||

## <a name="report-body-width"></a>Bredd på rapportens brödtext

Egenskaperna för sidstorleken avgör hur mycket tillgängligt utrymme som finns för rapportobjekt. Rapportobjekt kan vara dataområden, datavisualiseringar eller andra rapportobjekt.

En vanlig orsak till att tomma sidor skrivs ut, är att bredden på rapportens brödtext _överskrider det tillgängliga sidutrymmet_.

Du kan bara se och ange bredden på rapportens brödtext i fönstret **Egenskaper**. Klicka först någonstans på ett tomt område i rapportens brödtext.

![Bilden visar fönstret Egenskaper, med breddegenskapen för rapportens brödtext markerad.](media/report-paginated-blank-page/report-body-properties-width.png)

Kontrollera att breddvärdet inte överskrider den tillgängliga sidbredden. Följande formel kan vara till hjälp:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Det går inte att minska bredden på rapportens brödtext om det finns rapportobjekt i det utrymme som du vill ta bort. Du måste först flytta eller ändra storlek på dem innan du minskar bredden.
>
> Dessutom kan bredden på rapportens brödtext öka automatiskt när du lägger till nya objekt, eller om du ändrar storlek på eller flyttar befintliga objekt. Rapportdesignern breddar alltid brödtexten efter objektens position och storlek.

## <a name="report-body-height"></a>Höjd på rapportens brödtext

En annan orsak till att en tom sida skrivs ut, är att det finns överflödigt utrymme i rapportens brödtext efter det sista objektet.

Vi rekommenderar att du alltid minskar höjden på brödtexten och tar bort eventuella avslutande blanksteg.

![Bilden visar en rapportdesign. Utrymmet nedanför Tablix-dataområdet är markerat som onödigt.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Sidbrytningsalternativ

Alla dataområden och datavisualiseringar innehåller sidbrytningsalternativ. Du har åtkomst till de här alternativen på egenskapssidan eller i fönstret **Egenskaper**.

Kontrollera att egenskapen **Lägg till en sidbrytning efter** inte är aktiverad i onödan.

![Bilden visar ett fönster med Tablix-egenskaper. Egenskapen ”Lägg till en sidbrytning efter” är aktiverad.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Använda tomt containerutrymme

Om problemet med den tomma sidan kvarstår, kan du prova att inaktivera rapportegenskapen **ConsumeContainerWhitespace**. Den kan bara ställas in i fönstret **Egenskaper**.

![Bilden visar fönstret Egenskaper, med egenskapen ConsumeContainerWhitespace markerad.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Som standard är den aktiverad. Den styr om ett tomt minimiutrymme i containers, till exempel rapportens brödtext eller en rektangel, ska användas. Det är bara tomma utrymmen till höger om och nedanför innehållet som påverkas.

## <a name="printer-paper-size"></a>Pappersstorlek för skrivare

Slutligen, om du skriver ut rapporten på papper, kontrollerar du att skrivaren innehåller rätt papper. Den fysiska pappersstorleken ska motsvara [rapportens pappersstorlek](#page-setup).

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Vad är sidnumrerade rapporter i Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Sidnumrering i sidnumrerade Power BI-rapporter](../paginated-reports/paginated-reports-pagination.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
