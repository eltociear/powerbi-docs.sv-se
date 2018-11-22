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
ms.openlocfilehash: 3d9e8e46fdd84edbeb5b4ff5e8f7efe4a4291049
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679265"
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

## <a name="next-steps"></a>Nästa steg

Mer information och svar på frågor finns i [Vanliga frågor och svar om anpassade visuella Power BI-objekt](power-bi-custom-visuals-faq.md#organizational-custom-visuals).
