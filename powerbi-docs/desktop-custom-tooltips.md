---
title: Anpassa knappbeskrivningar i Power BI Desktop
description: Skapa anpassade knappbeskrivningar för visuella objekt med dra och släpp
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 08eda4e93a3e02e357c8153c656ec16811893ea9
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761443"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Anpassa knappbeskrivningar i Power BI Desktop
Knappbeskrivningar är ett elegant sätt att visa sammanhanget och detaljerad information om datapunkter. Följande bild visar en knappbeskrivning som tillämpas på ett diagram i Power BI Desktop.

![Standardknappbeskrivning](media/desktop-custom-tooltips/custom-tooltips-1.png)

När ett visuellt objekt skapas visas standardknappbeskrivningen datapunktens värde och kategori. Det finns många fall då det vore användbart att kunna anpassa knappbeskrivningen och visa sammanhanget eller mer information för de användare som tittar på det visuella objektet. Med anpassade knappbeskrivningar kan du ange fler datapunkter som ska visas som del av knappbeskrivningen.

## <a name="how-to-customize-tooltips"></a>Så här gör du för att anpassa knappbeskrivningar
Om du vill skapa en anpassad knappbeskrivning går du till brunnen **Fält** i fönstret **Visualiseringar**. Sedan drar du ett fält till bucketen **Knappbeskrivningar** enligt vad som visas i följande bild. I följande bild har två fält placerats i bucketen **Knappbeskrivningar**.

![Lägga till knappbeskrivningsfält](media/desktop-custom-tooltips/custom-tooltips-2.png)

När knappbeskrivningarna har lagts till i fältbrunnen visas värden för dessa fält i knappbeskrivningen när du håller muspekaren över det visuella objektet.

![Anpassad knappbeskrivning](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Anpassa knappbeskrivningar med aggregering eller snabberäkningar
Du kan anpassa en knappbeskrivning ytterligare genom att välja en aggregeringsfunktion eller en *Snabberäkning* genom att välja pilen bredvid fältet i bucketen **Knappbeskrivningar** och välja bland de tillgängliga alternativen.

![Knappbeskrivning med Snabberäkning](media/desktop-custom-tooltips/custom-tooltips-4.png)

Det finns många sätt att anpassa **knappbeskrivningar** med alla fält som är tillgängliga i din datamängd. Det gör att du kan förmedla snabb information och insikter till användare som tittar på dina instrumentpaneler och rapporter.

