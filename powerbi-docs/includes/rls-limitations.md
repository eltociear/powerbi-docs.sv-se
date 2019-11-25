---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: mblythe
ms.openlocfilehash: c658e683e86a899d45728220dee3706a0d617f0f
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284165"
---
## <a name="limitations"></a>Begränsningar

Nedan följer en lista med aktuella begränsningar för säkerhet på radnivå i molnmodeller.

* Om du tidigare har definierat roller och regler i Power BI-tjänsten måste du återskapa dem i Power BI Desktop.

* Du kan endast definiera RLS på datauppsättningar som skapats med Power BI Desktop. Om du vill aktivera RLS för datauppsättningar som skapats med Excel måste du först konvertera filerna till PBIX-filer (Power BI Desktop-filer). [Läs mer](../desktop-import-excel-workbooks.md)

* Endast ETL- och DirectQuery-anslutningar stöds. Live-anslutningar till Analysis Services hanteras i modellen lokalt.

## <a name="known-issues"></a>Kända problem

Det finns ett känt problem där du får ett felmeddelande om du försöker publicera en tidigare publicerad rapport från Power BI Desktop. Scenariot är följande.

1. Anna har en datauppsättning som har publicerats till Power BI-tjänsten och är konfigurerad med RLS.

1. Hon uppdaterar rapporten i Power BI Desktop och publicerar den igen.

1. Anna får ett fel.

**Tillfällig lösning:** Publicera Power BI Desktop-filen från Power BI-tjänsten tills problemet är löst. Du kan göra det genom att välja **Hämta data** > **Filer**.
