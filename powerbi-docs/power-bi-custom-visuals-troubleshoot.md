---
title: Felsökning av hur du utvecklar visuella objekt i Power BI
description: Den här artikeln går igenom några vanliga problem som kan uppstå när du utvecklar eller skapar ett anpassat objekt i Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: 4d863ff921df2a5cfb5233d85679f2277542bb44
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195372"
---
# <a name="troubleshoot-power-bi-power-bi-visuals"></a>Felsöka anpassade visuella Power BI-objekt

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

Ta gärna kontakt med supporten för visuella Power BI-objekt: *pbicvsupport@microsoft.com*  om du har frågor, kommentarer eller problem.

## <a name="next-steps"></a>Nästa steg

Mer information finns i [Vanliga frågor och svar om anpassade visuella Power BI-objekt](power-bi-custom-visuals-faq.md#organizational-visuals).