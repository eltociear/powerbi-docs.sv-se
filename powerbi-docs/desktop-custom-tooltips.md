---
title: Anpassa knappbeskrivningar i Power BI Desktop
description: Skapa anpassade knappbeskrivningar för visuella objekt med dra och släpp
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 93177ac56bc2d8ecfe4b85f4ab66daef6bf0f0f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161045"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Anpassa knappbeskrivningar i Power BI Desktop

Knappbeskrivningar är ett elegant sätt att visa sammanhanget och detaljerad information om datapunkter. Följande bild visar en knappbeskrivning som tillämpas på ett diagram i Power BI Desktop.

![Standardknappbeskrivning](media/desktop-custom-tooltips/custom-tooltips-1.png)

När ett visuellt objekt skapas visas standardknappbeskrivningen datapunktens värde och kategori. Det finns många tillfällen när det är användbart att kunna anpassa knappbeskrivningar. Anpassningen av knappbeskrivningar ger ytterligare kontext och information till användare som ser det visuella objektet. Med anpassade knappbeskrivningar kan du ange fler datapunkter som ska visas som del av knappbeskrivningen.

## <a name="how-to-customize-tooltips"></a>Så här gör du för att anpassa knappbeskrivningar

Om du vill skapa en anpassad knappbeskrivning går du till **Fält** i fönstret **Visualiseringar**. Dra sedan ett fält till bucketen **Knappbeskrivningar** enligt följande bild. I följande bild har tre fält placerats i bucketen **Knappbeskrivningar**.

![Lägga till knappbeskrivningsfält](media/desktop-custom-tooltips/custom-tooltips-2.png)

När knappbeskrivningarna har lagts till i **Knappbeskrivningar**, visas värden för dessa fält när du hovrar över en datapunkt i visualiseringen.

![Anpassad knappbeskrivning](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>Anpassa knappbeskrivningar med aggregering eller snabbmått

Du kan anpassa en knappbeskrivning ytterligare genom att välja en aggregeringsfunktion eller ett *snabbmått*. Välj pilen bredvid fältet i bucketen **Knappbeskrivningar**. Välj sedan bland de tillgängliga alternativen.

![Knappbeskrivning med snabbmått](media/desktop-custom-tooltips/custom-tooltips-4.png)

Det finns många sätt att anpassa knappbeskrivningar på. Du kan använda alla fält som är tillgängliga i din datamängd till att förmedla snabb information och insikter till användare som tittar på dina instrumentpaneler och rapporter.
