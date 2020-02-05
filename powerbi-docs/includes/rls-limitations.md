---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: davidi
ms.openlocfilehash: 6d1a239954a64da1c92cc68b56912e6f4ab67228
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "74882801"
---
## <a name="limitations"></a>Begränsningar

Nedan följer en lista med aktuella begränsningar för säkerhet på radnivå i molnmodeller.

* Om du tidigare har definierat roller och regler i Power BI-tjänsten måste du återskapa dem i Power BI Desktop.

* Du kan endast definiera RLS på datauppsättningar som skapats med Power BI Desktop. Om du vill aktivera RLS för datauppsättningar som skapats med Excel måste du först konvertera filerna till PBIX-filer (Power BI Desktop-filer). [Läs mer](../desktop-import-excel-workbooks.md)

* Du kan bara använda Import- och DirectQuery-anslutningar. Live-anslutningar till Analysis Services hanteras i modellen lokalt.

## <a name="known-issues"></a>Kända problem

Det finns ett känt problem där du får ett felmeddelande om du försöker publicera en tidigare publicerad rapport från Power BI Desktop. Scenariot är följande.

1. Anna har en datauppsättning som har publicerats till Power BI-tjänsten och är konfigurerad med RLS.

1. Hon uppdaterar rapporten i Power BI Desktop och publicerar den igen.

1. Anna får ett fel.

**Tillfällig lösning:** Publicera Power BI Desktop-filen från Power BI-tjänsten tills problemet är löst. Du kan göra det genom att välja **Hämta data** > **Filer**.
