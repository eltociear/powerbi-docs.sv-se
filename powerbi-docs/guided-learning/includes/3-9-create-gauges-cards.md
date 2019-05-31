---
ms.openlocfilehash: 3fd97374836978a4902a878da141865c271df643
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61397950"
---
I allmänhet används visualiseringar för att jämföra två eller flera olika värden. Men ibland när du skapar en rapport vill du kunna spåra ett mått eller ett nyckeltal (KPI) över tid. I Power BI Desktop sker detta med en **Mätare** eller ett kort med ett **enkelt nummer**. Om du vill skapa ett tomt diagram med någon av dessa typer, väljer du motsvarande ikon i fönstret **Visualiseringar**.

![](media/3-9-create-gauges-cards/3-9_1.png)

Mätare är särskilt användbara när du skapar instrumentpaneler och vill visa framsteg mot mål. Om du vill skapa en mätare väljer du ikonen från fönstret **Visualiseringar**. Dra fältet som du vill spåra i bucketen *Värde*.

![](media/3-9-create-gauges-cards/3-9_1a.png)

Mätare visas som standard på 50 % eller dubbla det *värdet* och det finns två sätt att ändra den här inställningen. Ange värdena dynamiskt genom att dra fält till buckets för *minsta*, *maximala* och *mål*-värden. Du kan också använda formateringsalternativ för visualiseringar för att manuellt anpassa intervallet för mätaren.

![](media/3-9-create-gauges-cards/3-9_2.png)

Kortvisualiseringar visar bara en numerisk representation av ett fält. Som standard används visningsenheter för att hålla värdena korta, till exempel visa ”5 md $” i stället för ”5 000 000 000 $”. Använd alternativ för visualiseringsformatering för att ändra vald enhet eller för att avaktivera den helt.

![](media/3-9-create-gauges-cards/3-9_3.png)

En intressant tillämpning av kort är att använda ett anpassat mått som du har sammanfogat med texten. I det tidigare exemplet, kan ett anpassat mått kortet omfatta avancerade DAX-funktioner och visa något i stil med ”Totalt antal intäkter i år: 5 md $” eller ”säljtal hittills i år”. Värdena som representerar utvecklingen läggs sedan till.

![](media/3-9-create-gauges-cards/3-9_4.png)

