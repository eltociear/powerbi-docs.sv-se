---
title: Markering
description: Markering av datapunktsval i visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4ff2187dc99d4e790b08c11f55a37e31e85693ad
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193973"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Markera datapunkter i visuella Power BI-objekt

När ett element väljs filtreras matrisen `values` i `dataView`-objektet som standard till endast de valda värdena. Det gör att alla andra visuella objekt på sidan endast visar valda data.

![standardbeteende för markering för ”datavy”](./media/highlight-dataview.png)

Om du anger egenskapen `supportsHighlight` i din `capabilities.json` till `true` får du den fullständiga ofiltrerade `values`-matris tillsammans med en `highlights`-matris. Matrisen `highlights` får samma längd som värdematrisen, och alla ej valda värden anges till `null`. Med den här egenskapen aktiverad ansvarar det visuella ansvaret för att markera lämpliga data genom att jämföra matrisen `values` med matrisen `highlights`.

![”Datavy”-markering stöder markeringar](./media/highlight-dataview-supports.png)

I exemplet ser du det enstaka fält som är markerat. Och det är det enda värdet i markeringsmatrisen. Det är även viktigt att observera att det kan finnas flera val och delvis markering. Det finns motsvarande numeriska värde i värdena och markeringsmatrisen förekommer då men är annorlunda.
