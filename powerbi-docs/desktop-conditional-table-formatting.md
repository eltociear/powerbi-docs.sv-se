---
title: Villkorlig tabellformatering i Power BI Desktop
description: Tillämpa anpassad formatering
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9599b40940c9d9cca254bb2ed2e87c161cce371f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="conditional-formatting-in-tables"></a>Villkorsstyrd formatering i tabeller
Med villkorsstyrd formatering för tabeller kan du ange anpassade cellbakgrundsfärger baserat på cellvärden, eller på andra värden eller fält, och använda toningar. Åtkomst till villkorlig formatering, i brunnen **fält** i fönstret **Visuella objekt** i Power BI Desktop väljer du nedpilen bredvid värdet i brunnen **Värden** som du vill formatera (eller högerklicka på fältet). Du kan endast hantera villkorsstyrd formatering för fälten i området **Värden** i brunnen **Fält**.

![Villkorsstyrd tabellformatering](media/desktop-conditional-table-formatting/table-formatting_1.png)

I dialogrutan som visas kan du konfigurera färgen, samt *minimi-* och *max*värden. Om du väljer rutan **Avvikande** kan du konfigurera ett valfritt *Centrumvärde*.

![Avvikande färger](media/desktop-conditional-table-formatting/table-formatting_2.png)

Du kan också basera färgtoningen på ett fält från datamodellen. Du kan också ange aggregeringstypen för det markerade fältet (det valda fältet visas i fältet **Använd färgen på**, så att du vet vilket fält du arbetar med).

![Grundfärger för ett fält](media/desktop-conditional-table-formatting/table-formatting_2b.png)

När det tillämpas på en tabell åsidosätter den eventuella anpassade tabellformateringar som har tillämpas på villkorsstyrt formaterade celler.

![Tabellformatering](media/desktop-conditional-table-formatting/table-formatting_3.png)

Du kan också använda villkorsstyrd formatering för text- och datumfält, förutsatt att du väljer ett numeriskt värde som bas för formateringen. 

Om du vill ta bort villkorlig formatering från en visualisering, bara högerklickar du på fältet igen och väljer **ta bort villkorsstyrd formatering**.

![Ta bort tabellformatering](media/desktop-conditional-table-formatting/table-formatting_4.png)

