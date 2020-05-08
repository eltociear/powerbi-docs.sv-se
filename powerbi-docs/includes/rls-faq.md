---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409387"
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

**Fråga:** Min datakälla har redan definierade säkerhetsroller (till exempel SQL Server-roller eller SAP BW-roller). Vad är förhållandet mellan dessa och RLS?  
**Svar:** Svaret beror på om du importerar data eller använder DirectQuery. Om du importerar data till din Power BI-datauppsättning används inte säkerhetsrollerna i din datakälla. I så fall bör du definiera RLS att tillämpa säkerhetsregler för användare som ansluter i Power BI. Om du använder DirectQuery används säkerhetsrollerna i din datakälla. När en användare öppnar en rapport skickar Power BI en fråga till den underliggande datakällan, som tillämpar säkerhetsregler på data baserat på användarens autentiseringsuppgifter.
