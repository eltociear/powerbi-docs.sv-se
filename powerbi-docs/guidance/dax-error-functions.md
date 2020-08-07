---
title: 'DAX: Lämplig användning av felfunktioner'
description: Vägledning om när du ska använda DAX-felfunktionerna.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: f00f554a35c4e92328b1ea1017baf7d8006386a0
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537491"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Lämplig användning av felfunktioner

När du som datamodellerare skriver ett DAX-uttryck som kan generera utvärderingstidsfel kan du överväga att använda två användbara DAX-funktioner.

- Funktionen [ISERROR](/dax/iserror-function-dax), som tar ett enda uttryck och returnerar TRUE om uttrycket resulterar i ett fel.
- Funktionen [IFERROR](/dax/iferror-function-dax), som tar två uttryck. Om det första uttrycket resulterar i fel returneras värdet för det andra uttrycket. Det är i själva verket en mer optimerad implementering som bäddar in ISERROR-funktionen i en [IF](/dax/if-function-dax)-funktion.

Men även om dessa funktioner kan vara användbara och kan bidra till att skriva lättförståeliga uttryck, kan de även märkbart försämra prestandan för beräkningar. Det beror på att de här funktionerna ökar antalet genomsökningar som krävs för lagringsmotorn.

De flesta utvärderingstidsfel beror på oväntade tomma värden eller nollvärden, eller ogiltig datatypskonverteringar.

## <a name="recommendations"></a>Rekommendationer

Det är bättre att undvika att använda ISERROR- och IFERROR-funktionerna. Använd i stället defensiva strategier när du utvecklar modellen och skriver uttryck. Strategier kan vara:

- **Säkerställa att kvalitetsdata läses in i modellen:** Använd Power Query-omvandlingar för att ta bort eller byta ut ogiltiga eller saknade värden och för att ange rätt datatyper. En Power Query-omvandling kan även användas för att filtrera rader när fel som ogiltig datakonvertering inträffar.

    Datakvalitet kan även styras genom att du anger egenskapen för modellkolumnen **Is Nullable** till av, vilket gör att datauppdateringen misslyckas om tomma värden påträffas. Om det här felet uppstår kvarstår data i tabellerna som lästs in vid en lyckad uppdatering.
- **Använda IF-funktionen:** IF-funktionens logiska testuttryck kan fastställa om ett felresultat skulle inträffa. Observera, precis som funktionerna ISERROR och IFERROR, kan den här funktionen resultera i ytterligare genomsökningar av lagringsmotorn, men den kommer förmodligen att ha bättre prestanda än dem då inget fel behöver inledas.
- **Använda feltoleranta funktioner:** Vissa DAX-funktioner testar och kompenserar för felvillkor. Med dessa funktioner kan du ange ett alternativt resultat som ska returneras i stället. Funktionen [DIVIDE](/dax/divide-function-dax) är ett exempel. Ytterligare information om den här funktionen finns i artikeln [DAX: DIVIDE-funktionen kontra divide-operatorn (/)](dax-divide-function-operator.md).

## <a name="example"></a>Exempel

Följande måttuttryck testar om ett fel skulle höjas. Den returnerar tom i den här instansen (vilket är fallet när du inte anger IF-funktionen med ett value-if-false-uttryck).

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

Nästa version av måttuttrycket har förbättrats med funktionen IFERROR i stället för funktionerna IF och ISERROR.

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

Den här slutliga versionen av måttuttrycket uppnår samma utfall men på ett mer effektivt och elegant sätt.

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)

- Utbildningsväg: [Använda DAX i Power BI Desktop](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
