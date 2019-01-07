---
title: Felsökning av hur du utvecklar anpassade visuella objekt i Power BI
description: Den här artikeln går igenom några vanliga problem som kan uppstå när du utvecklar eller skapar ett anpassat objekt i Power BI.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: bc5d5b7151643764b174d0bbec09e7f47ea2b1b2
ms.sourcegitcommit: 13fdc8d62960f20c6d9ca1ab292f98992b47083b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53553868"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Felsöka anpassade visuella objekt i Power BI

## <a name="debug"></a>Felsök

**Pbiviz-kommandot hittades inte (eller liknande fel)**

När du kör `pbiviz` på kommandoraden i terminalen bör du se hjälpskärmen. Om du inte gör det så har den inte installerats korrekt. Kontrollera att du har installerat version 4.0 av NodeJS eller senare.

**Det gick inte att hitta det visuella felsökningsobjektet på fliken Visualiseringar**

Det visuella felsökningsobjektet ser ut som en frågeikon på fliken **Visualiseringar**.

![Val av visuella objekt](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Kontrollera att du har aktiverat det på inställningarna för Power BI om du inte kan se det.

> [!NOTE]
> Det går för närvarande endast att felsöka visuella objekt i Power BI-tjänsten och inte i Power BI Desktop eller mobilappen. Det paketerade visuella objektet kommer fortfarande att fungera överallt.

**Det går inte att kontakta den visuella servern**

Kör den visuella servern `pbiviz start` på kommandoraden i terminalen från roten av ditt visuella projekt. Om servern inte körs är det troligt att dina SSL-certifikat inte har installerats korrekt.

Ta gärna kontakt med supporten för anpassade visuella objekt: *pbicvsupport@microsoft.com* om du har frågor, kommentarer eller problem.

## <a name="next-steps"></a>Nästa steg

Mer information finns i [Vanliga frågor och svar om anpassade visuella Power BI-objekt](power-bi-custom-visuals-faq.md#organizational-custom-visuals).
