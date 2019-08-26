---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560941"
---
## <a name="faq"></a>Vanliga frågor och svar
**Fråga:** Vad händer om jag tidigare har skapat roller och regler för en datamängd i Power BI-tjänsten? Fungerar de fortfarande om jag inte gör någonting?  
**Svar:** Nej, visuella objekt kommer inte att renderas korrekt. Du måste återskapa rollerna och reglerna i Power BI Desktop och sedan publicera till Power BI-tjänsten.

**Fråga:** Kan jag skapa rollerna för Analysis Services-datakällor?  
**Svar:** Du kan göra det om du har importerat data till Power BI Desktop. Om du använder en live-anslutning kan du inte konfigurera RLS i Power BI-tjänsten. Detta definieras i Analysis Services-modellen lokalt.

**Fråga:** Kan jag använda RLS för att begränsa kolumner eller mått som är tillgängliga för mina användare?  
**Svar:** Nej, om användarna har åtkomst till en viss datarad kan de se alla datakolumner för den raden.

**Fråga:** Tillåter RLS att jag döljer detaljerade data men ger åtkomst till data som sammanfattas i visuella objekt?  
**Svar:** Nej, du kan skydda enskilda datarader men användarna kan alltid se information eller sammanfattade data.

