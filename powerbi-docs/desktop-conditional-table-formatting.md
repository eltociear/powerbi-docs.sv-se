---
title: Villkorlig tabellformatering i Power BI Desktop
description: Tillämpa anpassad formatering
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1fa296fe5e0973842363563d703649102cca5b73
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="conditional-formatting-in-tables"></a>Villkorsstyrd formatering i tabeller
Med villkorsstyrd formatering för tabeller kan du specificera anpassade cellbakgrundsfärger baserat på cellvärden, inklusive toningar. Åtkomst till villkorlig formatering, i brunnen **fält** i fönstret **Visuella objekt** i Power BI Desktop väljer du nedpilen bredvid värdet i brunnen **Värden** som du vill formatera (eller högerklicka på fältet). Du kan endast hantera villkorsstyrd formatering för fälten i området **Värden** i brunnen **Fält**.

![](media/desktop-conditional-table-formatting/table-formatting_1.png)

I dialogrutan som visas kan du konfigurera färgen, samt *minimi-* och *max*värden. Om du väljer rutan **Avvikande** kan du konfigurera ett valfritt *Centrumvärde*.

![](media/desktop-conditional-table-formatting/table-formatting_2.png)

När det tillämpas på en tabell åsidosätter den eventuella anpassade tabellformateringar som har tillämpas på villkorsstyrt formaterade celler.

![](media/desktop-conditional-table-formatting/table-formatting_3.png)

Om du vill ta bort villkorlig formatering från en visualisering, bara högerklickar du på fältet igen och väljer **ta bort villkorsstyrd formatering**.

![](media/desktop-conditional-table-formatting/table-formatting_4.png)

