---
title: Anpassa knappbeskrivningar i Power BI Desktop
description: Skapa anpassade knappbeskrivningar för visuella objekt med dra och släpp
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: faabacabbd20930f90187f4c21fe539d61b3d678
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578829"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Anpassa knappbeskrivningar i Power BI Desktop
Knappbeskrivningar är ett elegant sätt att visa sammanhanget och detaljerad information om datapunkter. Följande bild visar en knappbeskrivning som tillämpas på ett diagram i Power BI Desktop.

![Standardknappbeskrivning](media/desktop-custom-tooltips/custom-tooltips-1.png)

När ett visuellt objekt skapas visas standardknappbeskrivningen datapunktens värde och kategori. Det finns många fall då det vore användbart att kunna anpassa knappbeskrivningen och visa användaren sammanhanget eller mer information om datapunkten. Med anpassade knappbeskrivningar kan du ange fler datapunkter som ska visas som del av knappbeskrivningen.

## <a name="how-to-customize-tooltips"></a>Så här gör du för att anpassa knappbeskrivningar
Om du vill skapa en anpassad knappbeskrivning i brunnen **Fält** i rutan **Visuella objekt** är det bara att dra ett fält till bucketen **Knappbeskrivningar** som visas i följande bild. I följande bild har två fält placerats i bucketen **Knappbeskrivningar**.

![Lägga till knappbeskrivningsfält](media/desktop-custom-tooltips/custom-tooltips-2.png)

När knappbeskrivningarna har lagts till i fältbrunnen visas värden för dessa fält i knappbeskrivningen när du håller muspekaren över det visuella objektet.

![Anpassad knappbeskrivning](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Anpassa knappbeskrivningar med aggregering eller snabberäkningar
Du kan anpassa en knappbeskrivning ytterligare genom att välja en aggregeringsfunktion eller en *Snabberäkning* genom att välja pilen bredvid fältet i bucketen **Knappbeskrivningar** och välja bland de tillgängliga alternativen.

![Knappbeskrivning med Snabberäkning](media/desktop-custom-tooltips/custom-tooltips-4.png)

Det finns många sätt att anpassa **Knappbeskrivningar** med alla fält som är tillgängliga i din datauppsättning för att förmedla snabb information och insikter till användare som visar dina instrumentpaneler och rapporter.

