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
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1626c2af5906004b6b4f79f4830f003b96e241fc
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2018
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

