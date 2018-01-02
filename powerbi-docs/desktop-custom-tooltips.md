---
title: Anpassa knappbeskrivningar i Power BI Desktop
description: "Skapa anpassade knappbeskrivningar för visuella objekt med dra och släpp"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: a54cc745cb341188efb511d66a71b185a7967212
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Anpassa knappbeskrivningar i Power BI Desktop
Knappbeskrivningar är ett elegant sätt att visa sammanhanget och detaljerad information om datapunkter. Följande bild visar en knappbeskrivning som tillämpas på ett diagram i Power BI Desktop.

![](media/desktop-custom-tooltips/custom-tooltips_1.png)

När ett visuellt objekt skapas visas standardknappbeskrivningen datapunktens värde och kategori. Det finns många fall då det vore användbart att kunna anpassa knappbeskrivningen och visa användaren sammanhanget eller mer information om datapunkten. Med anpassade knappbeskrivningar kan du ange fler datapunkter som ska visas som del av knappbeskrivningen.

## <a name="how-to-customize-tooltips"></a>Så här gör du för att anpassa knappbeskrivningar
Om du vill skapa en anpassad knappbeskrivning i brunnen **Fält** i rutan **Visuella objekt** är det bara att dra ett fält till bucketen **Knappbeskrivningar** som visas i följande bild. I följande bild har fyra fält har placerats i bucketen **knappbeskrivningar**.

![](media/desktop-custom-tooltips/custom-tooltips_2.png)

När knappbeskrivningarna har lagts till i fältbrunnen visas värden för dessa fält i knappbeskrivningen när du håller muspekaren över det visuella objektet.

![](media/desktop-custom-tooltips/custom-tooltips_3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Anpassa knappbeskrivningar med aggregering eller snabberäkningar
Du kan anpassa en knappbeskrivning ytterligare genom att välja en aggregeringsfunktion eller en *Snabberäkning* genom att välja pilen bredvid fältet i bucketen **Knappbeskrivningar** och välja bland de tillgängliga alternativen.

![](media/desktop-custom-tooltips/custom-tooltips_4.png)

Det finns många sätt att anpassa **Knappbeskrivningar** med alla fält som är tillgängliga i din datauppsättning för att förmedla snabb information och insikter till användare som visar dina instrumentpaneler och rapporter.

