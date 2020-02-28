---
title: Guide till användning av bilder i sidnumrerade rapporter
description: Guide till användning av bilder i sidnumrerade Power BI-rapporter.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 09fd2197cca31e083c0242b187d7e242244235eb
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530382"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Guide till användning av bilder i sidnumrerade rapporter

Den här artikeln är avsedd för rapportförfattare som skapar [sidnumrerade rapporter](../paginated-reports-report-builder-power-bi.md) i Power BI. Den innehåller förslag på hur du kan arbeta med bilder. Vanligtvis kan bilder i rapportlayouter visa en bild, som en företagslogotyp.

Bilder kan lagras på tre olika sätt:

- I rapporten (inbäddad)
- På en webbserver
- I en databas, som kan hämtas av en datamängd

De kan sedan användas på flera olika sätt i dina rapportlayouter:

- Fristående logotyp eller bild
- Bilder som är associerade med datarader
- Bakgrund till vissa rapportobjekt:
  - Rapportens brödtext
  - Textruta
  - Rektangel
  - Tablix-dataområde (tabell, matris eller lista)

## <a name="suggestions"></a>Förslag

Följande förslag kan hjälpa dig att skapa professionella rapportlayouter, göra underhållet enklare och optimera rapportens prestanda:

- **Använd minsta möjliga storlek**: Vi rekommenderar att du förbereder bilder med liten storlek men som ändå är skarpa och tydliga. Det viktiga är balansen mellan kvalitet och storlek. Överväg att använda ett grafikredigeringsprogram (som MS Paint) till att minska bildfilens storlek.
- **Undvik inbäddade bilder**: För det första så kan inbäddade bilder göra rapportfilen onödigt stor, och det kan göra att återgivningen tar längre tid. För det andra så kan inbäddade bilder snabbt göra underhållet till en mardröm, om du behöver uppdatera många bilder i rapporten (vilket kan hända om företaget skulle ändra sin logotyp).
- **Använd lagring på webbservrar**: Att lagra bilder på en webbserver är ett bra alternativ, särskilt om det gäller företagets logotyp som kan hämtas från företagets webbplats. Var dock försiktig om rapportanvändare ska öppna rapporter utanför nätverket. I så fall måste du se till att bilderna är tillgängliga via internet.

    När bilderna är relaterade till dina data (till exempel foton av säljarna) ska du namnge bildfilerna så att ett rapportuttryck kan skapa bildadressen dynamiskt. Du kan till exempel namnge bilderna på säljarna med respektive säljares anställningsnummer. Förutsatt att datamängden för rapporten hämtar anställningsnumret kan du skriva ett uttryck som genererar den fullständiga bildadressen.
- **Använd databaslagring**: När du lagrar bilddata i en relationsdatabas är det klokt att hämta bilddata direkt från databastabellerna, särskilt när bilderna inte är så stora.
- **Lämpliga bakgrundsbilder**: Om du bestämmer dig för att använda bakgrundsbilder måste du vara försiktig så att inte rapportanvändarna distraheras från data i rapporten. 

    Se också till att använda _bilder med vattenstämpelformat_. Bilder med vattenstämpelformat har normalt genomskinlig bakgrund (eller samma bakgrundsfärg som i rapporten). De har även svaga färger. Några vanliga exempel på bilder med vattenstämpelformat är företagslogotyper och innehållsetiketter som ”Utkast” eller ”Konfidentiellt”.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Vad är sidnumrerade rapporter i Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
