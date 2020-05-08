---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: b67025de5e2a70876a31fd42e22c9572403288fa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464421"
---
## <a name="limitations"></a>Begränsningar

Här är en lista med aktuella begränsningar för säkerhet på radnivå i molnmodeller:

* Om du tidigare har definierat roller och regler i Power BI-tjänsten måste du återskapa dem i Power BI Desktop.

* Du kan endast definiera RLS på datauppsättningar som skapats med Power BI Desktop. Om du vill aktivera RLS för datauppsättningar som skapats med Excel måste du först konvertera filerna till PBIX-filer (Power BI Desktop-filer). [Läs mer](../desktop-import-excel-workbooks.md).

* Du kan bara använda Import- och DirectQuery-anslutningar. Live-anslutningar till Analysis Services hanteras i modellen lokalt.

## <a name="known-issues"></a>Kända problem

Det finns ett känt problem där du får ett felmeddelande om du försöker publicera en tidigare publicerad rapport från Power BI Desktop. Scenariot är följande:

1. Anna har en datauppsättning som har publicerats till Power BI-tjänsten och är konfigurerad med RLS.

1. Hon uppdaterar rapporten i Power BI Desktop och publicerar den igen.

1. Anna får ett fel.

**Lösning:** Publicera Power BI Desktop-filen från Power BI-tjänsten tills problemet är löst. Du kan göra det genom att välja **Hämta data** > **Filer**.
